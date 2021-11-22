# Week 3

## Chapter 6：

In the chapters that follow, we consider some approaches for extending the linear model framework. In Chapter 7 we generalize (6.1) in order to accommodate non-linear, but still additive, relationships, while in Chapters 8 and 10 we consider even more general non-linear models. However, the linear model has distinct advantages in terms of inference and, on real-world problems, is often surprisingly competitive in relation to non-linear methods. Hence, before moving to the non-linear world, we discuss in this chapter some ways in which the simple linear model can be improved, by replacing plain least squares fitting with some alternative fitting procedures.

### Subset selection:

![](https://github.com/DD-Daniel/STA496/blob/main/images/image-20211011212132050.png)



![](https://github.com/DD-Daniel/STA496/blob/main/images/image-20211011212237366.png)

### Stepwise Selection：

![](https://github.com/DD-Daniel/STA496/blob/main/images/image-20211011212405029.png)



![](https://github.com/DD-Daniel/STA496/blob/main/images/image-20211011212436748.png)

![](https://github.com/DD-Daniel/STA496/blob/main/images/image-20211011212515300.png)

## Chapter 7:  Moving beyond linearity

**Polynomial regression**:

![](https://github.com/DD-Daniel/STA496/blob/main/images/image-20211011212809621.png)

**Step function**:



![](https://github.com/DD-Daniel/STA496/blob/main/images/image-20211011220245677.png)

### Regression Splines

Regression splines are more flexible than polynomials and step functions, and in fact are an extension of the two. They involve dividing the range of X into K distinct regions. Within each region, a polynomial function is fit to the data. However, these polynomials are constrained so that they join smoothly at the region boundaries, or knots. Provided that the interval is divided into enough regions, this can produce an extremely flexible fit.

**Piecewise Polynomials**:

Instead of fitting a high-degree polynomial over the entire range of X, piecewise polynomial regression involves fitting separate low-degree polynomial over different regions of X. For example, a piecewise cubic polynomial works by fitting a cubic regression model of the form 

![](https://github.com/DD-Daniel/STA496/blob/main/images/image-20211011230624554.png)

where the coefficients β0, β1, β2, and β3 differ in different parts of the range of X.  Knots: The points where the coefficients change are called knots.

**The Spline Basis Representation** :

A cubic spline with K knots can be modeled as the following for an appropriate choice of basis functions b1, b2, . . . , bK+3.

![](https://github.com/DD-Daniel/STA496/blob/main/images/image-20211011230853105.png)

truncated power basis: 

![](https://github.com/DD-Daniel/STA496/blob/main/images/image-20211011230811066.png)

where ξ is the knot. In other words, in order to fit a cubic spline to a data set with K knots, we perform least squares regression with an intercept and 3 + K predictors, of the form X, X2, X3, h(X, ξ1), h(X, ξ2),...,h(X, ξK), where ξ1,..., ξK are the knots. This amounts to estimating a total of K + 4 regression coefficients; for this reason, fitting a cubic spline with K knots uses K+4 degrees of freedom.

## Chapter 8:

Decision Tree:

STA 314 overlapped. I skipped this chapter.

Refer to notes in STA 314 courses.



## Chapter 9:

The support vector machine is a generalization of a simple and intuitive classifier called the maximal margin classifier. Though it is elegant and simple, we will see that this classifier unfortunately cannot be applied to most data sets, since it requires that the classes be separable by a linear boundary. Support vector machines are intended for the binary classification setting in which there are two classes.

I could not quite understand the hyperplane part.

Example of hyperplane:

![](https://github.com/DD-Daniel/STA496/blob/main/images/image-20211011231354698.png)

