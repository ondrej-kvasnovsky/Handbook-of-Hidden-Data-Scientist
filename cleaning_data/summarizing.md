# Summarizing

#### Get some data to summarize

We will use data from the following page: https://data.baltimorecity.gov/Culture-Arts/Restaurants/k5ry-ef3g

Run this code in order to download sample data for this tutorial.

``` R
if (!file.exists("./data")) { dir.create("./data") }
url <- "https://data.baltimorecity.gov/api/views/k5ry-ef3g/rows.csv?accessType=DOWNLOAD"

download.file(url, destfile="./data/restaurants.csv", method="curl")

data <- read.csv("./data/restaurants.csv")
```

View data to make sure there is at least something.

Check size in bytes.

``` R
object.size(data)

print(object.size(data), units="Mb")
```

View data in table.

``` R
View(data)
```

View first few rows.

``` R
head(data, n=3)
```

View last few rows.

``` R
tail(data, n=3)
```

Get summary for each attribute.

``` R
summary(data)
```

Return types and more info about data.

``` R
str(data)
```

See quantile of values in specific column.

``` R
quantile(data$councilDistrict, na.rm=TRUE)
```

Get quantile for different percentiles.

``` R
quantile(data$councilDistrict, probs = c(0.5, 0.75, 0.9))
```

Create table of values from a column. Option `ifany` will enable the table to show missing values.

``` R
table(data$zipCode, useNA = "ifany")
```

Make two dimensional table.

``` R
table(data$councilDistrict, data$zipCode)
```

Check for missing values. The following command returns number of NA values.

``` R
sum(is.na(data$zipCode))
```

The same as above but this returns true or false.

``` R
any(is.na(data$zipCode))
```

Take all values and check if all fulfil a condition.

``` R
all(data$zipCode < 0)
```

Check all columns and get count of NA values for each column.

``` R
colSums(is.na(data))
```

Covert the command above to single command that returns true or false instead of counts.

``` R
all(colSums(is.na(data)) == 0)
```


``` R
table(data$zipCode %in% c("21212"))
```

Find all values that full fill a condition.

``` R
table(data$zipCode %in% c("21212"))
```

The same as above but with multiple values. There is OR condition between the values in the condition.

``` R
table(data$zipCode %in% c("21212", "21213"))
```

Filter out specific rows based on a condition and return values (not just numbers/counts).

``` R
data[data$zipCode %in% c("21212", "21213"),]
```

Cross tabs. The following example is nonsense. But it will break down the data by policeDistrict and counsilDistrict and create sums from zipCodes values.

``` R
xtabs = xtabs(zipCode ~ policeDistrict + councilDistrict, data=data)

-- to make data compact and easier to view... if possible.
ftable(xtabs)
```
