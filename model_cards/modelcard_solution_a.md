---
{}
---
language: en
license: cc-by-4.0
tags:
- text-classification
repo: https://github.com/awabakram/NLU-Coursework

---

# Model Card for m54606aa-e17646fa-A

<!-- Provide a quick summary of what the model is/does. -->

This is a Support Vector Machine (SVM) model that classifies 
    natural language inference (NLI) pairs as entailment (1) or non-entailment (0).


## Model Details

### Model Description

<!-- Provide a longer summary of what this model is. -->

This model is based on a classical supervised machine learning pipeline 
    that combines TF-IDF vectorization and WordNet-based semantic features. It was trained on 
    the provided binary NLI dataset for COMP34812 coursework.

- **Developed by:** Awab Akram and Faysal Alkuraya
- **Language(s):** English
- **Model type:** Supervised
- **Model architecture:** SVM with TF-IDF and WordNet features
- **Finetuned from model [optional]:** Trained from scratch

### Model Resources

<!-- Provide links where applicable. -->

- **Repository:** N/A
- **Paper or documentation:** N/A

## Training Details

### Training Data

<!-- This is a short stub of information on the training data that was used, and documentation related to data pre-processing or additional filtering (if applicable). -->

24000 premise-hypothesis pairs from train.csv with binary labels.

### Training Procedure

<!-- This relates heavily to the Technical Specifications. Content here should link to that section when it is relevant to the training procedure. -->

#### Training Hyperparameters

<!-- This is a summary of the values of hyperparameters used in training the model. -->


      - TF-IDF: max_features=10000, ngram_range=(1,2), sublinear_tf=True
      - SVM: kernel="linear", C=0.1, class_weight="balanced"

#### Speeds, Sizes, Times

<!-- This section provides information about how roughly how long it takes to train the model and the size of the resulting model. -->


      - overall training time: 20 minutes (CPU)
      - model size: 11MB

## Evaluation

<!-- This section describes the evaluation protocols and provides the results. -->

### Testing Data & Metrics

#### Testing Data

<!-- This should describe any evaluation data used (e.g., the development/validation set provided). -->

Validation performed on dev.csv; test predictions on test.csv.

#### Metrics

<!-- These are the evaluation metrics being used. -->


      - Accuracy
      - Macro-F1
      - Macro-Precision
      - Macro-Recall
      - Matthews Correlation Coefficient (MCC)

### Results

On the dev set: Accuracy ~0.60, Macro-Precision ~0.61, Macro-Recall ~0.61, Macro-F1 ~0.60, MCC ~0.21.

## Technical Specifications

### Hardware


       - CPU (no GPU needed)
      - RAM: 4–8 GB recommended

### Software


      - Python 3.9.6
      - scikit-learn
      - nltk
      - joblib
      - pandas
      - tqdm

## Bias, Risks, and Limitations

<!-- This section is meant to convey both technical and sociotechnical limitations. -->

The model relies on lexical overlap and WordNet synonyms/antonyms, 
      which may not generalize well to more complex paraphrases or uncommon phrasing.

## Additional Information

<!-- Any other information that would be useful for other people to know. -->

The model is saved as a `joblib` pipeline. 
      WordNet-based features were implemented using `nltk.corpus.wordnet`.
