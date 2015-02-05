# Loop Functions

#### lapply

Loop over a list and apply a function.

Let's calculate mean of each element in the list using `mean` function.

``` R
list <- list(a = 1:10, b = 10:100)

lapply(list, mean)
```

Using `runif` function.

``` R
lapply(1:10, runif, min = 0, max = 10)
```

#### sapply

`sapply` is almost the same as `lapply` but it tries to simplify the result if possible.

* If the result is a list, it returns vector
* If the result is list where each element is vector, matrix is returned
* If it does not know, list is returned

Let's see what is the difference between lapply and sapply.

``` R
> lapply(list, mean)
$a
[1] 5.5

$b
[1] 55

> sapply(list,mean)
   a    b
 5.5 55.0
```

#### apply

Evaluate

``` R
> str(apply)
function (X, MARGIN, FUN, ...)
```

* X - is array
* MARGIN - margin to retain
* FUN - function
* ... - argumetns for FUN function

``` R
x <- matrix(rnorm(200), 20, 10)

apply(x, 1, mean)
apply(x, 2, mean)
```

> We can use `rowSums`, `rowMeans`, `colSums` and `colMeans` functions instead, they are faster.

#### mapply

With mapply function we can iterate trough multiple sets. E.g.

``` R
x <- list(rep(1, 4), rep(2, 3))
mapply(mean, x)
```

#### tapply

Applies function across subset of a vector. It splits data into little pieces and after calculation it is put together again.

First we create a sample data.

``` R
> x <- c(rnorm(10), runif(10), rnorm(10, 1))
> f <- gl(3, 10)
> x
 [1]  0.6546703  0.1908048  0.7510316 -0.5275388  0.1565112
 [6] -1.0819140  0.5881377  1.9318782 -1.6296265  0.1217391
[11]  0.8565242  0.9489818  0.6900339  0.9405762  0.5868754
[16]  0.7953035  0.1449435  0.3803465  0.6014722  0.7375775
[21]  0.9127986 -0.1662831  0.4377588  0.9954957  1.0922615
[26]  1.2733158  1.4715993  3.6705109  1.1215348  1.1913898
> f
 [1] 1 1 1 1 1 1 1 1 1 1 2 2 2 2 2 2 2 2 2 2 3 3 3 3 3 3 3 3 3 3
Levels: 1 2 3
```

Mean of each number in x.

``` R
> tapply(x, f, mean)
        1         2         3
0.1155694 0.6682635 1.2000382
```

Turn of simplify and function returns list then.

``` R
> tapply(x, f, mean, simplify=FALSE)
$`1`
[1] 0.1155694

$`2`
[1] 0.6682635

$`3`
[1] 1.200038
```
