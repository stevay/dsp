[Think Stats Chapter 4 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2005.html#toc41) (a random distribution)

>> REPLACE THIS TEXT WITH YOUR RESPONSE

# Problem

We want to generate 1000 random numbers between 0 and 1, with *numpy.random.random*, and plot PMF and CDF to confirm whether or not the numbers generated are uniform or not (every value in the range has the same probability).

# How to solve

1. Need to generate 1000 random numbers and assign to a variable (e.g. sample)
2. create the PMF distribution with **thinkstats2.Pmf()** then use **thinkplot.Pmf()** to plot the PMF
3. create the CDF distribution with **thinkstats2.Cdf()** then use **thinkplot.Cdf()** to plot the CDF
4. look at graphs and confirm if the distribution is uniform (straight line)


# Solution

```python
# generate 1000 numbers from random.random
sample = np.random.random(1000)

# plot PMF
sample_pmf = thinkstats2.Pmf(sample,label='random number between 0 and 1')
thinkplot.Pmf(sample_pmf)
thinkplot.Config(xlabel='number between 0 and 1',ylabel='PMF')

# plot CDF
sample_cdf = thinkstats2.Cdf(sample, label='random number between 0 and 1')
thinkplot.Cdf(sample_cdf)
thinkplot.Config(xlabel='Number between 0 and 1', ylabel='CDF')

print('CDF is approx. a straight line, meaning the distribution is uniform')
```