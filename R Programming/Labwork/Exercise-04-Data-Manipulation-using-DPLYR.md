Exercise 4. Data Manipulation using DPLYR
=========================================

<br>

<b>Estimated time: </b>  
45 Minutes

<b>What this exercise is about</b>  
Perform the following operations using only the dplyr library. We will
be reviewing the following operations:

-   filter (and slice())
-   arrange()
-   select() (and rename())
-   distinct()
-   mutate() (and transmute())
-   summarise0
-   sample\_n() and sample\_frac()

<b><br> Requirernents:</b> RStudio

``` r
library(dplyr)
```

    ## 
    ## Attaching package: 'dplyr'

    ## The following objects are masked from 'package:stats':
    ## 
    ##     filter, lag

    ## The following objects are masked from 'package:base':
    ## 
    ##     intersect, setdiff, setequal, union

<br> <b>  
Solve the following problerns using R </b>

Q1. Return rows of cars that have an mpg value greater than 20 and 6
cylinders?

``` r
df <- mtcars
filter(mtcars,mpg > 20 & cyl == 6)
```

    ##    mpg cyl disp  hp drat    wt  qsec vs am gear carb
    ## 1 21.0   6  160 110 3.90 2.620 16.46  0  1    4    4
    ## 2 21.0   6  160 110 3.90 2.875 17.02  0  1    4    4
    ## 3 21.4   6  258 110 3.08 3.215 19.44  1  0    3    1

<br> Q2. Reorder the Data Frame by cyl first, then by descending wt?

``` r
data_set <- arrange(.data = df,cyl, desc(wt))
head(x = data_set,n = 10)
```

    ##     mpg cyl  disp  hp drat    wt  qsec vs am gear carb
    ## 1  24.4   4 146.7  62 3.69 3.190 20.00  1  0    4    2
    ## 2  22.8   4 140.8  95 3.92 3.150 22.90  1  0    4    2
    ## 3  21.4   4 121.0 109 4.11 2.780 18.60  1  1    4    2
    ## 4  21.5   4 120.1  97 3.70 2.465 20.01  1  0    3    1
    ## 5  22.8   4 108.0  93 3.85 2.320 18.61  1  1    4    1
    ## 6  32.4   4  78.7  66 4.08 2.200 19.47  1  1    4    1
    ## 7  26.0   4 120.3  91 4.43 2.140 16.70  0  1    5    2
    ## 8  27.3   4  79.0  66 4.08 1.935 18.90  1  1    4    1
    ## 9  33.9   4  71.1  65 4.22 1.835 19.90  1  1    4    1
    ## 10 30.4   4  75.7  52 4.93 1.615 18.52  1  1    4    2

<br> Q3. Select the columns mpg and hp?

``` r
data_set <- select(.data = df, mpg, hp)
head(x = data_set,n = 10)
```

    ##                    mpg  hp
    ## Mazda RX4         21.0 110
    ## Mazda RX4 Wag     21.0 110
    ## Datsun 710        22.8  93
    ## Hornet 4 Drive    21.4 110
    ## Hornet Sportabout 18.7 175
    ## Valiant           18.1 105
    ## Duster 360        14.3 245
    ## Merc 240D         24.4  62
    ## Merc 230          22.8  95
    ## Merc 280          19.2 123

<br> Q4. Select the distinct values ot the gear column?

``` r
distinct(.data = df, gear)
```

    ##   gear
    ## 1    4
    ## 2    3
    ## 3    5

<br> Q5. Create a new column called “Performance” which is calculated by
hp divided by wt?

``` r
Performance <- df$hp/ df$wt
df <- mutate(.data = df,Performance)
```

<br> Q6. What is the average mpg value for all the cars?

``` r
summarise(.data = df,average = mean(mpg), n = n())
```

    ##    average  n
    ## 1 20.09062 32

<br> Q7. Use pipe operators to get the mean hp value for cars With 6
cylirxiers?

``` r
df %>% filter(cyl == 6) %>% summarise(average = mean(hp), n =n())
```

    ##    average n
    ## 1 122.2857 7

<br> Q8.Create two data frames?  
<br>
<table border =2 style="width:20%; text-align:center">
<tr>
<td>
ID
</td>
<td>
Salary
</td>
</tr>
<tr>
<td>
1
</td>
<td>
1000
</td>
</tr>
<tr>
<td>
2
</td>
<td>
2000
</td>
</tr>
<tr>
<td>
3
</td>
<td>
3000
</td>
</tr>
<tr>
<td>
4
</td>
<td>
4000
</td>
</tr>
</table>
<br>
<table border =2 style="width:20%; text-align:center">
<tr>
<td>
ID
</td>
<td>
Bonus
</td>
</tr>
<tr>
<td>
1
</td>
<td>
200
</td>
</tr>
<tr>
<td>
2
</td>
<td>
300
</td>
</tr>
<tr>
<td>
3
</td>
<td>
500
</td>
</tr>
<tr>
<td>
4
</td>
<td>
700
</td>
</tr>
<tr>
<td>
6
</td>
<td>
800
</td>
</tr>
</table>

``` r
sal <- data.frame(ID = 1:5, Salary = c(1000,2000,3000,4000,5000))
bon <- data.frame(ID = c(1,2,3,4,6), Bonus = c(200,300,500,700,800))
```

<br> Q9. Write a code to idetify the ID who do not have salary?

``` r
anti_join(x = bon,y = sal ,by = "ID")
```

    ##   ID Bonus
    ## 1  6   800

<br> Q10. Write a code to idetify the ID who do not have bonus?

``` r
anti_join(x = sal,y = bon ,by = "ID")
```

    ##   ID Salary
    ## 1  5   5000

<br> Q11. Write a code to idetify the ID who have both salary and bonus?

``` r
inner_join(x = sal,y = bon, by = "ID")
```

    ##   ID Salary Bonus
    ## 1  1   1000   200
    ## 2  2   2000   300
    ## 3  3   3000   500
    ## 4  4   4000   700

<br>
