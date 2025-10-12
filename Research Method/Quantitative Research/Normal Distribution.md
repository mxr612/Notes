---
Course:
  - PSYC10100 Introduction to Statistics for Psychological Sciences
tags:
  - statistics
  - probability
  - distributions
  - normal-distribution
---
## 1. Introduction to Probability Distributions

### 1.1. What is a Probability Distribution?

A probability distribution describes how probabilities are distributed over the values of a random variable. It specifies the likelihood of different outcomes in an experiment or observation.

### 1.2. Types of Probability Distributions

- **Discrete Distributions**: For countable outcomes (e.g., binomial, Poisson)
- **Continuous Distributions**: For measurable outcomes (e.g., normal, exponential)

## 2. The Normal Distribution

### 2.1. Definition and Properties
The normal distribution, also known as the Gaussian distribution, is a continuous probability distribution characterized by its bell-shaped curve.

**Key Properties**:
- Symmetrical about the mean
- Mean = Median = Mode
- Defined by two parameters: mean ($\mu$) and standard deviation ($\sigma$)
- Total area under the curve equals 1
- Follows the Empirical Rule (68-95-99.7 rule)

### 2.2. Probability Density Function
The probability density function (PDF) of the normal distribution is:

$$
f(x) = \frac{1}{\sigma\sqrt{2\pi}} e^{-\frac{1}{2}\left(\frac{x-\mu}{\sigma}\right)^2}
$$

Where:

- $\mu$ = mean
- $\sigma$ = standard deviation
- $\pi$ ≈ 3.14159
- $e$ ≈ 2.71828

### 2.3. Empirical Rule (68-95-99.7 Rule)

For normally distributed data:

- Approximately 68% of data falls within $\pm1$ standard deviation from the mean
- Approximately 95% of data falls within $\pm2$ standard deviations from the mean
- Approximately 99.7% of data falls within $\pm3$ standard deviations from the mean

## 3. Distribution Shape Characteristics

### 3.1. Skewness

Skewness measures the asymmetry of a probability distribution around its mean. It indicates whether data are concentrated more on one side of the distribution.

**Types of Skewness**:

- **Positive Skew (Right Skew)**: Tail extends to the right, mean > median > mode
- **Negative Skew (Left Skew)**: Tail extends to the left, mean < median < mode
- **Zero Skew**: Symmetrical distribution, mean = median = mode

**Calculation**: See [[Descriptive Statistics]]

### 3.2. Kurtosis

Kurtosis measures the "tailedness" of a probability distribution, indicating how much data are in the tails compared to a normal distribution.

**Types of Kurtosis**:

- **Mesokurtic**: Normal distribution, kurtosis = 3 (excess kurtosis = 0)
- **Leptokurtic**: Heavy tails and sharp peak, kurtosis > 3 (excess kurtosis > 0)
- **Platykurtic**: Light tails and flat peak, kurtosis < 3 (excess kurtosis < 0)

**Calculation**: See [[Descriptive Statistics]]

## 4. Standard Normal Distribution (Z-Distribution)

### 4.1. Definition

The standard normal distribution is a special case of the normal distribution with:

- Mean ($\mu$) = 0
- Standard deviation ($\sigma$) = 1

### 4.2. Z-Scores

A z-score (standard score) measures how many standard deviations an observation is from the mean:

$$
z = \frac{x - \mu}{\sigma}
$$

**Interpretation**:

- $z = 0$: Value equals the mean
- $z > 0$: Value above the mean
- $z < 0$: Value below the mean

### 4.3. Z-Table and Probability Calculations

Z-tables provide the cumulative probability from $-\infty$ to a given z-value. Common z-values and their probabilities:

| Z-Score | Cumulative Probability |
| ------- | ---------------------- |
| -3.0    | 0.0013                 |
| -2.0    | 0.0228                 |
| -1.0    | 0.1587                 |
| 0.0     | 0.5000                 |
| 1.0     | 0.8413                 |
| 2.0     | 0.9772                 |
| 3.0     | 0.9987                 |

## 5. Student's t-Distribution

### 5.1. Definition and Purpose
The t-distribution is used when:
- Sample sizes are small ($n < 30$)
- Population standard deviation is unknown
- We need to estimate population parameters from sample data

### 5.2. Properties

- Similar bell shape to normal distribution
- Heavier tails than normal distribution (more probability in extremes)
- Approaches normal distribution as degrees of freedom increase
- Defined by degrees of freedom ($df = n - 1$)

### 5.3. Degrees of Freedom

Degrees of freedom represent the number of independent pieces of information available to estimate a parameter:

$$
df = n - 1
$$

Where $n$ is the sample size.

### 5.4. T-Scores

T-scores are calculated similarly to z-scores but use sample standard deviation:

$$
t = \frac{\bar{x} - \mu}{s/\sqrt{n}}
$$

Where:

- $\bar{x}$ = sample mean
- $\mu$ = population mean (hypothesized)
- $s$ = sample standard deviation
- $n$ = sample size

## 6. Comparing Z and T Distributions

| Characteristic | Z-Distribution | T-Distribution |
|----------------|----------------|----------------|
| **When to Use** | $\sigma$ known, large $n$ | $\sigma$ unknown, small $n$ |
| **Parameters** | $\mu$, $\sigma$ | $\mu$, $s$, $df$ |
| **Shape** | Fixed bell curve | Varies with $df$ |
| **Tails** | Lighter | Heavier |
| **Applications** | Hypothesis testing, confidence intervals | Same, but for small samples |

## 7. Other Important Distributions

### 7.1. Bimodal Distribution

- Has two distinct peaks or modes
- Often indicates two different populations or processes
- Common in mixed data sets

### 7.2. Uniform Distribution

- All outcomes equally likely
- Rectangular shape
- Constant probability density function

### 7.3. Other Common Distributions

- **Binomial**: For binary outcomes
- **Poisson**: For count data
- **Exponential**: For time between events

## 8. Applications in Psychological Research

### 8.1. Hypothesis Testing

- Using z-tests for large samples with known population parameters
- Using t-tests for small samples or unknown population parameters

### 8.2. Confidence Intervals

- Constructing intervals for population means
- Determining margin of error

### 8.3. Effect Size Calculations

- Standardizing measures for comparison across studies
- Cohen's d and other effect size metrics

## 9. Practical Examples

### 9.1. Example 1: Z-Score Calculation

Given: $\mu = 100$, $\sigma = 15$, $x = 130$

$$
z = \frac{130 - 100}{15} = 2.0
$$

Interpretation: This score is 2 standard deviations above the mean.

### 9.2. Example 2: T-Score Calculation

Given: $\mu = 50$, $\bar{x} = 55$, $s = 8$, $n = 25$

$$
t = \frac{55 - 50}{8/\sqrt{25}} = \frac{5}{1.6} = 3.125
$$

$df = 25 - 1 = 24$

## 10. R Implementation

### 10.1. Normal Distribution Functions

```R
# Probability density
dnorm(x, mean = 0, sd = 1)

# Cumulative probability
pnorm(q, mean = 0, sd = 1)

# Quantile function
qnorm(p, mean = 0, sd = 1)

# Random generation
rnorm(n, mean = 0, sd = 1)
```

### 10.2. T-Distribution Functions

```R
# Probability density
dt(x, df)

# Cumulative probability
pt(q, df)

# Quantile function
qt(p, df)

# Random generation
rt(n, df)
```

### 10.3. Sample Standard Deviation

```R
sample_sd <- sd(data) # Sample standard deviation
```

## 11. Summary

- The normal distribution is fundamental in statistics with predictable properties
- Z-distribution is used when population parameters are known
- T-distribution is used for small samples with unknown population parameters
- Understanding distribution shapes (skewness, kurtosis) helps interpret data patterns
- These distributions form the basis for many statistical tests in psychological research
