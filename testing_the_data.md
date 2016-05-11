# Testing the Data

## Linear Regression

The function `glmfit` standards for generalised linear model fit and can be used for linear regression and log regression as well as a few more (binomial etc).

For linear regression `regress` is also a good place to start.

``` Matlab
% normalize to zero mean, unit variance
BourkeN = (BourkeN - mean(BourkeN)) ./ std(BourkeN);
BourkeS = (BourkeS - mean(BourkeS)) ./ std(BourkeS);

regress(BourkeN_norm,BourkeS_norm)

ans =

    0.9540
```

Compare to `glmfit` to get a slope and intercept

``` Matlab
linear_coeff = glmfit(BourkeN,BourkeS)

linear_coeff =

    8.6732
    1.0535

scatter(BourkeN,BourkeS)
hold on;
plot(BourkeN, linear_coeff(1) + linear_coeff(2) * BourkeN)
```

You can also access test statistics:

```Matlab
[linear_coeff,~,stats] = glmfit(BourkeN,BourkeS);
```

### *Challenge*

``` Matlab
%% CHALLENGE 1
% Get regress to output upper and lower bounds 
% on the estimate
% ie [coeff,bounds] = regress()

%% CHALLENGE 2
% Use glmfit to output confidence limits and 
% plot them as dashed lines on your plot
% HINT: use the standard error (se) in the output
% statistics of glmfit

% What other stats can you get from glmfit?
```
There is also a function (I think it is for people who like Stata) that will print statistics into the command window

``` Matlab
fitlm(BourkeN,BourkeS)

ans = 


Linear regression model:
    y ~ 1 + x1

Estimated Coefficients:
                   Estimate       SE        tStat       pValue  
                   ________    _________    ______    __________

    (Intercept)    8.6732         2.2884      3.79    0.00015081
    x1             1.0535      0.0015121    696.72             0


Number of observations: 47950, Error degrees of freedom: 47948
Root Mean Squared Error: 366
R-squared: 0.91,  Adjusted R-Squared 0.91
F-statistic vs. constant model: 4.85e+05, p-value = 0
```
## Logistic regression
## Testing Gaussians
Many standard tests are built into MATLAB. Eg to test if data is normally distributed we can use 