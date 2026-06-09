# Intrinsic Evaluation of Corpora and Script for Tokenization in Bangla

## Overview

This repository contains the experimental framework, datasets, and analysis developed for the study:

**"Intrinsic Evaluation of Corpora and Script for Tokenization in Bangla"**

The objective of this work is to investigate how textual domain, script representation, vocabulary size, and tokenizer design influence subword tokenization behavior in Bangla. The study evaluates three widely used subword tokenization algorithms across multiple corpora and script representations using intrinsic evaluation metrics and qualitative morphological analysis.

---

## Research Questions

This study addresses the following questions:

1. How does textual domain influence tokenization quality?
2. Does script representation affect subword segmentation behavior?
3. Which tokenizer performs best for Bangla text?
4. How does vocabulary size influence segmentation quality?
5. Do tokenizer-generated subwords align with linguistic and morphological boundaries?

---

## Datasets

Four corpora were evaluated:

### 1. News Corpus

A formal-domain corpus consisting of Bangla news articles.

### 2. Literature Corpus

A corpus containing literary texts including novels, stories, and other creative writing.

### 3. Mixed Corpus

A balanced combination of the News and Literature corpora, designed to represent heterogeneous language usage.

### 4. Social Media Corpus

A collection of user-generated Bangla social media comments containing informal language, spelling variation, colloquial expressions, and noisy text.

---

## Script Variants

Each corpus was evaluated in two script representations:

### Bengali Script

Native Bangla Unicode text.

### ISO 15919 Script

Romanized transliteration generated using the Aksharamukha framework.

The script comparison allows investigation of whether orthographic representation influences tokenization behavior while preserving identical linguistic content.

---

## Tokenization Methods

Three subword tokenization algorithms were evaluated:

### Byte Pair Encoding (BPE)

Frequency-based iterative merge algorithm.

### WordPiece

Likelihood-based subword segmentation algorithm widely used in transformer architectures.

### Unigram Language Model

Probabilistic tokenization approach that selects subword units using a language-model objective.

---

## Vocabulary Configurations

Each tokenizer was trained using the following vocabulary sizes:

```text
5,000
10,000
15,000
20,000
25,000
30,000
35,000
40,000
45,000
50,000
```

This enabled analysis of tokenizer behavior under different vocabulary constraints.

---

## Evaluation Metrics

Tokenizer quality was assessed using intrinsic evaluation metrics:

### Fertility

Average number of tokens generated per word.

Lower values indicate better segmentation efficiency.

### Characters per Token (CPT)

Average number of characters represented by each token.

Higher values indicate better compression.

### Word Fragmentation Ratio (WFR)

Proportion of words split into multiple subword units.

Lower values indicate more stable segmentation.

### Average Tokens per Sentence

Measures segmentation granularity at sentence level.

### Segmentation Variance

Measures consistency of tokenization across documents.

### Out-of-Vocabulary Rate (OOV)

Percentage of unseen words not adequately represented by the tokenizer.

---

## Morphological Analysis

A qualitative evaluation was performed using manually selected Bangla words divided into:

* Frequent words
* Medium-frequency words
* Rare words

Subword segmentations produced by BPE, WordPiece, and Unigram were analyzed to determine their conformity to morphological boundaries and linguistic plausibility.

---

## Key Findings

### 1. BPE Consistently Achieved the Best Performance

Across all domains and scripts, BPE produced:

* Lowest fertility
* Lowest fragmentation ratio
* Strong compression performance
* Most stable segmentation behavior

### 2. WordPiece Closely Followed BPE

WordPiece generally produced results comparable to BPE, though it consistently showed slightly higher fertility and fragmentation values.

### 3. Unigram Performed Worst Across Domains

Unigram generated:

* Higher fertility
* Higher fragmentation
* Lower compression

In several experiments, performance saturated around 30k vocabulary size, suggesting limited benefit from larger vocabularies.

### 4. Script Representation Influences Tokenization

ISO 15919 consistently produced:

* Higher CPT values
* Longer token representations
* Similar overall segmentation trends

This indicates that script representation affects tokenization characteristics even when linguistic content remains unchanged.

### 5. Domain Characteristics Matter

Tokenization behavior varied substantially across domains.

A particularly interesting finding was that the Social Media corpus achieved the lowest fertility values under BPE despite exhibiting the highest lexical diversity (TTR). This suggests that repetitive user-generated expressions allow effective subword learning even in highly diverse and noisy corpora.

---

## Reproducibility

The repository includes:

* Dataset preparation pipelines
* Transliteration workflows
* Tokenizer training scripts
* Intrinsic evaluation framework
* Morphological analysis experiments
* Result generation notebooks

All experiments were conducted using identical train/test splits and evaluation procedures across domains, scripts, tokenizers, and vocabulary sizes.

---

## Conclusion

This work presents a comprehensive intrinsic evaluation of Bangla tokenization across multiple domains and script representations. The results demonstrate that tokenizer choice, corpus characteristics, vocabulary size, and script representation all influence subword segmentation quality. Among the evaluated methods, BPE consistently provided the most effective balance between compression, segmentation efficiency, and morphological consistency, making it a strong candidate for future Bangla NLP applications.
