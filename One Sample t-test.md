# 0102---Two-Sample-t-test


# **Background**
## Description of the Two Sample T-Test
The two sample t-test was first created by William Sealy Gosset in 1908. The two sample t-test, also coined by the term ‘Student’s t-test’, is able to determine whether two populations means are equal to one another (Sun, 2020). 

## Hypotheses of the Two Sample T-Test
The hypotheses for the two sample t-test is typically written as follows:

H0: μ1 = μ2
Ha: μ1 ≠ μ2,  Ha: μ1 > μ2, or  Ha: μ1 < μ2.   

# **Method Scope**
## Formula for the Two Sample T-Test
The formula below is written under the assumption that the variances are equal:

$$ T = \frac{\bar{X} - \bar{Y}}{\sqrt{S_p^2\left(\frac{1}{n_x} + \frac{1}{n_y}\right)}} $$

The ‘n’ and ‘m’ values are the sample sizes and the Sp value is found through the given formula:

$$
S_p^2 = \frac{(n - 1)s_x^2 + (m - 1)s_y^2}{n + m - 2}
$$ 

If the variances are not equal, then the formula would be written as such:

$$
T = \frac{(\bar{x} - \bar{y}) - (\mu_x - \mu_y)}{\sqrt{\frac{s_x^2}{n} + \frac{s_y^2}{m}}}
$$

## Test Statistics and P-value Interpretation
Once the T statistic is found, we can then compare it to the critical value derived from the t distribution. With the given alternative hypothesis, we will form a critical region. This process is illustrated in the table below:

| Alternative Hypothesis | Rejection Region                          |
|------------------------|-------------------------------------------|
| H<sub>a</sub>: μ<sub>1</sub> ≠ μ<sub>2</sub> |\|T\| > t<sub>1-α⁄2, ν</sub>|
| H<sub>a</sub>: μ<sub>1</sub> > μ<sub>2</sub> | T > t<sub>1-α, ν</sub>     |
| H<sub>a</sub>: μ<sub>1</sub> < μ<sub>2</sub> | T < t<sub>α, ν</sub>       |


>Note: Reprinted from Tests for the equality of two variances, by National Institute of Standards and Technology (NIST), n.d. In the public domain.

## Assumptions for the Two Sample T-Test
1. _Independence_: Assumes that each observation within the two groups are independent from each other.
2. _Normality_: The data from both of the groups must be approximately normally distributed. It is mentioned that the t-test is known to give correct p-values even when the data is not normally distributed, especially when the data sets are large.
3. _Homogeneity of variances_: The variances between the two groups should be approximately equal. If this rule is violated, then a  student’s t-test would be used instead of the Welch test.
>**Note: The following assumptions were derived through the official documentation from both R code and SAS. Both gave similar assumptions for the two sample t-tests. It must be also remarked that, in python’s documentation, it was found to be missing the  normality assumption.

# Package Implementations
## R
In RStudios, it can be noted that the “R language provides us with a simple t.test built-in function” (Awan, 2023). Hence, the fundamental function includes the two sample t-test. Further, no packages nor any libraries are implemented here. In R, we must simply call the t.test() function and use it accordingly (refer to the Required Input Parameters section).

## Python
In python, one has the liberty of employing different techniques when doing a two sample t-test. The first method would be to utilize the Scipy library. Scipy is a “scientific python library” that has the ability to perform both complex data science methods as well as rudimentary statistical methods (GeeksforGeeks, 2022). Once the library is called, then we can then use the stats.ttest_ind() function.

The second method would be to use the Pingouin package, which is a statistical package that is “based on Pandas and NumPy” (GeeksforGeeks, 2022). Similarly to the first method, you would import the numpy and pingouin libraries. Once those libraries are called, the pg.ttest() function can then be used.

Finally, the last method would be to use the Statsmodels library, which is another library that specializes in both statistical methods and models. It can be remarked that the library acts somewhat similarly to how R is styled with its “modules and dataframes” (GeeksforGeeks, 2022). Once the library is imported, then you can use the ttest_ind() function to execute a two sample t-test.

## SAS
In SAS, there are no packages or libraries that are called before computing a two sample t-test. Simply, SAS uses the command proc ttest. The command has the ability to conduct “one sample, two samples and paired observations (UCLA Statistical Consulting Group). 

# Example Codes
## R - The t.test() Function
```
#Two-sample t-test (Welch's t-test by default)
result <- t.test(x, y)

# Two-sample t-test, assuming equal variances
t.test(x, y, var.equal = TRUE)

# If variances are not assumed equal (Student’s t-test)
t.test(x, y, var.equal = FALSE)
# t.test() being applied to an example model
plot(uptake ~ Treatment, data=CO2)
```
>Assume the variables x and y are numeric vectors that possess random values and have the same length. Furthermore, the t.test() function can also be applied to a model.

>Source: DataCamp. (n.d.). T-tests in R: A step-by-step tutorial. Retrieved May 27, 2025, from https://www.datacamp.com/tutorial/t-tests-r-tutorial

## Python and Its Three Methods
### 1 - The Scipy Library Method:
```
# Python program, performing two sample T-test with Scipy library

# Import the library
import scipy.stats as stats

# Perform the two sample t-test with equal variances
stats.ttest_ind(a = x, b = y, equal_var = True)
```
> For the code above, assume that x and y are both data groups that possess different values and have the same length. It can also be noted that they have been constructed by using the np.array() function.

> Source: GeeksforGeeks (2022). How to conduct a two-sample t-test in Python. https://www.geeksforgeeks.org/how-to-conduct-a-two-sample-t-test-in-python/

