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



I have also learned how to use github to upload markdown file for notes.

![](https://github.com/DD-Daniel/STA496/blob/main/images/image-20210916194858787.png)



R questions: R Studio



### Paper I have read: 

Mosheva, M, Hertz-Palmor, N, Dorman Ilan, S, et al. **Anxiety, pandemic-related stress and resilience among physicians during the COVID-19 pandemic. Depression and Anxiety.** 2020; 37: 965– 971. https://doi.org/10.1002/da.23085

This paper analyzes factors associated with anxiety related to the COVID-19 outbreak among physicians.

They used a cross-sectional survey of a nonprobability sample of physician in Israel. The analytic sample for the current study included respondents who consented to participate in the survey between March 19 to March 22, 2020. 

**Method**: They used descriptive statistics to present the sociodemographic characteristics, anxiety, resilience, and PRSF. They conducted multivariable linear regression with the PROMIS Anxiety score as a dependent variable to evaluate the crude association between anxiety, PRSF, and resilience and assessed its robustness when adjusted for age and sex. 

Results can be found in the paper's table.

In the paper, they found that since the pandemic outbreak, healthcare workers are under a lot of pressure, their mental health faces challenges. Physicians reporting high levels of anxiety are in line with a recently published report on mental health outcomes among healthcare workers exposed to the COVID-19 pandemic in China. 



Another paper I have read is about **Vaccinations or Non-Pharmaceutical Interventions:**
**Safe Reopening of Schools in England.**

In that paper, they used scenario-based approach to modelling potential interventions to assess relative changes rather than real-world forecasts. They assess the effects of vaccinating those aged 16-17, those aged 12-17, and not vaccinating children at all relative to only vaccinating the adult population. Vaccinating children in the 12-15 age group would have had a significant impact on the course of the epidemic, saving thousands of lives overall in these simulations. In the absence of such a vaccination campaign the simulations show there could still be a significant positive impact on the epidemic (fewer cases, fewer deaths) by continuing NPI strategies in schools . The analysis from the paper suggests that the best approach are likely derived from a combination of vaccinations and NPIs.

However, I think even there is no pandemic going on, the school should still implement NPIs. I think it can still help to improve the overall wellness of the students together with vacciantions. 

NPIs : non-pharmaceutical interventions





















## R code: 

dev.off() [This function closes the specified plot (by default the current device) and if it is an imguR device, uploads the plots for web hosting]









