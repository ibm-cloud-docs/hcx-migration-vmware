---

copyright:
  years: 2024
lastupdated: "2025-02-28"

keywords:

subcollection: hcx-migration-vmware

---

{{site.data.keyword.attribute-definition-list}}


# Zerto on IBM Cloud VMware
{: #zerto}
Migrating VMware Workloads to IBM Cloud Using Zerto: A Comprehensive Guide

A. Overview of Zerto on IBM Cloud

Zerto is a disaster recovery and migration solution that provides continuous data protection (CDP) for VMware workloads. It enables near-zero data loss and minimal downtime during migration by leveraging real-time replication, journal-based recovery, and automation.

On IBM Cloud, Zerto is fully compatible with IBM Cloud for VMware Solutions (VCS) and IBM Cloud VMware Cloud Foundation (VCF). It helps organizations move workloads from on-premises data centers to IBM Cloud with minimal disruption. Zerto’s platform integrates with IBM Cloud’s VMware environments to provide failover, failback, and long-term retention capabilities.

B. Deployment of Zerto for IBM Cloud Classic Environment

a. Architecture of Zerto on Client Side

In the IBM Cloud Classic environment, the client-side architecture includes:

Zerto Virtual Manager (ZVM): Installed on a Windows VM, managing replication and orchestrating recovery operations.

Zerto Virtual Replication Appliances (VRAs): Installed on each ESXi host to replicate data continuously.

Zerto Cloud Appliance (ZCA) (Optional): Facilitates hybrid cloud replication and disaster recovery.

WAN Connection: Secure VPN or Direct Link connection between on-premises and IBM Cloud.

b. Architecture of Zerto on IBM Cloud VCS Side

On IBM Cloud VCS, the architecture involves:

IBM Cloud VCS (VMware vSphere & vSAN): Target environment for migration and recovery.

Zerto Virtual Replication Appliances (VRAs): Deployed on IBM Cloud ESXi hosts to receive replicated data.

Zerto Journal & Replication Data Storage: Configured on IBM Cloud storage solutions (vSAN, NFS, or IBM Cloud Object Storage).

c. Migration Considerations and Requirements

Network Connectivity: Establish IBM Cloud Direct Link or VPN for seamless connectivity.

Storage & Compute Resources: Ensure IBM Cloud has enough capacity to handle incoming workloads.

RPO & RTO Requirements: Define acceptable recovery point and recovery time objectives.

Testing & Validation: Perform test failovers before production migration.

C. Deployment of Zerto for IBM Cloud VMware Cloud Foundation (VCF) Environment

a. Architecture of Zerto on Client Side

Zerto Virtual Manager (ZVM) & VRAs: Installed on existing on-premises VMware infrastructure.

Continuous Replication: Journal-based approach to maintain data integrity.

Secure Connectivity: VPN or IBM Cloud Direct Link.

b. Architecture of Zerto on IBM Cloud VCF Side

IBM Cloud VCF SDDC: Software-defined data center running VMware vSphere, NSX-T, and vSAN.

Zerto VRAs: Installed on ESXi hosts within the VCF environment.

Zerto Cloud Manager (ZCM) (Optional): For multi-site disaster recovery orchestration.

c. Migration Considerations and Requirements

Multi-Site Recovery: Plan for failover and failback between on-prem and IBM Cloud VCF.

Storage Optimization: Use IBM Cloud Object Storage for long-term data retention.

Security & Compliance: Align with regulatory requirements for data protection.

Automation & Monitoring: Leverage Zerto APIs and IBM Cloud monitoring tools.

D. Conclusions

Migrating VMware workloads to IBM Cloud using Zerto offers a seamless, low-downtime solution with continuous replication and automated failover. Organizations can leverage IBM Cloud for scalable, resilient disaster recovery while ensuring high availability of critical applications. Planning, testing, and optimizing network and storage configurations are crucial for a successful migration. 
