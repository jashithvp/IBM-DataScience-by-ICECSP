Exercise 6. Money Ball Project- Data Mining
===========================================

<br>

<b>Estimated time: </b>  
200 Minutes

<b>What this exercise is about</b>  
For this optional assignment we will be recreating this plot from The
Economist: Feel In this assignment, you will be tested for your skills
on Data mining. This project is based on a very famous movie Moneyball
and based on the game baseball.

Hope you all enjoy it.  
<b><br> Requirernents:</b> RStudio  
<br> <b> Rules of Baseball  
</b> You don’t need to know much about Baseball to complete this
exercise. If you’re totally unfamiliar with Baseball, check out this
useful <a href="https://www.youtube.com/watch?v=0bKkGeROiPA">
Explanatory Video. </a>  
<br> <b> Background  
<br> The 2002 Oakland A’s  
</b> <br>
<p align="justify">
The Oakland Athletics’ 2002 season was the team’s 35th in Oakland,
California. It was also the 102nd season in franchise history. The
Athletics finished first in the American League West with a record of
103-59. The Athletics’ 2002 campaign ranks among the most famous in
franchise history. Following 2001 season, Oakland saw the departure of
three key players (the lost boys). Billy Beane, the team’s general
manager, responded with a series of under-the-radar free-agent signings.
<br>
</p>
<p align="justify">
The new-look Athletics, despite a comparative lack of star power,
surprised the baseball world by besting the 2001 team’s regular-season
record. The team is most famous. however, for winning 20 consecutive
games between August 13 and September 4, 2002.\[1\] The Athletics’
season was the subject of Michael Lewis’ 2003 book Moneyball: The Art of
Winning an Unfair Game (as Lewis was given the opportunity to follow the
team around throughout that season) <br>
</p>

This project is based on the book written by Michael Lewis (later turned
into a movie). <br> <b>  
Solve the following problerns using R </b>

<br><b> Moneyball Book  
</b><br>
<p align="justify">
The central premise of book Moneyball is that the collective wisdom of
baseball insiders (including players, managers, coaches, scouts, and the
front office) over the past century is subjective and often flawed.
Statistics such as stolen bases, runs batted in, and batting average,
typically used to gauge players, are relics of a 19th-century view of
the game and the statistics available at that time. <br>
</p>
<p align="justify">
The book argues that the Oakland A’s’ front office took advantage of
more analytical gauges of player performance to field a team that could
better compete against richer competitors in Major League Baseball
(MLB). <br>
</p>
<p align="justify">
Rigorous statistical analysis had demonstrated that on-base percentage
and slugging percentage are better indicators of offensive success and
the A’s became convinced that these qualities were cheaper to obtain on
the open market than more historically valued qualities such as speed
and contact. These observations often flew in the face of conventional
baseball wisdom and the beliefs of many baseball scouts and
executives.<br>
</p>
<p align="justify">
By re-evaluating the strategies that produce wins on the field, the 2002
Athletics, with approximately US 44 million dollars in salary were
competitive with larger market teams such as the New York Yankees, who
spent over US$125 million in payroll that same season. Because of the
team’s smaller revenues, Oakland is forced to find players undervalued
by the market, and their system tor finding value in undervalued players
has proven itself thus far. This approach brought the A’s to the
playoffs in 2002 and 2003. <br>
</p>
<p align="justify">
In this project, we’ll work with some data and with the goal of trying
to find replacement players for the ones lost at the start of the
off-season - During the 2001-02 offseason, the team lost three key free
agents to larger market teams: 2000 AL MVP Jason Giambi to the New York
Yankees, outfielder Johnny Damon to the Boston Red Sox, and closer Jason
Isringhausen to the St. Louis Cardinals. <br>
</p>
<p>
The main goal of this project is for you to feel comfortable working
with R on real data to try and derive actionable insights! <br>
</p>

------------------------------------------------------------------------

Lets get started <br> Follow the steps outlined in bold below using your
new R skills and help the Oakland A’s recruit under-valued players! <br>

Use R to open the Batting.csv file and assign it to a dataframe called
batting using read.csv

``` r
batting <- read.csv("./Datasets/batting.csv")
```

<br> Use head() to check out the batting

``` r
head(as_tibble(batting))
```

    ## # A tibble: 6 x 22
    ##   playerID yearID stint teamID lgID      G    AB     R     H   X2B   X3B    HR
    ##   <fct>     <int> <int> <fct>  <fct> <int> <int> <int> <int> <int> <int> <int>
    ## 1 abercda~   1871     1 TRO    <NA>      1     4     0     0     0     0     0
    ## 2 addybo01   1871     1 RC1    <NA>     25   118    30    32     6     0     0
    ## 3 allisar~   1871     1 CL1    <NA>     29   137    28    40     4     5     0
    ## 4 allisdo~   1871     1 WS3    <NA>     27   133    28    44    10     2     2
    ## 5 ansonca~   1871     1 RC1    <NA>     25   120    29    39    11     3     0
    ## 6 armstbo~   1871     1 FW1    <NA>     12    49     9    11     2     1     0
    ## # ... with 10 more variables: RBI <int>, SB <int>, CS <int>, BB <int>,
    ## #   SO <int>, IBB <int>, HBP <int>, SH <int>, SF <int>, GIDP <int>

<br> Use str() to check the structure. Pay close attention to how
columns that start with a number get an \*X’ in front of them! You’ll
need to know this to call those columns! Make sure you understand how to
call the columns by using the $ symbol.

``` r
str(batting)
```

    ## 'data.frame':    107429 obs. of  22 variables:
    ##  $ playerID: Factor w/ 19689 levels "aardsda01","aaronha01",..: 21 105 241 245 419 479 804 845 871 894 ...
    ##  $ yearID  : int  1871 1871 1871 1871 1871 1871 1871 1871 1871 1871 ...
    ##  $ stint   : int  1 1 1 1 1 1 1 1 1 1 ...
    ##  $ teamID  : Factor w/ 149 levels "ALT","ANA","ARI",..: 136 111 39 142 111 56 111 24 56 24 ...
    ##  $ lgID    : Factor w/ 6 levels "AA","AL","FL",..: NA NA NA NA NA NA NA NA NA NA ...
    ##  $ G       : int  1 25 29 27 25 12 1 31 1 18 ...
    ##  $ AB      : int  4 118 137 133 120 49 4 157 5 86 ...
    ##  $ R       : int  0 30 28 28 29 9 0 66 1 13 ...
    ##  $ H       : int  0 32 40 44 39 11 1 63 1 13 ...
    ##  $ X2B     : int  0 6 4 10 11 2 0 10 1 2 ...
    ##  $ X3B     : int  0 0 5 2 3 1 0 9 0 1 ...
    ##  $ HR      : int  0 0 0 2 0 0 0 0 0 0 ...
    ##  $ RBI     : int  0 13 19 27 16 5 2 34 1 11 ...
    ##  $ SB      : int  0 8 3 1 6 0 0 11 0 1 ...
    ##  $ CS      : int  0 1 1 1 2 1 0 6 0 0 ...
    ##  $ BB      : int  0 4 2 0 2 0 1 13 0 0 ...
    ##  $ SO      : int  0 0 5 2 1 1 0 1 0 0 ...
    ##  $ IBB     : int  NA NA NA NA NA NA NA NA NA NA ...
    ##  $ HBP     : int  NA NA NA NA NA NA NA NA NA NA ...
    ##  $ SH      : int  NA NA NA NA NA NA NA NA NA NA ...
    ##  $ SF      : int  NA NA NA NA NA NA NA NA NA NA ...
    ##  $ GIDP    : int  0 0 1 0 0 0 0 1 0 0 ...

<br> Call the head() of the first five rows of AB (At Bats) column

``` r
head(batting$ab)
```

    ## NULL

<br> Call the head of the doubles (X2B) column

``` r
head(batting$double)
```

    ## NULL

<br> <b>Feature Engineering</b>  
<br> We need to add three more statistics that were used in Moneyball!
These are: \*
<a href = "https://en.wikipedia.org/wiki/Batting_average" >Batting
Average</a> \* <a>Base Percentage</a> \* <a>Sugqging Percenage</a> <br>
Click on the links provided and search the wikipedia page tor the
formula tor creating the new statistic! For example, tor Batting
Average. you’ll need to scroll down until you see:
*A**V**G* = *H*/*A**B*
Which means that the Batting Average is equal to H (Hits) divided by AS
(At Base). So we’ll do the following to create a new column calledd BA
and add it to our data frame.

``` r
batting$BA <- batting$H/batting$AB
```

<br> Now do the same for some new columns! On Base Percentage (OBP) and
Slugging Percentage(SLG). Hint: For 8LG, you need 18 (Singles), this
isn’t in your data frame. However you can calculate it by subtracting
doubles, triples, and home runs from total hits (H): 18 = H-2B-3B-HR

-   Create an OBP Column

$$\\frac{ H+BB+HBP } {AB+BB+HBP+SF}$$

``` r
batting$OBP <- (batting$H+batting$BB+batting$HBP)/(batting$AB+batting$BB+batting$HBP+batting$SF)
```

-   Create an SLG Column

$$\\frac{ (1\*1B)+(2\*2B)+(3\*3B)+(4\*HR) } {AB}$$

``` r
batting$X1B <- batting$H - batting$X2B - batting$X3B - batting$HR
batting$SLG <- (batting$X1B + 2 * batting$X2B + 3 * batting$X3B + 4 * batting$HR)/(batting$AB)
```

<br> Check the structure of your date frame using str ()

``` r
str(as_tibble( batting))
```

    ## tibble [107,429 x 26] (S3: tbl_df/tbl/data.frame)
    ##  $ playerID: Factor w/ 19689 levels "aardsda01","aaronha01",..: 21 105 241 245 419 479 804 845 871 894 ...
    ##  $ yearID  : int [1:107429] 1871 1871 1871 1871 1871 1871 1871 1871 1871 1871 ...
    ##  $ stint   : int [1:107429] 1 1 1 1 1 1 1 1 1 1 ...
    ##  $ teamID  : Factor w/ 149 levels "ALT","ANA","ARI",..: 136 111 39 142 111 56 111 24 56 24 ...
    ##  $ lgID    : Factor w/ 6 levels "AA","AL","FL",..: NA NA NA NA NA NA NA NA NA NA ...
    ##  $ G       : int [1:107429] 1 25 29 27 25 12 1 31 1 18 ...
    ##  $ AB      : int [1:107429] 4 118 137 133 120 49 4 157 5 86 ...
    ##  $ R       : int [1:107429] 0 30 28 28 29 9 0 66 1 13 ...
    ##  $ H       : int [1:107429] 0 32 40 44 39 11 1 63 1 13 ...
    ##  $ X2B     : int [1:107429] 0 6 4 10 11 2 0 10 1 2 ...
    ##  $ X3B     : int [1:107429] 0 0 5 2 3 1 0 9 0 1 ...
    ##  $ HR      : int [1:107429] 0 0 0 2 0 0 0 0 0 0 ...
    ##  $ RBI     : int [1:107429] 0 13 19 27 16 5 2 34 1 11 ...
    ##  $ SB      : int [1:107429] 0 8 3 1 6 0 0 11 0 1 ...
    ##  $ CS      : int [1:107429] 0 1 1 1 2 1 0 6 0 0 ...
    ##  $ BB      : int [1:107429] 0 4 2 0 2 0 1 13 0 0 ...
    ##  $ SO      : int [1:107429] 0 0 5 2 1 1 0 1 0 0 ...
    ##  $ IBB     : int [1:107429] NA NA NA NA NA NA NA NA NA NA ...
    ##  $ HBP     : int [1:107429] NA NA NA NA NA NA NA NA NA NA ...
    ##  $ SH      : int [1:107429] NA NA NA NA NA NA NA NA NA NA ...
    ##  $ SF      : int [1:107429] NA NA NA NA NA NA NA NA NA NA ...
    ##  $ GIDP    : int [1:107429] 0 0 1 0 0 0 0 1 0 0 ...
    ##  $ BA      : num [1:107429] 0 0.271 0.292 0.331 0.325 ...
    ##  $ OBP     : num [1:107429] NA NA NA NA NA NA NA NA NA NA ...
    ##  $ X1B     : int [1:107429] 0 26 31 30 25 8 1 44 0 10 ...
    ##  $ SLG     : num [1:107429] 0 0.322 0.394 0.481 0.467 ...

<br> <b>Merging Salary Data with Batting Data</b>  
<br> We know we don’t just want the best players, we want the most
undervalued players. meaning we will also Need to know current salary
information! We have salary information in the csv file
‘Salaries.csv’.  
<br> Complete the following steps to merge the salary data with the
player stats! Load the Salaries.cev file into a dataframe called sal
using read.csv  
<br>

``` r
sal <- read.csv("./Datasets/Salaries.csv")
```

<br> Use summary to get a summary of the baiting data frame and notice
the minimum year in the yearID column. Our batting data goes back to
1871! Our salary data starts at 1965, meaning we need to remove the
batting data that occurred before 1988.

``` r
summary(batting)
```

    ##       playerID          yearID         stint           teamID        lgID      
    ##  mcguide01:    31   Min.   :1871   Min.   :1.000   CHN    : 5013   AA  : 1893  
    ##  henderi01:    29   1st Qu.:1936   1st Qu.:1.000   PHI    : 4925   AL  :49458  
    ##  newsobo01:    29   Median :1976   Median :1.000   PIT    : 4871   FL  :  472  
    ##  johnto01 :    28   Mean   :1967   Mean   :1.079   SLN    : 4809   NL  :54385  
    ##  kaatji01 :    28   3rd Qu.:2000   3rd Qu.:1.000   CIN    : 4688   PL  :  149  
    ##  ansonca01:    27   Max.   :2019   Max.   :5.000   CLE    : 4644   UA  :  334  
    ##  (Other)  :107257                                  (Other):78479   NA's:  738  
    ##        G                AB              R                H         
    ##  Min.   :  1.00   Min.   :  0.0   Min.   :  0.00   Min.   :  0.00  
    ##  1st Qu.: 12.00   1st Qu.:  4.0   1st Qu.:  0.00   1st Qu.:  0.00  
    ##  Median : 34.00   Median : 47.0   Median :  4.00   Median :  8.00  
    ##  Mean   : 51.13   Mean   :140.5   Mean   : 18.64   Mean   : 36.71  
    ##  3rd Qu.: 80.00   3rd Qu.:228.0   3rd Qu.: 27.00   3rd Qu.: 57.00  
    ##  Max.   :165.00   Max.   :716.0   Max.   :198.00   Max.   :262.00  
    ##                                                                    
    ##       X2B              X3B               HR              RBI        
    ##  Min.   : 0.000   Min.   : 0.000   Min.   : 0.000   Min.   :  0.00  
    ##  1st Qu.: 0.000   1st Qu.: 0.000   1st Qu.: 0.000   1st Qu.:  0.00  
    ##  Median : 1.000   Median : 0.000   Median : 0.000   Median :  3.00  
    ##  Mean   : 6.254   Mean   : 1.261   Mean   : 2.865   Mean   : 16.93  
    ##  3rd Qu.: 9.000   3rd Qu.: 1.000   3rd Qu.: 2.000   3rd Qu.: 24.00  
    ##  Max.   :67.000   Max.   :36.000   Max.   :73.000   Max.   :191.00  
    ##                                                     NA's   :756     
    ##        SB                CS               BB               SO        
    ##  Min.   :  0.000   Min.   : 0.000   Min.   :  0.00   Min.   :  0.00  
    ##  1st Qu.:  0.000   1st Qu.: 0.000   1st Qu.:  0.00   1st Qu.:  1.00  
    ##  Median :  0.000   Median : 0.000   Median :  2.00   Median :  9.00  
    ##  Mean   :  2.948   Mean   : 1.193   Mean   : 12.95   Mean   : 20.68  
    ##  3rd Qu.:  2.000   3rd Qu.: 1.000   3rd Qu.: 18.00   3rd Qu.: 29.00  
    ##  Max.   :138.000   Max.   :42.000   Max.   :232.00   Max.   :223.00  
    ##  NA's   :2368      NA's   :23541                     NA's   :2100    
    ##       IBB              HBP               SH               SF       
    ##  Min.   :  0.00   Min.   : 0.000   Min.   : 0.000   Min.   : 0.00  
    ##  1st Qu.:  0.00   1st Qu.: 0.000   1st Qu.: 0.000   1st Qu.: 0.00  
    ##  Median :  0.00   Median : 0.000   Median : 0.000   Median : 0.00  
    ##  Mean   :  1.07   Mean   : 1.064   Mean   : 2.225   Mean   : 1.04  
    ##  3rd Qu.:  1.00   3rd Qu.: 1.000   3rd Qu.: 3.000   3rd Qu.: 1.00  
    ##  Max.   :120.00   Max.   :51.000   Max.   :67.000   Max.   :19.00  
    ##  NA's   :36651    NA's   :2817     NA's   :6069     NA's   :36104  
    ##       GIDP              BA             OBP             X1B        
    ##  Min.   : 0.000   Min.   :0.000   Min.   :0.00    Min.   :  0.00  
    ##  1st Qu.: 0.000   1st Qu.:0.145   1st Qu.:0.19    1st Qu.:  0.00  
    ##  Median : 0.000   Median :0.231   Median :0.29    Median :  7.00  
    ##  Mean   : 2.926   Mean   :0.208   Mean   :0.26    Mean   : 26.34  
    ##  3rd Qu.: 4.000   3rd Qu.:0.274   3rd Qu.:0.34    3rd Qu.: 41.00  
    ##  Max.   :36.000   Max.   :1.000   Max.   :1.00    Max.   :225.00  
    ##  NA's   :25441    NA's   :16849   NA's   :52438                   
    ##       SLG       
    ##  Min.   :0.000  
    ##  1st Qu.:0.175  
    ##  Median :0.310  
    ##  Mean   :0.290  
    ##  3rd Qu.:0.399  
    ##  Max.   :4.000  
    ##  NA's   :16849

<br> Use subset() to reassign batting to only contain data from 1985 and
onwards Now use summary again to make sure the subset reassignment
worked, your yearID min should be 1985.

``` r
batting <- subset(x = batting, yearID >=1985)
summary(batting)
```

    ##       playerID         yearID         stint           teamID      lgID      
    ##  moyerja01:   27   Min.   :1985   Min.   :1.000   TEX    : 1641   AA:    0  
    ##  mulhote01:   26   1st Qu.:1995   1st Qu.:1.000   CLE    : 1632   AL:22313  
    ##  weathda01:   26   Median :2004   Median :1.000   SDN    : 1623   FL:    0  
    ##  maddugr01:   25   Mean   :2003   Mean   :1.084   BOS    : 1617   NL:22861  
    ##  sierrru01:   25   3rd Qu.:2012   3rd Qu.:1.000   NYA    : 1610   PL:    0  
    ##  thomeji01:   25   Max.   :2019   Max.   :5.000   SEA    : 1601   UA:    0  
    ##  (Other)  :45020                                  (Other):35450             
    ##        G                AB              R                H         
    ##  Min.   :  1.00   Min.   :  0.0   Min.   :  0.00   Min.   :  0.00  
    ##  1st Qu.: 14.00   1st Qu.:  0.0   1st Qu.:  0.00   1st Qu.:  0.00  
    ##  Median : 33.00   Median : 21.0   Median :  1.00   Median :  3.00  
    ##  Mean   : 50.46   Mean   :122.2   Mean   : 16.33   Mean   : 31.84  
    ##  3rd Qu.: 74.00   3rd Qu.:185.0   3rd Qu.: 22.00   3rd Qu.: 46.00  
    ##  Max.   :163.00   Max.   :716.0   Max.   :152.00   Max.   :262.00  
    ##                                                                    
    ##       X2B              X3B                HR              RBI        
    ##  Min.   : 0.000   Min.   : 0.0000   Min.   : 0.000   Min.   :  0.00  
    ##  1st Qu.: 0.000   1st Qu.: 0.0000   1st Qu.: 0.000   1st Qu.:  0.00  
    ##  Median : 0.000   Median : 0.0000   Median : 0.000   Median :  1.00  
    ##  Mean   : 6.152   Mean   : 0.6831   Mean   : 3.621   Mean   : 15.49  
    ##  3rd Qu.: 8.000   3rd Qu.: 1.0000   3rd Qu.: 3.000   3rd Qu.: 20.00  
    ##  Max.   :59.000   Max.   :23.0000   Max.   :73.000   Max.   :165.00  
    ##                                                                      
    ##        SB               CS                BB               SO        
    ##  Min.   :  0.00   Min.   : 0.0000   Min.   :  0.00   Min.   :  0.00  
    ##  1st Qu.:  0.00   1st Qu.: 0.0000   1st Qu.:  0.00   1st Qu.:  0.00  
    ##  Median :  0.00   Median : 0.0000   Median :  1.00   Median :  6.00  
    ##  Mean   :  2.28   Mean   : 0.9729   Mean   : 11.74   Mean   : 23.98  
    ##  3rd Qu.:  1.00   3rd Qu.: 1.0000   3rd Qu.: 16.00   3rd Qu.: 35.00  
    ##  Max.   :110.00   Max.   :29.0000   Max.   :232.00   Max.   :223.00  
    ##                                                                      
    ##       IBB                HBP               SH               SF    
    ##  Min.   :  0.0000   Min.   : 0.000   Min.   : 0.000   Min.   : 0  
    ##  1st Qu.:  0.0000   1st Qu.: 0.000   1st Qu.: 0.000   1st Qu.: 0  
    ##  Median :  0.0000   Median : 0.000   Median : 0.000   Median : 0  
    ##  Mean   :  0.9331   Mean   : 1.115   Mean   : 1.149   Mean   : 1  
    ##  3rd Qu.:  1.0000   3rd Qu.: 1.000   3rd Qu.: 1.000   3rd Qu.: 1  
    ##  Max.   :120.0000   Max.   :35.000   Max.   :39.000   Max.   :17  
    ##                                                                   
    ##       GIDP              BA             OBP             X1B        
    ##  Min.   : 0.000   Min.   :0.000   Min.   :0.000   Min.   :  0.00  
    ##  1st Qu.: 0.000   1st Qu.:0.129   1st Qu.:0.182   1st Qu.:  0.00  
    ##  Median : 0.000   Median :0.231   Median :0.293   Median :  2.00  
    ##  Mean   : 2.732   Mean   :0.202   Mean   :0.258   Mean   : 21.38  
    ##  3rd Qu.: 4.000   3rd Qu.:0.272   3rd Qu.:0.339   3rd Qu.: 31.00  
    ##  Max.   :35.000   Max.   :1.000   Max.   :1.000   Max.   :225.00  
    ##                   NA's   :12232   NA's   :12127                   
    ##       SLG       
    ##  Min.   :0.000  
    ##  1st Qu.:0.158  
    ##  Median :0.333  
    ##  Mean   :0.301  
    ##  3rd Qu.:0.423  
    ##  Max.   :4.000  
    ##  NA's   :12232

<br> Now it is time to merge the batting data with the salary data!
Since we have players playing multiple years, we’ll have repetitions of
playerID for multiple years. meaning we want to merge on both players
and years. Use the merge() function to merge the batting and sai data
frames by c(‘player!D’,‘yearID’). Call the new data frame combo.

``` r
combo <- merge(x = batting,y = sal,by = c("playerID","yearID"))
head(as_tibble(combo))
```

    ## # A tibble: 6 x 29
    ##   playerID yearID stint teamID.x lgID.x     G    AB     R     H   X2B   X3B
    ##   <fct>     <int> <int> <fct>    <fct>  <int> <int> <int> <int> <int> <int>
    ## 1 aardsda~   2004     1 SFN      NL        11     0     0     0     0     0
    ## 2 aardsda~   2007     1 CHA      AL        25     0     0     0     0     0
    ## 3 aardsda~   2008     1 BOS      AL        47     1     0     0     0     0
    ## 4 aardsda~   2009     1 SEA      AL        73     0     0     0     0     0
    ## 5 aardsda~   2010     1 SEA      AL        53     0     0     0     0     0
    ## 6 aardsda~   2012     1 NYA      AL         1     0     0     0     0     0
    ## # ... with 18 more variables: HR <int>, RBI <int>, SB <int>, CS <int>,
    ## #   BB <int>, SO <int>, IBB <int>, HBP <int>, SH <int>, SF <int>, GIDP <int>,
    ## #   BA <dbl>, OBP <dbl>, X1B <int>, SLG <dbl>, teamID.y <fct>, lgID.y <fct>,
    ## #   salary <int>

<br> Use summary to check the data

``` r
summary(combo)
```

    ##       playerID         yearID         stint        teamID.x     lgID.x    
    ##  moyerja01:   27   Min.   :1985   Min.   :1.0   BOS    : 1057   AA:    0  
    ##  thomeji01:   25   1st Qu.:1994   1st Qu.:1.0   LAN    : 1050   AL:13835  
    ##  weathda01:   25   Median :2001   Median :1.0   NYA    : 1034   FL:    0  
    ##  vizquom01:   24   Mean   :2001   Mean   :1.1   PHI    : 1026   NL:14459  
    ##  gaettga01:   23   3rd Qu.:2009   3rd Qu.:1.0   CLE    : 1024   PL:    0  
    ##  griffke02:   23   Max.   :2016   Max.   :4.0   SDN    : 1004   UA:    0  
    ##  (Other)  :28147                                (Other):22099             
    ##        G                AB              R                H         
    ##  Min.   :  1.00   Min.   :  0.0   Min.   :  0.00   Min.   :  0.00  
    ##  1st Qu.: 26.00   1st Qu.:  1.0   1st Qu.:  0.00   1st Qu.:  0.00  
    ##  Median : 50.00   Median : 57.0   Median :  4.00   Median : 10.00  
    ##  Mean   : 63.94   Mean   :161.9   Mean   : 21.79   Mean   : 42.63  
    ##  3rd Qu.:101.00   3rd Qu.:298.0   3rd Qu.: 37.00   3rd Qu.: 76.00  
    ##  Max.   :163.00   Max.   :716.0   Max.   :152.00   Max.   :262.00  
    ##                                                                    
    ##       X2B              X3B                HR              RBI        
    ##  Min.   : 0.000   Min.   : 0.0000   Min.   : 0.000   Min.   :  0.00  
    ##  1st Qu.: 0.000   1st Qu.: 0.0000   1st Qu.: 0.000   1st Qu.:  0.00  
    ##  Median : 2.000   Median : 0.0000   Median : 0.000   Median :  4.00  
    ##  Mean   : 8.221   Mean   : 0.9092   Mean   : 4.777   Mean   : 20.78  
    ##  3rd Qu.:14.000   3rd Qu.: 1.0000   3rd Qu.: 6.000   3rd Qu.: 34.00  
    ##  Max.   :59.000   Max.   :23.0000   Max.   :73.000   Max.   :165.00  
    ##                                                                      
    ##        SB                CS               BB              SO        
    ##  Min.   :  0.000   Min.   : 0.000   Min.   :  0.0   Min.   :  0.00  
    ##  1st Qu.:  0.000   1st Qu.: 0.000   1st Qu.:  0.0   1st Qu.:  0.00  
    ##  Median :  0.000   Median : 0.000   Median :  3.0   Median : 15.00  
    ##  Mean   :  3.107   Mean   : 1.333   Mean   : 15.8   Mean   : 30.38  
    ##  3rd Qu.:  2.000   3rd Qu.: 2.000   3rd Qu.: 25.0   3rd Qu.: 50.00  
    ##  Max.   :110.000   Max.   :29.000   Max.   :232.0   Max.   :223.00  
    ##                                                                     
    ##       IBB               HBP               SH               SF        
    ##  Min.   :  0.000   Min.   : 0.000   Min.   : 0.000   Min.   : 0.000  
    ##  1st Qu.:  0.000   1st Qu.: 0.000   1st Qu.: 0.000   1st Qu.: 0.000  
    ##  Median :  0.000   Median : 0.000   Median : 0.000   Median : 0.000  
    ##  Mean   :  1.326   Mean   : 1.451   Mean   : 1.535   Mean   : 1.367  
    ##  3rd Qu.:  1.000   3rd Qu.: 2.000   3rd Qu.: 2.000   3rd Qu.: 2.000  
    ##  Max.   :120.000   Max.   :35.000   Max.   :39.000   Max.   :17.000  
    ##                                                                      
    ##       GIDP              BA             OBP             X1B        
    ##  Min.   : 0.000   Min.   :0.000   Min.   :0.000   Min.   :  0.00  
    ##  1st Qu.: 0.000   1st Qu.:0.158   1st Qu.:0.205   1st Qu.:  0.00  
    ##  Median : 1.000   Median :0.241   Median :0.304   Median :  7.00  
    ##  Mean   : 3.663   Mean   :0.211   Mean   :0.269   Mean   : 28.72  
    ##  3rd Qu.: 6.000   3rd Qu.:0.275   3rd Qu.:0.344   3rd Qu.: 51.00  
    ##  Max.   :35.000   Max.   :1.000   Max.   :1.000   Max.   :225.00  
    ##                   NA's   :6477    NA's   :6413                    
    ##       SLG           teamID.y     lgID.y         salary        
    ##  Min.   :0.000   CLE    : 1043   AL:13823   Min.   :       0  
    ##  1st Qu.:0.200   PHI    : 1029   NL:14471   1st Qu.:  300000  
    ##  Median :0.350   BOS    : 1024              Median :  600000  
    ##  Mean   :0.316   PIT    : 1024              Mean   : 2112891  
    ##  3rd Qu.:0.430   LAN    : 1020              3rd Qu.: 2425000  
    ##  Max.   :4.000   SDN    : 1019              Max.   :33000000  
    ##  NA's   :6477    (Other):22135

<br> <b>Analyzing the Lost Players</b>  
<br>
<p align="justify">
As previously mentioned, the Oakland A’s lost 3 key players during the
off-season. We’ll want to get their stats to see what we have to
replace. The players lost were. first baseman 2000 AL MVP Jason Giambi
(giambja01) to the New York Yankees, outfielder Johnny Damon (damonjo01)
to the Boston Red Sox and infielder Rainer Gustavo “Ray” Olmedo
(‘saenzol01’).<br>
</p>
Use the subset () function to get a data frame called lost\_players from
the combo data frame consisting of those 3 players. Hint: Try to figure
out how to use %in% to avoid a bunch of or statements!
</p>

``` r
lost_players <- subset(x = combo,playerID %in% c("saenzol01","giambja01","damonjo01"))
print(as_tibble(lost_players))
```

    ## # A tibble: 44 x 29
    ##    playerID yearID stint teamID.x lgID.x     G    AB     R     H   X2B   X3B
    ##    <fct>     <int> <int> <fct>    <fct>  <int> <int> <int> <int> <int> <int>
    ##  1 damonjo~   1995     1 KCA      AL        47   188    32    53    11     5
    ##  2 damonjo~   1996     1 KCA      AL       145   517    61   140    22     5
    ##  3 damonjo~   1997     1 KCA      AL       146   472    70   130    12     8
    ##  4 damonjo~   1998     1 KCA      AL       161   642   104   178    30    10
    ##  5 damonjo~   1999     1 KCA      AL       145   583   101   179    39     9
    ##  6 damonjo~   2000     1 KCA      AL       159   655   136   214    42    10
    ##  7 damonjo~   2001     1 OAK      AL       155   644   108   165    34     4
    ##  8 damonjo~   2002     1 BOS      AL       154   623   118   178    34    11
    ##  9 damonjo~   2003     1 BOS      AL       145   608   103   166    32     6
    ## 10 damonjo~   2004     1 BOS      AL       150   621   123   189    35     6
    ## # ... with 34 more rows, and 18 more variables: HR <int>, RBI <int>, SB <int>,
    ## #   CS <int>, BB <int>, SO <int>, IBB <int>, HBP <int>, SH <int>, SF <int>,
    ## #   GIDP <int>, BA <dbl>, OBP <dbl>, X1B <int>, SLG <dbl>, teamID.y <fct>,
    ## #   lgID.y <fct>, salary <int>

<br> Use subset again to only grab the rows where the yearID was 2001.

``` r
lost_players <- subset(lost_players, yearID == 2001)
```

<br> Reduce the lost\_players data frame to the following columns:
playerID,H,X2B,X36,HR,OBP,SLG,BA,AB

``` r
lost_players <- lost_players[,c("playerID","H","X2B","X3B","HR","OBP","SLG","BA","AB")]
print(as_tibble(lost_players))
```

    ## # A tibble: 3 x 9
    ##   playerID      H   X2B   X3B    HR   OBP   SLG    BA    AB
    ##   <fct>     <int> <int> <int> <int> <dbl> <dbl> <dbl> <int>
    ## 1 damonjo01   165    34     4     9 0.324 0.363 0.256   644
    ## 2 giambja01   178    47     2    38 0.477 0.660 0.342   520
    ## 3 saenzol01    67    21     1     9 0.291 0.384 0.220   305

<br> <b>Replacement Players</b> Now we have all the information we need!
Here is your final task - Find Replacement Players for the key three
players we lost. However, you have three constraints:<br>

-   The total combined salary of the three players can not exceed 15
    million dollars.
-   Theis combined number of At Bats (AB) needs to be equal to or
    greater than the lost players
-   The mean OB8P had to equal to or greater than the mean OBP of the
    lost players <br>
    <p align="justify">
    Use the combo dataframe you previously created as the source of
    information! Remember to just use the 2001 subset of that datatrame.
    There are lots of different ways you can do this, so be creative! It
    should be relatively simple to find 3 players that satisfy the
    requirements, note that there are many correct combinations
    available!  
    <br>
    </p>
    Subset the data for only the 2001

``` r
avail_players <- subset(x = combo, yearID == 2001)
```

<br> Plotting to find cutofff salary

``` r
ggplot(data = avail_players,aes(x = OBP,y = salary))+geom_point()+scale_y_continuous(limits = c(0,10000000))
```

    ## Warning: Removed 187 rows containing missing values (geom_point).

![](Figs/excercise%206%20plot1-1.png) <br> Looks like there is no point
in paying above 8 million or so . I’ll choose that as a cutt off point.
There are also a lot of players with OBP==0. Let’s get rid of them
too.  
<br>

``` r
avail_players <- filter(avail_players, salary<8000000 , OBP>0)
```

<br> The total AB of the lost players is 1469. This is about 1500,
meaning \| should probably cut off my avail\_players at 1500/3= 500 AB.

``` r
avail_players <- filter(.data = avail_players,AB>=500)
```

<br> Sorting by OBP

``` r
possible <- head(arrange(avail_players,desc(OBP)),10)
```

<br> Grab columns I’m interested in:

``` r
possible <- possible[,c("playerID", "OBP","AB", "salary" )]
possible
```

    ##     playerID       OBP  AB  salary
    ## 1  giambja01 0.4769001 520 4103333
    ## 2  heltoto01 0.4316547 587 4950000
    ## 3  berkmla01 0.4302326 577  305000
    ## 4  gonzalu01 0.4285714 609 4833333
    ## 5  thomeji01 0.4161491 526 7875000
    ## 6  alomaro01 0.4146707 575 7750000
    ## 7  edmonji01 0.4102142 500 6333333
    ## 8  gilesbr02 0.4035608 576 7333333
    ## 9  pujolal01 0.4029630 590  200000
    ## 10 olerujo01 0.4011799 572 6700000
