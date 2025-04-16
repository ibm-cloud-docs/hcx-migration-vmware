---
copyright:
  years: 2024
lastupdated: "2025-04-16"

keywords:

subcollection: hcx-migration-vmware

---

{{site.data.keyword.attribute-definition-list}}

# Migrate with PrimaryIO
{: #primaryio}

Below 

## Overview
{: #primaryio-overview}

PrimaryIO is a technology-first company with an IBM Cloud-native platform wrapped in orchestrated services. Together the technology, processes and people, PrimaryIO enables the Cloud Journey for organizations.

As a key step in the cloud journey, migration can deliver strategic benefits as well as cost savings from hardware, software license and operational optimization.

Cloud scalability and elasticity offer customers the ability to scale up and down according to their needs. Migrations are ideally tailored to the specific requirements, whether a swift “big bang” move, or a methodical, timed series of workload waves.

Irrespective of approach, migrations need to be well planned and well executed to minimize time, risk and cost. Due to their unique tools, experience and technical depth, PrimaryIO is the leading provider of migrations into IBM Cloud. Migrations have become a key offering from PrimaryIO, consumable through a tile in the IBM Cloud Catalog.  

From a technology perspective, PrimaryIO provide an IBM Cloud-native SaaS platform that supports migration into IBM Cloud. Use cases supported include, but are not limited to: 

1.  “Lift and shift” migration of VMware workloads into IBM Cloud VCF. 
2.  Migration of lower-tier applications, like Dev/Test, while simultaneously using IBM Cloud as a DR site for on-prem production VMware VMs.
3.  Migration of VMware VMs to IBM Cloud-native Virtual Server Instances (VSIs), thereby reducing dependence on VMware.  
4.  Migration of VMware VMs into IBM’s managed VCFaaS platform.

## Key Benefits 
{: #primaryio-benefits}

The key benefits of the PrimaryIO service include the following:

1.  Rapid, predictable relocation of VMware VMs to IBM Cloud as either a primary site, DR site or even a tertiary DR site.
2.  Easy-to-consume ordering via a IBM Cloud Catalog tile. 
3.  Engagements are initiated with an assessment and discovery phase, enabling an optimization of cloud-based infrastructure, thereby reducing cost and leveraging the most efficient cloud-available IaaS, such as Intel 4th Gen Xeon (“Sapphire Rapids”) server configurations. 
4.  As an optional capability, VM conversion at scale through automation, is available to re-platform to IBM Cloud-native Virtual Server Instances (VSIs).
5.  Due to PrimaryIO's proprietary Block Stream Protocol and the Continuous Data Protection of changed blocks, on-premise changes are synced with the Cloud-based VMs, resulting in seamless migrations.
6.  Enterprise-grade security is obtained as a result of encryption of all data whether in transit or at rest.
7.  Customer data remains in the customer’s control. Customer data is not ingested into the PrimaryIO-managed control plane SaaS application. 

Once migrated, customers can choose from a variety of platform features including ProtectIO which provides ongoing disaster recovery and ransomware recovery capabilities. Additional optional functionality includes the conversion from VMware VMs to IBM Cloud-native VSIs via the ConvertIO utility. 

Following migration, if protecting VMs with ProtectIO, the DR Recovery Point Objective is near-zero while Recovery Time Objective can be selected, based on the customer application criticality requirements and desire to reduce costs.

### Protection of on-premise and migrated VMs
{: #primaryio-protection}

The table below describes the features of the ProtectIO service:

| Feature                       | ProtectIO SaaS Platform                                                                                                                                                                                                                              |
|------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Function                      | Real-time VM replication and protection. Includes Ransomware Recovery.                                                                                                                                                                                   |
| Technology                     | VMware APIs for I/O (VAIO) filtering. Delivers Continuous (block level) Data Protection.                                                                                                                                                                 |
| Cloud-first                    | On-demand Cloud infrastructure enabling a minimum server configuration with instantiation of on-demand additional capacity when needed                                                                                                                   |
| Storage                        | Migration utilizes any VM-connected file storage, typically NFS. With the DR use-case, ProtectIO delivers storage optionality including lowest-cost Cloud Object Storage. Object storage is not an appropriate storage media for primary site, migrated VMs. |
| RPO (Recovery Point Objective) | Near-zero seconds                                                                                                                                                                                                                                        |
| RTO (Recovery Time Objective)  | Seconds to Hours depending on chosen storage configuration                                                                                                                                                                                               |
| Transport Modes                | Block Stream Protocol, Continuous Data Protection                                                                                                                                                                                                        |
| VMware Dependency              | Support for current versions of vSphere. VIB installed on production (source) ESXi host                                                                                                                                                                  |
| Best For                       | All VMware VMs, whether turned off and unused, to business-critical application workloads. These are “future-proof” migrations that, over time, can target cloud-native VSIs or containerized applications on a per-VM basis.                         |

## Migration to IBM Cloud Classic Environment
{: #primaryio-ibmcloudclassic}

### Architecture of PrimaryIO platform on IBM Cloud
{: #primaryio-ibmcloudclassic-prioarchitecture}

In the source environment, a VMware Installation Bundle (VIB) is installed on all ESXi hosts in a cluster to be migrated or protected by DRaaS/RRaaS. The VAIO filter coordinates with a block-sending agent responsible for sending new (initial) or changed blocks to a receiver agent running in the customer’s target site in IBM Cloud. Upon receipt of workload data, those blocks are committed to storage. The metadata keeping track of what VMs are being migrated (and potentially protected) and where the VM data resides are all kept in the SaaS control plane - an IBM Cloud-native Red Hat Openshift Kubernetes application running in IBM Cloud VPC. The PrimaryIO architecture is a truly modern application reflecting the state-of-the-art, designed with an in-depth knowledge of VMware, IBM Cloud and cloud-native design.

### Architecture of PrimaryIO platform on IBM Cloud VMware Solutions (VCF for Classic)
{: #primaryio-ibmcloudclassic-vcfprioclassic}

Supporting VCF for IBM Cloud Classic, PrimaryIO utilizes its flagship control plane SaaS platform. There is no application to install to orchestrate actions such as migration (initial sync), failover or fire-drill. These capabilities are always up and running in the ProtectIO DRaaS web-accessible application.

The following architecture diagram reflects the typical components of a source site, destination site and SaaS Control Plane is support of a typical VM workload migration into IBM Cloud Classic.

![PrimaryIO Migration Architecture](diagrams/On-premiseClassic.svg){: caption="PrimaryIO migration for VMware Workloads on {{site.data.keyword.Bluemix_notm}} Classic (VCF) architecture" caption-side="bottom"}

Key architectural features include the following:

1.  **Customer Source Site (On-prem or in IBM Cloud)**
    -   vSphere - VMware server
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
{: #primaryio-ibmcloudclassic-migration-requirement}

When planning a migration to IBM Cloud Classic using PrimaryIO, consider the following:

- Network Connectivity: Data integrity, reliability and speed will be a function of the connectivity between the migration source VMs and the IBM Cloud target site. This must be in place prior to migration.
- Resource Allocation: The necessary credentialing as well as compute, network and storage resources must be properly provisioned in IBM Cloud in order to assure that anticipated performance of the migrated VMs in IBM Cloud.
- Compatibility: On prem VMs including edge security must be provisioned in a compatible IBM Cloud environment.
- Minimal Impact Planning: Methodology coupled with resource allocation needs to be well-planned in order to minimize impact to the applications, and by extension to the business dependent on those applications.

## Migration to IBM Cloud VPC environment
{: #primaryio-vpc}

PrimaryIO has no significant architectural differences distinguishing IBM Cloud VPC from its IBM Cloud Classic offering. In fact, the SaaS platform is the same, whether on Cloud Classic or VPC. Due to differences between Classic and VPC, there are infrastructure and functional differences between migrated VMs in the two cloud environments. The single most significant difference between a Classic and VPC migration is the bare metal configuration options, coupled with the time it takes to implement configuration changes in the target account. The SLAs are purely a function of the IBM Cloud infrastructure limitations.

### Architecture of PrimaryIO platform on IBM Cloud
{: #primaryio-vpc-prioarchitecturevpc}

In the source environment, a VMware Installation Bundle (VIB) is installed on all ESXi hosts in a cluster to be migrated or protected by DRaaS/RRaaS. The VAIO filter coordinates with a block-sending agent responsible for sending new (initial) or changed blocks to a receiver agent running in the customer’s target site in IBM Cloud. Upon receipt of workload data, those blocks are committed to storage. The metadata keeping track of what VMs are being migrated (and potentially protected) and where the VM data resides are all kept in the SaaS control plane - an IBM Cloud-native Red Hat Openshift Kubernetes application running in IBM Cloud VPC. The PrimaryIO architecture is a truly modern application reflecting the state-of-the-art, designed with an in-depth knowledge of VMware, IBM Cloud and cloud-native design.

### Architecture of PrimaryIO platform on IBM Cloud VMware Solutions (VCF for VPC)
{: #primaryio-vpc-vcfpriovpc}

Supporting VCF for IBM Cloud VPC, PrimaryIO utilizes its flagship control plane SaaS platform. There is no application to install to orchestrate actions such as migration (initial sync), failover or fire-drill. These capabilities are always up and running in the ProtectIO DRaaS web-accessible application.

The following architecture diagram reflects the typical components of a source site, destination site and SaaS Control Plane is support of a typical VM workload migration into IBM Cloud VPC.

![PrimaryIO Migration Architecture to IBM Cloud VPC Entironment](diagrams/On-premiseVPC.svg){: caption="PrimaryIO migration for VMware Workloads on {{site.data.keyword.Bluemix_notm}} VPC (VCF) architecture" caption-side="bottom"}

Key architectural features include:

1.  **Customer Source Site (On-prem or in IBM Cloud)**
    -   vSphere - VMware server
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
{: #primaryio-vpc-migrations}

When planning a migration to IBM Cloud VPC using PrimaryIO, consider the following:

- Network Connectivity: Data integrity, reliability and speed will be a function of the connectivity between the migration source VMs and the IBM Cloud target site. This must be in place prior to migration.
- Resource Allocation: The necessary credentialing as well as compute, network and storage resources must be properly provisioned in IBM Cloud in order to assure that anticipated performance of the migrated VMs in IBM Cloud.
- Compatibility: On prem VMs including edge security must be provisioned in a compatible IBM Cloud environment.
- Minimal Impact Planning: Methodology coupled with resource allocation needs to be well-planned in order to minimize impact to the applications, and by extension to the business dependent on those applications.

## References:
{: #primaryio-references}

PrimaryIO references are listed below:

* [PrimaryIO](https://www.primaryio.com/){: external}
* [ProtectIO DRaaS Managed Service](https://cloud.ibm.com/catalog/services/protectio-draas-managed-service)
* [ConvertIO VMware Workload Migration and Conversion](https://cloud.ibm.com/catalog/services/convertio-vmware-workload-migration-and-conversion)
* [VMware Cloud Migration Services](https://cloud.ibm.com/catalog/services/vmware-cloud-migration-services)
