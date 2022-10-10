# Week 1 Reading/Lecture Notes

## Statistical Rethinking Lecture 1: Golem of Prague (video)

- Traditional statistical models and concepts are golems 
  - powerful but have no intellect - dangerous when used incorrectly
  - limiting
  - focus on rejecting null hypothesis, instead of research hypotheses
    - place for null hypothesis, but no as the baseline to reject
  - best in industrial, very organized experimental settings where assumptions can be clearly met
- Better science starts with hypotheses, moves to process models and causal pathways, which leads to statistical models
  - the same hypothesis can have multiple competing causal process models, and will probably lead to different statsitical models
- Lots of applications don't have valid unique null models 
  - they necessitate process models 
    - which necessitate statistical models that are justified by process models and question (estimand - what we want to know)
- This class will be about drawing the owl
  - flesh out assumptions and details of models
  - code it all out
  - understand what the models are about
  - documenting work and reducing error

- Drawing the Bayesian owl
1. Theoretical estimand
   1. what are you trying to learn
2. Scientific causal model(s)
3. Use estimand and scientific models to build statistical model(s)
4. Simulate from 2 to validate that 3 yields 1
5. Analyze real data
   1. data are entered at the last step

- Why Bayes?
  - Bayesian approach is very flexible and permissive
  - express uncertainty at all levels 
  - direct solutions for measurement error and missing data
  - focus on scientific modelling, rather than the null model

- not interested in Bayes vs frequentist fight
- it's about Bayes of course, but the important part is the causual inference
  - connecting the causal model to the statistical model

- The reasons for a statistical analysis are not found in the data themselves, but in the causes of the data
  - the causes of the data cannot be extracted from the data alone
  - no causes in no causes out

- Even when a goal is descriptive, need causal model
  - need causal information about how the sample differs from the population
  - describing the population requires causal thinking

- Causal inference is a prediction of an intervention
  - knowing a cause means being able to predict the consequences of an intervention in a system
- It's an imputation of missing observations
  - knowing a cause means being able to construct unobserved counterfactual outcomes

- DAGs are hueristic causal models
  - clarify scientific thinking
  - different scientific questions require different models
  - clarify which control variables you need to include 
    -  there are absolutely bad controls


 - A summary
   - Golems are brainless powerful statistical models
   - Owls: documented objective procedures
   - DAGs are transparent scientific assumptions to 
     - justify scientific effort
     - expose it to critique
     - connect theories to golems

## Bayes Rules chapter 1: The big Bayesian picture
- A Bayesian analysis assesses the uncertainty of the hypothesis given the observed data
- A frequentist analysis assesses the uncertainty of the data given the assumed hypothesis