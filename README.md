# Observations

## 1. Corpus Characteristics

The mixed corpus was created by combining equal portions of the news and literature datasets, resulting in a corpus containing 250,000 documents. The corpus contains 8.39 million words and a vocabulary of 671,371 unique word forms. The Type-Token Ratio (TTR) of 0.0800 lies between that of the news corpus (0.0621) and literature corpus (0.0933), indicating that the lexical diversity of the mixed corpus is intermediate between the two domains. Similarly, the average word length of 6.37 characters also falls between the values observed for news and literature data.

These statistics suggest that the mixed corpus successfully captures characteristics of both formal news writing and literary language, making it a suitable benchmark for evaluating tokenizer behavior across heterogeneous domains.

---

## 2. Effect of Transliteration

The Bengali corpus was transliterated into ISO format using the Aksharamukha transliteration framework. The transliterated corpus exhibited an expansion factor of 1.162, indicating that ISO representations require approximately 16.2% more characters than the original Bengali script. This increase is expected because several Bengali characters are represented by multiple Latin characters in ISO transliteration.

Despite the increase in character count, the vocabulary ratio between the ISO and Bengali versions remained relatively stable (0.962), suggesting that transliteration primarily changes orthographic representation rather than lexical content. The transliterated corpus therefore provides a useful alternative script representation while preserving the linguistic information present in the original corpus.

---

## 3. Impact of Vocabulary Size

Across all tokenization schemes, increasing the vocabulary size from 5,000 to 50,000 consistently improved tokenization efficiency. Fertility decreased steadily as vocabulary size increased, indicating that words were represented using fewer subword units. At the same time, Characters Per Token (CPT) increased, implying that learned tokens became longer and more semantically meaningful.

Word Fragmentation Rate (WFR) also decreased substantially with larger vocabularies, demonstrating that fewer words required decomposition into multiple subword segments. The reduction in token-count variance further suggests that tokenization became more stable and consistent across documents as the vocabulary size expanded.

These observations confirm the expected trade-off between vocabulary size and segmentation granularity: larger vocabularies reduce fragmentation and improve compression at the cost of increased model size.

---

## 4. Comparison of Tokenization Algorithms

### Bengali Script

For the Bengali corpus at a vocabulary size of 50,000, BPE achieved the lowest fertility (1.3186), the highest CPT (4.0728), and the lowest WFR (0.2420). WordPiece achieved slightly inferior performance, while Unigram produced the highest fertility and fragmentation among the three methods.

The ranking of tokenizer performance was:

BPE > WordPiece > Unigram

for all major efficiency metrics.

### ISO Script

A similar pattern was observed for the ISO-transliterated corpus. BPE again achieved the lowest fertility (1.3201) and WFR (0.2404), while WordPiece and Unigram followed in descending order of efficiency.

The consistency of these results across both scripts suggests that BPE is the most effective tokenizer among the evaluated approaches for Bengali-language text.

---

## 5. Influence of Transliteration on Tokenization

Comparing Bengali and ISO tokenization results reveals only minor differences in segmentation behavior. For example, at a vocabulary size of 50,000, Bengali BPE achieved a fertility of 1.3186, while ISO BPE achieved a fertility of 1.3201. Similar negligible differences were observed for WordPiece and Unigram.

Although transliteration increased character counts and CPT values, it did not significantly affect fertility or fragmentation rates. This suggests that tokenizer efficiency is influenced more strongly by lexical diversity and corpus characteristics than by the choice of script representation.

---

## 6. Cross-Domain Comparison

When compared with the previously evaluated news and literature corpora, the mixed corpus consistently produced intermediate results. For example, under BPE with a vocabulary size of 50,000:

| Domain | Fertility | CPT | WFR |
|----------|----------|----------|----------|
| News | 1.2745 | 4.3877 | 0.2102 |
| Mixed | 1.3186 | 4.0728 | 0.2420 |
| Literature | 1.3454 | 3.7880 | 0.2698 |

The same trend was observed across WordPiece and Unigram tokenizers. This behavior closely mirrors the lexical diversity measurements of the three corpora, where news exhibited the lowest TTR, literature the highest, and the mixed corpus occupied an intermediate position.

These findings indicate that lexical diversity has a direct influence on tokenization difficulty. As lexical diversity increases, fertility and fragmentation increase while compression efficiency decreases.

---

## 7. Overall Findings

The experimental results demonstrate that tokenizer performance is strongly influenced by both vocabulary size and corpus characteristics. Larger vocabularies consistently improve tokenization efficiency by reducing fragmentation and increasing token compactness. Among the evaluated tokenization methods, BPE consistently outperformed WordPiece and Unigram across all domains and scripts.

Furthermore, transliteration into ISO script had only a marginal effect on tokenization efficiency, suggesting that domain-specific lexical variation plays a substantially larger role than script representation. Finally, the mixed corpus behaved predictably between the news and literature domains, providing further evidence that lexical diversity is a key factor governing subword tokenization behavior.
