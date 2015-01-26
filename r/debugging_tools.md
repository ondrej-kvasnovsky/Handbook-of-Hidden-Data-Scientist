# Debugging

#### Theory

* `message` just a generic notification as message
* `warning` something could go wrong
* `error` fatal error that stops execution
* `condition` generic concept indicating something unexpected happened

#### Functions

* `traceback` prints out the function call stack trace
* `debug` flags function for debug mode
* `browser` suspends execution and starts function in debug
* `trace` allows insert debugging code into a function
* `recover` allows to modify error behavior so function stact trace can be browsed

#### Examples

##### traceback

``` R
> mean(x)
Error in mean(x) : object 'x' not found
> traceback()
1: mean(x)
```

##### debug

``` R
> debug(lm)
> lm (y- x)
debugging in: lm(y - x)
```

And you continue to debugging window.

##### recover

``` R
> options(error=recover)
> read.csv("donotexitfile")
Error in file(file, "rt") : cannot open the connection
In addition: Warning message:
In file(file, "rt") :
  cannot open file 'donotexitfile': No such file or directory

Enter a frame number, or 0 to exit

1: read.csv("donotexitfile")
2: read.table(file = file, header = header, sep = sep, quote = quote, dec = dec, fill = fill, comment.char = comment.char, ...)
3: file(file, "rt")
```
