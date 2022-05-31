---

copyright:
  years: 2015, 2022
lastupdated: "2022-05-31"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}

# Customize the JRE
{: #customizing_jre}

{{site.data.keyword.ibmcf_full}} is deprecated. As of 30 November 2022 new {{site.data.keyword.ibmcf_full}} applications cannot be created and only existing users will be able to deploy applications. End-of-support happens on 1 June 2023. Any instances that still exist on 1 June 2023 will be deleted. For more information, see [the deprecation details](/docs/cloud-foundry-public?topic=cloud-foundry-public-deprecation).
{: deprecated}

Apps run in a Java runtime environment (JRE) that is provided and configured by the Liberty buildpack. The Liberty buildpack also makes it possible to configure the JRE version or type, customize the JVM options, or overlay the JRE functions.

## {{site.data.keyword.IBM_notm}} JRE

By default, apps are configured to run with a lightweight version of the {{site.data.keyword.IBM}} JRE. This lightweight JRE is stripped down to provide core, essential function with a much reduced disk and memory footprint. For more information about the contents of the lightweight JRE, see [Small Footprint JRE](http://www.ibm.com/support/knowledgecenter/SSYKE2_8.0.0/com.ibm.java.lnx.80.doc/user/small_jre.html){: external}.

{{site.data.keyword.IBM_notm}} JRE version 8 is used by default.  The Liberty buildpack also includes the latest OpenJ9 11 JRE as an alternate JRE.  
Use the JBP_CONFIG_IBMJDK environment variable to specify an alternative JRE. For example, to use the latest OpenJ9 JRE provided by the Liberty buildpack set the following environment variable:

```text
ibmcloud cf set-env myapp JBP_CONFIG_IBMJDK "version: 11.+"
```
{: pre}

The version property can be set to a version range. There are two supported version ranges: 1.8.+ and 11.+. For best results, use Java 8.

## OpenJDK
{: #openjdk}

Optionally, apps can be configured to run with OpenJDK as the JRE. To enable an app to run with OpenJDK set the JVM environment variable to `openjdk`. For example, using the {{site.data.keyword.cloud_notm}} command line tool, run the command:

```text
ibmcloud cf set-env myapp JVM 'openjdk'
```
{: pre}

If enabled, OpenJDK version 8 is used by default. Use the JBP_CONFIG_OPENJDK environment variable to specify an alternative version of OpenJDK. For example, to use the latest OpenJDK 7, set the following environment variable:

```text
ibmcloud cf set-env myapp JBP_CONFIG_OPENJDK "version: 1.7.+"
```
{: pre}

The version property can be set to a version range such as 1.7.+, 1.8.+ or any specific version listed on the [list of available OpenJDK versions](https://download.run.pivotal.io/openjdk/lucid/x86_64/index.yml){: external}. For best results, use Java 8.

## OpenJ9
{: #openj9}

Optionally, apps can be configured to run with OpenJ9 as the JRE or JDK. To enable an app to run with OpenJ9 set the JVM environment variable to "openj9". For example, using the {{site.data.keyword.cloud_notm}} command line tool, run the command:

```text
ibmcloud cf set-env myapp JVM 'openj9'
```
{: pre}

If enabled, OpenJ9 version 11 is used by default. Use the JBP_CONFIG_OPENJ9 environment variable to specify an alternative version of OpenJ9. For example, to use the latest OpenJ9 8, set the following environment variable:

```text
ibmcloud cf set-env myapp JBP_CONFIG_OPENJ9 "version: 8.+"
```
{: pre}

If enabled, the OpenJ9 JRE is used by default. Use the JBP_CONFIG_OPENJ9 environment variable to use the JDK version of OpenJ9. For example, to use the OpenJ9 JDK, set the following environment variable:

```text
ibmcloud cf set-env myapp JBP_CONFIG_OPENJ9 "type: jdk"
```
{: pre}

## Oracle JRE
{: #oracle_jre}

See [Using your own JRE](/docs/cloud-foundry-public?topic=cloud-foundry-public-using_own_jre) for information on using the Oracle JRE.

## Configuring the JRE options
{: #configuring_jre}

### JVM default configuration
{: #jvm_default_config}

The Liberty buildpack configures the default JVM options by taking into account:

* An app's memory limit.  The applied JVM heap settings are calculated based on:
    * an app's memory limit, as explained in [Memory limits and the Liberty buildpack](/docs/cloud-foundry-public?topic=cloud-foundry-public-memory_limits)
    * the JRE type, as the heap-related options for the JVM vary according to the JRE's supported options.

* The [Liberty features supported in {{site.data.keyword.cloud_notm}}](/docs/cloud-foundry-public?topic=cloud-foundry-public-liberty_features).
    * Two-phase commit global database transactions are unsupported in {{site.data.keyword.cloud_notm}} and therefore disabled by setting `-Dcom.ibm.tx.jta.disable2PC=true`.

* The {{site.data.keyword.cloud_notm}} environment.

    The JVM options are configured to provide optimization in an {{site.data.keyword.cloud_notm}} environment and to aide diagnostics of memory-related error conditions.
    * Fast failure and recovery of an app is configured by disabling JVM dumps options and killing of the processes when an app's memory is exhausted.
    * Virtualization tuning ({{site.data.keyword.IBM_notm}} JRE only).
    * Routing of information on the app's available memory resources at the time of failure to the Loggregator.
    * If an app is configured to enable JVM memory dumps, the killing of Java processes is disabled, and JVM memory dumps are routed to a common app "dumps" directory. These dumps can then be viewed from the {{site.data.keyword.cloud_notm}} dashboard or the {{site.data.keyword.cloud_notm}} CLI.

The following is an example default JVM configuration that is generated by the buildpack for an app that is deployed with a 512M Memory Limit:

```text
    -Xtune:virtualized
    -Xmx384M
    -Xdump:none
    -Xdump:heap:defaults:file=../../../../../dumps/heapdump.%Y%m%d.%H%M%S.%pid.%seq.phd
    -Xdump:java:defaults:file=../../../../../dumps/javacore.%Y%m%d.%H%M%S.%pid.%seq.txt
    -Xdump:snap:defaults:file=../../../../../dumps/Snap.%Y%m%d.%H%M%S.%pid.%seq.trc
    -Xdump:tool:events=systhrow,filter=java/lang/OutOfMemoryError,request=serial+exclusive,exec=../../../../.buildpack-diagnostics/killjava.sh
    -Dcom.ibm.tx.jta.disable2PC=true
```
{: codeblock}

### Customizing the JVM configuration
{: #customizing_jvm}

Apps can customize the JVM options with the specifications that are defined by the JRE configured for the app. Reference the guidelines on how to specify an option and its usage directly from the JRE's documentation, as the options vary according to the JRE.

| JRE | Command Line Options Format | Reference |
|-----|-----------------------------|-----------|
|{{site.data.keyword.IBM_notm}} JRE | includes runtime options (prefixed by -X), any Java system properties (prefixed with -D), and does not recommend -XX for the casual usage (these options are subject to change) | [Version 8 command-line options](https://www.ibm.com/support/knowledgecenter/SSYKE2_8.0.0/openj9/cmdline_specifying/index.html){: external}, [Version 7 command-line options](https://www.ibm.com/support/knowledgecenter/SSYKE2_7.0.0/com.ibm.java.lnx.70.doc/diag/appendixes/cmdline/cmdline.html){: external} |
| OpenJDK | is based on the HotSpot runtime that has the notation of -X for non-standard, -XX for developer options, and Boolean values to enable or disable the option | [HotSpot Runtime Overview](http://openjdk.java.net/groups/hotspot//docs/RuntimeOverview.html){: external} | 

An app that requires customized JVM options can set the option as a value for one of the environment variables `IBM_JAVA_OPTIONS`, `JAVA_OPTS`, or `JVM_ARGS` in {{site.data.keyword.cloud_notm}}. Refer to the Environment Variables section on how to set an app's environment variable. A packaged server or a server directory can also include a `jvm.options` file that contains the command line options instead of setting an environment variable.

When the JVM options are applied to the JRE, the Liberty buildpack's default options are applied first, followed by the customized options. The customized options are appended in a specific order, which is listed in the table. The sequence of the applied Java options defines which options take precedence. Options that are applied last have precedence over options that were previously applied.

Note: Some options might not go into effect unless the option is triggered by an agent.

| Applied order | App JVM options setting | Description | Supported app type | To update the JVM option of a deployed app | Applicable to OpenJDK JRE |
|---------------|-------------------------|-------------|--------------------|-----------------------------|---------------------------|
| 1 | `IBM_JAVA_OPTIONS` | an environment variable that is supported by the {{site.data.keyword.IBM_notm}} JRE | All | Restart or restage the app | No | 
| 2 | `JAVA_OPTS` | an environment variable through the Liberty buildpack Java Options framework | All | Restage the app | Yes |
| 3 | `jvm.options` | a JVM configuration file that is supported by the Liberty runtime packaged server or server directory | Server package | Restage the app | Yes | 
| 4 | `JVM_ARGS` | an environment variable that is supported by the Liberty runtime | All | Restart or restage the app | Yes |

### Determining the applied JVM options of a running app
{: #determining_applied_jvm_options}

Except for app-defined options that are specified with the `JVM_ARGS` environment variable, the resulting options are persisted in the runtime environment either as command line options (stand-alone Java apps) or in a `jvm.options` file (non-stand-alone Java apps). The applied JVM options for the app can be viewed either from the {{site.data.keyword.cloud_notm}} console or the {{site.data.keyword.cloud_notm}} CLI.

The JVM options for stand-alone Java app are persisted as command line options. They can be viewed from the `staging_info.yml` file.

To view the `staging_info.yml` file, run:

```text
ibmcloud cf ssh myapp -c "cat staging_info.yml"
```
{: pre}

The JVM options for WAR, EAR, server directory and packaged server deployment are persisted in a `jvm.options` file. The `jvm.options` file can be found in the `app/wlp/usr/servers/<serverName>/` directory. In the most cases the `<serverName>` is set to `defaultServer` unless a packaged server was deployed with a different server name. For example:

To view the `jvm.options` file, run:

```text
ibmcloud cf ssh myapp -c "cat app/wlp/usr/servers/defaultServer/jvm.options"
```
{: pre}


#### Example usage
{: #example_usage}

Deploying an app with customized JVM options to enable {{site.data.keyword.IBM_notm}} JRE verbose garbage collection logging:
* The JVM options included in an app's `manifest.yml` file:

    ```yaml
        env:
          JAVA_OPTS: "-verbose:gc -Xverbosegclog:./verbosegc.log,10,1000"
    ```
    {: codeblock}

* To view the JVM generated verbose garbage collection log file, run:

    ```text
    ibmcloud cf ssh myapp -c "cat app/wlp/usr/servers/defaultServer/verbosegc.log.001"
    ```
    {: pre}

* To update a deployed app's {{site.data.keyword.IBM_notm}} JRE option to trigger a `heap`, `snap`, and `javacore` on an out-of-memory condition, set the app's environment variable with the JVM option and restart the app:

    ```text
    ibmcloud cf set-env myapp JVM_ARGS '-Xdump:heap+java+snap:events=systhrow,filter=java/lang/OutOfMemoryError'
    ```
    {: pre}

    ```text
    ibmcloud cf restart myapp
    ```
    {: pre}

 See the [Logging and tracing](/docs/cloud-foundry-public?topic=cloud-foundry-public-logging_tracing#download_dumps) documentation for details on viewing and downloading the generated dump files.

### Overlaying the JRE
{: #overlaying_jre}

There are some cases where files need to be bundled with the JRE to expose their functions. The app developer can supply JRE files for customization.

The files to be overlaid can be packaged with the app `WAR`, `EAR`, or `JAR` file in a resources folder at the root of the archive. For a server (compressed file or server directory), the files can be packaged in a resources folder in the server directory, with the `server.xml` file.

* `WAR` file
    * `WEB-INF`
    * `resources`
        * `other files`
        * `.java-overlay`


* `EAR` file
    * `META-INF`
    * `resources`
        * `other files`
        * `.java-overlay`


* `JAR` file
    * `META-INF`
    * `resources`
        * `other files`
        * `.java-overlay`


* <server_name> DIR
    * `apps`
    * `dropins`
    * `server.xml`
    * `resources`
        * `other files`
        * `.java-overlay`

The `.java-overlay` directory contains specific files in the same file hierarchy as the Java JRE that is being overlaid starting with `.java/jre`.

For example, if you want to use AES 256-bit encryption, you need to overlay these Java policy files:

```text
    .java\jre\lib\security\US_export_policy.jar
    .java\jre\lib\security\local_policy.jar
```
{: codeblock}

Download the appropriate unrestricted policy files and add them to your app as:

```text
    resources\.java-overlay\.java\jre\lib\security\US_export_policy.jar
    resources\.java-overlay\.java\jre\lib\security\local_policy.jar
```
{: codeblock}

When you push your app, these jars overlay the default policy jars in the Java runtime. This process enables AES 256-bit encryption.


