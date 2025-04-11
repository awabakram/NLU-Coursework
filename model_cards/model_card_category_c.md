---
{}
---
language: en
license: cc-by-4.0
tags:
- text-classification
repo: https://github.com/awabakram/NLU-Coursework

---

# Model Card for m54606aa-e17646fa-C

<!-- Provide a quick summary of what the model is/does. -->

This is a transformer-based model fine-tuned to classify 
    natural language inference (NLI) sentence pairs as entailment (1) or non-entailment (0).


## Model Details

### Model Description

<!-- Provide a longer summary of what this model is. -->

This model is based on the `roberta-large` transformer architecture 
    and was fine-tuned using the HuggingFace Trainer API. It was trained on binary NLI data 
    provided for the COMP34812 coursework at the University of Manchester.

- **Developed by:** Awab Akram and Faysal Alkuraya
- **Language(s):** English
- **Model type:** Supervised
- **Model architecture:** Transformer (RoBERTa)
- **Finetuned from model [optional]:** roberta-large

### Model Resources

<!-- Provide links where applicable. -->

- **Repository:** https://huggingface.co/roberta-large
- **Paper or documentation:** https://arxiv.org/abs/1907.11692

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


      - total training time: ~1.5 hours (A100 GPU)
      - model size: ~1.5GB (after fine-tuning)

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

On the dev set: Accuracy ~0.92, Macro-Precision ~0.92, Macro-Recall ~0.92, Macro-F1 ~0.92, MCC ~0.84.

## Technical Specifications

### Hardware


      - GPU: A100 (or equivalent 16GB+ memory recommended)
      - RAM: 16GB+
      - Disk: ~2GB for model

### Software


      - Python 3.9.6
      - transformers 4.51.1
      - datasets
      - evaluate
      - torch
      - scikit-learn

## Bias, Risks, and Limitations

<!-- This section is meant to convey both technical and sociotechnical limitations. -->

TThe model is sensitive to dataset biases and may not generalize well 
      to other domains or low-resource settings. Sentence truncation to 512 tokens may affect long inputs.

## Additional Information

<!-- Any other information that would be useful for other people to know. -->

The model and tokenizer were saved using HuggingFace `save_pretrained()` 
      and compressed into `nli_bert_model.zip` for submission. Inference is handled using a demo notebook 
      that automatically downloads and unzips the model.
