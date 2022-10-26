---

copyright:
  years: 2015, 2022
lastupdated: "2022-10-26"

keywords: cloud foundry release notes, cloud foundry update, cloud foundry buildpack updates

subcollection: cloud-foundry-public

---

{{site.data.keyword.attribute-definition-list}}

# Release notes for {{site.data.keyword.ibmcf_full}}
{: #cloud-foundry-public-release-notes}

{{site.data.keyword.ibmcf_full}} is deprecated. As of 30 November 2022 new {{site.data.keyword.ibmcf_full}} applications cannot be created and only existing users will be able to deploy applications. End-of-support happens on 1 June 2023. Any instances that still exist on 1 June 2023 will be deleted. For more information, see [the deprecation details](/docs/cloud-foundry-public?topic=cloud-foundry-public-deprecation).
{: deprecated}

Use these release notes to learn about the latest updates to {{site.data.keyword.ibmcf_full}}.
{: shortdesc}

The IBM Supported dotnet-core buildpack has been deprecated. The latest updates on the dotnet-core buildpack can be found here: [https://github.com/cloudfoundry/dotnet-core-buildpack/releases](https://github.com/cloudfoundry/dotnet-core-buildpack/releases){: external}.
{: important}

The SDK for Node.js has been deprecated. The latest updates on the Node.js buildpack can be found here: [https://github.com/cloudfoundry/nodejs-buildpack/releases](https://github.com/cloudfoundry/nodejs-buildpack/releases){: external}. For more details please read the [IBM announcement blog.](https://www.ibm.com/cloud/blog/announcements/ibm-cloud-foundry-nodejs-buildpack-change){: external}.
{: important}

<staging>
## 26 October 2022
{: #cloud-foundry-public-oct2622}
{: release-note}

IBM Cloud Foundry [end-of-marketing is 30 November 2022](https://ibm.biz/ibmcf-announce). On 30 November 2022 all new IBM Cloud users are blocked from deploying Cloud Foundry applications. Existing users that already have Cloud Foundry applications deployed can continue to deploy new applications and use their applications until the [end-of-support date.](/docs/cloud-foundry-public?topic=cloud-foundry-public-deprecation#dep_timeline)
<staging>

## 25 October 2022
{: #cloud-foundry-public-oct2522}
{: release-note}

Updated Liberty buildpack v3.75-20221012-1015
:   The alternate Liberty runtime version is changed to the `22.0.0.11` release. The default runtime remains the same [22.0.0.9](https://openliberty.io/blog/2022/08/30/password-utilities-22009.html)){: external}.
    * The default and monthly Liberty runtime contain the fix for the following security vulnerability:
        * [CVE-2022-24839](https://www.ibm.com/support/pages/node/6824871){: external} 

    * To specify the monthly runtime set the following two variables and restage your application: 
 
      ```text
      ibmcloud cf set-env <yourappname> JBP_CONFIG_LIBERTY "version: +"
      ibmcloud cf set-env <yourappname> IBM_LIBERTY_MONTHLY true
      ```
      {: codeblock}
    
    * The IBM Semeru Open J9 alternate JRE remains unchanged `ibm-semeru-open-jre_x64_linux_11.0.16.1_1_openj9-0.33.1`
        * To specify the alternate JRE set the following variable:

            ```text
            ibmcloud cf set-env myapp JBP_CONFIG_IBMJDK "version: 11.+"
            ```
            {: codeblock}
    
    * The IBM JRE version is changed to `8 SR7 FP16`.
    
## 27 September 2022
{: #cloud-foundry-public-sep2722}
{: release-note}

Updated Liberty buildpack v3.74-20220913-1224
:   The alternate Liberty runtime version is changed to the `22.0.0.10` release. The default runtime remains the same [22.0.0.9](https://openliberty.io/blog/2022/08/30/password-utilities-22009.html)){: external}.
    * The default and monthly Liberty runtime contain the fix for the following security vulnerability:
        * [CVE-2022-34165](https://www.ibm.com/support/pages/node/6618747){: external} 
        
	* To specify the monthly runtime set the following two variables and restage your application: 
 
	```text
	ibmcloud cf set-env <yourappname> JBP_CONFIG_LIBERTY "version: +"
	ibmcloud cf set-env <yourappname> IBM_LIBERTY_MONTHLY true
	```
	{: codeblock}          
        
    * The IBM Semeru Open J9 alternate JRE is changed to `ibm-semeru-open-jre_x64_linux_11.0.16.1_1_openj9-0.33.1`.
    
        * To specify the alternate JRE set the following variable:

          ```text
          ibmcloud cf set-env myapp JBP_CONFIG_IBMJDK "version: 11.+"
          ```
          {: codeblock}
    
    * The IBM JRE version is changed to `8 SR7 FP15` and contains fixes for the following security vulnerabilities: 
       * [CVE-2021-2163](https://www.ibm.com/support/pages/apar/IJ32229){: external}    
       * [July 2022 Oracle security fixes](https://www.ibm.com/support/pages/java-sdk-security-vulnerabilities){: external}. 


## 30 August 2022
{: #cloud-foundry-public-aug3022}
{: release-note}

Updated Liberty buildpack v3.73-20220816-0814
:   The alternate and default Liberty runtime version is changed to the `22.0.0.9` release. 
    * The default and monthly Liberty runtime `22.0.0.9` contains the security fix for the following PSIRT:
        * [CVE-2019-11777](https://www.ibm.com/support/pages/node/6602039){: external} 
        
    * The IBM Semeru Open J9 alternate JRE is changed to `ibm-semeru-open-jre_x64_linux_11.0.16_8_openj9-0.33.0`.
    
        * To specify the alternate JRE set the following variable:

          ```text
          ibmcloud cf set-env myapp JBP_CONFIG_IBMJDK "version: 11.+"
          ```
          {: codeblock}
    
    * The IBM JRE version remains unchanged `8 SR7 FP11`.        

## 29 August 2022
{: #cloud-foundry-public-aug29222}
{: release-note}

Change required custom domains
:    SSL certificates for custom domains must now be uploaded using {{site.data.keyword.secrets-manager_full}}. Custom domains where the SSL certificates have not been uploaded using the new process will stop working on dates depending on the region. For more information see [Custom Domain update required for Cloud Foundry Applications](/docs/cloud-foundry-public?topic=cloud-foundry-public-custom_domain_usage).


## 2 August 2022
{: #cloud-foundry-public-aug0222}
{: release-note}

Updated Liberty buildpack v3.72-20220720-1509
:    The alternate Liberty runtime GA version is changed to the `22.0.0.8` release. The default runtime remains the same [22.0.0.6](https://openliberty.io/blog/2022/06/07/microprofile-graphql-2-22006.html){: external}.

    * The monthly Liberty runtime `22.0.0.8` contains security fixes for the following PSIRTs:
        * [CVE-2019-11777](https://www.ibm.com/support/pages/node/6602039){: external} 
            * The monthly runtime 22.0.0.8 must be used to obtain this fix (steps found below)
        * [CVE-2022-22476](https://www.ibm.com/support/pages/node/6602015){: external} 
            * Both the default 22.0.0.6 and monthly 22.0.0.8 runtime contains this fix 

    * To specify the monthly runtime set the following two variables: 
    
        ```text
        ibmcloud cf set-env <yourappname> JBP_CONFIG_LIBERTY "version: +"
        ibmcloud cf set-env <yourappname> IBM_LIBERTY_MONTHLY true
        ```
        {: codeblock} 
    
    * The IBM Semeru Open J9 alternate JRE remains the same `ibm-semeru-open-jre_x64_linux_11.0.15_10_openj9-0.32.0`.
    
        * To specify the alternate JRE set the following variable:

          ```text
          ibmcloud cf set-env myapp JBP_CONFIG_IBMJDK "version: 11.+"
          ```
          {: codeblock}
    
    * The IBM JRE version is changed to `8 SR7 FP11`.

## 5 July 2022
{: #cloud-foundry-public-july0522}
{: release-note}

Updated Liberty buildpack v3.71-20220621-1017

:    The alternate Liberty runtime GA version is changed to the `22.0.0.7` release. The default runtime remains the same [22.0.0.6](https://openliberty.io/blog/2022/06/07/microprofile-graphql-2-22006.html){: external}.

    * To specify the monthly runtime set the following two variables: 
    
        ```text
        ibmcloud cf set-env <yourappname> JBP_CONFIG_LIBERTY "version: +"
        ibmcloud cf set-env <yourappname> IBM_LIBERTY_MONTHLY true
        ```
        {: codeblock} 
    
    * The IBM Semeru Open J9 alternate JRE remains the same `ibm-semeru-open-jre_x64_linux_11.0.15_10_openj9-0.32.0`.
    
        * To specify the alternate JRE set the following variable:

          ```text
          ibmcloud cf set-env myapp JBP_CONFIG_IBMJDK "version: 11.+"
          ```
          {: codeblock}
    
    * The IBM JRE version is changed to `8 SR7 FP10` and contains security fixes for the following PSIRTs: 
       * [April 2022 Oracle security fixes](https://www.ibm.com/support/pages/node/6591179){: external} which includes fixes to the following CVEs: 
        * [CVE-2022-21496](https://www.ibm.com/support/pages/apar/IJ39998){: external}
        * [CVE-2022-21434](https://www.ibm.com/support/pages/apar/IJ39999){: external}
        * [CVE-2022-21443](https://www.ibm.com/support/pages/apar/IJ40004){: external}
        
## 7 June 2022
{: #cloud-foundry-public-june0622}
{: release-note}        
        
Updated Liberty buildpack v3.70-20220525-0737

:   The alternate and default Liberty runtime GA version is changed to the `22.0.0.6` release. 
    * The 22.0.0.6 runtime includes a fix for the following CVE: 
        * [CVE-2022-22475](https://www.ibm.com/support/pages/node/6586734) {: external}

    * To specify the monthly runtime set the following two variables: 
    
        ```text
        ibmcloud cf set-env <yourappname> JBP_CONFIG_LIBERTY "version: +"
        ibmcloud cf set-env <yourappname> IBM_LIBERTY_MONTHLY true
        ```
        {: codeblock} 
    
    * The IBM Semeru Open J9 alternate JRE is changed to `ibm-semeru-open-jre_x64_linux_11.0.15_10_openj9-0.32.0`.
    
        * To specify the alternate JRE set the following variable:

          ```text
          ibmcloud cf set-env myapp JBP_CONFIG_IBMJDK "version: 11.+"
          ```
          {: codeblock}
    
    * The IBM JRE version remains unchanged `8 SR7 FP6`.


## 31 May 2022
{: #cloud-foundry-public-jun0222}
{: release-note}

{{site.data.keyword.ibmcf_full}} is deprecated
:   IBM announces the deprecation of {{site.data.keyword.ibmcf_full}}. For more information, see [the deprecation details](/docs/cloud-foundry-public?topic=cloud-foundry-public-deprecation).

## 12 May 2022
{: #cloud-foundry-public-may1222}
{: release-note}

Updated Liberty buildpack v3.69-20220426-1537

:   The alternate Liberty runtime GA version is changed to the `22.0.0.5` release. The default runtime remains the same [22.0.0.3](https://openliberty.io/blog/2022/03/15/sql-retries-22003.html){: external}.

    * To specify the monthly runtime set the following two variables: 
    
        ```text
        ibmcloud cf set-env <yourappname> JBP_CONFIG_LIBERTY "version: +"
        ibmcloud cf set-env <yourappname> IBM_LIBERTY_MONTHLY true
        ```
        {: codeblock} 
    
    * The IBM Semeru Open J9 alternate JRE remains the same `ibm-semeru-open-jre_x64_linux_11.0.14.1_1_openj9-0.30.1`.
    
        * To specify the alternate JRE set the following variable:

          ```text
          ibmcloud cf set-env myapp JBP_CONFIG_IBMJDK "version: 11.+"
          ```
          {: codeblock}
    
    * The IBM JRE version is changed to `8 SR7 FP6`.


## 12 April 2022
{: #cloud-foundry-public-apr1222}
{: release-note}


Updated Liberty buildpack v3.68-20220329-1120

:   The alternate Liberty runtime GA version is changed to the `22.0.0.4` release. The default runtime remains the same [22.0.0.3](https://openliberty.io/blog/2022/03/15/sql-retries-22003.html){: external}.

    * To specify the monthly runtime set the following two variables: 
    
        ```text
        ibmcloud cf set-env <yourappname> JBP_CONFIG_LIBERTY "version: +"
        ibmcloud cf set-env <yourappname> IBM_LIBERTY_MONTHLY true
        ```
        {: codeblock} 

    * The IBM Semeru Open J9 alternate JRE remains the same `ibm-semeru-open-jre_x64_linux_11.0.14.1_1_openj9-0.30.1`.
    
        * To specify the alternate JRE set the following variable:

          ```text
          ibmcloud cf set-env myapp JBP_CONFIG_IBMJDK "version: 11.+"
          ```
        {: codeblock}
        
    * The IBM JRE version remains unchanged `8 SR7 FP5`.

## 15 March 2022
{: #cloud-foundry-public-mar1522}
{: release-note}


Updated Liberty buildpack v3.67-20220303-1119

:   The alternate and default Liberty runtime GA version is changed to the `22.0.0.3` release.

    * To specify the monthly runtime set the following two variables: 
    
        ```text
        ibmcloud cf set-env <yourappname> JBP_CONFIG_LIBERTY "version: +"
        ibmcloud cf set-env <yourappname> IBM_LIBERTY_MONTHLY true
        ```
        {: codeblock} 

        
    * The IBM Semeru Open J9 alternate JRE is updated to `ibm-semeru-open-jre_x64_linux_11.0.14.1_1_openj9-0.30.1`.
    
        * To specify the alternate JRE set the following variable:

          ```text
          ibmcloud cf set-env myapp JBP_CONFIG_IBMJDK "version: 11.+"
          ```
        {: codeblock}

    * The IBM JRE version is changed to `8 SR7 FP5` and contains security fixes for the following PSIRTs including Oracle security fixes from the January 2022 CPU updates: 
      * [CVE-2021-35550](https://www.ibm.com/support/pages/node/6559262){: external}
      * [January 2022 Oracle security fixes](https://www.ibm.com/support/pages/node/6558558){: external} which includes fixes to the following CVEs: 
        * [CVE-2022-21365](https://www.ibm.com/support/pages/node/6559266){: external}
        * [CVE-2022-21360](https://www.ibm.com/support/pages/apar/IJ37842){: external}
        * [CVE-2022-21349](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-21349){: external}
        * [CVE-2022-21341](https://www.ibm.com/support/pages/apar/IJ37844){: external}
        * [CVE-2022-21340](https://www.ibm.com/support/pages/apar/IJ37847){: external}
        * [CVE-2022-21305](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-21305){: external}
        * [CVE-2022-21294](https://www.ibm.com/support/pages/apar/IJ37849){: external}
        * [CVE-2022-21293](https://www.ibm.com/support/pages/apar/IJ37851){: external}
        * [CVE-2022-21291](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-21291){: external}
        * [CVE-2022-21248](https://www.ibm.com/support/pages/apar/IJ37852){: external}


## 15 February 2022
{: #cloud-foundry-public-feb1522}
{: release-note}


Updated Liberty buildpack v3.66-20220202-1042
:   The alternate Liberty runtime GA version is changed to the `22.0.0.2` release. The default runtime remains the same [21.0.0.12](https://openliberty.io/blog/2021/11/26/jakarta-ee-9.1.html){: external}.

    * To specify the monthly runtime set the following two variables: 
    
        ```text
        ibmcloud cf set-env <yourappname> JBP_CONFIG_LIBERTY "version: +"
        ibmcloud cf set-env <yourappname> IBM_LIBERTY_MONTHLY true
        ```
        {: codeblock} 
        
    * The default and alternate runtime of `22.0.0.2` and `21.0.0.12` address the following PSIRT security vulnerabilities: 
      * [CVE-2021-39031](https://www.ibm.com/support/pages/node/6550488){: external}
      * [CVE-2022-22310](https://www.ibm.com/support/pages/node/6541530){: external}
    * The default runtime `21.0.0.12` includes the following fixes: 
      * [CVE-2022-22310](https://www.ibm.com/support/pages/node/6541522)
      * [CVE-2021-39031](https://www.ibm.com/support/pages/node/6549542)
    * The IBM JRE version remains unchanged (8 SR7 FP0)
    * The AdoptOpenJDK Open J9 alternate JRE is updated to `ibm-semeru-open-jre_x64_linux_11.0.14_9_openj9-0.30.0`.

## 18 January 2022
{: #cloud-foundry-public-jan1822}
{: release-note}


Updated Liberty buildpack v3.65-20220106-0934
:   The alternate Liberty runtime GA version is changed to the `22.0.0.1` release. The default runtime remains the same 21.0.0.12.

    * To specify the monthly runtime set the following two variables: 
    
        ```text
        ibmcloud cf set-env <yourappname> JBP_CONFIG_LIBERTY "version: +"
        ibmcloud cf set-env <yourappname> IBM_LIBERTY_MONTHLY true
        ```
        {: codeblock} 
    
    * The IBM JRE Version is updated to 8 SR7 FP0. The default security provider has been changed to IBMJCEPlus. The IBM JRE contains the Oracle Security fixes from Oct '21 CPU updates and IBM fixes including: 
      * [CVE-2021-35556](https://www.ibm.com/support/pages/apar/IJ36022){: external}
      * [CVE-2021-35559](https://www.ibm.com/support/pages/apar/IJ36021){: external}
      * [CVE-2021-35560](https://www.ibm.com/support/pages/apar/IJ36016){: external}
      * [CVE-2021-35565](https://www.ibm.com/support/pages/apar/IJ36023){: external}
      * [CVE-2021-35586](https://www.ibm.com/support/pages/apar/IJ36018){: external}
      * [CVE-2021-41035](https://www.ibm.com/support/pages/apar/IJ35976){: external}
      * [CVE-2021-35564](https://www.ibm.com/support/pages/apar/IJ35992){: external}
      * [CVE-2021-35578](https://www.ibm.com/support/pages/apar/IJ36019){: external}
    * The AdoptOpenJDK Open J9 alternate JRE is updated to ibm-semeru-open-jre_x64_linux_11.0.13_8_openj9-0.29.0.

## 01 December 2021
{: #cloud-foundry-public-dec0121}
{: release-note}

Updated Liberty buildpack v3.64-20211118-1947
:   The alternate and default Liberty runtime GA version is changed to the `21.0.0.12` release. 
    * To specify the monthly runtime set the following two variables: 
    
        ```text
        ibmcloud cf set-env <yourappname> JBP_CONFIG_LIBERTY "version: +"
        ibmcloud cf set-env <yourappname> IBM_LIBERTY_MONTHLY true
        ```
        {: codeblock} 
    
    * The AdoptOpenJDK OpenJ9 alternate JRE (`11.0.12_7_openj9-0.27.0`) and IBM JRE Version (`8 SR6 FP36`) remain unchanged. 

## 29 October 2021
{: #cloud-foundry-public-oct2921}
{: release-note}

Updated Liberty buildpack v3.63-20211020-1608
:   The alternate Liberty runtime GA version is changed to the `21.0.0.11` release. The default runtime remains the same [21.0.0.9](https://openliberty.io/blog/2021/09/03/microprofile-21009.html){: external}

    * To specify the monthly runtime set the following two variables: 
    
        ```text
        ibmcloud cf set-env <yourappname> JBP_CONFIG_LIBERTY "version: +"
        ibmcloud cf set-env <yourappname> IBM_LIBERTY_MONTHLY true
        ```
        {: codeblock} 
    
    * The AdoptOpenJDK OpenJ9 alternate JRE (`11.0.12_7_openj9-0.27.0`) and IBM JRE Version (`8 SR6 FP36`) remain unchanged. 


## 1 October 2021
{: #cloud-foundry-public-oct0121}
{: release-note}

Updated Liberty buildpack v3.62-20210922-1852
:   The alternate Liberty runtime GA version is changed to the `21.0.0.10` release. The default runtime remains the same 21.0.0.9.

    * To specify the monthly runtime set the following two variables: 
    
        ```text
        ibmcloud cf set-env <yourappname> JBP_CONFIG_LIBERTY "version: +"
        ibmcloud cf set-env <yourappname> IBM_LIBERTY_MONTHLY true
        ```
        {: codeblock} 

    * The default and alternate runtime 21.0.0.9 and 21.0.0.10 addresses the following PSIRT security vulnerabilities: 
        
        * [CVE-2021-36090, CVE-2021-35517](https://www.ibm.com/support/pages/node/6489683){: external}: Vulnerability in Apache Commons Compress library that is used by Websphere Application Server Liberty.
        
        * [CVE-2021-29842](https://www.ibm.com/support/pages/node/6488623){: external}: Vulnerability in WebSphere Application Server to information disclosure.
    
    * The IBM JRE Version is updated to 8 SR6 FP36. 

## 3 September 2021
{: #cloud-foundry-public-sep0321}
{: release-note}

Updated Liberty buildpack v3.61-20210826-1015
:   The alternate and default Liberty runtime GA version is changed to the `21.0.0.9` release.
    
    * To specify the monthly runtime set the following two variables: 
    
        ```text
        ibmcloud cf set-env <yourappname> JBP_CONFIG_LIBERTY "version: +"
        ibmcloud cf set-env <yourappname> IBM_LIBERTY_MONTHLY true
        ```
        {: codeblock} 

    * The new release includes MicroProfile 4.1 package. 
    
    * The IBM JRE Version is updated to 8 SR6 FP35 and includes the [Oracle's July Security fixes](https://www.oracle.com/security-alerts/cpujul2021.html){: external}.  

    * The AdoptOpenJDK Open J9 alternate JRE is updated to 1.0.13_8_openj9-0.29.0.

## 6 August 2021
{: #cloud-foundry-public-aug0621}
{: release-note}

Updated Liberty buildpack v3.60-20210730-0620
:   The alternate Liberty runtime GA version is changed to the `21.0.0.8` release.

    * The default Liberty runtime GA version remains the same [21.0.0.6](https://openliberty.io/blog/2021/06/11/request-timing-21006.html){: external}. 
    
    * To specify the monthly runtime set the following two variables: 
  
        ```text
        ibmcloud cf set-env <yourappname> JBP_CONFIG_LIBERTY "version: +"
        ibmcloud cf set-env <yourappname> IBM_LIBERTY_MONTHLY true
        ```
        {: codeblock}
      
    * The AdoptOpenJDK OpenJ9 alternate JRE (`11.0.11_9_openj9-0.26.0`) and IBM JRE Version (`8 SR6 FP31`) remains unchanged.

## 8 July 2021
{: #cloud-foundry-public-jul0821}
{: release-note}

Updated Liberty buildpack v3.59-20210701-1053
:   The alternate Liberty runtime GA version is changed to the `21.0.0.7` release.

    * The default Liberty runtime GA version remains the same [21.0.0.6](https://openliberty.io/blog/2021/06/11/request-timing-21006.html){: external} release.
    
    * To specify the monthly runtime set the following two variables: 
  
        ```text
        ibmcloud cf set-env <yourappname> JBP_CONFIG_LIBERTY "version: +"
        ibmcloud cf set-env <yourappname> IBM_LIBERTY_MONTHLY true
        ```
        {: codeblock}
    
    * The AdoptOpenJDK OpenJ9 alternate JRE (`11.0.11_9_openj9-0.26.0`) and IBM JRE Version (`8 SR6 FP31`) remains unchanged.

## 11 June 2021
{: #cloud-foundry-public-jun1121}
{: release-note}

Updated Liberty buildpack v3.58-20210602-1655
:   The default and alternate Liberty runtime GA version is changed to the `21.0.0.6` release.

    * The IBM JRE Version is updated to 8 SR6 FP31. 

    * The IBM JRE 8 SR6 FP31 includes the following security fix: 
        * [CVE-2021-20492](https://www.ibm.com/support/pages/node/6456017){: external} - Websphere Application Server Java Batch is vulnerable to an XML External Entity Injection (XXE) attack when processing XML data
  
    * To specify the monthly runtime set the following two variables: 
    
        ```text
        ibmcloud cf set-env <yourappname> JBP_CONFIG_LIBERTY "version: +"
        ibmcloud cf set-env <yourappname> IBM_LIBERTY_MONTHLY true
        ```
        {: codeblock}
    
    * The AdoptOpenJDK OpenJ9 alternate JRE (11.0.11_9_openj9-0.26.0) remains unchanged.

## 19 May 2021
{: #cloud-foundry-public-may1921}
{: release-note}

Updated Liberty buildpack v3.57-20210512-1446
:   The alternate Liberty runtime GA version is changed to the [21.0.0.5](https://openliberty.io/blog/2021/05/14/ldap-multipart-21005.html){: external} release.

    * The default Liberty runtime GA version remains the same [21.0.0.3](https://openliberty.io/blog/2021/03/19/microprofile-4-21003.html){: external} release.

    * The alternate Liberty runtime version [21.0.0.5](https://openliberty.io/blog/2021/05/14/ldap-multipart-21005.html) includes a fix for the [CVE-2021-26296)](https://www.ibm.com/support/pages/node/6441433){: external} security vulnerability.
    
    * To specify the monthly runtime set the following two variables: 
    
        ```text
        ibmcloud cf set-env <yourappname> JBP_CONFIG_LIBERTY "version: +"
        ibmcloud cf set-env <yourappname> IBM_LIBERTY_MONTHLY true
        ```
        {: codeblock}
    
    * For more information see [Use the monthly runtime](/docs/cloud-foundry-public?topic=cloud-foundry-public-using_monthly_runtime)

    * The AdoptOpenJDK OpenJ9 alternate JRE (`11.0.11_9_openj9-0.26.0`) and IBM JRE Version (`8 SR6 FP26`) remains unchanged

## 9 April 2021
{: #cloud-foundry-public-apr0921}
{: release-note}

Updated Liberty buildpack v3.56-20210412-1223
:   The alternate Liberty runtime GA version is changed to the `21.0.0.4` release.

    * The alternate Liberty runtime version `21.0.0.4` includes a fix for the [CVE-2021-26296](https://www.ibm.com/support/pages/node/6441433){: external} security vulnerability.
    
    * To specify the monthly runtime set the following two variables: 
  
        ```text
        ibmcloud cf set-env <yourappname> JBP_CONFIG_LIBERTY "version: +"
        ibmcloud cf set-env <yourappname> IBM_LIBERTY_MONTHLY true
        ```
        {: codeblock}
    
    * For more information see [Use the monthly runtime](/docs/cloud-foundry-public?topic=cloud-foundry-public-using_monthly_runtime)

    * The default Liberty runtime GA version is the [21.0.0.3](https://openliberty.io/blog/2021/03/19/microprofile-4-21003.html){: external} release.

    * The AdoptOpenJDK OpenJ9 alternate JRE (`11.0.10_9_openj9-0.24.0`) and IBM JRE Version (`8 SR6 FP26`) remains unchanged. 

## 19 March 2021
{: #cloud-foundry-public-mar1921}
{: release-note}

Updated the ASP.NET Core buildpack v2.10-20210312-1113
:   This release includes version 2.3.25 of the `dotnet-core` Cloud Foundry buildpack.

    * Add support for .NET ASP.NET Core 2.1.25
    * Add support for .NET ASP.NET Core 2.1.26
    * Add support for .NET ASP.NET Core 3.1.12
    * Add support for .NET ASP.NET Core 3.1.13
    * Add support for .NET ASP.NET Core 5.0.3
    * Add support for .NET ASP.NET Core 5.0.4
    * Add support for .NET Runtime 2.1.25
    * Add support for .NET Runtime 2.1.26
    * Add support for .NET Runtime 3.1.12
    * Add support for .NET Runtime 3.1.13
    * Add support for .NET Runtime 5.0.3
    * Add support for .NET Runtime 5.0.4
    * Add support for .NET SDK 2.1.813
    * Add support for .NET SDK 2.1.814
    * Add support for .NET SDK 3.1.406
    * Add support for .NET SDK 3.1.407
    * Add support for .NET SDK 5.0.200
    * Add support for .NET SDK 5.0.201
    * Remove support for .NET ASP.NET Core 2.1.22
    * Remove support for .NET ASP.NET Core 2.1.23
    * Remove support for .NET ASP.NET Core 3.1.9
    * Remove support for .NET ASP.NET Core 3.1.10
    * Remove support for .NET ASP.NET Core 5.0.0
    * Remove support for .NET Runtime 2.1.22
    * Remove support for .NET Runtime 2.1.23
    * Remove support for .NET Runtime 3.1.9
    * Remove support for .NET Runtime 3.1.10
    * Remove support for .NET Runtime 5.0.0
    * Remove support for .NET SDK 2.1.810
    * Remove support for .NET SDK 2.1.811
    * Remove support for .NET SDK 3.1.403
    * Remove support for .NET SDK 3.1.404
    * Remove support for .NET SDK 5.0.100
    * Update Node.js version to 10.23.0

## 15 March 2021
{: #cloud-foundry-public-mar1521}
{: release-note}

Updated Liberty buildpack v3.55-20210311-1642
:   The default and alternate Liberty runtime GA version is changed to the `21.0.0.3` release.

    * The IBM JRE Version is updated to 8 SR6 FP26.

    * The IBM JRE 8 SR6 FP26 includes the following security fixes:
       
        * [CVE-2020-14782](https://www.ibm.com/support/pages/node/6370061){: external} - A vulnerability in Java SE related to Libraries Component
       
        * [CVE-2020-14781](https://www.ibm.com/support/pages/node/6370061){: external} - A vulnerability in Java SE related to JNDI Component.
       
        * [CVE-2020-27221](https://www.ibm.com/support/pages/node/6417051){: external} - Eclipse OpenJ9 vulnerability to a stack-based buffer overflow.
    
        * [CVE-2020-2773](https://www.ibm.com/support/pages/node/6414729){: external} - A vulnerability in Java SE related to the Java SE Security component.

## 5 March 2021
{: #cloud-foundry-public-mar0521}
{: release-note}

Updated Node.js buildpack v4.6-20210305-2036
:   The SDK for Node.js buildpack v4.6 is based on community buildpack v1.7.44 and includes the following Node.js runtimes: v10.23.3, v10.24.0, v12.20.2, v12.21.0, v14.15.5, v14.16.0. The default runtime is the latest v10.x (currently 10.23.3). This buildpack is based on the community node.js buildpack [v1.7.44](https://github.com/cloudfoundry/nodejs-buildpack/releases/tag/v1.7.44).

    This release also includes fixes for CVE-2021-23839, CVE-2021-23840, CVE-2021-23841, CVE-2020-1971, CVE-2020-8265, CVE-2020-8287: 

    * [January 2021 Security Releases](https://nodejs.org/en/blog/vulnerability/january-2021-security-releases/)

    * [February 2021 Security Releases](https://nodejs.org/en/blog/vulnerability/february-2021-security-releases/)

## 12 February 2021
{: #cloud-foundry-public-feb1221}
{: release-note}

Updated Liberty buildpack v3.54-20210211-1310
:   The alternate Liberty runtime GA version is changed to the `21.0.0.2` release.

    * The default Liberty runtime GA version is the [20.0.0.12](https://openliberty.io/blog/2020/11/20/JNDI-gRPC-200012.html){: external} release.

    * The AdoptOpenJDK OpenJ9 alternate JRE is updated to version `11.0.10_9_openj9-0.24.0`.
    
    * The IBM JRE Version (8 SR 6 FP20) remains unchanged. 

## 15 January 2021
{: #cloud-foundry-public-jan1521}
{: release-note}

Updated Liberty buildpack v3.53-20210114-1605
:   The alternate Liberty runtime GA version is changed to the `21.0.0.1` release.

    * The default Liberty runtime GA version is the `20.0.0.12` release.

    * The AdoptOpenJDK OpenJ9 alternate JRE (11.0.9_11_openj9-0.23.0) and IBM JRE Version (8 SR 6 FP20) remains unchanged. 

## 17 December 2020
{: #cloud-foundry-public-dec1720}
{: release-note}

Updated Liberty buildpack v3.52-20201210-1626
:   The default and alternate Liberty runtime GA version is the [20.0.0.12](https://openliberty.io/blog/2020/11/20/JNDI-gRPC-200012.html) release.

    * The IBM JRE version is updated to 8 SR6 FP20. 

    * The IBM JRE 8 SR6 FP20 includes the following Oracle and IBM fixes: [CVE-2020-14792, CVE-2020-14797, CVE-2020-14781, CVE-2020-14779, CVE-2020-14798, CVE-2020-14796](https://www.ibm.com/support/pages/node/6370057)

    * The AdoptOpenJDK OpenJ9 alternate JRE (11.0.9_11_openj9-0.23.0) remains unchanged.

## 14 December 2020
{: #cloud-foundry-public-dec1420}
{: release-note}

Updated the ASP.NET Core buildpack v2.9-20201207-2154
:   This release includes version 2.3.19 of the `dotnet-core` Cloud Foundry buildpack.

    * Add support for .NET ASP.NET Core 5.0.0
    * Add support for .NET ASP.NET Core 3.1.10
    * Add support for .NET ASP.NET Core 3.1.9
    * Add support for .NET ASP.NET Core 2.1.23
    * Add support for .NET Runtime 5.0.0
    * Add support for .NET Runtime 3.1.10
    * Add support for .NET Runtime 3.1.9
    * Add support for .NET Runtime 2.1.23
    * Add support for .NET SDK 5.0.100
    * Add support for .NET SDK 3.1.404
    * Add support for .NET SDK 3.1.403
    * Add support for .NET SDK 2.1.811
    * Add support for .NET SDK 2.1.810
    * Remove support for .NET ASP.NET Core 3.1.8
    * Remove support for .NET ASP.NET Core 3.1.7
    * Remove support for .NET Runtime 3.1.8 
    * Remove support for .NET SDK 3.1.402
    * Update Node.js version to 10.23.0

## 2 December 2020
{: #cloud-foundry-public-dec0220}
{: release-note}

Updated Node.js buildpack v4.5-20201130-1530
:   The SDK for Node.js buildpack v4.5 is based on community buildpack v1.7.36, introduces v14 runtimes, and includes the following Node.js runtimes: v10.22.1, v10.23.0, v12.19.0, v12.19.1, v14.15.0, v14.15.1. The default runtime is the latest v10.x (currently 10.23.0). This buildpack is based on the community node.js buildpack [v1.7.36](https://github.com/cloudfoundry/nodejs-buildpack/releases/tag/v1.7.36).

    This release also includes CVE-2020-8201, CVE-2020-8251, CVE-2020-8252, CVE-2020-8277:

    * [September 2020 Security Releases](https://nodejs.org/en/blog/vulnerability/september-2020-security-releases/)

    * [November 2020 Security Releases](https://nodejs.org/en/blog/vulnerability/november-2020-security-releases/)

## 16 November 2020
{: #cloud-foundry-public-nov1620}
{: release-note}

Updated Liberty buildpack v3.51-20201113-1351
:   The default Liberty runtime GA version is the `20.0.0.12` release.

    * The alternate Liberty runtime GA version is changed to the `20.0.0.12` release.

    * The AdoptOpenJDK OpenJ9 alternate JRE was updated to version 11.0.9_11_openj9-0.23.0. 

    * The alternate Liberty runtime version `20.0.0.12` includes a fix for the [CVE-2020-10693 security vulnerability](https://www.ibm.com/support/pages/node/6348216){: external}.

    * The IBM JRE Version (8 SR 6 FP16) remains unchanged

## 22 October 2020
{: #cloud-foundry-public-oct2220}
{: release-note}

Updated Liberty buildpack v3.50-20201019-1521
:   The default Liberty runtime GA version is the [20.0.0.9](https://openliberty.io/blog/2020/08/28/graphql-apis-open-liberty-20009.html) release.

    * The alternate Liberty runtime GA version is the [20.0.0.11](https://openliberty.io/blog/2020/10/23/kerberos-grafana-200011.html) release.

    * The IBM JRE version is updated to 8 SR6 FP16.

## 15 October 2020
{: #cloud-foundry-public-oct1520}
{: release-note}

Updated Liberty buildpack v3.49.1-20201014-1251
:   The default Liberty runtime GA version is the [20.0.0.9](https://openliberty.io/blog/2020/08/28/graphql-apis-open-liberty-20009.html) release.

    * The alternate Liberty runtime GA version is the [20.0.0.10](https://openliberty.io/blog/2020/09/25/signed-certificate-with-acme-200010.html) release.

    * This buildpack contains a DB2 service fixing: 
     
        * Liberty incompatibility issue with updated DB2 paid plans. It will allow users to create the paid plan of the service and bind the application with new `VCAP` service format. 

## 2 October 2020
{: #cloud-foundry-public-oct0220}
{: release-note}

Updated Liberty buildpack v3.49-20200918-0244
:   The default Liberty runtime GA version is the [20.0.0.9](https://openliberty.io/blog/2020/08/28/graphql-apis-open-liberty-20009.html) release.

    * The default Liberty runtime version `20.0.0.9` includes a fix for the [CVE-2020-4590 security vulnerability](https://www.ibm.com/support/pages/node/6333623).

    * The alternate Liberty runtime GA version is changed to the [20.0.0.10](https://openliberty.io/blog/2020/09/25/signed-certificate-with-acme-200010.html) release.

    * AdoptOpenJDK and the IBM JRE Version (8 SR 6 FP15) is unchanged.

## 17 September 2020
{: #cloud-foundry-public-sep1720}
{: release-note}

Updated the ASP.NET Core buildpack v2.8-20200908-1929
:   This release includes version 2.3.13 of the `dotnet-core` Cloud Foundry buildpack.

    * Add support for .NET ASP.NET Core 3.1.8
    * Add support for .NET ASP.NET Core 3.1.7
    * Add support for .NET ASP.NET Core 2.1.22
    * Add support for .NET Runtime 3.1.8
    * Add support for .NET Runtime 2.1.22
    * Add support for .NET SDK 3.1.402
    * Add support for .NET SDK 2.1.810
    * Remove support for .NET ASP.NET Core 3.1.4
    * Remove support for .NET ASP.NET Core 2.1.18
    * Remove support for .NET Runtime 3.1.4
    * Remove support for .NET SDK 3.1.202
    * Remove support for .NET SDK 2.1.806
    * Update Node.js version to 10.22.1

## 8 September 2020
{: #cloud-foundry-public-sep0820}
{: release-note}

Updated Node.js buildpack v4.4-20200828-1028
:   The SDK for Node.js buildpack v4.4 provides Node.js community runtime versions v10.21.0, v.10.22.0, v12.18.2, v12.18.3. The default is latest 10.x, so it is currently 10.21.0.  This buildpack is based on the community node.js buildpack [v1.7.26](https://github.com/cloudfoundry/nodejs-buildpack/tree/v1.7.26). 

## 26 August 2020
{: #cloud-foundry-public-aug2620}
{: release-note}

Updated Liberty buildpack v3.48-20200821-1648
:   The default Liberty runtime GA version is the `20.0.0.9` release.

    * The alternate Liberty runtime GA version is changed to the `20.0.0.9` release.

    * The IBM JRE version is updated to 8 SR6 FP15.

    * The IBM JRE 8 SR6 FP15 includes fixes for the following three PSIRTs: 
        * [CVE-2020-2590](https://www.ibm.com/blogs/psirt/security-bulletin-cve-2020-2590-may-affect-ibm-sdk-java-technology-edition/) was disclosed as part of the Oracle January 2020 Critical Patch Update.
        
        * [CVE-2020-2601](https://www.ibm.com/blogs/psirt/security-bulletin-cve-2020-2601-may-affect-ibm-sdk-java-technology-edition/) was also  disclosed as part of the Oracle January 2020 Critical Patch Update.
    
        * IBM SDK, Java Technology Edition [Quarterly CPU - Jul 2020](https://www.ibm.com/blogs/psirt/security-bulletin-ibm-sdk-java-technology-edition-quarterly-cpu-jul-2020-includes-oracle-jul-2020-cpu-plus-one-additional-vulnerability-affects-content-collecor-for-sap-applications/).

## 29 July 2020
{: #cloud-foundry-public-jul2920}
{: release-note}

Updated Liberty buildpack v3.47-20200723-1022
:   The default Liberty runtime GA version is the [20.0.0.6](https://openliberty.io/blog/2020/06/05/graphql-open-liberty-20006.html){: external} release.

    * The alternate Liberty runtime GA version was changed to the 20.0.0.8 release.

    * The {{site.data.keyword.IBM_notm}} JRE version was updated to 8 SR6 FP11.

    * The AdoptOpenJDK OpenJ9 alternate JRE was updated to version 11.0.8_10_openj9-0.21.0.

## 7 July 2020
{: #cloud-foundry-public-jul0720}
{: release-note}

Updated Liberty buildpack v3.46-20200626-1029
:   The default Liberty runtime GA version is the [20.0.0.6](https://openliberty.io/blog/2020/06/05/graphql-open-liberty-20006.html){: external} release.

    * The alternate Liberty runtime GA version was changed to [20.0.0.7](https://openliberty.io/blog/2020/07/02/disable-default-cookies-20007.html){: external} release.

## 18 June 2020
{: #cloud-foundry-public-jun1820}
{: release-note}

Updated the ASP.NET Core buildpack v2.7-20200615-1457
:   This release includes version 2.3.11 of the `dotnet-core` Cloud Foundry buildpack.

    * Add support for .NET ASP.NET Core 2.1.18
    * Add support for .NET ASP.NET Core 3.1.4
    * Add support for .NET Runtime 3.1.4
    * Add support for .NET SDK 2.1.701
    * Add support for .NET SDK 2.1.806
    * Add support for .NET SDK 3.1.202
    * Remove support for .NET ASP.NET Core 3.1.2
    * Remove support for .NET ASP.NET Core 2.1.16
    * Remove support for .NET Runtime 2.1.16
    * Remove support for .NET SDK 2.1.804
    * Remove support for .NET SDK 3.1.200
    * Update Node.js version to 10.21.0


## 8 June 2020
{: #cloud-foundry-public-jun0820}
{: release-note}

Updated Node.js buildpack v4.3-20200606-1928
:   The SDK for Node.js buildpack v4.3 provides Node.js community runtime versions v10.20.1, v10.21.0, v12.17.0, v12.18.0. The default is latest 10.x, so it is currently 10.21.0.  This buildpack is based on the community node.js buildpack [v1.7.20](https://github.com/cloudfoundry/nodejs-buildpack/tree/v1.7.20){: external}.  

    This release also includes CVE-2020-8172, CVE-2020-11080, CVE-2020-8174 and CVE-2020-10531: [June 2020 Security Releases](https://nodejs.org/en/blog/vulnerability/june-2020-security-releases/){: external}


## 5 June 2020
{: #cloud-foundry-public-jun0520}
{: release-note}

Updated Liberty buildpack v3.45-20200601-1056
:   The default Liberty runtime GA version is the [20.0.0.6](https://openliberty.io/blog/2020/06/05/graphql-open-liberty-20006.html){: external} release.

    * The alternate Liberty runtime GA version was changed to `20.0.0.6` release

    * The {{site.data.keyword.IBM_notm}} JRE version was updated to 8 SR6 FP10.

## 4 May 2020
{: #cloud-foundry-public-may0420}
{: release-note}

Updated Liberty buildpack v.3.44-20200430-1451
:   The default Liberty runtime version is the [20.0.0.3](https://openliberty.io/blog/2020/03/13/access-specific-kafka-properties-samesite-20003.html){: external} release.

    * The alternate Liberty runtime version was changed to 20.0.0.5 release

    * The AdoptOpenJDK OpenJ9 alternate JRE was updated to version 11.0.7_10_openj9-0.20.0

    * The default Liberty runtime version `20.0.0.3` includes a fix for the [CVE-2020-4303 security vulnerability](https://www.ibm.com/support/pages/node/6147195){: external}.

## 1 May 2020
{: #cloud-foundry-public-may0120}
{: release-note}

Updated the ASP.NET Core buildpack v2.6-20200424-1047
:   This release includes version 2.3.9 of the `dotnet-core` Cloud Foundry buildpack.

    * Add support for .NET ASP.NET Core 2.1.16
    * Add support for .NET ASP.NET Core 2.1.17
    * Add support for .NET ASP.NET Core 3.1.2
    * Add support for .NET ASP.NET Core 3.1.3
    * Add support for .NET Runtime 2.1.16
    * Add support for .NET Runtime 2.1.17
    * Add support for .NET Runtime 3.1.3
    * Add support for .NET SDK 2.1.403
    * Add support for .NET SDK 2.1.508
    * Add support for .NET SDK 2.1.509
    * Add support for .NET SDK 2.1.605
    * Add support for .NET SDK 2.1.606
    * Add support for .NET SDK 2.1.804
    * Add support for .NET SDK 2.1.805
    * Add support for .NET SDK 3.1.200
    * Add support for .NET SDK 3.1.201
    * Remove support for .NET ASP.NET Core 2.1.12
    * Remove support for .NET ASP.NET Core 2.1.13
    * Remove support for .NET ASP.NET Core 2.2.6
    * Remove support for .NET ASP.NET Core 2.2.7
    * Remove support for .NET ASP.NET Core 3.0.0
    * Remove support for .NET Runtime 2.1.12
    * Remove support for .NET Runtime 2.1.13
    * Remove support for .NET Runtime 2.2.6
    * Remove support for .NET Runtime 2.2.7
    * Remove support for .NET Runtime 3.0.0
    * Remove support for .NET Runtime 2.2.6
    * Remove support for .NET SDK 2.1.701
    * Remove support for .NET SDK 2.1.802
    * Remove support for .NET SDK 2.2.301
    * Remove support for .NET SDK 2.2.402
    * Remove support for .NET SDK 3.0.100
    * Update Node.js version to 10.20.1

## 21 April 2020
{: #cloud-foundry-public-apr2120}
{: release-note}

Updated Node.js buildpack v4.2.1-20200420-1206
:   The SDK for Node.js buildpack v4.2.1 provides Node.js community versions v10.19.0, v10.20.1, v12.16.1, v12.16.2. The default is latest 10.x, so it is currently 10.20.1.  This buildpack is based on the community node.js buildpack [v1.7.17](https://github.com/cloudfoundry/nodejs-buildpack/tree/v1.7.17){: external}.  

    This release also includes CVE-2019-1551.

## 8 April 2020
{: #cloud-foundry-public-apr0820}
{: release-note}

Updated Liberty buildpack v3.43-20200406-1631
:   The default Liberty runtime version is the [20.0.0.3](https://openliberty.io/blog/2020/03/13/access-specific-kafka-properties-samesite-20003.html){: external} release.

    * The alternate Liberty runtime version was changed to the [20.0.0.4](https://openliberty.io/blog/2020/04/09/microprofile-3-3-open-liberty-20004.html){: external} release.

    * The {{site.data.keyword.IBM_notm}} JRE version was updated to 8 SR6 FP7.

    * The {{site.data.keyword.IBM_notm}} JRE 8 SR6 FP7 includes [CVE-2020-2654](https://www.ibm.com/support/pages/node/5736807){: external}.

## 11 March 2020
{: #cloud-foundry-public-mar1120}
{: release-note}

Updated Liberty buildpack v3.42-20200306-1144
:   The default Liberty runtime GA version was changed to the `20.0.0.3` release.

    * The alternate Liberty runtime GA version is also the `20.0.0.3` release.

    * GC logging is enabled by default and logs are stored in `/home/vcap/logs`.

## 2 March 2020
{: #cloud-foundry-public-mar0220}
{: release-note}

Updated Node.js buildpack v4.2
:   The SDK for Node.js buildpack v4.2 provides Node.js community versions v10.18.1, v10.19.0, v12.16.0, v12.16.1. The default is latest 10.x, so it is currently 10.19.0.  This buildpack is based on the community node.js buildpack [v1.7.13](https://github.com/cloudfoundry/nodejs-buildpack/tree/v1.7.13){: external}.  

    Beginning with this buildpack, the Node.js v8.x runtimes are no longer included.   
    {: important}

    This release also includes CVE-2019-15605, CVE-2019-15606, CVE-2019-15604: [February 2020 Security Releases](https://nodejs.org/en/blog/vulnerability/february-2020-security-releases/){: external}

## 7 February 2020
{: #cloud-foundry-public-feb0720}
{: release-note}

Updated Liberty buildpack v3.41-20200207-0830
:   The default Liberty runtime GA version is [19.0.0.12](https://openliberty.io/blog/2019/12/06/microprofile-32-health-metrics-190012.html){: external} release.

    * The alternate Liberty runtime GA version [20.0.0.2](https://openliberty.io/blog/2020/02/14/preview-microprofile-3-3-20002.html){: external} was added.

    * The alternate Liberty runtime version `20.0.0.2` includes a fix for the [CVE-2019-12406 security vulnerability](https://www.ibm.com/support/pages/node/1288774){: external}.

    * The alternate Liberty runtime version `20.0.0.2` includes a fix for the [CVE-2019-4720 security vulnerability]( https://www.ibm.com/support/pages/node/1285372){: external}.

    To use the alternate Liberty runtime set the following environment variables:

    ```text
    ibmcloud cf set-env <appName> JBP_CONFIG_LIBERTY "version: +"
    ibmcloud cf set-env <appName> IBM_LIBERTY_MONTHLY true
    ```
    {: codeblock}

    * The {{site.data.keyword.IBM_notm}} JRE version was updated to 8 SR6FP5.

    * The AdoptOpenJDK OpenJ9 alternate JRE was updated to version 11.0.6_10_openj9-0.18.1.

## 9 January 2020
{: #cloud-foundry-public-jan0920}
{: release-note}

Updated Liberty buildpack v3.40-20200108-1523
:   The default Liberty runtime GA version is [19.0.0.12](https://openliberty.io/blog/2019/12/06/microprofile-32-health-metrics-190012.html){: external} release.

    * The alternate Liberty runtime GA version [20.0.0.1](https://openliberty.io/blog/2020/01/17/openshift-oauth-server-social-login-liberty-20001.html){: external} was added.

    * The {{site.data.keyword.IBM_notm}} JRE version was updated to 8 SR6.

## 18 December 2019
{: #cloud-foundry-public-dec1820}
{: release-note}

Updated the ASP.NET Core buildpack v2.5-20191209-1920
:   This release includes version 2.3.2 of the `dotnet-core` Cloud Foundry buildpack.

    * Add support for .NET ASP.NET Core 2.1.13
    * Add support for .NET ASP.NET Core 2.1.14
    * Add support for .NET ASP.NET Core 2.2.7
    * Add support for .NET ASP.NET Core 2.2.8
    * Add support for .NET ASP.NET Core 3.0.1
    * Add support for .NET Runtime 2.1.13
    * Add support for .NET Runtime 2.1.14
    * Add support for .NET Runtime 2.2.7
    * Add support for .NET Runtime 2.2.8
    * Add support for .NET Runtime 3.0.1
    * Add support for .NET SDK 2.1.509
    * Add support for .NET SDK 2.1.606
    * Add support for .NET SDK 2.1.802
    * Add support for .NET SDK 2.2.402
    * Add support for .NET SDK 3.0.100
    * Add support for .NET SDK 3.0.101
    * Remove support for .NET ASP.NET Core 2.1.5
    * Remove support for .NET ASP.NET Core 2.1.11
    * Remove support for .NET ASP.NET Core 2.1.12
    * Remove support for .NET ASP.NET Core 2.2.5
    * Remove support for .NET ASP.NET Core 2.2.6
    * Remove support for .NET ASP.NET Core 3.0.0-preview7.19365.7
    * Remove support for .NET Runtime 2.1.5
    * Remove support for .NET Runtime 2.1.11
    * Remove support for .NET Runtime 2.1.12
    * Remove support for .NET Runtime 2.2.5
    * Remove support for .NET Runtime 2.2.6
    * Remove support for .NET Runtime 3.0.0-preview7-27912-14
    * Remove support for .NET SDK 2.1.801
    * Remove support for .NET SDK 2.2.205
    * Remove support for .NET SDK 2.2.401
    * Remove support for .NET SDK 3.0.100-preview7-012821
    * Update Node.js version to 10.17.0


## 11 December 2019
{: #cloud-foundry-public-dec1120}
{: release-note}

Updated Node.js buildpack v4.1
:   The SDK for Node.js buildpack v4.1 provides Node.js community versions v8.16.1, v8.16.2, v10.16.3, v10.17.0, v12.11.1, v12.13.0. The default is latest 10.x, so it is currently 10.17.0.  This buildpack is based on the community node.js buildpack [v1.7.3](https://github.com/cloudfoundry/nodejs-buildpack/releases/tag/v1.7.3){: external}.  


## 21 November 2019
{: #cloud-foundry-public-nov2119}
{: release-note}

Updated Liberty buildpack v3.39-20191121-1047
:   The default Liberty runtime GA version was changed to the [19.0.0.12](https://openliberty.io/blog/2019/12/06/microprofile-32-health-metrics-190012.html){: external} release.

    * The alternate Liberty runtime GA version is also the `19.0.0.12` release.

## 6 November 2019
{: #cloud-foundry-public-nov0619}
{: release-note}

Updated Liberty buildpack v3.38-20191031-1433
:   The default Liberty runtime GA version is [19.0.0.9](https://openliberty.io/blog/2019/12/06/microprofile-32-health-metrics-190012.html){: external} release.

    * The alternate Liberty runtime GA version `19.0.0.11` was added.

    * The AdoptOpenJDK OpenJ9 alternate JRE was updated to version 11.0.5+10_openj9-0.17.0.

## 11 October 2019
{: #cloud-foundry-public-oct1119}
{: release-note}

Updated Liberty buildpack v3.37-20191002-1726
:   The default Liberty runtime GA version is [19.0.0.9](https://openliberty.io/blog/2019/09/13/microprofile-reactive-messaging-19009.html){: external} release.

    * The alternate Liberty runtime GA version [19.0.0.10](https://openliberty.io/blog/2019/10/11/configure-logs-JSON-format-190010.html){: external} was added.

    * The {{site.data.keyword.IBM_notm}} JRE version was updated to 8 SR5 FP41.


## 24 September 2019
{: #cloud-foundry-public-sep2419}
{: release-note}

Updated Node.js buildpack v4.0
:   The SDK for Node.js buildpack v4.0 provides Node.js community versions v8.16.0, v8.16.1, v10.16.0, v10.16.3, v12.7.0, v12.8.1. The default is latest 10.x, so it is currently 10.16.0.  

    The `sdk-for-nodejs` buildpack was re-based on the community node.js buildpack v1.6.53 and contains some [important changes](https://www.ibm.com/cloud/blog/upcoming-important-changes-to-the-sdk-for-nodejs-buildpack){: external}.
    {: important}

    In addition, this buildpack contains fixes for the following security vulnerabilities:  CVE-2019-9516 CVE-2019-9515 CVE-2019-9518 CVE-2019-9517 CVE-2019-9512 CVE-2019-9511 CVE-2019-9514 CVE-2019-9513.

## 20 September 2019
{: #cloud-foundry-public-sep2019}
{: release-note}

Updated the ASP.NET Core buildpack v2.4-20190912-1554
:   This release includes version 2.2.14 of the `dotnet-core` Cloud Foundry buildpack.

    * Add support for .NET ASP.NET Core 2.1.12
    * Add support for .NET ASP.NET Core 2.2.6
    * Add support for .NET ASP.NET Core 3.0.0-preview7.19365.7
    * Add support for .NET Runtime 2.1.12
    * Add support for .NET Runtime 2.2.6
    * Add support for .NET Runtime 3.0.0-preview7-27912-14
    * Add support for .NET SDK 2.1.508
    * Add support for .NET SDK 2.1.605
    * Add support for .NET SDK 2.1.701
    * Add support for .NET SDK 2.1.801
    * Add support for .NET SDK 2.2.205
    * Add support for .NET SDK 2.2.301
    * Add support for .NET SDK 2.2.401
    * Add support for .NET SDK 3.0.100-preview7-012821
    * Remove support for .NET ASP.NET Core 2.1.10
    * Remove support for .NET ASP.NET Core 2.2.4
    * Remove support for .NET Runtime 1.0.15
    * Remove support for .NET Runtime 1.1.12
    * Remove support for .NET Runtime 1.1.13
    * Remove support for .NET Runtime 2.1.10
    * Remove support for .NET Runtime 2.2.4
    * Remove support for .NET SDK 1.1.13
    * Remove support for .NET SDK 1.1.14
    * Remove support for .NET SDK 2.1.507
    * Remove support for .NET SDK 2.2.107
    * Remove support for .NET SDK 2.2.203
    * Remove support for .NET SDK 2.2.204
    * Update Node.js version to 10.16.3

## 13 September 2019
{: #cloud-foundry-public-sep1319}
{: release-note}

Updated Liberty buildpack v3.36-20190905-1704
:   The default Liberty runtime GA version was changed to the [19.0.0.9](https://openliberty.io/blog/2019/09/13/microprofile-reactive-messaging-19009.html){: external} release.

    * The alternate Liberty runtime GA version is also the `19.0.0.9` release.

    * The {{site.data.keyword.IBM_notm}} JRE version was updated to 8 SR5 FP40.

## 17 August 2019
{: #cloud-foundry-public-aug1719}
{: release-note}

Updated Liberty buildpack v3.35
:   The default Liberty runtime GA version is [19.0.0.6](https://openliberty.io/blog/2019/06/21/microprofile-rest-client-19006.html){: external}.

    * The alternate Liberty runtime GA version `19.0.0.8` was added.

    * The default JRE is {{site.data.keyword.IBM_notm}} Small footprint JRE version 8 SR5 FP37.
    
    * The AdoptOpenJDK OpenJ9 alternate JRE was updated to version 11.0.4+11_openj9-0.15.1.

## 18 July 2019
{: #cloud-foundry-public-jul1819}
{: release-note}

Updated Liberty buildpack v3.34
:   The default Liberty runtime GA version is [19.0.0.6](https://openliberty.io/blog/2019/06/21/microprofile-rest-client-19006.html){: external}.

    * The alternate Liberty runtime GA version is [19.0.0.7](https://openliberty.io/blog/2019/07/18/microprofile-30-developer-experience.html){: external} was added.

    * The {{site.data.keyword.IBM_notm}} JRE version was updated to 8 SR5 FP37.

    * The OpenJ9 version 11.03 alternate JRE was updated to version 11.0.3+7_openj9-0.14.3.

## 16 July 2019
{: #cloud-foundry-public-jul1619}
{: release-note}

Updated Node.js buildpack v3.28
:   The SDK for Node.js buildpack v3.28 provides {{site.data.keyword.IBM_notm}} SDK for Node.js versions 4.8.5, 4.8.7 and Node.js community versions 8.15.1, 8.16.1, 10.15.0, 10.16.0 and 12.5.0. The default is latest 10.x, so it is currently 10.16.0.  

## 21 June 2019
{: #cloud-foundry-public-jun2119}
{: release-note}

Updated ASP.NET Core buildpack v2.3-20190609-2145
:   This release includes version 2.2.12 of the `dotnet-core` Cloud Foundry buildpack.

    * Add support for .NET ASP.NET Core 2.1.5
    * Add support for .NET ASP.NET Core 2.1.10
    * Add support for .NET ASP.NET Core 2.1.11
    * Add support for .NET ASP.NET Core 2.2.4
    * Add support for .NET ASP.NET Core 2.2.5
    * Add support for .NET Runtime 1.1.12
    * Add support for .NET Runtime 1.1.13
    * Add support for .NET Runtime 2.1.5
    * Add support for .NET Runtime 2.1.10
    * Add support for .NET Runtime 2.1.11
    * Add support for .NET Runtime 2.2.4
    * Add support for .NET Runtime 2.2.5
    * Add support for .NET SDK 1.1.13
    * Add support for .NET SDK 1.1.14
    * Add support for .NET SDK 2.1.507
    * Add support for .NET SDK 2.2.107
    * Add support for .NET SDK 2.2.203
    * Add support for .NET SDK 2.2.204
    * Remove support for .NET ASP.NET Core 2.1.7
    * Remove support for .NET ASP.NET Core 2.1.8
    * Remove support for .NET ASP.NET Core 2.2.1
    * Remove support for .NET ASP.NET Core 2.2.2
    * Remove support for .NET Runtime 1.0.11
    * Remove support for .NET Runtime 1.0.12
    * Remove support for .NET Runtime 1.1.10
    * Remove support for .NET Runtime 1.1.11
    * Remove support for .NET Runtime 2.0.7
    * Remove support for .NET Runtime 2.0.9
    * Remove support for .NET Runtime 2.1.7
    * Remove support for .NET Runtime 2.1.8
    * Remove support for .NET Runtime 2.2.1
    * Remove support for .NET Runtime 2.2.2
    * Remove support for .NET SDK 1.0.4
    * Remove support for .NET SDK 1.1.11
    * Remove support for .NET SDK 1.1.12
    * Remove support for .NET SDK 2.1.504
    * Remove support for .NET SDK 2.2.104
    * Update Node.js version to 10.15.2`

## 14 June 2019
{: #cloud-foundry-public-jun1419}
{: release-note}

Updated Liberty buildpack v3.33-20190619-1058
:   The default Liberty runtime GA version was changed to the [19.0.0.6](https://openliberty.io/blog/2019/06/21/microprofile-rest-client-19006.html){: external} release.

    * The alternate Liberty runtime GA version is also the `19.0.0.6` release.

    * The {{site.data.keyword.IBM_notm}} JRE version was updated to 8 SR5 FP36.

## 31 May 2019
{: #cloud-foundry-public-may3119}
{: release-note}

Updated Node.js buildpack v3.27
:   The SDK for Node.js buildpack v3.27 provides {{site.data.keyword.IBM_notm}} SDK for Node.js versions 4.8.5, 4.8.7 and Node.js community versions 6.17.0, 6.17.1, 8.15.1, 8.16.1, 10.15.0 and 10.16.0. The default is latest 6.x, so it is currently 6.17.1.  This is the last SDK for Node.js buildpack that includes v6.x runtimes.  

## 17 May 2019
{: #cloud-foundry-public-may1719}
{: release-note}

Updated Liberty buildpack v3.32-20190523-1138
:   The default Liberty runtime GA version is [19.0.0.3](https://openliberty.io/blog/2019/03/28/microprofile22-liberty-19003.html){: external}.

    * The alternate Liberty runtime GA version [19.0.0.5](https://openliberty.io/blog/2019/05/24/java11-hotspot-19005.html){: external} was added.  

    * The {{site.data.keyword.IBM_notm}} JRE version was updated to 8 SR5 FP35.

    * The OpenJ9 version 11.03 was added as an alternate JRE.  

## 26 April 2019
{: #cloud-foundry-public-apr2619}
{: release-note}

Updated Liberty buildpack v3.31-20190423-1354
:   The default Liberty runtime GA version is [19.0.0.3](https://openliberty.io/blog/2019/03/28/microprofile22-liberty-19003.html){: external}.

    * The alternate Liberty runtime GA version [19.0.0.4](https://openliberty.io/blog/2019/04/26/reactive-microservices-microprofile-19004.html){: external} was added.  

    * The auto-scaling agent was updated.

    * The {{site.data.keyword.IBM_notm}} JRE version was updated to 8 SR5 FP31.  

    * Possible breaking change: Review the [Potential WebSphere App Server problems when deployed behind a WebSphere-aware proxy server](https://www.ibm.com/support/pages/node/879485){: external} document to determine if your app is affected. This document includes the steps that are needed to resolve the issue. To resolve the issue, you will need to add a `httpDispatcher` directive with the `trustedSensitiveHeaderOrigin` attribute set to "*" and `enableWelcomePage` set to "false" to the `server.xml` file.

## 1 April 2019
{: #cloud-foundry-public-apr0119}
{: release-note}

Updated Liberty buildpack v3.30-20190325-1301
:   The default Liberty runtime GA version was changed to the [19.0.0.3](https://openliberty.io/blog/2019/03/28/microprofile22-liberty-19003.html){: external} release.

    * The alternate Liberty runtime GA version is also the `19.0.0.3` release.  

    * The Cloudant client libraries were updated to 2.15.0.

    * The {{site.data.keyword.IBM_notm}} JRE version was updated to 8 SR5 FP30.  

    * Possible breaking change: Review the [Potential WebSphere App Server problems when deployed behind a WebSphere-aware proxy server](https://www.ibm.com/support/pages/node/879485){: external} document to determine if your app is affected. This document includes the steps that are needed to resolve the issue. To resolve the issue, you will need to add a `httpDispatcher` directive with the `trustedSensitiveHeaderOrigin` attribute set to "*" and `enableWelcomePage` set to "false" to the `server.xml` file.

## 20 March 2019
{: #cloud-foundry-public-mar2019}
{: release-note}

Updated ASP.NET Core buildpack v2.2-20190319-1114
:   This release includes version 2.2.7 of the `dotnet-core` Cloud Foundry buildpack.

    * Add support for .NET ASP.NET Core 2.1.7
    * Add support for .NET ASP.NET Core 2.1.8
    * Add support for .NET ASP.NET Core 2.2.1
    * Add support for .NET ASP.NET Core 2.2.2
    * Add support for .NET Runtime 1.1.11
    * Add support for .NET Runtime 2.1.7
    * Add support for .NET Runtime 2.1.8
    * Add support for .NET Runtime 2.2.1
    * Add support for .NET Runtime 2.2.2
    * Add support for .NET SDK 1.1.12
    * Add support for .NET SDK 2.1.504
    * Add support for .NET SDK 2.2.104
    * Remove support for .NET ASP.NET Core 2.1.5
    * Remove support for .NET ASP.NET Core 2.1.4
    * Remove support for .NET ASP.NET Core 2.1.2
    * Remove support for .NET Runtime 1.1.9
    * Remove support for .NET Runtime 2.1.2
    * Remove support for .NET Runtime 2.1.4
    * Remove support for .NET Runtime 2.1.5
    * Remove support for .NET SDK 1.1.10
    * Remove support for .NET SDK 2.1.302
    * Update Node.js version to 6.17.0

## 18 March 2019
{: #cloud-foundry-public-mar1819}
{: release-note}

Updated Node.js buildpack v3.26
:   The SDK for Node.js buildpack v3.26 provides {{site.data.keyword.IBM_notm}} SDK for Node.js versions 4.8.5, 4.8.7 and Node.js community versions 6.16.0, 6.17.0, 8.15.0, 8.15.1, 10.15.0 and 10.15.3. The default is latest 6.x, so it is currently 6.17.0.


## 1 March 2019
{: #cloud-foundry-public-mar0119}
{: release-note}

Updated Liberty buildpack v3.29-20190223-2128
:   The default Liberty runtime GA version is the [18.0.0.4](https://openliberty.io/blog/2018/12/14/microprofile21-18004.html){: external} release.

    * The alternate Liberty runtime GA version [19.0.0.2](https://openliberty.io/blog/2019/03/01/sharding-keys-jdbc43-19002.html){: external} was added.  
    
    * The Cloudant client libraries were updated to 2.14.0.

## 1 February 2019
{: #cloud-foundry-public-feb0119}
{: release-note}

Updated Liberty buildpack v3.28-20190127-1723
:   The default Liberty runtime GA version is the [18.0.0.4](https://openliberty.io/blog/2018/12/14/microprofile21-18004.html){: external} release.

    * The alternate Liberty runtime GA version [19.0.0.1](https://openliberty.io/blog/2019/02/01/open-liberty-19001.html){: external} was added.  

    * The monthly Liberty beta release has been removed.  

    * The {{site.data.keyword.IBM_notm}} JRE version was updated to 8 SR5 FP27.

    * The MQ client was updated to the 9.1.0.0 release.

    * The auto-scaling agent was updated.

## 23 January 2019
{: #cloud-foundry-public-jan2319}
{: release-note}

Updated Node.js buildpack v3.25.1
:   The SDK for Node.js buildpack v3.25.1 provides {{site.data.keyword.IBM_notm}} SDK for Node.js versions 4.8.5, 4.8.7 and Node.js community versions 6.14.4, 6.16.0, 8.11.4, 8.15.0, 10.10.0 and 10.15.0. The default is latest 6.x, so it is currently 6.16.0. The versions 6.15.0, 8.14.0 and 10.14.0 that were included in the last buildpack had a regression. The regressions has been fixed in 6.16.0, 8.15.0 and 10.15.0 which are now included instead.

## 7 January 2019
{: #cloud-foundry-public-jan0719}
{: release-note}

Updated Node.js buildpack v3.25
:   The SDK for Node.js buildpack v3.25 provides {{site.data.keyword.IBM_notm}} SDK for Node.js versions 4.8.5, 4.8.7 and Node.js community versions 6.14.4, 6.15.0, 8.11.4, 8.14.0, 10.10.0 and 10.14.0. The default is latest 6.x, so it is currently 6.15.0. The buildpack also fixes a minor bug in the Dynatrace hook.

## 14 December 2018
{: #cloud-foundry-public-dec1418}
{: release-note}

Updated Liberty buildpack v3.27-20181130-1702
:   The buildpack now includes Java Platform, Enterprise Edition 8.0. Java EE 8 no longer needs to be installed when an app is pushed.  

    * The default Liberty runtime version was updated to the [18.0.0.4](https://openliberty.io/blog/2018/12/14/microprofile21-18004.html){: external} release.

    * The monthly Liberty runtime version was updated to the 2018.11.0.0 release.

    * The {{site.data.keyword.IBM_notm}} JRE version was updated to 8 SR5 FP26.

## 12 December 2018
{: #cloud-foundry-public-dec1218}
{: release-note}

Updated ASP.NET Core buildpack v2.1-20181205-1536
:   This release includes version 2.2.0 of the `dotnet-core` Cloud Foundry buildpack.

    * Add support for .NET ASP.NET Core 2.1.2
    * Add support for .NET ASP.NET Core 2.1.4
    * Add support for .NET ASP.NET Core 2.1.5
    * Add support for .NET Runtime 1.0.11
    * Add support for .NET Runtime 1.0.12
    * Add support for .NET Runtime 1.1.9
    * Add support for .NET Runtime 1.1.10
    * Add support for .NET Runtime 2.0.7
    * Add support for .NET Runtime 2.0.9
    * Add support for .NET Runtime 2.1.2
    * Add support for .NET Runtime 2.1.5
    * Add support for .NET SDK 1.0.4
    * Add support for .NET SDK 1.1.10
    * Add support for .NET SDK 1.1.11
    * Add support for .NET SDK 2.0.3
    * Add support for .NET SDK 2.1.302
    * Add support for .NET SDK 2.1.403
    * Remove support for .NET Framework 2.1.0
    * Remove support for .NET Framework 2.1.1
    * Remove support for .NET Framework 1.1.8
    * Remove support for .NET Core SDK 2.0.2
    * Remove support for .NET Core SDK 2.0.3
    * Remove support for .NET Core SDK 2.1.201
    * Remove support for .NET Core SDK 2.1.300
    * Remove support for .NET Core SDK 2.1.301
    * Update Node.js version to 6.14.4`

## 5 December 2018
{: #cloud-foundry-public-dec0518}
{: release-note}

Updated Node.js buildpack v3.24
:   The SDK for Node.js buildpack v3.24 provides {{site.data.keyword.IBM_notm}} SDK for Node.js versions 4.8.5, 4.8.7 and Node.js community versions 6.14.3, 6.14.4, 8.11.3, 8.11.4, 10.9.0 and 10.10.0. The default is latest 6.x, so it is currently 6.14.4. The buildpack also fixes a minor bug in the Dynatrace hook.

## 29 October 2018
{: #cloud-foundry-public-oct2918}
{: release-note}

Updated Liberty buildpack v3.26-20181023-1545
:   The default Liberty runtime version, `18.0.0.3`, was updated to include a fix for the [CVE-2014-7810 security vulnerability](https://www.ibm.com/support/pages/node/737055){: external}.

    * The monthly Liberty runtime version was updated to the 2018.10.0.0 release.

    * The {{site.data.keyword.IBM_notm}} JRE version was updated to 8 SR5 FP22.

## 21 September 2018
{: #cloud-foundry-public-sep2118}
{: release-note}

Updated Liberty buildpack v3.25-20180918-1034
:   The buildpack now supports Java Platform, Enterprise Edition 8.0. To use Java EE 8, install the `javaee-8.0` Liberty feature when you push your app. Learn more in [Install Liberty features](/docs/cloud-foundry-public?topic=cloud-foundry-public-install-features).

    * The default Liberty runtime version was updated to the 18.0.0.3 release.

    * The monthly Liberty runtime version was updated to [2018.8.0.1](https://developer.ibm.com/wasdev/blog/2018/08/31/reactive-rest-client-liberty-beta/){: external} release.

    * The {{site.data.keyword.IBM_notm}} JRE version was updated to 8 SR5 FP20.

## 20 September 2018
{: #cloud-foundry-public-sep2018}
{: release-note}

Updated ASP.NET Core buildpack v2.0-20180918-1356
:   Beginning with this release, the ASP.NET Core buildpack is based on the [Cloud Foundry .NET Core buildpack](https://docs.cloudfoundry.org/buildpacks/dotnet-core/index.html){: external}. This release includes version 2.1.3 of the `dotnet-core` Cloud Foundry buildpack.
{: important}

    * Add support for .NET Core SDK 1.1.9
    * Add support for .NET Core SDK 2.0.2
    * Add support for .NET Core SDK 2.0.3
    * Add support for .NET Core SDK 2.1.201
    * Add support for .NET Core SDK 2.1.300
    * Add support for .NET Core SDK 2.1.301
    * Add support for .NET Framework 1.0.11
    * Add support for .NET Framework 1.1.8
    * Add support for .NET Framework 2.0.7
    * Add support for .NET Framework 2.1.0
    * Add support for .NET Framework 2.1.1
    * Remove support for .NET Core SDK 1.1.0
    * Remove support for .NET Core SDK 1.0.0-preview2-003156
    * Remove support for .NET Core SDK 2.0.0
    * Remove support for .NET Core SDK 2.0.0-preview2-006497
    * Remove support for .NET Framework 1.0.4
    * Remove support for .NET Framework 1.1.1
    * Update Node.js version to 6.14.3
    * Change default .NET Core SDK 2.1.301

##  7 September 2018
{: #cloud-foundry-public-sep0718}
{: release-note}

Updated Node.js buildpack v3.22
:   Beginning with this buildpack, the SDK for Node.js buildpack includes the Node.js community release runtimes for version 6.x and 8.x. With this change, the Node.js OpenSSL FIPS module is no longer included in these versions of the buildpack. Only version 4.x continues to include the OpenSSL FIPS module.  
{: important}

    The SDK for Node.js buildpack v3.22 provides {{site.data.keyword.IBM_notm}} SDK for Node.js versions 4.8.5, 4.8.7 and Node.js community versions 6.14.3, 6.14.4, 8.11.3 and 8.11.4. The default is latest 6.x, so it is currently 6.14.4.

    This release also includes fixes for the following security vulnerability:
    
    * [CVE-2018-0732](https://www.ibm.com/support/pages/node/715089){: external}

##  10 August 2018
{: #cloud-foundry-public-aug1018}
{: release-note}

Updated Liberty buildpack v3.24-20180806-1313
:   The monthly Liberty runtime version was updated to 2018.8.0.0.

    * The {{site.data.keyword.IBM_notm}} JRE version was updated to 8 SR5 FP17.

## 24 July 2018
{: #cloud-foundry-public-jul2418}
{: release-note}

Updated Node.js buildpack v3.21
:   Beginning with the latest Node.js 6.x and 8.x versions in this release, the SDK for Node.js buildpack is based on the Node.js community release. With this change, the Node.js OpenSSL FIPS module in the buildpack will no longer be updated. The current OpenSSL FIPS module and {{site.data.keyword.IBM_notm}} SDK for Node.js builds are eligible for removal as of 24 August 2018. For more information, see the [Aligning the Node.js Buildpack to Community Runtimes](https://www.ibm.com/cloud/blog/announcements/aligning-the-node-js-buildpack-to-community-runtimes){: external} blog post.
{: important}

    The SDK for Node.js buildpack v3.21 provides {{site.data.keyword.IBM_notm}} SDK for Node.js versions 4.8.5, 4.8.7, 6.13.0 and 8.9.4 and Node.js community versions 6.14.3 and 8.11.3. The default is latest 6.x, so it is currently 6.14.3.

    This release also includes fixes for the following security vulnerability:

    * [CVE-2018-0739](https://www.ibm.com/support/pages/node/715221){: external}

## 2 July 2018
{: #cloud-foundry-public-jul0218}
{: release-note}

Updated Liberty buildpack v3.23-20180628-1052
:   The default Liberty runtime version was updated to the 18.0.0.2 release.

    * The {{site.data.keyword.IBM_notm}} JRE version was updated to 8 SR5 FP16.

## 8 June 2018
{: #cloud-foundry-public-jun0818}
{: release-note}

Updated Liberty buildpack v3.22-20180601-1200
:   The monthly Liberty runtime version was updated to 2018.6.0.0.

    * The {{site.data.keyword.IBM_notm}} JRE version was updated to 8 SR5 FP15.

## 1 June 2018
{: #cloud-foundry-public-jun0118}
{: release-note}

Updated Node.js buildpack v3.20.2
:   The SDK for Node.js buildpack v3.20.2 adds Dynatrace Managed PaaS integration for the current Node.js runtimes.

## 17 May 2018
{: #cloud-foundry-public-may1718}
{: release-note}

Updated Node.js buildpack v3.20.1
:   The SDK for Node.js buildpack v3.20.1 fixes Dynatrace PaaS integration for the current Node.js runtimes.

## 11 May 2018
{: #cloud-foundry-public-may1118}
{: release-note}

Updated Liberty buildpack v3.21-20180509-1456
:   The monthly Liberty runtime version was updated to 2018.5.0.0.

## 13 April 2018
{: #cloud-foundry-public-apr1318}
{: release-note}

Updated Liberty buildpack v3.20-20180409-1221
:   The monthly Liberty runtime version was updated to 2018.4.0.0.

    * The {{site.data.keyword.IBM_notm}} JRE version was updated to 8 SR5 FP11.

    * The auto-scaling agent was updated.

## 9 April 2018
{: #cloud-foundry-public-apr0918}
{: release-note}

Updated Node.js buildpack v3.20
:   The SDK for Node.js buildpack v3.20 adds Dynatrace PaaS integration for the current Node.js runtimes.

## 16 March 2018
{: #cloud-foundry-public-mar1618}
{: release-note}

Updated Liberty buildpack v3.19-20180313-1017
:   The default Liberty runtime version was updated to the 18.0.0.1 release.

    * The monthly Liberty runtime version was updated to 2018.3.0.0.

    * The {{site.data.keyword.IBM_notm}} JRE version was updated to 8 SR5 FP10.

    * The {{site.data.keyword.IBM_notm}} JRE version 7 was removed.  

    * The DB2 JDBC driver was updated to the `4.23.42` version.

Updated Node.js buildpack v3.19
:   The SDK for Node.js buildpack v3.19 provides {{site.data.keyword.IBM_notm}} SDK for Node.js versions 4.8.5, 4.8.7, 6.12.3, 6.13.0, 8.9.3 and 8.9.4. The default is latest 6.x, so it is currently 6.13.0.

## 13 February 2018
{: #cloud-foundry-public-feb1318}
{: release-note}

Updated Liberty buildpack v3.18-20180213-1234
:   The monthly Liberty runtime version was updated to 2018.2.0.0.

    * The default Liberty runtime also includes the [PI90804 Apache Commons interim fix](https://www.ibm.com/support/pages/node/301027){: external}.

## 6 February 2018
{: #cloud-foundry-public-feb0618}
{: release-note}

Updated Node.js buildpack v3.18
:   The SDK for Node.js buildpack v3.18 provides {{site.data.keyword.IBM_notm}} SDK for Node.js versions 4.8.5, 4.8.7, 6.12.2, 6.12.3, 8.9.3 and 8.9.4. The default is latest 6.x, so it is currently 6.12.3.

## 31 January 2018
{: #cloud-foundry-public-jan3118}
{: release-note}

Updated Liberty buildpack v3.17.1-20180131-1532
:   The buildpack includes Liberty feature `microProfile-1.2`.

## 26 January 2018
{: #cloud-foundry-public-jan2618}
{: release-note}

Updated Liberty buildpack v3.17-20180122-1037
:   The buildpack was updated to add the ability to dynamically set tracing on the Liberty server.

    * The monthly Liberty runtime version was updated to 2018.1.0.0.

    * The {{site.data.keyword.IBM_notm}} JRE version was updated to 8 SR5 FP7.

## 8 January 2018
{: #cloud-foundry-public-jan0818}
{: release-note}

Updated Node.js buildpack v3.17
:   The SDK for Node.js buildpack v3.17 provides {{site.data.keyword.IBM_notm}} SDK for Node.js versions 4.8.5, 4.8.7, 6.12.0, 6.12.2, 8.9.0 and 8.9.3. The default is latest 6.x, so it is currently 6.12.2.

## 5 January 2018
{: #cloud-foundry-public-jan0518}
{: release-note}

Updated Liberty buildpack v3.16-20180102-0938
:   The default Liberty runtime version was updated to the 17.0.0.4 release

    * The monthly Liberty runtime version was updated to 2017.12.0.0.

    * The {{site.data.keyword.IBM_notm}} JRE version was updated to 8 SR5 FP6.

## 11 December 2017
{: #cloud-foundry-public-dec1117}
{: release-note}

Updated Node.js buildpack v3.16.1
:   The SDK for Node.js buildpack v3.16.1 provides {{site.data.keyword.IBM_notm}} SDK for Node.js versions v4.8.4, v4.8.5, v6.11.4, v6.12.0, v8.6.0, v8.9.0. The default is latest 6.x, so it is currently 6.12.0.

    Please note that it fixes PSIRT Advisory ID: 10237 Product Record ID: 104487 Title: Node.js `zlib` DOS security vulnerability, October 2017 (CVE-2017-14919). It is recommended to upgrade to v3.16.1 to get fixes for security vulnerabilities affecting 8.6.0.0 and earlier, 6.10.2.0 to 6.11.4.0 and 4.8.2.0 to 4.8.4.0.

## 1 November 2017
{: #cloud-foundry-public-nov0117}
{: release-note}

Updated Node.js buildpack v3.15
:   The SDK for Node.js buildpack v3.15 provides {{site.data.keyword.IBM_notm}} SDK for Node.js versions 4.8.3, 4.8.4, 6.11.3, 6.11.4, 8.3.0 and 8.6.0. The default is latest 6.x, so it is currently 6.11.4.

## 31 October 2017
{: #cloud-foundry-public-oct3117}
{: release-note}

Updated Liberty buildpack v3.15
:   The monthly Liberty runtime version was updated to 2017.10.0.0.

## 17 October 2017
{: #cloud-foundry-public-oct1717}
{: release-note}

Updated Liberty buildpack v3.14-20171013-1023
:   The default Liberty runtime version was updated to the 17.0.0.3 release.

    * The monthly Liberty runtime version was updated to 2017.9.0.1.

    * The {{site.data.keyword.IBM_notm}} JRE version was updated to 8 SR5.

## 6 October 2017
{: #cloud-foundry-public-oct0617}
{: release-note}

Updated ASP.NET Core buildpack v1.0.26-20170913-1346
:   This release includes the following updates:

    * Add support for .NET Core runtime 2.0.0
    * Add support for .NET Core SDK 1.1.0
    * Add support for .NET Core SDK 2.0.0
    * Remove support for .NET Core SDK 1.1.0-preview1-005051
    * Remove support for .NET Core SDK 2.0.0-preview1-005977
    * Remove support for .NET Core runtime 1.0.3
    * Remove support for .NET Core runtime 1.1.0
    * Update Node version to 6.11.2
    * Change default .NET Core SDK to 2.0.0
    * Change default .NET Core SDK for F# projects to 1.1.0


## 5 October 2017
{: #cloud-foundry-public-oct0517}
{: release-note}

Updated Liberty buildpack v3.13-20170919-1721
:   The monthly Liberty runtime version was updated to 2017.9.0.0.

    * The {{site.data.keyword.IBM_notm}} JRE version was updated to 8 SR4 FP11.

    * The auto-scaling agent was updated.

## 20 September 2017
{: #cloud-foundry-public-sep2017}
{: release-note}

Updated Node.js buildpack v3.14
:   The SDK for Node.js buildpack v3.14 provides {{site.data.keyword.IBM_notm}} SDK for Node.js versions 4.8.3, 4.8.4, 6.11.2, 6.11.3, 8.1.4 and 8.3.0. The default is latest 6.x, so it is currently 6.11.3. A buildpack bug that prevented Node.js apps from [shutting down gracefully](https://docs.cloudfoundry.org/devguide/deploy-apps/app-lifecycle.html#shutdown){: external} was fixed in this release.

## 14 August 2017
{: #cloud-foundry-public-aug1417}
{: release-note}

Updated Liberty buildpack v3.12-20170814-1322
:   The monthly Liberty runtime version was updated to the [2017.8.0.0](https://developer.ibm.com/wasdev/blog/2017/08/04/beta-websphere-liberty-tools-august-2017/){: external} release.

    * The buildpack also contains updated {{site.data.keyword.IBM_notm}} JREs: version 8 SR4 FP10 and version 7.1 SR4 FP10.

    * JRE 8 includes Java Cryptography Extension (JCE) Unlimited Strength Jurisdiction Policy Files.

    * A buildpack bug that prevented Liberty apps from [shutting down gracefully](https://docs.cloudfoundry.org/devguide/deploy-apps/app-lifecycle.html#shutdown){: external} was fixed.

## 26 July 2017
{: #cloud-foundry-public-jul2617}
{: release-note}

Updated Node.js buildpack v3.13
:   The SDK for Node.js buildpack v3.13 provides {{site.data.keyword.IBM_notm}} SDK for Node.js versions 4.8.3, 4.8.4, 6.11.0, 6.11.1, 8.1.2 and 8.1.4. The default is latest 6.x, so it is currently 6.11.1. Please note that version 8 is available for testing but is not yet recommended for production.  

    This buildpack contains updated Node.js versions which address recent security vulnerabilities found in Node.js. Users should update their apps to use the latest versions available and then restage the apps in {{site.data.keyword.cloud_notm}}.  See [this security bulletin](http://www-01.ibm.com/support/docview.wss?uid=swg22006722){: external} for details on the CVE-2017-1000381 and CVE-2017-11499 fixes for Node.js security vulnerabilities.

## 26 July 2017
{: #cloud-foundry-public-jul2617}
{: release-note}

Updated ASP.NET Core buildpack v1.0.22-20170724-0813
:   This release includes the following updates:

    * Add support for .NET Core runtime 2.0.0 Preview 2
    * Add support for .NET Core SDK 1.1.0-preview1-005051
    * Add support for .NET Core SDK 2.0.0-preview2-006497
    * Update Node version to 6.11.1
    * Always make self-contained apps executable

## 14 July 2017
{: #cloud-foundry-public-jul1417}
{: release-note}

Updated Liberty buildpack v3.11-20170710-0312
:   The default Liberty runtime version `17.0.0.2` was updated to include the IFPI83713 interim fix.

    * The monthly Liberty runtime version was updated to the [2017.7.0.0](https://developer.ibm.com/wasdev/blog/2017/07/07/beta-websphere-liberty-tools-july-2017/){: external} release.

    * The buildpack also contains updated {{site.data.keyword.IBM_notm}} JREs: version 8 SR4 FP7 and version 7.1 SR4 FP5.

    * The default Cloudant Library is now the official [`java-cloudant`](https://github.com/cloudant/java-cloudant){: external}, the [Ektorp library](https://github.com/helun/Ektorp){: external} is still available as an option, for details about this change see the [blog post](https://www.ibm.com/blogs/bluemix/2017/05/default-library-change-cloudant-auto-wiring-liberty-buildpack/){: external}.

    * The default heap size ratio is now 50% when your app has less than 512mb of memory, if it has more than 512mb it will still be 75%.

    * A new staging task log is now generated, which allows for easier debugging of staging errors.

    * The Node.js runtime that is used by the [App Management utility](/docs/cloud-foundry-public?topic=cloud-foundry-public-app_management) was updated to the 6.13.0 version.

    * The buildpack also provides an updated agent for the Auto-Scaling service.

## 20 June 2017
{: #cloud-foundry-public-jun2017}
{: release-note}

Updated ASP.NET Core buildpack v1.0.20-20170620-1449
:   This release includes the following updates:

    * Add support for .NET Core runtime 2.0.0 Preview 1
    * Add support for .NET Core SDK 2.0.0-preview1-005977
    * Update Node version to 6.10.3
    * Remove support for .NET Core runtime version 1.0.0
    * Remove support for .NET Core runtime version 1.0.1
    * Remove support for .NET Core SDK version 1.0.0-preview2-1-003177
    * Add staging_task.log file to app container
    * Lower disk usage when caching dependencies

## 12 June 2017
{: #cloud-foundry-public-jun1217}
{: release-note}

Updated Liberty buildpack v3.10-20170525-1107
:   The default Liberty runtime version was updated to the 17.0.0.2 release.

    * The monthly Liberty runtime version was updated to the [2017.5.0.0](https://developer.ibm.com/wasdev/blog/2017/05/12/beta-websphere-liberty-tools-may-2017/){: external} release.

    * The Node.js runtime that is used by the [App Management utility](/docs/cloud-foundry-public?topic=cloud-foundry-public-app_management) was updated to the 6.10.0 version.

    * The buildpack also provides an updated version of the Extreme Scale Client.

## 12 May 2017
{: #cloud-foundry-public-may1217}
{: release-note}

Updated ASP.NET Core buildpack v1.0.18-20170516-1601
:   This release includes the following updates:

    * Add support for .NET Core runtime 1.0.5
    * Add support for .NET Core runtime 1.1.2
    * Add support for .NET Core SDK 1.0.3
    * Add support for .NET Core SDK 1.0.4
    * Update Node version to 6.10.2
    * Remove support for .NET Core SDK 1.0.1
    * Remove support for .NET Core SDK 1.0.0-preview4-004233
    * Use ASPNETCORE_URLS environment variable to specify port

## 5 May 2017
{: #cloud-foundry-public-may0517}
{: release-note}

Updated Node.js buildpack v3.12
:   The SDK for Node.js buildpack v3.12 provides {{site.data.keyword.IBM_notm}} SDK for Node.js versions 0.12.17, 0.12.18, 4.8.0, 4.8.2, 6.10.0 and 6.10.2. The default is now changed from the latest 4.x to latest 6.x, so it is currently 6.10.2. Being a major version change, this could affect apps that are relying on the default. See [Node.js version long-term support and the SDK for Node.js buildpack](https://www.ibm.com/blogs/bluemix/2016/11/node-version-support-and-sdk-buildpack/){: external} for more information about how to avoid any problems.

    In addition to the new runtimes, this release contains a buildpack bug fix an issue with the App Management Health Center handler and Node.js versions 6.9.5 and 6.10.0.

## 27 April 2017
{: #cloud-foundry-public-apr2717}
{: release-note}

Updated Liberty buildpack v3.9-20170419-1403
:   The default Liberty runtime version `17.0.0.1` was updated to include [PI77770](https://www.ibm.com/support/pages/node/589019){: external}, [PI77605](https://www.ibm.com/support/pages/apar/PI77605), [PI79275](https://www.ibm.com/support/pages/apar/PI79275){: external}, and PI77438 fixes.

    * The monthly Liberty runtime version was updated to the [2017.3.0.0](https://developer.ibm.com/wasdev/blog/2017/03/14/beta-websphere-liberty-tools-march-2017/){: external} release.

    * Memory Calculation was moved from staging to the start process, allowing for easier heap memory changes with the restart of an app.

    * The buildpack also provides updated versions of the agent for the Auto-Scaling service, and the Extreme Scale Client.

## 29 March 2017
{: #cloud-foundry-public-mar2917}
{: release-note}

Updated ASP.NET Core buildpack v1.0.13-20170330-1023
:   This release includes the following updates:

    * Add support for .NET Core runtime 1.0.4
    * Add support for .NET Core runtime 1.1.1
    * Add support for .NET Core SDK 1.0.1
    * Update Node version to 6.10.0
    * Remove support for .NET Core SDK 1.0.0-preview2-003131
    * Remove support for .NET Core SDK 1.0.0-preview3-004056

## 14 March 2017
{: #cloud-foundry-public-mar1417}
{: release-note}

Updated Liberty buildpack v3.8-20170308-1507
:   The default Liberty runtime version was updated to the 17.0.0.1 release.

    * The default Liberty runtime also includes the PI75512 WebSockets interim fix.

    * The monthly Liberty runtime version was updated to the [2017.2.0.0](https://developer.ibm.com/wasdev/blog/2017/02/17/beta-websphere-liberty-tools-february-2017/){: external} release.
    
    * The {{site.data.keyword.IBM_notm}} JRE versions 8 and 7.1 were updated to SR4 FP1.

    * The auto-configuration support was also extended to work with `ibm-websphere-extreme-scale` container.

    * The auto-configuration support for [Cloudant NoSQL Database](/docs/Cloudant?topic=Cloudant-getting-started-with-cloudant) was updated to provide the option of using the Cloudant Java Library instead of `org.ektorp`. To enable the use of the Cloudant Java Library you must set the following environment variable:    

        ```text
        ibmcloud cf set-env <appName> LBP_SERVICE_CONFIG_CLOUDANTNOSQLDB 'type : cloudant'
        ```
        {: codeblock}

    * The buildpack also provides an updated version of the agent for the Auto-Scaling service and a number of app management enhancements.

    * This buildpack also changes the way auto-configuration works for the Monitoring and Analytics service. Apps using the Free plan will no longer have the log capability added to their apps; it is being replaced by `logmet`.  

## 10 March 2017
{: #cloud-foundry-public-mar1017}
{: release-note}

Updated Node.js buildpack v3.11
:   This release of the buildpack supports {{site.data.keyword.IBM_notm}} SDK for Node.js runtime versions: 0.10.47, 0.10.48, 0.12.17, 0.12.18, 4.7.3, 4.8.0, 6.9.5, and 6.10.0. The default version now is 4.8.0.

    In addition to the new runtimes, this release contains a fix for a bug encountered when enabling the shell app management handler using the `devconsole` UI. This buildpack also changes the way auto-configuration works for the Monitoring and Analytics service. Apps using the Free plan will no longer have the log capability added to their apps, it is being replaced by `logmet`.

## 31 January 2017
{: #cloud-foundry-public-jan3117}
{: release-note}

Updated ASP.NET Core buildpack v1.0.10-20170124-1145
:   This release includes the following updates:

    * Add support for .NET Core 1.0.3
    * Add support for .NET Core MSBuild tooling
    * Add support for F# projects
    * Remove support for .NET Core SDK 1.0.0-preview2-003121

## 23 January 2017
{: #cloud-foundry-public-jan2317}
{: release-note}

Updated Liberty buildpack v3.7-20170118-2046
:   The monthly Liberty runtime version was updated to the [2017.1.0.0](https://developer.ibm.com/wasdev/blog/2017/01/20/beta-websphere-liberty-tools-january-2017/){: external} release.

    * The {{site.data.keyword.IBM_notm}} JRE version 8 was updated to SR3 FP22 version.

    * The [auto-configuration](/docs/cloud-foundry-public?topic=cloud-foundry-public-auto_config) support was also extended to work with the [Compose for MongoDB service](/docs/ComposeForMongoDB?topic=ComposeForMongoDB-about) (Currently only available with the monthly Liberty runtime).

## 20 January 2017
{: #cloud-foundry-public-jan2017}
{: release-note}

Updated Node.js buildpack v3.10
:   This release of the buildpack supports {{site.data.keyword.IBM_notm}} SDK for Node.js runtime versions: 0.10.47, 0.10.48, 0.12.17, 0.12.18, 4.7.0, 4.7.2, 6.9.2, and 6.9.4. The default is now 4.7.2.  It is also synchronized with the [Cloud Foundry Node.js buildpack v1.5.24](https://github.com/cloudfoundry/nodejs-buildpack/tree/v1.5.24){: external}.
It contains a fix for a bug where `npm start` was not always called to start apps.

## 13 December 2016
{: #cloud-foundry-public-dec1316}
{: release-note}

Updated Liberty buildpack v3.6-20161209-1351
:   The default Liberty runtime version was updated to the [16.0.0.4](https://www.ibm.com/support/pages/node/715555){: external} release.

    * The {{site.data.keyword.IBM_notm}} JRE version 8 was updated to SR3 FP21 version.

    * The [auto-configuration](/docs/cloud-foundry-public?topic=cloud-foundry-public-auto_config) support was also extended to work with the [Compose for PostgreSQL service](/docs/ComposeForPostgreSQL?topic=ComposeForPostgreSQL-about).
    
    *  The buildpack also provides an updated version of the agent for the Auto-Scaling service.
    
    * The buildpack was updated to support environment variables as part of the include locations in the `server.xml` file.

## 9 December 2016
{: #cloud-foundry-public-dec0916}
{: release-note}

Updated ASP.NET Core buildpack v1.0.6-20161205-0912
:   This release includes the following updates:

    * Add support for .NET Core 1.1.0
    * Remove support for .NET Core 1.0.0 RC2
    * Add an option to clear NuGet packages cache

## 29 November 2016
{: #cloud-foundry-public-nov2916}
{: release-note}

Updated Liberty buildpack v3.5-20161114-1152
:    The default Liberty runtime version `16.0.0.3` was updated to include [PI62375](https://www.ibm.com/support/pages/node/587681){: external} fix and to provide the `microProfile-1.0` convenience feature.

    * The monthly Liberty runtime version was updated to the `2016.11.0.0` release.

    * The buildpack also contains updated {{site.data.keyword.IBM_notm}} JREs: version 8 SR3 FP20 and version 7.1 SR3 FP60.

    * The DB2 JDBC driver was updated to the `4.21.29` version.

    * The Monitoring and Analytics service integration was fixed to work with [Diego](https://docs.cloudfoundry.org/concepts/diego/diego-architecture.html){: external}.

    * The [Dynatrace](/docs/cloud-foundry-public?topic=cloud-foundry-public-using_dynatrace) service integrations were updated to work better with the Dynatrace service offerings.

    * The [auto-configuration](/docs/cloud-foundry-public?topic=cloud-foundry-public-auto_config) support for PostgreSQL and MySQL type of services was improved to work better when deploying a server directory or packaged server.

    * The Node.js runtime that is used by the [`devconsole` and `shell` App Management utilities](/docs/cloud-foundry-public?topic=cloud-foundry-public-app_management) was updated to the latest `0.12.17` version.

    * [Security fixes](https://www.ibm.com/support/pages/node/286257){: external} for the Liberty runtime are included.

## 17 November 2016
{: #cloud-foundry-public-nov1716}
{: release-note}

Updated Node.js buildpack v3.9
:   This release of the buildpack supports {{site.data.keyword.IBM_notm}} SDK for Node.js runtime versions: 0.10.47, 0.10.48, 0.12.16, 0.12.17, 4.6.1, 4.6.2, 6.7.0, and 6.9.1. The default is now 4.6.2.

    Note that Node.js v6 was promoted to LTS status on October 18, 2016 and will soon become the buildpack's default runtime. Node.js v0.10 reached end of life on October 31, 2016 and will soon no longer be included in the buildpack. See [Node.js version long-term support and the SDK for Node.js buildpack](https://www.ibm.com/blogs/bluemix/2016/11/node-version-support-and-sdk-buildpack/){: external} for more details.

    Bugs affecting the trace and inspector App Management handlers, when used in conjunction with Node.js v6, have been addressed in this release. See [Managing Liberty and Node.js apps](/docs/cloud-foundry-public?topic=cloud-foundry-public-app_management){: external} for more information about how the inspector handler is changing now that Node.js v6 has integrated the inspector capability.

## 1 November 2016
{: #cloud-foundry-public-nov0116}
{: release-note}

Updated Liberty buildpack v3.4.1-20161030-2241
:   The buildpack contains a fix for a problem starting certain types of apps. Specifically, apps deployed as a server directory or a packaged server with the app files in the `dropins` directory.

## 21 October 2016
{: #cloud-foundry-public-oct2116}
{: release-note}

Updated Liberty buildpack v3.4-20161018-2004
:   The default Liberty runtime version `16.0.0.3` was updated to include [PI68805](https://www.ibm.com/support/pages/apar/PI68805){: external} and [PI69141](https://www.ibm.com/support/pages/apar/PI69141){: external} fixes.

    * The monthly Liberty runtime version was updated to the [2016.9.0.1](https://developer.ibm.com/wasdev/blog/2016/09/23/beta-websphere-liberty-and-tools-october-2016/){: external} release.

    * The buildpack also contains an updated version of {{site.data.keyword.IBM_notm}} JRE 8.0: SR3 FP12.

    * The {{site.data.keyword.IBM_notm}} JRE 8.0 and 7.1 are now configured to enable [all TLS protocols when `SSLContext.getContext("TLS")` is called](https://www.ibm.com/support/knowledgecenter/SSYKE2_8.0.0/com.ibm.java.security.component.80.doc/security-component/jsse2Docs/matchsslcontext_tls.html){: external} to match Oracle's JRE behavior. {{site.data.keyword.IBM_notm}} JRE 7.1 is also configured to enable [all TLS protocols when `SSLContext.getDefault()` is called](https://www.ibm.com/support/knowledgecenter/SSYKE2_7.1.0/com.ibm.java.security.component.71.doc/security-component/jsse2Docs/overrideSSLprotocol.html){: external} to match IBM's JRE 8.0 behavior.

    * The buildpack provides an updated data collector for the Monitoring and Analytics service.

    * The buildpack was changed back to download the latest 1.5.x [MariaDB Connector/J JDBC driver](https://mariadb.com/kb/en/about-mariadb-connector-j/){: external} when performing [auto-configuration for MySQL type of services](/docs/cloud-foundry-public?topic=cloud-foundry-public-auto_config).

    * The buildpack introduces support for customizing service auto-configuration behavior via the `LBP_SERVICE_CONFIG_<serviceType>` environment variable. For example, it can be used to change the location or version of a JDBC driver to download for the MySQL service. See the documentation of [services that support auto-configuration](/docs/cloud-foundry-public?topic=cloud-foundry-public-auto_config) for more information.

    * The buildpack also contains a number of [Diego](https://docs.cloudfoundry.org/concepts/diego/diego-architecture.html){: external} improvements related to app health check and the [App Management](/docs/cloud-foundry-public?topic=cloud-foundry-public-app_management) functionality.

## 10 October 2016
{: #cloud-foundry-public-oct1016}
{: release-note}

Updated ASP.NET Core buildpack v1.0.1-20161005-1225
:   This release includes the following updates:

    * Add support for .NET Core 1.0.1
    * Fix an intermittent issue which caused deployment to fail when caching NuGet packages

## 7 October 2016
{: #cloud-foundry-public-oct0716}
{: release-note}

Updated Node.js buildpack v3.8-20161006-1211
:   This release of the buildpack supports {{site.data.keyword.IBM_notm}} SDK for Node.js runtime versions: 0.10.46, 0.10.47, 0.12.15, 0.12.16, 4.5.0, 4.6.0, 6.6.0, and 6.7.0. The default is now 4.6.0.

    In addition to the new runtimes, this release contains buildpack bug fixes. A fix for the known issue when using Node.js 6.x and Development Mode that was mentioned in the v3.7-20160826-1101 release updates is one of them. It is also synchronized with the [Cloud Foundry Node.js buildpack v1.5.20](https://github.com/cloudfoundry/nodejs-buildpack/tree/v1.5.20){: external}.


## 16 September 2016
{: #cloud-foundry-public-sep1616}
{: release-note}

Updated Liberty buildpack v3.3-20160912-1729
:   The default Liberty runtime version was updated to the [16.0.0.3](https://www.ibm.com/support/pages/node/715555){: external} release. The monthly Liberty runtime version was updated to the [2016.9.0.0](https://developer.ibm.com/wasdev/blog/2016/08/26/beta-websphere-liberty-and-tools-september-2016/){: external} release. With these updates, the `cloudant-1.0` and `passwordUtilities-1.0` Liberty features, previously available as beta features, are now available as production-ready features.

    * [Security fixes](https://www.ibm.com/support/pages/node/551895){: external} for the Liberty runtime are included.

    * The buildpack also contains an updated version of {{site.data.keyword.IBM_notm}} JRE 8.0: SR3 FP11.

    * The buildpack was adjusted to download the latest 1.4.x [MariaDB Connector/J JDBC driver](https://mariadb.com/kb/en/about-mariadb-connector-j/){: external} when performing [auto-configuration for MySQL type of services](/docs/cloud-foundry-public?topic=cloud-foundry-public-auto_config) due to a problem with the latest 1.5.x driver.

## 31 August 2016
{: #cloud-foundry-public-aug3116}
{: release-note}

Updated ASP.NET Core buildpack v1.0-20160826-1345
:   The following updates are included in this release:

    * Add support for running pre and post compile scripts using NPM and Bower to install front-end JavaScript and CSS libraries.
    * Move buildpack from Beta status to GA status

## 26 August 2016
{: #cloud-foundry-public-aug2616}
{: release-note}

Updated Liberty buildpack v3.2-20160822-2200
:   The buildpack contains updated versions of {{site.data.keyword.IBM_notm}} JRE: 8 SR3 FP10 and 7.1 SR3 FP50.

    * The monthly Liberty runtime version was updated to the [2016.8.0.0](https://developer.ibm.com/wasdev/blog/2016/07/28/beta-websphere-liberty-and-tools-august-2016/){: external} release.

    * The service plug-in that provides auto-configuration support for the SQL Database service was updated to always use the JVM's trusted certificates when connecting to the service over TLS.

Updated Node.js buildpack v3.7-20160826-1101
:   This release of the buildpack supports {{site.data.keyword.IBM_notm}} SDK for Node.js runtime versions: 0.10.45, 0.10.46, 0.12.14, 0.12.15, 4.4.7, 4.5.0, 6.2.2, and 6.4.0. The default is now 4.5.0.

    This release includes bug fixes, including those from the [Cloud Foundry’s Node.js buildpack 1.5.18](https://github.com/cloudfoundry/nodejs-buildpack/tree/v1.5.18){: external}.

    The release removes support for the `strongpm` App Management handler as announced in [{{site.data.keyword.cloud_notm}} Node.js Buildpack v3.3 – FIPS mode and more](https://www.ibm.com/blogs/cloud-archive/2016/05/node-buildpack-update-fips-mode/){: external}.

    Note that there is a known issue when using Node.js 6.x and Development Mode. As a work around you will need to restage your app after enabling Development Mode before you can begin using it.

## 22 July 2016
{: #cloud-foundry-public-jul2216}
{: release-note}

Updated Liberty buildpack v3.1-20160717-2254
:   The [App Management](/docs/cloud-foundry-public?topic=cloud-foundry-public-app_management) functionality was updated to support federated authentication. Also, the Node.js runtime that is used by the `devconsole` and `shell` utilities was updated to the latest `0.12.15` version.

    * The buildpack adds support for the [Dynatrace Ruxit](https://www.dynatrace.com/solutions/cloud-native-application-monitoring/){: external} app monitoring agent.

    * The buildpack provides an updated data collector for the Monitoring and Analytics service.

    * The buildpack also provides an updated version of the agent for the Auto-Scaling service.

    * The monthly Liberty runtime version was updated to the [2016.7.0.0](https://developer.ibm.com/wasdev/blog/2016/06/30/beta-websphere-liberty-and-tools-july-2016/){: external} release.

Updated Node.js buildpack v3.6-20160715-0749
:   This release of the buildpack supports {{site.data.keyword.IBM_notm}} SDK for Node.js runtime versions: 0.10.45, 0.10.46, 0.12.14, 0.12.15, 4.4.6, 4.4.7, 6.2.1, and 6.2.2. The default is now 4.4.7.

    This release includes an updated App Management proxy that supports federated logins.

    Included are fixes for the following security vulnerabilities:

    * [CVE-2016-1669](https://www.ibm.com/support/pages/node/283763){: external}

## 11 July 2016
{: #cloud-foundry-public-jul1116}
{: release-note}

Updated ASP.NET Core buildpack v0.9-20160706-1603
:   This version of the buildpack includes the following changes:

    * This version of the buildpack supports the .NET CLI 1.0 Preview 2 build and .NET Core 1.0 RTM
    * The buildpack continues to support .NET CLI 1.0 Preview 1 and .NET Core 1.0 RC2
    * The default .NET CLI version to be installed is now 1.0.0-preview2-003121

## 22 June 2016
{: #cloud-foundry-public-jun2216}
{: release-note}

Updated Node.js buildpack v3.5-20160609-1608
:   This release of the buildpack adds {{site.data.keyword.IBM_notm}} SDK for Node.js runtime versions 4.4.5 and 6.2.0. The default becomes 4.4.5.

    The release removes support for older runtime versions as announced in [{{site.data.keyword.cloud_notm}} Node.js Buildpack v3.3 – FIPS mode and more](https://www.ibm.com/blogs/cloud-archive/2016/05/node-buildpack-update-fips-mode/){: external}. The buildpack now supports 0.10.44, 0.10.45, 0.12.13, 0.12.14, 4.4.4, 4.4.5, 6.1.0, and 6.2.0.

    This release includes bug fixes from the [Cloud Foundry’s Node.js buildpack 1.5.14](https://github.com/cloudfoundry/nodejs-buildpack/tree/v1.5.14){: external}.

## 17 June 2016
{: #cloud-foundry-public-jun1716}
{: release-note}

Updated Liberty buildpack v3.0-20160608-1450
:   The buildpack now contains two versions of WebSphere Liberty, the latest stable release and the latest monthly release. Specifically, it provides [16.0.0.2](https://www.ibm.com/support/pages/node/281685){: external} stable release and [2016.6.0.0](https://developer.ibm.com/wasdev/blog/2016/06/03/beta-websphere-liberty-and-tools-june-2016/){: external} monthly release. The stable release will be used by default. See [Liberty versions](/docs/cloud-foundry-public?topic=cloud-foundry-public-buildpack_defauts#liberty_versions) for additional details.

    * The buildpack also contains security fixes for the [Apache Standard Taglibs vulnerability](https://www.ibm.com/support/pages/node/282471){: external}.

## 10 June 2016
{: #cloud-foundry-public-jun1016}
{: release-note}

Updated ASP.NET Core buildpack v0.8.1-20160526-0957
:   This version of the buildpack includes the following changes:

    * The runtime's name is changed from ASP.NET 5 to ASP.NET Core.
    * The buildpack version number is included in detect script output.
    * This version of the buildpack removes support for DNX based apps using CoreCLR RC1 and lower.
    * This version of the buildpack supports the .NET CLI and .NET Core RC2.
    * The buildpack detects projects with either a `project.json` file or `*.runtimeconfig.json` files from publish output.

## 25 May 2016
{: #cloud-foundry-public-may2516}
{: release-note}

Updated Liberty buildpack v2.9-20160519-1249
:   The buildpack contains an updated version of WebSphere Liberty based on the [May beta](https://developer.ibm.com/wasdev/blog/2016/05/06/beta-websphere-liberty-and-tools-may-2016/){: external}. The updated version of Liberty makes the `bluemixLogCollector-1.1` and `logstashCollector-1.1` beta features available in {{site.data.keyword.cloud_notm}}.

## 20 May 2016
{: #cloud-foundry-public-may2016}
{: release-note}

Updated Node.js buildpack v3.4-20160518-1653
:   This release of the buildpack adds {{site.data.keyword.IBM_notm}} SDK for Node.js runtime versions 0.10.45, 0.12.14, 4.4.4, 6.0.0, and 6.1.0. The default is now 4.4.4.

    Included are fixes for the following security vulnerabilities:

    * [CVE-2015-8855](https://www.ibm.com/support/pages/node/278621){: external}

    * [CVE-2016-2108 CVE-2016-2107 CVE-2016-2105 CVE-2016-2106 CVE-2016-2109 CVE-2016-2176](https://www.openssl.org/news/secadv/20160503.txt){: external}

    Note that there is a known issue with NPM v3 and the App Management inspector utility. NPM 3.8.6 is the default with the 6.0.0 and 6.1.0 runtimes. If you want to use either of the 6.x runtimes and the inspector utility, you should specify a 2.x NPM version in your package.json as a temporary workaround.

## 5 May 2016
{: #cloud-foundry-public-may0516}
{: release-note}

Updated Liberty buildpack v2.8-20160430-1011
:   The buildpack contains an updated version of WebSphere Liberty based on the [April beta](https://developer.ibm.com/wasdev/blog/2016/04/08/beta-websphere-liberty-and-tools-april-2016/){: external}. The updated version of Liberty makes the `logstashCollector-1.0` GA feature and the `logmetCollector-1.0` beta feature available in {{site.data.keyword.cloud_notm}}.

    * The buildpack also contains updated versions of {{site.data.keyword.IBM_notm}} JRE: 8 SR3 and 7.1 SR3 FP40.

    * The buildpack adds initial support for the [AppDynamics](https://www.appdynamics.com/){: external} app monitoring agent.

    * The [Dynatrace](/docs/cloud-foundry-public?topic=cloud-foundry-public-using_dynatrace) support was improved to simplify the installation of the agent.

    * The buildpack provides an updated data collector for the Monitoring and Analytics service. It contains a fix for a problem with collection of the max heap data.

    * The Node.js runtime that is used by the [`devconsole` and `shell` App Management utilities](/docs/cloud-foundry-public?topic=cloud-foundry-public-app_management) was updated to the latest 0.12.13 version.

## 29 April 2016
{: #cloud-foundry-public-apr2916}
{: release-note}

Updated Node.js buildpack v3.3-20160428-1409
:   This release of the buildpack adds {{site.data.keyword.IBM_notm}} SDK for Node.js runtime versions 0.10.44, 0.12.13, 4.4.0, 4.4.1, 4.4.2, and 4.4.3. The default is now 4.4.3.

    For 4.3.1 and up, it is now possible to use a FIPS-enabled version of the runtime by setting the `FIPS_MODE=true` environment variable for your app.

    The updated buildpack and the new runtime versions also contain fixes for security vulnerabilities:

    * [CVE-2016-2515](https://www.ibm.com/support/pages/node/543037){: external}

    * [CVE-2016-2537](https://www.ibm.com/support/pages/node/543037){: external}

    * [CVE-2016-3956](https://www.ibm.com/support/pages/node/275571){: external}

    The updated buildpack also contains fixes for several bugs:

    * Now {{site.data.keyword.IBM_notm}} SDK for Node.js builds will always be used if one is available matching the requested range. Previously, this case was only true for 4.x runtime versions.

    * Now the App Management inspector utility will work with 4.x runtime versions.

    * Fixed a regression in the `strongpm` App Management utility.

## 25 March 2016
{: #cloud-foundry-public-mar2516}
{: release-note}

Updated Liberty buildpack v2.7-20160321-1358
:   The buildpack contains an updated version of WebSphere Liberty based on the [March beta](https://developer.ibm.com/wasdev/blog/2016/03/18/new-websphere-liberty-features-march-2016/){: external}. The updated version of Liberty makes the `cloudant-1.0` beta feature available in {{site.data.keyword.cloud_notm}}

    * The buildpack also contains updated versions of {{site.data.keyword.IBM_notm}} JRE: 8 SR2 FP12 and 7.1 SR3 FP32.

    * The buildpack provides an updated version of the agent for the Auto-Scaling service.

    * The buildpack now comes with a new data collector for the Monitoring and Analytics service. The new collector enables configuration of monitoring thresholds and contains a number of bug fixes.

    * The buildpack provides an updated DB2® JDBC driver version 4.19.49.

    * The Node.js runtime that is used by the [`devconsole` and `shell` App Management utilities](/docs/cloud-foundry-public?topic=cloud-foundry-public-app_management) was updated to the latest 0.12.12 version.

## 18 March 2016
{: #cloud-foundry-public-mar1816}
{: release-note}

Updated Node.js buildpack v3.2-20160315-1257
:   This release of the buildpack moves the default {{site.data.keyword.IBM_notm}} SDK for Node.js runtime from version 4.3.0 to 4.3.2. It also includes {{site.data.keyword.IBM_notm}} SDK for Node.js versions 0.10.43, 0.12.12, and 4.3.1. Use these recent Node.js versions to pick up fixes for several security vulnerabilities.

## 7 March 2016
{: #cloud-foundry-public-mar0716}
{: release-note}

Updated Liberty buildpack v2.6-20160225-1649
:   The buildpack adds support for Dynatrace app monitoring. See [Using Dynatrace](/docs/cloud-foundry-public?topic=cloud-foundry-public-using_dynatrace) for details.

    * The buildpack adds support for `DynamicPULSE`.

## 4 March 2016
{: #cloud-foundry-public-mar0416}
{: release-note}

Updated Node.js buildpack v3.1-20160222-1123
:   This release of the buildpack moves the default {{site.data.keyword.IBM_notm}} SDK for Node.js runtime from version 4.2.4 to 4.3.0. It also includes {{site.data.keyword.IBM_notm}} SDK for Node.js versions 0.10.42, 0.12.10, and 4.2.6. Use these recent Node.js versions to pick up fixes for several security vulnerabilities.

## 10 February 2016
{: #cloud-foundry-public-feb1016}
{: release-note}

Updated Liberty buildpack v2.5-20160209-1336
:   The buildpack contains an updated version of WebSphere Liberty based on the [February beta](https://developer.ibm.com/wasdev/blog/2016/02/12/beta-websphere-liberty-and-tools-february/){: external}. The updated version of the Liberty profile makes the `apiDiscovery-1.0` GA feature available in {{site.data.keyword.cloud_notm}}.

## 4 February 2016
{: #cloud-foundry-public-feb0416}
{: release-note}

Updated Liberty buildpack v2.4-20160127-1437
:   The buildpack contains an updated version of WebSphere Liberty based on the January beta. With this update, the `scim-1.0` Liberty feature, previously available as beta a feature, is now available as a production-ready feature. The updated version of Liberty also makes the `passwordUtilities-1.0` beta feature available in {{site.data.keyword.cloud_notm}}.

    * The buildpack also contains an updated {{site.data.keyword.IBM_notm}} JRE 7.1 SF3 FP20 and {{site.data.keyword.IBM_notm}} JRE 8 SR2 FP10.

    * The buildpack was updated to download the latest 1.x [MariaDB Connector/J JDBC driver](https://mariadb.com/kb/en/about-mariadb-connector-j/){: external} when performing [auto-configuration for MySQL type of services](/docs/cloud-foundry-public?topic=cloud-foundry-public-auto_config).

Updated Node.js buildpack v3.0-20160125-1224
:   This release is fully synchronized with the [Cloud Foundry community Node.js](https://github.com/cloudfoundry/nodejs-buildpack){: external} buildpack. In addition to community changes, modifications were made to certain defaults, along with optimizations to reduce staging time and updates to the App Management feature.

    * Buildpack updates:

        * Node.js v4.2.4 ({{site.data.keyword.IBM_notm}} SDK for Node.js Version 4) is now the default runtime on {{site.data.keyword.cloud_notm}}, replacing v0.12.9. This change might cause your app to behave differently if a particular version is not specified for your app. To learn how to specify a version of Node.js for your {{site.data.keyword.cloud_notm}} app, see [Node.js runtime](/docs/cloud-foundry-public?topic=cloud-foundry-public-nodejs_runtime){: external} documentation.

        * NODE_ENV is now set to *production* by default. This change will cause some node dependencies to behave differently. For example, the Express framework will no longer return stack traces in the web browser for faulty endpoints, but instead displays *Internal Server Error*. When NPM_CONFIG_PRODUCTION is set to *true*, NPM will set NODE_ENV to *production* for subshell scripts in the NPM install phase only. This function allows users to set NODE_ENV to another value like *development* for app runtime. For clarity, NPM scripts will see the message **NODE_ENV=production**.

        * A Bug-fix to the Monitoring and Analytics service is included.

    * Caching updates:

        * If cache is disabled (NODE_MODULES_CACHE=false) the buildpack will not attempt to cache any modules/components. Previously this setting made it so that the cache is not popped, but it would still cache the installed modules for future deploys. Now, it will not pop the cache or attempt to store any cache.

        * Bower_components are cached by default in addition to node_modules.

    * Other updates:

        * Added Helpful warnings for missing dependencies like gulp, bower, and angular.

        * The detect script is updated with buildpack version information.

        * The clustering recommendation (WEB_CONCURRENCY) initially introduced by community is removed as memory determination was inaccurate on {{site.data.keyword.cloud_notm}}.

## 16 December 2015
{: #cloud-foundry-public-dec1615}
{: release-note}

Updated Liberty buildpack v2.3-20151208-1311
:   The buildpack contains an updated version of the Liberty profile based on the [December beta](https://developer.ibm.com/wasdev/blog/2015/11/20/beta-was-liberty-beta-with-tools-december-2015/){: external}. The updated version of the Liberty profile makes the `spnego-1.0` and `wsSecuritySaml-1.1` GA features and the `scim-1.0` beta feature available in {{site.data.keyword.cloud_notm}}.

    * The buildpack also contains an updated {{site.data.keyword.IBM_notm}} JRE 8 SR2.

    * The buildpack was also updated to download the latest [9.4.x PostgreSQL JDBC driver](https://jdbc.postgresql.org/){: external} and 1.2.x [MariaDB Connector/J JDBC driver](https://mariadb.com/kb/en/about-mariadb-connector-j/){: external} when performing [auto-configuration](/docs/cloud-foundry-public?topic=cloud-foundry-public-auto_config) for PostgreSQL or MySQL type of services.

Updated Node.js buildpack v2.8-20151209-1403 and v3.0beta-20151211-2041
:   This release of the Node.js buildpack comes with two versions, v2.8 and v3.0beta. Both these versions include the following changes:

    * A bug-fix to Monitoring and Analytics service.
    
    * The inclusion of a cached runtime for {{site.data.keyword.IBM_notm}} SDK for Node.js v4.2.3.0, v4.2.2.0, v1.2.0.8 and v1.2.0.7, which are based on community versions Node.js v4.2.3, v4.2.2, v0.12.9 and v0.12.8.

    * In addition, in v3.0beta the default Node.js runtime is changed to v4.2.3.

    {{site.data.keyword.IBM_notm}} Node.js buildpack v3.0beta is now released as a non-default buildpack on {{site.data.keyword.cloud_notm}} with Node.js v4.2.3 as the default runtime. To ensure that your apps and services will continue to work on {{site.data.keyword.cloud_notm}}, push your app with the beta version of the buildpack. After 30 days or longer, v3 will be made the default buildpack.

    To push your app with v3.0beta:

    * Use "-b" option in your `ibmcloud cf push` command:

        ```text
        ibmcloud cf push -b sdk-for-nodejs-v3beta
        ```
        {: pre}

    * Or use the "buildpack" option in your manifest.yml file:

        ```yaml
        buildpack: sdk-for-nodejs-v3beta
        ```
        {: codeblock}

    This change to the default runtime will not affect your app if you configured a specific version of Node.js in your app's package.json.

    You can always specify the version of Node.js to run your app by using the engines.node entry in your package.json as explained in [Available versions](/docs/cloud-foundry-public?topic=cloud-foundry-public-available_versions).
    {: note}

## 23 November 2015
{: #cloud-foundry-public-nov2315}
{: release-note}

Updated Liberty buildpack v2.2-20151119-1720
:   The buildpack contains an updated version of the Liberty profile runtime and WebSphere eXtreme Scale Client with security fixes for the [Apache Commons Collection vulnerability](https://www.ibm.com/blogs/psirt/ibm-security-bulletin-vulnerability-in-apache-commons-affects-liberty-for-java-for-ibm-bluemix-cve-2015-7450/){: external}.

    * The buildpack also contains an updated version of the [Java MongoDB Driver](https://docs.mongodb.com/drivers/java){: external}, v2.13.3. The new driver is compatible with MongoDB version 2.4, 2.6 and 3.0.

    * The buildpack also provides an updated version of the data collector for the Monitoring and Analytics service. The updated data collector has improved method tracing capabilities.

Updated Node.js buildpack v2.7-20151118-1003
:   With 2.7, version 4.2.1.0 of the {{site.data.keyword.IBM_notm}} SDK for Node.js (based on Node v4.2.1 LTS) is included. It is not the default yet, but can be specified for use. **Note:** This version replaces the open source build that was previously available. We also made some small bug fixes to our service extension framework.

## 22 October 2015
{: #cloud-foundry-public-oct2215}
{: release-note}

Updated ASP.NET 5 buildpack v0.7-20151022-1257
:   This version of the buildpack removes Mono and instead supports the Beta 8 CoreCLR.

## 19 October 2015
{: #cloud-foundry-public-oct1915}
{: release-note}

Updated Node.js buildpack v2.6.1-20151015-1326
:   Node.js v2.6.1 introduces a bug fix to the [`strongpm` app management handler](https://www.ibm.com/blogs/cloud-archive/2015/10/strongloop-devops-on-bluemix/), and a more consistent NPM version.

## 16 October 2015
{: #cloud-foundry-public-oct1615}
{: release-note}

Updated Liberty buildpack v2.1-20151006-0912
:   The buildpack contains an updated version of the Liberty profile based on the [October beta](https://developer.ibm.com/wasdev/blog/2015/09/25/beta-was-liberty-beta-with-tools-october-2015/){: external}. With this update, the `bells-1.0`, `rtcomm-1.0`, `rtcommGateway-1.0`, `samlWeb-2.0`, `sipServlet-1.1` Liberty features, previously available as beta features, are now available as production-ready features.

    * The buildpack also contains an updated {{site.data.keyword.IBM_notm}} JRE 8 SR1 FP11.

    * The buildpack also provides a number of performance improvements and optimizations:
        
        * The [CDI 1.2](/docs/cloud-foundry-public?topic=cloud-foundry-public-options_for_pushing#stand_alone_apps) implicit bean archive scanning feature is disabled by default when deploying WAR or EAR files.  
        
        * To reduce the droplet size, the [App Management utilities](/docs/cloud-foundry-public?topic=cloud-foundry-public-app_management) `devconsole` and `shell`, require a restage operation instead of a restart.
    
        * The {{site.data.keyword.IBM_notm}} JRE's shared class cache is disabled as it was not being reused in the {{site.data.keyword.cloud_notm}} environment.

## 15 October 2015
{: #cloud-foundry-public-oct1515}
{: release-note}

Updated Node.js buildpack v2.6-20151006-1309
:   This release of the Node.js buildpack features the integration of [StrongLoop Process Manager](https://strong-pm.io){: external} to the App Management feature. For more information, see the blog post [StrongLoop DevOps for Node.js Apps on {{site.data.keyword.cloud_notm}}](https://www.ibm.com/blogs/cloud-archive/2015/10/strongloop-devops-on-bluemix/){: external}.

##  18 September 2015
{: #cloud-foundry-public-sep1815}
{: release-note}

Updated Liberty buildpack v2.0-20150914-1535
:   The buildpack introduces two major changes:
    
    * The default configuration for WAR and EAR files enables Java EE 7 Web Profile features instead of Java EE 6 Web Profile features.
    
    * The default Java version is version 8 instead of version 7.

    * Refer to the [Upcoming Liberty for Java buildpack changes](https://www.ibm.com/blogs/cloud-archive/2015/09/upcoming-liberty-for-java-buildpack-changes/){: external} blog post for details about these changes and how they may affect your app.

    * The buildpack also introduces app_state configuration option to disable the `appstate` feature via the `JBP_CONFIG_LIBERTY` environment variable. The `appstate` feature integrates with the Cloud Foundry health check process to ensure the Liberty app is fully initialized before the app can receive HTTP requests. To disable the `appstate` feature, you can set the `JBP_CONFIG_LIBERTY` environment variable to `app_state: false`.

Updated ASP.NET 5 buildpack v0.6-20150916-1220
:   This version of the buildpack supports Beta 7 DNX changes, and it can run apps dependent on older beta releases with the following custom start command:

    ```text
    dnx src/dotnetstarter kestrel --server.urls http://${VCAP_APP_HOST}:${PORT}
    ```
    {: pre}

    * Usage of the Nowin web server was removed from this buildpack and the [Kestrel](https://github.com/aspnet/KestrelHttpServer){: external} web server is used instead.


## 4 September 2015
{: #cloud-foundry-public-sep0415}
{: release-note}

Updated Liberty buildpack v1.22-20150824-1104
:   The buildpack supports the [HTTP_PROXY and HTTPS_PROXY environment variables](/docs/cloud-foundry-public?topic=cloud-foundry-public-environment_variables). If set, the buildpack uses the proxy server specified by these environment variables when it downloads various buildpack components.

## 19 August 2015
{: #cloud-foundry-public-aug1915}
{: release-note}

Updated Liberty buildpack v1.21-20150811-1342
:   The buildpack contains an updated version of the Liberty profile based on the [August beta](https://developer.ibm.com/wasdev/blog/2015/07/30/beta-was-liberty-beta-with-tools-august-2015/){: external}. The updated version of the Liberty profile makes the following new beta features available in {{site.data.keyword.cloud_notm}}: `bells-1.0`, `rtcommGateway-1.0`, `samlWebSso-2.0`.

## 31 July 2015
{: #cloud-foundry-public-jul3115}
{: release-note}

Updated Liberty buildpack v1.20.1-20150729-1255
:   The buildpack contains updated versions of {{site.data.keyword.IBM_notm}} JREs: 7.1 SR1 FP10 and 8 SR1 FP10.
The updated JREs contain [latest security fixes](https://www.ibm.com/support/pages/node/534887){: external} and other improvements.

    * The service plug-in that provides [auto-configuration support](/docs/cloud-foundry-public?topic=cloud-foundry-public-auto_config) for the [Cloudant NoSQL Database](/docs/Cloudant?topic=Cloudant-getting-started-with-cloudant) service was updated to ensure that the connections to the service are established over a secure channel.

## 21 July 2015
{: #cloud-foundry-public-jul2115}
{: release-note}

Updated Liberty buildpack v1.20-20150713-1450
:   The buildpack contains an updated version of the Liberty profile based on the [8.5.5.6 release](https://developer.ibm.com/wasdev/blog/2015/06/25/java-ee-7-has-landed-in-was-liberty/){: external}. With this release all the Java EE 7 Liberty features previous available as beta features, are now available as production-ready features. Due to port and other restrictions in the {{site.data.keyword.cloud_notm}}, some features such as for example remote EJBs are not be fully supported in the platform.

    * The buildpack recognizes and runs apps packaged in the [distZip-style](https://docs.gradle.org/current/userguide/application_plugin.html){: external}.

    * The buildpack contains an updated data collector for the Monitoring and Analytics service and WebSphere eXtreme Scale Client that support the new Liberty runtime version.

## 30 June 2015
{: #cloud-foundry-public-jun3015}
{: release-note}

Updated Liberty buildpack v1.19.1-20150622-1509
:   This version of the buildpack contains an updated {{site.data.keyword.IBM_notm}} JRE with a security fix for the [LogJam vulnerability](https://www.ibm.com/support/pages/node/531245){: external}.

    * The New Relic agent was updated to version 3.17. The new version provides improved integration with the Liberty profile runtime.

## 15 June 2015
{: #cloud-foundry-public-jun1515}
{: release-note}

Updated Node.js buildpack v2.0-20150608-1503
:   In this release, we synced our Node.js buildpack with the latest [CF community Node.js buildpack](https://github.com/cloudfoundry/nodejs-buildpack){: external}, which comes with a number of new features from the community.

    In addition, we revamped the App Management feature in the Node.js buildpack, which enables utilities like shell, node-inspector, {{site.data.keyword.cloud_notm}} Live Sync, and more. See [Managing Liberty and Node.js apps](/docs/cloud-foundry-public?topic=cloud-foundry-public-app_management) for details.

## 14 June 2015
{: #cloud-foundry-public-jun1415}
{: release-note}

Updated Liberty buildpack v1.19-20150608-1717
:   The buildpack contains a number of app management enhancements that include support for the development console and web-based shell access. See the [app management documentation](/docs/cloud-foundry-public?topic=cloud-foundry-public-app_management) for details.

    * The buildpack also contains a fix for a problem where the Liberty feature for the Monitoring and Analytics service could not be found.

## 27 May 2015
{: #cloud-foundry-public-may2715}
{: release-note}

Updated Liberty buildpack v1.18-20150519-1642
:   The buildpack contains an updated version of the Liberty profile based on the [May beta](https://developer.ibm.com/wasdev/blog/2015/05/08/beta-liberty-and-tools-may-2015/){: external}.

## 5 May 2015
{: #cloud-foundry-public-may0515}
{: release-note}

Updated Liberty buildpack v1.17-20150501-1729
:   The buildpack contains an updated version of the Liberty profile based on the [April beta](https://developer.ibm.com/wasdev/blog/2015/04/10/announcing-liberty-beta-with-tools-aprilmay-2015/){: external}. With this update, the `jsp-2.3`, `el-3.0`, and `jdbc-4.1` Liberty features, previously available as beta features, are now available as production-ready features. Also, additional Java EE 7 features such as `jsf-2.2`, `javaMail-1.5`, `webProfile-7.0`, and `javaee-7.0` are now available as beta features.

    * The buildpack also provides initial support for Java 8. {{site.data.keyword.IBM_notm}} JRE 7.1 remains the default JRE but {{site.data.keyword.IBM_notm}} JRE 8 can be enabled for an app by setting the JBP_CONFIG_IBMJDK environment variable. Configuring version of OpenJDK is also supported. See [Customizing the JRE](/docs/cloud-foundry-public?topic=cloud-foundry-public-customizing_jre) for all the details.

    * The buildpack provides a new JBP_CONFIG_LIBERTY environment variable that can be used to override the default set of Liberty features enabled for an app when it deploys a WAR or EAR file. See [Stand-alone Apps](/docs/cloud-foundry-public?topic=cloud-foundry-public-options_for_pushing#stand_alone_apps) for more information.

    * The service plug-in for the Monitoring and Analytics service was updated to reduce the size of logs that are generated for the service.

    * With this version of the buildpack, the way the app files are laid out in the droplet changed. The change in the file structure eliminated complexity that is related to maintaining symbolic links and should have no impact on the apps.

Updated Node.js buildpack v1.17-20150429-1033
:   The Node.js buildpack now comes with [{{site.data.keyword.IBM_notm}} SDK for Node.js v0.12.1](https://developer.ibm.com/languages/node-js/articles/download-nodejs-for-ibm-platforms/){: external}.

    * If your app doesn’t specify a runtime in its package.json file, your app will now start by using v0.12.1, instead of v0.10.x. If you need to use the previous version, specify v0.10.x in your package.json as shown.

        ```text
            "engines": {
                "node": "0.10.x"
            }
        ```
        {: codeblock}

    * Known issues with v0.12.1:
        * The `Suspend` feature is broken when you use the Debug Tools feature provided by {{site.data.keyword.cloud_notm}} Live Sync.
    
        * The `mqlight` module that is used for the MQ Light service is not supported on v0.12.x

    * Various security vulnerabilities were resolved:
        
        * Fixed vulnerabilities in OpenSSL affecting {{site.data.keyword.IBM_notm}} SDK for Node.js. More details are available in the [security bulletin](https://www.ibm.com/blogs/psirt/ibm-security-bulletin-vulnerabilities-in-openssl-affect-ibm-sdk-for-node-js-in-ibm-bluemix-cve-2015-0286-cve-2015-0287-cve-2015-0288-cve-2015-0289-cve-2015-0292-cve-2015-0293-cv/){: external}.
       
        * Fixed vulnerability in RC4 Stream Cipher affecting {{site.data.keyword.IBM_notm}} SDK for Node.js. More details are available in the [security bulletin](https://www.ibm.com/blogs/psirt/ibm-security-bulletin-vulnerability-in-rc4-stream-cipher-affects-ibm-sdk-for-node-js-in-ibm-bluemix-cve-2015-2808/){: external}.

## 15 April 2015
{: #cloud-foundry-public-apr1515}
{: release-note}

Updated Liberty buildpack v1.16-20150407-1737
:   This version of the buildpack contains an updated {{site.data.keyword.IBM_notm}} JRE 7.1-2.11 with a [security fix for the Bar Mitzvah vulnerability](https://www.ibm.com/blogs/psirt/ibm-security-bulletin-vulnerability-in-rc4-stream-cipher-affects-liberty-for-java-for-ibm-bluemix-cve-2015-2808/){: external}.

    * When stand-alone WAR files are deployed, if provided, the buildpack now uses the context-root that is specified in the embedded `ibm-web-ext.xml` file as the app's context root. With this change, apps that were previously deployed under the root context might be deployed under a different context based on the settings in the `ibm-web-ext.xml` file.

## 3 April 2015
{: #cloud-foundry-public-apr0315}
{: release-note}

Updated Liberty buildpack v1.15-20150402-1422
:   The buildpack contains an updated version of the Liberty profile based on the [March beta](https://developer.ibm.com/wasdev/blog/2015/03/13/announcing-liberty-beta-tools-march-2015/){: external}. The updated version of the Liberty profiles makes the `jsf-2.2` beta feature available in {{site.data.keyword.cloud_notm}}.

    * The buildpack also contains an updated version of the data collector for the Monitoring and Analytics service.

## 2 April 2015
{: #cloud-foundry-public-apr0215}
{: release-note}

Updated Node.js buildpack v1.15-20150331-2231
:   The Node.js buildpack now includes three new features to help quickly develop on {{site.data.keyword.cloud_notm}} as you would on the desktop, without redeploying
    
    * Desktop Sync: Synchronize any (Windows) desktop tree to a cloud-based project workspace
    
    * Live Edit: Allows you to make changes to a Node.js app that runs in {{site.data.keyword.cloud_notm}} and test them in your browser right away.
    
    * Debug: Shell into your environment and debug! You can edit code dynamically, insert breakpoints, step through code, restart the runtime, and more by using the Node Inspector debugger

    * We pulled in the latest changes from the [Cloud Foundry’s Node.js buildpack](https://github.com/cloudfoundry/nodejs-buildpack){: external}. This change comes with a number of bug-fixes and improvements made by the community.

    * The Node.js buildpack now comes with [{{site.data.keyword.IBM_notm}} SDK for Node.js v1.1.0.13](https://developer.ibm.com/languages/node-js/articles/download-nodejs-for-ibm-platforms/){: external}.


## 20 March 2015
{: #cloud-foundry-public-mar2015}
{: release-note}

Updated Liberty buildpack v1.14-20150319-1159
:   This version of the buildpack contains an updated {{site.data.keyword.IBM_notm}} JRE 7.1.2.11 with a security fix for the [FREAK vulnerability](https://www.ibm.com/blogs/psirt/ibm-security-bulletin-freak-vulnerability-fixed-in-liberty-for-java-for-ibm-bluemix-cve-2015-0138/).

    * The [SQL Database](/docs/sql-query?topic=sql-query-gettingstarted){: external} service offers paid plans that provide an option for connecting with the database server over the SSL protocol. The buildpack's auto-configuration support for SQL Database service was updated to configure the runtime to connect with the database over SSL if the SSL connection information is available.

    * The buildpack was updated to report an error when a stand-alone WAR or EAR file that contains a `server.xml` configuration file in root of the app archive is deployed.

    * The buildpack contains a fix for MongoDB's auto-configuration service plug-in that in certain cases generated an invalid `server.xml` configuration.

## 10 February 2015
{: #cloud-foundry-public-feb1015}
{: release-note}

Updated Liberty buildpack v1.13-20150209-1122
:   The buildpack contains security fixes for the [Apache `HttpComponents` and Java overlay feature vulnerabilities](https://www.ibm.com/blogs/psirt/ibm-security-bulletin-multiple-vulnerabilities-fixed-in-liberty-for-java-for-ibm-bluemix-cve-2012-6153-cve-2014-3577-cve-2015-0178/){: external}.

     * The buildpack contains an updated version of the Liberty profile based on the [February beta](https://developer.ibm.com/wasdev/blog/2015/02/13/announcing-liberty-beta-tools-february-2015/){: external}. The updated version of the Liberty profile provides an updated version of the WebSocket GA feature `websocket-1.1`. It also makes the following Java EE 7 beta features available in {{site.data.keyword.cloud_notm}}: `cdi-1.2`, `el-3.0`, `jsp-2.3`, `jca-1.7`, `jacc-1.5`, and `jaspic-1.1`.

     * The buildpack provides integration with the [JRebel tool](https://www.jrebel.com/products/jrebel){: external}. The integration makes it easy to use JRebel with {{site.data.keyword.cloud_notm}} apps and perform instant app updates without redeploying or restaging the app. Only stand-alone web apps are supported.

## 6 February 2015
{: #cloud-foundry-public-feb0615}
{: release-note}

Updated Liberty buildpack v1.12-20150130-1016
:   The buildpack contains an updated version of the Liberty profile based on the [January beta](https://developer.ibm.com/wasdev/blog/2015/01/16/announcing-liberty-beta-tools-january-2015/){: external}.

    * The buildpack contains a trimmed version of the data collector for the Monitoring and Analytics service.

## 23 January 2015
{: #cloud-foundry-public-jan2315}
{: release-note}

Updated Liberty buildpack v1.11-20150119-1511
:   The buildpack contains an updated {{site.data.keyword.IBM_notm}} JRE version 7.1 SR2 FP1.

    * It also contains an updated WebSphere eXtreme Scale Client version 8.6.0.6 and updated agent for the Auto-Scaling service.

    * The New Relic service support was enhanced to support user-defined services.

    * The buildpack was improved to report detailed versions of the Liberty profile and {{site.data.keyword.IBM_notm}} JRE.

## 5 January 2015
{: #cloud-foundry-public-jan0515}
{: release-note}

Updated Node.js buildpack v1.9.1-20141208-1221
:   The Node.js buildpack now includes dynamic log setting support. With this support, developers can change the log level of their app dynamically if the app is using `log4js`, `bunyan`, or {{site.data.keyword.cloud_notm}} modules for logging.

    * The Node.js buildpack now comes with [{{site.data.keyword.IBM_notm}} SDK for Node.js v0.10.33](https://developer.ibm.com/languages/node-js/articles/download-nodejs-for-ibm-platforms/){: external}. This update includes fixes for the POODLE issue.

## 19 December 2014
{: #cloud-foundry-public-dec1914}
{: release-note}

Updated Liberty buildpack v1.10-20141218-0103
:   The buildpack provides a development mode for apps. The development mode is a special mode that allows developers to conduct many activities for an app instance that were not possible before. By using this feature, this version of the {{site.data.keyword.eclipsetoolsfull}} can now support remote debugging with incremental file updates against a Liberty app that is running in {{site.data.keyword.cloud_notm}}. This makes it convenient for a developer that uses Eclipse to debug an app in the cloud and apply changes to that app instantly.

    * The buildpack also contains an updated version of the Liberty profile based on the [December beta](https://developer.ibm.com/wasdev/blog/2014/12/10/announcing-liberty-beta-december/){: external}.

    * In addition, the following four Liberty features that were previously available as beta features, are now production-ready:
     
        * `concurrent-1.0`
        * `jsonp-1.0`
        * `servlet-3.1`
        * `websocket-1.0`

    * The buildpack provides integration with the New Relic service. Once an app is bound to the New Relic service, the buildpack automatically downloads and configures the runtime with the New Relic agent.

    * The buildpack has the following known limitations:
        * When in development mode, a `SessionCache` service cannot be bound.
        * When in development mode, a thread dump cannot be created.
        * When using the `servlet-3.1` or `websocket-v1.0` feature, the Monitoring & Analytics service cannot be bound.

## 5 December 2014
{: #cloud-foundry-public-dec0514}
{: release-note}

Updated Liberty buildpack v1.9-20141202-0947
:   The buildpack provides an enhanced JVM option support. The JVM options can now be applied with a restart operation. Restaging of the app is not necessary. Also, the default JVM options are optimized for fast failure and pre-configured with a common location that makes it easy to find the generated dumps. More details are provided in the [Custom Configuration of Java JVM for the Liberty Runtime article](https://www.ibm.com/blogs/cloud-archive/2014/12/custom-configurations-java-jvm-liberty-runtime/){: external}.

    * The buildpack contains an updated DB2 JDBC driver version 4.17.29.

    * It also contains a fix for a problem that prevented collection of the Liberty thread pool usage information for the Monitoring & Analytics service.

## 21 November 2014
{: #cloud-foundry-public-nov2114}
{: release-note}

Updated Liberty buildpack v1.8-20141118-1610
:   The buildpack contains an updated {{site.data.keyword.IBM_notm}} JRE version 7.1 SR2 that provides a fix for the [POODLE vulnerability](https://www.ibm.com/support/pages/node/253801){: external}.

    * It also contains an updated version of the Liberty profile based on the [November beta](https://developer.ibm.com/wasdev/blog/2014/11/07/announcing-liberty-profile-beta-november/){: external}.

## 30 October 2014
{: #cloud-foundry-public-14}
{: release-note}

Updated Liberty buildpack v1.7-20141020-1759
:   The buildpack contains an updated {{site.data.keyword.IBM_notm}} JRE version 7.1 SR1 FP3.

    * It also provides a fix for a problem that prevented deployment of apps with server configuration that contained Unicode characters.

## 23 October 2014
{: #cloud-foundry-public-oct2314}
{: release-note}

Updated the Liberty Buildpack v1.6-20141013-1628
:   The buildpack now comes with a new data collector for the Monitoring and Analytics. The new data collector collects diagnostic deep dive information, which enables users of the Diagnostics plan of the service to diagnose problems with their apps, down to the specific line of code.

    * The buildpack contains updated versions of the management and auto-scaling agents that include bug fixes and minor improvements. It also includes an updated version of the [Liberty profile](https://developer.ibm.com/wasdev/) and [Java MongoDB Driver](https://docs.mongodb.com/drivers/java){: external}, v2.12.3.

    * In the `cloudAutowiring` feature, a bug that caused resource injection errors in some apps was fixed.

Updated Node.js buildpack v1.6-20141013-1736
:   The Node.js buildpack now comes with [{{site.data.keyword.IBM_notm}} SDK for Node.js v1.1.0.8](https://developer.ibm.com/languages/node-js/articles/download-nodejs-for-ibm-platforms/){: external}. This update means you get a fully supported {{site.data.keyword.IBM_notm}} Node.js runtime when you specify the latest stable Node.js runtime for your app, v0.10.32. This latest SDK comes with a fix for an issue with the embedded qs module that resulted in a denial-of-service. It also contains an updated version of the NPM module and other improvements in the HTTP and URL modules. For more details, see the [v0.10.32 Change Log](https://raw.githubusercontent.com/joyent/node/v0.10.32/ChangeLog){: external}.

    * The buildpack also contains a fix for a bug that was adding an incorrect index.html file in the customer’s app during deployment.

## 3 October 2014
{: #cloud-foundry-public-oct0314}
{: release-note}

Updated Liberty Buildpack v1.5-20140923-1143
:   With the updated buildpack, the apps can now use the Liberty beta features, including `WebSocket 1.0`, `Servlet 3.1`, or `JAX-RS 2.0`.

## 30 September 2014
{: #cloud-foundry-public-sep3014}
{: release-note}

Updated Liberty Buildpack v1.4-20140908-1803
:   The buildpack now provides support for ElephantSQL and ClearDB MySQL Database third-party services. The auto-configuration support also works with `posgresql` and `mysql` experimental services. With the new total of 13 services, the auto-configuration support in the Liberty buildpack makes it quicker and easier to consume {{site.data.keyword.cloud_notm}} services in Liberty apps.

    * During app staging the buildpack displays improved log messages about auto-configuration and other actions it takes.

    * The buildpack contains an updated version of Liberty profile with fixes and improvements.

    * It also contains an updated version of {{site.data.keyword.IBM_notm}} JRE version 7.1 that has performance improvements. 

Updated Node.js buildpack v1.4-20140908-1746
:   The Node.js buildpack now comes with [{{site.data.keyword.IBM_notm}} SDK for Node.js v1.1.0.7](https://developer.ibm.com/languages/node-js/articles/download-nodejs-for-ibm-platforms/){: external}. This update means that you get a fully supported {{site.data.keyword.IBM_notm}} Node.js runtime when you specify the latest stable Node.js runtime for your app, v0.10.31. With a fully supported Node.js runtime, the customers receive a consistent support experience.

    * The buildpack contains an improved service framework. Specifically, it works better when binding the Monitoring and Analytics service and provides more diagnostic information if the service fails.

## 28 August 2014
{: #cloud-foundry-public-aug2814}
{: release-note}

Updated Liberty Buildpack v1.3-20140818-1538
:   The buildpack contains an updated version of the [Liberty Profile](https://developer.ibm.com/wasdev/){: external} with the latest fixes and improvements.

    * This version of the buildpack fixes support for the JAVA_OPTS environment variable for passing additional JVM options to the app runtime.

    * It also fixes a problem that prevented deployment of stand-alone Spring-based apps.

    * It is now possible to generate and download {{site.data.keyword.IBM_notm}} JVM snap traces using the {{site.data.keyword.cloud_notm}} UI. See the [Troubleshooting topic](https://www.ibm.com/support/knowledgecenter/SSYKE2_7.0.0/com.ibm.java.lnx.70.doc/troubleshooting.html){: external} in the {{site.data.keyword.IBM_notm}} JVM documentation to learn more about the snap traces or other diagnostic information that is generated by the JVM.

Updated Node.js buildpack v1.3-20140821-1143
:   The newest Node.js buildpack now comes with {{site.data.keyword.IBM_notm}} SDK for Node.js v1.1.0.6. This update means you will get a fully supported {{site.data.keyword.IBM_notm}} Node.js runtime when you specify the latest stable Node.js runtime, v0.10.30, for your app. This runtime fixes the [V8 Memory Corruption vulnerability](https://nodejs.org/en/blog/vulnerability/v8-memory-corruption-stack-overflow/){: external}.

    The buildpack also includes improvements and bug fixes to the Monitoring and Analytics service extension, allowing you to diagnose performance and error conditions through the service.


## 29 July 2014
{: #cloud-foundry-public-jul2914}
{: release-note}

Updated Liberty Buildpack v1.1-20140725-1341
:   The new version of Liberty’s {{site.data.keyword.cloud_notm}} Edition is here!
    
    * With this version of Liberty, there are fixes in addition to new features that allow you to consume {{site.data.keyword.cloud_notm}} services more effectively!
    
    * With the new CouchDB feature available, the Cloudant® service can now automatically configure it so that a connector object is handily available! Parsing through `VCAP_SERVICES` and providing the `ektorp` client `.jar` files are no longer necessary.

    * The new version of {{site.data.keyword.IBM_notm}} SDK for Java is here!
        
        * When your apps are pushed again, they use {{site.data.keyword.IBM_notm}} SDK for Java Version 7.1-1.0. This comes with a substantial performance upgrade. Your app shows better throughput and reduced memory usage. See more about the {{site.data.keyword.IBM_notm}} Java SDK [here](https://www.ibm.com/support/pages/node/508269){: external}.

Updated Node.js buildpack v1.1-20140717-1447
:   The Node.js buildpack now comes with {{site.data.keyword.IBM_notm}} SDK for Node.js v1.1.0.5. This update means you'll get a fully supported {{site.data.keyword.IBM_notm}} Node.js runtime when you specify the latest stable Node.js runtime for your app, v0.10.29. See more about the [{{site.data.keyword.IBM_notm}} Node.js SDKs](https://developer.ibm.com/languages/node-js/articles/download-nodejs-for-ibm-platforms/){: external}.

