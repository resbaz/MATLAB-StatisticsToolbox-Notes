# Fitting the Data

We can make the observations from scatter plots & histograms more formal by looking at correlation values and pdf curves.

## Correlation
The function `corr(x,y)` gives the pairwise correlation coefficient between the column vectors `x` and `y` (they have to be columns).

``` Matlab
x = 1:10;
y = 10:-1:1;

% take the transpose so they are columns
corr(x',y')

ans =

    -1
```



The function`xcorr(x,y)` gives the cross-correlation between two time series `x` and `y`.

### *Challenge*
``` Matlab
% CHALLENGE
% What is the correlation value between Bourke Street North
% and Bourke Street South?
% Check the linear 

% EXTENSION

```

## Clustering

The function `kmeans` is a good "quick and dirty" way to segment data into groups. There are plenty of other more sophisticated options in the Machine Learning Toolbox.

### *Challenge*
``` Matlab
% CHALLENGE 
% Look up kmeans and use it to cluster the previous 
% data into two groups
```

## Probability

We can fit the probability density function to our histograms using a kernel-density estimation (`ksdensity`), or we can check the fit of specific distribution shapes, such as Gaussian, exponential, etc (`fitdist`).

### *Challenge*
``` Matlab
% CHALLENGE
% Fit a normal distribution to each of the clusters
```


## Regression

The function `glmfit` standards for generalised linear model fit and can be used for linear regression and log regression as well as a few more (binomial etc)
