# Random Variables

#### Random numbers

* `r` for random numner
* `d` for density
* `p` for cumulative distribution
* `q` for quantile function

More about functions is [here](http://www.biogem.org/downloads/notes/Generating%20Random%20Variables%20in%20R.pdf).

The random numbers are not actually random. You can reproduce them by setting seed.

``` R
> set.seed(1)
> rnorm(5)
[1] -0.6264538  0.1836433 -0.8356286  1.5952808  0.3295078

> set.seed(1)
> rnorm(5)
[1] -0.6264538  0.1836433 -0.8356286  1.5952808  0.3295078
```

#### Sampling

``` R
> set.seed(1)

> sample(1:10, 4)
 [1] 3 4 5 7
> sample(letters, 4)
 [1] "f" "w" "y" "p"
> sample(letters, replace=T)
 [1] "q" "b" "f" "e" "r" "j" "u" "m" "s" "z" "j" "u" "y" "f" "q" "d" "g" "k" "a" "j" "w" "i" "m" "p" "m" "e"
```

> With `replace` set to true, the values can repeate.
