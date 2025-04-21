# Advanced Statistical Methods for AB and Hypothesis Testing Methods of Experimentations
This project will showcase advanced statistical methods for A/B testing and hypothesis testing, applying various techniques to experimentations, statistical and data analysis. This project covers Normality tests, Variance tests, T-tests, Z-tests, Non-parametric, Parametric, Chi-Square tests and many more to help make data-driven decisions in experiments. 

---

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
![ alt text](img/shapiro-wilk.png)

### Shapiro-Wilk Normality Test Results
`1. Sepal Length: p-value = 0.0102 (not normally distributed, reject null hypothesis).`

`2. Sepal Width: p-value = 0.0752 (normally distributed, fail to reject null hypothesis).`

`3. Petal Length: p-value = 7.545419569615864e-10 (not normally distributed, reject null hypothesis).`

`4. Petal Width: p-value = 1.8647596517271003e-08 (not normally, reject null hypothesis).`

- Sepal Width is normally distributed, so parametric tests can be used.
- Sepal Length, Petal Length, and Petal Width are not normally distributed. Here we have to use non-parametric tests or applying data transformation for these columns.

---

## Levene's Test for Equal Variance (Homogeneity of Variance)

Levene's test is used to check the assumption of equal variances (also known as homogeneity of variances) across different groups or samples. This assumption is important for many statistical tests, such as `ANOVA` and `t-tests`, which require that the variability within each group being compared is similar. When variances are unequal (heteroscedasticity), it can lead to incorrect conclusions in statistical tests.

- The primary purpose of Levene’s test is to ensure that the assumption of equal variances holds before applying statistical tests that rely on this assumption (like One-Way ANOVA and t-test) and comparing more than two groups if the groups have similar variance

- Levene’s test is particularly useful when comparing more than two groups, and you want to verify if the groups have similar variances.

### State the Hypotheses
- **Null Hypothesis (H₀):** The variances of the groups are equal (homogeneity of variances).

- **Alternative Hypothesis (H₁):** The variances of the groups are not equal (heterogeneity of variances).
### Dataset
Using Housing Price Data for this test. This dataset has 3 Group of City. City 1, City 2, City 3 with Price Columns.

![ alt text](img/levenestest.png)

### Shapiro-Wilk Normality Test Results

**Normality Check:**

- **City 1:** The p-value is 0.9480, which is greater than 0.05, indicating that the data is normally distributed.

- **City 2:** The p-value is 0.1150, which is greater than 0.05, indicating that the data is normally distributed.

- **City 3:** The p-value is 0.6759, which is greater than 0.05, indicating that the data is normally distributed.

![ alt text](img/levenestest2.png)

### Levene's Test for Equality of Variance

**The p-value is 0.0006, which is less than 0.05. This indicates that the variances of house prices across the three cities are significantly different.**

---

## Independent T-test or Two Sample T-test

Independent T-test also called two-sample T-test. It is a statistical method used to compare the means of two indenpendent groups to see statistically significant difference between them.

Why and When we should use it ?
- We use it to test hypotheses about group differences and it help us to understand any observed difference is real or due to random chance.
- There is two independent groups.
- Comparing the means of two numeric/continuous variable.
- Data should be normally distributed.
- Variances are assumed to be equal or testable.

### Dataset

Python code to generate a perfect dataset for performing an Independent T-test. We'll create two independent groups (Group A and Group B) with normally distributed data, ensuring that they have different means, which will give us a noticeable difference when performing the T-test.

        Score      Group
    0  54.967142     A
    1  48.617357     B
    2  56.476885     A
    3  65.230299     B
    4  47.658466     A

### Normality Test (Shapiro-Wilk Test)
**Normality Check:**

**Group A:** The p-value is 0.0.8290, which is greater than 0.05, indicating that the data is normally distributed.

**Group B:** The p-value is 0.2498, which is greater than 0.05, indicating that the data is normally distributed.
![ alt text](img/independent_t_1.png)

### Levene's Test for Equality of Variance

![ alt text](img/independent_t_2.png)

- The p-value is 0.5148 for Levene’s Test is greater than 0.05, which means we fail to reject the null hypothesis (H₀).

- The variances of Group A and Group B are not significantly different, and we can assume that both groups have equal variances. This is an important assumption for performing the Independent T-test.

### Independent T-test Result

- The p-value is 0.0000 extremely small (much less than 0.05), which means we reject the null hypothesis (H₀).

- There is a statistically significant difference between Group A and Group B. Since the p-value is extremely small, this result strongly indicates that the difference between the two groups is not due to random chance.

---
## Paired Sample T-Test (Before vs After Campaign)

A Paired Sample T-test (also known as the Dependent Sample T-test) is a statistical test used to compare the means of two related groups. The test is used to determine whether there is a statistically significant difference between the two related groups.

Why and When we should use it ?

- Paired Sample T-test when we want to assess the effect of a treatment or intervention on a group of subject by comparing therir measurements before and after the treatment or intervention.

- The same participants are measured in two conditions or at two points in time

- The observations are not independent but are paired based on some criteria

- **Before and After Studies:** When measuring the same group of individuals at two different times

- **Matched Pairs:** When each participant is matched with another participant who has similar characteristics, and you want to compare their responses in different conditions.

- **Repeated Measures:** When having repeated measurements from the same individuals under different conditions.

### Dataset
#### Data Summary
**Total Participants:** 30

**Columns:**

- **Participant:** Unique identifier for each participant (1 through 5).

- **Before Weight (kg):** The weight of each participant before the diet program.

- **After Weight (kg):** The weight of each participant after the diet program.

- **Weight Loss (kg):** The amount of weight lost by each participant.

- **Weight Loss (%):** The percentage of weight lost by each participant.

- **Difference :** Before Weight and After Weight difference 

### Shapiro-Wilk Test for Normality of Differences

`Shapiro-Wilk Test: Statistic = 0.984, p-value = 0.91296`

`The differences between before and after weights appear to be normally distributed. We fail to reject the null hypothesis of normality.`

**Since the p-value is greater than 0.05, we fail to reject the null hypothesis and conclude that the differences between the before and after weights appear to be normally distributed. This means the normality assumption for performing a Paired Sample T-Test is met.**

![ alt text](img/pairedsamplettest1.png)
![ alt text](img/pairedsamplettest3.png)

### Paired T-test Result

![ alt text](img/pairedsamplettest2.png)

`Paired Sample T-Test: T-statistic = 14.974, p-value = 0.00000`

`Reject the null hypothesis. There is a significant difference between before and after weights, indicating the diet program had an effect.`

**The p-value is less than 0.05, so we reject the null hypothesis and conclude that there is a significant difference between the before and after weights. This suggests that the diet program had a significant effect on the participants' weight loss.**

----

