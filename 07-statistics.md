# Statistics

# Table of Contents

[1. Introduction](#section-a)  
[2. Why We Are Using Think Stats](#section-b)  
[3. Instructions for Cloning the Repo](#section-c)  
[4. Required Exercises](#section-d)  
[5. Optional Exercises](#section-e)  
[6. Recommended Reading](#section-f)  
[7. Resources](#section-g)

## <a name="section-a"></a>1.  Introduction

[<img src="img/think_stats.jpg" title="Think Stats"/>](http://greenteapress.com/thinkstats2/)

Use Allen Downey's [Think Stats (second edition)](http://greenteapress.com/thinkstats2/) book for getting up to speed with core ideas in statistics and how to approach them programmatically. This book is available online, or you can buy a paper copy if you would like.

Use this book as a reference when answering the 6 required statistics questions below.  The Think Stats book is approximately 200 pages in length.  **It is recommended that you read the entire book, particularly if you are less familiar with introductory statistical concepts.**

Complete the following exercises along with the questions in this file. Some can be solved using code provided with the book. The preface of Think Stats [explains](http://greenteapress.com/thinkstats2/html/thinkstats2001.html#toc2) how to use the code.  

Communicate the problem, how you solved it, and the solution, within each of the following [markdown](https://guides.github.com/features/mastering-markdown/) files. (You can include code blocks and images within markdown.)

## <a name="section-b"></a>2.  Why We Are Using Think Stats 

The stats exercises have been chosen to introduce/solidify some relevant statistical concepts related to data science.  The solutions for these exercises are available in the [ThinkStats repository on GitHub](https://github.com/AllenDowney/ThinkStats2).  You should focus on understanding the statistical concepts, python programming and interpreting the results.  If you are stuck, review the solutions and recode the python in a way that is more understandable to you. 

For example, in the first exercise, the author has already written a function to compute Cohen's D.  **You could import it, or you could write your own code to practice python and develop a deeper understanding of the concept.** 

Think Stats uses a higher degree of python complexity from the python tutorials and introductions to python concepts, and that is intentional to prepare you for the bootcamp.  

**One of the skills to learn here is to understand other people’s code.  And this author is quite experienced, so it’s good to learn how functions and imports work.**

---

## <a name="section-c"></a>3.  Instructions for Cloning the Repo 
Using the [code referenced in the book](https://github.com/AllenDowney/ThinkStats2), follow the step-by-step instructions below.  

**Step 1. Create a directory on your computer where you will do the prework.  Below is an example:**

```
(Mac):      /Users/yourname/ds/metis/metisgh/prework  
(Windows):  C:/ds/metis/metisgh/prework
```

**Step 2. cd into the prework directory.  Use GitHub to pull this repo to your computer.**

```
$ git clone https://github.com/AllenDowney/ThinkStats2.git
```

**Step 3.  Put your ipython notebook or python code files in this directory (that way, it can pull the needed dependencies):**

```
(Mac):     /Users/yourname/ds/metis/metisgh/prework/ThinkStats2/code  
(Windows):  C:/ds/metis/metisgh/prework/ThinkStats2/code
```

---


## <a name="section-d"></a>4.  Required Exercises

*Include your Python code, results and explanation (where applicable).*

### Q1. [Think Stats Chapter 2 Exercise 4](statistics/2-4-cohens_d.md) (effect size of Cohen's d)  
Cohen's D is an example of effect size.  Other examples of effect size are:  correlation between two variables, mean difference, regression coefficients and standardized test statistics such as: t, Z, F, etc. In this example, you will compute Cohen's D to quantify (or measure) the difference between two groups of data.   

You will see effect size again and again in results of algorithms that are run in data science.  For instance, in the bootcamp, when you run a regression analysis, you will recognize the t-statistic as an example of effect size.

CohenEffectSize(firsts.totalwgt_lb,others.totalwgt_lb)
-0.088672927072602006

CohenEffectSize(firsts.prglngth,others.prglngth)
0.028879044654449883


### Q2. [Think Stats Chapter 3 Exercise 1](statistics/3-1-actual_biased.md) (actual vs. biased)
This problem presents a robust example of actual vs biased data.  As a data scientist, it will be important to examine not only the data that is available, but also the data that may be missing but highly relevant.  You will see how the absence of this relevant data will bias a dataset, its distribution, and ultimately, its statistical interpretation.

actual_pmf = thinkstats2.Pmf(resp.numkdhh, label='actual') actual_pmf Pmf({0: 0.46617820227659301, 1: 0.21405207379301322, 2: 0.19625801386889966, 3: 0.087138558157791451, 4: 0.025644380478869556, 5: 0.010728771424833181})

biased_pmf = BiasPmf(actual_pmf, label='observed') biased_pmf thinkplot.PrePlot(2) thinkplot.Pmfs([actual_pmf, biased_pmf]) thinkplot.Config(xlabel='Number of kids per household', ylabel='PMF')

print('Actual mean', actual_pmf.Mean()) print('Observed-biased mean', biased_pmf.Mean()) Actual mean 1.02420515504 Observed-biased mean 2.40367910066

### Q3. [Think Stats Chapter 4 Exercise 2](statistics/4-2-random_dist.md) (random distribution)  
This questions asks you to examine the function that produces random numbers.  Is it really random?  A good way to test that is to examine the pmf and cdf of the list of random numbers and visualize the distribution.  If you're not sure what pmf is, read more about it in Chapter 3.  

my_nums = np.random.random(1000)
random_pmf = thinkstats2.Pmf(my_nums, label='random numbers')
thinkplot.Pmf(random_pmf, linewidth=0.1)
thinkplot.Config(xlabel='Random variate', ylabel='PMF')

r_cdf = thinkstats2.Cdf(my_nums, label='random_numbers')

**The plot of a CDF for the random numbers generated is that of a straight line
which is consistent for a uniform distribution. So, Yes, the random numbers
generated by numpy.random.random appears to have a uniform distribution.**

**In contrast,the plot of a CDF for a Normal distribution is sigmoidal.**

thinkplot.PrePlot(1)
thinkplot.Cdfs([r_cdf])
thinkplot.Config(xlabel='Random Variable', ylabel='CDF')

### Q4. [Think Stats Chapter 5 Exercise 1](statistics/5-1-blue_men.md) (normal distribution of blue men)
This is a classic example of hypothesis testing using the normal distribution.  The effect size used here is the Z-statistic. 

import scipy.stats
mu = 178
sigma = 7.7
dist = scipy.stats.norm(loc=mu, scale=sigma)

dist.mean(), dist.std()
(178.0, 7.7000000000000002)

# How many people are between 5'10" and 6'1"?

# Calculated Z score first than used cdf function
z1 = (mu - 177.8) / (sigma) # 5'10 in cm

z2 = (185.42 - mu) / (sigma) # 6'1 in cm

z2 = abs((mu- 185.42)) / (sigma)

#norm.cdf(z1) 
print(scipy.stats.norm.cdf(z1))
print(scipy.stats.norm.cdf(z2))
print()
print(scipy.stats.norm.cdf(z2) - scipy.stats.norm.cdf(z1))
print()
print("Percent of population between 5'10- 6'1:")
print(100*(scipy.stats.norm.cdf(z2) - scipy.stats.norm.cdf(z1)))

Output:

0.510360972135
0.832385865496

0.322024893361

**Percent of population between 5'10- 6'1:**
**32.2024893361**


### Q5. Bayesian (Elvis Presley twin) 

Bayes' Theorem is an important tool in understanding what we really know, given evidence of other information we have, in a quantitative way.  It helps incorporate conditional probabilities into our conclusions.

Elvis Presley had a twin brother who died at birth.  What is the probability that Elvis was an identical twin? Assume we observe the following probabilities in the population: fraternal twin is 1/125 and identical twin is 1/300.  

Hypothesis (H) : Elvis’s sibling is an identical twin

Data (D) : Elivis’s sibling is a boy(brother)

The Prior: the probability of hypothesis before any data, P(H) = 1 / 300

The Posterior:  P(H | D) the probability that H (sibling is an identical twin) provided by the Data (sibling is a brother)

The Likelihood: P(D | H) is the probability of data given hypothesis

P(D): the probability of the data (D), the probability that Elvis’s sibling is a brother for all possible hypothesis: Elivs sibling is identical twin or Elvis sibling is a fraternal twin. Hence,  P(D) = 1/2 * 1/300 + 1 /2 * 1/125


---

### Q6. Bayesian &amp; Frequentist Comparison  
How do frequentist and Bayesian statistics compare?

**Bayes:
Uses probabilities for both hypothesis and data.
Requires knowledge of the prior, the probability of the the hypothesis before any data. 
As a result, Bayes analysis requires one to either know the prior probability or construct one.**

**Frequentist:
Does not require knowledge of probability of a hypothesis. In frequentist
analysis, probability of an event or value is related to the observed frequency
of the event or value.**

---

## <a name="section-e"></a>5.  Optional Exercises

The following exercises are optional, but we highly encourage you to complete them if you have the time.

### Q7. [Think Stats Chapter 7 Exercise 1](statistics/7-1-weight_vs_age.md) (correlation of weight vs. age)
In this exercise, you will compute the effect size of correlation.  Correlation measures the relationship of two variables, and data science is about exploring relationships in data.    

### Q8. [Think Stats Chapter 8 Exercise 2](statistics/8-2-sampling_dist.md) (sampling distribution)
In the theoretical world, all data related to an experiment or a scientific problem would be available.  In the real world, some subset of that data is available.  This exercise asks you to take samples from an exponential distribution and examine how the standard error and confidence intervals vary with the sample size.

### Q9. [Think Stats Chapter 6 Exercise 1](statistics/6-1-household_income.md) (skewness of household income)
### Q10. [Think Stats Chapter 8 Exercise 3](statistics/8-3-scoring.md) (scoring)
### Q11. [Think Stats Chapter 9 Exercise 2](statistics/9-2-resampling.md) (resampling)

---

## <a name="section-f"></a>6.  Recommended Reading

Read Allen Downey's [Think Bayes](http://greenteapress.com/thinkbayes/) book.  It is available online for free, or you can buy a paper copy if you would like.

[<img src="img/think_bayes.png" title="Think Bayes"/>](http://greenteapress.com/thinkbayes/) 

---

## <a name="section-g"></a>7.  More Resources

Some people enjoy video content such as Khan Academy's [Probability and Statistics](https://www.khanacademy.org/math/probability) or the much longer and more in-depth Harvard [Statistics 110](https://www.youtube.com/playlist?list=PL2SOU6wwxB0uwwH80KTQ6ht66KWxbzTIo). You might also be interested in the book [Statistics Done Wrong](http://www.statisticsdonewrong.com/) or a very short [overview](http://schoolofdata.org/handbook/courses/the-math-you-need-to-start/) from School of Data.
