# **Cloud Services**

### **Benefits of using cloud services**
- High availability: Azure SLAs guarantee an extremely high service uptime, >99.9%.
- High scalability: Quickly able to adjust resources to meet demand. Cloud is a consumption-based model and you pay for what you need. Vertical Scaling (adjusting capabilities / power of resources) and Horizontal Scaling (adjusting number of resouces) are easy.
- High Reliability: Due to the cloud's decentralized nature, you can quickly deploy resouces around the world and adjust based on disasters or other events.
- Manageable Security & Governance: Easily configure and update policies to ensure deployed resources meet corporate standards and government regulatory requirements.

### **Cloud Service Types**
- Infrastructure as a Service (IaaS): Most flexible. Cloud provider maintains the hardware, connectivity to the internet, and phyiscal security. User is responsible for everything else (OS install, network config, data config, etc.)
- Platform as a Service (PaaS): Middle ground. Cloud provider maintains hardware, connectivity, physical security, OS maintenance, middleware, and BI services. User maintains data config and sometimes applications and directory infra.
- Software as a Service (SaaS): Most complete, essentially renting a fully developed app. Cloud provider maintains everything except data, accounts and identities, and sometimes identity infra.

### **Shared Responsibility Model**

<img width="853" height="503" alt="image" src="https://github.com/user-attachments/assets/fb56780a-8008-4d7e-9d00-0a59c776aaf6" />


# **Azure**

### **What is Azure?**
- Microsoft's collection of more than 100 cloud services. Allows you to do everything from running existing apps on VMs to exploring intelligent bots and mixed reality.
  
  <img width="604" height="479" alt="image" src="https://github.com/user-attachments/assets/69e1ea0e-6451-433c-89a3-f8afbff4b87f" />

### **Interacting with Azure**
- Web portal: portal.azure.com
- CLI: Started within the web portal. PowerShell and BASH can be used to interact with Azure. *Note: when using PowerShell, the command __az interactive__ can be used to make the CLI more IDE-esque with autocompetion, command descriptions, and examples.*

### **Azure Physical Infra**
- Datacenters: Facilities with dedicated power, cooling, and networking infra that run Azure. Located around the world and grouped into Azure Regions / Availability Zones to keep high resiliency and reliability
- Availability Zones: Physically separate datacenters within a region, each with their own power, cooling, and networking. Prevents a resource/application from going down in a region if a particular datacenter encounters a disaster.
- Regions: Geographical area on the planet that contains at least one, but generally multiple datacenters that are network together with low-latency. Used by Azure to ensure workloads are balanced.
- Region pairs: Pairs of regions within the same geography (US, Europe, Asia, etc.) that are at least 300 miles away from each other. Used for resource replication across a geopgrahy that helps reduce the likelihood of interruptions due to large-scale disasters.
- Sovereign Regions: Instances of Azure that are physical and logical network-isolated for compliance or legal purposes (ex. US DoD Central, US Gov Virginia).

<img width="1012" height="560" alt="image" src="https://github.com/user-attachments/assets/64fb25b6-b8ec-4b6c-8fd4-c153a157314c" />

### **Azure Management Infra**
- Resource: Anything you creat, provision, deploy, etc. in Azure. This includes VMs, virtual networks, databases, cognitive services, and more.
- Resource Group: A grouping of resources. Every resource has to be in a group, and can only be in one group at a time. Actions taken on a group (ex. permissions adjustments) apply to app resources in that group.
- Azure Subscriptions: A unit of management, billing, and scale. These allow you to organize your resource groups and facilitate billing.

<img width="654" height="269" alt="image" src="https://github.com/user-attachments/assets/6e768e61-1093-407e-b242-51897137e2a4" />

In a multi-subscription account, the subscriptions can be used to configure different billing models and apply different access-management policies. **Billing boundaries** are a subscription type that allows Azure to generate separate illing reports and invoices for each subscription so you can organize and manage costs. **Access control boundaries** are types that allows you to reflect different organizational structures (ex. you can manage and control access to the resources that users in a specific business department provision.)
- Management Groups: A collection of subscriptions that can have governance conditions applied to it.

In summary: Resources > Resource Groups > Subscriptions > Management Groups

<img width="608" height="376" alt="image" src="https://github.com/user-attachments/assets/bd5f4956-b548-48ec-8302-40ba18c08e0c" />
