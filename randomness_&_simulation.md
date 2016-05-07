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
%% CHALLENGE
% Work out how to use the rand, randn and randi commands
% to generate a random matrix instead of a
% single numbers


%% EXTENSION
% Write a function that simulates the output of a dice being
% rolled. If you want, give your function an input Nd, 
% which indicates how many die to roll.
% e.g.

dice(5)

ans =

     1     4     6     1     2
```

Using random numbers in a loop is a major part of running simulations. For example let's say there is a panel of 10 scientists at a conference, and two of them are women. How likely is it that that the outcome would happen by chance?

We can simulate one million random panels to check.
``` Matlab
% 1 million trials
Ntrials = 1e6;
% intialize count of women in the panel
Nwomen = zeros(1,Ntrials);

for n = 1:Ntrials
    
    % generate a random panel
    panel = rand(1,10);
    % let the probability a member is a woman be 50%
    Nwomen(n) = sum(panel > 0.5);
    
end

% plot the result
histogram(Nwomen,-0.5:10.5,'normalization','pdf')
```

The probability that the panel has less than three women is 

```Matlab
100 * sum(Nwomen <= 2) / Ntrials

ans =

    5.4748
```

### *Challenge*
The birthday party problem is a classic example of how humans can underestimate chance events.

How many people do you need to have in a room for there to be a more than 50% chance that two of them will have the same birth date? (Assume every birth date is equally likely).

``` Matlab
% CHALLENGE
% Use a simulation to numerically estimate the answer
% to the birthday party problem
```
