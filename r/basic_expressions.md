# Basics and Data Types

> Nice intro into [R for programmers](http://www.johndcook.com/blog/r_language_for_programmers/).

R uses $ in a manner analogous to the way other languages use dot.

R has several one-letter reserved words: c, q, s, t, C, D, F, I, and T.

#### Comment

``` R
# this is my comment
```

#### Assign a variable

Use `<-` symbols to assign value to a variable.

``` R
> x <- 1
> x
[1] 1
```

> We can assign variable in oposit direction too: `1 -> x`

As equivalent, we can use `assign` function to assign value to a variable.

``` R
> assign("x", 1)
> x
[1] 1
```

#### Print out value of an object

We can simply type name of a variable and that will print it out by itself. Or we can use `print` function to print it out.

``` R
> x <- 1
> x
[1] 1
> print(x)
[1] 1
```

#### Sequence

We can create sequence of number as follows and print it the same way as mentioned above.

``` R
> x <- 1:20
> x
 [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20
```

#### Structure of object

Find structure of an object.

``` R
> data <- data.frame(1:20)
> str(data)
'data.frame':	20 obs. of  1 variable:
 $ X1.20: int  1 2 3 4 5 6 7 8 9 10 ...
```

`str` function is very useful function that display compact structure of an object. It can return about any object, so we can use it also for functions.

``` R
> str(lm)
function (formula, data, subset, weights, na.action, method = "qr", model = TRUE, x = FALSE, y = FALSE, qr = TRUE, singular.ok = TRUE,
    contrasts = NULL, offset, ...)
```

#### Summary function

In case we want more information about an object, we can use `summary` function.

``` R
> library(datasets)
> str(airquality)
'data.frame':	153 obs. of  6 variables:
 $ Ozone  : int  41 36 12 18 NA 28 23 19 8 NA ...
 $ Solar.R: int  190 118 149 313 NA NA 299 99 19 194 ...
 $ Wind   : num  7.4 8 12.6 11.5 14.3 14.9 8.6 13.8 20.1 8.6 ...
 $ Temp   : int  67 72 74 62 56 66 65 59 61 69 ...
 $ Month  : int  5 5 5 5 5 5 5 5 5 5 ...
 $ Day    : int  1 2 3 4 5 6 7 8 9 10 ...
```

#### Arrays

You cannot have array of multiples types. So, you cannot mix integers with strings in one array.

``` R
> array(1, 3)
[1] 1 1 1
```

Now we can play with arrays to find out how they work with types.

``` R
> as.array(c(1, 2))
[1] 1 2
> as.array(c(1, "2"))
[1] "1" "2"
```

#### Numbers

If you type `1`, it gives numeric type `1`.But if you type `1L`, it give `1` as integer type.

#### Attributes

An object can have attributes. To access attributes, use `attributes()`. That allows you to set or modify the attributes.

### Vectors

To create empty vector, use this.

``` R
vector()
```

`c()` function will create a vector. So you can create vector like this:

``` R
c(1, 2)
1:2
```

Or we can create verctor like using `vector` function.

``` R
vector("numeric", length = 10)
```

What happens if you try to mix types in vecotor? R will try to convert it to the same type. So, a surprise might come out.

That leads to thing that you can convert variables to types using as. Like:

``` R
as.numeric(x)
```

> For example, you cannot convert strings to numbers.

#### List

In list, you can mix types.

``` R
list(1, "a")
```

Recursive lists.

```R
x <- list(list(list(list())))
str(x)
> List of 1
>  $ :List of 1
>   ..$ :List of 1
>   .. ..$ : list()
is.recursive(x)
```

> List is index with double brackets.

#### Matrices

Special type of vector.

``` R
matrix(nrows = 2, ncol = 3)
```

Or if you want to create matrix with values.

```R
matrix(1:6, nrows = 2, ncol = 3)
```

Matrix can be created from vector.

``` R
v<-1:10
dim(v) <- c(1, 2)
```

Or you can use cbind or rbind to create matrix.

``` R
x <- 1:3
y <- 1:3
cbind(x,y)
```

#### Factors

Factor is self-describing categorical data. It can be ordered or not ordered.

Factors can be created with factors() function.

``` R
factor(c("a", "b"))
```

Factores are represented as numbers internally. You can set ordering using level attribute.

``` R
factor(c("a", "b"), level=c("a", "b"))
```

#### Missing values

You can yous is.na() function to test whether a value is na.

#### Data Frames

Data frames store tabular data and they can be of different classes. Every raw has names.

``` R
> x <- data.frame(a = 1:4, b = c(T, T, F, F))
> x
  a     b
1 1  TRUE
2 2  TRUE
3 3 FALSE
4 4 FALSE
```

#### Names

All R objects can have names. It can help to create self-describing data.

``` R
> x <- 1:3
> names(x)
NULL
> names(x) <- c("a", "b", "c")
> names(x)
[1] "a" "b" "c"
```

Lists can have names too.

``` R
> x <- list(a=1, b=2)
> x
$a
[1] 1

$b
[1] 2
```

How to access variable in list.

``` R
> x <- list(aa=1)
> x$aa
[1] 1
```

R will try to determin what variable you want even if you not provide full name.

``` R
> x <- list(aa=1)
> x$a
[1] 1
```

Matrix can have names too (dim names).

``` R
> m <- matrix(1:4, nrow=2, ncol=2)
> dimnames(m) <- list(c("a", "b"), c("a", "b"))

> m
  a b
a 1 3
b 2 4
```
