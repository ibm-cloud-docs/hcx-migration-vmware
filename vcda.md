---

copyright:
  years: 2024
lastupdated: "2025-04-07"

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

The VCDA service is included by default in all multitenant virtual data centers (VDCs) and optionally included in your single-tenant VCF as a Service Cloud Director site order at no charge. For a VCDA disaster recovery configuration, a monthly charge is incurred per protected virtual machine (VM).

IBM Cloud® for VMware Cloud Foundation as a Service with VCDA supports several migration scenarios:

- Migrate vCenter virtual machine workloads from on-premises and vCenter Server environments to VMware Cloud Foundation (VCF) as a Service over the public or private IBM® network.
- Migrate workloads from VCF as a Service single-tenant and multitenant instances to another VCF as a Service instance.


IBM provides public instance endpoints with VCDA. Endpoints are used to access the VCDA web interface and also to migrate workloads. You can request new endpoints for private connections for an additional charge. With private endpoints, you can migrate workloads into VCF as a Service by using the IBM Cloud private network to improve consistency and security. Cloud-to-cloud migrations from both VMware Shared and from VCF as a Service to VCF as a Service are over the private network.
[For more details go through](https://cloud.ibm.com/docs/vmware-service?topic=vmware-service-tenant-vcda) 


## Deployment Models Overview
{: #Deployment-overview}

IBM Cloud® for VCF as a Service provides the VMware Cloud Director™ platform as either a dedicated or shared managed service.

IBM® performs the configuration, hosting, operations, and lifecycle management of the VMware® by Broadcom software so you can quickly deploy your VMware-based cloud computing environments. Compute resources are available as either dedicated or multitenant hosts that use IBM Cloud bare metal servers. Dedicated single-tenant VMware sites provide additional isolation and support multiple host configuration options to support flexible workload requirements.

VMware Cloud Foundation (VCF) as a Service multitenant instances are deployed to all supported regions by IBM. Create your virtual data centers (VDCs) on the IBM managed infrastructure. VCF as a Service single-tenant instances are provisioned and managed by your organization.

## Key Components
{: #key components}

a. On-Premises Components

- Replication Manager: Orchestrates VM replication and failover.
- Tunnel Server: Secures encrypted data transfer over public/private networks.
- vSphere Environment: Source ESXi hosts and vCenter Server.

b. IBM Cloud Components

- VCFaas Subscription

## Pre-requisites
{: #pre reqs}

Successful migration requires preparation at both the on-premises and IBM Cloud ends.

On-Premises Prerequisites

- VCDA Deployment: Install and configure the VCDA On-Premises to Cloud Director Replication Appliance. This requires downloading the OVF template from VMware and deploying it via vCenter.
- Network Connectivity: Ensure outbound access to IBM Cloud for replication traffic. A VPN or Direct Link to IBM Cloud is necessary.

IBM Cloud Prerequisites
- VCFaaS Subscription: An active IBM Cloud account with VCFaaS provisioned, including a virtual data center (VDC) managed by vCloud Director.
- VCDA Activation: VCDA is included by default in multi-tenant VDCs and optional in single-tenant VCFaaS setups. Ensure it’s enabled and paired with the on-premises appliance.
- Network Configuration: Configure the necessary networking for connectivity. If using Layer 2 extension, ensure NSX-T is set up with matching network segments.
- Storage Profiles: Define destination storage policies (e.g., vSAN or NFS) in vCloud Director to accommodate migrated VMs.
- Security: Implement firewalls, encryption, and access controls as per organizational policies.



## Architecture


For Additonal details - [Refer](https://cloud.ibm.com/docs/vmware-service?topic=vmware-service-vcda-migrating-onprem)
