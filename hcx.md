---
copyright:
  years: 2024
lastupdated: "2025-03-19"

keywords:

subcollection: hcx-migration-vmware

---

{{site.data.keyword.attribute-definition-list}}

# Migrate with HCX
{: #hcx}

VMware HCX on IBM Cloud is a robust solution for seamless workload migration and application mobility between on-premises VMware environments and IBM Cloud. It enables enterprises to modernize infrastructure with minimal downtime by automating large-scale live migrations and optimizing network performance. HCX provides secure, encrypted connectivity, simplifying hybrid cloud adoption without requiring application refactoring. Integrated with IBM Cloud for VMware Solutions, it ensures high availability, scalability, and operational consistency. Businesses benefit from reduced migration complexity, lower costs, and enhanced disaster recovery capabilities, making it ideal for enterprises transitioning to a hybrid or multi-cloud architecture.


## IBM Cloud VMWare overview
{: #ibmcloud-overview}

### HCX Overview
{: #hcxoverview}

VMware HCX on IBM Cloud: 

VMware HCX (Hybrid Cloud Extension) on IBM Cloud is a powerful solution designed to simplify and automate the migration of VMware-based workloads between on-premises data centers and IBM Cloud. It enables enterprises to seamlessly extend, migrate, and modernize applications across hybrid cloud environments with minimal disruption.

What is VMware HCX? VMware HCX is a multi-cloud application mobility platform that enables businesses to securely migrate workloads between different VMware environments. It abstracts the underlying infrastructure, allowing seamless workload mobility, disaster recovery, and hybrid cloud operations without requiring application refactoring.

When deployed on IBM Cloud, VMware HCX facilitates the movement of workloads from on-premises VMware environments to IBM’s global cloud infrastructure. This helps enterprises leverage IBM Cloud’s scalability, high availability, and security while maintaining compatibility with their existing VMware workloads.
Please visit thte following link for further reading on HCX.

HCX seamlessly extends the networks of on-premises data centers into IBM Cloud, which enables you to migrate virtual machines (VMs) to and from the IBM Cloud without any conversion or change. HCX creates an abstraction layer that enables application mobility and infrastructure hybridity through securely stretched networks. You can modernize your VMware environment from VMware vSphere v5.1 to the most recent vSphere version without having to refractor or modify your existing application. HCX allows you to bring your IP subnet ranges into IBM Cloud, which ensures IP consistency through a hybrid deployment, and it also provides high level security with end-to-end suite B encryptions.

[HCX Overview on IBM Cloud](https://cloud.ibm.com/docs/vmwaresolutions?topic=vmwaresolutions-hcx_considerations)

Key Features and Benefits

Seamless and Live Workload Migration VMware HCX on IBM Cloud supports multiple migration types, including:

- HCX vMotion – Live migration of virtual machines (VMs) without downtime. 
- HCX Bulk Migration – Scheduled migration of multiple VMs with minimal disruption. 
- HCX Replication-Assisted vMotion (RAV) – Combines replication and vMotion for efficient migration. 
- HCX Cold Migration – Moves powered-off VMs in bulk. 

These capabilities allow organizations to move workloads to the cloud without major reconfiguration or performance impact.

1.  Hybrid Cloud Mobility HCX provides an automated and secure extension of VMware environments between on-premises data centers and IBM Cloud. It creates high-performance, encrypted network tunnels between environments, enabling workload mobility without network reconfiguration.
2.  Disaster Recovery and Business Continuity With HCX Disaster Recovery (HCX DR), organizations can protect their applications by replicating workloads between on-premises and IBM Cloud. This ensures business continuity and minimizes downtime during unplanned outages.
3.  Network Extension and Optimization HCX’s Layer 2 network extension allows businesses to extend on-premises VLANs to IBM Cloud without changing IP addresses. Additionally, WAN optimization improves performance, reducing latency and bandwidth consumption during migration.
4.  Simplified Operations and Automation HCX simplifies workload migration with an intuitive interface, reducing manual efforts and operational complexity. It automates VM movement, ensuring faster cloud adoption without impacting productivity.

### Use Cases
{: #usecases}

1.  Cloud Migration Enterprises can migrate large-scale VMware workloads to IBM Cloud without re-architecting applications. This accelerates digital transformation while maintaining operational consistency.
2.  Data Center Extension HCX enables organizations to extend their existing VMware environment to IBM Cloud, providing additional capacity without upfront hardware investment.


### Deployment Models on IBM Cloud:


**IBM Cloud for VMware Solutions Dedicated:** A single-tenant model offering higher levels of isolation for enhanced security and compliance readiness. This model is ideal for organizations requiring dedicated resources and greater control over their environment.

**IBM Cloud for VMware Cloud Foundation (VCF):** Provides a fully integrated VMware software-defined data center (SDDC) stack, including vSphere, vSAN, NSX-T, and HCX, deployed on IBM Cloud's Virtual Private Cloud (VPC) infrastructure. This deployment supports both consolidated and standard architecture models, allowing flexibility based on organizational needs.

- [Architecture](https://cloud.ibm.com/docs/vmwaresolutions?topic=vmwaresolutions-hcx-archi-overview)
- [Ordering HCX](https://cloud.ibm.com/docs/vmwaresolutions?topic=vmwaresolutions-hcx_ordering)
- [HCX Architecture-VCF on VPC](https://cloud.ibm.com/docs/vmwaresolutions?topic=vmwaresolutions-arch-pattern-vcf-hcx-con)
- [HCX site peering & service mesh in IBM Cloud](https://cloud.ibm.com/docs/vmwaresolutions?topic=vmwaresolutions-arch-pattern-vcf-hcx-xconnectivity)

## Pre-Requisites for Migration

Deploying VMware HCX for migration requires meeting specific prerequisites on both the client-side (on-premises) and server-side (IBM Cloud). Ensuring these requirements are met is crucial for a seamless migration experience.

### On-Premises Requirements
- [Source site](https://cloud.ibm.com/docs/vmwaresolutions?topic=vmwaresolutions-hcx-archi-source)
- [Client Deployment setup](https://cloud.ibm.com/docs/vmwaresolutions?topic=vmwaresolutions-hcxclient-planning-prep-install)

### IBM Cloud Requirements
- [Target site with NSX-V deployments](https://cloud.ibm.com/docs/vmwaresolutions?topic=vmwaresolutions-hcx-archi-target-v)
- [Target site with NSX-T deployments](https://cloud.ibm.com/docs/vmwaresolutions?topic=vmwaresolutions-hcx-archi-target-t)


### Network Connectivity Requirements 

-   IBM Cloud Direct Link for private, high-speed connectivity.
-   VPN for low speed secure site-to-site communication.
-   NSX-T or NSX-V integration for network segmentation and security enforcement.
-   Public IPs (if required for public-facing workloads).
-   Proper firewall and security policies configured to allow necessary traffic.
-   [Network Port Requirements](https://cloud.ibm.com/docs/vmwaresolutions?topic=vmwaresolutions-hcx-archi-port-req)
-   To extend on-premises networks to IBM Cloud.We must connect to a vSphere Distributed Switch (vDS) at on-premises.


Here’s a **refined whitepaper-style section** that removes "architectural decisions" language while maintaining a formal and structured tone:  

---

## **VMware HCX Deployment Technical Considerations**  

Successful deployment of **VMware HCX** for cloud migration requires careful planning across several key areas, including **network connectivity, migration methods, licensing, security, and performance optimization**. This section outlines the critical factors to consider when implementing **HCX for workload mobility** to **IBM Cloud**.  

### **Network Connectivity**  

Reliable and high-performance connectivity is essential for **secure and efficient workload migration**. HCX supports multiple connectivity options:  
- **HCX over VPN (IPsec/SSL VPN)** – Suitable for **proof of concept (PoC), development, or small-scale migrations**.  
- **HCX over IBM Cloud Direct Link** – Provides **higher bandwidth, lower latency, and improved security** by avoiding public internet exposure.  

For **production environments**, **IBM Cloud Direct Link** is the recommended approach due to its **SLA-backed performance and reliability**.  

### **Migration Methods**  

VMware HCX provides multiple migration techniques to accommodate **different workload requirements, availability needs, and operational constraints**:  
- **HCX vMotion** – Enables **live migration** with zero downtime, best suited for **critical workloads requiring continuous availability**.  
- **Replication Assisted vMotion (RAV)** – Uses replication technology to achieve **near-zero downtime**, making it ideal for **enterprise applications**.  
- **Bulk Migration** – Designed for **large-scale workload moves** where **scheduled downtime** is acceptable.  
- **Cold Migration** – Requires **complete VM downtime**, primarily used for **non-production workloads** or maintenance scenarios.  
- **OS Assisted Migration** – Allows the migration of **non-vSphere workloads**, extending HCX’s capabilities beyond traditional VMware environments.  

### **HCX Licensing and Feature Enablement**  

HCX is available in two licensing tiers, each providing different levels of capability:  
- **HCX Advanced** – Includes **basic migration features**.  
- **HCX Enterprise** – Offers **enhanced capabilities**, including **stretched networks, mobility groups, and large-scale migration support**.  

For large-scale migrations with **complex network dependencies**, **HCX Enterprise** is recommended due to its **expanded feature set**.  

### **Security and Compliance Considerations**  

Data security is a key concern when migrating workloads across hybrid environments. HCX provides multiple mechanisms to ensure data integrity:  
- **VPN Encryption (IPsec/SSL)** – Protects **data in transit** when using public networks.  
- **Direct Link Encryption** – Provides **private connectivity** with enhanced security by eliminating exposure to the public internet.  

Both options ensure **secure data transfer**, but **Direct Link** is preferred for **higher security, performance, and compliance adherence**.  

### **Network Extension and IP Management**  

Maintaining **Layer 2 network connectivity** during migration is critical to avoid reconfiguration of applications and minimize disruption:  
- **Network Extension Service** – Preserves **existing IP and MAC addresses**, ensuring seamless migration without requiring network changes.  
- **Re-IP Workflows** – Applied when IP conflicts arise, requiring address reassignment.  

For most use cases, **Network Extension Service** is recommended as it **simplifies migration and reduces reconfiguration efforts**.  

### **Performance Optimization with WAN Acceleration**  

To optimize network efficiency, HCX includes **built-in WAN acceleration features**:  
- **Deduplication** – Eliminates redundant data transmission to improve throughput.  
- **Compression** – Reduces the data footprint for faster migration over constrained network links.  

These features should be **enabled in environments with limited bandwidth** to enhance performance. In **high-bandwidth environments**, disabling WAN optimization can **reduce processing overhead** without impacting migration speed.  

---


[HCX supported platforms](https://cloud.ibm.com/infrastructure/vmware-solutions/console/newserviceentry/HCX/vcs_nsx_t): 

    -   vSphere v5.1,v5.5
    -   vSphere 6.0,6.5,6.7
    -   vSphere 7.0
    -   vSphere 8.0

## Conclusions

Migrating VMware workloads to IBM Cloud using HCX provides a robust and flexible solution for enterprises seeking to migrate workloads from On premises to IBM Cloud for  rehosting application workloads with cloud agility.With HCX, you can migrate workloads from vSphere and non-vSphere (KVM and Hyper-V) environments to IBM Cloud with zero downtime and enable moving applications to the latest VCF software and hardware environment.

## References

- [Vmware HCX on IBM Cloud](https://cloud.ibm.com/docs/vmwaresolutions?topic=vmwaresolutions-hcx_considerations)
- [Vmware Solutions on IBM Cloud](https://cloud.ibm.com/docs/vmwaresolutions)
- [Offical HCX Documentation from Broadcom](https://techdocs.broadcom.com/us/en/vmware-cis/hcx.html)
