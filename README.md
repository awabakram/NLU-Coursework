# NLU Coursework

This repository contains the coursework for the Natural Language Understanding (NLU) course at the University of Manchester. The project focuses on solving the Natural Language Inference (NLI) task using two strategies:

- **Category A**: Traditional machine learning using an SVM pipeline
- **Category C**: Transformer-based deep learning using a fine-tuned RoBERTa model

## Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Installation](#installation)
- [Project Structure](#project-structure)
- [Usage](#usage)
- [License](#license)

## Introduction

The goal of this coursework is to implement and evaluate two different approaches to solving a Natural Language Inference task:

- A traditional machine learning pipeline based on SVM, TF-IDF vectorization, and WordNet-based semantic features.
- A transformer-based deep learning approach using a fine-tuned `roberta-base` model from HuggingFace.

Each model was evaluated based on its performance on a binary classification NLI task, and both models produce test set predictions for assessment.


## Features

- TF-IDF and WordNet-based semantic features for classical ML
- HuggingFace Transformers (`Trainer`) for fine-tuning RoBERTa
- Evaluation metrics: Accuracy, Macro-F1, Precision, Recall, MCC
- Demo notebooks for reproducibility
- Test prediction exports in required format

## Installation

1. Clone the repository:
    ```bash
    git clone https://github.com/your-username/NLU-Coursework.git
    cd NLU-Coursework
    ```

2. Create a virtual environment and activate it:
    ```bash
    python3 -m venv venv
    source venv/bin/activate
    ```

3. Install the required dependencies:
    ```bash
    pip install -r requirements.txt
    ```

## Project Structure

```
NLU-Coursework/
├── data/
│   ├── test_data
│   │   └── test.csv
│   └── training_data
│       ├── train.csv 
│       └── dev.csv
├── model_cards/
│   ├── model_card_category_a.md
│   └── model_card_category_c.md
├── solution_A/
│   ├── solution_a.ipynb        # Training + evaluation
│   ├── demo_a.ipynb            # Inference
│   └── Group_52_A.csv          # Predictions output file
├── solution_C/
│   ├── solution_c.ipynb        # Training + evaluation
│   ├── demo_c.ipynb            # Inference
│   └── Group_52_C.csv          # Predictions output file
├── COMP34812 Coursework AY2024-25.pdf
├── requirements.txt
├── README.md
└── .gitignore

```

<!-- ## Usage

### Category A

#### `solution_a.ipynb` (Training + Evaluation)
- Trains a pipeline consisting of TF-IDF, WordNet-based semantic features, and an SVM classifier.
- Evaluates performance using metrics like accuracy, F1, precision, recall, and MCC.
- Saves the trained model as `nli_svm_model.joblib`.

#### `demo_a.ipynb` (Inference Only)
- Automatically downloads `nli_svm_model.joblib` from Google Drive if not found locally (requires `gdown`).
- Loads test data from `data/test_data/test.csv`.
- Runs inference using the trained SVM model.
- Saves output predictions to `Group_52_A.csv`.

---

### Category C

#### `solution_c.ipynb` (Training + Evaluation)
- Fine-tunes the `roberta-large` model using HuggingFace Transformers.
- Evaluates the model on a validation set.
- Saves the trained model and tokenizer using `save_pretrained()`.
- Compresses the model directory as `nli_bert_model.zip` for submission.

#### `demo_c.ipynb` (Inference Only)
- Automatically downloads and unzips `nli_bert_model.zip` from Google Drive.
- Loads test data from `data/test_data/test.csv`.
- Tokenizes input and runs inference using the loaded model.
- Saves output predictions to `Group_52_C.csv`.

> ⚠️ Both demo notebooks require internet access to download the trained models from Google Drive. -->

## Usage

### Category A

#### `solution_a.ipynb` (Training + Evaluation)
- Loads training data from `data/training_data/train.csv` and validation data from `data/training_data/dev.csv`.
- Trains a pipeline consisting of TF-IDF, WordNet-based semantic features, and an SVM classifier.
- Evaluates performance using metrics such as accuracy, F1, precision, recall, and MCC on the dev set.
- Predicts on `data/training_data/dev.csv` and saves the output to `Group_52_A.csv`.
- Saves the trained model as `nli_svm_model.joblib`.

#### `demo_a.ipynb` (Inference Only)
- Automatically downloads `nli_svm_model.joblib` from Google Drive if not found locally (requires `gdown`).
- Loads test data from `data/test_data/test.csv`.
- Runs inference using the trained SVM model.
- Saves output predictions to `Group_52_A.csv`.

---

### Category C

#### `solution_c.ipynb` (Training + Evaluation)
- Loads training data from `data/training_data/train.csv` and validation data from `data/training_data/dev.csv`.
- Fine-tunes the `roberta-large` model using HuggingFace Transformers.
- Evaluates the model on the dev set and monitors performance during training.
- Predicts on `data/training_data/dev.csv` and saves the output to `Group_52_C.csv`.
- Saves the model and tokenizer using `save_pretrained()`, and compresses the directory as `nli_bert_model.zip`.

#### `demo_c.ipynb` (Inference Only)
- Automatically downloads and unzips `nli_bert_model.zip` from Google Drive.
- Loads test data from `data/test_data/test.csv`.
- Tokenizes inputs and performs inference using the loaded RoBERTa model.
- Saves output predictions to `Group_52_C.csv`.

> ⚠️ Both demo notebooks require internet access to download the trained models from Google Drive.


## Resources & Attribution

- The RoBERTa model (`roberta-large`) was obtained from [Hugging Face](https://huggingface.co/roberta-large).
- The TF-IDF vectorizer and SVM model were built using Scikit-learn and NLTK WordNet.
- gdown was used to download pretrained models from Google Drive.

### Model Links

- Category A model: [Download link](https://drive.google.com/file/d/1ilMvFGJQyKflsDgTvnxl7OTtt4ISq-wj/view?usp=drive_link)
- Category C model: [Download link](https://drive.google.com/file/d/1F-QLA-fLmYIzxXsOlh5RnlNx3A6WydL1/view?usp=drive_link)


## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
