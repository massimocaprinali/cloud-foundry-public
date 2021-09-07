---

copyright:
  years: 2015, 2021
lastupdated: "2021-09-07"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:android: data-hd-operatingsystem="android"}
{:api: .ph data-hd-interface='api'}
{:apikey: data-credential-placeholder='apikey'}
{:app_key: data-hd-keyref="app_key"}
{:app_name: data-hd-keyref="app_name"}
{:app_secret: data-hd-keyref="app_secret"}
{:app_url: data-hd-keyref="app_url"}
{:audio: .audio}
{:authenticated-content: .authenticated-content}
{:beta: .beta}
{:c#: .ph data-hd-programlang='c#'}
{:c#: data-hd-programlang="c#"}
{:cli: .ph data-hd-interface='cli'}
{:codeblock: .codeblock}
{:curl: #curl .ph data-hd-programlang='curl'}
{:curl: .ph data-hd-programlang='curl'}
{:deprecated: .deprecated}
{:dotnet-standard: .ph data-hd-programlang='dotnet-standard'}
{:download: .download}
{:external: .external target="_blank"}
{:external: target="_blank" .external}
{:faq: data-hd-content-type='faq'}
{:fuzzybunny: .ph data-hd-programlang='fuzzybunny'}
{:generic: data-hd-operatingsystem="generic"}
{:generic: data-hd-programlang="generic"}
{:gif: data-image-type='gif'}
{:go: .ph data-hd-programlang='go'}
{:help: data-hd-content-type='help'}
{:hide-dashboard: .hide-dashboard}
{:hide-in-docs: .hide-in-docs}
{:important: .important}
{:ios: data-hd-operatingsystem="ios"}
{:java: #java .ph data-hd-programlang='java'}
{:java: .ph data-hd-programlang='java'}
{:java: data-hd-programlang="java"}
{:javascript: .ph data-hd-programlang='javascript'}
{:javascript: data-hd-programlang="javascript"}
{:middle: .ph data-hd-position='middle'}
{:navgroup: .navgroup}
{:new_window: target="_blank"}
{:node: .ph data-hd-programlang='node'}
{:note: .note}
{:objectc: .ph data-hd-programlang='Objective C'}
{:objectc: data-hd-programlang="objectc"}
{:org_name: data-hd-keyref="org_name"}
{:php: .ph data-hd-programlang='PHP'}
{:php: data-hd-programlang="php"}
{:pre: .pre}
{:preview: .preview}
{:python: .ph data-hd-programlang='python'}
{:python: data-hd-programlang="python"}
{:release-note: data-hd-content-type='release-note'}
{:right: .ph data-hd-position='right'}
{:route: data-hd-keyref="route"}
{:row-headers: .row-headers}
{:ruby: .ph data-hd-programlang='ruby'}
{:ruby: data-hd-programlang="ruby"}
{:runtime: architecture="runtime"}
{:runtimeIcon: .runtimeIcon}
{:runtimeIconList: .runtimeIconList}
{:runtimeLink: .runtimeLink}
{:runtimeTitle: .runtimeTitle}
{:screen: .screen}
{:script: data-hd-video='script'}
{:service: architecture="service"}
{:service_instance_name: data-hd-keyref="service_instance_name"}
{:service_name: data-hd-keyref="service_name"}
{:shortdesc: .shortdesc}
{:space_name: data-hd-keyref="space_name"}
{:step: data-tutorial-type='step'}
{:step: data-tutorial-type='step'} 
{:subsection: outputclass="subsection"}
{:support: data-reuse='support'}
{:swift: #swift .ph data-hd-programlang='swift'}
{:swift: .ph data-hd-programlang='swift'}
{:swift: data-hd-programlang="swift"}
{:table: .aria-labeledby="caption"}
{:term: .term}
{:terraform: .ph data-hd-interface='terraform'}
{:tip: .tip}
{:tooling-url: data-tooling-url-placeholder='tooling-url'}
{:topicgroup: .topicgroup}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:tsSymptoms: .tsSymptoms}
{:tutorial: data-hd-content-type='tutorial'}
{:ui: .ph data-hd-interface='ui'}
{:unity: .ph data-hd-programlang='unity'}
{:url: data-credential-placeholder='url'}
{:user_ID: data-hd-keyref="user_ID"}
{:vbnet: .ph data-hd-programlang='vb.net'}
{:video: .video}


# Use JConsole to monitor Liberty in {{site.data.keyword.cloud_notm}}
{: #jconsole}

## Monitor the Liberty runtime with JConsole:
{: #steps_to_monitor}

1. Push your app within a server package that contains an appropriate `server.xml` file.
2. Start the JConsole app with the appropriate system properties on the command line.
3. Provide the proper `Remote Process URL`, `Username`, and `Password` to JConsole.

### Push the server package
{: #push_server_package}

Push the server package that contains your app to a single instance. Your `server.xml` file must contain the `monitor-1.0` and `restConnector-1.0` features. It must also contain a `basicRegistry` element and `administrator-role` element.
```
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
{: start_jconsole_app}

JConsole is included with your Java&trade; installation.  To start the JConsole app, go to `<java-home>/bin` and run the following command:
```
    jconsole -J-Djava.class.path=<java-home>/lib/jconsole.jar;<liberty-home>/wlp/clients/restConnector.jar
```
{: pre}

You might have to pass additional options to configure Java truststore. The following options will work in most cases:
```
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
```
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
```
    <logging traceSpecification="com.ibm.ws.jmx.*=all"/>
```
{: codeblock}




