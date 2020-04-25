Exercise 9 Loops
================

<br>

<b>Estimated time: </b>  
60 Minutes

<b>What this exercise is about</b>  
For those exercises, use the Loops

<b> Requirernents:</b> RStudio

<b>Solve the following problerns using R </b>

Q1. “Fizzbuzz” is a simple programming challenge often used at
interviews to test very bast programming skill. Your goal is the
following: for the numbers 1 to 100, print “fizz” if the number is a
multple of 3, “buzz” if the number is a multiple of 5, “fizzbuzz” if the
number is a multiple of both 3 and 5. and simply print the number
otherwise?

``` r
for (i in 1:15) {
   if(i %% 3 == 0){
      if(i %% 5 == 0){
           print("fizzbuzz")                           
      }else{
        print("fizz")
       }
   }else if(i %% 5 == 0){
            print("buzz")
   }else{
            print(i)
    }
        
}
```

    ## [1] 1
    ## [1] 2
    ## [1] "fizz"
    ## [1] 4
    ## [1] "buzz"
    ## [1] "fizz"
    ## [1] 7
    ## [1] 8
    ## [1] "fizz"
    ## [1] "buzz"
    ## [1] 11
    ## [1] "fizz"
    ## [1] 13
    ## [1] 14
    ## [1] "fizzbuzz"

<br> Q2. The Fibonacci Numbers are an integer sequence. The is usually
recursively defined as follows:  
F0 = F1 = 1 For n \> 1, Fn = Fn—1 + Fn—2 so for example F2 = F1 +F0 = 1
+ 1 = 2  
Write an R script that, for any non-negative integer n produces n’th
Fibonacci Number. Test that your script works by verifying that F25 =
121393?

``` r
n <- 26

if(n==0 || n==1){
        print(1)
}else{
        first <- second <- 1
        i <- 2
        while(i<n){
                third <- first + second
                first <- second
                second <- third
                i <- i + 1
        }
}
print(third)
```

    ## [1] 121393

<br> Q3. Find an primes smaller than 100

``` r
x <- 2:100
n <- sqrt (max (x))
for (i in x [1: n]) { 
        for (j in x[which(x>i)]){
                if(j%%i == 0){
                        x[j - 1] <- 0
                }
        }
}
x[which(x>0)]
```

    ##  [1]  2  3  5  7 11 13 17 19 23 29 31 37 41 43 47 53 59 61 67 71 73 79 83 89 97

<br> Q4. Sorting a list of numbers is a shockingly important problem in
programming  
Consider the vector x \<- c (10,5,3,6,1,4,2,8,7,9)

-   Sort the vector using the sort() function
-   Sort the vector in reverse order using the sort function (Hint: see
    help(sort()))  
-   (Difficult challenge) Sort the vector using the sample function.  
-   (Very difficult challenge) sort the vetor using the Sys.sleep()
    function

``` r
x <- c (10,5,3,6,1,4,2,8,7,9) 
sort(x)
```

    ##  [1]  1  2  3  4  5  6  7  8  9 10

``` r
sort(x ,decreasing = T)
```

    ##  [1] 10  9  8  7  6  5  4  3  2  1

<br> Q5. Imagine a high school with 1000 lockers all in a row, nurnbered
1 to 1000 in order. At the start all of them are closed. 1000 students
are sent, one after the other, to change the state of a set of lockers
(from open to closed or closed to open), The first student changes the
state ot all lockers. The second changes the state of every other one
(2,4,6,8, …) The third changes the state of every third one (3,6,9,12,
…) This process continues until 1000 students have gone. Which ockers
are at the end of this process? For bonus points, explaln why these are
the remaining lockers.

``` r
locker_status <- rep(0, 1000)
for (i in 1:1000) {
        for (j in seq(from = i, to = 1000, by = i)) {
        locker_status[j] <- 1-locker_status[j]                
        }
        
}
which(locker_status >0)
```

    ##  [1]   1   4   9  16  25  36  49  64  81 100 121 144 169 196 225 256 289 324 361
    ## [20] 400 441 484 529 576 625 676 729 784 841 900 961

<br>
