# Randomness & Simulation

The command `rand`, `randn`, and `randi` can be used to generate random numbers (uniform, normally distributed, or integers respectively), which is useful for Monte Carlo simulations and other kinds of hypothesis testing.

To generate random numbers from a uniform distribution between [a b] we can use
``` Matlab
a = 0;
b = 1;
a + (b - a) * rand

ans =

    0.9058
```
And from a normal distribution with mean (mu) of 0 and standard deviation (sigma) of 1

``` Matlab
mu = 0;
sigma = 1;
randn(mu,sigma)

ans =

   -2.2588
```

To generate random integers on the range [a b] we can use
``` Matlab
a = -10;
b = 10;
randi([a b])

ans =

     9
```
### *Challenge*
```Matlab
% CHALLENGE
% Work out how to use the rand, randn and randi commands
% to generate a random matrix instead of a
% single numbers
```