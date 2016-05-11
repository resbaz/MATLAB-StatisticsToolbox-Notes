# Testing the Data

## Regression

The function `glmfit` standards for generalised linear model fit and can be used for linear regression and log regression as well as a few more (binomial etc).

For linear regression `regress` is also a good place to start.

``` Matlab
BourkeN = (BourkeN - mean(BourkeN)) ./ std(BourkeN);
BourkeS = (BourkeS - mean(BourkeS)) ./ std(BourkeS);
regress(Y,X)
```