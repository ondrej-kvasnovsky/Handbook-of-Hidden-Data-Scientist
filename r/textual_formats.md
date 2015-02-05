# Textual Serialization

We can serialize an object into a file with all the metadata.

#### Write object into file

``` R
data <- data.frame(a=1, b=2)
dput(data, file="data.R")
```

#### Read object from file

``` R
newData <- dget("data.R")
```

#### Reading and writting multiple objects

[dump](http://stat.ethz.ch/R-manual/R-devel/library/base/html/dump.html) and [source](http://stat.ethz.ch/R-manual/R-devel/library/base/html/source.html) functions are used to read and write multiple objects.

Or we can use [save](http://stat.ethz.ch/R-manual/R-devel/library/base/html/save.html) and [load](http://stat.ethz.ch/R-manual/R-devel/library/base/html/load.html) functions.
