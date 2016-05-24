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

We can also use `glmfit` for logistic regression, using the options 'binomial' and 'logit'. For an example, let's look at separating two Gaussian distributions.

```Matlab
% use randn to make two fake distributions
mu1 = 1;
sigma1 = 0.5;
mu2 = 2;
sigma2 = 1;
x1 = mu1 + sigma1 * randn(100,1);
x2 = mu2 + sigma2 * randn(100,1);
```

Now we need to treat them as one variable, and create a model that predicts class 1 (x1) or class 2 (x2).

``` Matlab
% this is our input
X = [x1 ; x2];

% this is our class label
% 0 = class 1
% 1 = class 2
Y = [zeros(size(x1)) ; ones(size(x2))];

% fit a logistic regresion model
log_model = glmfit(X,[Y ones(size(Y))],'binomial','link','logit')

log_model =

   -2.9920
    2.0685
```

The model contains an intercept, $$w_0$$ and weights for the input (only one dimension in our case - $$w_1$$) and is given by:
$$ \mathrm{output} = \frac{1}{1 + \exp\left(-(w_0 + w_1X)\right)}$$

So to get the output of our model
```Matlab
% apply our weights
input = log_model(1) + log_model(2)*X;

% run the model
output = 1 ./ (1 + exp(-input));
```

The output is between 0 and 1. It is usual to classify the input as class 1 (or Y = 0) for output < 0.5 and class 2 (or Y = 1) for output > 0.5. 

Let's plot the results. We'll make class 2 red, and class 1 blue. We'll make the true predictions circles and the false ones crosses.

``` Matlab
% these are correctly predicted values for class 2
% we'll make class red 
plot(X(output >= 0.5 & Y == 1),'ro')
hold on
% these are the correctly predicted values for class 1
plot(X(output < 0.5 & Y == 0),'bo')

% now the incorrect predictions for 
% class 2 and class 1
plot(X(output >= 0.5 & Y == 0),'rx')
plot(X(output < 0.5 & Y == 1),'bx')
```

We can also count how many we got right and wrong

``` Matlab
% wrong
Nwrong = sum(output >= 0.5 & Y == 0) + sum(output < 0.5 & Y == 1);

Nright = sum(output >= 0.5 & Y == 1) + sum(output < 0.5 & Y == 0);
```

### *Challenge*
``` Matlab
%% CHALLENGE
% Using logistic regression to distinguish between
% two Gaussians with different means 
% ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
% Use 80% of your data from Flinders street 
% station between 8am - 9am to fit a logistic
% regression model

% Run your model on the remaining 20% of the data
% and classify it as either a weekend or weeday

%% EXTENSION
% how accurate is your classifier?

%% EXTENSION
% make your accuracy measure more robust using
% k-fold cross validation
% That means running your entire code (fit model,
% run model, test performance) in a loop. 
% For each loop use a different partition of data
% to train and test. With 10 loops, train on 
% 90% of the data, and test on 10%.
% With 5 loops, train on 80% of the data and 
% test on 20%.

```

## Testing Gaussians
Many standard tests are built into MATLAB. For example, to test if data are normally distributed we can use `kstest`.

Another common test is `ttest2` (two-sampled t-test) and its non-parametric cousin `ranksum` (Wilcoxon rank sum / Mann-Whitney U test - why do statisticians like to name everything after themselves?).

### *Challenge*
``` Matlab
%% CHALLENGE
%Check if the weekday pedestrian count data from
%Southern Cross station and Flinders Street
%station is normally distributed.

%% CHALLENGE
%Check if there is any difference between the two
%distributions? Use ttest2 if the data are normal,
%or ranksum if they are not.
```