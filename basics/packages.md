# Packages

Before we start installing and loading packages, lets have a look how to view all the available packages.

### Browse packages

Assign result of `available.packages()` function call to `packages` variable.

``` R
packages <- available.packages()
```

Now we can browse a package details.

In order to display first 3 columns from the first row, use head function.

``` R
head(rownames(packages), 3)
```

If you want to browse all the packages in a table, use View function.

``` R
View(packages)
```

### Using packages

Before we start using a package, we have to intall it. Use `install.packages()` to install a package.

``` R
install.packages("ggplot2")
```

We can also install multiple packages in one line.

``` R
install.packages(c("ggplot2", "devtools"))
```

We need to load a package before using it. Note that all the dependendent packages will be loaded before the named package is loaded.

``` R
library(ggplot2)
library(devtools)
```

### Available packages

Run `search()` function after you install a package in order to see all the available and loaded packages.

``` R
search()
```

The code above will display the following list of functions in the console:

``` R
> search()
 [1] ".GlobalEnv"        "package:devtools"  "package:ggplot2"   "tools:rstudio"     "package:stats"     "package:graphics"
 [7] "package:grDevices" "package:utils"     "package:datasets"  "package:methods"   "Autoloads"         "package:base"
 ```

### Package details

Quick information can be obtainedby using citation() function.

``` R
citation("ggplot2")
```

### More interesting packages

* [twitterR](http://cran.r-project.org/web/packages/twitteR/index.html)
* [rfigshare](http://cran.r-project.org/web/packages/rfigshare/index.html)
* [rplos](http://cran.r-project.org/web/packages/rplos/index.html)
* [rOpenSci](http://ropensci.org/packages/)
* [RFacebook](http://cran.r-project.org/web/packages/Rfacebook/index.html)
* [RGoogleMaps](http://cran.r-project.org/web/packages/RgoogleMaps/index.html)
