# XML and Web pages

We will use [XML package](http://cran.r-project.org/web/packages/XML/index.html) to do the parsing.

#### Install package

``` R
install.packages("XML", dep = T)
library(XML)
```

#### Load XML tree

``` R
install.packages("XML")
library(XML)

url <- "http://www.w3schools.com/xml/simple.xml"

document <- xmlTreeParse(url, useInternal=TRUE)
```

Get element name

``` R
rootNode <- xmlRoot(document)
xmlName(rootNode)
```

Access first element.

``` R
rootNode[[1]]
```

Get element on exact position (going through subelements).

``` R
rootNode[[1]][[1]]
```

Using custom function to load values from XML. `xmlValue` is that function.

``` R
xmlSApply(rootNode, xmlValue)
```

Using XPath.

``` R
xpathSApply(rootNode, "//name", xmlValue)
```

#### Read a table from HTML

* [cran/XML/docs/readHTMLTable](http://www.inside-r.org/packages/cran/XML/docs/readHTMLTable)
* [grabbing-tables-in-webpages-using-the-xml-package](http://yihui.name/en/2010/10/grabbing-tables-in-webpages-using-the-xml-package/)

``` R
library(XML)

url <- "http://www.drugs.com/top200_2003.html"

html.table.data <- readHTMLTable(url, which = 2, skip.rows = 1)

View(html.table.data)
```

### Get page using httr package

``` R
library(httr)
library(XML)

url <- "http://www.drugs.com/top200_2003.html"

html = GET(url)
content = content(html, as="text")
parsedHtml = htmlParse(content, asText=TRUE)

xpathSApply(parsedHtml, "//title", xmlValue)
```

### Authentificate with httr package

We can use `authenticate` function in order to access a secured page.

``` R
library(httr)
library(XML)

url <- "http://httpbin.org/basic-auth/user/passwd"

GET(url, authenticate("user", "passwd"))
```

The code above returns the following response.

``` R
Response [http://httpbin.org/basic-auth/user/passwd]
  Date: 2014-12-30 16:30
  Status: 200
  Content-Type: application/json
  Size: 47 B
{
  "authenticated": true,
  "user": "user"
}
```

> Use `handle` function to access more page with during one authentificated session.
