Exercise 1. Basics of R
=======================

<br>

<b>Estimated time: </b>  
45 Minutes Basics of R

<b>What this exercise is about</b>  
We will test you on a few topics

-   Basic Data Types  
-   Basic Arithmetic  
-   Vector  
-   Vector Operations  
-   Comparison operators  
-   Vector Selection and Indexing

<b> Requirernents: RStudio

Solve the following problerns using R </b>

Q1. What is two to the Of five?

``` r
5^2
```

    ## [1] 25

<br> Q2. Create a vector caned stock.prices with the following data
points: 23,27,23,21.34.

``` r
stoke.prices <-c(23,27,23,21,34)
```

Q3. Find the rnean Of stock.prices

``` r
mean(stoke.prices)
```

    ## [1] 25.6

<br> Q3. Find the Standard deviation for the stockprices

``` r
sd(stoke.prices)
```

    ## [1] 5.176872

<br> Q4. Find the Scum for the stock.prices

``` r
sd(stoke.prices)
```

    ## [1] 5.176872

<br> Q5. Assign names to the price data points relating to the day Of
the week, starting With Mon, Tue, Wed, etc.

``` r
names(stoke.prices) <- c("Mon","Tue","Wed","Thurs","Fri")
```

Q6. What was the average (mean) stock price for the week? (You may need
to reference a built-in function)

``` r
mean(stoke.prices)
```

    ## [1] 25.6

Q7. Create a vector called over.23 consisting of logicals that
correspond to the days where the sttxk price was more than $23

``` r
over.23 <- stoke.prices >23
```

Q8. Use the over23 vector to finer out the stock.prices vector and only
return the day and prices where the price was over $23.

``` r
stoke.prices[over.23]
```

    ## Tue Fri 
    ##  27  34

Q9. Use a built-in function to find the day the price was the highest?

``` r
max(stoke.prices)
```

    ## [1] 34

Q10. Create a variable named var and store the value “Welcome” on it?

``` r
var <- "Welcome"
```

Q11. Check the datatype of var?

``` r
class(var)
```

    ## [1] "character"

Q12. What is console Window?  
The console window (in RStudio, the bottom left panel) is the place
where R is waiting for you to tell it what to do, and where it will show
the results of a command. You can type commands directly into the
console, but they will be forgotten when you close the session.

Q13. HOW many packages are there in R?  
There are now more than 10,000 R packages available for download.

Q14. What is the full form Of CRAN?  
Comprehensive R Archive Network

Q15. What is the difference between data types and data structures in
R?  
R has 6 basic data types. (In addition to the five listed below, there
is also raw which will not be discussed in this workshop.)

-   character
-   numeric (real or decimal)
-   integer
-   logical
-   complex

Elements of these data types may be combined to form data structures,
such as atomic vectors. When we call a vector atomic, we mean that the
vector only holds data of a single data type. Below are examples of
atomic character vectors, numeric vectors, integer vectors, etc.

-   character: “a”, “swc”
-   numeric: 2, 15.5
-   integer: 2L (the L tells R to store this as an integer)
-   logical: TRUE, FALSE
-   complex: 1+4i (complex numbers with real and imaginary parts)

Q16. What is the difference R and RStudio?  
It is important to note the differences between R and RStudio. R is a
programming language used for statistical computing while RStudio uses
the R language to develop statistical programs. In R, you can write a
program and run the code independently of any other computer program.
