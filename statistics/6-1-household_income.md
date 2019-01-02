[Think Stats Chapter 6 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2007.html#toc60) (household income)

import hinc
income_df = hinc.ReadData()
log_sample = InterpolateSample(income_df, log_upper=6.0)
log_cdf = thinkstats2.Cdf(log_sample)
thinkplot.Cdf(log_cdf)
thinkplot.Config(xlabel='Household income (log $)',
               ylabel='CDF')
sample = np.power(10, log_sample)

print(min(log_sample))
print()
print(max(log_sample))
print()
print(np.mean(log_sample))
print()
output:
3.0

6.0

4.65758573589

print(min(sample))
print()
print(max(sample))
print()
print(np.mean(sample))
print()
output:
1000.0

1000000.0

74278.7075312

cdf = thinkstats2.Cdf(sample)
thinkplot.Cdf(cdf)
thinkplot.Config(xlabel='Household income ($)',
               ylabel='CDF')


