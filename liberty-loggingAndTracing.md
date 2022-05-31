---

copyright:
  years: 2015, 2022
lastupdated: "2022-05-31"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}

# Configure logging and tracing
{: #logging_tracing}

## Log files
{: #log_files}

{{site.data.keyword.ibmcf_full}} is deprecated. As of 30 November 2022 new {{site.data.keyword.ibmcf_full}} applications cannot be created and only existing users will be able to deploy applications. End-of-support happens on 1 June 2023. Any instances that still exist on 1 June 2023 will be deleted. For more information, see [the deprecation details](/docs/cloud-foundry-public?topic=cloud-foundry-public-deprecation).
{: deprecated}

The standard Liberty logs, such as `messages.log` or the `ffdc` directory, are available in {{site.data.keyword.cloud}} in the `logs` directory of each app instance. These logs can be accessed from the {{site.data.keyword.cloud_notm}} console or via the {{site.data.keyword.cloud_notm}} CLI. For example:

* To access recent logs for an app, run the following command:

    ```text
    ibmcloud cf logs --recent <appname>
    ```
    {: pre}


* To see the `messages.log` file of an app, run the following command:

    ```text
    ibmcloud cf ssh <appname> -c "cat logs/messages.log"
    ```
    {: pre}

The log level and other trace options can be set through the Liberty configuration file. For more information, see [Troubleshooting Liberty: Logging and Trace](http://www.ibm.com/support/knowledgecenter/SSEQTP_liberty/com.ibm.websphere.wlp.doc/ae/rwlp_logging.html){: external}.

## Using the trace and dump capabilities
{: #using_trace_and_dump}

### Using trace and dump in {{site.data.keyword.cloud_notm}} console (Deprecated)

The Liberty tracing configuration can be adjusted for a running app directly from the {{site.data.keyword.cloud_notm}} console. The console also provides capability for requesting and downloading thread and heap dumps. In order to adjust the tracing configuration or request a dump, select a Liberty app in the {{site.data.keyword.cloud_notm}} console and choose the `Runtime` menu in the navigation. In the `Runtime` view, select an instance and press the *TRACE* or *DUMP* button. If adjusting the trace level, see [Troubleshooting Liberty: Logging and Trace](http://www.ibm.com/support/knowledgecenter/SSEQTP_liberty/com.ibm.websphere.wlp.doc/ae/rwlp_logging.html){: external} for the details of the syntax of the trace specification.

### Changing trace configuration via SSH

When you push the app, the `server.xml` file includes the default properties  `updateTrigger` set to `polled` and `monitorInterval` set to 1 minute. The Liberty server is automatically configured to check for updates to the `server.xml` file each minute.

See [Push Liberty apps with `server.xml`](/docs/cloud-foundry-public?topic=cloud-foundry-public-options_for_pushing#options_for_pushing) for options to push Liberty apps with a customized `server.xml` file.

See [Controlling Dynamic Updates](https://www.ibm.com/support/knowledgecenter/SSEQTP_liberty/com.ibm.websphere.wlp.doc/ae/twlp_setup_dyn_upd.html){: external} for how to set up dynamic updates in the `server.xml` file.

Follow these steps to change tracing configuration:

1. SSH to your app

    ```text
    ibmcloud cf ssh <appname> [-i instance_index]
    ```
    {: pre}

2. Edit `<logging traceSpecification="xxxx"/>` in the `server.xml` file to set your trace specification;  for example, using *vi*:

    ```text
    vi /app/wlp/usr/servers/defaultServer/server.xml
    ```
    {: pre}

Note: The `server.xml` file change will be lost on a restage or restart and is only valid for the SSH instance.

See [Troubleshooting Liberty: Logging and Trace](http://www.ibm.com/support/knowledgecenter/SSEQTP_liberty/com.ibm.websphere.wlp.doc/ae/rwlp_logging.html){: external} for the details of the syntax of the trace specification.

### Triggering dumps via SSH

Use the command below to trigger a thread and heap dump via {{site.data.keyword.cloud_notm}} CLI using the SSH feature:

```text
ibmcloud cf ssh <appname> -c "pkill -3 java"
```
{: pre}

See the documentation below for details on downloading the generated dump files.

## Download dump files
{: #download_dumps}

By default, the various dump files are placed in the `dumps` directory of the app container. Use {{site.data.keyword.cloud_notm}} CLI `ibmcloud cf ssh` to view and download the dump files.

* To see the generated dumps, run the following command:

    ```text
    ibmcloud cf ssh <appname> -c "ls -l dumps"
    ```
    {: pre}

* To download a dump file, run the following command:

    ```text
    ibmcloud cf ssh <appname> -i <instance_id> -c "cat dumps/<dump_file_name>" > <local_dump_file_name>
    ```
    {: pre}

It is also possible to use `scp` and other similar tools to view and download the dump files. Refer to [Accessing Apps with SSH](https://docs.cloudfoundry.org/devguide/deploy-apps/ssh-apps.html){: external} for more information.


