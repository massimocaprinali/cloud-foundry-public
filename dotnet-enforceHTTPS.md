---

copyright:
  years: 2015, 2021
lastupdated: "2021-11-05"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}

# Enforce HTTPS on all pages in your app
{: #dotnet-enforce_https}

To enforce HTTPS instead of HTTP on all pages in your app when it runs in {{site.data.keyword.cloud}}, you need to make the following changes to your app.

Add the following `using` statements in the `Startup` class:

```text
  using Microsoft.AspNetCore.Mvc;
  using Microsoft.AspNetCore.Rewrite;
```
{: codeblock}

Add the following to the `ConfigureServices` method in the `Startup` class:

```text
  // if app is running in {{site.data.keyword.cloud_notm}}
  if (!string.IsNullOrEmpty(Environment.GetEnvironmentVariable("BLUEMIX_REGION")))
  {
    services.Configure<MvcOptions>(options =>
    {
      options.Filters.Add(new RequireHttpsAttribute());
    });
  }
```
{: codeblock}

Add the following to your `Configure` method in the `Startup` class:

```text
  // if app is running in {{site.data.keyword.cloud_notm}}
  if (!string.IsNullOrEmpty(Environment.GetEnvironmentVariable("BLUEMIX_REGION")))
  {
    app.Use(async (context, next) =>
      {
        if (string.Equals(context.Request.Headers["X-Forwarded-Proto"], "https", StringComparison.OrdinalIgnoreCase))
        {
          context.Request.Scheme = "https";
        }

        await next();
      });
    var options = new RewriteOptions()
                .AddRedirectToHttps();

    app.UseRewriter(options);
  }
```
{: codeblock}


