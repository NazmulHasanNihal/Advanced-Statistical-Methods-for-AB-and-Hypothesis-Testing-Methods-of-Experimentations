# Advanced Statistical Methods for AB and Hypothesis Testing Methods of Experimentations
This project will showcase advanced statistical methods for A/B testing and hypothesis testing, applying various techniques to experimentations, statistical and data analysis. This project covers Normality tests, Variance tests, T-tests, Z-tests, Non-parametric, Parametric, Chi-Square tests and many more to help make data-driven decisions in experiments. 

## Shapiro-Wilk Test (Normality Test)

In many statistical tests (**t-tests**, **ANOVA**, **linear regression**) we assume that the data comes from a normal distribution. If this assumption is violated, the results of these tests might not be valid.

The **Shapiro-Wilk** test helps us to verify if the data meets this assumption, so we can decide wheter to proceed with parametric tests (**t-test** or **ANOVA**) or non-parametric (**Mann-Whitney U test**, **Kruskal-Wallis test**) but most of the case we don't need normarlity in non-parametric tests.

When not to use the **Shapiro-Wilk**:

- If the dataset is large like more then 5000 values in **Shapiro-Wilk** test become too sensitive. minor deviations from normality lead to rejecting the null hypothesis even if the deviation is not practically significant. 
>
- The **Shapiro-Wilk** test is only suitable for continuous numerical data. If the data is categorical (**gender**, **country**, **product type**), the normality test is not applicable.
>
- If the data is highly skewed or has many outliers, it may violate the assumptions of the **Shapiro-Wilk** test, and the results might not be meaningful.

### Dataset
Using `Iris Plants Database` in this test. The dataset contains a set of `150 records` under `5 attributes` - `Petal Length`, `Petal Width`, `Sepal Length`, `Sepal width` and Class(Species).
![ alt text](img\shapiro-wilk.png)

### Shapiro-Wilk Normality Test Results
`1. Sepal Length: p-value = 0.0102 (not normally distributed, reject null hypothesis).`
`2. Sepal Width: p-value = 0.0752 (normally distributed, fail to reject null hypothesis).`
`3. Petal Length: p-value = 7.545419569615864e-10 (not normally distributed, reject null hypothesis).`
`4. Petal Width: p-value = 1.8647596517271003e-08 (not normally, reject null hypothesis).`

- Sepal Width is normally distributed, so parametric tests can be used.
- Sepal Length, Petal Length, and Petal Width are not normally distributed. Here we have to use non-parametric tests or applying data transformation for these columns.

## Levene's Test for Equal Variance (Homogeneity of Variance)

Levene's test is used to check the assumption of equal variances (also known as homogeneity of variances) across different groups or samples. This assumption is important for many statistical tests, such as `ANOVA` and `t-tests`, which require that the variability within each group being compared is similar. When variances are unequal (heteroscedasticity), it can lead to incorrect conclusions in statistical tests.

- The primary purpose of Levene’s test is to ensure that the assumption of equal variances holds before applying statistical tests that rely on this assumption (like One-Way ANOVA and t-test) and comparing more than two groups if the groups have similar variance

- Levene’s test is particularly useful when comparing more than two groups, and you want to verify if the groups have similar variances.

### State the Hypotheses
- **Null Hypothesis (H₀):** The variances of the groups are equal (homogeneity of variances).

- **Alternative Hypothesis (H₁):** The variances of the groups are not equal (heterogeneity of variances).
### Dataset
Using Housing Price Data for this test. This dataset has 3 Group of City. City 1, City 2, City 3 with Price Columns.

![ alt text](img\levenestest.png)

### Shapiro-Wilk Normality Test Results

**Normality Check:**

- **City 1:** The p-value is 0.9480, which is greater than 0.05, indicating that the data is normally distributed.

- **City 2:** The p-value is 0.1150, which is greater than 0.05, indicating that the data is normally distributed.

- **City 3:** The p-value is 0.6759, which is greater than 0.05, indicating that the data is normally distributed.

### Levene's Test for Equality of Variance

**The p-value is 0.0006, which is less than 0.05. This indicates that the variances of house prices across the three cities are significantly different.**

