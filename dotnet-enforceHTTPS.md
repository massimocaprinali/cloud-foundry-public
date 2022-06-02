---

copyright:
  years: 2015, 2022
lastupdated: "2022-05-31"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}

# Enforce HTTPS on all pages in your app
{: #dotnet-enforce_https}

{{site.data.keyword.ibmcf_full}} is deprecated. As of 30 November 2022 new {{site.data.keyword.ibmcf_full}} applications cannot be created and only existing users will be able to deploy applications. End-of-support happens on 1 June 2023. Any instances that still exist on 1 June 2023 will be deleted. For more information, see [the deprecation details](/docs/cloud-foundry-public?topic=cloud-foundry-public-deprecation).
{: deprecated}

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


