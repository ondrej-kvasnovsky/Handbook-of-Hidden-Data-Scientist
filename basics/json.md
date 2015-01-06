# JSON

Load library.

``` R
library(jsonlite)
```

``` R
url <- "https://api.github.com/users/ondrej-kvasnovsky/repos"

json <- fromJSON(url)
```

Iterating through JSON document.

``` R
names(json)
names(json$owner)

json$owner$login
```

toJSON

``` R
prettyJson <-toJSON(json, pretty=TRUE)

cat(prettyJson)
```

fromJSON

``` R
prettyJson <-toJSON(json, pretty=TRUE)
json <- fromJSON(prettyJson)

head(json)
```
