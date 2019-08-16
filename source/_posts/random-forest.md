---
title: Random Forest
date: 2019-08-06 11:21:35
tags: classification
math: true
---
Introduction of random forest and decision tree. Talking about their advantage and disadvantage. 
<!--more-->
# Introduction of Random Forest

RF(random forest) is one of the classification method. And it consists of many random decision trees. The "random"  in RF means it used random sample of original data and also used random subset features to build the model.    

It has several advantage:
* RF includes 2 randomness which makes model not too overfitted and good to avoid noise
* In high dimensional problems, we do not need to do the feature selection and dimension reduction.
* Can also give the importance to each classification
* RF can both works on continuous and categorical data
* It generates an internal unbiased estimate of the generalization error as the forest building progresses

# Introduction of Decision Tree
DT(decisiona tree) is a tree-like graph and decision model which produce the events outcome, resource costs and utility. DT is a supervised learning methods and are adaptable at solving any kind of problem (classification or regression).

When split the node into sub-nodes, DT should decide which classification should be top. Here we need use Gini importance: for each split at variable m, the child nodes should has smaller gini impurity criterion than the parent node.

## DT algorithm
The DT algorithms refered as CART(classification and regression trees).

In [skit-learn](https://scikit-learn.org/stable/modules/tree.html)
~~~ python
from sklearn.datasets import load_iris
from sklearn import tree
iris = load_iris()
clf = tree.DecisionTreeClassifier()
clf = clf.fit(iris.data, iris.target)

tree.plot_tree(clf.fit(iris.data, iris.target)) 
~~~

# How Random Forests work
It used [out-of-bag(oob)](https://www.stat.berkeley.edu/~breiman/RandomForests/cc_home.htm#inter) error to get the unbiased estimate and find the importance of variables.

Also use Gini to find the variables when split from top to down.

## Bagging and Boosting
RF belongs to Ensemble Learning in Machine Learning where Ensemble Learning has 2 major algorithms as Bagging and Boosting

### Bagging
* Using Bootstrapping randomly take n training samples(random draw with replacment). Repeating k times which we can get k training sets. (all k sets are independent)

* For k trainign sets, we get k models

* For classification problem, use voting. For regression problems, use average of the results.

### Boosting 
* 123123

