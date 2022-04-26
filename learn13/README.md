# Learning-Journal - 13

## Overview

***Regression***
<br>
Regression analysis is one of the most important fields in statistics and machine learning.
There are many regression methods available.
Linear regression is one of them.

***Linear Regression***<br>
Linear regression is probably one of the most important and widely used regression techniques.
It’s among the simplest regression methods.
One of its main advantages is the ease of interpreting results.

## Summary

<ins> **sklearn.linear_model.LinearRegression** </ins>
<br><br>

<hr>

**Parameters**

<br>
<br>

**fit_interceptbool, default=True**<br>
Whether to calculate the intercept for this model. If set to False, no intercept will be used in calculations (i.e. data is expected to be centered).

**normalizebool, default=False**<br>
This parameter is ignored when fit_intercept is set to False. If True, the regressors X will be normalized before regression by subtracting the mean and dividing by the l2-norm. If you wish to standardize, please use StandardScaler before calling fit on an estimator with normalize=False.

**copy_Xbool, default=True**<br>
If True, X will be copied; else, it may be overwritten.

**n_jobsint, default=None**<br>
The number of jobs to use for the computation. This will only provide speedup in case of sufficiently large problems, that is if firstly n_targets > 1 and secondly X is sparse or if positive is set to True. None means 1 unless in a joblib.parallel_backend context. -1 means using all processors. See Glossary for more details.

**positivebool, default=False**<br>
When set to True, forces the coefficients to be positive. This option is only supported for dense arrays.

**coef_array of shape (n_features, ) or (n_targets, n_features)**<br>
Estimated coefficients for the linear regression problem. If multiple targets are passed during the fit (y 2D), this is a 2D array of shape (n_targets, n_features), while if only one target is passed, this is a 1D array of length n_features.

**rank_int**<br>
Rank of matrix X. Only available when X is dense.

**singular_array of shape (min(X, y),)**<br>
Singular values of X. Only available when X is dense.

**intercept_float or array of shape (n_targets,)**<br>
Independent term in the linear model. Set to 0.0 if fit_intercept = False.

**n_features_in_int**<br>
Number of features seen during fit.

---

***Example***

```python
>>> import numpy as np
>>> from sklearn.linear_model import LinearRegression
>>> X = np.array([[1, 1], [1, 2], [2, 2], [2, 3]])
>>> # y = 1 * x_0 + 2 * x_1 + 3
>>> y = np.dot(X, np.array([1, 2])) + 3
>>> reg = LinearRegression().fit(X, y)
>>> reg.score(X, y)
1.0
>>> reg.coef_
array([1., 2.])
>>> reg.intercept_
3.0...
>>> reg.predict(np.array([[3, 5]]))
array([16.])
```