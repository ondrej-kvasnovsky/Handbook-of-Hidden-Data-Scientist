# Reshaping

The goal is to get tidy data. That means to have:

* Each variable forms a column
* Each observation forms a row
* Each table/file stores data about one kind of observations.

### Data to reshape

We will use standard R data set `mtcars`.

``` R
head(mtcars)
```

#### Install reshape2 package

> Nice article about [respahe2](http://seananderson.ca/2013/10/19/reshape.html)

``` R
install.packages("reshape2")
library(reshape2)
```

#### Melting data set

We will pass the following variables into `melt` function:
* data set
* what columns are IDs
* what columns are variables

The following code will add one more column with row names and primarilly, make IDs from "carname", "gear" and "cyl". The remaining columns will be melted down.

``` R
mtcars$carname <- rownames(mtcars)

carMelt <- melt(
    mtcars,
    id=c("carname", "gear", "cyl"),
    measure.vars=c("mpg", "hp")
)
```

Let's have a look at the melted values.

``` R
> head(carMelt, n=3)
        carname gear cyl variable value
1     Mazda RX4    4   6      mpg  21.0
2 Mazda RX4 Wag    4   6      mpg  21.0
3    Datsun 710    4   4      mpg  22.8
...
62  Ferrari Dino    5   6       hp   175
63 Maserati Bora    5   8       hp   335
64    Volvo 142E    4   4       hp   109
```

The better way to see what happend is to display values in table. Watch values in `variable` column.

``` R
View(carMelt)
```

#### Casting data sets

We can cast the data set into different shapes.

``` R
> cylData <- dcast(carMelt, cyl ~ variable)
Aggregation function missing: defaulting to length

> cylData

  cyl mpg hp
1   4  11 11
2   6   7  7
3   8  14 14
```

We can specify function to aggregate values.

``` R
> cylData <- dcast(carMelt, cyl ~ variable, mean)

> cylData

  cyl      mpg        hp
1   4 26.66364  82.63636
2   6 19.74286 122.28571
3   8 15.10000 209.21429
```

#### Average Values

We will `InsectSprays` data set.

``` R
> head(InsectSprays)

  count spray
1    10     A
2     7     A
3    20     A
4    14     A
5    14     A
6    12     A
```

The following code is using `tapply` function to show sum of `count` column for each `spray`.

``` R
> tapply(InsectSprays$count, InsectSprays$spray, sum)

  A   B   C   D   E   F
174 184  25  59  42 200
```

#### Split values

``` R
> split <- split(InsectSprays$count, InsectSprays$spray)

> split
$A
 [1] 10  7 20 14 14 12 10 23 17 20 14 13

$B
 [1] 11 17 21 11 16 14 17 17 19 21  7 13
...
```

#### Split and sum

``` R
> splitSum <- lapply(split, sum)

> splitSum
$A
[1] 174

$B
[1] 184
...
```

#### Combine

We can combine the values craeted above in two ways.

``` R
unlist(splitSum)
```

``` R
sapply(split, sum)
```

#### Using plyr package to summarize values

> Be careful, there is `summarise` and NOT `summarize`. If you do that mistake you get **argument "by" is missing, with no default** error.

``` R
ddply(InsectSprays, .(spray), summarise, sum=sum(count))
```

> More to lear on http://www.r-bloggers.com/a-fast-intro-to-plyr-for-r

#### Other functions

* `acast` casting multi-dimensional array
* `arrange` faster reordering without using order() function
* `mutate` adding new variables


