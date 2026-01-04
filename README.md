Fake News Detection using Stance Detection (ML + Transformers)
Overview

This project presents a two-stage framework for Fake News Detection based on stance detection between news headlines and article bodies. Instead of treating fake news as a simple binary classification problem, the model determines how an article relates to a claim—whether it agrees, disagrees, discusses, or is unrelated.

The approach combines traditional machine learning techniques with state-of-the-art transformer models (BERT & BART) to improve both accuracy and interpretability.

Problem Statement

Fake news spreads rapidly on social media platforms and poses serious social, political, and economic risks. Existing models often:

Treat fake news as a binary classification problem

Fail to capture contextual and semantic relationships

Struggle with nuanced language and stance interpretation

This project addresses these limitations by detecting the stance of an article relative to a headline and then inferring whether the claim is likely real or fake.

Dataset

Fake News Challenge (FNC-1) Dataset

Total samples: 75,385 headline–article pairs

Training: 49,972

Testing: 25,413

Labels:

Agree

Disagree

Discuss

Unrelated

Additional real-time news articles were scraped from reputed sources to evaluate real-world performance.

Methodology
Stage 1: Baseline Model-1 (2-Class Classification)

Goal: Identify whether an article is Related or Unrelated to a headline.

Feature Engineering

Seven linguistic and semantic features were extracted:

Jaccard Similarity

Jaccard Similarity (Nouns)

Semantic Similarity

GloVe Similarity

Latent Dirichlet Allocation (LDA)

Kullback-Leibler Divergence

N-grams

Best Features Selected:

Jaccard Similarity (Nouns)

GloVe Similarity

N-grams

Model Used: Random Forest
Accuracy:

Train: 98%

Test: 94%

Stage 2: Baseline Model-2 (3-Class Stance Detection)

Goal: Classify related articles into:

Agree

Disagree

Discuss

Architecture

BART (Summarization)

Reduces article length

Prevents information loss due to BERT’s 512-token limit

BERT (Sequence Pair Classification)

Input: (Headline, Summarized Article)

Model: bert-base-uncased

Fine-tuned for 3-class stance detection

Key Hyperparameters

Learning Rate: 3e-5

Epochs: 5

Batch Size: 4

Max Sequence Length: 512

Optimizer: Adam

Dropout: 0.1

Results
Baseline Model-1 (2-Class)

Test Accuracy: 94%

Misclassification Rate: ~1.5%

Baseline Model-2 (3-Class BERT)
Dataset	Accuracy	MCC
Train	98%	0.97
Validation	88%	0.78
Test	75%	0.54

The transformer-based approach significantly improved contextual understanding and reduced misclassification compared to traditional ML models.

Final Decision Logic (Fake vs Real)

A claim is classified as Fake or Real based on:

Frequency of Agree, Disagree, and Discuss predictions

Threshold-based conditional rules applied across reputable news sources

Key Contributions

Two-stage stance-based fake news detection framework

Combination of ML feature engineering and Transformer models

Improved interpretability over binary fake-news classifiers

Reduced runtime and higher classification accuracy

Limitations

Imbalanced dataset (FNC-1 has fewer related articles)

Real-world performance affected by source credibility variations

Thresholding introduces some bias in real-news classification

Future Work

Train on larger, balanced real-world datasets

Incorporate source credibility scoring

Add style-based fake news detection (emotion, subjectivity, manipulation patterns)

Extend from 3-class stance detection to full 4-class inference

Keywords

Fake News Detection, Stance Detection, NLP, BERT, BART, Machine Learning, Transformers, Semantic Similarity, Text Classification
