---
copyright:
  years: 2024
lastupdated: "2025-03-06"

keywords:

subcollection: hcx-migration-vmware

---

{{site.data.keyword.attribute-definition-list}}

# Migrate with HCX
{: #hcx}

VMware HCX on IBM Cloud is a robust solution for seamless workload migration, disaster recovery, and application mobility between on-premises VMware environments and IBM Cloud. It enables enterprises to modernize infrastructure with minimal downtime by automating large-scale live migrations and optimizing network performance. HCX provides secure, encrypted connectivity, simplifying hybrid cloud adoption without requiring application refactoring. Integrated with IBM Cloud for VMware Solutions, it ensures high availability, scalability, and operational consistency. Businesses benefit from reduced migration complexity, lower costs, and enhanced disaster recovery capabilities, making it ideal for enterprises transitioning to a hybrid or multi-cloud architecture.

## IBM Cloud VMWare overview
{: #ibmcloud-overview}

### HCX Overview
{: #hcxoverview}

VMware HCX on IBM Cloud: 

VMware HCX (Hybrid Cloud Extension) on IBM Cloud is a powerful solution designed to simplify and automate the migration of VMware-based workloads between on-premises data centers and IBM Cloud. It enables enterprises to seamlessly extend, migrate, and modernize applications across hybrid cloud environments with minimal disruption.

What is VMware HCX? VMware HCX is a multi-cloud application mobility platform that enables businesses to securely migrate workloads between different VMware environments. It abstracts the underlying infrastructure, allowing seamless workload mobility, disaster recovery, and hybrid cloud operations without requiring application refactoring.

When deployed on IBM Cloud, VMware HCX facilitates the movement of workloads from on-premises VMware environments to IBM’s global cloud infrastructure. This helps enterprises leverage IBM Cloud’s scalability, high availability, and security while maintaining compatibility with their existing VMware workloads.
Please visit thte following link for further reading on HCX.

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
3.  Disaster Recovery Businesses can leverage IBM Cloud as a secondary site for disaster recovery, ensuring business continuity in case of on-premises failures.
4.  Application Modernization Once in IBM Cloud, workloads can be modernized with IBM’s AI, Kubernetes, and automation services, enabling businesses to innovate faster.

### Deployment Models on IBM Cloud:
{: #deploymentmodel}

**IBM Cloud for VMware Solutions Dedicated:** A single-tenant model offering higher levels of isolation for enhanced security and compliance readiness. This model is ideal for organizations requiring dedicated resources and greater control over their environment.

**IBM Cloud for VMware Cloud Foundation (VCF):** Provides a fully integrated VMware software-defined data center (SDDC) stack, including vSphere, vSAN, NSX-T, and HCX, deployed on IBM Cloud's Virtual Private Cloud (VPC) infrastructure. This deployment supports both consolidated and standard architecture models, allowing flexibility based on organizational needs.

**HCX supported platforms :** 

    -   vSphere v5.1,v5.5
    -   vSphere 6.0,6.5,6.7
    -   vSphere 7.0
    -   vSphere 8.0

## VMware HCX Deployment architecture/Key Components

Deploying VMware HCX requires details about your vSphere sites, networks, and configurations. VMware HCX includes a virtual management component at both the source and destination sites, along with various Interconnect service appliances. The HCX services are configured and activated at the source site, where virtual appliances are deployed. A corresponding peer appliance is then deployed at the destination site.

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


## VMware HCX Architectural Decisions

| **Architecture** | **Requirements** | **Options** | **Rationale** | **Decisions** |
|--------------------------|-----------------|-------------|---------------|---------------|
| **Networking** | **Connectivity Type** | - HCX over VPN (IPsec/SSL VPN) <br> - HCX over IBM Cloud Direct Link | IBM Cloud Direct Link ensures high bandwidth, low latency, enhanced security, and reliability. VPN is suitable for small-scale migrations or PoC. | **Direct Link**: Preferred for production workloads (high bandwidth, low latency, SLA-backed). <br> **VPN**: Suitable for PoC, dev/test, or small-scale migrations. |
| **Migration Type** | **Method Selection** | - HCX vMotion <br> - Replication Assisted vMotion (RAV) <br> - Bulk Migration <br> - Cold Migration <br> - OS Assisted Migration | Choose based on workload criticality, downtime tolerance, performance, and migration scale. | **HCX vMotion**: Zero downtime; ideal for **single VM live migration**. <br> **RAV**: Near-zero downtime; uses replica copy for **production workloads**. <br> **Bulk Migration**: Scheduled downtime; best for **non-critical large-scale migrations**. <br> **Cold Migration**: High downtime; use for **non-production or maintenance windows**. <br> **OS Assisted Migration**: Used for **bulk migration of guest (non-vSphere) virtual machines**. |
| **HCX Licenses** | **[License Model](https://techdocs.broadcom.com/us/en/vmware-cis/hcx/vmware-hcx/4-10/vmware-hcx-user-guide-4-10/vmware-hcx-services.html)** | - HCX Advanced <br> - HCX Enterprise | HCX Advanced provides basic services, while HCX Enterprise supports large-scale migrations with enhanced features. | **HCX Enterprise** recommended for **advanced features** (e.g., stretched networks, mobility groups). |
| **Security** | **Data Encryption & Compliance** | - VPN (IPsec/SSL encryption) <br> - Direct Link (private encryption) | Direct Link offers better security by avoiding public internet exposure. | Both options encrypt data **in transit**. **Direct Link** ensures a more secure migration. |
| **Network Extension** | **Layer 2 Stretch** | - Network Extension Service (retain IP/MAC) <br> - Re-IP workflows | L2 Extension prevents IP changes and minimizes security disruptions. Re-IP is used only if there's an IP conflict. | Use **Network Extension Service** for **zero IP changes**. Re-IP only if **network overlap** exists. |
| **WAN Optimization** | **Bandwidth Efficiency** | - Deduplication <br> - Compression | Enhances migration speed when bandwidth is limited. | Enable **WAN optimization** for **limited bandwidth**. Disable if **network bandwidth is sufficient**. |




## Conclusions

Migrating VMware workloads to IBM Cloud using HCX provides a robust and flexible solution for enterprises seeking to migrate workloads from On premises to IBM Cloud for  rehosting application workloads with cloud agility.With HCX, you can migrate workloads from vSphere and non-vSphere (KVM and Hyper-V) environments to IBM Cloud with zero downtime and enable moving applications to the latest VCF software and hardware environment.

## References

- [Vmware HCX on IBM Cloud](https://cloud.ibm.com/docs/vmwaresolutions?topic=vmwaresolutions-hcx_considerations)
- [Vmware Solutions on IBM Cloud](https://cloud.ibm.com/docs/vmwaresolutions)
- [Offical HCX Documentation from Broadcom](https://techdocs.broadcom.com/us/en/vmware-cis/hcx.html)
