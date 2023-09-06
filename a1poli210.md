---
title: 'A1: POLI210'
author: "EMT"
date: "2023-09-05"
output: 
  html_document: 
    keep_md: true
---
  
  Exercises 4.4 of "R for Data Science"
  09-06-2023
  
  
  Exercise 1
  Why does the code not work?
  
  my_variable <- 10
  my_varıable
  
    
    ```r
      my_variable <- 10
      my_variable
    ```
    
    ```
    ## [1] 10
    ```

  The code doesn't work because the i in "my_variable" is replaced by a different
  letter (no dot), and so R cannot recognize the variable, the code is referring to.
  
  Exercise 2
  Tweak the following R commands so that they run correctly.
  The correct running code has been inserted. 
  

  install.packages("tidyverse")
    
    ```r
      library(tidyverse)
    ```
    
    ```
    ## ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
    ## ✔ dplyr     1.1.3     ✔ readr     2.1.4
    ## ✔ forcats   1.0.0     ✔ stringr   1.5.0
    ## ✔ ggplot2   3.4.3     ✔ tibble    3.2.1
    ## ✔ lubridate 1.9.2     ✔ tidyr     1.3.0
    ## ✔ purrr     1.0.2     
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()
    ## ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors
    ```
  Tweak: Install the package first
    
    
    ```r
      ggplot(data = mpg) + 
    geom_point(mapping = aes(x = displ, y = hwy))
    ```
    
    ![](a1poli210_files/figure-html/unnamed-chunk-3-1.png)<!-- -->
    
  Tweak: dota changed to data
  
    
    ```r
      filter(mpg, cyl == 8)
    ```
    
    ```
    ## # A tibble: 70 × 11
    ##    manufacturer model      displ  year   cyl trans drv     cty   hwy fl    class
    ##    <chr>        <chr>      <dbl> <int> <int> <chr> <chr> <int> <int> <chr> <chr>
    ##  1 audi         a6 quattro   4.2  2008     8 auto… 4        16    23 p     mids…
    ##  2 chevrolet    c1500 sub…   5.3  2008     8 auto… r        14    20 r     suv  
    ##  3 chevrolet    c1500 sub…   5.3  2008     8 auto… r        11    15 e     suv  
    ##  4 chevrolet    c1500 sub…   5.3  2008     8 auto… r        14    20 r     suv  
    ##  5 chevrolet    c1500 sub…   5.7  1999     8 auto… r        13    17 r     suv  
    ##  6 chevrolet    c1500 sub…   6    2008     8 auto… r        12    17 r     suv  
    ##  7 chevrolet    corvette     5.7  1999     8 manu… r        16    26 p     2sea…
    ##  8 chevrolet    corvette     5.7  1999     8 auto… r        15    23 p     2sea…
    ##  9 chevrolet    corvette     6.2  2008     8 manu… r        16    26 p     2sea…
    ## 10 chevrolet    corvette     6.2  2008     8 auto… r        15    25 p     2sea…
    ## # ℹ 60 more rows
    ```
  
  Tweak: The command filter demands "==" syntax + spell filter correctly
  
    
    ```r
      filter(diamonds, carat > 3)
    ```
    
    ```
    ## # A tibble: 32 × 10
    ##    carat cut     color clarity depth table price     x     y     z
    ##    <dbl> <ord>   <ord> <ord>   <dbl> <dbl> <int> <dbl> <dbl> <dbl>
    ##  1  3.01 Premium I     I1       62.7    58  8040  9.1   8.97  5.67
    ##  2  3.11 Fair    J     I1       65.9    57  9823  9.15  9.02  5.98
    ##  3  3.01 Premium F     I1       62.2    56  9925  9.24  9.13  5.73
    ##  4  3.05 Premium E     I1       60.9    58 10453  9.26  9.25  5.66
    ##  5  3.02 Fair    I     I1       65.2    56 10577  9.11  9.02  5.91
    ##  6  3.01 Fair    H     I1       56.1    62 10761  9.54  9.38  5.31
    ##  7  3.65 Fair    H     I1       67.1    53 11668  9.53  9.48  6.38
    ##  8  3.24 Premium H     I1       62.1    58 12300  9.44  9.4   5.85
    ##  9  3.22 Ideal   I     I1       62.6    55 12545  9.49  9.42  5.92
    ## 10  3.5  Ideal   H     I1       62.8    57 12587  9.65  9.59  6.03
    ## # ℹ 22 more rows
    ```
    
    Tweak: The dataset is called diamonds, not diamond - now specified correctly
  
  Exercise 3
  Alt + Shift + K opens an overview of shortcuts.
  I can get to the same place by going to Tools -> "Keyboard Shortcuts Help"
  
  
