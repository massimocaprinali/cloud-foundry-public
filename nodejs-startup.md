---

copyright:
  years: 2015, 2021
lastupdated: "2021-11-05"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}

# Use the startup command
{: #startup_commmand}

The recommended ways to specify a start command for your {{site.data.keyword.cloud}} Node.js app are to use either a `Procfile` or a `package.json` file.
{: shortdesc}

1. Specify a startup command in your `Procfile` in the form that follows. Here, _app.js_ is the startup js script for your app.

    ```text
    web: node app.js
    ```
    {: codeblock}

2. Save the `Procfile` in the root directory of your app.

If a `Procfile` is not present, the {{site.data.keyword.cloud_notm}} Node.js buildpack checks for a scripts.start entry in the `package.json` file. Again in the example below, app.js is the startup js script for your app.

```json
{
    ...   
    "scripts": {
      "start": "node app.js"
    }
}
```
{: codeblock}

If a start script entry is present in the `package.json`, a `Procfile` is generated automatically. The content of the auto-generated `Procfile` is:

```text
    web: npm start
```
{: codeblock}

For more information on the `Procfile` and `package.json` file see [Tips for Node.js Apps](https://docs.cloudfoundry.org/buildpacks/node/node-tips.html){: external}.


