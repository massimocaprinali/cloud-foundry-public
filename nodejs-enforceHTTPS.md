---

copyright:
  years: 2015, 2022
lastupdated: "2022-03-08"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}

# Enforce HTTPS on all pages in your app
{: #nodejs-enforce_https}

When you run your app in {{site.data.keyword.cloud}} with the express framework, the following changes need to be made to enforce HTTPS instead of HTTP on all pages in your app.

```text
var express = require("express");
var app = express();

app.enable('trust proxy');

app.use (function (req, res, next) {
  if (req.secure || process.env.BLUEMIX_REGION === undefined) {
    next();
  } else {
    console.log('redirecting to https');
    res.redirect('https://' + req.headers.host + req.url);
  }
});
```
{: codeblock}


