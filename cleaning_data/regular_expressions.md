# Regular Expressions

In many cases, first we will have to develop a regular expression. We can use http://www.regexr.com to do that.

Lets say we created this regular expression `want|develop` that will find rows where there is "want" or "develop" words.

We can use regular expressions with `grep`, `grepl`, `sub`, `strsplit`, `regexpr`, `gregexpr` and `gsub` functions.

#### [grep](http://stat.ethz.ch/R-manual/R-devel/library/base/html/grep.html) function

``` R
> text <- "We want to develop new regular expression."
> grep("want|develop", text, value=TRUE)

[1] "We want to develop new regular expression."
```

More about [regular expressions in R](http://www.regular-expressions.info/rlanguage.html) or [here](http://stat.ethz.ch/R-manual/R-devel/library/base/html/regex.html).
