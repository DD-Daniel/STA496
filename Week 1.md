# **Week 1 Note:**

**End of week summary**: The area of my interest is statistical learning. The book I chose is <An Introduction to Statistical Learning: with Applications in R>. I am planning to finish the book in the first four weeks and get myself speed up with it.  This is the first week's note. I just traveled to Toronto and I was busy with moving stuffs to my places, so the first week I just read two chapters.

## Introduction to Statistical learning:

### 1 Introduction

Wage data:

![](https://github.com/DD-Daniel/STA496/blob/main/images/image-20210916142009854.png)

Stock market data: 

![](https://github.com/DD-Daniel/STA496/blob/main/images/image-20210916142037824.png)



### 2.1 What is Statistical learning?

**Statistical learning refers to a vast set of tools for understanding data. These**
**tools can be classified as supervised or unsupervised. Broadly speaking,**
**supervised statistical learning involves building a statistical model for predicting,**
**or estimating, an output based on one or more inputs. Problems of**
**this nature occur in fields as diverse as business, medicine, astrophysics, and**
**public policy. With unsupervised statistical learning, there are inputs but**
**no supervising output; nevertheless we can learn relationships and structure**
**from such data. (This is basically what machine learning does STA314)**

**The hardest part of statistical learning is to choose the best method for a particular dataset.**

**There is no free lunch in statistics: no one method dominates all others over all**
**possible data sets. On a particular data set, one specific method may work**
**best, but some other method may work better on a similar but different**
**data set. Hence it is an important task to decide for any given set of data**
**which method produces the best results.**

### 2.2 Assessing Model Accuracy

Mean Squared Error:

![MSE](https://github.com/DD-Daniel/STA496/blob/main/images/image-20210916005614362.png)      (**training MSE**)

MSE is the most commonly used measure to check the quality of the fit.

We do not really care how well the method works on the training data. Rather, we are interested in the accuracy of the predictions that we obtain when we apply our method to previously unseen test data. Example: (stock price). We used training data to find the model and then we want this model to predict instead of how the model accurately measures the training data.

So basically we need to minimize the test MSE

![Ave](https://github.com/DD-Daniel/STA496/blob/main/images/image-20210916100449478.png)

Average squared prediction error

**Problem**: No guarantee that the method with the lowest training MSE will have the lowest testing MSE.

**Ex:**

![](https://github.com/DD-Daniel/STA496/blob/main/images/image-20210916120843443.png)

** Degrees of freedom** (Ch 7)

Fundamental property of statistical learning: As model flexibility increases, training MSE will decrease, but the test MSE may not.

Overfit: Small training MSE, Large test MSE (random noise)

Note that regardless of whether or not overfitting has occurred, we almost always expect the training MSE to be smaller than the test MSE because most statistical learning methods either directly or indirectly seek to minimize the training MSE. Overfitting refers specifically
to the case in which a less flexible model would have yielded a smaller test MSE.

cross-validation is a method to estimate test MSE using the training data.

the expected test MSE, for a given value x0, can always be decomposed into the sum of three fundamental quantities: the variance of estimated f(x0), the squared bias of estimated f(x0) and the variance of the error terms:  <u>**(???????? I do not quite understand how we get this equation)**</u>

![](https://github.com/DD-Daniel/STA496/blob/main/images/image-20210916132106404.png)

The job is to minimize the variance and bias.

In general, more flexible statistical methods have higher variance. The variance will
increase and the bias will decrease when we add more predictors.

As we increase the flexibility of a class of methods, the bias tends to initially decrease faster than the variance increases. Consequently, the expected test MSE declines. However, at some point increasing flexibility has little impact on the bias but starts to significantly increase the variance. When this happens the test MSE increases. (STA302)

Bias and variance trade off.

**Good example of Bias-Variance Trade-off:**

![](https://github.com/DD-Daniel/STA496/blob/main/images/image-20210916142346888.png)

In real-life it is hard to compute test MSE because we do not have *f*

**Classification Setting: **(STA314 Week1)

K-nearest Neighbors: 

![](https://github.com/DD-Daniel/STA496/blob/main/images/image-20210916143049647.png)

![](https://github.com/DD-Daniel/STA496/blob/main/images/image-20210916143105519.png)



### 2.4 Exercise:

(a).  Better, because n is large, the variance wont increase much as we increase p, but we can decrease bias by increasing p.

(b). worse because we have small n, and if we use large *p*, it will probably increase the variance by a lot. 

(c). flexible(non-linear)

(d). ??? I don't think we can conclude based on the error term.



R questions: R 































## R code: 

dev.off() [This function closes the specified plot (by default the current device) and if it is an imguR device, uploads the plots for web hosting]









