# Handling Non-Normal Data in Hypothesis Testing
## If your data is not normally distributed, you have several options:

1. Check if the Central Limit Theorem (CLT) Applies
</br>If the sample size is large (typically >30 per group), the CLT suggests that the sample mean distribution will be approximately normal, and you can still use parametric tests like the t-test.

2. Use Non-Parametric Tests  
</br>If the sample size is small and normality is uncertain, use non-parametric tests that don’t assume normality:
    - Mann-Whitney U Test (Wilcoxon Rank-Sum Test) – for comparing two independent groups.
    - Wilcoxon Signed-Rank Test – for paired data (before/after scenarios).
    - Kolmogorov-Smirnov (KS) Test – for comparing distributions.
      
3. Apply Data Transformations
</br>If the data is skewed, you can transform it to approximate normality:
    - Log transformation (if data is right-skewed, e.g., revenue, time on page).
    - Square root transformation (for count data).
    - Box-Cox transformation (more general).
      
4. Use Bootstrapping
</br>Resample the data with replacement to estimate the distribution of the test statistic without assuming normality.
</br>This works well when comparing means or medians.

5. Use Generalized Linear Models (GLMs)
</br>If the data follows a specific distribution (e.g., Poisson for counts, binomial for conversion rates), use regression-based approaches like Poisson regression or logistic regression.

# When to Use Bayesian A/B Testing Instead of Frequentist?
## A Bayesian A/B test is preferable when:

1. You Need Continuous Monitoring Without P-Hacking
    - Frequentist tests require a fixed sample size and can suffer from peeking issues (increasing false positives if checked mid-experiment).
    - Bayesian methods update beliefs continuously, allowing for early stopping when confidence is high.
2. You Want Probabilistic Interpretations
    - Frequentist p-values only tell you whether the result is significant but don’t quantify how likely one variant is better.
    - Bayesian A/B testing provides posterior probabilities, e.g., “There is a 95% probability that Version B is better than A by at least 2%.”
3. You Have Small Sample Sizes
    - Bayesian methods incorporate prior knowledge, making them more robust when data is limited.
    - Frequentist tests require large samples to achieve reliable statistical power.
4. Dealing with Skewed or Heavy-Tailed Data
    - If your data is not normally distributed, Bayesian approaches are more flexible since they don’t rely on assumptions like normality or equal variances.
5. Handling Business Risk and Decision-Making
    - If the cost of a wrong decision is high, Bayesian approaches allow incorporating prior business knowledge to guide decisions.
    - Instead of a hard significance threshold (e.g., p < 0.05), Bayesian methods let you set decision rules, like "Proceed if B is at least 90% likely to be better."

## When to Stick with Frequentist A/B Testing?
- If you need a simple, standardized approach without prior assumptions.
- If decision-makers are familiar with traditional p-values and confidence intervals.
- If you have a large dataset and can run a fixed-duration test without peeking.
