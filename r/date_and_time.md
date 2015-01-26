# Date and Time

Date is represented by `Date` class. Date is stored as number of days since 1970-01-01.

Time is represented by `POSIXct` (represents date as large integer) or `POSIXlt` (represents date as list of values) classes. Time is stored as number of seconds since 1970-01-01.

# Dates

Get current time.

``` R
> date = date()
[1] "Mon Jan  5 10:54:17 2015"

> class(date)
[1] "character"
```

Get system date.

``` R
date = Sys.Date()
[1] "2015-01-05"

class(date)
[1] "Date"
```

#### Formatting and Parsing

We can use [format function](http://www.inside-r.org/r-doc/base/format) to format dates.

``` R
> date = Sys.Date()

> format(date, "%a %b %d")
[1] "Mon Jan 05"
```

``` R
> as.Date("1982-01-01")
[1] "1982-01-01"
```

``` R
time <- Sys.time()

as.POSIXlt(time)
as.POSIXct(time)
```

#### Create dates from vector

> Have a look [here](http://www.statmethods.net/input/dates.html) for help with formatting strings.

``` R
> strings = c("05-01-2015", "06-01-2015")
> dates = as.Date(strings, "%d-%m-%Y")
> dates
[1] "2015-01-05" "2015-01-06"
```

After the strings are converted to Date type, we can, for example, easily find the difference in days.

``` R
> dates[2] - dates[1]
Time difference of 1 days

> as.numeric(dates[2] - dates[1])
[1] 1
```

Or, for example do the following.

``` R
> weekdays(date[1])
[1] "Monday"

> months(date[1])
[1] "January"

> julian(date[1])
[1] 16440
attr(,"origin")
[1] "1970-01-01"
```

#### lubridate package

We can use [lubridate package](http://cran.r-project.org/web/packages/lubridate/index.html) to work with dates.

``` R
install.packages("lubridate")
library(lubridate)
```

Then we can use functions like:

``` R
> ymd("20150105")
[1] "2015-01-05 UTC"

> myd("05-2015-01")
[1] "2015-05-01 UTC"

> ymd_hms("2015-01-05 10:15:01")
[1] "2015-01-05 10:15:01 UTC"

> wday(ymd("20150105"))
[1] 2
```

> More info about the package is [here](http://www.r-statistics.com/2012/03/do-more-with-dates-and-times-in-r-with-lubridate-1-1-0/).
