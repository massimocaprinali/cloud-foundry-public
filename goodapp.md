---

copyright:
  years: 2015, 2022
lastupdated: "2022-05-11"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}

# What makes a good Cloud Foundry app?
{: #goodapp}


Modern cloud apps, including those using Cloud Foundry, follow key development methodologies: cloud platforms, agile development, DevOps, microservices, and continuous delivery.

To follow these methodologies, you want to have a Platform-as-a-Service (PaaS) model. Although not  required, PaaS makes things a lot easier. Most cloud customers are using or start out with infrastructure-as-a-service (IaaS), which helps abstract their apps from the underlying hardware. However, PaaS adds an extra layer to abstract the underlying OS, so you can focus entirely on the business logic of your app and not worry about managing the platform.

There are two major concepts that come into play: "cloud-native" apps and "12 Factor apps".


## Cloud-Native
{: #cloudnative}

A "cloud-native" app is defined by the Cloud Native Computing Foundation.

* “Cloud-native technologies empower organizations to build and run scalable apps in modern, dynamic environments such as public, private, and hybrid clouds. Containers, service meshes, microservices, immutable infrastructure, and declarative APIs exemplify this approach.

* These techniques enable loosely coupled systems that are resilient, manageable, and observable. Combined with robust automation, they allow engineers to make high-impact changes frequently and predictably, with minimal toil.”

So a "cloud-native" app isn't just an "app". It's a set of processes and best practices that also go along with it. The transformation of the development processes is critical.  The "development ecosystem" is quickly learning the best ways to deliver software, and that is an important part of the latest app creation process.

So let's overview the important points about cloud-native apps:

* Apps are highly connected with various technologies and architectures, such as containers, container orchestration, microservices, and declarative APIs.
* Apps are built to run on modern infrastructures, typically "clouds". The cloud can be an external cloud vendor, or your own internal cloud environment.
* Building cloud-native apps is critically a practice and philosophy, not just a technology choice - it's about changing the way software is delivered in a DevOps and automation culture.
* They represent the dynamic and distributed nature of computing today, and the need for increased deployment speed, flexibility, agility, scalability, reliability, and security.


## 12 Factor App
{: #12factor}

As explained by the original concept creator:

*"Twelve Factor apps are built for agility and rapid deployment, enabling continuous delivery and reducing the time and cost for new developers to join a project. They are designed to use the principles of modern cloud platforms while permitting maximum portability between projects. Finally, they can scale up without significant changes to tooling, architecture, or development practices"*

The 12 factor apps check-list is a set of guidelines that dictate how an app is built to properly support the concept of independently-managed and iterated services.

The [12 factors website](https://12factor.net){: external} describes the 12 factors as:

1. One codebase tracked in revision control, many deployments.
2. Explicitly declare and isolate dependencies.
3. Store configuration in the environment.
4. Treat backing services as attached resources.
5. Strictly separate build and run stages.
6. Run the app as one or more stateless processes.
7. Export services by port binding.
8. Scale out using the process model.
9. Maximize robustness with fast startup and graceful shutdown.
10. Keep development, staging, and production as similar as possible.
11. Treat logs as Event Streams.
12. Run admin or management tasks as one-off processes.

These steps allow a maturing development organization to start adopting the range of cloud-native capabilities and create highly capable and flexible cloud apps.


