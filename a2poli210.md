---
title: "A2 homework"
author: "EMT"
date: "2023-09-12"
output: 
  html_document: 
    keep_md: true
---

A2 homework: Criminal Record and the Labor Market



### Part 1

1)  Reading the CSV file:


```
## 
## Attaching package: 'dplyr'
```

```
## The following objects are masked from 'package:stats':
## 
##     filter, lag
```

```
## The following objects are masked from 'package:base':
## 
##     intersect, setdiff, setequal, union
```

```
## Rows: 696 Columns: 4
## ── Column specification ────────────────────────────────────────────────────────
## Delimiter: ","
## chr (1): race
## dbl (3): job_id, criminal, call
## 
## ℹ Use `spec()` to retrieve the full column specification for this data.
## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
```

2.  Heading to view


```r
head(applications)
```

```
## # A tibble: 6 × 4
##   job_id criminal race   call
##    <dbl>    <dbl> <chr> <dbl>
## 1      1        0 white     1
## 2      1        1 white     1
## 3      2        1 white     0
## 4      2        0 white     0
## 5      3        1 white     0
## 6      3        0 white     0
```

3.  Each observation in the dataset represents a job application by one of the people in the experiment. Thus, the variables in the data reflect what type of job, the application is for (job_id), if the applicant is presenting as a criminal or not (criminal), their race (race) and whether they were called back for an interview (call).
4.  The first observation in the dataset represents an application for job nr. 1. The applicant did not present as a criminal, was white and did receive a call back for an interview.
5.  job_id is a numeric non-binary variable, criminal and call are numeric binary variables and race is a character variable.
6.  How many observations are in the dataset?


```r
dim(applications)
```

```
## [1] 696   4
```

There are 696 observations in the dataset.

### Part 2

1.  Observations in the master and new dataframe


```r
applications_white <- applications[applications$race=="white",]
dim(applications)
```

```
## [1] 696   4
```

```r
dim(applications_white)
```

```
## [1] 300   4
```

There are 696 observations in the full dataset and 300 observations in the restricted dataset, meaning that 300 of the applications were sent by white applicants. If no race data is N/A , we know that there must be 396 applications sent by black applicants.

2.  Calculating the average of *criminal* in the dataframe applications_white


```r
mean(applications_white$criminal)
```

```
## [1] 0.5
```

Since *criminal* is a binary variable, the average reflects the share of the white applications where the applicant presented as a criminal. The results from the code above reveals that in 50% of the white applications, the applicant presented as a criminal. This proves that the applicants in the white pair did indeed alternate pretending to be a criminal, such that they served in the criminal record condition for an equal number of applications.

3.  Calculating the average of the variable *call* in the dataframe applications_white


```r
mean(applications_white$call)
```

```
## [1] 0.2533333
```

25,3 % of the applications in the dataset where all applicants were white received a call back for an interview. The interpretation and units correspond to that of the variable criminal, since call is also a numeric binary variable. Thus, there is on average a 25,3% probability of getting a call back.

4.a If we wanted to estimate the average causal effect of having a criminal record on the probability of getting a call back, the treatment variable would be *criminal...*

4.b ... and the outcome variable would be *call*.

5.a The treatment group would be the applicants assigned with a criminal record.

5.b The control group would be the applicants not presenting as criminals. Given that the two groups are assumed identical in all other aspects, and since we have subsetted the data set to only include white applicants, we could use a difference in means estimator to identify the causal effect of having a criminal record on the probability of getting a call back for a job interview for white applicants.

### Part 3

1.  We can use the difference in means estimator to estimate the average causal effect of having a criminal record of getting a call back if you are a white applicant. Meaning we can compute the difference between the average probability of getting a call back when the applicant presents as a criminal and when they do not.

2.   Probability of receiving a call back with and without a criminal record

    
    ```r
    applications_white %>%
        group_by(criminal) %>%
        summarise(avg_call = mean(call))
    ```
    
    ```
    ## # A tibble: 2 × 2
    ##   criminal avg_call
    ##      <dbl>    <dbl>
    ## 1        0    0.34 
    ## 2        1    0.167
    ```

Using group_by we see that there is a 34% probability of getting a call back if you do not have a criminal record (criminal==0), whilst there is only a 16,6% probability of getting a call back if you do have a criminal record (criminal==1).

4.  The estimated average causal effect of having a criminal record on the probability of receiving a call back for a job interview is -17.33 percentage points. Having a criminal record decreases your probability of getting a call back on average by 17.33 percentage points. Since the average probability of getting a call back when you do not have a criminal record was 34%, this reduction actually halves the probability, which seems like a substantial effect.

    Interpreting this as a causal effect rests on the assumption that the treatment and the control group are identical, or at least sufficiently comparable, with respect to all variables that could influence the outcome, i.e. whether or not they get a call back. In this instance, it is given from the research design that the two applicants are as good as identical and thus the treatment - whether they have a criminal record or not - should be the only thing affecting outcome.

    
    ```r
    mean(applications_white$call[applications_white$criminal==1])-mean(applications_white$call[applications_white$criminal==0])
    ```
    
    ```
    ## [1] -0.1733333
    ```
