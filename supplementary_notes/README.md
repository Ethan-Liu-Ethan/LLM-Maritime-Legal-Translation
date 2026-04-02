# Supplementary Notes

This folder provides technical details, statistical explanations, figure/table reading guides, and LLM access information that complement the main paper. These materials were moved from the published article to this repository to meet journal word-length requirements while remaining accessible to readers seeking additional detail.

## Files

| File                                                        | Content                                                                                                                                                                                                             | Relevant Paper Sections |
| ----------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------- |
| [evaluation_metrics_details.md](evaluation_metrics_details.md) | Technical descriptions of BERTScore, BLEURT, and COMET; parameter settings for each metric; descriptions of related metrics (BLEU, chrF, TER, FLORES-200)                                                           | Sections 3.3 & 3.4      |
| [statistical_glossary.md](statistical_glossary.md)             | Definitions of statistical terms used in the quantitative analysis: Spearman's ρ, skewness, kurtosis, CV, Shapiro-Wilk test, Levene's test, Kruskal-Wallis H test, Dunn's post-hoc test with Bonferroni correction | Sections 4.1.1–4.1.3   |
| [figure_annotations.md](figure_annotations.md)                 | Reading guides for all figures (Figures 1–5) and tables (Tables 1–2) in the paper, including how to interpret heatmaps, box plots, distribution plots, and Sankey diagrams                                        | Section 4               |
| [LLM_access_links.md](LLM_access_links.md)                     | Official access links, developer information, and versioning notes for the eight LLMs evaluated in this study                                                                                                       | Section 3.2             |

## How to Use These Notes

- **For readers unfamiliar with quantitative research methods**: Start with [statistical_glossary.md](statistical_glossary.md) for terminology, then consult [figure_annotations.md](figure_annotations.md) when reading the results section.
- **For readers interested in replicating or extending the evaluation**: Refer to [evaluation_metrics_details.md](evaluation_metrics_details.md) for exact model checkpoints, parameter settings, and metric computation details.
- **For readers seeking to access the evaluated LLMs**: See [LLM_access_links.md](LLM_access_links.md) for direct links and access notes.

## Citation

If you use these materials, please cite the associated paper:

> Liu, S., & Zhang, Y. Evaluating translation performance of large language models in maritime legal translation. *Perspectives: Studies in Translation Theory and Practice*.
