# Intrinsic Evaluation of Corpora and Script Representations for Bangla Tokenization

## Overview

This repository presents a systematic intrinsic evaluation of Bangla subword tokenization across multiple corpus domains and corpus combinations. The study investigates how corpus composition and script representation influence tokenization quality in Bangla.

The experiments are conducted on:

* News text
* Literary text
* Social media text
* Pairwise combinations of these domains
* A balanced three-domain corpus

Each corpus is evaluated in:

* Native Bengali script
* ISO transliterated representation generated using Aksharamukha

Three tokenization algorithms are trained and evaluated:

* Byte Pair Encoding (BPE)
* WordPiece
* Unigram Language Model

Vocabulary sizes range from 5,000 to 50,000 tokens.

---

# Motivation

Tokenization plays a critical role in modern NLP systems, particularly for morphologically rich languages such as Bangla.

Most tokenizer studies focus on:

* English
* Multilingual corpora
* Downstream task performance

However, little work examines:

* The influence of corpus domain on Bangla tokenization
* The effect of script transformation
* Tokenizer behavior across heterogeneous Bangla corpora

This repository addresses those questions through a large-scale intrinsic evaluation framework.

---

# Research Questions

This project investigates:

1. How does corpus domain affect tokenization quality?

2. Does ISO transliteration improve tokenization efficiency compared to native Bengali script?

3. Which tokenizer performs best for Bangla?

4. How does vocabulary size influence tokenization quality?

5. Do mixed-domain corpora produce more robust tokenizers than single-domain corpora?

---

# Datasets

## Literature Corpus

Source:

* Vacaspati literary corpus

Contains:

* Novels
* Stories
* Essays
* Literary writings

---

## News Corpus

Source:

* IndicCorpV2 Bengali corpus

Contains:

* News reports
* Editorial content
* Contemporary formal language

---

## Social Media Corpus

Source:

* Bangla cyberbullying / social media comments dataset

Contains:

* Informal language
* User-generated content
* Noisy spellings
* Slang expressions

---

# Experimental Design

Seven separate experiments were performed.

## Single-Domain Experiments

### SURGE_2.ipynb

News Corpus

### SURGE_3.ipynb

Literature Corpus

### SURGE_5.ipynb

Social Media Corpus

---

## Dual-Domain Experiments

### SURGE_4.ipynb

News + Literature

### SURGE_6.ipynb

News + Social Media

### SURGE_7.ipynb

Literature + Social Media

---

## Multi-Domain Experiment

### SURGE_8.ipynb

News + Literature + Social Media

Balanced corpus:

* 125,000 news documents
* 125,000 literature documents
* 125,000 social media documents

Total:

* 375,000 documents

---

# Processing Pipeline

Each notebook follows the same workflow.

## Step 1: Data Collection

Domain-specific corpus acquisition and cleaning.

## Step 2: Text Normalization

* Unicode NFC normalization
* Whitespace normalization
* Empty document removal

## Step 3: Corpus Statistics

Computed statistics include:

* Number of documents
* Character count
* Word count
* Vocabulary size
* Type-Token Ratio (TTR)
* Average word length

## Step 4: Transliteration

Bengali → ISO

using:

Aksharamukha transliteration framework.

## Step 5: Transliteration Validation

Round-trip evaluation:

Bengali → ISO → Bengali

Metrics:

* Exact Match Accuracy
* Expansion Factor
* Vocabulary Ratio

## Step 6: Train-Test Split

Typical split:

* 90% training
* 10% testing

## Step 7: Tokenizer Training

For each script:

* Bengali
* ISO

For each tokenizer:

* BPE
* WordPiece
* Unigram

For each vocabulary size:

* 5k
* 10k
* 15k
* 20k
* 25k
* 30k
* 35k
* 40k
* 45k
* 50k

---

# Evaluation Metrics

## OOV Rate

Percentage of unknown words.

Lower is better.

---

## Fertility

Average number of tokens produced per word.

Lower values indicate more compact tokenization.

---

## Characters per Token (CPT)

Average number of characters represented by each token.

Higher values indicate better compression.

---

## Compression Ratio

Measures tokenization compactness.

Higher values are preferred.

---

## Word Fragmentation Rate (WFR)

Measures the degree of word splitting.

Lower values indicate better preservation of word structure.

---

## Token Length Variance

Measures segmentation consistency.

Lower values indicate more stable tokenization behavior.

---

# Main Findings

Across all experiments, several consistent patterns emerge.

## 1. ISO Representation Improves Compression

ISO-transliterated text consistently achieves:

* Higher CPT
* Better compression
* Comparable fertility

than native Bengali script.

---

## 2. BPE Performs Best Overall

Across nearly all corpora:

BPE > WordPiece > Unigram

for:

* CPT
* Fertility
* WFR
* Compression

---

## 3. Vocabulary Growth Shows Diminishing Returns

Performance improves rapidly between:

5k → 30k

After approximately:

30k–40k

the gains become relatively small.

---

## 4. Mixed-Domain Corpora Produce More Balanced Behavior

Single-domain corpora exhibit domain-specific tokenization patterns.

Mixed-domain corpora:

* Improve vocabulary coverage
* Reduce domain bias
* Produce more general-purpose tokenizers

---

## 5. Social Media Is the Most Challenging Domain

Compared with literature and news:

* Higher lexical variability
* Greater spelling variation
* More fragmented tokenization

This results in lower compression efficiency.

---

# Repository Structure

```text
SURGE/
│
├── SURGE_2.ipynb
│   └── News Corpus Evaluation
│
├── SURGE_3.ipynb
│   └── Literature Corpus Evaluation
│
├── SURGE_4.ipynb
│   └── News + Literature Evaluation
│
├── SURGE_5.ipynb
│   └── Social Media Evaluation
│
├── SURGE_6.ipynb
│   └── News + Social Media Evaluation
│
├── SURGE_7.ipynb
│   └── Literature + Social Media Evaluation
│
├── SURGE_8.ipynb
│   └── News + Literature + Social Media Evaluation
│
└── README.md
```

---

# Software and Libraries

* Python
* Hugging Face Datasets
* Tokenizers
* SentencePiece
* Aksharamukha
* NumPy
* Pandas
* Matplotlib

---

# Future Work

Potential extensions include:

* Extrinsic evaluation on downstream NLP tasks
* Language modeling experiments
* Morphology-aware tokenization
* Cross-script tokenization studies
* Bangla LLM pretraining analysis
* Comparison with Indic multilingual tokenizers

---


