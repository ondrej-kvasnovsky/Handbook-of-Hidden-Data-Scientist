# Editing text

Rules for editing column names:
* All lower case when possible
* Name should be descriptive, not shortcuts
* No duplicates
* No underscores, dots or white spaces

Rules for values:
* Should be factors
* Should be descrpitive, like TRUE/FALSE instead of 1/0.

#### Get some data to edit

We will use data from the following page: https://data.baltimorecity.gov/Transportation/Baltimore-Fixed-Speed-Cameras/dz54-2aru

Run this code in order to download sample data for this tutorial.

``` R
if (!file.exists("./data")) { dir.create("./data") }
url <- "https://data.baltimorecity.gov/api/views/dz54-2aru/rows.csv?accessType=DOWNLOAD"

download.file(url, destfile="./data/cameras.csv", method="curl")

data <- read.csv("./data/cameras.csv")

names(data)
```

#### Lower or upper case

``` R
tolower(names(data))
toupper(names(data))
```

#### Split values

For example, split word when there is a dot.

``` R
strsplit(names(data), "\\.")
```

#### Get only first element

In this example, we will split a string and get only first element.

``` R
firstElement <- function (x) { unlist(strsplit(x, ".", fixed=TRUE))[1] }

sapply(as.list(names(data)), firstElement)
```

#### Replace characters

The following code will replace all `_` by empty space.

``` R
sub("_", " ", names(reviews))
```

`sub` function will always replace only first found characeter. In order to replace all, use `gsub`.

``` R
> test <- "test_value_1"

> sub("_", " ", test)
[1] "test value_1"

> gsub("_", " ", test)
[1] "test value 1"
```

#### Searching

Search for a string in a column.
``` R
> grep("Alameda", data$intersection)
[1]  4  5 36
```

How many times a string appears in column.

``` R
> table(grepl("Alameda", data$intersection))

FALSE  TRUE
   77     3
```

> More about `grep` function is [here](http://stat.ethz.ch/R-manual/R-devel/library/base/html/grep.html).

#### More string functions

We can use [stringr package](http://cran.r-project.org/web/packages/stringr/index.html) to easier work with strings.

``` R
install.packages("stringr")
library(stringr)
```

Get number of characters.

``` R
> nchar("Hello there")
[1] 11
```

Get sub string.

``` R
substr("Hello there", 1,5)
```

Connect strings into one.

``` R
> paste("Hello", "there")
[1] "Hello there"

> paste0("Hello", "there")
[1] "Hellothere"
```

Trim string.

``` R
str_trim("   Hello   ")
```
