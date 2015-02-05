# Control Structures

Control structures allow us to control flow of the program.

#### If Else

``` R
a <- 0
if (a < 1) {
    a <- 100
} else {
    a <- -100
}
a

[1] 100
```

#### For loop

``` R
numbers <- 1:10
for (i in numbers) {
    print (i)
    # or
    print (numbers[i])
}
```

Nested loops.

``` R
numbers <- matrix(1:6, 2, 3)
for (i in seq_len(nrow(numbers))) {
    for (j in seq_len(ncol(numbers))) {
        print (numbers[i, j])
    }
}
```

#### While loops

``` R
count <- 0

while(count < 10) {
    print(count)
    count <- count + 1
}
```

#### Repeat

``` R
repeat {
    x <- runif(1, 0, 200)

    print(x)
    if(x < 100) {
        break
    }
}
```

#### Next, break

``` R
for (i in 1:10) {
    if (i <= 5) {
        next
    }
    if (i == 8) {
        break
    }
    print(i)
}
```

