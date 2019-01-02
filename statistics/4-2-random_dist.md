[Think Stats Chapter 4 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2005.html#toc41) (a random distribution)
my_nums = np.random.random(1000)
random_pmf = thinkstats2.Pmf(my_nums, label='random numbers')
thinkplot.Pmf(random_pmf, linewidth=0.1)
thinkplot.Config(xlabel='Random variate', ylabel='PMF')

r_cdf = thinkstats2.Cdf(my_nums, label='random_numbers')

thinkplot.PrePlot(1)
thinkplot.Cdfs([r_cdf])
thinkplot.Config(xlabel='Random Variable', ylabel='CDF')
