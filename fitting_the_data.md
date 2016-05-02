# Fitting the Data

## Correlation & Probability
We're going to make our scatter plots & histograms more formal by looking at correlation values and pdf functions.

Look up `xcorr(x,y)` returns 

We can fit a pdf to our histograms using a kernel-density estimation (`ksdensity`), or we can check different types of distribution like Gaussian, exponential, etc (`fitdist`).

### Kernel density




## Clustering

The function `kmeans` is a good "quick and dirty" way to segment data into groups. There are plenty of other more sophisticated options in the Machine Learning Toolbox.

## Regression

The function `glmfit` standards for generalised linear model fit and can be used for linear regression and log regression as well as a few more (binomial etc)
