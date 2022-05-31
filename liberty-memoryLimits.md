---

copyright:
  years: 2015, 2022
lastupdated: "2022-05-31"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}

# Memory limits and the Liberty buildpack
{: #memory_limits}

{{site.data.keyword.ibmcf_full}} is deprecated. As of 30 November 2022 new {{site.data.keyword.ibmcf_full}} applications cannot be created and only existing users will be able to deploy applications. End-of-support happens on 1 June 2023. Any instances that still exist on 1 June 2023 will be deleted. For more information, see [the deprecation details](/docs/cloud-foundry-public?topic=cloud-foundry-public-deprecation).
{: deprecated}

A memory limit must be specified when you deploy an app with the Liberty buildpack.

## Memory limits and the Liberty buildpack
{: #memory_limits_and_liberty}


When you deploy an app with the Liberty buildpack, you are prompted for a "Memory Limit". The Liberty for Java buildpack sets a default heap memory size ratio to prevent your process from exceeding the memory limit. You can also specify the heap memory size or ratio by defining the `JVM_ARGS` or `JBP_CONFIG_IBMJDK` environmental variables. See [Heap memory options](#heap_memory_options) to learn more.

To determine what Memory Limit to specify, it is important to understand that you are not specifying the size of the Java app heap. You are specifying the amount of memory available for the Diego container to use. This amount includes the memory that is used by the following components:

* by the warden container.
* to map kernel extensions and system libraries into the process.
* for the JVM executables, JVM working heap, JIT space, and compressed references.
* for classes (app server and app), thread stacks, and direct I/O buffers.
* by the Java app heap.

More information on JVM memory usage can be found at the developerWorks article [Thanks for the memory](http://www.ibm.com/developerworks/library/j-nativememory-linux/){: external}

When you deploy an app, the memory usage of the entire process is monitored. If memory usage exceeds the memory limit that you specified when the app was deployed, the kernel stops the process. This action happens without warning and might be manifested in several ways.

If the Memory Limit is exceeded during app deployment, you receive a message that a failure occurred and you might see any the following.

* You might see that the app is flapping.
* You might see that the app attempted to start multiple times, always unsuccessfully.
* You might receive a message that indicates the app deployment failed.

If the Memory Limit is exceeded while the app is in service, the process stops and Cloud Foundry attempts to restart the app. The app might restart, but it is unavailable for some amount of time.

## Heap memory options
{: #heap_memory_options}

You can customize the maximum amount of heap memory your app is allocated in various ways including by using the `JVM_ARGS` environment variable, changing the `jvm.options` file, or setting the `JBP_CONFIG_IBMJDK` environment variable which controls the `heap_size_ratio`. If you do not specify any settings, the buildpack uses the default settings.

### Heap memory defaults
{: #heap_memory_defaults}

To prevent errors that result from exceeding memory limits, the Liberty for Java buildpack sets a default heap size ratio depending on the memory limit that you specify when you deploy your app.

* Apps with memory limits of less than 512M have a heap size ratio of 50%
* Apps that have memory limits greater than or equal to 512M have a heap size ratio of 75%

When you specify the heap memory using environment variables, you override the default heap size ratios.

### Specifying Heap Memory
{: #specifying_heap_memory}

You can set the heap memory size by using environment variables or by changing the `jvm.options` file. When you use either the `JVM_ARGS` or `JBP_CONFIG_IBMJDK` environment variables, any changes will take effect when pushing your app to {{site.data.keyword.cloud_notm}}. By changing the `jvm.options` file, the effect to the heap size configuration can also be tested locally.

* Use the `JVM_ARGS` environment variable and the `-Xmx` argument. For example to set the maximum heap size to 512 M use the following command, then restage your app.

    ```text
    ibmcloud cf set-env myapp JVM_ARGS -Xmx512m
    ```
    {: codeblock}

* Specify the heap size ratio using the JBP_CONFIG_IBMJDK environment variable.  The heap_size_ratio is a floating point value which specifies how much of memory limit to allocate to the heap.  For example, to allocate half of the available memory to the heap (50% or 0.50), issue the following command and restage your app.

    ```text
    ibmcloud cf set-env myapp JBP_CONFIG_IBMJDK "heap_size_ratio: 0.50"
    ```
    {: codeblock}

* Specify the `-Xmx` argument in the `jvm.options` file if your app is a [server directory](/docs/cloud-foundry-public?topic=cloud-foundry-public-options_for_pushing#server_directory) or a [packaged server](/docs/cloud-foundry-public?topic=cloud-foundry-public-options_for_pushing#packaged_server). For more information about  using the `jvm.options` file with the Liberty runtime, see [Setting generic JVM](https://www.ibm.com/support/pages/node/476495){: external}.  


