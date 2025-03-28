---
copyright:
  years: 2024
lastupdated: "2025-03-28"

keywords:

subcollection: hcx-migration-vmware

---

{{site.data.keyword.attribute-definition-list}}

# Overview

{: prio-overview}

PrimaryIO is a technology-first company with an IBM Cloud-native platform wrapped in orchestrated services. Together the technology, processes and people from PrimaryIO enable the Cloud Journey for organizations. As a key step in the Cloud Journey, migration can deliver strategic benefits as well as cost savings from hardware, software license and operational optimization. Cloud scalability and elasticity offer customers the ability to scale up and down according to need. Migrations are ideally tailored to the specific requirements, whether a swift “big bang” move, or a methodical, timed series of workload waves. Irrespective of approach, migrations need to be well planned and well executed to minimize time, risk and cost. Due to unique tools, experience and technical depth, PrimaryIO is the leading provider of migrations into IBM Cloud; migrations have become a key offering from PrimaryIO, consumable through a tile in the IBM Cloud Catalog.  
From a technology perspective, PrimaryIO is the only company to provide an IBM Cloud-native SaaS platform that supports migration into IBM Cloud. Platform use cases supported include, but are not limited to: ● migration of lower-tier applications, like Dev/Test, while simultaneously using IBM Cloud as a DR site for on-prem production VMware VMs; ● migration of VMware VMs to IBM Cloud-native Virtual Server Instances (VSIs), thereby reducing dependence on VMware.  
● A third use case is the migration of VMware VMs into IBM’s VCFaaS hosted VMware platform.  
● The most prevalent use case is the often-cited “lift and shift” migration of VMware workloads into IBM Cloud VCF. Key Benefits {: \#priobenefits} • Rapid, predictable relocation of VMware VMs to IBM Cloud as either a primary site, DR site or even a tertiary DR site. • Easy-to-consume functionality via IBM Cloud Catalog tile.  
• Initiated engagements with assessment and discovery enabling an optimization of cloud-based infrastructure thereby reducing cost and leveraging the most efficient cloud-available IaaS, such as Intel 4th Gen Xeon (“Sapphire Rapids”) server configurations. • As an optional capability, conversion, at scale, through automation to IBM Cloud-native Virtual Server Instances (VSIs) • Due to proprietary Block Stream Protocol and the Continuous Data Protection of changed blocks, on-prem changes are synced with the Cloud-based VMs, resulting in seamless migrations • Enterprise-Grade Security is obtained as a result of encryption of all data whether in transit or at rest • Customer data remains in the customer’s control. Customer data is not ingested into the PrimaryIO-managed control plane SaaS application. Once migrated, customers can choose from a variety of platform features including ProtectIO which provides ongoing disaster recovery and ransomware recovery capabilities. Additional optional functionality includes the conversion from VMware VMs to IBM Cloud-native VSIs via the ConvertIO utility. Following migration, if protecting VMs with ProtectIO, the DR Recovery Point Objective is near-zero seconds and Recovery Time Objective provides optionality to the customer based on application criticality and desire to reduce protected mode costs.

**Protection of On-prem and Migrated VMs:**

| **Feature**                        | **ProtectIO SaaS Platform**                                                                                                                                                                                                                              |
|------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Function**                       | Real-time VM replication and protection. Includes Ransomware Recovery.                                                                                                                                                                                   |
| **Technology**                     | VMware APIs for I/O (VAIO) filtering. Delivers Continuous (block level) Data Protection.                                                                                                                                                                 |
| **Cloud-first**                    | On-demand Cloud infrastructure enabling a minimum server configuration with instantiation of on-demand additional capacity when needed                                                                                                                   |
| **Storage**                        | Migration utilizes any VM-connected file storage, typically NFS. With the DR use-case, ProtectIO delivers storage optionality including lowest-cost Cloud Object Storage. Object storage is not an appropriate storage media primary site, migrated VMs. |
| **RPO (Recovery Point Objective)** | Near-zero seconds                                                                                                                                                                                                                                        |
| **RTO (Recovery Time Objective)**  | Seconds to Hours depending on chosen storage configuration                                                                                                                                                                                               |
| **Transport Modes**                | Block Stream Protocol, Continuous Data Protection                                                                                                                                                                                                        |
| **VMware Dependency**              | Support for current versions of vSphere. VIB installed on production (source) ESXi host                                                                                                                                                                  |
| **Best For**                       | All VMware VMs, whether turned off and unused to business-critical application workloads. These are “future-proof” migrations that, over time, can bleed into cloud-native VSIs or Containerized applications on a per-VM basis.                         |

## Migration into IBM Cloud Classic Environment

{: ibmcloudclassic}

### Architecture of PrimaryIO platform on IBM Cloud

{: prioarchitecture}

Supporting the IBM Cloud environment, the client (source)-side architecture involves deploying a VMware Installation Bundle (VIB) within all ESXi hosts in a cluster to be migrated or protected by DRaaS/RRaaS. The VAIO filter coordinates with a block-sending agent responsible for sending new (initial) or changed blocks to a receiver agent running in the customer’s target site in IBM Cloud. Upon receipt of workload data, those blocks are committed to storage. The metadata keeping track of what VMs are being migrated (and potentially protected) and where the VM data resides are all kept in the SaaS control plane - an IBM Cloud-native Red Hat Openshift Kubernetes application running in IBM Cloud VPC. This architecture is a truly modern application reflecting the state-of-the-art, in-depth knowledge of VMware, IBM Cloud and cloud-native design - a differentiating expertise of PrimaryIO.

### Architecture of PrimaryIO platform on IBM Cloud VMware Solutions (VCF for Classic)

{: vcfprioclassic}

Supporting VCF for IBM Cloud classic, PrimaryIO utilizes its flagship control plane SaaS platform. There is no application to install to orchestrate actions such as migration (initial sync), failover or firedrill. These capabilities are always up and running in the ProtectIO DRaaS web-accessible application.

The following architecture diagram reflects the typical components of a source site, destination site and SaaS Control Plane is support of a typical VM workload migration into IBM Cloud Classic.

Key architectural features include:

1.  **Customer Source Site (On-prem or in IBM Cloud)**
    -   VSphere - VMware server
    -   ESXi host with VMware Virtual Machines
    -   Connectivity (IPSec Tunnel) to IBM Public Cloud
    -   VAIO filter sending blocks to Target Site
2.  **IBM Cloud Classic Target Site**
    -   DR Data Receiver Agent
    -   VMware ESXi host
    -   Target VMs
3.  **PrimaryIO SaaS Application Control Plane in IBM Cloud**
    -   Served UI Web Console (PIO UI)
    -   SQL database storing key metadata (not VM application data)
    -   Red Hat OpenShift Kubernetes (ROKs) on IBM Cloud

### Migration Considerations and Requirements

When planning a migration to IBM Cloud Classic using PrimaryIO, consider the following:

-   Network Connectivity: Data integrity, reliability and speed will be a function of the connectivity between the migration source VMs and the IBM Cloud target site. This must be in place prior to migration.
-   Resource Allocation: The necessary credentialing as well as compute, network and storage resources must be properly provisioned in IBM Cloud in order to assure that anticipated performance of the migrated VMs in IBM Cloud.
-   Compatibility: On prem VMs including edge security must be provisioned in a compatible IBM Cloud environment.
-   Minimal Impact Planning: Methodology coupled with resource allocation needs to be well-planned in order to minimize impact to the applications, and by extension to the business dependent on those applications.

## MIgration into IBM Cloud VPC environment

-   PrimaryIO has no significant architectural differences distinguishing IBM Cloud VPC from its IBM Cloud Classic offering. In fact, the SaaS platform is the same, whether on Cloud Classic or VPC.
-   Due to differences between Classic and VPC, there are infrastructure and functional differences between migrated VMs in the two cloud environments
-   The single most significant difference between a Classic and VPC migration is the bare metal configuration options, coupled with the time it takes to implement configuration changes in the target account. The SLAs are purely a function of the IBM Cloud infrastructure limitations.

{: ibmcloudvpc}

### Architecture of PrimaryIO platform on IBM Cloud

{: prioarchitecture}

Supporting the IBM Cloud environment, the client (source)-side architecture involves deploying a VMware Installation Bundle (VIB) within all ESXi hosts in a cluster to be migrated or protected by DRaaS/RRaaS. The VAIO filter coordinates with a block-sending agent responsible for sending new (initial) or changed blocks to a receiver agent running in the customer’s target site in IBM Cloud. Upon receipt of workload data, those blocks are committed to storage. The metadata keeping track of what VMs are being migrated (and potentially protected) and where the VM data resides are all kept in the SaaS control plane - an IBM Cloud-native Red Hat Openshift Kubernetes application running in IBM Cloud VPC. This architecture is a truly modern application reflecting the state-of-the-art, in-depth knowledge of VMware, IBM Cloud and cloud-native design - a differentiating expertise of PrimaryIO.

### Architecture of PrimaryIO platform on IBM Cloud VMware Solutions (VCF for VPC)

{: vcfpriovpc}

Supporting VCF for IBM Cloud VPC, PrimaryIO utilizes its flagship control plane SaaS platform. There is no application to install to orchestrate actions such as migration (initial sync), failover or firedrill. These capabilities are always up and running in the ProtectIO DRaaS web-accessible application.

The following architecture diagram reflects the typical components of a source site, destination site and SaaS Control Plane is support of a typical VM workload migration into IBM Cloud VPC.

Key architectural features include:

1.  **Customer Source Site (On-prem or in IBM Cloud)**
    -   VSphere - VMware server
    -   ESXi host with VMware Virtual Machines
    -   Connectivity (IPSec Tunnel) to IBM Public Cloud
    -   VAIO filter sending blocks to Target Site
2.  **IBM Cloud VPC Target Site**
    -   DR Data Receiver Agent
    -   VMware ESXi host
    -   Target VMs
3.  **PrimaryIO SaaS Application Control Plane in IBM Cloud**
    -   Served UI Web Console (PIO UI)
    -   SQL database storing key metadata (not VM application data)
    -   Red Hat OpenShift Kubernetes (ROKs) on IBM Cloud

### Migration Considerations and Requirements

When planning a migration to IBM Cloud VPC using PrimaryIO, consider the following:

-   Network Connectivity: Data integrity, reliability and speed will be a function of the connectivity between the migration source VMs and the IBM Cloud target site. This must be in place prior to migration.
-   Resource Allocation: The necessary credentialing as well as compute, network and storage resources must be properly provisioned in IBM Cloud in order to assure that anticipated performance of the migrated VMs in IBM Cloud.
-   Compatibility: On prem VMs including edge security must be provisioned in a compatible IBM Cloud environment.
-   Minimal Impact Planning: Methodology coupled with resource allocation needs to be well-planned in order to minimize impact to the applications, and by extension to the business dependent on those applications.




# PrimaryIO Architecture Diagrams:

-   On Premise to IBM VPC![A screenshot of a computer AI-generated content may be incorrect.](image/3a62b02348fd503c9cbf35368a0e7225.png)

Link to Draw.io file:

<https://drive.google.com/file/d/1eVbz7f4MrOr39MoNgIDuEmu5tHhixznU/view?usp=drive_link>

-   On Premise to IBM Classic

![A screenshot of a computer AI-generated content may be incorrect.](image/f69a74f674c86de36eeada441fa0f496.png)

Link to Draw.io file:

<https://drive.google.com/file/d/1qrBta2hGMA4rWcbwmmPNUq87LK1vpyYK/view?usp=drive_link>
