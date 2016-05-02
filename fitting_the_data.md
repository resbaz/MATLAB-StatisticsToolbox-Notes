# Fitting the Data

We can make the observations from scatter plots & histograms more formal by looking at correlation values and pdf curves.

## Correlation

The function`xcorr(x,y)` gives the 

## Clustering

The function `kmeans` is a good "quick and dirty" way to segment data into groups. There are plenty of other more sophisticated options in the Machine Learning Toolbox.

``` Matlab
% Look up kmeans and use it to cluster the previous 
% data into two groups
```

## Probability

We can fit a pdf to our histograms using a kernel-density estimation (`ksdensity`), or we can check different types of distribution like Gaussian, exponential, etc (`fitdist`).

### *



## Regression

The function `glmfit` standards for generalised linear model fit and can be used for linear regression and log regression as well as a few more (binomial etc)
