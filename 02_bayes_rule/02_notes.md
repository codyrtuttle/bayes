# Week 2 Reading/Lecture Notes

## Statistical Rethinking Lecture 2: Bayesian Inference

### cartoon examples for context

Ex: trying to calculate water proportion on Earth
- process: spin the globe, randomly land on land or water, record which
- each proportion guess is a possible explanation of the data (see below)

- Bayesian data analysis
  - For each possible explanation of the data,
  - count all the ways data can happen.
  - Explanations with more ways to produce the data are more plausible

Ex: 
- bag contains 4 marbles, either blue or white
- 5 combinations possible
- we observe:
  - B,W,B
- Process: 
  - assume 1 B and 3 W
  - draw all possible events to get that combination 
    - four possibilities on the first draw
    - sixteen possibilities on the second
    - 64 possible on the third
  - assuming B first draw, one way that can happen on first draw
    - three possibilities for W second 
    - three on the the third for B third
  - thus, there are 3 possible ways to produce BWB observation (because three on the third draw)
    - 8 possible paths for BBWW
    - 9 for BBBW

Counts to plausibility
- unglamorous basis of applied probability
- things that can happen more ways are more plausible

Possible composition | p | ways to produce data | plausibility
WWWW | 0 | 0 | 0
BWWW |0.25 | 3 | 0.15
BBWW | 0.5 | 8 | 0.40
BBBW |0.75 | 9 | 0.45
BBBB | 1 | 0 | 0

```{r to-get-plausibilities}
ways <- c(3, 8, 9)
ways/sum(ways)
```

Updating 
- another B draw
- 0, 1, 2, 3, 4 ways to produce this given conjectures of bag combos
- multiply new counts by previous counts to get updated counts
- Rules
  - state a causal model for how the observations arise, given each possible explanation
  - count ways data could arise for each explanation
  - relative plausibility is relative value from 2

Back to water proportion
- for each possible proportion of water, 
- count number of ways data could happen
- must state how obs are generated

- if you randomly land on L
- density line on proportion water is straight diagonal line from high to low
- if you randomly land on W
- density line on proportion water is straight diagonal line from low to high

- relative plausibility of the combination LW is multiplying those lines together 
- resulting curve is the posterior distribution
  - has all relevant information for making inference because it's normalized (area under the curve is always 1)
  - more data (sample size) makes the curve taller and thinner
- no point estimate - the distribution is the estimate
  - can take the mode, mean
  - always use the entire distribution in the analysis
  - summary is the last step
- no one true interval - infinite number of intervals

- density: relative plausibility of proportion of water

### Formalities
- in practice we write the model in a way that communicates all of the probability assumptions
- the observations (data) and explanations (parameters) are variables
- for each variable, must say how it is generated

Data: W and L, the number of water and land obs
- Pr(W,L|p) = ((W + L)! / W!L!)(p^W)(1 - p)^L
- binomial probability function 
  - `{r} dbinom(W, W + L, p)
- parameters: p, the proportion of water on the globe
  - Pr(p) = (1 / 1 - 0) = 1 
    - relative plausibility of each possible p
- Posterior is (normalized) product:
  - Pr(p|W, L) = ((Pr(W,L|p) Pr(p)) / Pr(W, L))
    - relative plausibility of each possible p after learning W, L

With Numbers
- Ignore the math and draw the owl
  1. For each possible value of p
  2. compute product Pr(W, L|p)Pr(p)
  3. relative sizes of products in 2 are posterior probabilities

From posterior to prediction
- implications of model depend upon the entire posterior
- must average any inference over entire posterior
- this usually requires integral calculus
- OR we can just take samples from posterior
  - sample from posterior, compute desired quantity for each sample, profit
  - much easier than integrals
  - turns a calculus problem into a data summary problem
  - MCMC produces only samples anyway

Bayesian modesty
- no guarantees except logical
- probability theory is a method of logically deducing implications of data under assumptions that you must choose
- any framework selling you more is hiding assumptions