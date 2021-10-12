# Week 4:

## Chapter 11:

Survival analysis and censored survival data. These arise in the analysis of a unique kind of outcome variable: the analysis censored data time until an event occurs. For example, suppose that we have conducted a five-year medical study, in which patients have been treated for cancer. We would like to fit a model to predict patient survival time, using features such as baseline health measurements or type of treatment. At first pass, this may sound like a regression problem of the kind discussed in Chapter 3. But there is an important complication: hopefully some or many of the patients have survived until the end of the study. Such a patient’s survival time is said to be censored: we know that it is at least five years, but we do not know its true value. We do not want to discard this subset of surviving patients, as the fact that they survived at least five years amounts to valuable information. However, it is not clear how to make use of this information using the techniques covered thus far in the textbook.

Survival and Censoring times: There is a true survival time, T, as well as a true censoring time, C. (The survival time is also known as the failure time or the event time) The survival time represents the time at which the event of interest occurs. The censoring time is the time at which censoring occurs. The random variable is represented by Y = min(T,C) indicator function We need to assume that the censoring mechanism is independent: conditional on the features, the event time T is independent of the censoring time C. Interval censoring refers to the setting in which we do not know the exact event time, but we know that it falls in some interval.

![](https://github.com/DD-Daniel/STA496/blob/main/images/image-20211011232000113.png)

**Example:**

![](https://github.com/DD-Daniel/STA496/blob/main/images/image-20211011232039079.png)

## **Note on Paper to Replicate:**

**Summary**:

The study in this paper aimed to investigate age differences in risk-taking concerning the corona virus pandemic, while disentangling the contribution of risk attitude, objective risk and numeracy. In the paper they tested (i) whether older and younger adults differed in taking corona virus-related health risks, (ii) whether there are age differences in corona virus risk, risk attitude and numerical ability and (iii) whether these age differences in corona virus risk, attitude and numerical ability are related to corona virus risk-taking. The study was observational, with measures presented to all participants in random order. A sample of 469 participants reported their corona virus-related risk-taking behavior, objective risk, risk attitude towards health and safety risks, numerical ability and risk perception. The findings show that age was significantly related to corona virus risk-taking, with younger adults taking more risk, and that this was partially mediated by higher numeracy, but not objective risk or risk attitude. Exploratory analyses suggest that risk perception for self and others partially mediated age differences in corona virus risk-taking. The benefits of the study may better the understanding of why age groups differ in their adoption of protective behaviors during a pandemic and contribute to the debate whether age differences in risk-taking occur due to decline in abilities or changes in risk attitude.

**ALL DATA ARE AVAILABLE HERE:**

https://osf.io/u6exb/