# NLP-for-Political-Orientation-Detection

## Overview

This project focuses on the automatic classification of French political texts according to their ideological orientation: **left, center, or right**.

The objective is to compare several Natural Language Processing (NLP) approaches, ranging from classical methods to more advanced embedding-based models, in order to evaluate their effectiveness on this task.

---

## Dataset

The dataset is composed of:

- Political texts (programs, speeches, etc.)
- Metadata including political party information

A preprocessing step was required to map political parties to three ideological classes:
- Left
- Center
- Right

This mapping is manually constructed and introduces some approximation in the labels.

---

## Methods

Three main approaches were implemented and compared.

### 1. TF-IDF + LinearSVC

- Texts are represented using TF-IDF vectors
- Classification is performed using a linear Support Vector Machine

This approach captures **discriminative words directly**.

---

### 2. Doc2Vec + LinearSVC

- Documents are embedded into dense vector representations
- These embeddings are used as input for a LinearSVC classifier

This method captures **global semantic information**.

---

### 3. SBERT + LinearSVC

- Sentence embeddings generated using SBERT
- Long texts are split into chunks (max 512 tokens)
- Embeddings are aggregated (mean pooling)

This approach captures **contextual semantic representations**, but requires handling long documents carefully.

---

## Results

| Model                     | Accuracy | F1-score (macro) |
|--------------------------|----------|------------------|
| TF-IDF + LinearSVC       | 0.965    | 0.955            |
| Doc2Vec + LinearSVC      | 0.940    | 0.923            |
| SBERT + LinearSVC        | 0.890    | 0.850            |

Key findings:

- TF-IDF achieves the best performance
- More complex models (Doc2Vec, SBERT) do not outperform simpler methods

---

## Key Insights

- Political text classification is strongly driven by **word usage**
- Semantic embeddings do not necessarily improve performance in this context
- Handling **long documents** is a central challenge
- Model complexity does not guarantee better results
