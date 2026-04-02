# Evaluation Metrics: Technical Details

> **Paper**: Evaluating translation performance of large language models in maritime legal translation  
> **Journal**: *Perspectives: Studies in Translation Theory and Practice*  
> **Authors**: Shijie Liu & Yan Zhang

This document provides detailed technical descriptions of the three automated evaluation metrics used in this study, as well as the specific parameter settings for their implementation. These details supplement Sections 3.3 and 3.4 of the main paper.

---

## 1. Evaluation Metrics Overview

Three model-based metrics were selected for their semantic focus and robustness: **BERTScore** (Zhang et al., 2019), **BLEURT** (Sellam et al., 2020), and **COMET** (Rei et al., 2020). These metrics, built on pre-trained models and demonstrating better correlation with human judgment in recent metrics shared tasks (Freitag et al., 2021), have been widely applied across multiple evaluation scenarios, including machine translation quality assessment (Kocmi et al., 2021; Glushkova et al., 2023; Liu, 2024), text generation evaluation (Liu et al., 2023; Es et al., 2024), and text summarization (Bhandari et al., 2020; Zhang et al., 2024b). The broad application and proven effectiveness of these model-based evaluation metrics across diverse natural language processing tasks support their selection for this study.

### 1.1 BERTScore

BERTScore utilizes pre-trained BERT models and their variants (such as RoBERTa, XLNet) to obtain contextual word embedding vector representations of reference and generated texts (Zhang et al., 2019). By calculating the cosine similarity between high-dimensional embedding vectors of each word in the reference and generated texts, it evaluates their semantic similarity. This metric does not require exact word form matching, supports IDF-based word weighting, and demonstrates strong robustness in noise resistance and synonym recognition, showing high correlation with human evaluation.

### 1.2 BLEURT

BLEURT is a learned evaluation metric based on the pre-trained BERT language model, adding additional linear layers to the BERT model and fine-tuning on task-specific human-annotated data (Sellam et al., 2020). To enhance model robustness and generalization ability, researchers used millions of Wikipedia articles, generating synthetic data (reference text–candidate text pairs) through mask filling and back-translation for pre-training. Experiments show that pre-training can significantly improve model performance when training data is scarce or unevenly distributed. BLEURT has demonstrated excellent performance and few-shot learning capabilities in WMT 2017–2019 shared tasks and WebNLG text generation tasks.

### 1.3 COMET

COMET is a neural network-based machine translation evaluation metric, employing pre-trained multilingual encoder models to evaluate translation quality through independent encoding of source language sentences, candidate translations, and reference translations (Rei et al., 2020). It includes two model architectures: an "Estimator" that directly regresses human scores and "Translation Ranking" trained by minimizing the distance between "good" translations and source/reference texts. All models are based on the pre-trained XLM-RoBERTa encoder and fine-tuned on human-annotated data. In the WMT 2019 shared tasks, COMET achieved best performance across all translation directions with English as the target language, particularly showing good discriminative ability in ranking high-quality machine translation systems.

---

## 2. Related Metrics (Not Used in This Study)

The following metrics are mentioned in the main paper for contextual comparison but were **not** used as primary evaluation metrics in this study:

- **FLORES-200**: A multilingual evaluation benchmark comprising 204 languages for assessing machine translation quality (NLLB Team et al., 2022).

- **BLEU** (Bilingual Evaluation Understudy): Measures n-gram overlap between machine and reference translations (Papineni et al., 2002).

- **chrF**: Character-level F-score metric focusing on character n-gram matches (Popović, 2015).

- **TER** (Translation Error Rate): Measures the minimum number of edits needed to transform a machine translation output into the reference translation (Snover et al., 2006).

---

## 3. Evaluation Parameter Settings

The implementation of the selected evaluation metrics requires specification of technical parameters that determine how each metric processes the translation data.

### 3.1 BERTScore Parameters

| Parameter | E2C Direction | C2E Direction |
|-----------|--------------|---------------|
| **Pre-trained model** | `bert-base-chinese` | `microsoft/deberta-xlarge-mnli` |
| **IDF weighting** | Enabled | Enabled |
| **Batch size** | 64 | 64 |
| **Library** | `bert_score` | `bert_score` |

These models serve as the computational foundation for understanding semantic relationships in each language. Scores (precision, recall, F1 score) were computed using the `bert_score` library:

- **Precision**: Measures how much of the generated translation is semantically correct.
- **Recall**: Measures how much of the reference translation is captured.
- **F1 Score**: Provides a balanced measure combining precision and recall.

### 3.2 BLEURT Parameters

| Parameter | Value |
|-----------|-------|
| **Model checkpoint** | BLEURT-20 |
| **Parameters** | 579M |
| **Base model** | BERT-large |
| **Fine-tuning data** | WMT news datasets |

BLEURT-20 is a general BLEURT model checkpoint released by Google, fine-tuned on WMT news datasets based on BERT-large, suitable for evaluating texts across different domains. This pre-trained evaluation model functions as a learned quality assessor that applies patterns from extensive translation evaluation training to new texts.

### 3.3 COMET Parameters

| Parameter | Value |
|-----------|-------|
| **Model checkpoint** | `wmt22-comet-da/model.ckpt` |
| **Tokenizer** | `XLM-RoBERTa-large` |
| **Architecture** | Estimator |
| **Input** | Source sentence + candidate translation + reference translation |

This model adopts the "Estimator" architecture, which utilizes information from source sentences, candidate translations, and reference translations. The "Estimator" architecture extracts combined features from the three inputs through independent encoding, then uses a feed-forward regressor to directly predict human quality scores. During inference, this model outputs a quality score representing the overall translation quality relative to both source and reference.

---

## References

- Bhandari, M., Gour, P., Ashfaq, A., Liu, P., & Neubig, G. (2020). Re-evaluating evaluation in text summarization. *arXiv*. https://arxiv.org/pdf/2010.07100
- Es, S., James, J., Anke, L. E., & Schockaert, S. (2024). Ragas: Automated evaluation of retrieval augmented generation. In *Proceedings of EACL 2024: System Demonstrations* (pp. 150–158).
- Freitag, M., Rei, R., Mathur, N., et al. (2021). Results of the WMT21 metrics shared task. In *Proceedings of WMT 2021* (pp. 733–774).
- Glushkova, T., Zerva, C., & Martins, A. F. (2023). BLEU meets COMET: Combining lexical and neural metrics towards robust machine translation evaluation. *arXiv*. https://arxiv.org/pdf/2305.19144
- Kocmi, T., Federmann, C., et al. (2021). To ship or not to ship: An extensive evaluation of automatic metrics for machine translation. *arXiv*. https://arxiv.org/pdf/2107.10821
- Liu, S. (2024). Evaluating the application efficacy of machine translation in maritime contexts. *Journal of Ocean University of China (Social Sciences)*, (2), 21–31.
- Liu, Y., Iter, D., Xu, Y., et al. (2023). G-eval: NLG evaluation using GPT-4 with better human alignment. *arXiv*. https://arxiv.org/pdf/2303.16634
- NLLB Team et al. (2022). No language left behind: Scaling human-centered machine translation. *arXiv*. https://arxiv.org/abs/2207.04672
- Papineni, K., Roukos, S., Ward, T., & Zhu, W.-J. (2002). BLEU: A method for automatic evaluation of machine translation. In *Proceedings of ACL 2002* (pp. 311–318).
- Popović, M. (2015). chrF: Character n-gram F-score for automatic MT evaluation. In *Proceedings of WMT 2015* (pp. 392–395).
- Rei, R., Stewart, C., Farinha, A. C., & Lavie, A. (2020). COMET: A neural framework for MT evaluation. *arXiv*. https://arxiv.org/abs/2009.09025
- Sellam, T., Das, D., & Parikh, A. P. (2020). BLEURT: Learning robust metrics for text generation. *arXiv*. https://arxiv.org/abs/2004.04696
- Snover, M., Dorr, B., Schwartz, R., et al. (2006). A study of translation edit rate with targeted human annotation. In *Proceedings of AMTA 2006* (pp. 223–231).
- Zhang, T., Kishore, V., Wu, F., et al. (2019). BERTScore: Evaluating text generation with BERT. *arXiv*. https://arxiv.org/abs/1904.09675
- Zhang, T., Ladhak, F., Durmus, E., et al. (2024b). Benchmarking large language models for news summarization. *Transactions of the ACL*, 12, 39–57.
