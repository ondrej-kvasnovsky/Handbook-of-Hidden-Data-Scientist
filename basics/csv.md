# CSV

### Read CSV file into memory

In order to read tabular data use `read.table` or `read.csv`.

``` R
data <- read.table("./rows.csv", sep=",", header=TRUE)

head(data)
```

or

``` R
data <- read.csv("./rows.csv")

head(data)
```
