---
Course:
  - PSYC10100 Introduction to Statistics for Psychological Sciences
---

## 1. Population Parameter & Sample Statistics

### 1.1. Why We Need Parameter Estimation

| Method         | Accuracy | Cost      | Time      | Practicality     |
| -------------- | -------- | --------- | --------- | ---------------- |
| **Census**     | Perfect  | Very High | Very Long | Often Impossible |
| **Estimation** | High     | Low       | Fast      | Usually Feasible |

Parameter estimation is fundamental to statistical inference because **complete population data is rarely available** in practice. Here are the key reasons why estimation is necessary:

#### 1.1.1. Practical Constraints

**Cost and Resource Limitations**:

- Conducting a census requires enormous financial resources
- Sampling reduces costs while maintaining reasonable accuracy
- Example: Surveying all 330 million Americans vs. a representative sample of 1,000

**Time Constraints**:

- Many research questions require timely answers
- Complete enumeration takes too long for decision-making
- Example: Election polling needs results before the election occurs

**Feasibility Issues**:

- Some populations are too large or dispersed to study completely
- Access to all population members may be impossible
- Example: Studying all ocean fish species worldwide

#### 1.1.2. Destructive Testing

When measurement destroys or alters the subject being studied:

- **Product testing**: Light bulb lifespan, crash testing cars
- **Medical research**: Drug efficacy trials, medical procedures
- **Quality control**: Testing food products, pharmaceutical batches

In these cases, testing the entire population would destroy the population itself.

#### 1.1.3. Infinite or Dynamic Populations

**Theoretical Infinity**:

- All possible coin flips or dice rolls
- Future customers or events
- Potential outcomes of an experiment

**Constantly Changing Populations**:

- Human populations (births, deaths, migration)
- Customer bases (new customers, churn)
- Social media users (new accounts, deletions)

#### 1.1.4. Accuracy vs. Efficiency Trade-off

While a census provides exact parameter values, well-designed estimation can achieve remarkable efficiency:

### 1.2. The Fundamental Statistical Problem

We face a fundamental gap in knowledge:

**What we want to know**: Population parameters ($\mu$, $\sigma$, $\pi$)
**What we can know**: Sample statistics ($\bar{x}$, $s$, $p$)

**Parameter estimation provides the mathematical bridge** between these two, allowing us to make reasonable inferences about populations based on samples.

### 1.3. Real-World Applications

**Scientific Research**:

- Estimating treatment effects in clinical trials
- Measuring environmental pollution levels
- Studying animal behavior patterns

**Business and Economics**:

- Market research and consumer preferences
- Quality control in manufacturing
- Economic indicators and forecasts

**Social Sciences**:

- Public opinion polling
- Educational achievement studies
- Health and wellness surveys

**Government and Policy**:

- Unemployment rate estimation
- Crime statistics
- Public health monitoring

### 1.4. The Role of Uncertainty

Because we work with samples rather than complete populations, **uncertainty is inherent** in parameter estimation. Statistical methods provide tools to:

- **Quantify uncertainty** through standard errors and confidence intervals
- **Manage uncertainty** through proper sampling design
- **Communicate uncertainty** to ensure proper interpretation of results

### 1.5. Key Insight

Parameter estimation transforms statistics from mere description to **inference** - allowing us to draw conclusions about populations based on limited sample data. This makes scientific research, business decision-making, and public policy formulation possible in a practical, cost-effective manner.

Through [*Sampling*](Population%20and%20Sample.md), researchers obtain a subset of the population, and through parameter estimation, they make informed inferences about the population characteristics.

## 2. Point Estimation

### 2.1. Sample Mean as Estimator

The sample mean $\bar{x}$ is the most common estimator for the population mean $\mu$. It's calculated as:

$$\bar{x} = \frac{\sum_{i=1}^{n} x_i}{n}$$

#### 2.1.1. Understanding Bias in Sample Mean

**Bias Definition**: An estimator is **unbiased** if its expected value equals the population parameter it's estimating:

$$E[\bar{x}] = \mu$$

**Proof of Unbiasedness**:

$$E[\bar{x}] = E\left[\frac{\sum_{i=1}^{n} x_i}{n}\right] = \frac{1}{n} \sum_{i=1}^{n} E[x_i] = \frac{1}{n} \sum_{i=1}^{n} \mu = \frac{n\mu}{n} = \mu$$

**Key Properties**:

1. **Unbiased**: On average across many samples, $\bar{x}$ equals $\mu$
2. **Consistent**: As sample size increases, $\bar{x}$ converges to $\mu$
3. **Efficient**: Among unbiased estimators, it has minimum variance (for normal distributions)

**Visual Interpretation**:

- If you take many samples and calculate $\bar{x}$ for each, the average of all these sample means will be $\mu$
- Individual samples may overestimate or underestimate $\mu$, but there's no systematic tendency in either direction

**Important Distinction**:

- **One sample mean**: Can be used as a *point estimate* of $\mu$, but it might be inaccurate for that particular sample
- **Many sample means**: The *average* of many $\bar{x}$ values will converge to $\mu$, demonstrating the unbiased property

**Practical Implications**:

- No need for correction factors (unlike sample variance)
- Larger samples provide more precise estimates, but the estimator remains unbiased regardless of sample size
- In practice, we typically work with one sample but understand that our estimate has uncertainty

### 2.2. Sample Variance as Estimator

- Bessel's correction explanation
- Why n-1 instead of n

## 3. Interval Estimation

### 3.1. Central Limit Theorem

The Central Limit Theorem (CLT) is one of the most important concepts in statistics, providing the theoretical foundation for interval estimation and many inferential procedures.

#### 3.1.1. Definition

The Central Limit Theorem states that:

> **Regardless of the shape of the population distribution, the sampling distribution of the sample mean approaches a normal distribution as the sample size increases.**

Mathematically, for a population with mean $\mu$ and standard deviation $\sigma$, the sampling distribution of $\bar{x}$ has:

- Mean: $\mu_{\bar{x}} = \mu$
- Standard deviation: $\sigma_{\bar{x}} = \frac{\sigma}{\sqrt{n}}$ (standard error)
- Distribution: Approximately normal for large $n$

#### 3.1.2. Formal Statement

If $X_1, X_2, \dots, X_n$ are independent and identically distributed random variables with:
- $E[X_i] = \mu$
- $Var(X_i) = \sigma^2 < \infty$

Then as $n \to \infty$, the standardized sample mean converges to a standard normal distribution:

$\frac{\bar{X} - \mu}{\sigma/\sqrt{n}} \xrightarrow{d} N(0,1)$

#### 3.1.3. Key Conditions

**Essential Conditions**:

1. **Random Sampling**: Observations must be independent and randomly selected
2. **Finite Variance**: Population variance $\sigma^2$ must be finite
3. **Sample Size**: Generally $n \geq 30$ for reasonable approximation

**Relaxed Conditions**:

- For populations that are already normal, CLT holds for any sample size
- For symmetric populations, smaller samples ($n \geq 15$) may suffice
- For highly skewed populations, larger samples ($n \geq 50$) may be needed

#### 3.1.4. Practical Implications

**For Any Population Distribution**:

- Even if the population is highly skewed, binomial, or uniform
- The distribution of sample means will be approximately normal
- This allows us to use normal-based inference methods

**Sample Size Guidelines**:

- $n \geq 30$: Good approximation for most populations
- $n \geq 50$: Better approximation for skewed populations
- $n \geq 100$: Excellent approximation for virtually all populations

#### 3.1.5. Visual Interpretation

Consider sampling from different population distributions:

**Uniform Population**:

- Population: Rectangular distribution
- Sample means: Bell-shaped distribution (even for small $n$)

**Skewed Population**:

- Population: Asymmetric distribution
- Sample means: More symmetric, approaching normal as $n$ increases

**Bimodal Population**:

- Population: Two distinct peaks
- Sample means: Single peak, normal shape for large $n$

#### 3.1.6. Role in Parameter Estimation

The CLT is crucial for interval estimation because:

1. **Justifies Normality Assumption**:
   - Allows us to assume sampling distribution is normal
   - Enables use of z-scores and t-scores
2. **Enables Confidence Intervals**:
   - Provides theoretical basis for constructing intervals
   - Determines margin of error calculations
3. **Supports Hypothesis Testing**:
   - Forms foundation for test statistics
   - Allows calculation of p-values
4. **Sample Size Determination**:
   - Guides how large samples need to be
   - Informs precision requirements

#### 3.1.7. Mathematical Foundation

The CLT explains why:

$\bar{X} \sim N\left(\mu, \frac{\sigma^2}{n}\right)$

This means we can standardize sample means using:

$Z = \frac{\bar{X} - \mu}{\sigma/\sqrt{n}} \sim N(0,1)$

When $\sigma$ is unknown (common case), we use:

$t = \frac{\bar{X} - \mu}{s/\sqrt{n}} \sim t_{n-1}$

#### 3.1.8. Common Misconceptions

**Myth 1**: "The population must be normal"
**Truth**: CLT works for any population distribution

**Myth 2**: "n=30 is always sufficient"
**Truth**: Required sample size depends on population skewness

**Myth 3**: "CLT applies to individual observations"
**Truth**: CLT applies to sample means, not individual data points

**Myth 4**: "The approximation is perfect"
**Truth**: It's an approximation that improves with larger samples

#### 3.1.9. Key Insight

The Central Limit Theorem is the "magic" that makes statistical inference possible. It tells us that **no matter how weird or non-normal our population is, if we take large enough samples, the means of those samples will follow a predictable, normal pattern.** This predictability is what allows us to make probabilistic statements about population parameters using sample data.

### 3.2. Sampling Distribution of the Mean

The sampling distribution of the mean is a fundamental concept that describes how sample means vary from sample to sample. It provides the theoretical foundation for understanding the precision of our estimates and constructing confidence intervals.

#### 3.2.1. Definition

The **sampling distribution of the mean** is the probability distribution of all possible sample means of a given size $n$ from a population.

**Key Characteristics**:

- Describes how $\bar{x}$ varies across different samples
- Shows the pattern of sampling variability
- Forms the basis for statistical inference

#### 3.2.2. Properties of the Sampling Distribution

For a population with mean $\mu$ and standard deviation $\sigma$:

1. **Mean of Sampling Distribution**: $\mu_{\bar{x}} = \mu$
   - The average of all possible sample means equals the population mean
   - This demonstrates the unbiased property
2. **Standard Deviation of Sampling Distribution**: $\sigma_{\bar{x}} = \frac{\sigma}{\sqrt{n}}$
   - This is called the **standard error of the mean**
   - Measures how much sample means vary from the population mean
3. **Shape of Sampling Distribution**:
   - If population is normal: Sampling distribution is exactly normal for any $n$
   - If population is not normal: Sampling distribution is approximately normal for large $n$ (by CLT)

#### 3.2.3. Standard Error of the Mean

The **standard error** ($SE$ or $\sigma_{\bar{x}}$) is the standard deviation of the sampling distribution:

$SE = \sigma_{\bar{x}} = \frac{\sigma}{\sqrt{n}}$

**When $\sigma$ is unknown** (most common case), we estimate the standard error using:

$SE = \frac{s}{\sqrt{n}}$

where $s$ is the sample standard deviation.

**Interpretation**:

- Smaller standard error → More precise estimates
- Larger standard error → Less precise estimates

#### 3.2.4. Relationship to Sample Size

The standard error decreases as sample size increases:

$\sigma_{\bar{x}} = \frac{\sigma}{\sqrt{n}}$

This relationship shows that:

- **Doubling sample size** reduces standard error by factor of $\sqrt{2} \approx 1.41$
- **Quadrupling sample size** reduces standard error by factor of 2
- **Increasing sample size** improves precision but with diminishing returns

**Example**:
If $\sigma = 10$,

- $n = 25$: $SE = \frac{10}{\sqrt{25}} = 2$
- $n = 100$: $SE = \frac{10}{\sqrt{100}} = 1$
- $n = 400$: $SE = \frac{10}{\sqrt{400}} = 0.5$

#### 3.2.5. Practical Implications

**Precision of Estimates**:

- Standard error quantifies how close $\bar{x}$ is likely to be to $\mu$
- Smaller SE means our point estimate is more reliable

**Confidence Interval Width**:

- Margin of error is proportional to standard error
- Smaller SE → Narrower confidence intervals

**Sample Size Planning**:

- We can determine required sample size for desired precision
- Trade-off between cost and precision

#### 3.2.6. Empirical Rule for Sampling Distributions

For approximately normal sampling distributions:

- **68%** of sample means fall within $\mu \pm 1 \cdot SE$
- **95%** of sample means fall within $\mu \pm 1.96 \cdot SE$  
- **99.7%** of sample means fall within $\mu \pm 3 \cdot SE$

This means if we took many samples, about 95% of the $\bar{x}$ values would be within about 2 standard errors of $\mu$.

#### 3.2.7. Connection to Confidence Intervals

The sampling distribution directly informs confidence interval construction:

$\bar{x} \pm z_{\alpha/2} \cdot \frac{\sigma}{\sqrt{n}}$

Where:

- $\bar{x}$ is our sample mean (center of interval)
- $z_{\alpha/2}$ is the critical value from standard normal distribution
- $\frac{\sigma}{\sqrt{n}}$ is the standard error (determines interval width)

**Interpretation**:

- The typical distance between sample means and $\mu$ is about 0.42 inches
- If we took many samples of 100 students, about 95% of the sample means would be within $2 \times 0.42 = 0.84$ inches of $\mu$

#### 3.2.9. Key Insight

The sampling distribution of the mean transforms our understanding of variability:

- **Individual observations** vary with standard deviation $\sigma$
- **Sample means** vary with standard error $\frac{\sigma}{\sqrt{n}}$

This reduction in variability ($\sigma$ to $\frac{\sigma}{\sqrt{n}}$) is what makes statistical inference powerful. It explains why we can make precise statements about populations using relatively small samples, and why increasing sample size improves precision in a predictable way.

### 3.3. Confidence Interval

Confidence intervals provide a range of plausible values for a population parameter, quantifying the uncertainty in our estimation. They represent one of the most important applications of statistical inference in practice.

#### 3.3.1. Definition and Interpretation

A **confidence interval** is a range of values that is likely to contain the true population parameter with a specified level of confidence.

**95% Confidence Interval Interpretation**:
> "If we were to take many samples and construct a confidence interval from each sample, about 95% of those intervals would contain the true population parameter."

**Important**: The confidence level refers to the **long-run success rate of the method**, not the probability that a particular interval contains the parameter.

#### 3.3.2. General Formula for Confidence Intervals

The general form of a confidence interval is:

$\text{Point Estimate} \pm \text{Margin of Error}$

Or more specifically:

$\text{Point Estimate} \pm (\text{Critical Value}) \times (\text{Standard Error})$

#### 3.3.3. Confidence Interval for Population Mean

**When $\sigma$ is known** (Z-interval):

$\bar{x} \pm z_{\alpha/2} \cdot \frac{\sigma}{\sqrt{n}}$

**When $\sigma$ is unknown** (t-interval, more common):

$\bar{x} \pm t_{\alpha/2, n-1} \cdot \frac{s}{\sqrt{n}}$

Where:

- $\bar{x}$ = sample mean
- $z_{\alpha/2}$ = critical value from standard normal distribution
- $t_{\alpha/2, n-1}$ = critical value from t-distribution with $n-1$ degrees of freedom
- $s$ = sample standard deviation
- $n$ = sample size

#### 3.3.4. Common Confidence Levels and Critical Values

| Confidence Level | $\alpha$ | $\alpha/2$ | $z_{\alpha/2}$ | $t_{\alpha/2}$ (df=30) |
|------------------|----------|------------|----------------|------------------------|
| 90%              | 0.10     | 0.05       | 1.645          | 1.697                  |
| 95%              | 0.05     | 0.025      | 1.960          | 2.042                  |
| 99%              | 0.01     | 0.005      | 2.576          | 2.750                  |

#### 3.3.5. Margin of Error

The **margin of error** (ME) is the half-width of the confidence interval:

$ME = \text{Critical Value} \times \text{Standard Error}$

For a 95% confidence interval for the mean:

$ME = z_{0.025} \cdot \frac{\sigma}{\sqrt{n}} \quad \text{or} \quad ME = t_{0.025, n-1} \cdot \frac{s}{\sqrt{n}}$

**Factors affecting margin of error**:
1. **Confidence level**: Higher confidence → Larger margin of error
2. **Sample size**: Larger sample → Smaller margin of error  
3. **Population variability**: More variability → Larger margin of error

#### 3.3.6. Z-Intervals vs T-Intervals

| Aspect              | Z-Interval                | T-Interval                  |
| ------------------- | ------------------------- | --------------------------- |
| **When to use**     | Population $\sigma$ known | Population $\sigma$ unknown |
| **Distribution**    | Standard normal           | Student's t                 |
| **Critical values** | $z_{\alpha/2}$            | $t_{\alpha/2, n-1}$         |
| **Sample size**     | Any size                  | Preferably $n \geq 30$      |
| **Practicality**    | Rare in practice          | Most common scenario        |

**Rule of thumb**: Use t-intervals when $\sigma$ is unknown (which is almost always).

#### 3.3.7. Step-by-Step Construction

**Example**: Constructing a 95% CI for mean height

1. **Sample data**: $n = 36$, $\bar{x} = 68$ inches, $s = 3$ inches
2. **Identify distribution**: $\sigma$ unknown → use t-distribution
3. **Find critical value**: $t_{0.025, 35} \approx 2.030$
4. **Calculate standard error**: $SE = \frac{s}{\sqrt{n}} = \frac{3}{\sqrt{36}} = 0.5$
5. **Calculate margin of error**: $ME = 2.030 \times 0.5 = 1.015$
6. **Construct interval**: $68 \pm 1.015 = (66.985, 69.015)$

**Interpretation**: We are 95% confident that the true population mean height is between 66.985 and 69.015 inches.

#### 3.3.8. Proper Interpretation

**Correct Interpretation**:

- "We are 95% confident that the interval (66.985, 69.015) contains the true population mean."
- "This method of constructing intervals would capture the true parameter in 95% of repeated samples."

**Incorrect Interpretations** (to avoid):

- "There is a 95% probability that $\mu$ is between 66.985 and 69.015."
- "95% of the population has heights between 66.985 and 69.015."
- "There is a 95% chance that $\mu$ is in this interval."

#### 3.3.9. Factors Affecting Interval Width

**Wider intervals** (less precision) occur when:

- Higher confidence level (e.g., 99% vs 95%)
- Smaller sample size
- Greater population variability

**Narrower intervals** (more precision) occur when:

- Lower confidence level (e.g., 90% vs 95%)
- Larger sample size  
- Less population variability

#### 3.3.10. Sample Size Determination

We can determine the required sample size for a desired margin of error:

$n = \left( \frac{z_{\alpha/2} \cdot \sigma}{ME} \right)^2$

**Example**: For 95% confidence, $\sigma = 10$, desired $ME = 2$:
$n = \left( \frac{1.96 \times 10}{2} \right)^2 = (9.8)^2 \approx 96.04 \rightarrow 97$

We would need a sample size of 97.

#### 3.3.11. Key Insight

Confidence intervals provide a much more informative approach to estimation than point estimates alone. They:

1. **Quantify uncertainty** about our estimates
2. **Provide a range** of plausible values for the parameter
3. **Allow comparison** across studies or groups
4. **Inform decision-making** by showing precision of estimates
5. **Bridge the gap** between sample statistics and population parameters

The construction of confidence intervals represents the culmination of all the previous concepts: sampling distributions, standard error, and the Central Limit Theorem working together to enable practical statistical inference.