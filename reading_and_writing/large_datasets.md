# Larger Datasets

`read.csv` and similar function will read all the data into RAM memory. That will cause issues when the data is bigger and it does not fit into the memory.

#### Calculating Memory Requirements

Example, where one cell in a table takes 8 bytes, which might be size of a number.

``` R
> rows <- 1500000
> columns <- 120
> bytes <- 8
> megaBytes <- (rows * columns * bytes) / 2^20
> megaBytes
[1] 1373.291

> gigaBytes <- (rows * columns * bytes) / 1024^3
> gigaBytes
[1] 1.341105
```

Then make sure you have twice more memory then calculated. So, for 1.3GB you should have 2.6GB.

#### Speed up loading

Tell what types are in each columns. Estimate how many rows is in the file.

``` R
initial <- read.table("data.txt", nrows=100)
classes <- sapply(initial, class)
data <- read.table("data.txt", colClasses = classes)
```

#### Larger than Large Datasets

If your data do not fit into RAM memory use [colbycol](http://colbycol.r-forge.r-project.org) or [bigmemory](http://cran.r-project.org/web/packages/bigmemory/index.html) package. It will internally split table into columns where each column is stored in separate file. Then it will operate over these files and that will not require huge RAM memory on your computer or server.

Read [Handling Large Datasets in R](http://www.r-bloggers.com/handling-large-datasets-in-r) blog post to lear more about reading large datasets.
