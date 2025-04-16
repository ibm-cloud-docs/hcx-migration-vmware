---
copyright:
  years: 2025
lastupdated: "2025-04-16"

keywords:

subcollection: hcx-migration-vmware

---

{{site.data.keyword.attribute-definition-list}}

# Migrate with HCX
{: #hcx}

## VMware HCX Overview
{: #hcx-overview}

VMware HCX on IBM Cloud is a robust solution for seamless workload migration and application mobility between on-premises VMware environments and IBM Cloud. It enables enterprises to modernize infrastructure with minimal downtime by automating large-scale live migrations and optimizing network performance. HCX provides secure, encrypted connectivity, simplifying hybrid cloud adoption without requiring application refactoring. Integrated with IBM Cloud for VMware Solutions, it ensures high availability, scalability, and operational consistency. Businesses benefit from reduced migration complexity, lower costs, and enhanced disaster recovery capabilities, making it ideal for enterprises transitioning to a hybrid or multi-cloud architecture.

Please visit the following link for further reading on HCX, [VMware HCX](https://www.vmware.com/products/cloud-infrastructure/hcx){: external}. Also visit [VCF CORE TECH](https://vcfcore.tech){: external}, a blog with extensive HCX information.

## IBM Cloud VMware overview
{: #hcx-ibmcloud-overview}

IBM Cloud for VMware Solutions is a cloud-based offering that allows organizations to extend or migrate their existing VMware-based virtualized datacenters to the IBM Cloud. The solution offers different deployment options, including self-managed and managed models, and can be used for both virtualized and cloud-native applications. Key features and benefits include the following:

* Extending Existing Datacenters - The solution facilitates extending on-premises VMware environments to the cloud, allowing for flexible capacity management and resource allocation. 
* Migration to the Cloud - It supports the migration of existing VMware workloads to the cloud, enabling businesses to modernize their infrastructure and leverage cloud services. 
* Disaster Recovery and Business Continuity - IBM Cloud for VMware Solutions can serve as a cost-effective disaster recovery site or provide off-site backup options, enhancing business resilience. 
* Cloud Native Applications - The solution can host cloud-native applications alongside traditional VMware workloads, providing a unified platform for different application types. 
* Flexibility and Scalability- The solution offers flexibility in deployment options and allows for scaling resources up or down as needed, based on workload demands. 
* Security and Compliance - The solution provides a secure and compliant platform for running VMware workloads, with options for enhanced security features. 
* Deployment Models:
    * Self-managed - Provides single-tenant, bare-metal infrastructure with full control over the hypervisor and vCenter Server, ideal for organizations needing high levels of isolation and control. 
    * Managed - Utilizes VMware Cloud Director for a managed, cost-effective solution, ideal for cost-conscious organizations or those needing quick migration of VMs to the cloud.
* Management and Control - With the self-managed model, customers have access to the native VMware stack to manage resources and workloads, similar to their on-premises environments. In the managed model, IBm manages up to and including the hypervizor so that customers can focus on the workloads

IBM Cloud for VMware Solutions provides a comprehensive platform for extending and migrating VMware workloads to the cloud, offering a flexible and secure environment for running various types of applications. 

### Overview
{: #hcx-ibmcloud-overview-overview}

VMware HCX (Hybrid Cloud Extension) on IBM Cloud is a powerful solution designed to simplify and automate the migration of VMware-based workloads between on-premises data centers and IBM Cloud. It enables enterprises to seamlessly extend, migrate, and modernize applications across hybrid cloud environments with minimal disruption.

VMware HCX is a multi-cloud application mobility platform that enables businesses to securely migrate workloads between different VMware environments. It abstracts the underlying infrastructure, allowing seamless workload mobility, and hybrid cloud operations without requiring application refactoring.

When deployed on IBM Cloud, VMware HCX facilitates the movement of workloads from on-premises VMware environments to IBM’s global cloud infrastructure. This helps enterprises leverage IBM Cloud’s scalability, high availability, and security while maintaining compatibility with their existing VMware workloads.

HCX provides the flexibility of extending the networks of on-premises data centers into IBM Cloud, enabling the migration of virtual machines (VMs) to and from the IBM Cloud without any conversion or change. HCX creates an abstraction layer that enables application mobility and infrastructure hybridity through securely stretched networks. You can modernize your VMware environment from legacy VMware vSphere software versions to the most recent vSphere version without having to refractor or modify your existing application. HCX allows you to bring your IP subnet ranges into IBM Cloud, which ensures IP consistency through a hybrid deployment, and it also provides high level security with end-to-end suite B encryptions.

For further information regarding HCX on IBM Cloud please follow this link [HCX Overview on IBM Cloud](/docs/vmwaresolutions?topic=vmwaresolutions-hcx_considerations).

### Key Features and Benefits
{: #hcx-ibmcloud-overview-benifits}

The following are the key features and benefits of VMware HCX:

* Seamless and live workload migration.
* VMware HCX on IBM Cloud supports multiple migration types in line to your business requirement.
* Allows organizations to move workloads to the cloud without major reconfiguration or performance impact.
* Hybrid cloud mobility provides an automated and secure extension of VMware environments between on-premises data centers and IBM Cloud. It creates high-performance, encrypted network tunnels between environments, enabling workload mobility without network reconfiguration.
* Network Extension, HCX’s Layer 2 network extension allows businesses to extend on-premises VLANs to IBM Cloud without changing IP addresses.
* WAN optimization improves performance, reducing latency and bandwidth consumption during migration.
* With simplified operations and automation, HCX simplifies workload migration with an intuitive interface, reducing manual efforts and operational complexity. It automates VM movement, ensuring faster cloud adoption without impacting productivity.

### Use Cases
{: #hcx-ibmcloud-overview-usecases}

Typically HCX in OBM Cloud is used in the following usecases:

1.  Cloud Migration - Enterprises can migrate large-scale VMware workloads to IBM Cloud without re-architecting applications. This accelerates digital transformation while maintaining operational consistency.
2.  Data Center Extension - HCX enables organizations to extend their existing VMware environment to IBM Cloud, providing additional capacity without upfront hardware investment.

### Deployment Models on IBM Cloud:
{: #hcx-ibmcloud-overview-deployment}

While IBM Cloud has a number of VMware offering, only the following offer suitable deployment models for VMware HCX

**VMware Cloud Foundation for Classic - Automated:** A single-tenant, self-managed, automated build model offering higher levels of isolation for enhanced security and compliance readiness. The offering is an integrated VMware software-defined data center (SDDC) stack, including vSphere, NSX-T and optionally vSAN. This model is ideal for organizations requiring dedicated resources and greater control over their environment. VMware HCX can be automatically deployed onto this platform.

**VMware Cloud Foundation for Classic - Flexible:** A single-tenant, self-managed, manual build model offering clients with in-depth skills to build their own environment on top of vSphere according to their architecture needs. VMware HCX can be manually deployed onto this platform.

**IBM Cloud for VMware Cloud Foundation (VCF) on VPC:** A single-tenant, self-managed, automated build model deployed on IBM Cloud's Virtual Private Cloud (VPC) infrastructure. It provides a fully integrated VMware VCF stack, including vSphere, vSAN, NSX-T, and SDDC Manager. HCX can be manually installed. This deployment can support both VCF consolidated and VCF standard architecture models, allowing flexibility based on organizational needs.

- [Architecture](/docs/vmwaresolutions?topic=vmwaresolutions-hcx-archi-overview)
- [Ordering HCX](/docs/vmwaresolutions?topic=vmwaresolutions-hcx_ordering)
- [HCX Architecture-VCF on VPC](/docs/vmwaresolutions?topic=vmwaresolutions-arch-pattern-vcf-hcx-con)
- [HCX site peering & service mesh in IBM Cloud](/docs/vmwaresolutions?topic=vmwaresolutions-arch-pattern-vcf-hcx-xconnectivity)

## Pre-Requisites for Migration
{: #hcx-prereq}

Deploying VMware HCX for migration requires meeting specific prerequisites on both the source side (on-premises) and target side (IBM Cloud). Ensuring these requirements are met is crucial for a seamless migration experience.

### On-Premises Requirements
{: #hcx-prereq-onprem}

Review the following documents:

- [Source site](/docs/vmwaresolutions?topic=vmwaresolutions-hcx-archi-source)
- [Client Deployment setup](/docs/vmwaresolutions?topic=vmwaresolutions-hcxclient-planning-prep-install)

### IBM Cloud Requirements
{: #hcx-prereq-cloud}

Review the following document:

- [Target site with NSX-T deployments](/docs/vmwaresolutions?topic=vmwaresolutions-hcx-archi-target-t)

### Network Connectivity Requirements
{: #hcx-prereq-networking}

The following define the network connectivity requirements:

- Internet connectivity to enable registration and product updates, and optionally network extension and migration.
- Optionally, IBM Cloud Direct Link for private, high-speed connectivity for network extension and migration.
- The target site requires NSX-T integration for network segmentation and security enforcement.
- Public IPs (if required for public-facing workloads).
- Proper firewall and security policies configured to allow necessary traffic.
- For further networking port configuration and understanding the requirement, visit the following link [Network Port Requirements](/docs/vmwaresolutions?topic=vmwaresolutions-hcx-archi-port-req)
-   To extend on-premises networks to IBM Cloud, HCX must connect to a vSphere Distributed Switch (vDS) or NSX-T on-premises.

## VMware HCX Deployment Technical Considerations  
{: #hcxconsideration}

Successful deployment of VMware HCX for cloud migration requires careful planning across several key areas, including network connectivity, migration methods, licensing, security, and performance optimization**. This section outlines the critical factors to consider when implementing HCX for workload mobility to IBM Cloud.  

### Network Connectivity
{: #hcx-prereq-networkconnectivity}

Reliable and high-performance connectivity is essential for secure and efficient workload migration. HCX supports multiple connectivity options:

- HCX over the Internet – Suitable for proof of concept (PoC), development, or small-scale migrations. HCX over a VPN is not recommended due to the additional overheads of the VPN. HCX uses encryption to protect the network extension or migration data transfer.  
- HCX over IBM Cloud Direct Link – Provides higher bandwidth, lower latency, and improved security by avoiding public internet exposure.  

For production environments, IBM Cloud Direct Link is the recommended approach due to its SLA-backed performance and reliability.  

### Migration Methods
{: #hcx-prereq-migrationmethods}

VMware HCX provides multiple migration techniques to accommodate different workload requirements, availability needs, and operational constraints: 

- HCX vMotion – Enables live migration with zero downtime, best suited for critical workloads requiring continuous availability.  
- Replication Assisted vMotion (RAV) – Uses replication technology to achieve near-zero downtime, making it ideal for enterprise applications.  
- Bulk Migration – Designed for large-scale workload moves where scheduled downtime is acceptable.  
- Cold Migration – Requires complete VM downtime, primarily used for non-production workloads or maintenance scenarios.  
- OS Assisted Migration – Allows the migration of non-vSphere workloads, extending HCX’s capabilities beyond traditional VMware environments.  
 

### Security and Compliance Considerations  
{: #hcx-prereq-security}

Data security is a key concern when migrating workloads across hybrid environments. HCX provides multiple mechanisms to ensure data integrity:

- Suite-B encryption – Secures all in-flight data using military-grade Suite-B encryption.  
- Direct Link – Provides private connectivity with enhanced security by eliminating exposure to the public internet.  

### Network Extension and IP Management  
{: #hcx-prereq-network-extension}

Extending your network to IBM Cloud during migration is critical to avoid reconfiguration of applications and minimize disruption:

- Network Extension Service – Preserves existing IP and MAC addresses, ensuring seamless migration without requiring network changes.  
- Re-IP Workflows – Applied when IP conflicts arise, requiring address reassignment.  

For most use cases, Network Extension Service is leveraged as it simplifies migration and reduces reconfiguration efforts.  

### Performance Optimization with HCX WAN Acceleration
{: #hcx-prereq-optimization}

To optimize network efficiency, HCX includes built-in WAN acceleration features:

- Deduplication – Eliminates redundant data transmission to improve throughput.  
- Compression – Reduces the data footprint for faster migration over constrained network links. 


### vSphere Versions
{: #hcx-prereq-vsphere-versions}

See [HCX supported platforms](https://cloud.ibm.com/infrastructure/vmware-solutions/console/newserviceentry/HCX/vcs_nsx_t) for supported vSphere versions:

-   vSphere v5.1,v5.5
-   vSphere 6.0,6.5,6.7
-   vSphere 7.0
-   vSphere 8.0

## Conclusions
{: #hcx-conclusion}

Migrating VMware workloads to IBM Cloud using HCX provides a robust and flexible solution for enterprises seeking to migrate workloads from on-premises to IBM Cloud for re-hosting application workloads with cloud agility. With HCX, you can migrate workloads from vSphere and non-vSphere (KVM and Hyper-V) environments to IBM Cloud with zero downtime and enable moving applications to the latest VCF software and hardware environment.

## References
{: #hcx-reference}

- [VMware HCX on IBM Cloud](/docs/vmwaresolutions?topic=vmwaresolutions-hcx_considerations)
- [VMware Solutions on IBM Cloud](/docs/vmwaresolutions)
- [Official HCX Documentation from Broadcom](https://techdocs.broadcom.com/us/en/vmware-cis/hcx.html){: external}
