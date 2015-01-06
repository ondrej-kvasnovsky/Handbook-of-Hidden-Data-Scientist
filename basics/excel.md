# Excel

On Mac, we can use [gdata package](http://cran.r-project.org/web/packages/gdata/index.html).

### Read Excel file into memory

You might need to intall the following package to run this example.

``` R
install.packages("gdata", dep = T)

library(gdata)
```

Run the following code.

``` R
url <- "https://data.baltimorecity.gov/api/views/dz54-2aru/rows.xlsx?accessType=DOWNLOAD"

download.file(url, destfile="./raw-data.xlsx", method="curl")

excel.data <- read.xls("raw-data.xlsx")

View(excel.data)
```
