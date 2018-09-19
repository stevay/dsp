[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)

>> REPLACE THIS TEXT WITH YOUR RESPONSE

# Problem

The problem presents an example of actual vs. biased data. Purpose is to recognize how the absence of relevant data will bias a dataset, its distribution, and ultimately, its statistical interpretation.  

We want to see what the 'class size paradox' would look like with regards to how many children are in a family.  

Using NSFG respondent variable **NUMKDHH**, we want to calculate the following:
* actual distribution for the number of children under 18 in the household
* biased distrubtion we would see if we surveyed the children and asked them how many children under 18 are in their household  

Plot the actual and biased distributions, and compute their means.

# How to solve

1. pull in the data on NSFG respondents, and assign to a variable (e.g. resp)
2. with the variable **NUMKDHH**, we create the actual distribution (pmf) using the *thinkstats2.Pmf* function
3. define a function (e.g. biasedPmf) that takes in two arguments: actual distribution + label. In the function, create a copy of the actual distribution, go through each value in the new distribution, and use the *.Mult()* function to multiply the probability associated by the value itself (to capture the biased PMF if we were to survey every child)
4. with both the actual and biased distributions, plot both distributions on one graph with the *thinkplot.Pmfs* function
5. calculate the actual and biased distrubtions' means with the *.Mean()* function

# Solution

```python

# first, we pull in the NSFG respondent data and assign to variable 'resp'
resp = nsfg.ReadFemResp()

# Compute actual distribution for the number of children under 18 in the respondents' households
actual_pmf = thinkstats2.Pmf(resp.numkdhh,label='actual')

# Create function 'biasedPmf' that computes the biased distribution we would see if we surveyed the children
def biasedPmf(pmf,label):
    new_pmf = pmf.Copy(label=label)
    
    for val, prob in pmf.Items():
        new_pmf.Mult(val,val)
    
    new_pmf.Normalize()
    return new_pmf

# plot the actual and biased distributions
biased_pmf = biasedPmf(actual_pmf,label='observed')
thinkplot.PrePlot(2)
thinkplot.Pmfs([actual_pmf,biased_pmf])
thinkplot.Config(xlabel='# of children',ylabel='PMF')

# calculate the means of both actual_pmf and biased_pmf
print('actual PMF mean: ',actual_pmf.Mean())
print('biased PMF mean: ',biased_pmf.Mean())
```