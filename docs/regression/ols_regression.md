---
sidebar_position: 6
---
# Ordinary Least Square

1. Assumption

- Linear relationship: $$ Y = \beta_0 + \beta_1  X_1 + \beta_2 X_2 + \beta_3 X_3 + e $$

Y = dependent variable
X1, X2, X3 are independent variable
e = error terms

- No multicolinearti:
This assumption for OLS means that the error terms from each observation will be independent of each other.

Assume we have these two observations from the dataset $ ( y_1, X_{11}, X_{21}, X_{31} )$ and $ ( y_{2}, X_{12}, X_{22}, X_{32} ) $. We can plug these two observations into an OLS regression model system.

$$ y_{1} = \beta_{0} + \beta_{1}  X_{11} + \beta_{2}  X_{21} + \beta_{3} X_{31} + e_{1} $$

$$ y_{2} = \beta_{0} + \beta_{1} X_{12} + \beta_{2} X_{22} + \beta_{3} X_{32} + e_{2} $$

This assumption states that $e_{1}$ and $e_{2}$ are independent of each other. If they are not independent, we call them **autocorrelated**.

- Error terms are normallty distributed
From our example, this means that $e_{1}$ and $e_{2}$ have to be normally distributed.

- Expected values of error terms are 0
From our example, the expected values of $e_{1}$ and $e_{2}$ have to be $0$.

- Error Terms Have the Same Variance (Homoscedasticity)

When the variances of error terms are constant, we call the error terms **homoscedastic.** If the error terms are not constant, we call them **heteroskedastic.**

With all the above assumptions about error terms, we usually call the error terms **IID: independent and identically distributed**. With the assumptions of 1.4, 1.5, and 1.6, we can summarize the error terms as follows: