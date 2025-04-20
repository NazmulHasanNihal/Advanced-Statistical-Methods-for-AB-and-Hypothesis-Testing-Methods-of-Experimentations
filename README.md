# Advanced Statistical Methods for AB and Hypothesis Testing Methods of Experimentations
This project will showcase advanced statistical methods for A/B testing and hypothesis testing, applying various techniques to experimentations, statistical and data analysis. This project covers Normality tests, Variance tests, T-tests, Z-tests, Non-parametric, Parametric, Chi-Square tests and many more to help make data-driven decisions in experiments. 

## Shapiro-Wilk Test (Normality Test)

In many statistical tests (**t-tests**, **ANOVA**, **linear regression**) we assume that the data comes from a normal distribution. If this assumption is violated, the results of these tests might not be valid.

The **Shapiro-Wilk** test helps us to verify if the data meets this assumption, so we can decide wheter to proceed with parametric tests (**t-test** or **ANOVA**) or non-parametric (**Mann-Whitney U test**, **Kruskal-Wallis test**) but most of the case we don't need normarlity in non-parametric tests.

When not to use the **Shapiro-Wilk**:

> - If the dataset is large like more then 5000 values in **Shapiro-Wilk** test become too sensitive. minor deviations from normality lead to rejecting the null hypothesis even if the deviation is not practically significant. 
>
>- The **Shapiro-Wilk** test is only suitable for continuous numerical data. If the data is categorical (**gender**, **country**, **product type**), the normality test is not applicable.
>
>- If the data is highly skewed or has many outliers, it may violate the assumptions of the **Shapiro-Wilk** test, and the results might not be meaningful.

### Dataset
Using Iris Plants Database in this test. The dataset contains a set of 150 records under 5 attributes - Petal Length, Petal Width, Sepal Length, Sepal width and Class(Species).
![ alt text](img\shapiro-wilk.png)

### Shapiro-Wilk Normality Test Results
1. Sepal Length: p-value = 0.0102 (not normally distributed, reject null hypothesis).

2. Sepal Width: p-value = 0.0752 (normally distributed, fail to reject null hypothesis).

3. Petal Length: p-value = 7.545419569615864e-10 (not normally distributed, reject null hypothesis).

4. Petal Width: p-value = 1.8647596517271003e-08 (not normally, reject null hypothesis).

> - Sepal Width is normally distributed, so parametric tests can be used.
> - Sepal Length, Petal Length, and Petal Width are not normally distributed. Here we have to use non-parametric tests or applying data transformation for these columns.

