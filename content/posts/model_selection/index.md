---
title: "Model Selection"
date: "2022-02-28"
description: "An overview of selection methods for linear models"
---

## Understanding Submodels

We assume that there is a given _correctly specified_ model.

$$
E[y|x] = x^T\beta = x_1\beta_1 + ... + x_p\beta_p
$$

We want to be able to find (if existing) submodels that have **fewer terms** and are _"almost as good"_.
- We use $I$ to be the subset of terms included in the submodel and $D$ to be those that we remove or *D*elete.

* Now the full mean function is: 

$$
E[y|x] = {x^T}_I{\beta_I}+{x^T}_D{\beta_D}
$$

where the mean function for the submodel is the first part of this equation.

*Note: "Good models" will have a $RSS_I$ close the the $RSS$ of the full model, and $p_I$ as small as possible.*

## Selection Criteria

From the *Note* above, we cannot achieve both of these goals well at the same time, so the selection criteria help handle this tradeoff.

### Mallows' $C_I$

$$
C_I = \frac{RSS_I}{s^2} + 2p_I - n
$$

with the equivalent expression

$$
C_I = \frac{RSS_I-RSS}{s^2} + p_I - p_D = ... = p_D(F_D-1)+p_I
$$

where the subscript $I$ refers to the statistics calculated from the submodel. 
* And $F_D$ is the F-statistic for testing the null hypothesis $H_0$ that $\beta_D = 0$

* Good candidates for the submodels will have 

$$
F_D \leqslant 1
$$

which is equivalent to $C_I \leqslant p_I$

### (AIC) Akaike Information Criterion

* Closely related to $C_I$ where we aim to minimise 

$$
AIC_I = -2L_I + p_I
$$

* Can be seen as a maximum likelihood technique that penalises large values of $p_I$

### Minimising the Residual Mean Square

$$
{s_I}^2 = \frac{RSS_I}{df_I}
$$

with $df_I = n - p_I$.

* This selects the submodel with the smallest estimated error variance $\sigma^2$

### Turkey's Rule

* Similarly, now we want to minimise

$$
{s_I}^2/{df_I} = \frac{RSS_I}{(n-p_I)^2}
$$