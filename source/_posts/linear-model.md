---
title: Multiple Linear Model
date: 2019-08-05 15:04:51
tags:
---

## Multiple Linear Regression Model
Multiple linear regression is a linear model with more than 1 variable. These variables are called dependent variables and the predict variable is called independent variables.

Where the formula for Multiple linear regression model is:
<p align="center">
<img src="https://latex.codecogs.com/svg.latex?\Large&space; y_i=\beta_0+\beta_1x_{i1}+\beta_2x_{i2}+...+\beta_nx_{ip}+\epsilon_n"/>
</p> 
for i = 1,...,n is the number of observations or data. p is the number of dependent variables. 

Hence the matrix notation for multiple linear regression is:

<p align="center">
<img src="https://latex.codecogs.com/svg.latex?\Large&space; 
\begin{bmatrix}
    y_1 \\
    y_2 \\
    \vdots \\
    y_n
\end{bmatrix}
=\begin{bmatrix}
    1 & x_{11} & x_{12} & \dots  & x_{1n} \\
    1 & x_{21} & x_{22} & \dots  & x_{2n} \\
    \vdots & \vdots & \vdots & \ddots & \vdots \\
    1 & x_{d1} & x_{d2} & \dots  & x_{dn}
\end{bmatrix}
\begin{bmatrix}
    \beta_0 \\
    \beta_1 \\
    \vdots \\
    \beta_n
\end{bmatrix}
+
\begin{bmatrix}
    \epsilon_1 \\
    \epsilon_2 \\
    \vdots \\
    \epsilon_n
\end{bmatrix}
"/>
</p> 

Which can also write in simple statement:
 <p align="center">
<img src="https://latex.codecogs.com/svg.latex?\Large&space; Y=X \beta+\epsilon"/>
</p> 

Using leat square, we need to minimise this function 
 <p align="center">
<img src="https://latex.codecogs.com/svg.latex?\Large&space; \sum_{i=1}^{n}\epsilopn_i^2=\epsilon^T\epsilon=(y-X\beta)^T(y-X\beta)"/>
</p>

To find the 'best'  $\beta$

 <p align="center">
<img src="https://latex.codecogs.com/svg.latex?\Large&space; \hat{Y}=X \hat{\beta}"/>
</p> 

![A test image](linear-model/orth.png)

Then the residuals $y-\hat{y}$ are [orthogonal](http://mathworld.wolfram.com/Orthogonal.html) to the columns of $X$:

<p align="center">
<img src="https://latex.codecogs.com/svg.latex?\Large&space; X^T(y-X\hat{\beta})=0"/>
</p>
<p align="center">
<img src="https://latex.codecogs.com/svg.latex?\Large&space; \Leftrightarrow X^Ty-X^TX\hat{\beta}=0"/>
</p> 
<p align="center">
<img src="https://latex.codecogs.com/svg.latex?\Large&space; \Leftrightarrow X^TX\hat{\beta}=X^Ty"/>
</p> 

Then we can define 
<p align="center">
<img src="https://latex.codecogs.com/svg.latex?\Large&space; \hat{\beta}=(X^TX)^{-1}X^TXy"/>
</p> 

This of course works only if the inverse exists. If the inverse does not exist, the normal equations can still be solved, but the solution may not be unique.

For fitted $\hat{y}$, we can plug in the $\hat{\beta}$

<p align="center">
<img src="https://latex.codecogs.com/svg.latex?\Large&space; \hat{y}=X\hat{\beta}=X(X^TX)^{-1}X^Ty=Hy"/>
</p> 

The matrix $H$ (Hat-matrix) is a $n*n$ matrix, it maps the observed values $y$ onto the fitted value $\hat{y}$

And residuals can be written as 
<p align="center">
<img src="https://latex.codecogs.com/svg.latex?\Large&space; \epsilon=y-\hat{y}=y-X\hat{\beta}=y-Hy=(I-H)y"/>
</p> 

Then we can try an example:

