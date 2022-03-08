---

copyright:
  years: 2015, 2022
lastupdated: "2022-03-08"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}

# Use your own JRE
{: #using_own_jre}

You can run your Liberty app on {{site.data.keyword.cloud}} with your own JRE. The liberty-for-java buildpack will provide support for the [runtimes supported by WebSphere Liberty](https://www.ibm.com/support/knowledgecenter/en/SSEQTP_liberty/com.ibm.websphere.wlp.doc/ae/rwlp_restrict.html#rwlp_restrict__rest13){: external}, but cannot guarantee full functionality of unsupported versions. You must complete the following to make your JRE available for your app.
* Host the JRE in a location that the buildpack can download it from.
* Host an `index.yml` file that provides the location of the JRE.
* Configure your app to use your JRE.

## Host the JRE and `index.yml`
{: #hosting_jre}

You must host the JRE file on a web server that the liberty-for-java buildpack can download from. You can host the file on {{site.data.keyword.cloud_notm}} with any of the available server facilities, or you can host it in a publicly available location. The server must be configured with an `index.yml` file that specifies details about the JRE file.

Complete the following steps to host the JRE and the `index.yml` file:

1. Acquire the JRE, which must be the version for use on a UNIX 64-bit OS, and must be a `tar.gz` file.
2. Host the JRE file in a location from which the liberty-for-java buildpack can download it.
3. Provide an `index.yml` file at the hosting location. The `index.yml` file must include an entry that contains a version ID of the JRE followed by a colon and the complete JRE file location URL.

    * Define the JRE version in the `index.yml` file.

        ```text
        ---
        jre_version: https://hostingLocation/jreName.tar.gz
        ```
        {: codeblock}

    * Include the JRE version ID and the complete JRE file location.  For example:

        ```text
        ---
        1.8.0_91: https://myHostingApp.ng.bluemix.net/jre-8u91-fcs-bin-b14-linux-x64-01_apr_2016.tar.gz
        ```
        {: codeblock}

## Configure the app
{: #configure_app}

You must set two environment variables on the Liberty app to configure the buildpack to use an alternative JRE. Set the `JBP_CONFIG_OPENJDK` to identify the location of the `index.yml` file  and set the `JVM` environment variable to `openjdk`. For more information on the format for version-value strings, see the Cloud Foundry documentation on [Version Syntax and Ordering and Wildcards](https://github.com/cloudfoundry/ibm-websphere-liberty-buildpack/blob/master/docs/util-repositories.md){: external}.

The value for the `JBP_CONFIG_OPENJDK` variable is the `index.yml` file location and the JRE version to choose from the index.yml file.

```text
'{repository_root: "https://locationToIndexYml", version: version-value}'
```
{: codeblock}

Issue the `ibmcloud cf se myAPP` command to set the `JBP_CONFIG_OPENJDK` variable, for example:

```text
ibmcloud cf se myApp JBP_CONFIG_OPENJDK '{repository_root: "https://myHostingApp.ng.bluemix.net", version: 1.8.+}'
```
{: pre}

The *repository_root* URL does not include `index.yml` in the URL. The *repository_root* URL points to the directory level that contains the `index.yml` file, not the file itself.

To set the JVM environment variable, issue the following command:

```text
ibmcloud cf se myApp JVM 'openjdk'
```
{: pre}

**Note**: Restage your app after setting the environment variables for the changes to take effect.

## Confirm
{: #confirmation}

To confirm that Liberty is using the expected JRE, check the staging log. Look for a message that indicates the server downloaded the buildpack from the location indicated in the `index.yml` file. See the following snippet for an example of the log output when Liberty successfully uses the expected JRE.

```text
-----> Downloading OpenJdk 1.8.0_91 from
 https://myHostingApp.ng.bluemix.net/jre-8u91-fcs-bin-b14-linux-x64-01_apr_2016.tar.gz (6.2s)
```
{: screen}


