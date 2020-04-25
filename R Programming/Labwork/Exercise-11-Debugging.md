Exercise 11. Debugging
======================

<br>

<b>Estimated time: </b>  
30 Minutes

<b>What this exercise is about</b>  
For these exercises, debug the codes

<b> Requirernents:</b> RStudio

<b>Solve the following problerns using R </b>

Find the Bugs:

Q1.

``` r
x <- 0:9
if(x[1] = 1){
    print(x)
}
```

= should be changed to ==, since if evaluates condition not assign
condition  
<br> Q2.

``` r
x <- 0:9
if(x[0] == 1){
        print(x)
}
```

0th index is not defined in R, the index starts from 1  
<br> Q3.

``` r
myfactorial <- function(x)
{
        if (x == 1)
                return(1)
        else
                return(x*myfactorial(x))
}
```

This will become a infinite recurssion, to find the factorial use
return(x\*myfactorial(x - 1))  
<br> Q4.

``` r
f <- function(x)
{
        scl <- sum(as.numeric(x$a))
        ans <- scl * (as.numeric(x$a) + x$b)
        ans <- crossprod(ans)
        
        return(ans)
}

x <- list(a = factor(-2,2), b = matrix(1:30,nrow =10))
f(x)
```

In factors leveles internally stored as number, by default the levels
are represented by 1,2,3 etc when the factors are coverted to numeric
they are converted to the internal reprentation. if you want to convert
you can use as.numeric(as.character(x))  
<br> Q5.

``` r
f <- function(n)
{
        if(n == 1)
                return(1)
        else{
                if( n %% 2 == 0)
                        return(n/2)
                else
                        return(3*x)
        }
}
x <- 1
f(x)
n <- 3
f(n)
```

Here x is not defined in the function, so it checks the environment the
function is defined, here it is the global environment.  
<br> Q6.

``` r
f <- function(n, p = NULL)
{
        if(n - p)
                1
        else
                0
}
f(1)
```

n-p is a length 0 numeric vector  
<br> Q7. )

``` r
f <- function(n, p = -1)
{
        if(sqrt(p) == 1)
                1
        else
                0
}
f(1)
```

sqrt(-1) is NaN ie. Not a Number, when it is compared to 1 the the
output is NA, which throws an error.  
<br> Q8.

``` r
x <- factor(c(1,3,5))
as.numeric(x)
```

    ## [1] 1 2 3

In factors leveles internally stored as number, by default the levels
are represented by 1,2,3 etc when the factors are coverted to numeric
they are converted to the internal reprentation. if you want to convert
you can use as.numeric(as.character(x))  
<br> Q9.

``` r
f <- function(.)
{
        if(runif(1) > .5)
                x <- 1
        return(x)
                
}
x <- 0
sapply(1:10, f)
```

    ##  [1] 1 0 1 0 1 0 1 1 0 0

``` r
x
```

    ## [1] 0

Here the x used inside and outside of the function are different. this
example shows the concept of lexical scoping. That is a variable is
declared in the function it is been called apon. If a variable is
declared in enivironment and a function separete from the variable. It
can be used in the funtion. These are called global variable.  
<br>
