---

copyright:
  years: 2015, 2022
lastupdated: "2022-05-11"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}

# Configuration options
{: #configuration_options}

A variety of options are available for configuring the
`sdk-for-nodejs` buildpack.
{: shortdesc}


## NPM scripts
{: #npm_scripts}

NPM provides a scripting facility allowing you to run scripts, including pre-installation and post-installation scripts which are applied before and after your node_modules are installed.  See [npm-scripts](https://docs.npmjs.com/misc/scripts){: external} for complete details.

## Cache behavior
{: #cache_behavior}

{{site.data.keyword.cloud}} maintains a cache directory per node app, that is persisted between builds. The cache stores resolved dependencies so they are not downloaded and installed every time the app is deployed.  For example, suppose `myapp` depends on **express**.  Then the first time `myapp` is deployed the **express** module is downloaded.  On subsequent deployments of `myapp`,  the cached instance of **express** is used. The default behavior is to cache all node_modules installed by NPM and bower_components installed by bower.

Use the NODE_MODULES_CACHE variable to determine whether or not the Node buildpack uses or ignores the cache from previous builds. The default value is true.  To disable caching set NODE_MODULES_CACHE to false, for example via the {{site.data.keyword.cloud_notm}} command line:

```text
ibmcloud cf set-env myapp NODE_MODULES_CACHE false
```
{: pre}

Note that node_modules that are included in your app are not cached.

You can use a `cacheDirectories` array in your top-level `package.json` file to achieve fine grained control over what modules are cached.  When the `cacheDirectories` element is present in the `package.json` file only those modules which are in the `cacheDirectories` array will be cached.  In the following example only `node_modules` and `bower_components` are cached.

```text
{
  "cacheDirectories": ["node_modules","bower_components"],
  ...
}
```
{: codeblock}


