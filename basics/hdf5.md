# HDF5

What is [HDF5](http://www.hdfgroup.org/HDF5/).

* Used for storing large data sets
* Supports large range of data types
* Can be used to optimize reading and writing from disc in R

> Why HDF5 and not just Hadoop? In short **HDF5 is a smart data container and HDFS is a file system**. Longer version is [here](http://www.hdfgroup.org/HDF5/faq/hadoop.html).

#### Install pacakge

More details about [rhdf5](http://watson.nci.nih.gov/bioc_mirror/packages/2.11/bioc/vignettes/rhdf5/inst/doc/rhdf5.pdf) package. [Here](http://www.bioconductor.org/packages/devel/bioc/manuals/rhdf5/man/rhdf5.pdf) is more details about provided functions.

``` R
source("http://bioconductor.org/biocLite.R")
biocLite("rhdf5")

library(rhdf5)
```

#### Create h5 file

In order to create a file use `h5createFile` function.

``` R
created = h5createFile("example.h5")
```

Create file in a group.

``` R
createdFile = h5createFile("example.h5")

createdGroup = h5createGroup("example.h5", "group1")
```

List h5 files.

``` R
h5ls("example.h5")
```

#### Write data into h5 file

Here is an example how to write a matrix into h5 file.

``` R
library(data.table)

matrixFile = h5createFile("matrix.h5")

A = matrix(1:10, nr=5, nc=2)
h5write(A, "matrix.h5", "a matrix")
```

> You might need to run H5close() after experimenting with h5 files.

Here is an example how to write an array into h5 file.

``` R
library(data.table)

arrayFile = h5createFile("array.h5")

B = array(seq(0.1, 0.2, by=0.1), dim=c(5,2,2))

h5write(B, "array.h5", "an array")
```

#### Write a data set

An example how to write `data.table` into h5 file.

``` R
library(data.table)

years = c(2012, 2013)
average = c(250, 275)
table.values <- data.table(year = years, averageBeerConsumption = average)

datasetFile = h5createFile("dataset.h5")
h5write(table.values, "dataset.h5", "data set")
```

We can also add an attribute (or rather call it metadata) as follows. We add date when the table has been created.

``` R
attr(table.values, "created") <- date()
```

#### Read data from h5 file

``` R
h5read("array.h5", "data set")
```
