Exercise 12.Visualization
=========================

<br>

<b>Estimated time: </b>  
45 Minutes

<b>What this exercise is about</b>  
For these exercises, use the GGPLOT2 library

<b> Requirernents:</b> RStudio

``` r
library(ggplot2)
```

<b>Solve the following problerns using R </b>

Q1. Run ggplot(data = mpg) what do you see?

``` r
ggplot(data = mpg)
```

It creates an empty plot. The ggplot() function only creates the
background of the plot, there is no layers specified.  
<br> Q2. How many rows are in mtcars? How many columns?.

``` r
dim(mtcars)
```

    ## [1] 32 11

32 rows and 11 columns.  
<br> Q3. What does the drv variable describe? Read the help for ?mpg to
find out

``` r
?mpg
```

It is a categorical variable used to define the type of drive train,
where f = front-wheel drive, r = rear wheel drive, 4 = 4wd <br> Q4. Make
a scatter plot of mpg vs. cyl

``` r
ggplot(data = mpg, mapping = aes(x = hwy, y = cyl)) + geom_point()
```

![](Figs/Exercise%2012%20Visualization%201-1.png) <br> Q5. What happens
if you make a scatter plot of class vs drv? Why is the plot not useful?

``` r
ggplot(data = mpg, mapping = aes(x = class, y = drv)) + geom_point()
```

There are only few data points  
<br> Q6. What’s gone wrong with this code? Why are the points not blue?

``` r
ggplot(data = mpg)+
        geom_point(mapping = aes(x = displ,y = hwy,color = "Blue"))
```

![](Figs/Exercise%2012%20Visualization%202-1.png) Here since the colour
attribute is given inside the aes “blue” passed to the color is
considered as a catergorical varoable with single value “Blue”. To
change the color to blue the color attribute should be give outside the
aes as a parameter of geom\_ponit() <br> Q7. Which variables in mpg are
categorical? Which variables are continuous? (Hint: type ?mpg to read
the documentation for the dataset). How can you see this information
when you run mpg?

``` r
?mpg
```

The following list contains the categorical variables

-   model
-   trans
-   drv
-   fl
-   class

The following list contains the continuous variables

-   displ
-   year
-   cyl
-   city
-   hwy

<br>
