# MySql

We will use [RMySQL](http://cran.r-project.org/web/packages/RMySQL/index.html) package to connect to database.

#### Install you own database

Install via brew

```
brew install mysql
```

Or do it manually:

Download MySql

* http://dev.mysql.com/downloads/mysql/

Install MySql

* http://dev.mysql.com/doc/refman/5.7/en/installing.html

#### Use existing MySql

We can connect to [MySql database](https://genome.ucsc.edu/goldenPath/help/mysql.html).

```
mysql --user=genome --host=genome-mysql.cse.ucsc.edu -A
```

#### Install package for Mac OSX

``` R
Sys.setenv(PKG_CPPFLAGS = "-I/usr/local/include/mysql")
Sys.setenv(PKG_LIBS = "-L/usr/local/lib -lmysqlclient")

install.packages("RMySQL")

library(RMySQL)
```

> When installation of RMySQL package fails, have a look here: [adding-rmysql-package-to-r-fails](http://stackoverflow.com/questions/4785933/adding-rmysql-package-to-r-fails) or [installing-rmysql-in-mavericks](http://stackoverflow.com/questions/24537257/installing-rmysql-in-mavericks)

#### Connect

``` R
db <- dbConnect(
    MySQL(),
    user="genome",
    db="hg19",
    host="genome-mysql.cse.ucsc.edu"
)
```

#### Query

``` R
allDatabases <- dbGetQuery(db, "show databases;")

allTables <- dbListTables(db)
length(allTables)

allFields <- dbListFields(db, "wgEncodeUwDgfHmvecfSig")

queryResult <- dbGetQuery(db, "SELECT COUNT(1) FROM wgEncodeUwDgfHmvecfSig")

dbDisconnect(db)
```

#### Read from table

``` R
result <- dbReadTable(db, "wgEncodeUwDgfHmvecfSig")

dbDisconnect(db)
```

### Lazy loading

When there is too much valuse in a table, so almost always, fetch only little data into memory.

``` R
query <- dbSendQuery(db, "SELECT * FROM affyU133Plus2")

result <- fetch(query, n=10)

dbClearResult(query)

dbDisconnect(db)
```
