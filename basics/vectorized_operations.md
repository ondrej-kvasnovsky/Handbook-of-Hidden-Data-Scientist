# Vectorized Operations

R will loop through the lists and do the operation on all data inside.

``` R
> x <- 1:3
> y <- 2:4
>
> x >= y
[1] FALSE FALSE FALSE
>
> x == y
[1] FALSE FALSE FALSE
>
> x * y
[1]  2  6 12
>
> x / y
[1] 0.5000000 0.6666667 0.7500000
```

We can also do the same with matricies.

``` R
x <- matrix(1:4, 2, 2)
y <- matrix(1:4, 2, 2)
```

Element-wise multiplication.

``` R
> x * y
     [,1] [,2]
[1,]    1    9
[2,]    4   16
```

True matrix multiplication.

``` R
> x %*% y
     [,1] [,2]
[1,]    7   15
[2,]   10   22
```
