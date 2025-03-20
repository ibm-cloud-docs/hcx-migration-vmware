---

copyright:

years: 2024

lastupdated: "2025-03-20"

keywords:

subcollection: hcx-migration-vmware

---

{{site.data.keyword.attribute-definition-list}}

# Migrate with Veeam
{: #veeam}

## Overview
{: #veeamoverview}
Veeam on IBM Cloud is a third-party add-on service that seamlessly integrates with IBM Cloud for VMware Solutions, providing robust backup and recovery capabilities for VMware workloads. This service ensures high availability and offers recovery points for critical applications and data, including enterprise solutions like Oracle and SAP HANA. By leveraging Veeam's integration, businesses can achieve rapid and reliable restoration of files, individual items, or entire virtual machines (VMs) across on-premises, hybrid, and public cloud environments. Additionally, Veeam facilitates the efficient movement of backup files to cost-effective IBM Cloud Object Storage, optimizing storage costs without compromising data accessibility.

- Veeam is an add-on additional service that can be ordered from the {{site.data.keyword.Bluemix_notm}} catalog.
- Veeam Replication is a technology that creates an exact copy of the protected VMware virtual machine at the recovery site. The replication maintains this copy in sync with the protected VM with Recovery Point Objective (RPO) of hours. Replication provides a minimum Recovery Time Objective (RTO) as the recovery replicas that are in a ready-to-start state. For more information, see [Replication](https://helpcenter.veeam.com/docs/backup/vsphere/replication.html?ver=120){: external}.
- Veeam Continuous Data Protection (CDP) is a technology that helps protect VMware virtual machines where data loss for seconds or minutes, not hours, is required. CDP also provides a minimum RTO as the CDP replicas that are in a ready-to-start state. For more information, see [Continuous Data Protection (CDP)](https://helpcenter.veeam.com/docs/backup/vsphere/cdp_replication.html?ver=120){: external}.
- Veeam supports VM encryption, and in this pattern, protected workloads must use data encryption as General Data Protection Regulation (GPDR), and other regulations requires Personally Identifiable Information (PII) or Sensitive Personal Information (SPI) data to be protected.

Veeam Git test comment

## Deployment of Veeam in IBM Cloud Classic Environment
{: #ibmcloudclassic}

### Architecture of Veeam on IBM Cloud
{: #veeamarchitecture}

In the IBM Cloud Classic environment, the client-side architecture involves deploying the Veeam Backup & Replication (VBR) server within the client's on-premises infrastructure. This setup allows for centralized management of backup and replication tasks. The VBR server coordinates with Veeam proxies and repositories to handle data processing and storage. Proxies are responsible for data movement, optimizing the transfer between source and target, while repositories serve as storage locations for the backup data. This configuration ensures efficient data protection and recovery processes.

### Architecture of Veeam on IBM Cloud VMware Solutions (VCF for Classic)
{: #vcfveeamclassis}

On the IBM Cloud classic VCF side, Veeam components are deployed to facilitate seamless integration with the client's on-premises VBR server. This includes setting up Veeam proxies within the IBM Cloud environment to handle incoming replication traffic and manage data efficiently. These proxies communicate with the on-premises VBR server, enabling secure and optimized data transfer. Additionally, backup repositories can be configured within IBM Cloud to store replicated data, providing a scalable and secure solution for disaster recovery and data archiving.

The following image is the disaster recovery pattern architecture for VMware workloads on {{site.data.keyword.Bluemix_notm}} Classic (VCS).

![Veeam Disaster Recovery Architecture](diagrams/veeamibmcloud.svg){: caption="Veeam migration for VMware Workloads on {{site.data.keyword.Bluemix_notm}} Classic (VCF) architecture" caption-side="bottom"}

Review the key features of this pattern:

1. **IBM Cloud Infrastructure:**
   - VMware Cloud Foundation.
   - Multiple ESXi bare metal servers forming a cluster hosting virtual machines.
2. **Veeam Backup and Replication Server:**
   - Responsible for managing the replication jobs.
   - Deployed onto a Microsoft Windows operating system.
   - Deployed within the VMware recovery environment as a virtual machine.
   - Veeam is deployed by using the [Simple Deployment](https://helpcenter.veeam.com/docs/backup/vsphere/simple.html?ver=120){: external} scenario that's also known as all-in-one.
3. **Veeam Repository:**
   - The backup repository is responsible for storing replication metadata of the Veeam VMware Replication proxies.
   - The backup repository stores replica metadata that contains information on the read data blocks. For more information, see [Backup Repository](https://helpcenter.veeam.com/docs/backup/vsphere/replication_components.html?ver=120#backup-repository){: external}.
   - Only the backup repository at the protected site is required.
   - In this pattern, the backup repository is installed on a Linux virtual machine.
   - Backup repositories can be hosted on Microsoft Windows or Linux operating systems.
   - The repository has a single network interface, one on an {{site.data.keyword.Bluemix_notm}} portable subnet that is used for proxies and on the {{site.data.keyword.Bluemix_notm}} Private VLAN - Primary (Management) to enable efficient traffic flow from the Veeam VMware Backup proxy to the backup replication.
   - For more information, see [VMware Backup Proxies](https://helpcenter.veeam.com/docs/backup/vsphere/backup_proxy.html?ver=120){: external}.
4. **Veeam Backup Proxy:**
   - The backup proxy is responsible for replication of virtual machines.
   - A minimum of one backup proxy per site is required, however, multiple backup proxies should be deployed for availability and scaling.
   - In this pattern backup proxies are installed on Linux virtual machines.
   - Backup proxies can be hosted on Microsoft Windows or Linux operating systems.
   - The proxies have two network interfaces; one on an {{site.data.keyword.Bluemix_notm}} portable subnet used for proxies and on the {{site.data.keyword.Bluemix_notm}} Private VLAN - Primary (Management) and a second on an {{site.data.keyword.Bluemix_notm}} portable subnet on the {{site.data.keyword.Bluemix_notm}} Private VLAN - Secondary (Storage/vMotion). This is to enable efficient traffic flow from the ESXi hosts' vmk0 interfaces to the proxies and the from the proxies to the remote proxies bypassing the firewalls.
   - For more information, see [VMware Backup Proxies](https://helpcenter.veeam.com/docs/backup/vsphere/backup_proxy.html?ver=120){: external}.
   - ![Veeam Disaster Recovery Architecture](diagrams/veeamreplicate.svg){: caption="Veeam replicate solution for VMware Workloads on {{site.data.keyword.Bluemix_notm}}" caption-side="bottom"}
5. **Veeam VMware CDP Proxy:**
   - The VMware CDP backup proxy is responsible for replication of virtual machines using CDP.
   - VMware CDP backup proxies are only needed if RPO in seconds is needed.
   - A minimum of one VMware CDP proxy per site is required, however, multiple VMware CDP proxies should be deployed for availability and scaling.
   - In this pattern VMware CDP proxies are installed on Linux virtual machines.
   - VMware CDP proxies can be hosted on Microsoft Windows or Linux operating systems.
   - The proxies have two network interfaces; one on an {{site.data.keyword.Bluemix_notm}} portable subnet used for proxies and on the {{site.data.keyword.Bluemix_notm}} Private VLAN - Primary (Management) and a second on an {{site.data.keyword.Bluemix_notm}} portable subnet on the {{site.data.keyword.Bluemix_notm}} Private VLAN - Secondary (Storage/vMotion). This is to enable efficient traffic flow from the ESXi hosts' vmk0 interfaces to the proxies and the from the proxies to the remote proxies bypassing the firewalls.
   - For more information, see [VMware CDP Proxies](https://helpcenter.veeam.com/docs/backup/vsphere/cdp_proxy.html?ver=120){: external}
   - ![Veeam CDP](diagrams/veeamcdp.svg){: caption=" Veeam CDP architecture " caption-side="bottom"}
6. **Veeam Backup Console:**
   - Console for configuring and monitoring replication jobs.
   - Installed by default on the Veeam Backup and Replication Server.
   - It is recommended that it is uninstalled from the Veeam Backup and Replication Server and installed on DevOps consoles.
   - For more information, see [Installing Veeam Backup and Replication Console](https://helpcenter.veeam.com/docs/backup/vsphere/install_console.html?ver=120){: external}
7. **Veeam ONE:**
   - Veeam ONE, part of the Veeam Availability Suite, provides visibility into Veeam-protected workloads.
   - Veeam ONE provides; monitoring, reporting, alerting, diagnostics with automated resolutions and infrastructure utilization and capacity planning.

### Migration Considerations and Requirements

When planning a migration to IBM Cloud Classic using Veeam, consider the following:

-   Network Connectivity: Establish a secure and reliable network connection between the on-premises infrastructure and IBM Cloud. This may involve configuring VPNs or dedicated connections to ensure data integrity during transfer.
-   Resource Allocation: Ensure that adequate compute and storage resources are provisioned in IBM Cloud to handle the incoming workloads and data.
-   Compatibility: Verify that the on-premises VMware environment is compatible with IBM Cloud's VMware offerings to ensure a smooth migration process.
-   Downtime Planning: Develop a strategy to minimize downtime during the migration, possibly by leveraging Veeam's replication capabilities to synchronize data before cutting over to the new environment.

## Deployment of Veeam in IBM Cloud VMware Cloud Foundation (VCF) Environment

### Architecture of Veeam on Client Side

In a VCF environment, the client-side architecture remains similar, with the Veeam Backup & Replication server managing backup and replication tasks. The VBR server interfaces with Veeam proxies and repositories to handle data operations, ensuring efficient management of backup and replication processes.

### Architecture of Veeam on IBM Cloud VCF Side

Within the IBM Cloud VCF environment, Veeam components are deployed to integrate seamlessly with the client's VBR server. This includes setting up Veeam proxies within the management domain of the VCF architecture. These proxies handle data processing tasks, facilitating efficient backup and replication operations. Backup repositories can also be established within the IBM Cloud VCF environment to store backup data securely. This setup ensures that data protection operations are optimized and aligned with the VCF infrastructure.


![Veeam architecture on IBM Cloud VPC](diagrams/Veeam-vpc.svg)

### Migration Considerations and Requirements

Key considerations for migrating to IBM Cloud VCF using Veeam include:

-   Network Configuration: Implement appropriate networking configurations to ensure secure and efficient data transfer between on-premises systems and the IBM Cloud VCF environment.
-   Resource Planning: Allocate sufficient resources within the IBM Cloud VCF environment to accommodate the workloads being migrated, ensuring performance and scalability requirements are met.
-   Integration Testing: Conduct thorough testing to validate the integration between on-premises Veeam components and the IBM Cloud VCF infrastructure, ensuring compatibility and performance standards are achieved.
-   Data Consistency: Utilize Veeam's replication features to maintain data consistency during the migration process, reducing the risk of data loss or corruption.

## Conclusions

Migrating VMware workloads to IBM Cloud using Veeam provides a robust and flexible solution for enterprises seeking to enhance their data protection and disaster recovery capabilities. By leveraging Veeam's seamless integration with IBM Cloud's VMware offerings, businesses can achieve high availability, secure backup, and efficient recovery of critical applications and data. Careful planning and consideration of network configurations, resource allocation, and compatibility are essential to ensure a smooth and successful migration process.

## References

-   IBM Cloud Docs: Veeam Deployment on VMware Cloud Foundation:

    [ondeck.console.cloud.ibm.com](https://ondeck.console.cloud.ibm.com/docs/vmwaresolutions?topic=vmwaresolutions-arch-pattern-vcf-veeam-con)
-   IBM Cloud Docs: Veeam Replication Connectivity on VMware Cloud Foundation:

    [ondeck.console.cloud.ibm.com](https://ondeck.console.cloud.ibm.com/docs/vmwaresolutions?topic=vmwaresolutions-arch-pattern-vcf-veeam-xconnectivity)


-   IBM Cloud Docs: Veeam Backup Service for VMware Cloud Foundation:

    [cloud.ibm.com](https://cloud.ibm.com/docs/vmware-service?topic=vmware-service-tenant-veeam)

-   Veeam on IBM Cloud [Veeam on IBM Cloud](https://cloud.ibm.com/docs/vmwaresolutions?topic=vmwaresolutions-arch-pattern-vcf-veeam-con)

-   Veeam VCF network connectivity[Veeam Network connectivity](https://cloud.ibm.com/docs/vmwaresolutions?topic=vmwaresolutions-arch-pattern-vcf-veeam-xconnectivity)
