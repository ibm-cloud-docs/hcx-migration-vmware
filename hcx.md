---
copyright:
  years: 2024
lastupdated: "2025-03-03"

keywords:

subcollection: hcx-migration-vmware

---

{{site.data.keyword.attribute-definition-list}}

# Migrate with HCX
{: #hcx}

This is a short description that introduces the content in this topic. {: shortdesc}

## IBM Cloud VMWare overview
{: #ibmcloud-overview}

### HCX Overview
{: #hcxoverview}

VMware HCX on IBM Cloud: [Overview](https://cloud.ibm.com/docs/vmwaresolutions?topic=vmwaresolutions-hcx_considerations)

VMware HCX (Hybrid Cloud Extension) on IBM Cloud is a powerful solution designed to simplify and automate the migration of VMware-based workloads between on-premises data centers and IBM Cloud. It enables enterprises to seamlessly extend, migrate, and modernize applications across hybrid cloud environments with minimal disruption.

What is VMware HCX? VMware HCX is a multi-cloud application mobility platform that enables businesses to securely migrate workloads between different VMware environments. It abstracts the underlying infrastructure, allowing seamless workload mobility, disaster recovery, and hybrid cloud operations without requiring application refactoring.

When deployed on IBM Cloud, VMware HCX facilitates the movement of workloads from on-premises VMware environments to IBM’s global cloud infrastructure. This helps enterprises leverage IBM Cloud’s scalability, high availability, and security while maintaining compatibility with their existing VMware workloads.

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

| **Architecture Decision** | **Requirements**            | **Options**                                                                          | **Decisions**                                                                                                                                                                                                                                                                                                            | **Rationale** |
|--------------------------|----------------------------|--------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------|
| **Networking**           | **Connectivity Type**       | - HCX over VPN (IPsec/SSL VPN) <br> - HCX over IBM Cloud Direct Link                 | **Direct Link**: Preferred for production workloads (high bandwidth, low latency, SLA-backed). <br> **VPN**: Suitable for PoC, dev/test, or small-scale migrations.                                                                                                             | VPN maybe used for small-scale migrations, IBM Cloud Direct Link is recommended for VMware HCX migration due to its high bandwidth, low latency, enhanced security, and reliability. It ensures seamless workload mobility, reduces migration risks, and supports long-term hybrid cloud operations efficiently. |
| **Migration Type**       | **Method Selection**        | - HCX vMotion <br> - Replication-Assisted vMotion (RAV) <br> - Bulk Migration <br> - Cold Migration <br> - OS Assisted Migration | **HCX vMotion**: Zero downtime; ideal for **single VM live migration**. <br> **RAV**: Near-zero downtime; uses replica copy for **production workloads**. <br> **Bulk Migration**: Scheduled downtime; best for **non-critical large-scale migrations**. <br> **Cold Migration**: High downtime; use for **non-production or maintenance windows**. <br> **OS Assisted Migration**: Used for the **bulk migration of guest (non-vSphere) virtual machines**. | Choose your migration type based on workload criticality, downtime tolerance, performance needs, and migration scale. |
| **HCX Licenses**       | **[License Model](https://techdocs.broadcom.com/us/en/vmware-cis/hcx/vmware-hcx/4-10/vmware-hcx-user-guide-4-10/vmware-hcx-services.html)**        | - HCX Advanced <br> - HCX Enterprise                                                 | **HCX Enterprise** recommended for **advanced features** (e.g., stretched networks, mobility groups).                                                                                                                                       | HCX services fall into two general categories: Advanced and Enterprise. HCX Advanced delivers basic connectivity and mobility services to enable hybrid interconnect and migration services. HCX Enterprise provides additional functionality for scalability and performance when transforming large data centers or moving large quantities of virtual machines to cloud infrastructures. |
| **Security**             | **Data Encryption & Compliance**         | - VPN (IPsec/SSL encryption) <br> - Direct Link (private encryption)                 | Both options encrypt data **in transit**. **Direct Link** avoids **public internet exposure**.                                                                                                                                            | For secure, enterprise-grade VMware HCX migrations, Direct Link is the best choice to protect workloads, ensure compliance, and prevent data exposure. |
| **Network Extension**    | **Layer 2 Stretch**         | - Network Extension Service (retain IP/MAC) <br> - Re-IP workflows                   | Use **Network Extension Service** for **zero IP changes**. Re-IP only if **network overlap** exists.                                                                                                                                     | Network L2 Extension avoids IP address changes,minimize disruptions,security policy changes, between on premises and cloud |
| **WAN Optimization**     | **Bandwidth Efficiency**    | - Deduplication <br> - Compression                                                   | Enable **WAN optimization** for **limited bandwidth**. Disable if **network bandwidth is sufficient**.                                                                                                                                    | Improves migration speed and efficiency. |
