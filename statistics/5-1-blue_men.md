[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

>> REPLACE THIS TEXT WITH YOUR RESPONSE

# Problem

Given a roughly normal distribution of heights provided by the BRFSS (section 5.4 in ThinkStats2) - along with the mean = 178cm and standard deviation = 7.7cm for men, we want to see what percentage of the U.S. male population is between the height ranges of 5'10'' and 6'1'' (which are the height requirements to join Blue Man Group)

# How to solve

1. import scipy.stats to use objects related to analytic distrubtions
2. convert the heights provided in inches to centimeters (to align with the height distribution data from BRFSS)
3. use the scipy.stats.norm.cdf method to evaluate the percentile ranks of the the lower and upper bound heights provided.
  - you will need to include both the mean and standard deviation from the normal distribution of heights into the method
4. Once you capture the percentile ranks of both the lower and upper bound heights, take their difference to capture the percentage of the U.S. population that fall between 5'10'' and 6'1''

# Solution

```python
import scipy.stats

# use scipy.stats.norm.cdf
# alternative solution: thinkstats2.EvalNormalCdf(178,mu=178,sigma=7.7)

# convert provided heights to cm - 1 inch = 2.54 cm
lower_ht = ((5*12) + 10) * 2.54 # 5'10'' to cm
upper_ht = ((6*12) + 1) * 2.54 # 6'1'' to cm

# calculate the percentile ranks of each height
lower_pct = scipy.stats.norm.cdf(lower_ht,loc=178,scale=7.7)
upper_pct = scipy.stats.norm.cdf(upper_ht,loc=178,scale=7.7)

# get the difference in percentile ranks to capture the percentage of population between provided heights
(upper_pct - lower_pct)