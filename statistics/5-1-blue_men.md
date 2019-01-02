[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

>> REPLACE THIS TEXT WITH YOUR RESPONSE
import scipy.stats
mu = 178
sigma = 7.7
dist = scipy.stats.norm(loc=mu, scale=sigma)

dist.mean(), dist.std()
(178.0, 7.7000000000000002)

How many people are between 5'10" and 6'1"?

# Calculated Z score first than used cdf function
z1 = (mu - 177.8) / (sigma) # 5'10 in cm
#z2 = (185.42 - mu) / (sigma) # 6'1 in cm
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

Percent of population between 5'10- 6'1:
32.2024893361
