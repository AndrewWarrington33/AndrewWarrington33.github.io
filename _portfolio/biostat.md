---
title: "Biostatistics Final Data Analysis"
excerpt: "Analysis of the Cox Lab Functional Ecology Data <br/><img src='/images/green_anole.png'>"
collection: portfolio
---

## Read in the data:

```{r}
anole <- read.csv("data/cox_functional_ecology_data.csv")
ovx <- subset(anole, Treat == "OVX")
sham <- subset(anole, Treat == "SHAM")
```

## Explore summaries of the two groups:

```{r}
summary(ovx)
summary(sham)
```

## The growth (in mm) five number summary for the OVX group:
- Min: **-1.0**
- 1st Quart: **2.0**
- Median: **2.0**
- 3rd Quart: **3.0**
- Max: **7.0**
- Mean: **2.309**
- SD: **1.274607**


```{r}
sd(ovx$Growth..mm., na.rm = TRUE)

hist(ovx$Growth..mm., main = "Change in Body Length of OVX Lizards", xlab = "Growth (mm)", col = "blue")

boxplot(ovx$Growth..mm., main = "Change in Body Length of OVX Lizards", ylab = "Growth (mm)", col = "green")
```

- The histogram and box plot visualizations indicate a uni-modal, right-skewed distribution. 
- There are at least 3 high outliers and at least 2 low outliers.  
- The center appears to be around 2.0 mm of growth, with a mean value of 2.309 mm, and a median value of 2.0 mm of growth.
- The mean being of higher value than the median is also indicative of a right-skewed distribution.


## Growth (in mm) 5 number summary for the sham group:

- Min: **-1.0**
- 1st Quart: **1.0**
- Median: **1.0**
- 3rd Quart: **2.0**
- Max: **4.0**
- Mean: **1.426**
- SD: **1.042156**


```{r}
sd(sham$Growth..mm., na.rm = TRUE)

hist(sham$Growth..mm., main = "Change in Body Length of SHAM Lizards", xlab = "Growth (mm)", col = "cyan")

boxplot(sham$Growth..mm., main = "Change in Body Length of SHAM Lizards", ylab = "Growth (mm)", col = "red")
```

- The histogram and boxplot visualizations indicate the growth for the sham group follows a bimodal distribution. - - There is at least one high outlier and one low outlier.  
- There are two centers, one around 1.0 mm and a center closer to 2.0 mm.  
- The growth for sham group has a mean growth of 1.426 mm and a median growth of 1.0 mm. 

## Hypothesis Test and Confidence Interval:

**H_0: mu_ovx = mu_sham**

**H_a: mu_ovx > mu_sham**

*Is there sufficient evidence to conclude that the mean growth of the ovx group is significantly higher than the mean sham growth?*

**Choosing a two-sample t test, one-sided, right-tailed:**

- Because we have two independent random samples and Population parameters
m1,s1,m2,s2 are unknown.

- Our H_a is that the mean ovx growth in mm is significantly greater than
the mean sham growth.


## Assumptions:

1. Sample Mean is Approximately Normal.
2. Data Comes from SRS (simple random sample) or random experiment
3. Observations are independent.
4. This data came from a random sample of Anoles.

*Even though the data itself is slightly right skewed (with outliers, both
high and low), we have a large enough sample size to assume that the
sample mean and standard deviation will be approximately normal.
The anole observations are independent.*

## Calculating T test statistic:

*Calling ovx group 1 and sham group 2*

- T_ts (T-test statistic)
- ovx: n = 139, (140 observations - 1 NA)
- sham: n = 121, (122 observations - 1 NA)

```{r}
(2.309 - 1.426)

(1.274607^2) / (139) + (1.042156^2) / (121)

sqrt(0.02066388)

0.883 / 0.1437494
```

**T_ts = 6.142634**  

**Df = 120** (Degrees of freedom)


## P-Value Calculation:
A one-sided, right-tailed t-test

```{r}
pt(6.142634, df = 120, lower.tail = FALSE)
```


**P-value = 5.445521e-09**

**Our cutoff**: significance level of 5% or 0.05 (alpha)

**5.445521e-09 < 0.05**, we *reject* the null hypothesis, which states that the mean growth of ovx and sham group are the same.

## P-value interpretation:

If the true mean growth for the ovx and sham group were equal (H_0 is
true), then there is a 5.445521e-09 chance that we would have obtained the sample means we observed from both groups
based on the data.

There is sufficient evidence to reject the null hypothesis (H_0), which
states that the mean growth for the ovx and sham groups of anoles is the same, and conclude H_a, which states that the mean growth in mm ofr ovx group is greater than the sham group.


```{r}
# Calculate t*
qt(.025, df = 120)

# t* = -1.97993

-1.97993 * 0.1437494 # equals m (margin of error) -> -0.2846137
(2.309 - 1.426) + (-0.2846137) # 0.5983863, lower bound of 95% CI
(2.309 - 1.426) - (-0.2846137) # 1.167614, upper bound of 95% CI
```


We are 95% confident that the difference in true mean growth for the ovx
and shame group is between 0.5983863 and 1.167614 mm.

## Conclusion:

There is sufficient evidence to reject the null hypothesis (H_0), which
states that the mean growth for the ovx and sham groups of anoles is the same, and conclude H_a, which states that the mean growth in mm ofr ovx group is greater than the sham group.

We are 95% confident that the difference in true mean growth for the ovx
and shame group is between 0.5983863 and 1.167614 mm.

These findings are relevant because they suggest that there is a
reproductive cost that is associated with the growth of female anoles.
When reproductive mechanisms are removed in OVX, they experience a
greater growth relative to the sham group that reproduces normally.
The lack of growth that occurs in reproducing anoles could contribute to
their lower annual survival rate.