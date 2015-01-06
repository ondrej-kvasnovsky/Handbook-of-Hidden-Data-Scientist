# Subsetting

First we create a table with random values.

``` R
data <- data.frame(
    "column1"=sample(1:5),
    "column2"=sample(6:10),
    "column3"=sample(11:15)
)

data <- data[sample(1:5),]

data$column2[c(1,3)] = NA
```

Here is how that table could look like.

``` R
> data
  column1 column2 column3
5       5      NA      11
2       4       9      15
4       1      NA      12
3       2       6      13
1       3       7      14
```

Return first column by index. When we pass a number, it will return column from that position.

``` R
> data[,1]

[1] 5 4 1 2 3
```

Return column by name.

``` R
> data[,"column2"]

[1] NA  9 NA  6  7
```

Return column by name and rows by position.

``` R
> data[1:2,"column2"]

[1] NA  9
```

Filter by column values using logical operator AND.

``` R
> data[(data$column1 >= 5 & data$column3 > 10),]

  column1 column2 column3
5       5      NA      11
```

Filter by column values using logical operator OR.

``` R
> data[(data$column1 >= 5 | data$column3 > 10),]

  column1 column2 column3
5       5      NA      11
2       4       9      15
4       1      NA      12
3       2       6      13
1       3       7      14
```

If tehre is missing value in the data set and we do not want to return it, we have to use `which` function.

``` R
> data[which(data$column2 > 3),]

  column1 column2 column3
2       4       9      15
3       2       6      13
1       3       7      14
```
Visually compare what is returned by the query above and the query below, which is not using `which` function..

``` R
> data[(data$column2 > 3),]

     column1 column2 column3
NA        NA      NA      NA
2          4       9      15
NA.1      NA      NA      NA
3          2       6      13
1          3       7      14
```

Sort values by column.

``` R
sort(data$column1, decreasing=FALSE)

[1] 1 2 3 4 5
```

Sort values by column and place "NA" values at the end.

``` R
> sort(data$column2, decreasing=FALSE, na.last=TRUE)

[1]  6  7  9 NA NA
```

Order data by a column.

``` R
> data[order(data$column1),]

  column1 column2 column3
4       1      NA      12
3       2       6      13
1       3       7      14
2       4       9      15
5       5      NA      11
```

Ordering with `plyr` library.

``` R
> library(plyr)
> arrange(data, column1)

  column1 column2 column3
1       1      NA      12
2       2       6      13
3       3       7      14
4       4       9      15
5       5      NA      11

> arrange(data, desc(column1))

  column1 column2 column3
1       5      NA      11
2       4       9      15
3       3       7      14
4       2       6      13
5       1      NA      12
```

Adding columns

``` R
data$column4 <- rnorm(5)
```

or

``` R
data <- cbind(data, rnorm(5))
```
