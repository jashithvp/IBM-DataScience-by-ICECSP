Exercise 2. Matrices
====================

<br>

<b>Estimated time: </b>  
20 Minutes

<b>What this exercise is about</b>  
Through these exercises we review the matrix data structure and perhaps
introduce you to a few ideas for you to discover on your own.

<b><br> Requirernents:</b> RStudio <br> <b>  
Solve the following problerns using R </b>

Q1. Create 2 vectors A and B, where A is (1,2,3) and B is (4,5,6). With
these vectors, use the cbind() or ’rbind() function to create a 2 by 3
matrix from the vectors. You’ll need to figure Out which of these
binding functions is the correct choice?

``` r
a <- c(1,2,3)
b <- c(4,5,6)
rbind(a,b)
```

    ##   [,1] [,2] [,3]
    ## a    1    2    3
    ## b    4    5    6

<br> Q2. Create a 3 by 3 matrix consisting ot the numbers Create this
matrix using the shortcut 19 and by specifying the nrow argument the
matrix() function call. Assign this matrix to the variable mat?

``` r
mat <- matrix(1:9, nrow = 3, ncol = 3, byrow = T)
```

<br> Q3. Find the mean ot matrix created?

``` r
mean(mat)
```

    ## [1] 5

<br> Q4. Find the standard deviation for the matrix?

``` r
sd(mat)
```

    ## [1] 2.738613

<br> Q5. Find the sum for the matrix?

``` r
sum(mat)
```

    ## [1] 45

<br> Q6. Find the row sum for matrix?

``` r
rowSums(mat)
```

    ## [1]  6 15 24

<br> Q7. Find the coloum sum for matrix?

``` r
colSums(mat)
```

    ## [1] 12 15 18

<br> Q8. Find the row means for matrix?

``` r
rowMeans(mat)
```

    ## [1] 2 5 8

<br> Q9. Confirm that mat is a matrix using is.rnatrix()

``` r
is.matrix(mat)
```

    ## [1] TRUE

<br> Q10. Create a 5 by 5 matrix consisting of the numbers 1-25 and
assign it to the variable mat2, The top row should the numbers 1-5?

``` r
mat2 <- matrix(data = 1:25,nrow = 5,byrow = T)
```

<br> Q11. Give the row names for the matrix as Day1, Day2..

``` r
row.names(mat2) <- c("Day1","Day2","Day3","Day4","Day5")
```

<br> Q12. Using indexing notation, grab a sub-section Of mat2 from the
previous exercise mat looks like this  
\[7,8\]  
\[12,13\]

``` r
mat2[2:3,2:3]
```

    ##      [,1] [,2]
    ## Day2    7    8
    ## Day3   12   13

<br> Q13. Using indexing notation, grab a sub-section Of mat2 from the
previous exercise mat looks like this  
\[19,20\]  
\[24,25\]

``` r
mat2[4:5,4:5]
```

    ##      [,1] [,2]
    ## Day4   19   20
    ## Day5   24   25

<br> Q14. What is the sum of all the elements in mat2?

``` r
sum(mat2)
```

    ## [1] 325

<br> Q15. Find out how to use runif() to create a 4 by 5 matrix
consisting of 20 random numbers (4\*5=20)?

``` r
matrix(data = runif(n = 20,min = 20,max = 100),nrow = 4)
```

    ##          [,1]     [,2]     [,3]     [,4]     [,5]
    ## [1,] 36.06239 74.48421 76.29469 23.66703 27.97938
    ## [2,] 81.41211 98.13396 80.54951 73.47554 43.60337
    ## [3,] 28.96240 32.71499 40.74425 47.46678 89.12522
    ## [4,] 40.40219 95.05841 42.50324 86.74606 96.98206
