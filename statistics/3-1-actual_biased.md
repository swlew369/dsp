[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)

actual_pmf = thinkstats2.Pmf(resp.numkdhh, label='actual')
actual_pmf
Pmf({0: 0.46617820227659301, 1: 0.21405207379301322, 2: 0.19625801386889966, 3: 0.087138558157791451, 4: 0.025644380478869556, 5: 0.010728771424833181})

biased_pmf = BiasPmf(actual_pmf, label='observed')
biased_pmf
thinkplot.PrePlot(2)
thinkplot.Pmfs([actual_pmf, biased_pmf])
thinkplot.Config(xlabel='Number of kids per household', ylabel='PMF')

print('Actual mean', actual_pmf.Mean())
print('Observed-biased mean', biased_pmf.Mean())
Actual mean 1.02420515504
Observed-biased mean 2.40367910066
