---

copyright:
  years: 2015, 2022
lastupdated: "2022-06-02"

keywords: cloud foundry, deprecation, deprecated

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}

# {{site.data.keyword.ibmcf_notm}} migration tooling
{: #deprecation_migration_tooling}

{{site.data.keyword.ibmcf_full}} is deprecated. As of 30 November 2022 new {{site.data.keyword.ibmcf_full}} applications cannot be created and only existing users will be able to deploy applications. End-of-support happens on 1 June 2023. Any instances that still exist on 1 June 2023 will be deleted. For more information, see [the deprecation details](/docs/cloud-foundry-public?topic=cloud-foundry-public-deprecation).
{: deprecated}

While no specific migration tool exists to automatically migrate your {{site.data.keyword.ibmcf_full}} application to a new IBM Cloud compute service, there are certain projects that exist that move applications between Kubernetes container deployment computes.
{: shortdesc}

[Konveyor.io](http://Konveyor.io){: external} is an open source project that helps the adoption and transformation of application from many sources to various Kubernetes offerings.
Transformation support includes items like re-platforming (moving to a new platform) and re-factoring (improving the application to work more efficiently on the new platform). This is a potential method for you to continue the investigation of your {{site.data.keyword.ibmcf_full}} applications, and assist in your migration to Kubernetes-based IBM Cloud offerings such as {{site.data.keyword.codeenginefull_notm}}, {{site.data.keyword.containerlong_notm}}, or {{site.data.keyword.openshiftlong_notm}}.

[Move2Kube](https://move2kube.konveyor.io/){: external} is a sub-project within `Konveyor.io`, and is a command-line tool that accelerates the process of re-platforming to Kubernetes-based platforms. It does so by analyzing the environment and source artifacts, asking guidance from the user when required. You can customize the generation of the directory structure and artifacts in the format required for your project.

This tool can also be used to gather information about your {{site.data.keyword.ibmcf_full}} applications, even without migrating the applications. Use the  `move2kube collect -a cf` command to obtain information about your {{site.data.keyword.ibmcf_full}} applications, similar to the way described manually in [{{site.data.keyword.ibmcf_full}} application deployment analysis.](/docs/cloud-foundry-public?topic=cloud-foundry-public-deprecation_deploy_analysis)

The tool sill not work for all users, all apps, and all cases, but it is a starting point to help you in your migration planning. Even if you hand-migrate much of your application later, the tool can be a first pass to see how to migrate. This tool is more useful to move to a service with base Kubernetes capability.  A service such as {{site.data.keyword.codeenginefull_notm}} might not benefit as much since {{site.data.keyword.codeenginefull_notm}} does so many things automatically for you, unlike most direct-Kubernetes offerings.

This tool is an Open Source project.  No guarantees are made by either the Open Source project, `konveyor.io`, or IBM.

Investigate and evaluate the tool at [Konveyor.io](http://Konveyor.io){: external} and [Move2Kube](https://move2kube.konveyor.io/){: external}.  These resources include an overview of the tools and installation steps.

If you want to use a sample Cloud Foundry application to test this migration capability, the following is a sample app with instructions on how to deploy to {{site.data.keyword.ibmcf_full}}. You can then use the app to try `move2kube` steps.

## Sample Cloud Foundry Application
{: #cf_deptool1}

The sample application is called `enterprise-app`, and is located [here](https://github.com/konveyor/move2kube-demos/tree/main/samples/enterprise-app/src){: external}  There are also a [number of other Tutorials and Examples you can explore.](https://move2kube.konveyor.io/tutorials){: external}

The `Enterprise-App` consists of several microservices that work together to create a retail application that handles various customer transactions for the business. It is a non-trival application that shows how several components working together in an application can be migrated together.

Review the details of the application - including the components `Inventory`, `Orders`, `Customers`, `Gateway`, and `Frontend`:

* [Inventory](https://github.com/konveyor/move2kube-demos/tree/main/samples/enterprise-app/src/inventory){: external}
* [Orders](https://github.com/konveyor/move2kube-demos/tree/main/samples/enterprise-app/src/orders){: external}
* [Customers](https://github.com/konveyor/move2kube-demos/tree/main/samples/enterprise-app/src/customers){: external}
* [Gateway](https://github.com/konveyor/move2kube-demos/tree/main/samples/enterprise-app/src/gateway){: external}
* [Frontend](https://github.com/konveyor/move2kube-demos/tree/main/samples/enterprise-app/src/frontend){: external}

You don't have to deploy all components if you don't want to. `Inventory`, `Orders`, and `Customers` are underlying microservices. They are connected to by `Gateway` and `Frontend` connects to `Gateway`.  You can see the layout and connection information [here](https://github.com/konveyor/move2kube-demos/tree/main/samples/enterprise-app/src){: external}. If you have deployment problems, the components you are able to deploy can be used to analyze `move2kube`.


## Deploy the sample application
{: #cf_depsampapp}

Deploying a version of this application only takes a few steps. You will need standard development tools such as Git, Java, node.js, the ibmcloud CLI, the ability to log into the IBM Cloud, and so on.

The following are the minimum steps to make deploying the sample application easy.  You can reference the rest of details at the previous links as needed. Some steps are related to making your application unique in the multi-tenant {{site.data.keyword.ibmcf_full}} environment, creating a space to deploy it, and so on. These steps were tested on a MAC OSX machine. Slight command adjustments might be required depending on your development platform.

## Preparation
{: #cf_depsampprep}

Do the following before deploying the sample application.

1. [Authenticate to the IBM Cloud using the CLI](/docs/cli?topic=cli-ibmcloud_cli#ibmcloud_login).

   ```text
   ibmcloud login
   ```
   {: pre}

2. Connect to an IBM Cloud using use any region.

   ```text
   ibmcloud target --cf-api mccp.us-south.cf.cloud.ibm.com
   ```
   {: pre}

3. List the Orgs and Spaces you have.

   ```text
   ibmcloud cf orgs
   ibmcloud cf spaces
   ```
   {: pre}

4. Reuse a given space, or create a new one, for this sample application.

   ```text
   ibmcloud target -o <ORG TARGET>
   ibmcloud account space-create enterprise
   ```
   {: pre}

5. Set the target the proper Org and Space.

   ```text
   ibmcloud target -o <ORG> -s <SPACE>
   ```
   {: pre}

6. Log into IBM Cloud Container registry and create a namespace

   ```text
   ibmcloud cr login
   ibmcloud cr namespace-add myproject
   ```
   {: pre}


## Extract the sample application
{: #cf_dep_extract}

Create a folder structure for `move2kube` to deploy this application to {{site.data.keyword.ibmcf_full}} and migrate this application to your cluster. This structure will be explained in depth later.

Run the following commands to create this folder structure. Replace `<name_of_target>` with your target of choice (for example, `CE` for Code Engine, `ROKS` for Red Hat OpenShift on IBM Cloud, or `IKS` for IBM Kubernetes Service).

   ```shell
   mkdir move2kube-tutorial
   cd mkdir move2kube-tutorial
   git clone https://github.com/konveyor/move2kube-demos.git
   mkdir move2kube-demos-<name_of_target>
   cd move2kube-demos-<name_of_target>
   git clone https://github.com/konveyor/move2kube-demos.git
   cd ..
   ```
   {: pre}

Examine the `enterprise-app` source contents by running the following command:

   ```shell
   ls move2kube-demos/samples/enterprise-app/src
   ```
   {: pre}

## Run the Cloud Foundry installation script
{: #cf_run_install}

Once extracted, you can use the script in the directory to deploy the application to {{site.data.keyword.ibmcf_full}}.

1. Set extra time to stage and start the larger components.

   ```shell
   export CF_STAGING_TIMEOUT=30
   ```
   {: pre}


2. Create a shared variable for deploying the application with a unique application name. An example you can use your initials and some numbers for `<some_unique_string>`.

    ```shell
    export appname="enterprise-app-<some_unique_string>"
    ```
    {: pre}

3. Before running the deploy script, set the `CF_CLI_TOOL` variable to `'ibmcloud cf'`, so that it deploys the application to your {{site.data.keyword.ibmcf_notm}} service.
    
   ```shell
   cd move2kube-demos/samples/enterprise-app/src
   CF_CLI_TOOL='ibmcloud cf'
   ./deploy-to-cf.sh
   ```
   {: pre}

   The script will deploy the relevant application components and you will be able to test and access them by using the instructions located where the code was cloned from GitHub.

4. The names of the deployed applications can be found by running the following command:

   ```text
   ibmcloud cf apps
   ```
   {: pre}

   The following is a sample result from the command:

   ```text
   Invoking 'cf apps'...

   Getting apps in org MYORG / space MYSPACE as USER...
   OK

   name                                 requested state   instances   memory   disk   urls
   enterprise-app-eg220430297-frontend    started           1/1         2G       1G     enterprise-app-220430297.mybluemix.net
   enterprise-app-eg220430297-gateway     started           1/1         1G       1G     enterprise-app-220430297-gateway.mybluemix.net
   enterprise-app-eg220430297-customers   started           1/1         1G       1G     enterprise-app-220430297-customers.mybluemix.net
   enterprise-app-eg220430297-inventory   started           1/1         1G       1G     enterprise-app-220430297-inventory.mybluemix.net
   enterprise-app-eg220430297-orders      started           1/1         1G       1G     enterprise-app-220430297-orders.mybluemix.net
   ```
   {: screen}

## Testing the application
{: #cf_deptool_test}

You can connect to the various subcomponents to test that they are working properly.

1. Connect to each component using the following commands:

   ```shell
   curl http://$appname-inventory.mybluemix.net/products
   curl http://$appname-customers.mybluemix.net/customers
   curl http://$appname-orders.mybluemix.net/orders
   ```
   {: pre}

   The following is an example of what is returned:

   ```shell
   curl http://$appname-inventory.mybluemix.net/products
   ```
   {: pre}
   
   ```text
   {"content":[{"id":1,"name":"Grog","description":"A secret mixture that contains one or more of the following: Kerosene, Propylene Glycol, Artificial Sweeteners, Sulfuric Acid, Rum, Acetone, Battery Acid, red dye#2, Scumm, Axle grease and/or pepperoni."},{"id":2,"name":"Ship's Horn","description":"Made in Hong Kong"},{"id":3,"name":"Well-Polished Old Saw","description":"Found at the bottom of the sea. Great condition."},{"id":4,"name":"Rubber Chicken With A Pulley In The Middle","description":"What possible use could this have?"},{"id":5,"name":"Idol of Many Hands","description":"Also known as the Fabulous Idol"},{"id":6,"name":"How Much Wood? - Hardcover","description":"From the Woodchuck Mystery series"}],"pageable":{"sort":{"sorted":false,"unsorted":true,"empty":true},"pageNumber":0,"pageSize":20,"offset":0,"paged":true,"unpaged":false},"last":true,"totalPages":1,"totalElements":6,"sort":{"sorted":false,"unsorted":true,"empty":true},"numberOfElements":6,"first":true,"size":20,"number":0,"empty":false}%
   ```
   {: screen}

   ```shell
   curl http://$appname-customers.mybluemix.net/customers
   ```
   {: pre}

   ```text
   {"content":[{"id":1,"username":"phlegm_master_19","name":"Guybrush","surname":"Threepwood","address":"1060 West Addison","zipCode":"ME-001","city":"Melee Town","country":"Melee Island"},{"id":2,"username":"hate_guybrush","name":"Pirate","surname":"Lechuck","address":"Caverns of Meat, no number","zipCode":"MO-666","city":"Giant Monkey Head","country":"Monkey Island"},{"id":3,"username":"the_governor_em","name":"Elaine","surname":"Marley","address":"PO Box 1","zipCode":"BO-001","city":"Ville de la Booty","country":"Booty Island"},{"id":4,"username":"rescue_me","name":"Herman","surname":"Toothrot","address":"1110 Gorgas Ave","zipCode":"94129","city":"Dinky Beach","country":"Dinky Island"},{"id":5,"username":"i_rule_scabb","name":"Largo","surname":"LaGrande","address":"Swamp Rot Inn","zipCode":"SC-002","city":"Woodtick","country":"Scabb Island"}],"pageable":{"sort":{"sorted":false,"unsorted":true,"empty":true},"pageNumber":0,"pageSize":20,"offset":0,"unpaged":false,"paged":true},"totalPages":1,"totalElements":5,"last":true,"sort":{"sorted":false,"unsorted":true,"empty":true},"first":true,"numberOfElements":5,"size":20,"number":0,"empty":false}%
   ```
   {: screen}
   
   ```shell
   curl http://$appname-orders.mybluemix.net/orders
   ```
   {: pre}
   
   ```text
   {"content":[{"id":1,"customerUID":1,"date":"30-05-2018","items":[{"id":1,"productUID":4,"quantity":1,"price":30.00},{"id":2,"productUID":3,"quantity":1,"price":50.00},{"id":3,"productUID":5,"quantity":1,"price":200.00},{"id":4,"productUID":1,"quantity":4,"price":5.00},{"id":5,"productUID":2,"quantity":1,"price":60.00},{"id":6,"productUID":6,"quantity":1,"price":20.00}]},{"id":2,"customerUID":2,"date":"12-04-2018","items":[{"id":7,"productUID":3,"quantity":1,"price":45.00},{"id":8,"productUID":6,"quantity":1,"price":20.00}]},{"id":3,"customerUID":5,"date":"14-04-2018","items":[{"id":9,"productUID":1,"quantity":5,"price":5.00}]},{"id":4,"customerUID":4,"date":"25-04-2018","items":[{"id":10,"productUID":2,"quantity":1,"price":60.00}]}],"pageable":{"sort":{"sorted":false,"unsorted":true,"empty":true},"pageNumber":0,"pageSize":20,"offset":0,"paged":true,"unpaged":false},"totalPages":1,"totalElements":4,"last":true,"sort":{"sorted":false,"unsorted":true,"empty":true},"numberOfElements":4,"first":true,"size":20,"number":0,"empty":false}%    
   ```
   {: screen}

2. Verify the gateway is properly pulling the data.  The results of these commands should return the same information as step 1.

   ```shell
   curl http://$appname> -gateway.mybluemix.net/customers
   curl http://$appname-gateway.mybluemix.net/orders
   curl http://$appname-gateway.mybluemix.net/products
   ```
   {: pre}

   After completing steps 1 and 2 you have tested 4 of the 5 components.

3. Load the final component.  This is the front-end UI. From a browser navigate to [http://$appname-gateway.mybluemix.net/products](http://$appname-gateway.mybluemix.net/products){: external}

   If for some reason you have a problem deploying the last component try running `ibmcloud cf push $appname-frontend`. This might, or might not resolve the problem. If you can't get the final component deployed, you can still move forward with the `move2kube` steps and work with just the first 4 components.

## Next steps - `move2kube` phases (`collect`, `plan`, `transform`)
{: #cf_deptool7}

There are three phases when running `move2kube`.  These are: collect, plan, and transform.

### Collect information from your {{site.data.keyword.ibmcf_full}} application 
{: #cf_deptool_collect}

Now that you have a working deployment of a sample {{site.data.keyword.ibmcf_notm}} application, you can use the first phase of the `move2kube` tool to `collect` information about the Cloud Foundry app.

In the transform phase, You will collect information about the buildpacks that are supported, the memory, the number of instances, and the ports that are supported. If there are environment variables, that information is collected as well.


Running the `./deploy-to-cf` script to deploy application services into IBM Cloud Foundry will generate artifacts. Because of this you will need a new copy of the source code to invoke `move2kube`. If you followed the folder structure mentioned above, no actions are required.
{: note}

```shell
 cd ../.../../../move2kube-demos-<name_of_target>
 move2kube collect -a cf
```
{: pre}

The following is an example of the output from this command:

```text
INFO[0000] Begin collection
INFO[0000] [*collector.CfAppsCollector] Begin collection
INFO[0006] Changing metadata name from IBM Cloud to ibm-cloud
INFO[0009] [*collector.CfAppsCollector] Done
INFO[0009] [*collector.CfServicesCollector] Begin collection
INFO[0013] Changing metadata name from IBM Cloud to ibm-cloud
INFO[0013] [*collector.CfServicesCollector] Done
INFO[0013] Collection done
INFO[0013] Collect Output in [/Users/elvinjohngalarza@ibm.com/move2kube-roks-demo/move2kube-demos-clean/m2k_collect]. Copy this directory into the source directory to be used for planning.
```
{: screen}

Run the following command to look at the collected data.  The data is stored in your current working directory by default. 

```shell
ls m2k_collect/cf
```
{: pre}

The following is an example of the output from this command:

```text
cfapps-ibm-cloud-39e7da7a9e635f73.yaml
cfservices-ibm-cloud-3873c1404a0c63f9.yaml
```
{: screen}

In this case the `m2k_collect/cf` directory contains the runtime information of the application that you are going to transform. 

### Create a plan on how to transform your {{site.data.keyword.ibmcf_notm}} application 
{: #cf_deptool_plan}

The plan phase combines the runtime information with the `enterprise-app` source artifacts to determine a plan to transform and subsequently deploy  the app to the cluster. You give `Move2Kube` the path to the source directory that contains the source code and the manifest files of the {{site.data.keyword.ibmcf_notm}} application by using the `-s` flag.

Move the `./m2k_collect_cf` directory into the `enterprise-app/src` directory using the following command:

```shell
mv m2k_collect move2kube-demos/samples/enterprise-app/src
```
{: pre}

Stay in the current working directory (`move2kube-demos-<name_of_target>`) that you moved  `m2k_collect` from. Do not make `enterprise-app/src` directory your current working directory when running the remaining `move2kube` commands.
{: important}

You should now have `m2k_collect` in the `enterprise-app/src` directory.

Invoke `move2kube plan` to create a `plan` for the `enterprise-app` by specifying the `enterprise-app` source directory with `-s` flag.

```shell
move2kube plan -s move2kube-demos/samples/enterprise-app/src
```
{: pre}

The following is an example of the returned output: 

```text
INFO[0000] Configuration loading done
INFO[0000] Start planning
INFO[0000] Planning started on the base directory
INFO[0000] [CloudFoundry] Planning
INFO[0000] Identified 5 named services and 0 to-be-named services
INFO[0000] [CloudFoundry] Done
INFO[0000] [ComposeAnalyser] Planning
INFO[0000] [ComposeAnalyser] Done
INFO[0000] [DockerfileDetector] Planning
INFO[0001] [DockerfileDetector] Done
INFO[0001] [Base Directory] Identified 5 named services and 0 to-be-named services
INFO[0001] Planning finished on the base directory
INFO[0001] Planning started on its sub directories
INFO[0001] Identified 1 named services and 0 to-be-named services in customers
INFO[0001] Identified 1 named services and 0 to-be-named services in frontend
INFO[0001] Identified 1 named services and 0 to-be-named services in gateway
INFO[0001] Identified 1 named services and 0 to-be-named services in inventory
INFO[0001] Identified 1 named services and 0 to-be-named services in orders
INFO[0001] Planning finished on its sub directories
INFO[0001] [Directory Walk] Identified 5 named services and 0 to-be-named services
INFO[0001] [Named Services] Identified 5 named services
INFO[0001] Planning done
INFO[0001] No of services identified : 5
INFO[0001] Plan can be found at [/Users/elvinjohngalarza@ibm.com/move2kube-roks-demo/move2kube-demos-clean/m2k.plan].
```
{: screen}

By default, your `plan` is created in your current working directory. Run the following command to see the contents of the `plan`.

```shell
cat m2k.plan
```
{: pre}

The following is an example `plan`.

```yaml
apiVersion: move2kube.konveyor.io/v1alpha1
kind: Plan
metadata:
  name: myproject
spec:
  sourceDir: move2kube-demos/samples/enterprise-app/src
  services:
    customers:
      - transformerName: CloudFoundry
        paths:
          BuildArtifact:
            - customers/target/ROOT.war
          CfManifest:
            - customers/manifest.yml
          ServiceDirectories:
            - customers
        configs:
          CloudFoundryService:
            serviceName: customers
          ContainerizationOptions:
            - Maven
      - transformerName: Maven
        name: customers
        type: Service
        paths:
          ServiceDirectories:
            - customers
          ServiceRootDirectory:
            - customers
          pomFiles:
            - customers/pom.xml
        configs:
          Maven:
            mavenAppName: customers
            packagingType: war
            mavenProfiles:
              - local
              - dev-inmemorydb
              - prod-externaldb
            isMvnwPresent: true
            childModules:
              - name: customers
                pomPath: pom.xml
    frontend:
      - transformerName: CloudFoundry
        paths:
          CfManifest:
            - frontend/manifest.yml
          ServiceDirectories:
            - frontend
        configs:
          CloudFoundryService:
            serviceName: frontend
          ContainerizationOptions:
            - Nodejs-Dockerfile
      - transformerName: Nodejs-Dockerfile
        paths:
          ServiceDirectories:
            - frontend
    gateway:
      - transformerName: CloudFoundry
        paths:
          BuildArtifact:
            - gateway/target/gateway-2.0.0-SNAPSHOT.jar
          CfManifest:
            - gateway/manifest.yml
          ServiceDirectories:
            - gateway
        configs:
          CloudFoundryService:
            serviceName: gateway
          ContainerizationOptions:
            - Maven
      - transformerName: Maven
        name: gateway
        type: Service
        paths:
          ServiceDirectories:
            - gateway
          ServiceRootDirectory:
            - gateway
          pomFiles:
            - gateway/pom.xml
        configs:
          Maven:
            mavenAppName: gateway
            packagingType: jar
            mavenProfiles:
              - local
              - dev
              - prod
            isMvnwPresent: true
            childModules:
              - name: gateway
                pomPath: pom.xml
    inventory:
      - transformerName: CloudFoundry
        paths:
          BuildArtifact:
            - inventory/target/inventory-0.0.1-SNAPSHOT.jar
          CfManifest:
            - inventory/manifest.yml
          ServiceDirectories:
            - inventory
        configs:
          CloudFoundryService:
            serviceName: inventory
          ContainerizationOptions:
            - Maven
      - transformerName: Maven
        name: inventory
        type: Service
        paths:
          ServiceDirectories:
            - inventory
          ServiceRootDirectory:
            - inventory
          pomFiles:
            - inventory/pom.xml
        configs:
          Maven:
            mavenAppName: inventory
            packagingType: jar
            mavenProfiles:
              - local
              - dev-inmemorydb
              - prod-externaldb
            isMvnwPresent: true
            childModules:
              - name: inventory
                pomPath: pom.xml
    orders:
      - transformerName: CloudFoundry
        paths:
          BuildArtifact:
            - orders/target/orders-2.0.0-SNAPSHOT.jar
          CfManifest:
            - orders/manifest.yml
          ServiceDirectories:
            - orders
        configs:
          CloudFoundryService:
            serviceName: orders
          ContainerizationOptions:
            - Maven
      - transformerName: Maven
        name: orders
        type: Service
        paths:
          ServiceDirectories:
            - orders
          ServiceRootDirectory:
            - orders
          pomFiles:
            - orders/pom.xml
        configs:
          Maven:
            mavenAppName: orders
            packagingType: jar
            mavenProfiles:
              - local
              - dev-inmemorydb
              - prod-externaldb
            isMvnwPresent: true
            childModules:
              - name: orders
                pomPath: pom.xml
  transformers:
    Buildconfig: m2kassets/built-in/transformers/kubernetes/buildconfig/transformer.yaml
    CloudFoundry: m2kassets/built-in/transformers/cloudfoundry/transformer.yaml
    ClusterSelector: m2kassets/built-in/transformers/kubernetes/clusterselector/transformer.yaml
    ComposeAnalyser: m2kassets/built-in/transformers/compose/composeanalyser/transformer.yaml
    ComposeGenerator: m2kassets/built-in/transformers/compose/composegenerator/transformer.yaml
    ContainerImagesPushScriptGenerator: m2kassets/built-in/transformers/containerimagespushscript/transformer.yaml
    DockerfileDetector: m2kassets/built-in/transformers/dockerfile/dockerfiledetector/transformer.yaml
    DockerfileImageBuildScript: m2kassets/built-in/transformers/dockerfile/dockerimagebuildscript/transformer.yaml
    DockerfileParser: m2kassets/built-in/transformers/dockerfile/dockerfileparser/transformer.yaml
    DotNetCore-Dockerfile: m2kassets/built-in/transformers/dockerfilegenerator/dotnetcore/transformer.yaml
    EarAnalyser: m2kassets/built-in/transformers/dockerfilegenerator/java/earanalyser/transformer.yaml
    EarRouter: m2kassets/built-in/transformers/dockerfilegenerator/java/earrouter/transformer.yaml
    Golang-Dockerfile: m2kassets/built-in/transformers/dockerfilegenerator/golang/transformer.yaml
    Gradle: m2kassets/built-in/transformers/dockerfilegenerator/java/gradle/transformer.yaml
    Jar: m2kassets/built-in/transformers/dockerfilegenerator/java/jar/transformer.yaml
    Jboss: m2kassets/built-in/transformers/dockerfilegenerator/java/jboss/transformer.yaml
    Knative: m2kassets/built-in/transformers/kubernetes/knative/transformer.yaml
    Kubernetes: m2kassets/built-in/transformers/kubernetes/kubernetes/transformer.yaml
    KubernetesVersionChanger: m2kassets/built-in/transformers/kubernetes/kubernetesversionchanger/transformer.yaml
    Liberty: m2kassets/built-in/transformers/dockerfilegenerator/java/liberty/transformer.yaml
    Maven: m2kassets/built-in/transformers/dockerfilegenerator/java/maven/transformer.yaml
    Nodejs-Dockerfile: m2kassets/built-in/transformers/dockerfilegenerator/nodejs/transformer.yaml
    PHP-Dockerfile: m2kassets/built-in/transformers/dockerfilegenerator/php/transformer.yaml
    Parameterizer: m2kassets/built-in/transformers/kubernetes/parameterizer/transformer.yaml
    Python-Dockerfile: m2kassets/built-in/transformers/dockerfilegenerator/python/transformer.yaml
    ReadMeGenerator: m2kassets/built-in/transformers/readmegenerator/transformer.yaml
    Ruby-Dockerfile: m2kassets/built-in/transformers/dockerfilegenerator/ruby/transformer.yaml
    Rust-Dockerfile: m2kassets/built-in/transformers/dockerfilegenerator/rust/transformer.yaml
    Tekton: m2kassets/built-in/transformers/kubernetes/tekton/transformer.yaml
    Tomcat: m2kassets/built-in/transformers/dockerfilegenerator/java/tomcat/transformer.yaml
    WarAnalyser: m2kassets/built-in/transformers/dockerfilegenerator/java/waranalyser/transformer.yaml
    WarRouter: m2kassets/built-in/transformers/dockerfilegenerator/java/warrouter/transformer.yaml
    WinConsoleApp-Dockerfile: m2kassets/built-in/transformers/dockerfilegenerator/windows/winconsole/transformer.yaml
    WinSLWebApp-Dockerfile: m2kassets/built-in/transformers/dockerfilegenerator/windows/winsilverlightweb/transformer.yaml
    WinWebApp-Dockerfile: m2kassets/built-in/transformers/dockerfilegenerator/windows/winweb/transformer.yaml
    ZuulAnalyser: m2kassets/built-in/transformers/dockerfilegenerator/java/zuul/transformer.yaml
```
{: screen}

In the `plan`, you can see that `Move2Kube` has detected all the services related to the `enterprise-app` application. This includes the `order`, `customer`, and `inventory` backend services, as well as the `gateway`, and the `frontend`.

This plan is used along with the `manifest.yml` files associated with each of the `enterprise-app` services in the source directory to do the transformation.

Now that you have all the artifacts needed for the transformation phase, you are ready to run `move2kube transform`. Continue with the steps needed for your new application hosting compute service to complete the `move2kube` process.

Examples of next steps to use `move2kube` with various IBM Cloud compute services can be found [here](http://ibm.github.io/ibmcf-migration-tooling){: external}.


