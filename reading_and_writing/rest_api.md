# REST API

#### Setup OAuth application

Open https://apps.twitter.com and create new applicaiton. You will need security tokens in order to read from Twitter REST API.

#### Authentificate

First we have to authentificate. Copy paste consumer key, consumer secret, token and token secret from Twitter application you have created in previous step.

We will use [httr package](http://cran.r-project.org/web/packages/httr/index.html) to do OAuth authentification.

``` R
library(httr)

app = oauth_app(
    "twitter",
    key = "yourConsumerKey",
    secret="yourConsumerSecret"
)
sign = sign_oauth1.0(
    app,
    token = "yourToken",
    token_secret = "yourTokenSecret"
)

response = GET("https://api.twitter.com/1.1/statuses/home_timeline.json", sign)
```

Now we want to get the JSON value from the response. We will use [rjson package](http://cran.r-project.org/web/packages/rjson/rjson.pdf)  for that.

``` R
install.packages("rjson")
library(rjson)

json = content(response)

prettyJson = jsonlite::fromJSON(toJSON(json))
```

> Next step could to study [Twitter documentation](https://dev.twitter.com/overview/documentation) to find what is possible to get from there.
