# Data Table

Facts about `data.table`.

* Extends from `data.frame` and therefore should provide the same API.
* Is written in C and is really fast.
* Much faster at subsetting, group and updating.

#### Hello world

``` R
install.packages("data.table")
library(data.table)

years = c(2012, 2013)
average = c(250, 275)
table.values <- data.table(year = years, averageBeerConsumption = average)
```

See all `data.table` tables created in memory.

``` R
tables()
```

#### Subsetting rows.

Access row on specific index.

``` R
table.values[2]
table.values[c(1,2)]
```

Access rows that fulfil a condition.

``` R
table.values[table.values$year==2012]
```

#### Calculate values from columns

``` R
table.values[, sum(averageBeerConsumption)]

table.values[, list(mean(year), sum(averageBeerConsumption))]
```

#### Return table of values for a column

``` R
table.values[, table(year)]
```

#### Add new column

``` R
table.values[, volume:=averageBeerConsumption*0.5]
```

#### Multiple operations.

``` R
table.values[,
    x:={temp <- averageBeerConsumption*year;
log2(temp)
}]
```

#### Plyr like operations

``` R
table.values[, y:= year<2013]
```

#### Grouping by

``` R
table.values[, sum:= sum(averageBeerConsumption), by= year]
```

#### Count number of occurrences

``` R
table.values[, .N, by=year]
```

#### Keys

Making table faster by setting the keys

``` R
setkey(table.values, year)
```

Then we can join tables by keys.

``` R
setkey(table1.values, year)
setkey(table2.values, year)

merge(table1.values, table2.values)
```

#### Fast reading

First we create a file that we can use to test speed of reading.

``` R
big.file <- data.frame(x=rnorm(1E6), y=rnorm(1E6))

file <- tempfile()

write.table(big.file, file=file, row.names=FALSE, col.names=TRUE, sep="\t", quote=FALSE)
```

Slow approach using `read.table` function.

``` R
system.time(read.table(file, header=TRUE, sep="\t"))
```

Faster approach using `fread` function.

``` R
system.time(fread(file))
```
