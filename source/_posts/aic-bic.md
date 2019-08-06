---
title: AIC and BIC
date: 2019-07-29 11:51:17
tags:
---

## AIC 


## Note 
As you know, AIC and BIC are both penalized-likelihood criteria. They are sometimes used for choosing best predictor subsets in regression and often used for comparing nonnested models, which ordinary statistical tests cannot do. The AIC or BIC for a model is usually written in the form 
<div style="text-align:center">
<img src="https://latex.codecogs.com/svg.latex?\Large&space;AIC=-2ln(\hat{L}) + 2k"/>
</div>
<p align="center">
<img src="https://latex.codecogs.com/svg.latex?\Large&space;BIC=-2ln(\hat{L}) + ln(n)k"/>
</p>

where $\hat{L}$ is the max value of likelihood function for the model, n is the number of data points(observations), and k is number of estimated parameter.

where $\hat{L}$ is the max value of likelihood function for the model. And likelihood function is how likely particular values of statistical parameters are for a given set of observations and is defined as 
<p align="center">
<img src="https://latex.codecogs.com/svg.latex?\Large&space;L(\theta | x) = f(x | \theta)"/>
</p>


where $f(x | \theta)$ is joint probability density function, $k$ is the number of estimated parameter in our model.

For AIC information criterion, it contains information of goodness which is represented in likelihood. And AIC also include the penalty part of number of estimated parameter as a increasing function. As we know increasing the number of parameters in the model almost always improves the goodness of the fit, the penalty discourages overfitting.

AIC is an estimate of a constant plus the relative distance between the unknown true likelihood function of the data and the fitted likelihood function of the model, so that a lower AIC means a model is considered to be closer to the truth. BIC is an estimate of a function of the posterior probability of a model being true, under a certain Bayesian setup, so that a lower BIC means that a model is considered to be more likely to be the true model. Both criteria are based on various assumptions and asymptotic approximations. Each, despite its heuristic usefulness, has therefore been criticized as having questionable validity for real world data. But despite various subtle theoretical differences, their only difference in practice is the size of the penalty; BIC penalizes model complexity more heavily. The only way they should disagree is when AIC chooses a larger model than BIC.

AIC and BIC are both approximately correct according to a different goal and a different set of asymptotic assumptions. Both sets of assumptions have been criticized as unrealistic. Understanding the difference in their practical behavior is easiest if we consider the simple case of comparing two nested models. In such a case, several authors have pointed out that IC’s become equivalent to likelihood ratio tests with different alpha levels. Checking a chi-squared table, we see that AIC becomes like a significance test at alpha=.16, and BIC becomes like a significance test with alpha depending on sample size, e.g., .13 for n = 10, .032 for n = 100, .0086 for n = 1000, .0024 for n = 10000. Remember that power for any given alpha is increasing in n. Thus, AIC always has a chance of choosing too big a model, regardless of n. BIC has very little chance of choosing too big a model if n is sufficient, but it has a larger chance than AIC, for any given n, of choosing too small a model.

So what’s the bottom line? In general, it might be best to use AIC and BIC together in model selection. For example, in selecting the number of latent classes in a model, if BIC points to a three-class model and AIC points to a five-class model, it makes sense to select from models with 3, 4 and 5 latent classes. AIC is better in situations when a false negative finding would be considered more misleading than a false positive, and BIC is better in situations where a false positive is as misleading as, or more misleading than, a false negative.

