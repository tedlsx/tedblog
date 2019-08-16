---
title: Generalized Linear Model
date: 2019-08-08 09:04:51
tags:
---

Objective:
* General linear model (GLM) used to predict response variables with both continuous or discrete distribution and response variables can have linear or non-linear relationship with explanatory variables. 

Model structure: 
* GLM includes three parts. Random component, Systematic component, Link function.

Assumption:  
* $y_i$ is independent and typically assumed to follow an [exponential family](https://tedlsx.github.io/2019/08/06/exp=family/) distribution with $\mu_i$. 
* GLM assumes transformed dependent variables (through link function) and independent variables has a linear relationship. 
* Error $\epsilon_i$ should be independent but not normally distributed.

Parameter estimate: 
* $x_i$ as covariates and $\beta$ for coefficients

Model selection: 
* feature selection 

Model fit: 
* Least square 
<!--more-->

## Generalized Linear Models (GLM)
| Model | Random | Link | Systematic |
| ----- | ------ | ---- | -----------|
| linear regression | normal | identity | continuous |
| ANOVA | normal | identity | ategorical |
| logistic regression | binomial | logit | mixed |
| loglinear | poisson | log | categorical |
| poisson regression | poisson | log | mixed |
| multinomial response | multinomial | generalized logit | mixed |

Introduction of 3 components of any GLM:
random component: which is the probability distribution of response variable Y

systematic component: show the explanatory variables $(x_1,x_2,..,x_k)$ in the model. And GLM has a strong assumption that $\eta=\beta x$, which means the natural parateter $\eta$ in exponential family should equal to linear predictor (design choice). 

link function: $\eta$ or $g(u)$ - refer to the link between random and systematic components. In another words, it shows how response variables change based on explanatory variables. It can be a non-linear function. In addition, the inverse function $g^{-1}(\eta)=\mu$ is the response function which can reflect linear predictor to the target $y$.

Then we look some examples for GLM component:

### simple linear regression

$$y_I = \beta_0 + \beta x_i + \epsilon_i$$

* Random component: Y is dependent variable and has $y\sim N(\eta,\sigma_e^2)$, $\epsilon_i \sim N(0,\sigma^2)$
* Systematic component:  independent variable X typically be continuous and linear predictor is $\eta = \beta x_i$ 
* Link function: identity link , $\eta=g(E(y_i))=E(y_i)$, this is the simple link function which model the mean directly. Hypothesis $h(x) = E(y|x,\beta)=\mu=g^{-1}(\eta)=\mu$

### Logistic regression

$$logit(\pi)=log(\frac{\pi}{1-\pi})=\beta_0+\beta x_i$$
which is the log odds of probability of "success" as a function of explanatory variables.

* Random component: The distribution of Y is assumed as $Bernoulli(\pi)$, $\pi$ is probability of "success"
* Systematic component: X is independent variables typically be discrete, linear predictor is $\eta = \beta x_i$  
* link function: Logit function, $\eta = logit(\pi)=log(\frac{\pi}{1-\pi})$ which models the log odds of the mean($\mu$). Hypothesis $h(x_i)=E(y_i|\beta,x_i) = sigmoid(\eta_i)$

### Log-linear model
$$log(\mu_{ij}) = \lambda + \lambda_i^A + \lambda_j^B + \lambda_{ij}^{AB}$$

* Random component: The distribution of counts, follows Poisson distribution
* Systematic component: Independent variable X is discrete and is linear in parameters $\lambda + \lambda_i^{x_i}+...+ \lambda_n^{x_n}$
* Link function: Log link, $\eta = log(\mu)$ which model the log of mean.

## Advantage of GLM over OLS(ordinary least square)
* There is no need to transform the respose $Y$ to have normal distribution.
* Variance no need to be constant