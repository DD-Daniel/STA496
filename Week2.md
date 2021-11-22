# Week 2:

##  Chapter 3:

Linear regression, which is familiar with.

When p is large we might have some false discoveries.

For model selection, we cold use AIC, BIC.



![](https://github.com/DD-Daniel/STA496/blob/main/images/image-20210924155926774.png)



Interaction effect to the regression. 

Variance inflation factor (VIF) is a measure of the amount of multicollinearity in a set of multiple regression variables. Mathematically, the VIF for a regression model variable is **equal to the ratio of the overall model variance to the variance of a** model that includes only that single independent variable



## Chapter 4: Classification



If the response variable is qualitative, we can use classification.

KNN-classifier(sta314)

logistic regression, linear discriminant analysis, quadratic dislogistic regression, linear discriminant analysis criminant analysis, naive Bayes, and K-nearest neighbors.

At least two reasons of not using regression model for classification:

1. a regression method cannot accommodate a qualitative response with more than two classes
2. a regression method will not provide meaningful estimates of Pr(Y |X), even with just two classes

Logistic regression:



## Chapter 5: Cross-Validation

Resampling methods are an indispensable tool in modern statistics. They involve repeatedly drawing samples from a training set and refitting a model of interest on each sample in order to obtain additional information about the fitted model. For example, in order to estimate the variability of a linear regression fit, we can repeatedly draw different samples from the training data, fit a linear regression to each new sample, and then examine the extent to which the resulting fits differ. Such an approach may allow us to obtain information that would not be available from fitting the model only once using the original training sample.

cross-validation can be used to estimate the test error associated with a given statistical learning method in order to evaluate its performance, or to select the appropriate level of flexibility.
