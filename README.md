# intrusion-detection-algorithmic-efficiency-smote-xgboost

This repository contains a hybrid intrusion detection pipeline designed to run in Google Colab with Google Drive integration. It supports multiple cybersecurity datasets, configurable preprocessing, optional class balancing, feature selection, machine learning models, deep learning models, and automatic saving of reports, figures, and checkpoints.

## Overview

The pipeline is organized as an end-to-end experimental workflow for intrusion detection and traffic classification tasks. It includes dataset loading, data cleaning, scaling, class balancing with SMOTE, feature importance analysis, model training, evaluation, and result persistence.

The notebook is built to work with datasets such as KDD-CUP99, CICMalMem2022 and CICIDS2017. It also supports both binary and multiclass classification, depending on the dataset and task configuration.

## Methodology

The workflow begins by preparing the execution environment in Google Colab, mounting Google Drive, and defining input and output directories. This structure allows datasets, generated figures, reports, and checkpoints to remain organized across experiments.

Next, the selected dataset is loaded and preprocessed. The preprocessing stage includes basic cleaning to handle problematic values such as `inf`, `-inf`, and `NaN`, followed by feature scaling before training.

After preprocessing, the pipeline can apply class balancing using SMOTE. It supports different balancing strategies, generates class distribution outputs, and then prepares the train-test split for the downstream models.

The next stage performs feature selection using XGBoost-based importance ranking. This step is used to identify the most relevant variables before training the selected machine learning and deep learning models.

Finally, the notebook evaluates the trained models using common classification metrics and stores the outputs in structured folders. These outputs can include summary files, CSV reports, plots, confusion matrices, ROC curves, and reusable checkpoints.

## Configuration Options

The experiment setup is controlled through a small set of configurable variables. The `DATASET` variable can be set to `KDD`, `CICIDS2017`, or `MalMem2022`, while `TASKMODE` can be configured as `binary` or `multiclass` depending on the selected dataset.

The `SMOTEMODE` variable supports `dynamic`, `full`, or `none`, allowing the user to choose adaptive oversampling, full oversampling, or no SMOTE at all. In the same way, `RUNML` and `RUNDL` act as switches to enable or disable machine learning and deep learning execution blocks.

For classical models, the `MLTORUN` list can include algorithms such as `RF`, `DT`, `KNN`, `MLP`, `LightGBM`, and `CatBoost`. For deep learning experiments, the `DLTORUN` list can include `ANN`, `CNN1D`, `LSTM`, and `AELR`.

The pipeline also uses configurable paths for the dataset root, run directory, figures directory, reports directory, and checkpoint directory. This design makes it easy to reuse the same notebook across different experiments without changing the main logic.

## Output Structure

The project organizes results into separate directories for each experiment run. At a high level, the structure distinguishes between the main output folder, the dataset folder, and run-specific folders for figures, reports, and checkpoints.

This layout improves reproducibility and makes it easier to compare experiments across datasets, task modes, and model selections. It also helps keep intermediate outputs and final results clearly separated.

## Google Drive Links

- [Datasets folder](https://drive.google.com/drive/folders/12ehEfgjbDM9Kzf6NX8MsiWseCoRfu-lJ?usp=sharing)
- [Run results folder](https://drive.google.com/drive/folders/1Be-qf91Dyn_gg3t5ia41IkXBWQ19zBOL?usp=sharing)

## Usage

1. Open the notebook in Google Colab.
2. Mount Google Drive.
3. Place the datasets in the expected Drive directories.
4. Select the dataset, task mode, balancing strategy, and models to run.
5. Execute the notebook blocks in order to generate results, figures, reports, and checkpoints.
