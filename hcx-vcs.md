---

copyright:
  years: 2024
lastupdated: "2025-02-17"

keywords:

subcollection: hcx-migration-vmware

---

{{site.data.keyword.attribute-definition-list}}


# HCX on VCS 
{: #vcs}

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
