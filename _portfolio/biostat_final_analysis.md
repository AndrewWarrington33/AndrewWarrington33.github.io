---
title: "Biostat Final Data Analysis"
author: "Andrew Warrington"
date: "2024-07-06"
output: 
  html_document: 
    keep_md: true
---



## Read in the data:


``` r
anole <- read.csv("data/cox_functional_ecology_data.csv")
ovx <- subset(anole, Treat == "OVX")
sham <- subset(anole, Treat == "SHAM")
```

## Explore summaries of the two groups:


``` r
summary(ovx)
```

```
##   Animal.ID            Treat               Site                SVL1      
##  Length:140         Length:140         Length:140         Min.   :38.00  
##  Class :character   Class :character   Class :character   1st Qu.:42.00  
##  Mode  :character   Mode  :character   Mode  :character   Median :43.00  
##                                                           Mean   :43.09  
##                                                           3rd Qu.:45.00  
##                                                           Max.   :47.00  
##                                                                          
##      Mass1            SVL2           Mass2        Growth..mm.    
##  Min.   :0.900   Min.   :42.00   Min.   :1.100   Min.   :-1.000  
##  1st Qu.:1.300   1st Qu.:44.75   1st Qu.:1.800   1st Qu.: 2.000  
##  Median :1.400   Median :45.00   Median :1.900   Median : 2.000  
##  Mean   :1.503   Mean   :45.42   Mean   :1.954   Mean   : 2.309  
##  3rd Qu.:1.700   3rd Qu.:46.00   3rd Qu.:2.200   3rd Qu.: 3.000  
##  Max.   :2.200   Max.   :49.00   Max.   :2.900   Max.   : 7.000  
##                                                  NA's   :1       
##    Growth..g.      PHA...swelling       Hematocrit        Fat..g.      
##  Min.   :-0.3000   Min.   :-0.05556   Min.   :0.2083   Min.   :0.0054  
##  1st Qu.: 0.2000   1st Qu.: 0.10259   1st Qu.:0.2740   1st Qu.:0.1314  
##  Median : 0.5000   Median : 0.18182   Median :0.3099   Median :0.1635  
##  Mean   : 0.4453   Mean   : 0.20725   Mean   :0.3093   Mean   :0.1619  
##  3rd Qu.: 0.7000   3rd Qu.: 0.30312   3rd Qu.:0.3399   3rd Qu.:0.2049  
##  Max.   : 1.5000   Max.   : 0.56000   Max.   :0.4444   Max.   :0.2859  
##  NA's   :1         NA's   :36         NA's   :78       NA's   :113
```

``` r
summary(sham)
```

```
##   Animal.ID            Treat               Site                SVL1      
##  Length:122         Length:122         Length:122         Min.   :39.00  
##  Class :character   Class :character   Class :character   1st Qu.:42.00  
##  Mode  :character   Mode  :character   Mode  :character   Median :43.00  
##                                                           Mean   :42.96  
##                                                           3rd Qu.:44.00  
##                                                           Max.   :48.00  
##                                                                          
##      Mass1            SVL2           Mass2        Growth..mm.    
##  Min.   :0.800   Min.   :41.00   Min.   :1.100   Min.   :-1.000  
##  1st Qu.:1.300   1st Qu.:43.00   1st Qu.:1.500   1st Qu.: 1.000  
##  Median :1.450   Median :45.00   Median :1.600   Median : 1.000  
##  Mean   :1.453   Mean   :44.41   Mean   :1.622   Mean   : 1.426  
##  3rd Qu.:1.600   3rd Qu.:45.00   3rd Qu.:1.700   3rd Qu.: 2.000  
##  Max.   :2.000   Max.   :49.00   Max.   :2.000   Max.   : 4.000  
##                  NA's   :1       NA's   :1       NA's   :1       
##    Growth..g.      PHA...swelling       Hematocrit        Fat..g.       
##  Min.   :-0.3000   Min.   :-0.15625   Min.   :0.1739   Min.   :0.00000  
##  1st Qu.: 0.0000   1st Qu.: 0.02741   1st Qu.:0.2197   1st Qu.:0.00085  
##  Median : 0.2000   Median : 0.10172   Median :0.2500   Median :0.00405  
##  Mean   : 0.1661   Mean   : 0.12016   Mean   :0.2492   Mean   :0.01291  
##  3rd Qu.: 0.3000   3rd Qu.: 0.22074   3rd Qu.:0.2727   3rd Qu.:0.00930  
##  Max.   : 0.8000   Max.   : 0.42857   Max.   :0.3600   Max.   :0.15390  
##  NA's   :1         NA's   :26         NA's   :72       NA's   :102
```

## The growth (in mm) five number summary for the OVX group:
- Min: **-1.0**
- 1st Quart: **2.0**
- Median: **2.0**
- 3rd Quart: **3.0**
- Max: **7.0**
- Mean: **2.309**
- SD: **1.274607**


``` r
sd(ovx$Growth..mm., na.rm = TRUE)
```

```
## [1] 1.274607
```

``` r
hist(ovx$Growth..mm., main = "Change in Body Length of OVX Lizards", xlab = "Growth (mm)", col = "blue")
```

![](biostat_final_analysis_files/figure-html/unnamed-chunk-3-1.png)<!-- -->

``` r
boxplot(ovx$Growth..mm., main = "Change in Body Length of OVX Lizards", ylab = "Growth (mm)", col = "green")
```

![](biostat_final_analysis_files/figure-html/unnamed-chunk-3-2.png)<!-- -->

The histogram and box plot visualizations indicate a uni-modal, right-skewed distribution. There are at least 3 high outliers and at least
2 low outliers.  
The center appears to be around 2.0 mm of growth, with a mean value of 2.309 mm, and a median value of 2.0 mm of growth.The mean being of higher value than the median is also indicative of a right-skewed distribution.


## Growth (in mm) 5 number summary for the sham group:

- Min: **-1.0**
- 1st Quart: **1.0**
- Median: **1.0**
- 3rd Quart: **2.0**
- Max: **4.0**
- Mean: **1.426**
- SD: **1.042156**


``` r
sd(sham$Growth..mm., na.rm = TRUE)
```

```
## [1] 1.042156
```

``` r
hist(sham$Growth..mm., main = "Change in Body Length of SHAM Lizards", xlab = "Growth (mm)", col = "cyan")
```

![](biostat_final_analysis_files/figure-html/unnamed-chunk-4-1.png)<!-- -->

``` r
boxplot(sham$Growth..mm., main = "Change in Body Length of SHAM Lizards", ylab = "Growth (mm)", col = "red")
```

![](biostat_final_analysis_files/figure-html/unnamed-chunk-4-2.png)<!-- -->

The histogram and boxplot visualizations indicate the growth for the sham group follows a bimodal distribution. There is at least one high outlier and one low outlier.  
There are two centers, one around 1.0 mm and a center closer to 2.0 mm.  
The growth for sham group has a mean growth of 1.426 mm and a median growth of 1.0 mm. 

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
sample mean and standard deviation will be approximately Normal.
The anole observations are independent.*

## Calculating T test statistic:

*Calling ovx group 1 and sham group 2*

- T_ts (T-test statistic)
- ovx: n = 139, (140 observations - 1 NA)
- sham: n = 121, (122 observations - 1 NA)


``` r
(2.309 - 1.426)
```

```
## [1] 0.883
```

``` r
(1.274607^2) / (139) + (1.042156^2) / (121)
```

```
## [1] 0.02066388
```

``` r
sqrt(0.02066388)
```

```
## [1] 0.1437494
```

``` r
0.883 / 0.1437494
```

```
## [1] 6.142634
```
**T_ts = 6.142634**  

**Df = 120** (Degrees of freedom)

## P-Value Calculation:


``` r
pt(6.142634, df = 120, lower.tail = FALSE)
```

```
## [1] 5.445521e-09
```

A one-sided, right-tailed t-test

**P-value = 5.445521e-09**

**Our cutoff**: significance level of 5% or 0.05 (alpha)

**5.445521e-09 < 0.05**, we *reject* the null hypothesis, which states that the mean growth of ovx and sham group are the same.

## P-value interpretation:

If the true mean growth for the ovx and sham group were equal (H_0 is
true), then there is a 5.445521e-09 chance that we would have obtained the sample means we observed from both groups
based on the data.

There is sufficient evidence to reject the null hypothesis (H_0), which
states that the mean growth for the ovx and sham groups of anoles is the same, and conclude H_a, which states that the mean growth in mm ofr ovx group is greater than the sham group.



``` r
# Calculate t*
qt(.025, df = 120)
```

```
## [1] -1.97993
```

``` r
# t* = -1.97993

-1.97993 * 0.1437494 # equals m (margin of error) -> -0.2846137
```

```
## [1] -0.2846137
```

``` r
(2.309 - 1.426) + (-0.2846137) # 0.5983863, lower bound of 95% CI
```

```
## [1] 0.5983863
```

``` r
(2.309 - 1.426) - (-0.2846137) # 1.167614, upper bound of 95% CI
```

```
## [1] 1.167614
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
