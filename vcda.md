---

copyright:
  years: 2024
lastupdated: "2025-04-11"

keywords:

subcollection: hcx-migration-vmware

---

{{site.data.keyword.attribute-definition-list}}

# Migrate with VCDA
{: #vcda}

This is a short description that introduces the content in this topic.
{: shortdesc}


## IBM Cloud VCDA Overview
{: #ibmcloud-overview}

The VMware Cloud Director Availability™ solution enables migration from on premises to IBM Cloud  for VMware Cloud Director™ and  vCenter Server workloads at both the virtual machine and at the vApp level.

VCDA is oficially the recommended tool of choice for VMware migrations from on-premises to IBM Cloud VCFaaS. 

The VCDA service is included by default in all multitenant virtual data centers (VDCs) and optionally included in your single-tenant VCF as a Service Cloud Director site order at no charge. For a VCDA disaster recovery configuration, a monthly charge is incurred per protected virtual machine (VM).

IBM Cloud® for VMware Cloud Foundation as a Service with VCDA supports several migration scenarios:

- Migrate vCenter virtual machine workloads from on-premises and vCenter Server environments to VMware Cloud Foundation (VCF) as a Service over the public or private IBM® network.
- Migrate workloads from VCF as a Service single-tenant and multitenant instances to another VCF as a Service instance.

- For more details - [Refer](https://cloud.ibm.com/docs/vmware-service?topic=vmware-service-tenant-vcda)

IBM provides public instance endpoints with VCDA. Endpoints are used to access the VCDA web interface and also to migrate workloads. You can request new endpoints for private connections for an additional charge. With private endpoints, you can migrate workloads into VCF as a Service by using the IBM Cloud private network to improve consistency and security. Cloud-to-cloud migrations from both VMware Shared and from VCF as a Service to VCF as a Service are over the private network.
 
- For more details - [Refer](https://techdocs.broadcom.com/us/en/vmware-cis/cloud-director/availability/4-7/what-is-vcda.html)


## Deployment Models Overview
{: #Deployment-overview}

IBM Cloud® for VCF as a Service provides the VMware Cloud Director™ platform as either a dedicated single tenant  or a shared multi tenant managed service.

IBM® performs the configuration, hosting, operations, and lifecycle management of the VMware® by Broadcom software so you can quickly deploy your VMware-based cloud computing environments. Compute resources are available as either dedicated or multitenant hosts that use IBM Cloud bare metal servers. Dedicated single-tenant VMware sites provide additional isolation and support multiple host configuration options to support flexible workload requirements.

VMware Cloud Foundation (VCF) as a Service multitenant instances are deployed to all supported regions by IBM. Create your virtual data centers (VDCs) on the IBM managed infrastructure. VCF as a Service single-tenant instances are provisioned and managed by your organization.

For more details - [Refer](https://cloud.ibm.com/docs/vmwaresolutions?topic=vmwaresolutions-vmware-aas-overview)

## Key Components
{: #key components}

a. On-Premises

- Replication Manager: Orchestrates VM replication and failover.
- Tunnel Server: Secures encrypted data transfer over public/private networks.
- vSphere Environment: Source ESXi hosts and vCenter Server.

b. IBM Cloud

- VCFaas Subscription
- vCloud Director
- VCDA Cloud Appliances

VMware Cloud Director™ and VMware Cloud Director Availability Versions for VCFaaS- [Refer](https://cloud.ibm.com/docs/vmware-service?topic=vmware-service-vmaas-bom)

## Pre-requisites
{: #pre reqs}

Successful migration requires preparation at both the on-premises and IBM Cloud ends.

On-Premises Prerequisites

- VCDA Deployment: Install and configure the VCDA On-Premises to Cloud Director Replication Appliance. This requires downloading the OVF template from VMware and deploying it via vCenter.
- Network Connectivity: Ensure outbound access to IBM Cloud for replication traffic. A VPN or Direct Link to IBM Cloud is necessary.Direct Link is preferred for low latency and faster migrations.
- For detailed requirements -[Refer](https://techdocs.broadcom.com/us/en/vmware-cis/cloud-director/availability/4-7/on-prem-availability-install-config-and-upgrade-guide-4-7/installing-and-configuring-vcav-on-premises/on-premises-vcav-deployment-requirements.html)

IBM Cloud Prerequisites
- VCFaaS Subscription: An active IBM Cloud account with VCFaaS provisioned, including a virtual data center (VDC) managed by vCloud Director.
- VCDA Activation: VCDA is included by default in multi-tenant VDCs and optional in single-tenant VCFaaS setups. Ensure it’s enabled and paired with the on-premises appliance.
- Network Configuration: Configure the necessary networking for connectivity. If using Layer 2 extension, ensure NSX-T is set up with matching network segments.
- Storage Profiles: Define destination storage policies (e.g., vSAN or NFS) in vCloud Director to accommodate migrated VMs.
- Security: Implement firewalls, encryption, and access controls as per organizational policies.

## VCDA Architecture
{: #VCDA Architecture}
![VCDA VCFAaas Architecture](diagrams/VCDA-reference-architecture-vcfaas.svg){: caption=VCDA architecture}
- The on-premises VCDA Replication Manager communicates with vCenter to identify VMs and initiate replication. It then coordinates with the Tunnel Appliance to send encrypted data over the internet or a private connection to the IBM Cloud Tunnel Appliance.
- In IBM Cloud, the VCDA Cloud Appliances receive the data and integrate it into the target VDC via vCloud Director. vCloud Director assigns compute, storage, and networking resources from the underlying VCFaaS stack.
- NSX-T optionally enables Layer 2 network extension, allowing VMs to retain their IP addresses, while the Edge Gateway manages external connectivity. 
- Additional Streched Networking details. [Refer](https://techdocs.broadcom.com/us/en/vmware-cis/cloud-director/availability/4-7/availability-admin-guide-4-7/vcav-administration-on-premises/stretching-l2-on-premises-networks.html)
- For more VCDA Architecture  details - [Refer](https://techdocs.broadcom.com/us/en/vmware-cis/cloud-director/availability/4-7/on-prem-availability-install-config-and-upgrade-guide-4-7/installing-and-configuring-vcav-on-premises/deployment-architecture-on-premises.html)


## VCDA Migration Details:
{: #VCDA Migration Details}

VMware vCloud Director Availability (VCDA) serves as the cornerstone for migrating VMware workloads from an on-premises vSphere environment to IBM Cloud VMware Solutions, specifically the VMware Cloud Foundation as a Service (VCFaaS) delivered through vCloud Director. VCDA facilitates this process by leveraging asynchronous replication to transfer virtual machines (VMs) and vApps with minimal downtime, ensuring data integrity and operational continuity. The migration operates in a source-to-target model, where the on-premises environment acts as the source and the IBM Cloud VCFaaS environment serves as the target.

The migration architecture relies on a set of interconnected modules that bridge the on-premises and IBM Cloud environments. Below is an overview of these modules and how they communicate:

On-Premises :
- vCenter Server: Manages the source vSphere environment, hosting the VMs and vApps targeted for migration. It provides the VCDA appliances with access to VM metadata and storage.
- VCDA On-Premises Appliance: Comprises the Replication Management Appliance and Tunnel Appliance. The Replication Manager orchestrates replication tasks, while the Tunnel Appliance establishes a secure, encrypted connection (port 8048) to IBM Cloud for data transfer.
- ESXi Hosts: Execute the VMs and facilitate disk-level replication via integration with VCDA.

IBM Cloud :
- vCloud Director: Acts as the management layer for the VCFaaS environment, providing tenant isolation, resource allocation, and the target VDC for migrated workloads.
- VCDA Cloud Appliances: Deployed within IBM Cloud, these include the Cloud Director Replication Management Appliance (paired with vCloud Director) and the Tunnel Appliances, which receives and processes replicated data.
- VMware Cloud Foundation Stack: Includes vSphere, vSAN, and NSX-T, hosted on IBM Cloud infrastructure, serving as the runtime environment for migrated workloads.
- Cloud Networking : Ensures secure, high-speed connectivity between on-premises and cloud networks, often supplemented by Direct Link or VPN.

For Additonal details - [Refer](https://cloud.ibm.com/docs/vmware-service?topic=vmware-service-vcda-migrating-onprem)

## Conclusions
{: #conclusion}

Migrating VMware workloads to IBM Cloud using VCDA provides a robust and flexible solution for enterprises seeking to migrate workloads from On premises to IBM Cloud for rehosting application workloads with cloud agility.With VCDA, you can migrate workloads from vSphere  environments to IBM Cloud VCFaas with options to host your VMware workloads on a single tenant VCF stack or completely managed VCFaaS VMware stack.


## References:
{: #Reference}
- [VCFaas](https://cloud.ibm.com/docs/vmware-service?topic=vmware-service-getting-started)
- [Broadcom VCDA](https://techdocs.broadcom.com/us/en/vmware-cis/cloud-director/availability/4-7/what-is-vcda.html)
