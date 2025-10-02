# **AZ-900 Notes**

## **Cloud Services**

### **Definition**
- The delivery of convenient, on-demand computing services over the internet to a shared pool of configurable computing resources (VMs, apps, etc.) that can be quickly provisioned with minimal management effort.

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

### **Cloud Models**
- Public Cloud: Built, controlled, and maintained by a third-party CSP (ex. Microsoft, Amazon, etc.) General public availability. Anyone can purchase cloud services to access and use. Cost- effective.
- Private Cloud: A cloud used by a single entity/organization in an on-site datacenter or a dedicated offsite datacenter. Much greater control for the organization, but much more responsibility and cost.
- Hybrid Cloud: An environment that uses both public and private clouds in an inter-connected system. Allows for flexible security (ex. choosing which services to keep on public or private) and elasticity (ex. allowing a private cloud to surge for increased demand by deploying public cloud resources.)

### **Cloud Concept Definitions**
- Economies of Scale: The ability to do things more efficiently / lower cost-per-unit when operating at a larger scale
- Capital Expenditure (CapEx): Money spent on physical infra up front (ex. Physical On-Prem Datacenters)
- Operation Expenditure (OpEx): Money spent on services or products now and being billed as you go (ex. Public Cloud Consuption)
- Consumption-based Model: Paying for you what use (per-minute, per-GB, per-execution, etc.)
- Fixed-price Model: Provisioning resources and paying for them whether you use them or not
- Serverless Architecture: A consumption-based model where the CSP dynamically manages the allocation and provisioning of servers. Resources are stateless, servers are ephemeral, and often capable of being triggered (ex. Azure Logic App, Azure Functions, Azure Event Grid.)
