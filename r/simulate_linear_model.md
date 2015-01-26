# Simulate Linear Model

Here is an example how to simplate data with linear relationship.

``` R
set.seed(10)

x <- rnorm(100)
e <- rnorm(100, 0, 2)
y <- 0.5 + 2 * x +e
summary(y)
plot(x, y)
```

What if `x` is binary?

``` R
set.seed(10)

x <- rbinom(100, 1, 0.5)
e <- rnorm(100, 0, 2)
y <- 0.5 + 2 * x +e
summary(y)
plot(x, y)
```

#### Possion Distribution

``` R
set.seed(10)

x <- rnorm(100)
log.mu <- 0.5 + 0.3 * x
y <- rpois(100, exp(log.mu))
summary(y)
plot(x, y)
```

> More about [Poisson distribution](http://en.wikipedia.org/wiki/Poisson_distribution).
