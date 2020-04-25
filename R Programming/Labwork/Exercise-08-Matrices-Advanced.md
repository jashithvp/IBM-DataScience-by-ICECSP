Exercise 8. Matrices Advanced
=============================

<br>

<b>Estimated time: </b>  
60 Minutes

<b>What this exercise is about</b>  
For these exercises, use the learnings of matrices

<b> Requirernents:</b> RStudio

<b>Solve the following problerns using R </b>

Q1. Suppose

$$
A = \\left(\\begin{array}{cc} 
1 & 1 & 3 \\\\
5 & 2 & 6 \\\\
-2 & -1 & -3
\\end{array}\\right)
$$
a. Check that A 3 = 0 where 0 is a 3 \* 3 matrix with every entry equal
to 0?

``` r
tmp <- matrix(data = c(1,1,3,5,2,6,-2,-1,-3), byrow = T, nrow = 3)
tmp%*%tmp%*%tmp
```

    ##      [,1] [,2] [,3]
    ## [1,]    0    0    0
    ## [2,]    0    0    0
    ## [3,]    0    0    0

<br> b. Replace the third column Of A by the sum Of the second and third
columns

``` r
tmp[,3] <- tmp[,1]+tmp[,2]
tmp
```

    ##      [,1] [,2] [,3]
    ## [1,]    1    1    2
    ## [2,]    5    2    7
    ## [3,]   -2   -1   -3

<br> Q2. Create the following matrix B with 15 rows

$$
B = \\left(\\begin{array}{cc} 
10 & -10 & 10 \\\\
10 & -10 & 10 \\\\
... & ... & ... \\\\
10 & -10 & 10
\\end{array}\\right)
$$
Calculate the 3 \* 3 matrix B TB. (Look at the help for crossprod)?

``` r
B <- matrix(data = rep(c(10,-10,10),15), nrow = 15,byrow = T)
t(B)%*%B
```

    ##       [,1]  [,2]  [,3]
    ## [1,]  1500 -1500  1500
    ## [2,] -1500  1500 -1500
    ## [3,]  1500 -1500  1500

``` r
crossprod(B)
```

    ##       [,1]  [,2]  [,3]
    ## [1,]  1500 -1500  1500
    ## [2,] -1500  1500 -1500
    ## [3,]  1500 -1500  1500

<br> Q3. Create a 6 \* 6 matrix matE with every entry equal to 0. Check
what the functions row and col return when applied to matE. Hence create
the 6 6 matrix:
$$
B = \\left(\\begin{array}{cc} 
0 & 1 & 0 & 0 & 0 & 0 \\\\
1 & 0 & 1 & 0 & 0 & 0 \\\\
0 & 1 & 0 & 1 & 0 & 0 \\\\
0 & 0 & 1 & 0 & 1 & 0 \\\\
0 & 0 & 0 & 1 & 0 & 1 \\\\
0 & 0 & 0 & 0 & 1 & 0 
\\end{array}\\right)
$$

``` r
matE <- matrix(data = 0, nrow = 6,ncol = 6)
matE[abs(col(matE) - row(matE)) == 1] <- 1
matE
```

    ##      [,1] [,2] [,3] [,4] [,5] [,6]
    ## [1,]    0    1    0    0    0    0
    ## [2,]    1    0    1    0    0    0
    ## [3,]    0    1    0    1    0    0
    ## [4,]    0    0    1    0    1    0
    ## [5,]    0    0    0    1    0    1
    ## [6,]    0    0    0    0    1    0

<br> Q4. Look at the help for the Outer. Hence create the following
patterned matrix?
$$
\\left(\\begin{array}{cc} 
0 & 1 & 2 & 3 & 4 \\\\
1 & 2 & 3 & 4 & 5 \\\\
6 & 3 & 4 & 5 & 6 \\\\
3 & 4 & 5 & 6 & 7 \\\\
4 & 5 & 6 & 7 & 8
\\end{array}\\right)
$$

``` r
outer(0:4,0:4,'+')
```

    ##      [,1] [,2] [,3] [,4] [,5]
    ## [1,]    0    1    2    3    4
    ## [2,]    1    2    3    4    5
    ## [3,]    2    3    4    5    6
    ## [4,]    3    4    5    6    7
    ## [5,]    4    5    6    7    8

<br> Q5. Creating the following patterned matrices. in each case, your
solution should make use of the special form of the matrix - this means
that the solution should easily generalise to creating a larger matrix
with the same structure and should not involve typing in all the entries
in the matrix
$$
(a)\\left(\\begin{array}{cc} 
0 & 1 & 2 & 3 & 4 \\\\
1 & 2 & 3 & 4 & 0 \\\\
2 & 3 & 4 & 0 & 1 \\\\
3 & 4 & 0 & 1 & 2 \\\\
4 & 0 & 1 & 2 & 3
\\end{array}\\right)
      \\
(b)\\left(\\begin{array}{cc} 
0 & 1 & 2 & 3 & 4 & 5 & 6 & 7 & 8 & 9 \\\\
1 & 2 & 3 & 4 & 5 & 6 & 7 & 8 & 9 & 0 \\\\
: & : & : & : & : & : & : & : & : & : \\\\
8 & 9 & 0 & 1 & 2 & 3 & 4 & 5 & 6 & 7 \\\\
9 & 0 & 1 & 2 & 3 & 4 & 5 & 6 & 7 & 8 \\\\
\\end{array}\\right)
\\\\
(c)\\left(\\begin{array}{cc} 
0  &  8  &  7  &  6  &  5  &  4  &  3  &  2  &  1 \\\\
1  &  0  &  8  &  7  &  6  &  5  &  4  &  3  &  2 \\\\
2  &  1  &  0  &  8  &  7  &  6  &  5  &  4  &  3 \\\\
3  &  2  &  1  &  0  &  8  &  7  &  6  &  5  &  4 \\\\
4  &  3  &  2  &  1  &  0  &  8  &  7  &  6  &  5 \\\\
5  &  4  &  3  &  2  &  1  &  0  &  8  &  7  &  6 \\\\
6  &  5  &  4  &  3  &  2  &  1  &  0  &  8  &  7 \\\\
7  &  6  &  5  &  4  &  3  &  2  &  1  &  0  &  8 \\\\
8  &  7  &  6  &  5  &  4  &  3  &  2  &  1  &  0 \\\\
\\end{array}\\right)
$$
(a)

``` r
outer(X = 0:4,Y = 0:4,FUN = "+") %% 5
```

    ##      [,1] [,2] [,3] [,4] [,5]
    ## [1,]    0    1    2    3    4
    ## [2,]    1    2    3    4    0
    ## [3,]    2    3    4    0    1
    ## [4,]    3    4    0    1    2
    ## [5,]    4    0    1    2    3

<br> (b)

``` r
outer(X = 0:9,Y = 0:9,FUN = "+") %% 10
```

    ##       [,1] [,2] [,3] [,4] [,5] [,6] [,7] [,8] [,9] [,10]
    ##  [1,]    0    1    2    3    4    5    6    7    8     9
    ##  [2,]    1    2    3    4    5    6    7    8    9     0
    ##  [3,]    2    3    4    5    6    7    8    9    0     1
    ##  [4,]    3    4    5    6    7    8    9    0    1     2
    ##  [5,]    4    5    6    7    8    9    0    1    2     3
    ##  [6,]    5    6    7    8    9    0    1    2    3     4
    ##  [7,]    6    7    8    9    0    1    2    3    4     5
    ##  [8,]    7    8    9    0    1    2    3    4    5     6
    ##  [9,]    8    9    0    1    2    3    4    5    6     7
    ## [10,]    9    0    1    2    3    4    5    6    7     8

<br> (c)

``` r
outer(X = 0:8,Y = 0:8,FUN = "-") %% 9
```

    ##       [,1] [,2] [,3] [,4] [,5] [,6] [,7] [,8] [,9]
    ##  [1,]    0    8    7    6    5    4    3    2    1
    ##  [2,]    1    0    8    7    6    5    4    3    2
    ##  [3,]    2    1    0    8    7    6    5    4    3
    ##  [4,]    3    2    1    0    8    7    6    5    4
    ##  [5,]    4    3    2    1    0    8    7    6    5
    ##  [6,]    5    4    3    2    1    0    8    7    6
    ##  [7,]    6    5    4    3    2    1    0    8    7
    ##  [8,]    7    6    5    4    3    2    1    0    8
    ##  [9,]    8    7    6    5    4    3    2    1    0

<br> Q6. Solve the following system of linear equations in five
unknowns  
x + 2y + 3z + 4p + 5q = 7  
2x + y + 2z + 3p + 4q = -1  
3x + 2y + z + 2p + 3q = -3  
4x + 3y + 2z + p + 2q = 5  
5x + 4y + 3z + 2p + q = 17

``` r
A <- matrix(data = c(1,2,3,4,5,2,1,2,3,4,3,2,1,2,3,4,3,2,1,2,5,4,3,2,1),byrow = TRUE, ncol = 5)
B <- matrix(data = c(7,-1,-3,5,17))
solve(A) %*% B #or
```

    ##      [,1]
    ## [1,]   -2
    ## [2,]    3
    ## [3,]    5
    ## [4,]    2
    ## [5,]   -4

``` r
solve(a = A,b = B)
```

    ##      [,1]
    ## [1,]   -2
    ## [2,]    3
    ## [3,]    5
    ## [4,]    2
    ## [5,]   -4

<br> Checking if the obtained output is correct

``` r
A %*% solve(a = A,b = B)
```

    ##      [,1]
    ## [1,]    7
    ## [2,]   -1
    ## [3,]   -3
    ## [4,]    5
    ## [5,]   17
