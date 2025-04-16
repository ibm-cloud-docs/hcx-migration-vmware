---
copyright:

years: 2025

lastupdated: "2025-04-16"

keywords:

subcollection: hcx-migration-vmware

---

{{site.data.keyword.attribute-definition-list}}

# Migrate with Veeam
{: #veeam}

## Overview
{: #veeam-overview} 

Migrating VMware workloads to the IBM cloud is a strategic move that enhances scalability, resilience, and cost efficiency. However, ensuring a secure, fast, and disruption-free migration requires the right tools. Veeam on IBM Cloud provides a robust, enterprise-grade solution that simplifies VMware workload migration while ensuring business continuity, minimal downtime, and strong data protection.

With Veeam’s advanced replication and continuous data protection (CDP) technologies, organizations can move mission-critical applications such as Oracle and SAP HANA with zero impact on performance. Whether transferring entire virtual machines (VMs), critical application data, or hybrid workloads, Veeam ensures high availability and reliability across on-premises, hybrid, and public cloud environments.

### Key benefits:
{: #veeam-overview-benefits}

Using Veeam to migrate workloads to IBM Cloud VMware Solutions has the following benefits:

1. Effortless Migration & Seamless Integration – Easily deployable from the IBM Cloud catalog, ensuring a smooth migration process without complex configurations.
2. Fast, Reliable Replication & Near-Zero Data Loss with Continuous Data Protection (CDP) – Veeam Backup & Replication offers two powerful built-in migration capabilities for VMware VMs, ensuring fast, reliable replication with minimal downtime. The first approach leverages Veeam Backup Proxy, utilizing traditional backup and restore methods for secure data transfer. The second, Continuous Data Protection (CDP), provides real-time replication, delivering near-zero data loss and achieving low Recovery Point Objectives (RPOs). Designed for mission-critical workloads, CDP enables instant failover, ensuring high availability and rapid recovery in the event of a failure. See [Continuous Data Protection (CDP)](https://helpcenter.veeam.com/docs/backup/vsphere/cdp_replication.html?ver=120){: external}.
3.  Enterprise-Grade Security & Compliance – Protects sensitive workloads with end-to-end encryption, ensuring compliance with regulations like GDPR while safeguarding Personally Identifiable Information (PII) and Sensitive Personal Information (SPI).
4.  Cost-Effective Storage Optimization – Seamlessly moves migrated workloads and backup files to IBM Cloud Object Storage, reducing storage costs while maintaining easy accessibility and high performance.

By leveraging Veeam on IBM Cloud, enterprises can streamline VMware workload migration, minimize risks, and accelerate their cloud transformation journey. With automated failover, robust security, and cost-optimized storage, Veeam ensures a smooth, secure, and highly efficient migration experience. Migrate smarter, reduce complexity, and future-proof your VMware workloads with Veeam on IBM Cloud.

The table below shows the key differences between the features of Veeam Backup Proxy and Veeam VMware CDP Proxy

| Feature                        | Veeam Backup Proxy                | Veeam VMware CDP Proxy                |
|--------------------------------|-----------------------------------|---------------------------------------|
| Function                       | Backup & restore of VMs           | Real-time replication of VMs          |
| Technology                     | Snapshot-based backups            | VMware APIs for I/O Filtering (VAIO)  |
| RPO (Recovery Point Objective) | Hours/Minutes (based on schedule) | Near-Zero (real-time replication)     |
| RTO (Recovery Time Objective)  | Minutes to Hours                  | Near-Instant Failover                 |
| Transport Modes                | SAN, HotAdd, NBD                  | Uses VAIO without snapshots           |
| VMware Dependency              | Works with VMware & Hyper-V       | Only VMware (vSphere 6.5+)            |
| Best For                       | Standard backups, restores, DR    | Mission-critical apps needing low RPO |

## Deployment of Veeam in IBM Cloud Classic environment
{: #veeam-ibmcloudclassic}

### Architecture of Veeam on IBM Cloud
{: #veeam-ibmcloudclassic-veeamarchitecture}

Typically in a migration scenario, the Veeam Backup & Replication (VBR) server is already deployed within the client's on-premises infrastructure. This setup allows for centralized management of backup and replication tasks. The VBR server coordinates with Veeam proxies and repositories to handle data processing and storage. Proxies are responsible for data movement, optimizing the transfer between source and target, while repositories serve as storage locations for the backup data. This configuration ensures efficient data protection and recovery processes.

If the VBR server is not already deployed then the VBR server can be deployed in IBM Cloud, with the required Veeam components deployed on-premises.

### Architecture of Veeam on IBM Cloud VMware Solutions (VCF for Classic)
{: #veeam-ibmcloudclassic-vcfveeamclassis}

On the IBM Cloud classic VCF side, Veeam components are deployed to facilitate seamless integration with the client's on-premises VBR server. This includes setting up Veeam proxies within the IBM Cloud environment to handle incoming replication traffic and manage data efficiently. These proxies communicate with the on-premises VBR server, enabling secure and optimized data transfer. Additionally, backup repositories can be configured within IBM Cloud to store replicated data, providing a scalable and secure solution for disaster recovery and data archiving.

The following image is the disaster recovery pattern architecture for VMware workloads on IBM Cloud VCF on Classic.

![Veeam Disaster Recovery Architecture](diagrams/veeamibmcloud.svg){: caption="Veeam migration for VMware Workloads on {{site.data.keyword.Bluemix_notm}} Classic (VCF) architecture" caption-side="bottom"}

This pattern has the following key features of this pattern:

1.  IBM Cloud Infrastructure:
    1.  VMware Cloud Foundation.
    2.  Multiple ESXi bare metal servers forming a cluster hosting virtual machines.
2.  Veeam Backup and Replication Server
    1.  Responsible for managing the replication jobs.
    2.  Deployed onto a Microsoft Windows operating system.
    3.  Deployed within the VMware recovery environment as a virtual machine.
    4.  Veeam is deployed by using the [Simple Deployment](https://helpcenter.veeam.com/docs/backup/vsphere/simple.html?ver=120){: external} scenario that's also known as all-in-one.
3.  Veeam Repository:
    1.  The backup repository is responsible for storing replication metadata of the Veeam VMware Replication proxies.
    2.  The backup repository stores replica metadata that contains information on the read data blocks. For more information, see [Backup Repository](https://helpcenter.veeam.com/docs/backup/vsphere/replication_components.html?ver=120#backup-repository){: external}.
    3.  Only the backup repository at the protected site is required.
    4.  In this pattern, the backup repository is installed on a Linux virtual machine.
    5.  Backup repositories can be hosted on Microsoft Windows or Linux operating systems.
    6.  The repository has a single network interface, one on an {{site.data.keyword.Bluemix_notm}} portable subnet that is used for proxies and on the {{site.data.keyword.Bluemix_notm}} Private VLAN - Primary (Management) to enable efficient traffic flow from the Veeam VMware Backup proxy to the backup replication.
    7.  For more information, see [VMware Backup Proxies](https://helpcenter.veeam.com/docs/backup/vsphere/backup_proxy.html?ver=120){: external}.
4.  Veeam Backup Proxy:
    1.  The backup proxy is responsible for replication of virtual machines.
    2.  A minimum of one backup proxy per site is required, however, multiple backup proxies should be deployed for availability and scaling.
    3.  In this pattern backup proxies are installed on Linux virtual machines.
    4.  Backup proxies can be hosted on Microsoft Windows or Linux operating systems.
    5.  The proxies have two network interfaces; one on an {{site.data.keyword.Bluemix_notm}} portable subnet used for proxies and on the {{site.data.keyword.Bluemix_notm}} Private VLAN - Primary (Management) and a second on an {{site.data.keyword.Bluemix_notm}} portable subnet on the {{site.data.keyword.Bluemix_notm}} Private VLAN - Secondary (Storage/vMotion). This is to enable efficient traffic flow from the ESXi hosts' vmk0 interfaces to the proxies and the from the proxies to the remote proxies bypassing the firewalls.
    6.  For more information, see [VMware Backup Proxies](https://helpcenter.veeam.com/docs/backup/vsphere/backup_proxy.html?ver=120){: external}.
    7.  ![Veeam Disaster Recovery Architecture](diagrams/veeamreplicate.svg){: caption="Veeam replicate solution for VMware Workloads on {{site.data.keyword.Bluemix_notm}}" caption-side="bottom"}
5.  Veeam VMware CDP Proxy:
    1.  The VMware CDP backup proxy is responsible for replication of virtual machines using CDP.
    2.  VMware CDP backup proxies are only needed if RPO in seconds is needed.
    3.  A minimum of one VMware CDP proxy per site is required, however, multiple VMware CDP proxies should be deployed for availability and scaling.
    4.  In this pattern VMware CDP proxies are installed on Linux virtual machines.
    5.  VMware CDP proxies can be hosted on Microsoft Windows or Linux operating systems.
    6.  The proxies have two network interfaces; one on an {{site.data.keyword.Bluemix_notm}} portable subnet used for proxies and on the {{site.data.keyword.Bluemix_notm}} Private VLAN - Primary (Management) and a second on an {{site.data.keyword.Bluemix_notm}} portable subnet on the {{site.data.keyword.Bluemix_notm}} Private VLAN - Secondary (Storage/vMotion). This is to enable efficient traffic flow from the ESXi hosts' vmk0 interfaces to the proxies and the from the proxies to the remote proxies bypassing the firewalls.
    7.  For more information, see [VMware CDP Proxies](https://helpcenter.veeam.com/docs/backup/vsphere/cdp_proxy.html?ver=120){: external}
    8.  ![Veeam CDP](diagrams/veeamcdp.svg){: caption=" Veeam CDP architecture " caption-side="bottom"}
6.  Veeam Backup Console:
    1.  Console for configuring and monitoring replication jobs.
    2.  Installed by default on the Veeam Backup and Replication Server.
    3.  It is recommended that it is uninstalled from the Veeam Backup and Replication Server and installed on DevOps consoles.
    4.  For more information, see [Installing Veeam Backup and Replication Console](https://helpcenter.veeam.com/docs/backup/vsphere/install_console.html?ver=120){: external}
7.  Veeam ONE:
    1.  Veeam ONE, part of the Veeam Availability Suite, provides visibility into Veeam-protected workloads.
    2.  Veeam ONE provides; monitoring, reporting, alerting, diagnostics with automated resolutions and infrastructure utilization and capacity planning.

### Migration Considerations and Requirements
{: #veeam-ibmcloudclassic-vcfveeammigrationrequirements}

When planning a migration to IBM Cloud Classic using Veeam, consider the following:

- Network Connectivity: Establish a secure and reliable network connection between the on-premises infrastructure and IBM Cloud. This may involve configuring VPNs or dedicated connections to ensure data integrity during transfer.
- Resource Allocation: Ensure that adequate compute and storage resources are provisioned in IBM Cloud to handle the incoming workloads and data.
- Compatibility: Verify that the on-premises VMware environment is compatible with IBM Cloud's VMware offerings to ensure a smooth migration process.
- Downtime Planning: Develop a strategy to minimize downtime during the migration, possibly by leveraging Veeam's replication capabilities to synchronize data before cutting over to the new environment.

## Deployment of Veeam in IBM Cloud VMware Cloud Foundation (VCF) Environment
{: #veeam-vcfveeamVCF}

### Architecture of Veeam on Client Side
{: #veeam-vcfveeamVCF-archclient}

In a VCF environment, the client-side architecture remains similar, with the Veeam Backup & Replication server managing backup and replication tasks. The VBR server interfaces with Veeam proxies and repositories to handle data operations, ensuring efficient management of backup and replication processes.

### Architecture of Veeam on IBM Cloud VCF Side
{: #veeam-vcfveeamVCF-archcloud}

Within the IBM Cloud VCF environment, Veeam components are deployed to integrate seamlessly with the client's VBR server. This includes setting up Veeam proxies within the management domain of the VCF architecture. These proxies handle data processing tasks, facilitating efficient backup and replication operations. Backup repositories can also be established within the IBM Cloud VCF environment to store backup data securely. This setup ensures that data protection operations are optimized and aligned with the VCF infrastructure.

![Veeam architecture on IBM Cloud VPC](diagrams/Veeam-vpc.svg)

### Migration Considerations and Requirements
{: #veeam-vcfveeamVCF-considerations}

Key considerations for migrating to IBM Cloud VCF using Veeam include the following:

- Network Configuration: Implement appropriate networking configurations to ensure secure and efficient data transfer between on-premises systems and the IBM Cloud VCF environment.
- Resource Planning: Allocate sufficient resources within the IBM Cloud VCF environment to accommodate the workloads being migrated, ensuring performance and scalability requirements are met.
- Integration Testing: Conduct thorough testing to validate the integration between on-premises Veeam components and the IBM Cloud VCF infrastructure, ensuring compatibility and performance standards are achieved.
- Data Consistency: Utilize Veeam's replication features to maintain data consistency during the migration process, reducing the risk of data loss or corruption.

## Conclusions
{: #veeam-conclusion}

Migrating VMware workloads to IBM Cloud using Veeam provides a robust and flexible solution for enterprises seeking to enhance their data protection and disaster recovery capabilities. By leveraging Veeam's seamless integration with IBM Cloud's VMware offerings, businesses can achieve high availability, secure backup, and efficient recovery of critical applications and data. Careful planning and consideration of network configurations, resource allocation, and compatibility are essential to ensure a smooth and successful migration process.

## References(Veeam doc Suresh)

- [Veeam on IBM Cloud](/docs/vmwaresolutions?topic=vmwaresolutions-arch-pattern-vcf-veeam-con)
- [Veeam Replication Connectivity on VMware Cloud Foundation](/docs/vmwaresolutions?topic=vmwaresolutions-arch-pattern-vcf-veeam-xconnectivity)
- [Veeam Backup Service for VMware Cloud Foundation](/docs/vmware-service?topic=vmware-service-tenant-veeam)
- [Veeam Network connectivity](/docs/vmwaresolutions?topic=vmwaresolutions-arch-pattern-vcf-veeam-xconnectivity)
