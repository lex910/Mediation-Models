# Mediation-Models
Estimating mediation models and generating confidence intervals for mediation effects 

### What is mediation?

Mediation is when the effect of the independent variable on the dependent variable goes through an additional mediating variable. There is a direct effect of the independent variable in the dependent variable as well as an indirect effect that goes through the mediating variable before having an effect on the dependent variable. The mediating variable acts as both a dependent and an independent variable.

### How did we estimate the mediation models?

We estimate mediation models by running multiple linear regression models to account for mediators effects with the independent variables on the dependent variable. We first have to estimate the mediator regression using the lag of awareness. We need to use lag because previous awareness of a product influences current awareness and how effective out of home and social media advertising will be. We then regress lag awareness on both independent variables, out of home and social media advertising. For the last regression we can run a regression of the dependent variable lag sales, on awareness, out of home advertising, social media advertising, and add in the two control variables of temperature and covid stringency. We have to use lag sales because previous sales will have an effect on current sales.
Next, we can make estimates of the steady state effects using the output from the linear regression summaries by calculating beta/(1-lambda). The steady states are estimated for the a1 path: OOH->awareness, a2 path: social-> awareness, b path: awareness->sales and the direct paths of c1: OOH->sales, and c2 path social->sales. To find the mediation effects we multiply a1*b and a2*b. We can then estimate the total effect by adding the direct effects to the mediating effects.

### How were the 95% CI’s computed?
When mediation variables are added to a model, we calculate confidence intervals because the interaction of the independent variables with the mediating variables (a x b) are not normally distributed and we do not know the distribution. When we do not know the distribution, bootstrap methods are usually useful to estimate confidence intervals. However, the addition of lag variables leads to problems when implementing both data and residual bootstrap. Monte Carlo inference becomes the method of choice to compute confidence intervals. Only aware->sales shows significance because the confidence interval does not contain zero.
1. Find the asymptotic covariance matrix of the parameter estimates related to indirect effects (using vcov function)
2. The above matrix is then used to simulate a sampling distribution of the indirect effect using repeated sampling
3. Percentiles from this distribution are then utilized to build a confidence interval


### CIs for mediation effects, direct effects, total effects 
![Screenshot 2024-06-19 at 2 20 19 PM](https://github.com/lex910/Mediation-Models/assets/101606445/ee513a9d-7796-46f6-8698-2c0fd8d85e4c)
