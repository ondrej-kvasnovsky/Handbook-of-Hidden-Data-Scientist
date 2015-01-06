# New Variables

We might want to create new variables because we want to
* add extra value for missing values, e.g. NA
* create quantitavive values, for example from numbers
* do transformation

#### Get some data to summarize

We will use data from the following page: https://data.baltimorecity.gov/Culture-Arts/Restaurants/k5ry-ef3g

Run this code in order to download sample data for this tutorial.

``` R
if (!file.exists("./data")) { dir.create("./data") }
url <- "https://data.baltimorecity.gov/api/views/k5ry-ef3g/rows.csv?accessType=DOWNLOAD"

download.file(url, destfile="./data/restaurants.csv", method="curl")

data <- read.csv("./data/restaurants.csv")
```

#### How to create a sequence

Sometimes, we might need to create a sequence.

``` R
> seq(1, 10, by=2)

[1] 1 3 5 7 9
```

``` R
> seq(1, 10, length=3)

[1]  1.0  5.5 10.0
```

#### Create new column by subsetting.

``` R
> data$nearMe = data$neighborhood %in% c("Roland Park", "Homeland")

> table(data$nearMe)

FALSE  TRUE
 1314    13
```

#### Create binary column

``` R
> data$wrongZip = ifelse(data$zipCode < 0, TRUE, FALSE)

> table(data$wrongZip)

FALSE  TRUE
 1326     1
```

#### Create categorical values

The following code will create categorize zipCode values into percentile 0-25, 25-50, 50-75 and 75-100.

``` R
data$zipGroups = cut(data$zipCode,breaks=quantile(data$zipCode))

table(data$zipGroups)
table(data$zipGroups, data$zipCode)
```

Easier way to do that using Hmisc package.

``` R
install.packages("Hmisc")
library(Hmisc)

data$zipGroups = cut2(data$zipCode, g=4)

table(data$zipGroups)
```

#### Create factor values

zipCode is integer and we might want to turn it into factor type.

``` R
> data$zipCodeFactor <- factor(data$zipCode)

> class(data$zipCodeFactor)
[1] "factor"
```

#### Levels of factor variables

``` R
> options <- sample(c("yes", "no"), size=10, replace=TRUE)
> options
 [1] "yes" "no"  "no"  "yes" "yes" "no"  "yes" "no"  "yes" "no"

> optionsFactor = factor(options, levels=c("yes", "no"))
> optionsFactor
 [1] yes no  no  yes yes no  yes no  yes no
Levels: yes no

relevel(optionsFactor, ref="yes")

as.numeric(optionsFactor)
```

#### Mutate function

Mutate function can be used to add variable to a new table.

``` R
install.packages("Hmisc")
library(Hmisc)
install.packages("plyr")
library(plyr)

newData = mutate(data, zipGroups=cut2(zipCode, g=4))

View(newData)
```

#### Transformations

``` R
absolute value
abs(x)

square root
sqrt(x)

ceiling(3.4) is 4
ceiling(x)

floor(3.4) is 3
floor(x)

rounding
round(x, digits=n)

signif(3.475, digits=2) is 3.5
signif(x, digits=n)

cos(x), sin(x), etc.

natural logarithm
log(x)

other logaritmhs
log2(x), log10(x)

exponentiating x
exp(x)
```

More here functions here: http://www.statmethods.net/management/functions.html

