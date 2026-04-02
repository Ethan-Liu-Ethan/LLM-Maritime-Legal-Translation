# Figure and Table Annotations

> **Paper**: Evaluating translation performance of large language models in maritime legal translation  
> **Journal**: *Perspectives: Studies in Translation Theory and Practice*  
> **Authors**: Shijie Liu & Yan Zhang

This document provides detailed reading guides for the figures and tables presented in the main paper (Section 4).

---

## Table 1. Average Scores of LLMs on BLEURT and COMET Metrics

**Location in paper**: Section 4.1.1

This table reports the mean scores (± standard deviation) of eight LLMs across two evaluation metrics (BLEURT and COMET) in both translation directions (E2C and C2E), based on 1,000 sentence pairs per direction.

**How to read**:
- Each cell contains `mean ± SD`, where the mean represents average translation quality and SD indicates score variability.
- Higher scores indicate better translation quality.
- BLEURT scores range from approximately 0 to 1; COMET scores also typically range from 0 to 1.

---

## Table 2. Average Scores of LLMs on BERTScore Metrics

**Location in paper**: Section 4.1.1

This table reports the BERTScore results (Precision, Recall, and F1 Score) for each of the eight LLMs in both translation directions.

**How to read**:
- **P_BERT (Precision)**: Measures how much of the generated translation is semantically correct relative to the reference.
- **R_BERT (Recall)**: Measures how much of the reference translation's meaning is captured in the generated translation.
- **F_BERT (F1 Score)**: The harmonic mean of precision and recall, providing a balanced overall measure.
- Values range from 0 to 1, with higher values indicating better performance.

---

## Figure 1. Spearman Correlation Matrix of Metrics

**Location in paper**: Section 4.1.1

This figure displays a heatmap showing the Spearman rank correlation coefficients (ρ) between the three evaluation metrics (BERTScore F1, BLEURT, and COMET) for both translation directions.

**How to read**:
- **Cell color** represents the Spearman correlation coefficient (ρ) between two metrics.
- **The color bar** (legend) indicates the mapping from color to coefficient value.
- Darker/warmer colors typically indicate stronger positive correlations.
- Values closer to **1.0** indicate that two metrics rank the translations in very similar order.
- The matrix is symmetric — the upper and lower triangles mirror each other.

**Key findings**:
- E2C direction (n = 8,000): COMET–BLEURT show the highest correlation (ρ = 0.77).
- C2E direction (n = 8,000): BLEURT–COMET again show the highest correlation (ρ = 0.76).
- BLEURT was selected as the primary metric based on its consistently high correlations with both other metrics.

---

## Figure 2. Score Distributions of LLMs in E2C and C2E Directions

**Location in paper**: Section 4.1.2

This figure displays the overall score distributions of all LLMs in both translation directions using histograms or density plots.

**How to read**:
- The x-axis represents BLEURT scores.
- The y-axis represents the frequency or density of scores.
- **E2C direction**: Shows high negative skewness (−0.98) and kurtosis (2.70) — scores are concentrated in higher ranges with a long tail toward lower values.
- **C2E direction**: Shows milder negative skewness (−0.34) and near-zero kurtosis (0.01) — a more symmetrical, flatter distribution.

---

## Figure 3. Score Comparison of LLMs in E2C and C2E Directions

**Location in paper**: Section 4.1.2

This figure uses **box plots** to compare the score distributions of individual LLMs across both translation directions.

**How to read box plots**:
- **Center line**: Median score (50th percentile).
- **Box edges**: 25th percentile (Q1, bottom edge) and 75th percentile (Q3, top edge).
- **Whiskers**: Extend to the most extreme data points within 1.5 × IQR from the box edges.
- **Individual dots**: Outlier data points beyond the whiskers.
- **Box width (IQR)**: Represents the spread of the middle 50% of scores — narrower boxes indicate more consistent performance.

---

## Figure 4. Pairwise Comparison Results of LLMs' Translation Performance Based on Dunn's Test

**Location in paper**: Section 4.1.3

This figure displays a heatmap of pairwise comparison p-values from Dunn's post-hoc test with Bonferroni correction.

**How to read**:
- **Cell color** represents the statistical significance (p-value) of differences between two models.
- **The color bar** indicates the mapping from color to p-value.
- **Larger p-values** (lighter colors): Less significant differences — the two models perform similarly.
- **Smaller p-values** (darker colors): More significant differences — the two models perform differently.
- **p < 0.05**: Conventionally considered statistically significant.
- **p = 0.0000**: Highly significant difference.
- The matrix is symmetric.

---

## Figure 5. Repeated Evaluation Sentence IDs (Sankey Diagram)

**Location in paper**: Section 4.2

This Sankey diagram visualizes which specific test sentences repeatedly appeared among the top 10 and bottom 10 scores across different LLMs.

**How to read**:
- **First column (burgundy)**: Sentence IDs that repeatedly appeared among the **top 10** highest-scoring translations.
- **Third column (cyan)**: Sentence IDs that repeatedly appeared among the **bottom 10** lowest-scoring translations.
- **Flow width**: Indicates the frequency of a sentence appearing in the top/bottom 10 across models.
- Sentences appearing frequently across multiple models' top/bottom lists suggest consistent strengths or challenges shared by LLMs.
