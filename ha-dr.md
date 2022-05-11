---

copyright:
  years: 2015, 2022
lastupdated: "2022-05-11"

keywords: HA for cloud foundry, DR for cloud foundry, high availability for cloud foundry, disaster recovery for cloud foundry, failover for cloud foundry

subcollection: cloud-foundry-public

---

{{site.data.keyword.attribute-definition-list}}

# Understanding high availability and disaster recovery for {{site.data.keyword.ibmcf_notm}}
{: #ha-dr}

{{site.data.keyword.ibmcf_full}} provides high availability and disaster recovery that complies with {{site.data.keyword.cloud}} standards.
{: shortdesc}

When you run a single instance of an app the app is not guaranteed to be available all the time.  For example, the app might be unavailable during system upgrades.  With no additional instances the app will be unavailable when the system is down.

Apps can also slow down when they receive a large numbers of requests.

To help with these issues you can make sure your app has the resources it needs and is highly available (HA).  To make your app highly available your app will need to be deployed in a way to maximize the possibility that an instance is always ready to respond to a user's request.

All {{site.data.keyword.cloud}} general availability (GA) services that are deployed in a single region have a Service Level Agreement (SLA) of 99.9% availability. {{site.data.keyword.ibmcf_notm}} is a GA service that is offered in five regions: Dallas, Washington, Frankfurt, London, and Sydney. Each location has three different data centers for redundancy. The data for each location is stored in the three data centers near that location. If all the data centers in a location fail, the {{site.data.keyword.ibmcf_notm}} service for that location will be unavailable.

To increase your SLA to 99.99% you must deploy your app in multiple regions.

## High availability in a single region

To ensure your app is responsive and highly available for basic operations and performance, complete the following steps:

1. Make sure your app is stateless and handles multiple connections. For more information about the best practices for constructing an app, see [The Twelve-Factor App](https://12factor.net/){: external}.

2. Deploy two or more instances of your app.  Optimally, you want to deploy at least three instances, which is a standard {{site.data.keyword.cloud}} deployment.  Your instances are deployed to multiple hardware-isolated Availability Zones in a single {{site.data.keyword.cloud}} multi-zone region; for example, `US-SOUTH` or `EU-DE`.

## High availability by using multiple regions

To ensure your app is the most responsive and has the highest availability, complete the following steps:

1. Make sure your app is stateless and handles multiple connections. For more information about the best practices for constructing an app, see [The Twelve-Factor App](https://12factor.net/){: external}.

2. Deploy two or more instances of your app in multiple regions.  Optimally, you want to deploy at least three instances in each region, which is a standard {{site.data.keyword.cloud}} deployment for a region.  Your instances are  deployed to multiple hardware-isolated Availability Zones in each {{site.data.keyword.cloud}} multi-zone region; for example, `US-SOUTH` and `EU-DE`.

3. Use a global load balancer.  

    {{site.data.keyword.ibmcf_notm}} provides a load balancer to balance traffic within a single region. To balance traffic across multiple regions you must use a global load balancer such as [{{site.data.keyword.cloud}} Internet Services](/docs/cis?topic=cis-getting-started).  
   
    Each app that is deployed in a region is a separate URL target.  A global load balancer connects multiple URLs and spreads the load over multiple regions.

## Scaling instances depending on load

After you have a high-availability deployment, you can optimize your environment.  For example, you might not need full capacity in every region. By scaling down regions that do not handle your primary workload you can save money on those regions and then autoscale the regions when those regions need to handle more traffic.

Not every app requires the capability to monitor app performance but most benefit from monitoring.  Monitoring ensures that your app can keep up with the usage load.

{{site.data.keyword.ibmcf_notm}} can [dynamically scale](/docs/cloud-foundry-public?topic=cloud-foundry-public-autoscale_cloud_foundry_apps) your app instances as usage changes over time.  Autoscaling automatically increases or decreases the capacity of your app.  The number of app instances are dynamically adjusted based on defined policies.

## Try it out

You can try out configuring high availability by using the following labs:

* [High availability in a single region](https://ibm.ent.box.com/notes/344432520384?s=qw9hjyrwd1bm0t8pnegvekdq08y3ubu9){: external}

* [High availability in multiple regions](https://ibm.ent.box.com/notes/344405888320?s=he7jr9pt5o6rlvk813nlbm3z1m0eyv33){: external}

* [Scaling instances depending on load](https://ibm.ent.box.com/notes/302764242833?s=8fybw54tw7i6oq7luqugj6i1m8bbzp4l){: external}

## Related links

See [how {{site.data.keyword.cloud_notm}} ensures high availability and disaster recovery](/docs/overview?topic=overview-zero-downtime#zero-downtime). You can also find more information about [Service Level Agreements](/docs/overview?topic=overview-slas).  


