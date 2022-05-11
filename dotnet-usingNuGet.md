---

copyright:
  years: 2015, 2022
lastupdated: "2022-05-11"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}

# Customize NuGet package sources
{: #customizing_nuget}

You can use the `NuGet.Config` file in the app's root directory to control where the app downloads dependencies. In the following example, configuring the `<packageSources>` property defines any keys and API URLs for the app to retrieve packages.

```text
   <?xml version="1.0" encoding="utf-8"?>
   <configuration>
   <packageSources>
      <add key="NuGet.org" value="https://api.nuget.org/v3/index.json"/>
   </packageSources>
   </configuration>
```
{: codeblock}


