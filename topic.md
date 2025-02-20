---
copyright:
  years: 2024
lastupdated: "2025-02-20"

keywords:

subcollection: hcx-migration-vmware
---
{{site.data.keyword.attribute-definition-list}}

# Overview

{: #overview}

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
2. Hybrid Cloud Mobility
   HCX provides an automated and secure extension of VMware environments between on-premises data centers and IBM Cloud. It creates high-performance, encrypted network tunnels between environments, enabling workload mobility without network reconfiguration.
3. Disaster Recovery and Business Continuity
   With HCX Disaster Recovery (HCX DR), organizations can protect their applications by replicating workloads between on-premises and IBM Cloud. This ensures business continuity and minimizes downtime during unplanned outages.
4. Network Extension and Optimization
   HCX’s Layer 2 network extension allows businesses to extend on-premises VLANs to IBM Cloud without changing IP addresses. Additionally, WAN optimization improves performance, reducing latency and bandwidth consumption during migration.
5. Simplified Operations and Automation
   HCX simplifies workload migration with an intuitive interface, reducing manual efforts and operational complexity. It automates VM movement, ensuring faster cloud adoption without impacting productivity.

VMware HCX on IBM Cloud supports multiple migration types, including:

HCX vMotion – Live migration of virtual machines (VMs) without downtime.
HCX Bulk Migration – Scheduled migration of multiple VMs with minimal disruption.
HCX Replication-Assisted vMotion (RAV) – Combines replication and vMotion for efficient migration.
HCX Cold Migration – Moves powered-off VMs in bulk.
These capabilities allow organizations to move workloads to the cloud without major reconfiguration or performance impact.

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

# New Topic

## 1. Introduction & Solution Overview

VMware HCX (Hybrid Cloud Extension) is a powerful migration technology designed to facilitate seamless, secure, and scalable migrations of virtual machines (VMs) from on-premises VMware environments to IBM Cloud VMware Solutions (ICVS). It provides live, bulk, cold, and replication-assisted migrations, helping enterprises modernize their infrastructure with minimal downtime.

**Key Components of VMware HCX Network Architecture:**

1.  **HCX Manager:** Acts as the central control point, orchestrating the deployment and management of HCX services across both source and destination sites.
2.  **Interconnect Service:** Establishes a secure, optimized transport between environments, facilitating encrypted data transfer with WAN optimization.
3.  **Network Extension Service:** Enables the extension of Layer 2 networks across sites, allowing virtual machines to retain their IP and MAC addresses during migration.
4.  **WAN Optimization Service:** Enhances data transfer efficiency by reducing bandwidth consumption and improving throughput through techniques like deduplication and compression.
5.  **Replication Service:** Manages the replication of virtual machine data to ensure consistency and support various migration types.

## Pre-Requisites for Migration

### On-Premises Requirements (Client-Side)

1.  **VMware Environment**
    * vSphere 6.0 or later (recommended vSphere 6.5 and above)
    * VMware HCX installed and licensed
    * VMware NSX
    * Meet the minimum compute requirements for HCX components as per below.

    https://techdocs.broadcom.com/us/en/vmware-cis/hcx/vmware-hcx/4-9/vmware-hcx-user-guide-4-9/preparing-for-hcx-installations/system-requirements-for-hcx.html
2.  **Network Connectivity**
    * VPN or Direct Connect (IBM Cloud Classic or IBM Cloud VPC)
    * Public IPs (if required for public-facing workloads)
    * Ensure proper firewall and security policies

    https://techdocs.broadcom.com/us/en/vmware-cis/hcx/vmware-hcx/4-9/vmware-hcx-user-guide-4-9/preparing-for-hcx-installations/network-port-and-protocol-requirements.html
3.  **HCX Deployment Resources**
    * HCX Connector installed on-premises
    * Sufficient resources (compute, storage, and network bandwidth) for migration

### Prepare for HCX Installations:  

https://techdocs.broadcom.com/us/en/vmware-cis/hcx/vmware-hcx/4-9/vmware-hcx-user-guide-4-9/preparing-for-hcx-installations/system-requirements-for-hcx.html 

### IBM Cloud Requirements

https://cloud.ibm.com/docs/vmwaresolutions?topic=vmwaresolutions-arch-pattern-vcf-hcx-con 

1.  **IBM Cloud VMware Solutions**
    * For choosing VMware Cloud Foundation for Classic - Automated with NSX-T™ instances, HCX is supported for NSX-T 3.1 or later and for VMware vSphere® 7.
    * For choosing VCF for Classic - Automated with NSX-V instances (VMware Solutions V4.7 and earlier), HCX is supported for vSphere 6.7.
2.  **IBM Cloud Network Configurations**
    * IBM Cloud Direct Link for private, high-speed connectivity
    * VPN for site-to-site secure connection
    * NSX-T integration for network segmentation and security

https://cloud.ibm.com/docs/vmwaresolutions?topic=vmwaresolutions-arch-pattern-vcf-hcx-xconnectivity

## **Diagram Architecture**

Below is a high-level architecture showing how VMware HCX facilitates migration from an on-premises data center to IBM Cloud:

* HCX Manager on-premises connects to HCX Manager on IBM Cloud.
* HCX migrates workloads over Direct Link, VPN, or internet-based transport.
* NSX-based networking extensions help maintain VM connectivity during migration.

## Client Side Configuration

* Install HCX Connector in the on-premises VMware environment.
* Configure VPN or Direct Link for secure connectivity.
* Validate the VM hardware compatibility for IBM Cloud VMware Solutions.
* Set up HCX Network Extensions for extending L2 networking if applicable.

## IBM Cloud Side Configuration

* Deploy IBM Cloud VMware Solutions and size your compute clusters.
* Install HCX Cloud Manager in IBM Cloud VMware environment.
* Establish connectivity with the on-premises HCX instance.
* Ensure that IBM Cloud Direct Link or VPN is set up for connectivity.

## Networking Integrations

### Network Connectivity Options

1.  **IBM Cloud Direct Link:** Best for high-speed private connectivity.
2.  **Site-to-Site VPN:** Good for secure, encrypted migration over the internet.
3.  **NSX-T/NSX-V Integration:** Enables Layer 2 network extension and security policies.

### Additonal Networking Considerations

* Extend VLANs using HCX Network Extension to avoid re-IPing workloads.
* Use NSX DFW (Distributed Firewall) for security and micro-segmentation.
* Optimize bandwidth and QoS (Quality of Service) for large-scale migrations.

## Migration Considerations

### A. Pre-Requisites to Migrate

* Ensure vCenter and ESXi versions are compatible with HCX.
* Establish secure connectivity between on-prem and IBM Cloud.
* Validate application dependencies before migration.
* Set up monitoring and alerts for tracking migration performance.
* Ensure sufficient storage & compute resources in IBM Cloud VMware.

### B. How to Migrate?

1.  Deploy HCX Connector on-premises and HCX Cloud Manager in IBM Cloud.
2.  Set up HCX Network Extension to preserve IP addressing if applicable.
3.  Select migration type (live, bulk, cold, replication-assisted) based on business needs.
4.  Execute migration via HCX vMotion or Replication-Assisted vMotion.

### Migration Options with VMware HCX

1.  **HCX vMotion (Live Migration)**
    * Best for zero downtime migrations.
    * Uses vMotion technology over VPN or Direct Link.
    * Ideal for business-critical applications.
    * **Challenges**
        * Requires low-latency, high-bandwidth connection.
        * Limited to one VM at a time (bulk live migrations need Replication Assisted vMotion).
2.  **HCX Bulk Migration**
    * Moves multiple VMs simultaneously in scheduled waves.
    * Uses offline migration (cold migration) for non-time-sensitive workloads.
    * Reboots VMs after migration to apply network changes.
    * **Challenges**
        * Requires downtime but offers higher migration efficiency.
        * IP address changes may be required if no HCX Network Extension is used.
3.  **HCX Replication Assisted vMotion (RAV)**
    * Hybrid approach combining vMotion (live) and replication (bulk).
    * Pre-replicates VM disks to IBM Cloud before final cutover.
    * Useful for migrating large-scale workloads with minimal downtime.
    * **Challenges**
        * Requires additional storage and compute resources during replication.
        * Network bandwidth usage can be high during bulk replication.


**Architectural Decisions:**

**Choosing Migration Type:**

| HCX Migration Method                         | Best Use Case                               | Downtime           | Notes                                                                       |
| -------------------------------------------- | ------------------------------------------- | ------------------ | --------------------------------------------------------------------------- |
| **HCX vMotion**                        | Live migration of VMs with minimal impact   | Zero               | Ideal for single VM moves but can be slower for bulk migrations             |
| **Replication-Assisted vMotion (RAV)** | Large-scale migration with minimal downtime | Near-zero          | Uses a replica copy and final switchover; suitable for production workloads |
| **Bulk Migration**                     | Migration of many workloads at scale        | Scheduled Downtime | Uses replication and switchover; best for non-critical workloads            |
| **Cold Migration**                     | Offline migration of workloads              | High               | Best for non-production workloads or maintenance windows                    |


**Choosing Connectivity Options for HCX Migration**

**A. HCX over VPN (IPsec VPN or SSL VPN)**

* **Use Case:** Quick deployment without dedicated bandwidth, suitable for small-scale migrations.
* **Implementation:**

  * Configure an IPsec VPN tunnel between on-premises and IBM Cloud.
  * Ensure HCX appliances are reachable over the VPN tunnel.
  * Validate firewall rules to allow HCX migration traffic.
* **Pros:**

  * Quick and cost-effective setup.
  * No additional hardware required.
* **Cons:**

  * Lower performance due to internet-based connectivity.
  * Increased latency and potential packet loss.

**B. HCX over IBM Cloud Direct Link (Recommended for Production Workloads)**

* **Use Case:** Best for high-performance, low-latency workload migrations.
* **Implementation:**
  * Use IBM Cloud Direct Link to establish a dedicated private connection.
  * Allocate at least 1 Gbps (10 Gbps recommended for large migrations).
  * Deploy HCX Interconnect to optimize network throughput.
* **Pros:**
  * Predictable performance with minimal latency.
  * Secure, private network with dedicated bandwidth.
* **Cons:**
  * Higher setup cost compared to VPN-based migration.
