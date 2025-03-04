---

copyright:
  years: 2024
lastupdated: "2025-03-04"

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

IBM Cloud for VMware Cloud Foundation (VCF): Provides a fully integrated VMware software-defined data center (SDDC) stack, including vSphere, vSAN, NSX-T, and HCX, deployed on IBM Cloud's Virtual Private Cloud (VPC) infrastructure. This deployment supports both consolidated and standard architecture models, allowing flexibility based on organizational needs.

Migrating workloads to VCF as a Service with VCDA

Deliver simple, secure, and cost-effective migration support with VMware Cloud Director Availability (VCDA).

Both migration and disaster recovery support are available when you install the VCDA service. For more information about disaster recovery configurations, see Protecting workload data in VCF as a Service with VCDA.

The VCDA service is included by default in all multitenant virtual data centers (VDCs) and optionally included in your single-tenant VCF as a Service Cloud Director site order at no charge. For a VCDA disaster recovery configuration, a monthly charge is incurred per protected virtual machine (VM).

IBM Cloud® for VMware Cloud Foundation as a Service with VCDA supports several migration scenarios:

Migrate vCenter virtual machine workloads from on-premises and vCenter Server environments to VMware Cloud Foundation (VCF) as a Service over the public or private IBM® network.
Migrate workloads from VMware Shared to VCF as a Service.
Migrate workloads from VCF as a Service single-tenant and multitenant instances to another VCF as a Service instance.
IBM provides public instance endpoints with VCDA. Endpoints are used to access the VCDA web interface and also to migrate workloads. You can request new endpoints for private connections for an additional charge. With private endpoints, you can migrate workloads into VCF as a Service by using the IBM Cloud private network to improve consistency and security. Cloud-to-cloud migrations from both VMware Shared and from VCF as a Service to VCF as a Service are over the private network.

https://cloud.ibm.com/docs/vmware-service?topic=vmware-service-tenant-vcda
