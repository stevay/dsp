[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

>> REPLACE THIS TEXT WITH YOUR RESPONSE

# Problem

Using the variable **totalwgt_lb** from ThinkStats' female pregnancy survey results, we want to investigate whether or not first babies are lighter or heavier than others (non-first babies). 

The suggested solution is to compute Cohen's *d* to quantify the differene between the groups.

# How to solve

In order to calculate Cohen's *d*, we first need to calculate a few variables:
* first babies' mean total weight in lbs
* other babies' mean total weight in lbs
* number of first babies
* number of other babies
* variance of first babies' total weight in lbs
* variance of other babies' total weight in lbs

From here, we need to use above variables to calculate a couple items:
* mean difference = first babies' mean total weight - other babies' mean total weight
* pooled variance = ((number of first babies * variance of first babies' total weight) + (number of other babies * variance of other babies' total weight)) / (number of first babies + number of other babies)

From there, we can calculate the Cohen effect size with the above variables, like so:  
**Cohen effect size = mean difference / sqrt(pooled variance)**

Note for the above equation, we can import the module numpy in order to get the square root of the *pooled variance*

# Solution

```python
def CohenEffectSize(group1, group2):
    """Computes Cohen's effect size for two groups.
    
    group1: Series or DataFrame
    group2: Series or DataFrame
    
    returns: float if the arguments are Series;
             Series if the arguments are DataFrames
    """
    diff = group1.mean() - group2.mean()

    var1 = group1.var()
    var2 = group2.var()
    n1, n2 = len(group1), len(group2)

    pooled_var = (n1 * var1 + n2 * var2) / (n1 + n2)
    d = diff / np.sqrt(pooled_var)
    return d
```