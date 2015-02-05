# Functions

Function is an object, as everything in R.

#### Hello world function

Function that sums two numbers.

``` R
sumNumbers <- function(x, y) {
  x + y
}

sumNumbers(1, 2)
# or better to name parameter when assigining values
sumNumbers(x=1, y=2)

```

#### Default parameter

The following function shows how to create parameter with a default value.

``` R
above <- function(x, n = 10) {
    use <- x > n
    x[use]
}

x <- 1:20
above(x, 10)
```

#### Calculating mean

Let's calculate mean of column in a matrix.

``` R
columnMean <- function(matrix, removeNA = TRUE){
    columnCount <- ncol(matrix)
    means <- numeric(columnCount)
    for (i in 1:columnCount) {
        means[i] <- mean(matrix[,i], na.rm = removeNA)
    }
    means
}

columnMean(airquality)
```

#### Lazy Evaluation

When function `f` does not use `b` parameter, it will never complain thanks to lazy evaluation.

``` R
f <- function(a, b) {
    a
}

f(1)
```

#### Three dots `...` argument

Can be used to pass multiple parameters and we do not want to list them all.

``` R
myplot <- function(x, y, type="1", ...) {
    plot(x, y, type, ...)
}
```

If we do not know number of arguments. The function prints all parameters we have passed into the function.

``` R
f <- function(..., x) {
    print(as.list(match.call()))
}

f("a", "b", x = 1)
```


#### Find function's environment

``` R
ls(environment(read.table))
```

#### Lexical Scoping

* Typically, a function is defined in global environment.
* You can have functions inside functions

``` R
> make.fun <- function(n) {
    fun <- function(x) {
        x*n
    }
    fun
}

> fun <- make.fun(2)
> fun
function(x) {
        x*n
    }
<environment: 0x1057113f8>
> fun(2)
[1] 4
```

R searches a variable in a series of environments to find appropiate value.

#### Lexical vs. Dynamic Scoping

What is returned when we execute `f(3)` function.

``` R
y <- 10

f <- function(x) {
    print("f 1")
    print(y)
    print(x)

    y <- 2

    result <- y^2 + g(x)
    print("f 2")
    print(y)
    print(x)

    result
}

g <- function(x) {
    print("g")
    print(y)
    print(x)

    print(x*y)
    x*y
}
```

* With lexical scoping, `y` is looked up by environment where `g` function has been created. In this case, in *global environment*.
* With dynamic scoping, `y` is looked up by environment where the function was called. It is also referred as *calling environment* or *parent frame*.

The result is following.

``` R
> f(3)
[1] "f 1"
[1] 10
[1] 3
[1] "g"
[1] 10
[1] 3
[1] 30
[1] "f 2"
[1] 2
[1] 3
[1] 34
```
> Consequence of lexical scoping: all objects must be stored in memory and all function must have pointer to their environment.

> More about [scoping in R](https://darrenjw.wordpress.com/2011/11/23/lexical-scope-and-function-closures-in-r/).

#### Scoping Rules - Example

For more information about scoping have a look [here](https://github.com/jtleek/modules/blob/master/02_RProgramming/Scoping/index.md).


