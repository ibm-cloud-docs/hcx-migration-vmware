---

copyright:

years: 2024

lastupdated: "2025-03-03"

keywords:

subcollection: hcx-migration-vmware

---

{{site.data.keyword.attribute-definition-list}}

# Migrate with Veeam
{: #veeam}

## Overview
Veeam on IBM Cloud is a third-party add-on service that seamlessly integrates with IBM Cloud for VMware Solutions, providing robust backup and recovery capabilities for VMware workloads. This service ensures high availability and offers recovery points for critical applications and data, including enterprise solutions like Oracle and SAP HANA. By leveraging Veeam's integration, businesses can achieve rapid and reliable restoration of files, individual items, or entire virtual machines (VMs) across on-premises, hybrid, and public cloud environments. Additionally, Veeam facilitates the efficient movement of backup files to cost-effective IBM Cloud Object Storage, optimizing storage costs without compromising data accessibility.

## Deployment of Veeam in IBM Cloud Classic Environment

### Architecture of Veeam on Client Side

In the IBM Cloud Classic environment, the client-side architecture involves deploying the Veeam Backup & Replication (VBR) server within the client's on-premises infrastructure. This setup allows for centralized management of backup and replication tasks. The VBR server coordinates with Veeam proxies and repositories to handle data processing and storage. Proxies are responsible for data movement, optimizing the transfer between source and target, while repositories serve as storage locations for the backup data. This configuration ensures efficient data protection and recovery processes.

### Architecture of Veeam on IBM Cloud VMware Solutions (VCS) Side

On the IBM Cloud VCS side, Veeam components are deployed to facilitate seamless integration with the client's on-premises VBR server. This includes setting up Veeam proxies within the IBM Cloud environment to handle incoming replication traffic and manage data efficiently. These proxies communicate with the on-premises VBR server, enabling secure and optimized data transfer. Additionally, backup repositories can be configured within IBM Cloud to store replicated data, providing a scalable and secure solution for disaster recovery and data archiving.

### Migration Considerations and Requirements

When planning a migration to IBM Cloud Classic using Veeam, consider the following:

-   Network Connectivity: Establish a secure and reliable network connection between the on-premises infrastructure and IBM Cloud. This may involve configuring VPNs or dedicated connections to ensure data integrity during transfer.
-   Resource Allocation: Ensure that adequate compute and storage resources are provisioned in IBM Cloud to handle the incoming workloads and data.
-   Compatibility: Verify that the on-premises VMware environment is compatible with IBM Cloud's VMware offerings to ensure a smooth migration process.
-   Downtime Planning: Develop a strategy to minimize downtime during the migration, possibly by leveraging Veeam's replication capabilities to synchronize data before cutting over to the new environment.

## Deployment of Veeam in IBM Cloud VMware Cloud Foundation (VCF) Environment**

### Architecture of Veeam on Client Side

In a VCF environment, the client-side architecture remains similar, with the Veeam Backup & Replication server managing backup and replication tasks. The VBR server interfaces with Veeam proxies and repositories to handle data operations, ensuring efficient management of backup and replication processes.

### Architecture of Veeam on IBM Cloud VCF Side

Within the IBM Cloud VCF environment, Veeam components are deployed to integrate seamlessly with the client's VBR server. This includes setting up Veeam proxies within the management domain of the VCF architecture. These proxies handle data processing tasks, facilitating efficient backup and replication operations. Backup repositories can also be established within the IBM Cloud VCF environment to store backup data securely. This setup ensures that data protection operations are optimized and aligned with the VCF infrastructure.

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
