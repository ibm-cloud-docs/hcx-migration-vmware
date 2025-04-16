---

copyright:
  years: 2024
lastupdated: "2025-04-16"

keywords:

subcollection: hcx-migration-vmware

---

{{site.data.keyword.attribute-definition-list}}

# Migrate with VCDA
{: #vcda}

## IBM Cloud VCDA Overview
{: #vcda-ibmcloud-overview}

The VMware Cloud Director Availability solution enables migration from on-premises to VMware Cloud Foundation as a Service as a Service (VCFaaS) at both the virtual machine and at the vApp level. 

The VCDA service is included by default in all multi-tenant virtual data centers (VDCs) and optionally included in your single-tenant VCFaaS Cloud Director site order at no charge. For a VCDA disaster recovery configuration, a monthly charge is incurred per protected virtual machine (VM).

IBM Cloud for IBMCloud VCFaaS with VCDA supports several migration scenarios:

- Migrate vCenter virtual machine workloads from on-premises and vCenter Server environments to VMware Cloud Foundation (VCF) as a Service over the public or private IBM network.
- Migrate workloads from VCF as a Service single-tenant and multi-tenant instances to another VCF as a Service instance.

For more details, see [VMware Cloud Foundation as a Service](/docs/vmware-service?topic=vmware-service-tenant-vcda)

IBM provides public instance endpoints with VCDA. Endpoints are used to access the VCDA web interface and also to migrate workloads. You can request new endpoints for private connections for an additional charge. With private endpoints, you can migrate workloads into VCF as a Service by using the IBM Cloud private network to improve consistency and security. Cloud-to-cloud migrations from both VMware Shared and from VCF as a Service to VCF as a Service are over the private network. See [Adding and deleting private instance endpoints with VCDA](/docs/vmware-service?topic=vmware-service-vcda-adding-deleting-private-ep).

## VCFaaS service models
{: #vcda-deployment}

IBM Cloud for VMware Cloud Foundation (VCF) as a Service (VCFaaS) has two service models:

Single-tenant - Dedicated infrastructure to host your virtual data centers (VDCs).
Multi-tenant  - Shared infrastructure to host your VDCs.

VCFaaS multi-tenant instances are deployed to all supported regions by IBM. You create your VDCs on the IBM managed infrastructure. VCFaaS single-tenant instances are provisioned by your organization. For both service models, IBM performs the configuration, hosting, operations, and lifecycle management of the VMware by Broadcom software so you can quickly deploy your VMware-based cloud computing environments.

For more details, see [VCF as a Service overview](/docs/vmwaresolutions?topic=vmwaresolutions-vmware-aas-overview). To understand the VMware Cloud Director and VMware Cloud Director Availability Versions for VCFaaS, see [VCF as a Service BOM](https://cloud.ibm.com/docs/vmware-service?topic=vmware-service-vmaas-bom).

## Key VCDA components
{: #vcda-key}

The following components are installed, configured and managed by IBM in the single-tenant and multi-tenant instances and the services provided to you.

- VCFaas Subscription.
- vCloud Director.
- VCDA Cloud Appliances.

If the source environment is on-premises or an instance of VCF on Classic or VCF on VPC then you are responsible for the following components:

- Replication Manager: Orchestrates VM replication and failover.
- Tunnel Server: Secures encrypted data transfer over public/private networks.
- vSphere Environment: Source ESXi hosts and vCenter Server.

See [Installing VCDA on-premises in VMware vCenter Server](/docs/vmware-service?topic=vmware-service-vcda-migrating). The same information can be used for installing VCDA on an instance of VCF on Classic or VCF on VPC.

## Pre-requisites
{: #vcda-prereqs}

Successful migration requires preparation at both the on-premises and IBM Cloud ends.

On-premises prerequisites:

- VCDA Deployment: Install and configure the VCDA On-Premises to Cloud Director Replication Appliance. This requires downloading the OVF template from VMware and deploying it via vCenter.
- Network Connectivity: Ensure outbound access to IBM Cloud for replication traffic. An Internet connection or a Direct Link to IBM Cloud is necessary. Direct Link is preferred for low latency and faster migrations.
- For detailed requirements -[Refer](https://techdocs.broadcom.com/us/en/vmware-cis/cloud-director/availability/4-7/on-prem-availability-install-config-and-upgrade-guide-4-7/installing-and-configuring-vcav-on-premises/on-premises-vcav-deployment-requirements.html){: external}
- Optionally, for layer 2 network extension, to establish the client L2 VPN session in a site not managed by NSX, download and deploy a standalone VMware NSX Edge appliance, called a NSX Autonomous Edge. 

IBM Cloud prerequisites:

- VCFaaS Subscription: An active IBM Cloud account with VCFaaS provisioned, including a virtual data center (VDC) managed by vCloud Director.
- VCDA Activation: VCDA is included by default in multi-tenant VDCs and optional in single-tenant VCFaaS setups. Ensure it’s enabled and paired with the on-premises appliance.
- Network Configuration: Configure the necessary networking for connectivity. If using Layer 2 extension, you have configured matching network segments in your VDC.
- Storage Profiles: Define destination storage policies (e.g., vSAN or NFS) in vCloud Director to accommodate migrated VMs.
- Security: Implement network address translations, firewall rules, VPN tunnels encryption, and access controls as per your organizational policies.

## VCDA Architecture
{: #Vvcda-architecture}

VMware vCloud Director Availability (VCDA) serves as the cornerstone for migrating VMware workloads from a source vSphere environment to IBM Cloud VMware Cloud Foundation as a Service (VCFaaS). VCDA facilitates this process by leveraging asynchronous replication to transfer virtual machines (VMs) and vApps with minimal downtime, ensuring data integrity and operational continuity. The migration operates in a source-to-target model, where the source environment acts as the source for data transfer and the IBM Cloud VCFaaS environment serves as the target for the data transfer.

The migration architecture relies on a set of interconnected modules that bridge the on-premises and IBM Cloud environments, the diagram below shows the VCFaaS VCDA architecture:

![VCFaaS VCDA Architecture](diagrams/VCDA-reference-architecture-vcfaas.svg){: caption=VCFaaS VCDA Architecture}

- The on-premises VCDA Replication Manager communicates with vCenter to identify VMs and initiate replication. It then coordinates with the Tunnel Appliance to sends encrypted data over the Internet or a private connection to the IBM Cloud Tunnel Appliance.
- In IBM Cloud, the VCDA Cloud Appliances receives the data and integrates it into the target VDC via vCloud Director. vCloud Director assigns compute, storage, and networking resources from the underlying VCFaaS stack.
- NSX optionally enables Layer 2 network extension via the server L2 VPN session on the Edge Gateway. For layer 2 network extensions see [On-premises stretching layer 2 networks to the Cloud Director site](https://techdocs.broadcom.com/us/en/vmware-cis/cloud-director/availability/4-7/availability-admin-guide-4-7/vcav-administration-on-premises/stretching-l2-on-premises-networks.html){: external}

Source:
- vCenter Server: Manages the source vSphere environment, hosting the VMs and vApps targeted for migration. It provides the VCDA appliances with access to VM metadata and storage.
- VCDA On-Premises Appliance: Comprises the Replication Management Appliance and Tunnel Appliance. The Replication Manager orchestrates replication tasks, while the Tunnel Appliance establishes a secure, encrypted connection (port 8048) to IBM Cloud for data transfer.
- ESXi Hosts: Execute the VMs and facilitate disk-level replication via integration with VCDA.

VCFaaS:
- vCloud Director: Acts as the management layer for the VCFaaS environment, providing tenant isolation, resource allocation, and the target VDC for migrated workloads.
- VCDA Cloud Appliances: Deployed within IBM Cloud, these include the Cloud Director Replication Management Appliance (paired with vCloud Director) and the Tunnel Appliances, which receives and processes replicated data.
- VMware Cloud Foundation Stack: Includes vSphere, vSAN, and NSX-T, hosted on IBM Cloud infrastructure, serving as the runtime environment for migrated workloads.
- Cloud Networking : Ensures secure, high-speed connectivity between on-premises and cloud networks. VCDA endpoints are available on the Internet or the IBM Cloud private network that can be reached from on-premise locations via Direct Link or VPN.

For more VCDA architecture details, see [Deployment architecture for the On-Premises to Cloud Director Replication Appliance](https://techdocs.broadcom.com/us/en/vmware-cis/cloud-director/availability/4-7/on-prem-availability-install-config-and-upgrade-guide-4-7/installing-and-configuring-vcav-on-premises/deployment-architecture-on-premises.html){: external}

For additional migration details, see [Migrating workloads from an on-premises vCenter environment to VCF as a Service](/docs/vmware-service?topic=vmware-service-vcda-migrating-onprem).

## Conclusions
{: #vcda-conclusion}

Migrating VMware workloads to IBM Cloud VCFaaS using VCDA provides a robust and flexible solution for enterprises seeking to migrate workloads from source vSphere environments to IBM Cloud VCFaaS for re-hosting application workloads with cloud agility. With VCDA, you can migrate workloads quickly and easily from vSphere environments to IBM Cloud VCFaaS with options to host your VMware workloads on an IBM managed single-tenant or multi-tenant instance.

## References:
{: #vcda-reference}
- [Getting started with VCF as a Service](/docs/vmware-service?topic=vmware-service-getting-started)
- [What is VMware Cloud Director Availability](https://techdocs.broadcom.com/us/en/vmware-cis/cloud-director/availability/4-7/what-is-vcda.html){: external}
