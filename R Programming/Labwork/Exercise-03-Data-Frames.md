Exercise 3. Data Frames
=======================

<br>

<b>Estimated time: </b>  
45 Minutes

<b>What this exercise is about</b>  
For this exercise we will test your knowledge of data frames

<b><br> Requirernents:</b> RStudio <br> <b>  
Solve the following problerns using R </b>

Q1. Recreate the following datatrame by creating vectors and using the
data-frame function?  
<br>
<table border =2 style="width:60%; text-align:center">
<th>
<td>
Age
</td>
<td>
Weight
</td>
<td>
Sex
</td>
</th>
<tr>
<td>
Sam
</td>
<td>
22
</td>
<td>
150
</td>
<td>
M
</td>
</tr>
<tr>
<td>
Frank
</td>
<td>
25
</td>
<td>
160
</td>
<td>
K
</td>
</tr>
<tr>
<td>
Amy
</td>
<td>
26
</td>
<td>
120
</td>
<td>
F
</td>
</tr>
</table>

``` r
name <- c("Sam","Frank","Amy")
Age <- c(22,25,26)
Weight <- c(150,160,120)
Sex <- c("M","F","K")
df <-data.frame(row.names = name,Age,Weight,Sex)
df
```

    ##       Age Weight Sex
    ## Sam    22    150   M
    ## Frank  25    160   F
    ## Amy    26    120   K

<br> Q2. Check if mtcars is a dataframe using is.data.frame()?

``` r
is.data.frame(df)
```

    ## [1] TRUE

<br> Q3. Use as.data.frame() to convert a matrix into a dataframe?

``` r
mat <- matrix(data = 1:25,nrow = 5,byrow = T)
as.data.frame(mat)
```

    ##   V1 V2 V3 V4 V5
    ## 1  1  2  3  4  5
    ## 2  6  7  8  9 10
    ## 3 11 12 13 14 15
    ## 4 16 17 18 19 20
    ## 5 21 22 23 24 25

<br> Q4. Set the built-in data frame mtcars as a variable df. We’ll use
this df variable for the rest of the exercises.

``` r
df <- mtcars
```

<br> Q5. Display the first 6 rows Of df?

``` r
head(df)
```

    ##                    mpg cyl disp  hp drat    wt  qsec vs am gear carb
    ## Mazda RX4         21.0   6  160 110 3.90 2.620 16.46  0  1    4    4
    ## Mazda RX4 Wag     21.0   6  160 110 3.90 2.875 17.02  0  1    4    4
    ## Datsun 710        22.8   4  108  93 3.85 2.320 18.61  1  1    4    1
    ## Hornet 4 Drive    21.4   6  258 110 3.08 3.215 19.44  1  0    3    1
    ## Hornet Sportabout 18.7   8  360 175 3.15 3.440 17.02  0  0    3    2
    ## Valiant           18.1   6  225 105 2.76 3.460 20.22  1  0    3    1

<br> Q6. What is the average mpg value for all the cars?

``` r
mean(df$mpg)
```

    ## [1] 20.09062

<br> Q7. Select the rows where all cars have 6 cylinders (cyl column)?

``` r
df[df$cyl==6,]
```

    ##                 mpg cyl  disp  hp drat    wt  qsec vs am gear carb
    ## Mazda RX4      21.0   6 160.0 110 3.90 2.620 16.46  0  1    4    4
    ## Mazda RX4 Wag  21.0   6 160.0 110 3.90 2.875 17.02  0  1    4    4
    ## Hornet 4 Drive 21.4   6 258.0 110 3.08 3.215 19.44  1  0    3    1
    ## Valiant        18.1   6 225.0 105 2.76 3.460 20.22  1  0    3    1
    ## Merc 280       19.2   6 167.6 123 3.92 3.440 18.30  1  0    4    4
    ## Merc 280C      17.8   6 167.6 123 3.92 3.440 18.90  1  0    4    4
    ## Ferrari Dino   19.7   6 145.0 175 3.62 2.770 15.50  0  1    5    6

<br> Q8. Select the columns am,gear, and cart?

``` r
df[,c("am","gear","carb")]
```

    ##                     am gear carb
    ## Mazda RX4            1    4    4
    ## Mazda RX4 Wag        1    4    4
    ## Datsun 710           1    4    1
    ## Hornet 4 Drive       0    3    1
    ## Hornet Sportabout    0    3    2
    ## Valiant              0    3    1
    ## Duster 360           0    3    4
    ## Merc 240D            0    4    2
    ## Merc 230             0    4    2
    ## Merc 280             0    4    4
    ## Merc 280C            0    4    4
    ## Merc 450SE           0    3    3
    ## Merc 450SL           0    3    3
    ## Merc 450SLC          0    3    3
    ## Cadillac Fleetwood   0    3    4
    ## Lincoln Continental  0    3    4
    ## Chrysler Imperial    0    3    4
    ## Fiat 128             1    4    1
    ## Honda Civic          1    4    2
    ## Toyota Corolla       1    4    1
    ## Toyota Corona        0    3    1
    ## Dodge Challenger     0    3    2
    ## AMC Javelin          0    3    2
    ## Camaro Z28           0    3    4
    ## Pontiac Firebird     0    3    2
    ## Fiat X1-9            1    4    1
    ## Porsche 914-2        1    5    2
    ## Lotus Europa         1    5    2
    ## Ford Pantera L       1    5    4
    ## Ferrari Dino         1    5    6
    ## Maserati Bora        1    5    8
    ## Volvo 142E           1    4    2

<br> Q9. Create a new column called performance. which is calculated by
hp/wt?

``` r
df["Performance"] <- df$hp/df$wt
```

<br> Q10. Your performance column will have several decimal place
precision. Figure out how to use round() (check help(round)) to reduce
this accuracy to only 2 decimal places?

``` r
df$Performance <- round(df$Performance,2)
```

<br> Q11. What is the average mpg for cars that have more than 100 hp
AND a value Of more than 2.5?

``` r
mean(subset(x = df, hp>100 & wt >2.5)$mpg)
```

    ## [1] 16.86364

<br> Q12. What is the mpg of the Hornet Sponabout?

``` r
df["Hornet Sportabout",]$mpg
```

    ## [1] 18.7
