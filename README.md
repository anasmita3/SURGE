
# Intrinsic Evaluation of Corpora and Script for Tokenization in Bangla

## Overview

This repository contains the implementation and experimental framework for the research project **"Intrinsic Evaluation of Corpora and Script for Tokenization in Bangla."**

The study presents a comprehensive intrinsic evaluation of three widely used subword tokenization algorithms across multiple Bangla corpus domains and script representations. We investigate how corpus composition, vocabulary size, and transliteration influence tokenizer behavior using several intrinsic evaluation metrics.

---

## Features

* Intrinsic evaluation of three tokenizers:

  * Byte Pair Encoding (BPE)
  * WordPiece
  * SentencePiece Unigram

* Comparison across three script representations:

  * Native Bangla
  * ISO 15919
  * ASCII Transliteration

* Evaluation on multiple corpus domains:

  * Literature
  * News
  * Social Media

* Mixed-domain experiments:

  * Literature + News
  * Literature + Social Media
  * News + Social Media
  * Literature + News + Social Media

* Vocabulary sizes ranging from **5,000 to 50,000**

* Quantitative and qualitative evaluation

---

## Repository Structure

.
├── data/
│   ├── literature/
│   ├── news/
│   ├── social_media/
│   ├── merged/
│
├── preprocessing/
│   ├── cleaning.ipynb
│   ├── transliteration.ipynb
│
├── tokenizers/
│   ├── bpe/
│   ├── wordpiece/
│   ├── unigram/
│
├── evaluation/
│   ├── metrics.py
│   ├── qualitative_analysis.ipynb
│
├── plots/
│
├── results/
│
└── README.md


---

## Dataset

Three publicly available Bangla corpora were used.

| Corpus       | Source                        |
| ------------ | ----------------------------- |
| Literature   | VACASPATI                     |
| News         | IndicCorpV2                   |
| Social Media | Bengali Cyberbullying Dataset |

Balanced mixed-domain corpora were additionally constructed for comparative evaluation.

---

## Experimental Pipeline


Raw Corpus
      │
      ▼
Cleaning & Normalization
      │
      ▼
90:10 Train/Test Split
      │
      ▼
Transliteration
(Bangla / ISO / ASCII)
      │
      ▼
Tokenizer Training
(BPE / WordPiece / Unigram)
      │
      ▼
Intrinsic Evaluation
      │
      ▼
Comparative Analysis

---

## Tokenizer Configuration

* Vocabulary Sizes


5000
10000
15000
20000
25000
30000
35000
40000
45000
50000


Training Parameters

* Minimum Frequency = 1
* No pretrained tokenizer
* Independent tokenizer trained for every experiment

---

## Evaluation Metrics

The following intrinsic metrics were computed.

* Out-of-Vocabulary Rate (OOV)
* Fertility
* Characters per Token (CPT)
* Compression Ratio
* Word Fragmentation Rate (WFR)
* Token Length Variance

Additionally, qualitative morphological segmentation analysis was performed.

---

## Major Findings

* BPE consistently produced the most compact tokenization.

* Increasing vocabulary size reduced segmentation fragmentation for all tokenizers.

* Corpus composition influenced tokenizer behavior more strongly than script representation.

* Mixed-domain corpora generated more representative vocabularies.

* ISO 15919 and ASCII transliterations exhibited nearly identical intrinsic performance.

* WordPiece and SentencePiece preserved meaningful morphological boundaries, while BPE achieved the most compact segmentation.

---

## Technologies Used

* Python

* Hugging Face Tokenizers

* SentencePiece

* Aksharamukha

* NumPy

* Matplotlib

* Google Colab

---

## Citation

If you use this repository, please cite:

```
Anasmita Bhattacharya,
Srinidhi Balasubramanian,
Arnab Bhattacharya.

Intrinsic Evaluation of Corpora and Script for Tokenization in Bangla.
2025.
```

---

## Acknowledgements

This work was carried out under the **Summer Undergraduate Research Grant for Excellence (SURGE) 2025** at the **Indian Institute of Technology Kanpur**. We sincerely thank **Prof. Arnab Bhattacharya** for his invaluable guidance, continuous support, and insightful discussions throughout the project. We also acknowledge the Department of Computer Science and Engineering, IIT Kanpur, for providing an excellent research environment, as well as the developers and maintainers of the publicly available datasets and open-source tools used in this study.

---

## License

This project is intended for academic and research purposes. Please cite the associated publication if you build upon this work.

