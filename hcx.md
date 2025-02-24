---

copyright:
  years: 2024
lastupdated: "2025-02-24"

keywords:

subcollection: hcx-migration-vmware

---

{{site.data.keyword.attribute-definition-list}}


# HCX on IBM Cloud VMware 
{: #hcx}

This is a short description that introduces the content in this topic.
{: shortdesc}


## IBM Cloud VMWare overview
{: #ibmcloud-overview}


### HCX Overview
{: #hcxoverview}

VMware HCX on IBM Cloud: Overview

VMware HCX (Hybrid Cloud Extension) on IBM Cloud is a powerful solution designed to simplify and automate the migration of VMware-based workloads between on-premises data centers and IBM Cloud. It enables enterprises to seamlessly extend, migrate, and modernize applications across hybrid cloud environments with minimal disruption.

What is VMware HCX?
VMware HCX is a multi-cloud application mobility platform that enables businesses to securely migrate workloads between different VMware environments. It abstracts the underlying infrastructure, allowing seamless workload mobility, disaster recovery, and hybrid cloud operations without requiring application refactoring.

When deployed on IBM Cloud, VMware HCX facilitates the movement of workloads from on-premises VMware environments to IBM’s global cloud infrastructure. This helps enterprises leverage IBM Cloud’s scalability, high availability, and security while maintaining compatibility with their existing VMware workloads.

Key Features and Benefits
1. Seamless and Live Workload Migration
VMware HCX on IBM Cloud supports multiple migration types, including:

HCX vMotion – Live migration of virtual machines (VMs) without downtime.
HCX Bulk Migration – Scheduled migration of multiple VMs with minimal disruption.
HCX Replication-Assisted vMotion (RAV) – Combines replication and vMotion for efficient migration.
HCX Cold Migration – Moves powered-off VMs in bulk.
These capabilities allow organizations to move workloads to the cloud without major reconfiguration or performance impact.

2. Hybrid Cloud Mobility
HCX provides an automated and secure extension of VMware environments between on-premises data centers and IBM Cloud. It creates high-performance, encrypted network tunnels between environments, enabling workload mobility without network reconfiguration.

3. Disaster Recovery and Business Continuity
With HCX Disaster Recovery (HCX DR), organizations can protect their applications by replicating workloads between on-premises and IBM Cloud. This ensures business continuity and minimizes downtime during unplanned outages.

4. Network Extension and Optimization
HCX’s Layer 2 network extension allows businesses to extend on-premises VLANs to IBM Cloud without changing IP addresses. Additionally, WAN optimization improves performance, reducing latency and bandwidth consumption during migration.

5. Simplified Operations and Automation
HCX simplifies workload migration with an intuitive interface, reducing manual efforts and operational complexity. It automates VM movement, ensuring faster cloud adoption without impacting productivity.

### Use Cases
{: #usecases}
1. Cloud Migration
Enterprises can migrate large-scale VMware workloads to IBM Cloud without re-architecting applications. This accelerates digital transformation while maintaining operational consistency.

2. Data Center Extension
HCX enables organizations to extend their existing VMware environment to IBM Cloud, providing additional capacity without upfront hardware investment.

3. Disaster Recovery
Businesses can leverage IBM Cloud as a secondary site for disaster recovery, ensuring business continuity in case of on-premises failures.

4. Application Modernization
Once in IBM Cloud, workloads can be modernized with IBM’s AI, Kubernetes, and automation services, enabling businesses to innovate faster.

### Deployment Models:
{: #deploymentmodel}

**IBM Cloud for VMware Solutions Dedicated:** A single-tenant model offering higher levels of isolation for enhanced security and compliance readiness. This model is ideal for organizations requiring dedicated resources and greater control over their environment. 


**IBM Cloud for VMware Cloud Foundation (VCF):** Provides a fully integrated VMware software-defined data center (SDDC) stack, including vSphere, vSAN, NSX-T, and HCX, deployed on IBM Cloud's Virtual Private Cloud (VPC) infrastructure. This deployment supports both consolidated and standard architecture models, allowing flexibility based on organizational needs. 

## Key Components of VMware HCX Network Architecture

A successful HCX deployment relies on several key components that ensure secure, efficient, and optimized migration of workloads:

### HCX Manager
- Acts as the central control point for orchestrating the deployment and management of HCX services across both source and destination sites.

### Interconnect Service
- Establishes a secure, optimized transport layer between environments.
- Facilitates encrypted data transfer with WAN optimization for improved performance.

### Network Extension Service
- Extends Layer 2 networks across sites.
- Allows virtual machines (VMs) to retain their IP and MAC addresses, ensuring minimal disruption.

### WAN Optimization Service
- Enhances data transfer efficiency by reducing bandwidth consumption.
- Uses techniques such as deduplication and compression to improve throughput.

### Replication Service
- Manages the replication of VM data to ensure consistency.
- Supports various migration types, including cold, live, and bulk migrations.

## Pre-Requisites for Migration

For a successful HCX-based migration, organizations must meet specific prerequisites both on-premises and in IBM Cloud.

## On-Premises Requirements (Client-Side)

### VMware Environment
- Supported vSphere environment.
- VMware HCX installed and licensed.
- VMware NSX deployed for network virtualization (if required).

### Network Connectivity
- VPN or Direct Connect (IBM Cloud Classic or IBM Cloud VPC) for secure communication.
- Public IPs (if required for public-facing workloads).
- Proper firewall and security policies configured to allow necessary traffic.

### HCX Deployment Resources
- HCX Manager installed on-premises.
- Sufficient resources (compute, storage, and network bandwidth) available to support migration activities.

## IBM Cloud Requirements

### IBM Cloud VMware Solutions
- Active subscription to IBM Cloud VMware Solutions.
- For NSX-T instances, HCX requires you to use one of the following licenses: NSX Data Center SP Base Professional, Advanced or Enterprise Plus (E+) from IBM Cloud, or an equivalent BYOL license.
- For NSX-V instances, HCX requires you to use one of the following licenses: NSX Advanced or NSX Enterprise from IBM Cloud, or an equivalent BYOL license.
- As an HCX customer, you are limited to three simultaneous connections.
- HCX supported platforms
    - vSphere v5.1,v5.5
    - vSphere 6.0,6.5,6.7
    - vSphere 7.0
    - vSphere 8.0

### IBM Cloud Network Configurations
- IBM Cloud Direct Link for private, high-speed connectivity.
- VPN for secure site-to-site communication.
- NSX-T or NSX-V integration for network segmentation and security enforcement.

# VMware HCX Architectural Decisions

| **Category**          | **Decision Factor**               | **Options**                                                                 | **Recommendations & Considerations**                                                                 |
|-----------------------|------------------------------------|-----------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------|
| **Networking**        | **Connectivity Type**             | - HCX over VPN (IPsec/SSL VPN) <br> - HCX over IBM Cloud Direct Link        | **Direct Link**: Preferred for production workloads (high bandwidth, low latency, SLA-backed). <br> **VPN**: Suitable for PoC, dev/test, or small-scale migrations. |
|                       | **Bandwidth Requirements**        | - VPN (limited by ISP bandwidth) <br> - Direct Link (dedicated bandwidth)  | Use Direct Link for large data volumes (>1 Gbps). VPN may require WAN optimization for throughput.    |
|                       | **Latency Tolerance**             | - VPN (higher latency) <br> - Direct Link (low latency)                    | Direct Link ensures sub-10ms latency for latency-sensitive workloads (e.g., databases, real-time apps). |
| **Compute**           | **HCX Resource Allocation**       | - On-premises HCX Manager <br> - Cloud-side HCX (IBM Cloud VMware Solutions)| Allocate sufficient compute/storage for HCX appliances (4 vCPU, 16GB RAM minimum). Scale for bulk migrations. |
| **Migration Type**    | **Method Selection**              | - HCX vMotion <br> - Replication-Assisted vMotion (RAV) <br> - Bulk Migration <br> - Cold Migration | **HCX vMotion**: Zero downtime; ideal for single VM live migration. <br> **RAV**: Near-zero downtime; uses replica copy for production workloads. <br> **Bulk Migration**: Scheduled downtime; best for non-critical large-scale migrations. <br> **Cold Migration**: High downtime; use for non-production or maintenance windows. |
|                       | **Data Volume**                   | - Bulk Migration <br> - Incremental Sync                                   | Bulk migration for large datasets. Replication service handles incremental syncs for consistency.     |
| **HCX Deployment**    | **Deployment Model**              | - HCX Advanced <br> - HCX Enterprise                                       | HCX Enterprise recommended for advanced features (e.g., stretched networks, mobility groups).         |
| **Security**          | **Data Encryption**               | - VPN (IPsec/SSL encryption) <br> - Direct Link (private encryption)       | Both options encrypt data in transit. Direct Link avoids public internet exposure.                     |
|                       | **Compliance**                    | - HIPAA/GDPR/PCI-DSS                                                       | Direct Link meets strict compliance needs (private backbone). VPN requires additional audit controls.  |
| **Network Extension** | **Layer 2 Stretch**               | - Network Extension Service (retain IP/MAC) <br> - Re-IP workflows         | Use Network Extension Service for zero IP changes. Re-IP only if network overlap exists.              |
| **WAN Optimization**  | **Bandwidth Efficiency**          | - Deduplication <br> - Compression                                         | Enable WAN optimization for limited bandwidth. Disable if network bandwidth is sufficient.            |
