# Merging

``` R
fileUrl1 <- "https://dl.dropboxusercontent.com/u/7710864/data/reviews-apr29.csv"
fileUrl2 <- "https://dl.dropboxusercontent.com/u/7710864/data/solutions-apr29.csv"
download.file(fileUrl1,destfile="./data/reviews.csv",method="curl")
download.file(fileUrl2,destfile="./data/solutions.csv",method="curl")
reviews <- read.csv("./data/reviews.csv"); solutions <- read.csv("./data/solutions.csv")
head(reviews,2)
head(solutions,2)
```

First, look at the names in data sets.

``` R
names(reviews)
names(solutions)
```

Merge is done by column names.

``` R
> data = merge(reviews, solutions, by.x="solution_id", by.y="id", all=TRUE)
```

Now look at what has been done.

``` R
> head(reviews, n=3)
  id solution_id reviewer_id      start       stop time_left accept
1  1           3          27 1304095698 1304095758      1754      1
2  2           4          22 1304095188 1304095206      2306      1
3  3           5          28 1304095276 1304095320      2192      1

> head(solutions, n=3)
  id problem_id subject_id      start       stop time_left answer
1  1        156         29 1304095119 1304095169      2343      B
2  2        269         25 1304095119 1304095183      2329      C
3  3         34         22 1304095127 1304095146      2366      C

> head(data, n=3)

  solution_id id reviewer_id    start.x     stop.x time_left.x accept problem_id subject_id    start.y
1           1  4          26 1304095267 1304095423        2089      1        156         29 1304095119
2           2  6          29 1304095471 1304095513        1999      1        269         25 1304095119
3           3  1          27 1304095698 1304095758        1754      1         34         22 1304095127
... and other columns
```

The default merge is done by names that are common to both data sets. Have a look at common fields.

``` R
> intersect(names(reviews), names(solutions))

[1] "id"        "start"     "stop"      "time_left"
```

Then we can try to merge the data sets. The result will be a mess, in this example because we are matching two data sets by nonsense columns, like `time_left` while `time_left` could be totaly different number for each data set. That means the data will be larger because there be more unique combinations of matching column values.

``` R
> data = merge(reviews, solutions, all=TRUE)

> head(data)
  id      start       stop time_left solution_id reviewer_id accept problem_id subject_id answer
1  1 1304095119 1304095169      2343          NA          NA     NA        156         29      B
2  1 1304095698 1304095758      1754           3          27      1         NA         NA   <NA>
3  2 1304095119 1304095183      2329          NA          NA     NA        269         25      C
4  2 1304095188 1304095206      2306           4          22      1         NA         NA   <NA>
5  3 1304095127 1304095146      2366          NA          NA     NA         34         22      C
6  3 1304095276 1304095320      2192           5          28      1         NA         NA   <NA>
```

#### Using join from plyr package

``` R
arrange(join(reviews, solutions), id)
```

> Documentation for [arrange](http://www.inside-r.org/packages/cran/plyr/docs/arrange) and  [join](http://www.inside-r.org/packages/cran/plyr/docs/join)

> And if you want to mrege columns by different names using plyr, look at [stackoverflow question](http://stackoverflow.com/questions/24296375/how-can-i-use-join-on-columns-with-different-names).

#### Merging multiple data frames

Merging data frames with the same ID column name

``` R
df1 = data.frame(id=sample(1:10), x=rnorm(10))
df2 = data.frame(id=sample(1:10), x=rnorm(10))
df3 = data.frame(id=sample(1:10), x=rnorm(10))

dfs = list(df1, df2, df3)

join_all(dfs)
```
