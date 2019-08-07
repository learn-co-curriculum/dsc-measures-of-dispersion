
# Measures of Dispersion

## Introduction

Previously, you learned about three Measures of Central Tendency: the mean, median and mode. These metrics can give you a general understanding of where data values lie within the range of the whole data set but they don't tell you whole story. In fact, they can often be misleading!

To truly understand your data, you also need **Measures of Dispersion**, namely: absolute deviation, standard deviation, and variance. These measures tell you how tightly (or loosely) your data is clustered around its center. Generally, measures of dispersion report on how "noisy" your dataset is. 

In this lesson, you'll learn about the different measures of dispersion and explore how they are related to each other as well as other summary statistics.

## Objectives
You will be able to:
- Describe the significance of calculating measures of dispersion for continuous data
- Understand the formula and intuition behind absolute deviation, variance, and standard deviation
- Understand quantiles, quartiles, percentiles, and interquartile range
- Understand, interpret, and visualize interquartile distances with box plots


## Absolute Deviation

**Absolute Deviation** is the simplest way of calculating the dispersion of a dataset. It is calculated by taking a value from the data set and subtracting the mean of the data set. This helps to identify the "distance" between a given value and the mean. In other words, how much a value *deviates* from the mean.  

> $\left|x_i - \bar{x}\right|$

Here $x_i$ denotes an element from $[x_1, x_2, .., x_n]$ , where n is the total number of data points in the data set. The symbol $\bar{x}$ (pronounced "x-bar") is a commonly used mathematical notation to represent the mean. The vertical bars are used to denote absolute value which means all absolute deviation values are positive. This is important because when measuring deviation, you just want to focus on how big the difference is, not its sign.

If that sounded a little confusing, consider this example: Say the mean test score for a group of 100 students is 58.75 out of 100. If a particular student scored 60 out of 100, the absolute deviation of that score from the mean is:

> $ \left|60 - 58.75\right| = 1.25 $ 

**Average Absolute Deviation** is calculated by taking the mean of all individual absolute deviations in a data set as shown in the formula below:

$$\large \dfrac{1}{n}\sum^n_{i=1}\left|(x_i-\bar x)\right| $$

The advantage here is that the average absolute deviation yields one number to describe dispersion. To illustrate this consider this example: In a group of four people, two people earn 50K USD a year and two earn 60K USD a year. The mean of the data set is 55K USD. The absolute deviations are:

> $ \left|50 - 55\right| = 5 $   
> $ \left|50 - 55\right| = 5 $   
> $ \left|60 - 55\right| = 5 $     
> $ \left|60 - 55\right| = 5 $     

The average absolute deviation is:

> $ \large \frac{5+5+5+5}{4} = 5 $

## Variance

A more complex measure of dispersion is **Variance**. Remember, measures of dispersion emphasize the magnitude of differences from the mean, not their sign. Unlike the absolute deviation, which uses the absolute value of the deviation to take care of negative values, the variance achieves positive values by *squaring* each of the deviations. Similar to what you saw with the average absolute deviation, the next step in calculating variance is to add up the squared deviations (the **sum of squares**), then divide by the total number of values in your data set. 

OK, that was a mouthful but you can break it down mathematically as follows:

$$ \large \sigma^2 = \dfrac{1}{n}\displaystyle\sum^n_{i=1}(x_i-\mu)^2 $$

You'll notice a new term: $\mu$ (mu). $\mu$ is the true mean and $\bar x$ is the arithmetic mean. For this purpose, we can think of them as essentially the same. However, in mathematical terms, $\bar x$ is our sample mean and $\mu$ is the mean of the population that the sample was taken from. The variance formula changes slightly depending on whether you are working with data from a sample or data from the entire population. Don't worry if this is confusing now, the details will be discussed further later. 

Say you want to calculate the variance of our salary data above. The first step is to calculate all of the differences from the mean:

> $ 50 - 55 = -5 $   
> $ 50 - 55 = -5 $   
> $ 60 - 55 = 5 $     
> $ 60 - 55 = 5 $  

*Note: no absolute values, the signs are kept*

Next, square the differences:

> $ (-5)^2 = 25 $   
> $ (-5)^2 = 25 $   
> $ 5^2 = 25 $     
> $ 5^2 = 25 $

Finally, add them up and divide by the total number:

> $ \large \frac{25+25+25+25}{4} = 25 $

As a measure of dispersion, the variance is very useful. If the values in the data set are spread out about their mean, the variance will be a large number. On the other hand, if the values are clustered closely around their mean, the variance will be a much smaller number. 

There are, however, two potential problems with the variance. First, because the deviations of values from the mean are squared, this gives more weight to extreme values. Outliers, which differ substantially more from the mean than the rest of the data in a data set, will impact the variance. Secondly, the variance is not in the same *units* as the individual values in a data set. Variance is measured in the *units squared*. This means we cannot directly relate a variance value to the values in our data set. In this isn't clear, go back to the salary example above. The salaries are measured in USD but the variance is measured in *USD squared* which is not the same thing.

Fortunately, calculating the standard deviation rather than the variance fixes this problem. 

## Standard Deviation

The **Standard Deviation** is another measure of the spread of values within a data set. 
It is simply the square root of the variance. In the above formula, $\sigma^2$ is the variance so $\sigma$ is the standard deviation. 

$$ \large \sigma = \sqrt{\dfrac{1}{n}\displaystyle\sum^n_{i=1}(x_i-\mu)^2} $$

So for the salary example above, you can calculate:

> $ \sigma = \sqrt{\sigma^2} = \sqrt{25} = 5 $

Now, the units are in dollars again!

One common application of calculating the standard deviation is in *statistical inference*. As a data scientist, you will often be presented with data from a sample of a population like discussed above. The task in statistical inference is to estimate the population standard deviation from the sample standard deviation. Don't worry about the details for now. You'll learn about statistical inference soon.

## Quantiles, Percentiles, and Quartiles

**Quantiles** are points in a distribution that relate to the *rank order* of values in that distribution. Rank ordering just means the data are sorted in ascending order. You can find any quantile by sorting the sample. The middle value of the sorted sample (middle quantile, 50th percentile) is known as the **median**. The **limits** are the **minimum** and **maximum** values. Any other locations between these points can be described in terms of **percentiles**.

Percentiles are descriptions of quantiles relative to 100. So the 80th percentile is 80% of the way up an ascending list of sorted values of data. For example, take a look at the image below. You are in the 80th percentile for height so 80% of people in the data set are shorter than you. 

![](images/percent.svg)


## InterQuartile Range - IQR
The **quartiles** of a data set divide the data into **four** equal parts with one-fourth of the data values in each part. Since there are four equal parts, there are 3 quartile positions that divide them. These are denoted by Q1, Q2, and Q3. The second quartile position, Q2, is the median of the data set, which divides the data set in half. Q1 is the border between the first two groups and is known as the "lower quartile". Similarly, Q3 is the border between the last two groups and is known as the "upper quartile". The image below illustrates how this looks:

<img src="images/IQR_new.png" width="600">

The **InterQuartile Range (IQR)** is a measure of where the “middle fifty” is in a data set which is given by $ Q3 - Q1 $. This is useful because it tells you where the bulk of the values lie. It turns out IQR is sometimes preferred over other measures of centrality (i.e. the average or median) when reporting things like retirement age or test scores.  

### Calculating IQR for a Given Data Set

Look at the steps for calculating IQR for an odd number of elements:

```
Data = 1, 5, 2, 7, 6, 12, 15, 18, 9, 27, 19

Step 1: Put the numbers in order.
1, 2, 5, 6, 7, 9, 12, 15, 18, 19, 27

Step 2: Find the median.
1, 2, 5, 6, 7, 9, 12, 15, 18, 19, 27

Step 3: Place parentheses around the numbers above and below the median. 
Not necessary statistically, but it makes Q1 and Q3 easier to spot.
(1, 2, 5, 6, 7), 9, (12, 15, 18, 19, 27)

Step 4: Find Q1 and Q3
Q1 is the median of the lower half of the data and Q3 is the median of the upper half of the data.
(1, 2, 5, 6, 7),  9, ( 12, 15, 18, 19, 27). Q1 = 5 and Q3 = 18

Step 5: Subtract Q1 from Q3 for IQR  
18 – 5 = 13
```

---

For calculating IQR for an even number of elements, the process is slightly modified as below:

```
data = 3, 5, 7, 8, 9, 11, 15, 16, 20, 21

Step 1: Put the numbers in order.
3, 5, 7, 8, 9, 11, 15, 16, 20, 21

Step 2: Put a mark where the median would be.
3, 5, 7, 8, 9, | 11, 15, 16, 20, 21

Step 3: Place parentheses around the numbers above and below the mark you made in Step 2.
(3, 5, 7, 8, 9), | (11, 15, 16, 20, 21)

Step 4: Find Q1 and Q3.
Q1 is the median of the lower half of the data and Q3 is the median of the upper half of the data.
(3, 5, 7, 8, 9), | (11, 15, 16, 20, 21). Q1 = 7 and Q3 = 16

Step 5: Subtract Q1 from Q3 for IQR
16 – 7 = 9
```

The above is graphically depicted below:

![](images/IQR.png)

## Visualizing Dispersion with Box Plots

As a data scientist, you will need to be able to present your analysis visually. Box plots are a commonly used visual representation of centrality and spread of data that is based on quartiles.

A general depiction of a box plot is shown below:
<img src="./images/boxplot.png" width="600">

When creating box plots, follow the procedure described above for determining IQR. First, sort the data. Next, divide the data into four equal-sized groups, that is, 25% of all values are placed in each group. Identify Q1, Q2, and Q3 based on the groups. An important feature of the box plot is the set of lines that radiate from the middle to the "minimum" and "maximum" values. These lines are commonly called "whiskers". You've probably noticed in the image above that the lines do not go to the true minimum and maximum values (confusing right?) but rather $ Q1 - 1.5*IQR $ and $ Q3 + 1.5*IQR $, respectively. Any values that fall outside this range are shown as individual data points. These values are considered outliers. Note: you might have read about some alternative definitions for how to draw the whiskers. Though these alternative definitions may be acceptable in some contexts, the definition presented here is what Python uses so it's best to stick with that.

Matplotlib can be used to generate box plots given a collection of values.


```python
import matplotlib.pyplot as plt
%matplotlib inline

plt.style.use('ggplot') # for viewing a grid on plot
x = [54, 54, 54, 55, 56, 57, 57, 58, 58, 60, 81]
plt.boxplot(x)
plt.title ("Retirement Age Box Plot")
plt.show()
```


![png](index_files/index_4_0.png)


In this box plot, you can see that it is very easy to visualize the central tendency of the data. The median is drawn as a blue line at 57. The IQR identifies the middle 50% of the data which is shown as the box. The whiskers (two horizontal lines) show the minimum (54) and maximum (60) values in our dataset that fall within $Q1-1.5IQR$ and $Q3+1.5IQR$, respectively. The point at 81 falls outside the range of the whiskers so it is shown as a data point and is considered an outlier.

The outlier value squishes the visualization of the box. Sometimes, it is convenient to hide the outliers to get a better view of the box. You can pass the argument `showfliers=False` to hide the outliers:


```python
plt.boxplot(x, showfliers=False)
plt.title ("Retirement Age Box Plot - Without Outliers")
plt.show()
```


![png](index_files/index_6_0.png)


You will revisit these topics continuously throughout the course and will see how these concepts are used toward effective data analysis. 

## Summary

In this lesson, you learned about some commonly used measures of dispersion. These measures identify the spread or deviation present in a data set. You also looked at quantiles, percentiles, quartiles, and IQR as well as how to use those concepts to construct box blots for visualizing the distribution of data in a given data set.
