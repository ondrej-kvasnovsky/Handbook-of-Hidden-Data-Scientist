# Profiler

> We shoudn't do performance optimalizations as a first thing. Do it after a function or feature is developed. Have a look at [Not Today](http://i.imgur.com/j5b5JCr.jpg) image.

### system.time()

`system.time()` returns amount of time taken to evaluate an expression.

``` R
> system.time(readLines("http://www.jhsph.edu"))
   user  system elapsed
  0.003   0.002   0.820
```


``` R
system.time({
    lines <- readLines("http://www.jhsph.edu")
    print(lines)
})
# prints a lot lof lines...
   user  system elapsed
  0.184   0.038   0.675
```

### Rprof

There are two function provided:

* `Rprof()`
* `summaryRprof()`

> Do not use `system.time` and `Rprof` together!

``` R
Rprof(tmp <- tempfile())
example(glm)
Rprof()
summaryRprof(tmp)
```

> More about profiler is [here](https://tgmstat.wordpress.com/2013/09/25/profiling-r-code/)
