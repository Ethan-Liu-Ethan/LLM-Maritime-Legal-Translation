# Statistical Glossary

> **Paper**: Evaluating translation performance of large language models in maritime legal translation  
> **Journal**: *Perspectives: Studies in Translation Theory and Practice*  
> **Authors**: Shijie Liu & Yan Zhang

This document provides definitions and explanations of statistical terms and concepts used in the quantitative analysis sections (Sections 4.1.1–4.1.3) of the main paper.

---

## 1. Correlation Analysis Terms

### Spearman Rank Correlation Coefficient (ρ)

**ρ** (rho) denotes the Spearman rank correlation coefficient, which measures the strength and direction of a **monotonic relationship** between two variables. Unlike Pearson's correlation, it does not assume a linear relationship or normal distribution, making it suitable for non-normally distributed data.

- **ρ = 1.0**: Perfect positive monotonic relationship
- **ρ = 0**: No monotonic relationship
- **ρ = −1.0**: Perfect negative monotonic relationship

> **Note**: ρ (rho) is distinct from *p*, which represents the statistical significance (p-value) of a test.

### p-value

The **p-value** indicates the probability of observing the test results (or more extreme results) under the null hypothesis. In this study:

- **p < 0.001**: Indicates a highly significant result; the observed relationship or difference is very unlikely due to chance alone.

---

## 2. Distribution Analysis Terms

### Skewness

**Skewness** is a statistical measure that describes the asymmetry of a data distribution.

- **Negative skewness** (< 0): Distribution is skewed to the right, with data concentrated around higher values, and a long tail extending toward lower values.
- **Positive skewness** (> 0): Distribution is skewed to the left, with data concentrated around lower values, and a long tail extending toward higher values.
- **Zero skewness** (= 0): A perfectly symmetrical distribution, such as the normal distribution.

### Kurtosis

**Kurtosis** measures the steepness or "tailedness" of a data distribution.

- **Positive kurtosis** (> 0): Distribution is steeper (more peaked) than the normal distribution, with heavier tails — meaning more extreme values.
- **Negative kurtosis** (< 0): Distribution is flatter than the normal distribution, with lighter tails — meaning fewer extreme values.
- **Zero kurtosis** (= 0): Corresponds to the steepness of a normal distribution.

### Interquartile Range (IQR)

The **IQR** is the range between the 25th percentile (Q1) and the 75th percentile (Q3) of a data distribution. It captures the middle 50% of data points and is a robust measure of variability that is not influenced by outliers.

### Standard Deviation (SD)

**Standard deviation** measures the average amount of dispersion or spread in a dataset. A lower SD indicates that data points tend to be closer to the mean.

---

## 3. Stability Analysis Terms

### Coefficient of Variation (CV)

The **Coefficient of Variation** (CV) is a standardized measure of dispersion, calculated as the ratio of the standard deviation to the mean, expressed as a percentage:

$$CV = \frac{SD}{\bar{x}} \times 100\%$$

Following statistical practices in quantitative assay analysis (Reed et al., 2002):

| CV Range | Stability Level |
|----------|----------------|
| CV ≤ 10% | **High stability** |
| 10% < CV ≤ 20% | **Medium stability** |
| CV > 20% | **Low stability** |

---

## 4. Hypothesis Testing Terms

### Shapiro-Wilk Test

The **Shapiro-Wilk test** (Shapiro & Wilk, 1965) assesses whether a data sample comes from a normally distributed population. It produces a test statistic **W**, where:

- **W close to 1**: Data are consistent with a normal distribution.
- **W significantly less than 1** (with p < 0.05): Data deviate from normality.

In this study, the Shapiro-Wilk test was used to determine the appropriate correlation and comparison methods (parametric vs. non-parametric).

### Levene's Test

**Levene's test** (Brown & Forsythe, 1974) assesses the equality of variances across groups (variance homogeneity). It is robust for non-normal data. A significant result (p < 0.05) indicates that variances differ significantly between groups, which influences the choice of subsequent statistical tests.

### Kruskal-Wallis H Test

The **Kruskal-Wallis H test** (Kruskal & Wallis, 1952) is a non-parametric alternative to one-way ANOVA, used to compare medians among three or more independent groups when data do not meet normality or variance homogeneity assumptions.

- **H statistic**: A larger value indicates greater differences among groups.
- **Degrees of freedom**: Number of groups minus one — in this study, df = 7 (for 8 LLMs).

### Dunn's Post-hoc Test with Bonferroni Correction

**Dunn's test** (Dunn, 1961) is used after a significant Kruskal-Wallis test to identify which specific group pairs differ significantly. The **Bonferroni correction** adjusts p-values for multiple comparisons to control the Type I error rate (false positives).

- For *k* groups, the number of pairwise comparisons is $\frac{k(k-1)}{2}$.
- Adjusted significance threshold: $\alpha / \frac{k(k-1)}{2}$.

---

## References

- Brown, M. B., & Forsythe, A. B. (1974). Robust tests for the equality of variances. *Journal of the American Statistical Association*, 69(346), 364–367.
- Dunn, O. J. (1961). Multiple comparisons among means. *Journal of the American Statistical Association*, 56(293), 52–64.
- Kruskal, W. H., & Wallis, W. A. (1952). Use of ranks in one-criterion variance analysis. *Journal of the American Statistical Association*, 47(260), 583–621.
- Reed, G. F., Lynn, F., & Meade, B. D. (2002). Use of coefficient of variation in assessing variability of quantitative assays. *Clinical and Diagnostic Laboratory Immunology*, 9(6), 1235–1239.
- Shapiro, S. S., & Wilk, M. B. (1965). An analysis of variance test for normality (complete samples). *Biometrika*, 52(3/4), 591–611.
