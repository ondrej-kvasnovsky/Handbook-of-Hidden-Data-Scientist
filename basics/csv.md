# CSV

### Read CSV file into memory

``` R
data <- read.table("./rows.csv", sep=",", header=TRUE)

head(data)
```

or

``` R
data <- read.csv("./rows.csv")

head(data)
```
