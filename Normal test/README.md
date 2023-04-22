# Statistical tests for normality

Here we deal with three common statistical tests for normality: Anderson-Darling, Shapiro-Wilk, and Kolmogorov-Smirnov.

**Anderson-Darling Test:**
The Anderson-Darling test is a statistical test used to assess whether a given data set follows a normal distribution. It is a variation of the Anderson test that takes into account the magnitude of the differences between the data and the expected values under the normal distribution. The Anderson-Darling test calculates a test statistic that measures the distance between the empirical distribution function (EDF) of the data and the cumulative distribution function (CDF) of a normal distribution. The higher the Anderson-Darling test statistic, the more evidence there is to reject the null hypothesis of normality.

**Shapiro-Wilk Test:**
The Shapiro-Wilk test is another popular statistical test used to assess the normality of a data set. It calculates a test statistic that measures the discrepancy between the data and the expected values under a normal distribution. The Shapiro-Wilk test is known for its ability to accurately detect deviations from normality, especially in small sample sizes. A low p-value from the Shapiro-Wilk test indicates evidence against the null hypothesis of normality.

**Kolmogorov-Smirnov Test:**
The Kolmogorov-Smirnov test is a non-parametric statistical test used to compare the empirical distribution of a data set with a specified theoretical distribution, such as the normal distribution. It calculates a test statistic that quantifies the largest discrepancy between the empirical distribution function (EDF) of the data and the cumulative distribution function (CDF) of the theoretical distribution. A low p-value from the Kolmogorov-Smirnov test suggests evidence against the null hypothesis of normality.

In summary, Anderson-Darling, Shapiro-Wilk, and Kolmogorov-Smirnov tests are commonly used statistical tests to assess the normality of data sets. They provide test statistics and p-values that can be used to make conclusions about the normality of the data. A low p-value typically indicates evidence against normality, while a high p-value suggests that the data may follow a normal distribution. It's important to use these tests in conjunction with other diagnostic tools and visualizations to thoroughly assess the normality of a data set.

## Some technical details

### The Anderson-Darling test

Here's a technical description of the Anderson-Darling test for normality:

The Anderson-Darling test is a variation of the Anderson test that is used to assess whether a given data set follows a normal distribution. It is a statistical test that calculates a test statistic based on the differences between the empirical distribution function (EDF) of the data and the cumulative distribution function (CDF) of a normal distribution. The Anderson-Darling test statistic is defined as:

$A^2 =−n−S$,

where $n$ is the sample size and $S$ is the sum of weighted squared differences between the EDF and the CDF of a normal distribution at each data point.

The Anderson-Darling test has critical values that are used to determine the significance of the test statistic. These critical values are obtained from tables or computed using Monte Carlo simulations. The critical values depend on the desired level of significance, sample size, and the parameters of the normal distribution (mean and variance) assumed in the test.

To perform the Anderson-Darling test in Python, you can use the anderson() function from the `scipy.stats` module. Here's an example:

```
import numpy as np
from scipy.stats import anderson

# Generate example data
data = np.random.normal(loc=0, scale=1, size=100)

# Perform Anderson-Darling test
result = anderson(data)

# Extract test statistic and critical values
test_statistic = result.statistic
critical_values = result.critical_values

# Print results
print("Anderson-Darling Test Statistic: {:.3f}".format(test_statistic))
print("Critical Values: {}".format(critical_values))

```
The Anderson-Darling test statistic is obtained from `result.statistic`, and the critical values are obtained from `result.critical_values`. You can compare the test statistic to the critical values to make conclusions about the normality of the data. If the test statistic is greater than the critical value at a certain level of significance, it suggests evidence against the null hypothesis of normality. Otherwise, if the test statistic is smaller than the critical value, it suggests that the data may follow a normal distribution.

Note that the Anderson-Darling test is sensitive to deviations from normality in the tails of the distribution, making it particularly useful for detecting departures from normality in the tails of the data. However, it may not be as powerful for detecting deviations from normality in the center of the distribution, especially in small sample sizes. It's important to interpret the results of the Anderson-Darling test in conjunction with other diagnostic tools and visualizations to thoroughly assess the normality of a data set.

### The Shapiro-Wilk test

The Shapiro-Wilk test is a widely used statistical test for assessing whether a given data set follows a normal distribution. It is a goodness-of-fit test that calculates a test statistic based on the differences between the observed values of the data and the expected values under a normal distribution.

The Shapiro-Wilk test has critical values that are used to determine the significance of the test statistic. These critical values are obtained from tables or computed using Monte Carlo simulations. The critical values depend on the desired level of significance and the sample size.

To perform the Shapiro-Wilk test in Python, you can use the `shapiro()` function from the `scipy.stats` module. Here's an example:

```
import numpy as np
from scipy.stats import shapiro

# Generate example data
data = np.random.normal(loc=0, scale=1, size=100)

# Perform Shapiro-Wilk test
statistic, p_value = shapiro(data)

# Print results
print("Shapiro-Wilk Test Statistic: {:.3f}".format(statistic))
print("p-value: {:.3f}".format(p_value))

```
The Shapiro-Wilk test statistic is obtained from `statistic`, and the `p-value` is obtained from p_value. You can compare the test statistic to critical values or use the p-value to make conclusions about the normality of the data. If the p-value is less than the chosen level of significance (e.g., 0.05), it suggests evidence against the null hypothesis of normality. Otherwise, if the p-value is greater than the chosen level of significance, it suggests that the data may follow a normal distribution.

Note that the Shapiro-Wilk test is generally considered to be a more powerful test for normality compared to the Anderson-Darling test, especially for small to moderate sample sizes. However, like any statistical test, it has assumptions and limitations, and it's important to interpret the results in conjunction with other diagnostic tools and visualizations to thoroughly assess the normality of a data set.

### The Kolmogorov-Smirnov test

The Kolmogorov-Smirnov test is a non-parametric test that assesses whether a given data set follows a normal distribution. It is a goodness-of-fit test that calculates a test statistic based on the maximum absolute difference between the empirical distribution function (EDF) of the data and the cumulative distribution function (CDF) of a normal distribution.

The Kolmogorov-Smirnov test has critical values that are used to determine the significance of the test statistic. These critical values are obtained from tables or computed using simulations. The critical values depend on the desired level of significance and the sample size.

To perform the Kolmogorov-Smirnov test in Python, you can use the `kstest()` function from the `scipy.stats` module. Here's an example:

```
import numpy as np
from scipy.stats import kstest, norm

# Generate example data
data = np.random.normal(loc=0, scale=1, size=100)

# Perform Kolmogorov-Smirnov test
statistic, p_value = kstest(data, norm.cdf)

# Print results
print("Kolmogorov-Smirnov Test Statistic: {:.3f}".format(statistic))
print("p-value: {:.3f}".format(p_value))

```

The Kolmogorov-Smirnov test statistic is obtained from `statistic`, and the p-value is obtained from `p_value`. You can compare the test statistic to critical values or use the p-value to make conclusions about the normality of the data. If the p-value is less than the chosen level of significance (e.g., 0.05), it suggests evidence against the null hypothesis of normality. Otherwise, if the p-value is greater than the chosen level of significance, it suggests that the data may follow a normal distribution.

Note that the Kolmogorov-Smirnov test is a non-parametric test, meaning it does not assume any specific distribution for the data. However, it has less power compared to the Anderson-Darling and Shapiro-Wilk tests, especially for small sample sizes. It's important to interpret the results in conjunction with other diagnostic tools and visualizations to thoroughly assess the normality of a data set.

#### About p-value

The p-value is a measure used in statistical hypothesis testing that indicates the strength of evidence against a null hypothesis. It is the probability of observing a test statistic as extreme or more extreme than the one actually observed, under the assumption that the null hypothesis is true. In other words, the p-value quantifies the likelihood of obtaining a test statistic as extreme or more extreme than the observed test statistic, assuming that the null hypothesis is true.

The p-value is an important statistical concept because it helps in making decisions about the validity of a null hypothesis. In hypothesis testing, the null hypothesis is a statement that assumes there is no effect or relationship in the data, while the alternative hypothesis assumes there is an effect or relationship. The p-value is used to evaluate the strength of evidence against the null hypothesis.

If the p-value is low (typically less than a chosen significance level, commonly 0.05), it suggests that the observed data is unlikely to have occurred by chance alone, assuming the null hypothesis is true. This may lead to rejecting the null hypothesis in favor of the alternative hypothesis, indicating that there is evidence to support the presence of an effect or relationship in the data.

On the other hand, if the p-value is high (greater than the chosen significance level), it suggests that the observed data is reasonably likely to have occurred by chance alone, assuming the null hypothesis is true. In this case, there is insufficient evidence to reject the null hypothesis, and the conclusion may be that there is no significant effect or relationship in the data.

It's important to note that the p-value is not a measure of the strength or size of an effect, but rather a measure of the strength of evidence against the null hypothesis. A low p-value does not necessarily indicate the magnitude or importance of an effect, but rather suggests that the observed data is unlikely to have occurred by chance alone, assuming the null hypothesis is true. It's also important to interpret p-values in conjunction with other statistical measures, effect sizes, and subject-matter knowledge to make informed decisions in hypothesis testing and statistical inference.
