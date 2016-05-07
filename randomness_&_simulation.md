# Randomness & Simulation

The command `rand` and `randn` can be used to generate random numbers (uniform or normally distributed respectively), which is useful for Monte Carlo simulations or permutation testing.

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

