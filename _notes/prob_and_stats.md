---
layout : page
title: Probability and Statistics

---

**Important Articles**

1. [The 5 Basic Statistics Concepts Data Scientists Need to Know](https://towardsdatascience.com/the-5-basic-statistics-concepts-data-scientists-need-to-know-2c96740377ae)
2. [Probability Cheatsheet]({{site.url}}{{ site.baseurl }}/assets/docs/probability_cheatsheet.pdf)

---
**Probability Topics**


-----
**Statistics Topics**

1. Population versus sample
- sample is a representative of the population
- in population we measure a parameter, in sample we measure statistic
- always two version of maths formulas - one for population and one for sample

2. Descriptive statistics
- types of variables - categorical (labels, names) and quantitative (numeric values)
- Descriptive statistics is summarising data for categorical variable
- common techniques - frequency distribution, relative frequency
- Quantitative data is summarised by binning and making histogram
- cross-tabulation is table summary of 2 variables

3. Measures of variability
- variance and standard deviation
- measures the distance from mean, ie, the spread
- mean, std and variance are three important measure to compare two populations or to compare a population against a theoretical value
- coefficient of variation = std divided by mean
		- useful for comparing populations having different mean and standard deviations
		- unit independent, so we can compare populations having different measurement units		
- z-score - measures distance of a given data point from mean
		- measured in terms of std
		- standardised measure so same for all units
		- formula = (x-mean)/std
	
4. Why do we visualize data?
- to check if it is normal distributed or not
- many statistical techniques assume normal distribution
- patterns to observe 
		- skewness (lopsided)
		- kurtosis (very fat tails)
		- bi-modal
		- other type of distribution : exponential, weibull, lognormal	
		
5. Bivariate relationship
- Covariance
		- measures how two variables co-vary
		- measures LINEAR relationship between two variables
		- does not tell anything about the strength of relationship, only about the direction	
- Correlation
		- standardized measure of covariance in range [-1,1]
		- tells both direction and strength of covariance
		- correlation does not imply causation
		- famous measure: pearson correlation coefficient		
		
6. Normal Distribution
- most general form of distribution
- symmetrical
- mean = median = mode
- standard normal distribution, aka z-distribution : mean = 0, std = 1
- two version depending on the sample size and whether std is known or not 
		- z distribution : if std is known and sample size >= 30
		- t distribution : if std is unknown and sample size < 30
- t-distribution is calculated on small sample size so it is less representative of the entire population, thus it has fatter tails implying more uncertainty
- risk can be estimated from shape of normal distribution, fatter tails -> higher risk

7. Inferential statistics
- descriptive statistics is all about describing the entire population using a sample of data
- inferential statistics is about estimating the entire population using a sample of data
- the error between the true population and the estimated population is called 'margin of error', measured as confidence interval
- point estimators: we estimate population parameters like mean, std, proportion, variance using samples
- degrees of freedom (n-1) are defined as the number of "observations" (pieces of information) in the data that are free to vary when estimating statistical parameters ([hat example](https://blog.minitab.com/blog/statistics-and-quality-data-analysis/what-are-degrees-of-freedom-in-statistics))

8. Sampling distribution
- distribution of means of various samples taken from a population
- expected value of sampling distribution = expected value of the population
- 
		