---
title: "Azure"
lastmod: 2022-10-08T00:00:00+08:00
draft: false
tags: [azure, cloud]
author: Brittany Ellich

toc:
  enable: true
  auto: true
---

## Cloud Computing

### Overview

* **Cloud Computing** is the delivery of computing services over the internet. Services include things like virtual machines, storage, databases, and networking.
* **The Shared Responsibility Model** is a description of the shared responsibilities between a cloud provider and the consumer. Physical security, power, cooling, and network connectivity are the responsibility of the cloud provider. The consumer is responsible for all the data and information stored in the cloud, as well as access security.
* **Cloud Models**:
  * Private cloud: A cloud that is built, controlled, and maintained by a single entity. Provides greater control for the company but is much more costly and provides fewer of the benefits of a public cloud.
    * Organizations have complete control over resources and security
    * Data is not collocated with other organizations' data
    * Hardware must be purchased for startup and maintenance
    * Organizations are responsible for hardware maintenance and updates
  * Public cloud: Built, controlled, and maintained by a third-party cloud provider. Anyone that wants to purchase cloud services can access and use resources.
    * No capital expenditures to scale up
    * Applications can be quickly provisioned and deprovisioned
    * Organizations pay only for what they use
    * Organizations don't have complete control over resources and security
  * Hybrid cloud: A computing environment that uses both poublic and private clouds in an inter-connected environment.
    * Provides the most flexibility
    * Organizations determine where to run their applications
    * Organizations control security, compliance, or legal requirements
  * Multi-cloud: You use multiple public cloud providers
* **Azure Arc**: A set of technologies that helps manage your cloud environment whether it's a public cloud only on Azure, a private cloud in your datacenter, a hybrid configuration, or event a multi-cloud environment running on multiple cloud providers at once

### Benefits of Cloud Computing

* **High Availability**: A focus on ensuring maximum availability, regardless of disruptions or events that may occur. Keep in mind SLAs to account for service availability in your system. 99.99% availability is available for SOME azure resources.
* **Scalability**: The ability to adjust resources to meet demand. You can scale up to handle increased demand, or scale down to save money on resources if demand drops off.
  * Vertical scaling focuses on increasing or decreasing the capabilities of existing resources
  * Horizontal scaling is adding or subtracting the number of resources
* **Reliability**: The ability of a system to recover from failures and continue to function. One of the pillars of the Microsoft Azure Well-Architected Framework. With a decentralized design, the cloud enables you to have resources deployed to regions around the world. If one region has a catastrophic event, other regions are still up and running.
* **Predictability**: Performance predictability focuses on predicting the resources needed to deliver apositive experience for your customers. Autoscaling, load balancing, and high availability are some of the cloud concepts that support performance predictability. Cost predictability is focused on predicting or forecasting the cost of the cloud spend.
* **Security and governance**: Cloud-based auditing helps flag any resourrce that's out of compliance with your corporate standards. Software patches and updates may also automatically be applied. You can use IaaS to maintain and secure your own resources.
* **Manageability**:
  * Management of the cloud: Managing your cloud resources, including auto scaling resources, deploying resources, monitoring their health, and receiving alerts based on configured metrics of your resources.
  * Management in the cloud: How you manage your cloud environment and resources, such as using the web portal, the CLI, APIs, or PowerShell.

### Cloud Service Types

* **Infrastructure as a Service**: Provides you the maximum amount of control for your cloud resources. The cloud provider is responsible for maintaining the hardware, network connectivity, and physical security. You're responsible for everything else (OS install, configuration and maintenance, network configuration, database and storage configuration, etc)
  * Scenarios where this may make sense:
    * Lift-and-shift migration: You're standing up cloud resources similar to your on-prem datacenter, and then simply move the things running on-prem to running on the IaaS infrastructure.
    * Testing and development: Replicating development and test environments
* **Platform as a Service**: The cloud provider maintains the physical infrastructure, physical security, connection to the internet, operating systems, middleware, development tools, and business intelligence services. You don't have to worry about licensing or patching.
  * Scenarios where this may make sense:
    * Development framework: Provides a framework that developers can build upon to develop or customize cloud-based applications.
    * Analytics of business intelligence: Allows organizations to analyze and mine their data, finding insights and patterns and predicting outcome to improve forecasting.
* **Software as a Service**: Renting or using a fully developed application.
  * Scenarios where this may make sense:
    * Email and messaging
    * Business and productivity applications
    * Finance and expense tracking

## Azure Overview

* [Azure Global Infrastructure](https://infrastructuremap.microsoft.com/)
* **Regions**: A region is a geographical area on the planet that contains at least one, but potentially multiple datacenters that are nearby and networked together with a low-latency network.
  * Region Pairs: Most Azure regions are paired with another region within the same geography, at least 300 miles away. Services can automatically fail over to the other region in its region pair if something were to affect one of the regions in the pair. Not all Azure services automatically replicate data or automatically fall back from a failed region to cross-replicate to another enabled region.
* **Availability Zones**: Physically separate datacenters within an Azure region. Each zone is made up of one or more datacenters equipped with independent power, cooling, and neworking. If one zone goes down, the other continues working. They are connected through high-speed private fiber-optic networks. Azure services fall into three categories regarding availability zones:
  * Zonal services: You pin the resource to a specific zone
  * Zone-redundant services: The platform replicates automatically across zones
  * Non-regional services: Services are always available from Azure geographies and are resilient to zone-wide outages as well as region-wide outages
* **Resource**: Anything you create, provision, deploy, etc., is a resource. Virtual Machines, virtual networks, database, cognitive services, etc., are all considered resources within Azure.
* **Resource Groups**: Groupings of resources. All resources are placed in a resource group. It's a convenient way to logically group resources together. When you apply an action to a resource group, that action will apply to all the resources within the resource group. You can use this for access management to the resources within the resource group.
* **Subscriptions**: A unit of management, billing, and scale. Allow you to logically organize your resource groups and facilitate billing. You can use subscriptions to define boundaries around Azure products, services, and resources. There are two types of subscription boundaries:
  * Billing Boundary: Determines how an Azure account is billed for using Azure. Azure generates separate billing reports and invoices for each subscription so that you can organize and manage costs.
  * Access Control Boundary: Access-management policies are applied at the subscription level, and you can create separate subscriptions to reflect different organizational structures.
* **Azure Management Groups**: A level of scope above subscriptions to apply governance across subscriptions (which apply governance across resource groups).

## Learning Resources

### Articles

* [ ] [Microsoft Azure Fundamentals: Describe cloud concepts learning path](https://learn.microsoft.com/en-us/training/paths/microsoft-azure-fundamentals-describe-cloud-concepts/)
* [ ] [Azure 204 Learning Path](https://learn.microsoft.com/en-us/training/paths/create-azure-app-service-web-apps/)
