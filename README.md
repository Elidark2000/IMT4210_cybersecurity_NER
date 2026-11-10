# How much annotated data does cybersecurity entity recognition need?

This repository holds the code and results for the IMT4210 Computational Forensics project at NTNU, autumn 2026. 

The notebook fine-tunes bert-base-uncased on two cybersecurity NER datasets, CyNER and APTNER. Each model is trained on a subset of the training data.

IMT4210_project_cybersecurity_NER.ipynb holds all the code, with the outputs from the final run.

cyner_results.json and aptner_results.json hold the scores from the 51 sweep runs. The learning curves and the per type results in the paper are computed from these two files.

cyner_test_predictions.json holds the test set predictions from the full data CyNER run. The code reuses this file. The CyNER results are the same in every run.

aptner_test_predictions.json holds the test set predictions from the full data APTNER run. The code creates this file and uses it for the error analysis. A different run can give different numbers, but with little variance. 

The code trains one full data model on APTNER and writes its predictions to aptner_test_predictions.json. Cell 31 reads the file back for the error analysis. The file from the final run was not saved outside Colab. The APTNER error analysis in the paper comes from that run, and its results are in the saved output of the code. A new run creates the file again, but the numbers can differ slightly, because GPU training is not fully deterministic.

The datasets are not in this repository. The notebook downloads them from the original repositories. CyNER is at https://github.com/aiforsec/CyNER. APTNER is at https://github.com/wangxuren/APTNER.

The notebook runs in Google Colab on a T4 GPU.

1. Open the notebook in Colab and choose a T4 GPU runtime.
2. Upload the JSON files to the Colab session.
3. Run all cells

Without the JSON files, the notebook trains every model again. This takes about 90 minutes on a T4. 
