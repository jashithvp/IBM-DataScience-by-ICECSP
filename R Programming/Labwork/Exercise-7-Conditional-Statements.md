Exercise 7. Conditional Statements
==================================

<br>

<b>Estimated time: </b>  
30 Minutes

<b>What this exercise is about</b>  
For these exercises, use what you have learned about if,else if, and
else statements to answer the questions

<b> Requirernents:</b> RStudio

<b>Solve the following problerns using R </b>

Q1. Write a script that will print “Even Number” if the variable x is an
even number, otherwise print “Not Even”?

``` r
x <- 3
if(x %% 2 == 0){
        print("the number is even")
}else{
        print("the number is odd")
}
```

    ## [1] "the number is odd"

<br> Q2. Write a script that will print ‘Is a Matrix’ the variable x is
a matrix, othemise print “Not a Matrix”. Hint: You may want to check out
help(is.matrix)?

``` r
mat <- matrix(data = 1:25,nrow = 5)
if(is.matrix(mat)){
        print("It is a matrix")
}else{
        print("Not a matrix")
}
```

    ## [1] "It is a matrix"

<br> Q3. Create a script that given a numeric vector x with a length 3,
will print out the elements in order trom high to low. You must use
if,else if, and else statements for your logic. (This code will be
relatively long)

``` r
vec <- c(7,5,8)
if (vec[1]>vec[2]) {
        fir <- vec[1]
        sec <- vec[2]
}else{
        fir <- vec[2]
        sec <- vec[1]
}
if(vec[3]>fir & vec[3]>sec){
        thi <- sec
        sec <- fir
        fir <- vec[3]
}else if( fir >vec[3] & sec>vec[3]){
        thi <- vec[3]
}else{
        thi <- sec
        sec<- vec[3]
}
```

<br> Q4. Write a script that uses if,else if, and else statements to
print the max element in a numeric vector with 3 elements?

``` r
vec <- c(790,54,82)
if(vec[1] > vec[2]){
        if(vec[1]>vec[3]){
                print(paste("maximun = ",vec[1]))
        }else{
                print(paste("maximun = ",vec[3]))
        }
}else{
        if(vec[2]>vec[3]){
                print(paste("maximun = ",vec[2]))
        }else{
                print(paste("maximun = ",vec[3]))
        }
}
```

    ## [1] "maximun =  790"

<br>
