# Limitations

* R loads data into memory by default. You could you some packages like [ff](http://cran.r-project.org/web/packages/ff/index.html) or [bigmemory](http://cran.r-project.org/web/packages/bigmemory/index.html).
* R uses just 1 CPU. Stackoverflow says [you can go multi-threaded](http://stackoverflow.com/questions/10835122/multithreading-with-r).
* R does not have int64, but it seems [R has it](http://google-opensource.blogspot.com/2011/11/bringing-64-bit-data-to-r.html).
* Not all packages mentioned above supports all the other packages.

