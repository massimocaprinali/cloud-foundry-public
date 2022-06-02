---

copyright:
  years: 2015, 2022
lastupdated: "2022-05-31"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}

# Use JConsole to monitor Liberty in {{site.data.keyword.cloud_notm}}
{: #jconsole}

{{site.data.keyword.ibmcf_full}} is deprecated. As of 30 November 2022 new {{site.data.keyword.ibmcf_full}} applications cannot be created and only existing users will be able to deploy applications. End-of-support happens on 1 June 2023. Any instances that still exist on 1 June 2023 will be deleted. For more information, see [the deprecation details](/docs/cloud-foundry-public?topic=cloud-foundry-public-deprecation).
{: deprecated}

## Monitor the Liberty runtime with JConsole:
{: #steps_to_monitor}

1. Push your app within a server package that contains an appropriate `server.xml` file.
2. Start the JConsole app with the appropriate system properties on the command line.
3. Provide the proper `Remote Process URL`, `Username`, and `Password` to JConsole.

### Push the server package
{: #push_server_package}

Push the server package that contains your app to a single instance. Your `server.xml` file must contain the `monitor-1.0` and `restConnector-1.0` features. It must also contain a `basicRegistry` element and `administrator-role` element.

```text
       <featureManager>
           <feature>jsp-2.2</feature>
           <feature>monitor-1.0</feature>
           <feature>restConnector-1.0</feature>
       </featureManager>

       <basicRegistry>
           <user name="jconuser" password="jconpassw0rd"/>
       </basicRegistry>

       <administrator-role>
           <user>jconuser</user>
       </administrator-role>
```
{: codeblock}

Encode the password with the `securityUtility` tool provided by Liberty.
{: note}

### Start the JConsole app
{: #start_jconsole_app}

JConsole is included with your Java&trade; installation.  To start the JConsole app, go to `<java-home>/bin` and run the following command:

```text
    jconsole -J-Djava.class.path=<java-home>/lib/jconsole.jar;<liberty-home>/wlp/clients/restConnector.jar
```
{: pre}

You might have to pass additional options to configure Java truststore. The following options will work in most cases:

```text
    -J-Djavax.net.ssl.trustStore=<java-home>/jre/lib/security/cacerts -J-Djavax.net.ssl.trustStorePassword=changeit -J-Djavax.net.ssl.trustStoreType=jks
```
{: codeblock}

### Complete the connection
{: start_jconsole_app}

1. In the Remote Process field enter `service:jmx:rest://<appName>.mybluemix.net:443/IBMJMXConnectorREST`.
2. Specify the **Username** and **Password** fields.  Enter a user with an administrator-role, and a password from the `server.xml` file.
3. Click Connect.

When the connection succeeds, JConsole starts monitoring.

If the connection fails, you can produce logs to help diagnose the problem.  First, try collecting client-side tracing by adding `-J-Djava.util.logging.config.file=c:/tmp/logging.properties` to the `jconsole` command.

The following is a sample logging properties file:

```text
    handlers= java.util.logging.FileHandler
    .level=INFO java.util.logging.FileHandler.pattern = /tmp/jmxtrace.log
    java.util.logging.FileHandler.limit = 50000
    java.util.logging.FileHandler.count = 1
    java.util.logging.FileHandler.formatter = java.util.logging.SimpleFormatter
    javax.management.level=FINEST
    javax.management.remote.level=FINER
    com.ibm.level=FINEST
```
{: codeblock}

You can add `-J-Djavax.net.debug=ssl` to the `jconsole` command. The `-J-Djavax.net.debug=ssl` option produces SSL diagnostic tracing in a separate JConsole output window.  You can also enable tracing on the server side by adding the following to your `server.xml` file:

```text
    <logging traceSpecification="com.ibm.ws.jmx.*=all"/>
```
{: codeblock}


