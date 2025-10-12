---
Course:
  - PSYC10100 Introduction to Statistics for Psychological Sciences
---
## 1. Size

We note the size of:

- Population: $N$
- Sample: $n$

To distinguish the difference between Population and Sample. For difference between which, see more in [Population and Sample](Population%20and%20Sample.md). 

## 2. Central Tendency

Central tendency provides a general description of the data set, using mean, mode, and median.

| Measure    | Advantages                          | Disadvantages                           | Best for             |
| ---------- | ----------------------------------- | --------------------------------------- | -------------------- |
| **Mean**   | Uses all data, algebraic properties | Sensitive to outliers                   | Normal distributions |
| **Median** | Robust to outliers                  | Ignores magnitude of extreme values     | Skewed distributions |
| **Mode**   | Works for categorical data          | May not be unique, ignores other values | Nominal data         |

### 2.1. Mean

Mean is the average of a specific variable in a data set. To tell apart, a population mean is noted as $\mu$, while a sample mean is noted as $\bar{x}$.

$$
\mu = \frac{\sum_{i}^{N}{x}}{N}
$$
$$
\bar{x} = \frac{\sum_{i}^{n}{x}}{n}
$$

In some article, it is also considered as the expectation of a variable, notated as $E[x] = \sigma$. In most situation, people estimate $\mu$ by $E[x]$, but which leads to a degree of freedom (DoF) lost.

Trying to avoid the influence of outliers, a *trimmed mean* calculates the average after removing a specified percentage of the highest and lowest values to reduce the effect of outliers.

``` R
describe(data, trim = 0.1) # Set the persentace for trimed mean
```

### 2.2. Mode

The **mode** is the value that appears most frequently in a data set. Unlike mean and median, a data set can have:

- **Unimodal**: One mode
- **Bimodal**: Two modes  
- **Multimodal**: Multiple modes
- **No mode**: All values appear with equal frequency

**Characteristics**:
- Useful for categorical data and discrete distributions
- Not affected by extreme values (outliers)
- May not exist or may not be unique
- For continuous data, mode is often estimated using kernel density estimation

**Example**: For data set {1, 2, 2, 3, 4, 4, 4, 5}, the mode is 4.

### 2.3. Median

The **median** is the middle value in an ordered data set. It divides the data into two equal halves:

- For odd number of observations: Middle value
- For even number of observations: Average of two middle values

**Calculation**:
- Order the data from smallest to largest
- If $n$ is odd: $\text{median} = x_{(n+1)/2}$
- If $n$ is even: $\text{median} = \frac{x_{n/2} + x_{n/2 + 1}}{2}$

**Characteristics**:
- Robust to outliers and skewed distributions
- More appropriate than mean for ordinal data
- Represents the 50th percentile (second quartile)

**Example**: 
- Data: {3, 1, 7, 4, 2} → Ordered: {1, 2, 3, 4, 7} → Median = 3
- Data: {3, 1, 7, 4} → Ordered: {1, 3, 4, 7} → Median = (3+4)/2 = 3.5

## 3. Measures of Dispersion

### 3.1. Variance

Variance measures the average squared deviation from the mean. It distinguishes between population and sample variance due to degrees of freedom considerations.

#### 3.1.1. Population Variance ($\sigma^2$)
The variance of the entire population:

$$
\sigma^2 = \frac{\sum_{i=1}^{N}(x_i - \mu)^2}{N}
$$

where:

- $N$ = population size
- $\mu$ = population mean
- $x_i$ = individual values

**Example**:
Population {1, 3, 5, 7, 9}, $\mu = 5$.
  $\sigma^2 = \frac{(1-5)^2 + (3-5)^2 + (5-5)^2 + (7-5)^2 + (9-5)^2}{5} = \frac{16+4+0+4+16}{5} = 8$
#### 3.1.2. Sample Variance ($s^2$)
The variance estimated from a sample, using $n-1$ in denominator for unbiased estimation:

$$
s^2 = \frac{\sum_{i=1}^{n}(x_i - \bar{x})^2}{n-1}
$$

where:
- $n$ = sample size
- $\bar{x}$ = sample mean
- $x_i$ = individual values

**Key Differences**:
- **Denominator**: Population uses $N$, sample uses $n-1$ (Bessel's correction)
- **Purpose**: Population variance describes the entire population, sample variance estimates population variance
- **Bias**: Using $n$ instead of $n-1$ in sample variance creates a biased estimator

**Why $n-1$ for sample variance?**

Using $n-1$ (degrees of freedom) corrects for the fact that we're estimating the population mean from the sample, making $s^2$ an unbiased estimator of $\sigma^2$. 

**Example**:
Subset {1, 3, 5} from population, $\bar{x} = 3$.
  $s^2 = \frac{(1-3)^2 + (3-3)^2 + (5-3)^2}{3-1} = \frac{4+0+4}{2} = 4$

**R Implementation**:

```R
sample_var <- var(data) # Sample variance (built-in function)
```

### 3.2. Standard Deviation

Standard deviation is the square root of variance, providing a measure of dispersion in the original units of the data. Like variance, it distinguishes between population and sample standard deviation.

#### 3.2.1. Population Standard Deviation ($\sigma$)
The standard deviation of the entire population:

$$
\sigma = \sqrt{\sigma^2} = \sqrt{\frac{\sum_{i=1}^{N}(x_i - \mu)^2}{N}}
$$

#### 3.2.2. Sample Standard Deviation ($s$)
The standard deviation estimated from a sample:

$$
s = \sqrt{s^2} = \sqrt{\frac{\sum_{i=1}^{n}(x_i - \bar{x})^2}{n-1}}
$$

**Interpretation**:

- Approximately 68% of data falls within $\pm1$ standard deviation from the mean (for normal distributions)
- Approximately 95% of data falls within $\pm2$ standard deviations from the mean
- Approximately 99.7% of data falls within $\pm3$ standard deviations from the mean

**Advantages over Variance**:

- Same units as original data (easier to interpret)
- More intuitive measure of spread
- Directly comparable to the mean

**Example** (continuing from variance examples):

- Population: $\sigma = \sqrt{8} \approx 2.83$
- Sample: $s = \sqrt{4} = 2$

**R Implementation**:
```R
sample_sd <- sd(data) # Sample standard deviation (built-in function)
```

### 3.3. Median Absolute Deviation

Median Absolute Deviation (MAD) is a robust measure of statistical dispersion that uses the median rather than the mean, making it resistant to outliers.

**Definition**:
MAD is the median of the absolute deviations from the data's median:

$$
\text{MAD} = \text{median}(|x_i - \text{median}(x)|)
$$

**Scale Factor**:
For normally distributed data, MAD needs to be scaled by approximately 1.4826 to be comparable to standard deviation:

$$
\text{MAD}_{\text{normal}} = 1.4826 \times \text{MAD}
$$

**Why Use MAD?**

- **Robustness**: Not influenced by extreme values
- **Breakdown point**: 50% - up to half the data can be outliers without affecting MAD
- **Interpretation**: Similar to standard deviation but for median-based analysis

**Comparison with Standard Deviation**:

| Aspect          | Standard Deviation          | MAD                 |
| --------------- | --------------------------- | ------------------- |
| **Sensitivity** | Sensitive to outliers       | Robust to outliers  |
| **Center**      | Uses mean                   | Uses median         |
| **Breakdown**   | 0% (any outlier affects it) | 50%                 |
| **Units**       | Original data units         | Original data units |

**Example**:
Data: {1, 2, 3, 4, 100} (100 is an outlier)

- Median = 3
- Absolute deviations: |1-3|=2, |2-3|=1, |3-3|=0, |4-3|=1, |100-3|=97
- Sorted deviations: {0, 1, 1, 2, 97}
- MAD = median{0, 1, 1, 2, 97} = 1

**R Implementation**:
```R
# Calculate MAD
mad_value <- mad(data)

# Scaled MAD for normal distributions
scaled_mad <- mad(data, constant = 1.4826)
```
### 3.4. Interquartile Range

Interquartile Range (IQR) is a robust measure of statistical dispersion that describes the spread of the middle 50% of the data. It is particularly useful for identifying outliers and understanding data distribution.

**Definition**:
IQR is the difference between the third quartile (Q3) and the first quartile (Q1):

$$
\text{IQR} = Q_3 - Q_1
$$

where:
- $Q_1$ = First quartile (25th percentile)
- $Q_3$ = Third quartile (75th percentile)

**Quartile Calculation Methods**:
There are several methods to calculate quartiles. Common approaches include:

1. **Method 1 (Inclusive)**: $Q_1$ at position $(n+1)/4$, $Q_3$ at position $3(n+1)/4$
2. **Method 2 (Exclusive)**: $Q_1$ at position $n/4$, $Q_3$ at position $3n/4$
3. **Tukey's Method**: Median of lower half and upper half

**Outlier Detection**:
IQR is commonly used to identify outliers using the "1.5×IQR rule":
- **Lower fence**: $Q_1 - 1.5 \times \text{IQR}$
- **Upper fence**: $Q_3 + 1.5 \times \text{IQR}$
- Values outside these fences are considered potential outliers

**Box Plot Relationship**:
IQR forms the "box" in box plots:
- Box extends from Q1 to Q3
- Line inside box represents median
- Whiskers extend to most extreme non-outlier values

**Advantages**:
- **Robust**: Not affected by extreme values
- **Intuitive**: Easy to interpret and visualize
- **Standardized**: Widely used in exploratory data analysis

**Example**:
Data: {1, 2, 3, 4, 5, 6, 7, 8, 9, 10}

- Q1 (25th percentile) = 3.25
- Q3 (75th percentile) = 7.75
- IQR = 7.75 - 3.25 = 4.5
- Lower fence = 3.25 - 1.5×4.5 = -3.5
- Upper fence = 7.75 + 1.5×4.5 = 14.5
- No outliers in this dataset

**R Implementation**:
```R
# Calculate IQR (built-in function)
iqr_value <- IQR(data)

# Calculate quartiles
q1 <- quantile(data, 0.25)
q3 <- quantile(data, 0.75)
manual_iqr <- q3 - q1

# Outlier detection
lower_fence <- q1 - 1.5 * iqr_value
upper_fence <- q3 + 1.5 * iqr_value
outliers <- data[data < lower_fence | data > upper_fence]

# Box plot visualization
boxplot(data, main = "Box Plot with IQR")
```

**Comparison with Other Dispersion Measures**:

| Measure | Robustness | Interpretation | Best Use |
|---------|------------|----------------|----------|
| **Range** | Not robust | Total spread | Quick overview |
| **Variance/SD** | Not robust | Average deviation | Normal distributions |
| **MAD** | Very robust | Median-based spread | Outlier-prone data |
| **IQR** | Robust | Middle 50% spread | Exploratory analysis |

## 4. Distribution Shape

### 4.1. Skewness

Skewness measures the asymmetry of a probability distribution around its mean. It indicates whether data are concentrated more on one side of the distribution.

**Types of Skewness**:

- **Positive Skew (Right Skew)**: Tail extends to the right, mean > median > mode
- **Negative Skew (Left Skew)**: Tail extends to the left, mean < median < mode
- **Zero Skew**: Symmetrical distribution, mean = median = mode

**Calculation**:
The most common measure is Pearson's moment coefficient of skewness:

$$
\text{Skewness} = \frac{E[(X - \mu)^3]}{\sigma^3}
$$

For sample data:

$$
g_1 = \frac{\frac{1}{n}\sum_{i=1}^{n}(x_i - \bar{x})^3}{\left(\frac{1}{n}\sum_{i=1}^{n}(x_i - \bar{x})^2\right)^{3/2}}
$$

**Interpretation**:

- **|Skewness| < 0.5**: Approximately symmetric
- **0.5 ≤ |Skewness| < 1**: Moderately skewed
- **|Skewness| ≥ 1**: Highly skewed

**R Implementation**:
```R
# Using moments package
library(moments)
skewness_value <- skewness(data)

# Using psych package
library(psych)
skewness_value <- describe(data)$skew

# Manual calculation
manual_skew <- function(x) {
  n <- length(x)
  mean_x <- mean(x)
  sd_x <- sd(x)
  (sum((x - mean_x)^3) / n) / (sd_x^3)
}
```

### 4.2. Kurtosis

Kurtosis measures the "tailedness" of a probability distribution, indicating how much data are in the tails compared to a normal distribution.

**Types of Kurtosis**:

- **Mesokurtic**: Normal distribution, kurtosis = 3 (excess kurtosis = 0)
- **Leptokurtic**: Heavy tails and sharp peak, kurtosis > 3 (excess kurtosis > 0)
- **Platykurtic**: Light tails and flat peak, kurtosis < 3 (excess kurtosis < 0)

**Calculation**:
Pearson's moment coefficient of kurtosis:

$$
\text{Kurtosis} = \frac{E[(X - \mu)^4]}{\sigma^4}
$$

Excess kurtosis (more commonly used):

$$
\text{Excess Kurtosis} = \frac{E[(X - \mu)^4]}{\sigma^4} - 3
$$

For sample data:

$$
g_2 = \frac{\frac{1}{n}\sum_{i=1}^{n}(x_i - \bar{x})^4}{\left(\frac{1}{n}\sum_{i=1}^{n}(x_i - \bar{x})^2\right)^2} - 3
$$

**Interpretation**:
- **Excess Kurtosis = 0**: Normal distribution
- **Excess Kurtosis > 0**: Heavy tails (more outliers)
- **Excess Kurtosis < 0**: Light tails (fewer outliers)

**R Implementation**:
```R
# Using moments package
library(moments)
kurtosis_value <- kurtosis(data)  # Returns excess kurtosis

# Using psych package
library(psych)
kurtosis_value <- describe(data)$kurtosis

# Manual calculation
manual_kurtosis <- function(x) {
  n <- length(x)
  mean_x <- mean(x)
  sd_x <- sd(x)
  (sum((x - mean_x)^4) / n) / (sd_x^4) - 3
}
```

## 5. Estimation Accuracy

### 5.1. Standard Error

Standard Error (SE) measures the precision of a sample statistic as an estimate of the population parameter. It quantifies the variability of the sampling distribution.

**Standard Error of the Mean (SEM)**:
The most common standard error, measuring how much the sample mean varies from sample to sample:

$$
\text{SEM} = \frac{s}{\sqrt{n}}
$$

where:

- $s$ = sample standard deviation
- $n$ = sample size

**Interpretation**:

- Smaller SE indicates more precise estimate
- SE decreases as sample size increases
- Used to construct confidence intervals

**Other Standard Errors**:

- **Standard Error of Proportion**: $\text{SE}_p = \sqrt{\frac{p(1-p)}{n}}$
- **Standard Error of Difference**: $\text{SE}_{\bar{x}_1 - \bar{x}_2} = \sqrt{\frac{s_1^2}{n_1} + \frac{s_2^2}{n_2}}$

**R Implementation**:
```R
# Standard Error of the Mean
sem <- function(x) {
  sd(x) / sqrt(length(x))
}

# Using built-in functions
sample_mean <- mean(data)
sample_sd <- sd(data)
n <- length(data)
sem_manual <- sample_sd / sqrt(n)

# For proportions
se_prop <- function(p, n) {
  sqrt(p * (1 - p) / n)
}
```

### 5.2. Confidence Interval

Confidence Interval (CI) provides a range of values that likely contains the population parameter with a specified level of confidence.

**Confidence Interval for Mean**:
For large samples or known population variance:

$$
\text{CI} = \bar{x} \pm z_{\alpha/2} \times \frac{s}{\sqrt{n}}
$$

For small samples with unknown population variance:

$$
\text{CI} = \bar{x} \pm t_{\alpha/2, df} \times \frac{s}{\sqrt{n}}
$$

where:
- $\bar{x}$ = sample mean
- $s$ = sample standard deviation
- $n$ = sample size
- $z_{\alpha/2}$ = critical z-value
- $t_{\alpha/2, df}$ = critical t-value with $df = n-1$

**Common Confidence Levels**:
- **90% CI**: $\alpha = 0.10$, $z_{0.05} = 1.645$
- **95% CI**: $\alpha = 0.05$, $z_{0.025} = 1.96$
- **99% CI**: $\alpha = 0.01$, $z_{0.005} = 2.576$

**Interpretation**:
- "We are 95% confident that the true population mean lies between [lower, upper]"
- Does NOT mean there's a 95% probability that the specific interval contains the parameter

**R Implementation**:
```R
# Using t.test for confidence interval
result <- t.test(data)
ci <- result$conf.int

# Manual calculation for 95% CI
manual_ci <- function(x, conf_level = 0.95) {
  n <- length(x)
  mean_x <- mean(x)
  sd_x <- sd(x)
  se <- sd_x / sqrt(n)
  t_critical <- qt(1 - (1 - conf_level)/2, df = n - 1)
  lower <- mean_x - t_critical * se
  upper <- mean_x + t_critical * se
  return(c(lower, upper))
}

# For proportions
prop_ci <- function(x, conf_level = 0.95) {
  p <- mean(x)
  n <- length(x)
  se <- sqrt(p * (1 - p) / n)
  z_critical <- qnorm(1 - (1 - conf_level)/2)
  lower <- p - z_critical * se
  upper <- p + z_critical * se
  return(c(lower, upper))
}
```

## 6. Implementation in R

The package `psych` provides pretty descriptive statistic:

``` R
library(psych)
data <- c(1, 1, 6, 8, 8, 8, 8, 9, 9, 9, 9, 9, 9)
View(describe(data))
```

But which package does not calculate the mode of data set, you could calculate it by:

``` R
# Calculate mode
mode_val <- as.numeric(names(sort(table(data), decreasing = TRUE)[1]))
```