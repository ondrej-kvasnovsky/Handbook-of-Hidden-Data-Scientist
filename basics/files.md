# Files

Before we start working with files we need to set working directory using `setwd()` function. When we set working directory, all the files will be automatically stored there.

### Functions

Here is few functions that might be handy while working with files.

`getwd()` returns current working directory.

`setwd()` sets current working directory. For example `setwd("/Users/ondrej/R/examples")` will change working directory to `"/Users/ondrej/R/examples"`.

`file.exists("raw-data.csv")` checks whether a file exists.

`dir.create("temp")` creates a new directory in working directory.


`download.file()` downloads file to working directory.

``` R
url <- "https://data.baltimorecity.gov/api/views/dz54-2aru/rows.csv?accessType=DOWNLOAD"
download.file(url, destfile="./rows.csv", method="curl")
```

`list.files(".")` lists files in working directory.

`readLines` reads file into memory

`load` will read binary data

`file.remove(...)` removes a file

More info is [here](http://stat.ethz.ch/R-manual/R-devel/library/base/html/files.html).
