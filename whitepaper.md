---
copyright:
  years: 2025
lastupdated: "2025-04-22"

keywords:

subcollection: hcx-migration-vmware

---

{{site.data.keyword.attribute-definition-list}}

# Migration Overview
{: #migration-overview}

This whitepaper address and covers IBM Cloud migration options for customers who would like to consider migrating VMware workloads to IBM Cloud VMware environent.

The Whitepaper will cover high level recommendations and approach.

As enterprises accelerate their cloud adoption journeys, moving VMware workloads to the cloud has become a top priority for IT leaders. IBM Cloud provides a robust VMware environment that allows organizations to migrate workloads with minimal disruption, leveraging industry-leading tools and methodologies.
{: shortdesc}

For CTOs and CIOs evaluating cloud migration, it is crucial to choose the right migration approach to align with business goals, operational efficiency, and risk mitigation. This blog provides an overview of the top five migration strategies for moving VMware workloads to IBM Cloud:

1. VMware HCX
2. Veeam
3. Zerto
4. VMware Cloud Director Availability (VCDA)
5. PrimaryIO

Each of the following migration methods offers unique advantages, addressing different use cases such as workload mobility, disaster recovery, data replication, and cost efficiency.

## 1. VMware HCX
{: #overview-hcx}

VMware HCX (Hybrid Cloud Extension) is a purpose-built solution designed to simplify workload migration and inter-connectivity between on-premises data centers and IBM Cloud. It enables live migrations without downtime, making it ideal for businesses that require continuous availability. Key benefits include the following:

* Seamless large-scale migration of workloads without reconfiguration.
* Supports vMotion for real-time migration and bulk migration for large workloads.
* WAN optimization improves data transfer efficiency.
* Offers disaster recovery capabilities to minimize risks.
* Ideal for companies requiring long-term hybrid cloud strategies.

### VMware HCX Overview
{: #hcx-overview}

VMware HCX on IBM Cloud is a robust solution for seamless workload migration and application mobility between on-premises VMware environments and IBM Cloud. It enables enterprises to modernize infrastructure with minimal downtime by automating large-scale live migrations and optimizing network performance. HCX provides secure, encrypted connectivity, simplifying hybrid cloud adoption without requiring application refactoring. Integrated with IBM Cloud for VMware Solutions, it ensures high availability, scalability, and operational consistency. Businesses benefit from reduced migration complexity, lower costs, and enhanced disaster recovery capabilities, making it ideal for enterprises transitioning to a hybrid or multi-cloud architecture.

Please visit the following link for further reading on HCX, [VMware HCX](https://www.vmware.com/products/cloud-infrastructure/hcx){: external}. Also visit [VCF CORE TECH](https://vcfcore.tech){: external}, a blog with extensive HCX information.

### IBM Cloud VMware overview
{: #hcx-ibmcloud-overview}

IBM Cloud for VMware Solutions is a cloud-based offering that allows organizations to extend or migrate their existing VMware-based virtualized datacenters to the IBM Cloud. The solution offers different deployment options, including self-managed and managed models, and can be used for both virtualized and cloud-native applications. Key features and benefits include the following:

* Extending Existing Datacenters - The solution facilitates extending on-premises VMware environments to the cloud, allowing for flexible capacity management and resource allocation.
* Migration to the Cloud - It supports the migration of existing VMware workloads to the cloud, enabling businesses to modernize their infrastructure and leverage cloud services.
* Disaster Recovery and Business Continuity - IBM Cloud for VMware Solutions can serve as a cost-effective disaster recovery site or provide off-site backup options, enhancing business resilience.
* Cloud Native Applications - The solution can host cloud-native applications alongside traditional VMware workloads, providing a unified platform for different application types.
* Flexibility and Scalability- The solution offers flexibility in deployment options and allows for scaling resources up or down as needed, based on workload demands.
* Security and Compliance - The solution provides a secure and compliant platform for running VMware workloads, with options for enhanced security features.
* Deployment Models:
  * Self-managed - Provides single-tenant, bare-metal infrastructure with full control over the hypervisor and vCenter Server, ideal for organizations needing high levels of isolation and control.
  * Managed - Utilizes VMware Cloud Director for a managed, cost-effective solution, ideal for cost-conscious organizations or those needing quick migration of VMs to the cloud.
* Management and Control - With the self-managed model, customers have access to the native VMware stack to manage resources and workloads, similar to their on-premises environments. In the managed model, IBm manages up to and including the hypervizor so that customers can focus on the workloads

IBM Cloud for VMware Solutions provides a comprehensive platform for extending and migrating VMware workloads to the cloud, offering a flexible and secure environment for running various types of applications.
HCX provides the flexibility of extending the networks of on-premises data centers into IBM Cloud, enabling the migration of virtual machines (VMs) to and from the IBM Cloud without any conversion or change. HCX creates an abstraction layer that enables application mobility and infrastructure hybridity through securely stretched networks. You can modernize your VMware environment from legacy VMware vSphere software versions to the most recent vSphere version without having to refractor or modify your existing application. HCX allows you to bring your IP subnet ranges into IBM Cloud, which ensures IP consistency through a hybrid deployment, and it also provides high level security with end-to-end suite B encryptions.

For further information regarding HCX on IBM Cloud please follow this link [HCX Overview on IBM Cloud](/docs/vmwaresolutions?topic=vmwaresolutions-hcx_considerations).

### Key Features and Benefits
{: #hcx-ibmcloud-overview-benefits}

The following are the key features and benefits of VMware HCX:

* Seamless and live workload migration.
* VMware HCX on IBM Cloud supports multiple migration types in line to your business requirement.
* Allows organizations to move workloads to the cloud without major reconfiguration or performance impact.
* Hybrid cloud mobility provides an automated and secure extension of VMware environments between on-premises data centers and IBM Cloud. It creates high-performance, encrypted network tunnels between environments, enabling workload mobility without network reconfiguration.
* Network Extension, HCX’s Layer 2 network extension allows businesses to extend on-premises VLANs to IBM Cloud without changing IP addresses.
* WAN optimization improves performance, reducing latency and bandwidth consumption during migration.
* With simplified operations and automation, HCX simplifies workload migration with an intuitive interface, reducing manual efforts and operational complexity. It automates VM movement, ensuring faster cloud adoption without impacting productivity.

#### Deployment on IBM Cloud
{: #hcx-ibmcloud-overview-deployment}

While IBM Cloud has a number of VMware offering, only the following offer suitable deployment models for VMware HCX

**VMware Cloud Foundation for Classic - Automated:** A single-tenant, self-managed, automated build model offering higher levels of isolation for enhanced security and compliance readiness. The offering is an integrated VMware software-defined data center (SDDC) stack, including vSphere, NSX-T and optionally vSAN. This model is ideal for organizations requiring dedicated resources and greater control over their environment. VMware HCX can be automatically deployed onto this platform.

**VMware Cloud Foundation for Classic - Flexible:** A single-tenant, self-managed, manual build model offering clients with in-depth skills to build their own environment on top of vSphere according to their architecture needs. VMware HCX can be manually deployed onto this platform.

**IBM Cloud for VMware Cloud Foundation (VCF) on VPC:** A single-tenant, self-managed, automated build model deployed on IBM Cloud's Virtual Private Cloud (VPC) infrastructure. It provides a fully integrated VMware VCF stack, including vSphere, vSAN, NSX-T, and SDDC Manager. HCX can be manually installed. This deployment can support both VCF consolidated and VCF standard architecture models, allowing flexibility based on organizational needs.

* [Architecture](/docs/vmwaresolutions?topic=vmwaresolutions-hcx-archi-overview)
* [Ordering HCX](/docs/vmwaresolutions?topic=vmwaresolutions-hcx_ordering)
* [HCX Architecture-VCF on VPC](/docs/vmwaresolutions?topic=vmwaresolutions-arch-pattern-vcf-hcx-con)
* [HCX site peering & service mesh in IBM Cloud](/docs/vmwaresolutions?topic=vmwaresolutions-arch-pattern-vcf-hcx-xconnectivity)

#### Pre-Requisites for Migration
{: #hcx-prereq}

Deploying VMware HCX for migration requires meeting specific prerequisites on both the source side (on-premises) and target side (IBM Cloud). Ensuring these requirements are met is crucial for a seamless migration experience.

##### On-Premises Requirements
{: #hcx-prereq-onprem}

Review the following documents:

* [Source site](/docs/vmwaresolutions?topic=vmwaresolutions-hcx-archi-source)
* [Client Deployment setup](/docs/vmwaresolutions?topic=vmwaresolutions-hcxclient-planning-prep-install)

##### IBM Cloud Requirements
{: #hcx-prereq-cloud}

Review the following document:

* [Target site with NSX-T deployments](/docs/vmwaresolutions?topic=vmwaresolutions-hcx-archi-target-t)

##### Network Connectivity Requirements
{: #hcx-prereq-networking}

The following define the network connectivity requirements:

* Internet connectivity to enable registration and product updates, and optionally network extension and migration.
* Optionally, IBM Cloud Direct Link for private, high-speed connectivity for network extension and migration.
* The target site requires NSX-T integration for network segmentation and security enforcement.
* Public IPs (if required for public-facing workloads).
* Proper firewall and security policies configured to allow necessary traffic.
* For further networking port configuration and understanding the requirement, visit the following link [Network Port Requirements](/docs/vmwaresolutions?topic=vmwaresolutions-hcx-archi-port-req)
* To extend on-premises networks to IBM Cloud, HCX must connect to a vSphere Distributed Switch (vDS) or NSX-T on-premises.

### VMware HCX Deployment Technical Considerations  
{: #hcxconsideration}

Successful deployment of VMware HCX for cloud migration requires careful planning across several key areas, including network connectivity, migration methods, licensing, security, and performance optimization**. This section outlines the critical factors to consider when implementing HCX for workload mobility to IBM Cloud.  

#### Network Connectivity
{: #hcx-prereq-networkconnectivity}

Reliable and high-performance connectivity is essential for secure and efficient workload migration. HCX supports multiple connectivity options:

* HCX over the Internet – Suitable for proof of concept (PoC), development, or small-scale migrations. HCX over a VPN is not recommended due to the additional overheads of the VPN. HCX uses encryption to protect the network extension or migration data transfer.  
* HCX over IBM Cloud Direct Link – Provides higher bandwidth, lower latency, and improved security by avoiding public internet exposure.  

For production environments, IBM Cloud Direct Link is the recommended approach due to its SLA-backed performance and reliability.  

#### Migration Methods
{: #hcx-prereq-migrationmethods}

VMware HCX provides multiple migration techniques to accommodate different workload requirements, availability needs, and operational constraints:

* HCX vMotion – Enables live migration with zero downtime, best suited for critical workloads requiring continuous availability.  
* Replication Assisted vMotion (RAV) – Uses replication technology to achieve near-zero downtime, making it ideal for enterprise applications.  
* Bulk Migration – Designed for large-scale workload moves where scheduled downtime is acceptable.  
* Cold Migration – Requires complete VM downtime, primarily used for non-production workloads or maintenance scenarios.  
* OS Assisted Migration – Allows the migration of non-vSphere workloads, extending HCX’s capabilities beyond traditional VMware environments.  

#### Security and Compliance Considerations  
{: #hcx-prereq-security}

Data security is a key concern when migrating workloads across hybrid environments. HCX provides multiple mechanisms to ensure data integrity:

* Suite-B encryption – Secures all in-flight data using military-grade Suite-B encryption.  
* Direct Link – Provides private connectivity with enhanced security by eliminating exposure to the public internet.  

#### Network Extension and IP Management  
{: #hcx-prereq-network-extension}

Extending your network to IBM Cloud during migration is critical to avoid reconfiguration of applications and minimize disruption:

* Network Extension Service – Preserves existing IP and MAC addresses, ensuring seamless migration without requiring network changes.  
* Re-IP Workflows – Applied when IP conflicts arise, requiring address reassignment.  

For most use cases, Network Extension Service is leveraged as it simplifies migration and reduces reconfiguration efforts.  

#### Performance Optimization with HCX WAN Acceleration
{: #hcx-prereq-optimization}

To optimize network efficiency, HCX includes built-in WAN acceleration features:

* Deduplication – Eliminates redundant data transmission to improve throughput.  
* Compression – Reduces the data footprint for faster migration over constrained network links.

#### vSphere Versions
{: #hcx-prereq-vsphere-versions}

See [HCX supported platforms](https://cloud.ibm.com/infrastructure/vmware-solutions/console/newserviceentry/HCX/vcs_nsx_t) for supported vSphere versions:

### Conclusions
{: #hcx-conclusion}

Migrating VMware workloads to IBM Cloud using HCX provides a robust and flexible solution for enterprises seeking to migrate workloads from on-premises to IBM Cloud for re-hosting application workloads with cloud agility. With HCX, you can migrate workloads from vSphere and non-vSphere (KVM and Hyper-V) environments to IBM Cloud with zero downtime and enable moving applications to the latest VCF software and hardware environment.

### References
{: #hcx-reference}

* [VMware HCX on IBM Cloud](/docs/vmwaresolutions?topic=vmwaresolutions-hcx_considerations)
* [VMware Solutions on IBM Cloud](/docs/vmwaresolutions)
* [Official HCX Documentation from Broadcom](https://techdocs.broadcom.com/us/en/vmware-cis/hcx.html){: external}

## 2. Veeam – Backup & Replication for Data Protection
{: #overview-veeam}

Veeam is an industry leader in backup, replication, and disaster recovery. Organizations leveraging Veeam can backup on-premises VMware environments and restore them directly into IBM Cloud. Key benefits include the following:

* Ensures data protection and business continuity with secure backups.
* Supports incremental replication, reducing migration downtime.
* Ransomware protection through immutable storage and encrypted backups.
* Works well for enterprises that require a backup-first approach before migration.

### Overview of Veeam on IBM Cloud
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

### Deployment of Veeam in IBM Cloud Classic environment
{: #veeam-ibmcloudclassic}

#### Architecture of Veeam on IBM Cloud
{: #veeam-ibmcloudclassic-veeamarchitecture}

Typically in a migration scenario, the Veeam Backup & Replication (VBR) server is already deployed within the client's on-premises infrastructure. This setup allows for centralized management of backup and replication tasks. The VBR server coordinates with Veeam proxies and repositories to handle data processing and storage. Proxies are responsible for data movement, optimizing the transfer between source and target, while repositories serve as storage locations for the backup data. This configuration ensures efficient data protection and recovery processes.

If the VBR server is not already deployed then the VBR server can be deployed in IBM Cloud, with the required Veeam components deployed on-premises.

#### Architecture of Veeam on IBM Cloud VMware Solutions (VCF for Classic)
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

#### Migration Considerations and Requirements
{: #veeam-ibmcloudclassic-vcfveeammigrationrequirements}

When planning a migration to IBM Cloud Classic using Veeam, consider the following:

- Network Connectivity: Establish a secure and reliable network connection between the on-premises infrastructure and IBM Cloud. This may involve configuring VPNs or dedicated connections to ensure data integrity during transfer.
- Resource Allocation: Ensure that adequate compute and storage resources are provisioned in IBM Cloud to handle the incoming workloads and data.
- Compatibility: Verify that the on-premises VMware environment is compatible with IBM Cloud's VMware offerings to ensure a smooth migration process.
- Downtime Planning: Develop a strategy to minimize downtime during the migration, possibly by leveraging Veeam's replication capabilities to synchronize data before cutting over to the new environment.

### Deployment of Veeam in IBM Cloud VPC Environment (VCF for VPC)
{: #veeam-vcfveeamVCF}

#### Architecture of Veeam on Client Side
{: #veeam-vcfveeamVCF-archclient}

In a VCF environment, the client-side architecture remains similar, with the Veeam Backup & Replication server managing backup and replication tasks. The VBR server interfaces with Veeam proxies and repositories to handle data operations, ensuring efficient management of backup and replication processes.

#### Architecture of Veeam on IBM Cloud VCF Side
{: #veeam-vcfveeamVCF-archcloud}

Within the IBM Cloud VCF environment, Veeam components are deployed to integrate seamlessly with the client's VBR server. This includes setting up Veeam proxies within the management domain of the VCF architecture. These proxies handle data processing tasks, facilitating efficient backup and replication operations. Backup repositories can also be established within the IBM Cloud VCF environment to store backup data securely. This setup ensures that data protection operations are optimized and aligned with the VCF infrastructure.

![Veeam architecture on IBM Cloud VPC](diagrams/Veeam-vpc.svg)

#### Migration Considerations and Requirements
{: #veeam-vcfveeamVCF-considerations}

Key considerations for migrating to IBM Cloud VCF using Veeam include the following:

- Network Configuration: Implement appropriate networking configurations to ensure secure and efficient data transfer between on-premises systems and the IBM Cloud VCF environment.
- Resource Planning: Allocate sufficient resources within the IBM Cloud VCF environment to accommodate the workloads being migrated, ensuring performance and scalability requirements are met.
- Integration Testing: Conduct thorough testing to validate the integration between on-premises Veeam components and the IBM Cloud VCF infrastructure, ensuring compatibility and performance standards are achieved.
- Data Consistency: Utilize Veeam's replication features to maintain data consistency during the migration process, reducing the risk of data loss or corruption.

### Conclusions
{: #veeam-conclusion}

Migrating VMware workloads to IBM Cloud using Veeam provides a robust and flexible solution for enterprises seeking to enhance their data protection and disaster recovery capabilities. By leveraging Veeam's seamless integration with IBM Cloud's VMware offerings, businesses can achieve high availability, secure backup, and efficient recovery of critical applications and data. Careful planning and consideration of network configurations, resource allocation, and compatibility are essential to ensure a smooth and successful migration process.

### References(Veeam doc Suresh)

- [Veeam on IBM Cloud](/docs/vmwaresolutions?topic=vmwaresolutions-arch-pattern-vcf-veeam-con)
- [Veeam Replication Connectivity on VMware Cloud Foundation](/docs/vmwaresolutions?topic=vmwaresolutions-arch-pattern-vcf-veeam-xconnectivity)
- [Veeam Backup Service for VMware Cloud Foundation](/docs/vmware-service?topic=vmware-service-tenant-veeam)
- [Veeam Network connectivity](/docs/vmwaresolutions?topic=vmwaresolutions-arch-pattern-vcf-veeam-xconnectivity)

## 3. Zerto – Continuous Data Protection & Disaster Recovery
{: #overview-zerto}

Zerto specializes in disaster recovery and workload mobility by offering continuous data replication with near-zero downtime. This solution is well-suited for organizations requiring high availability and resilience. Key benefits include the following::

* Journal-based recovery enables point-in-time restores, preventing data loss.
* Supports automated failover and failback for minimal disruption.
* Works across multi-cloud and hybrid environments, giving businesses flexibility.
* Best for companies with strict RTO/RPO requirements.

### Overview of Zerto on IBM Cloud
{: #zerto-overview}

Zerto is a disaster recovery and migration solution that provides continuous data protection (CDP) for VMware workloads. It enables near-zero data loss and minimal downtime during migration by leveraging real-time replication, journal-based recovery, and automation. It brings together disaster recovery and data protection across on-premises, hybrid, and multi-cloud environments. A single, unified, and automated recovery and data management solution that simplifies the experience across all virtualized or cloud-based workloads.

Please visit the following link for further reading on Zerto, [Zerto Overview on IBM Cloud](https://www.ibm.com/products/zerto)

### Key benefits
{: #zerto-overview-benefits}

The key features and benefits of Zerto include the following:

1. Continuous data protection – Use agent-less, non-disruptive continuous data replication with journalling versus snapshots.
2. Built-in WAN optimization and encryption – The Zerto appliance replicates every change generated in real time to the target journal.
3. Data storage - A long-term retention repository allows you to store data for years on cost-effective Cloud Object Storage.
4. Native VMware and Zerto – The management server integrates with any hypervisor management platform.
5. Semplified deployment – An all-in-one cloud appliance combines management and replication components.

On IBM Cloud, Zerto automatic deployment is supported on VMware Cloud Foundation for Classic - Automated instances and can be deployed as an add-on service to the VCF instance.

### Architecture of Zerto on IBM Cloud
{: #zerto-overview-ertoarchitecture}

In the IBM Cloud environment, the architecture involves deploying the Zerto Virtual Manager (ZVM) server that is key management component that controls everything other than the actual replication of data. The ZVMs need to be installed both in the client's on-premises infrastructure and on IBM Cloud and then paired.

Moreover, a Virtual Replication Appliance (VRA) needs to be installed in each hypervisor host where VMs are to be moved from or to. The VRA manages the replication of data from the on prem to the IBM Cloud by adjusting the compression level according to CPU usage. See [The Zerto Solution Architecture](https://help.zerto.com/bundle/Admin.VC.HTML/page/The_Zerto_Solution_Architecture.htm){: external}.

#### Migration Considerations and Requirements
{: #zerto-deploymentclassic-migrationclassicconsiderations}

Consider the following when migrating using Zerto:

* Network Connectivity: Establish IBM Cloud Direct Link or VPN for seamless connectivity. On IBM Cloud Classic, the Direct Link or the VPN, can terminate to a Virtual Router Appliance (for example Juniper vSRX) to be deployed as Edge Cluster in the VMWare environment. In VPC the Direct Link will terminate into an instance of the Transit Gateway and a virtual firewall appliance on VPC (for example the Fortinet's FortiGate Next Generation Firewall) can be deployed into the VPC to control the network traffic.
  * The Zerto Virtual Manager needs to connect the Call Home feature for Zerto, on public internet. This requires to configure it by using a proxy or NAT connection to the public network.
  * The Zerto replication doesn't support Network Address Translation (NAT) traversal. Establishing connectivity between the IBM Cloud Zerto instance and your own data center might require customization of routes on the Zerto Virtual Manager appliances or Zerto Virtual Replication Appliances (VRAs) on either side.
* Storage & Compute Resources: Ensure your IBM Cloud VCF instance has enough capacity to handle incoming workloads. The VRA appliances alone require 100GB of disk.
* RPO & RTO Requirements: Define acceptable recovery point and recovery time objectives.
* Testing & Validation: Perform test fail-overs before production migration.

### Deployment of Zerto for IBM Cloud VMware Cloud Foundation for Classic
{: #zerto-deploymentclassic}

#### Architecture of Zerto on the on prem
{: #zerto-deploymentclassic-architectureclassiconprem}

The on-premise site architecture includes the following:

* Zerto Virtual Manager Appliance (ZVMA): a Linux-based virtual appliance featuring microservices for security and authentication, logging, and management. The ZVM Appliance runs on a secure Linux operating system, managing replication and orchestrating recovery operations.
* Zerto Virtual Replication Appliances (VRAs): Installed, from the ZVM console, to each ESXi host to replicate data continuously from the source to the target VRA.
* WAN Connection: Secure VPN or Direct Link connection between on-premises and IBM Cloud.

#### Architecture of Zerto on IBM Cloud VCF for Classic
{: #zerto-deploymentclassic-architectureclassicvcf}

On IBM Cloud VCF on Classic - Automated, the architecture includes the following:

* Zerto Virtual Manager (ZVM): Installed on a Microsoft Windows 2019 VSI on Classic, managing replication and orchestrating recovery operations. The installation os the ZVM is automated on IBM Cloud and can be done by simply adding the Zerto service to the VCF instance.
* Zerto Virtual Replication Appliances (VRAs): Installed on each ESXi host to replicate data continuously. They are deployed by IBM Cloud the automation only into the default cluster.
* One portable private IP address for the Zerto Virtual Manager.
* One private portable subnet dedicated to the VRA deployment.

The following image shows the migration pattern architecture for VMware workloads on {{site.data.keyword.Bluemix_notm}} VCF on Classic - Automated.

![Zerto Migration Architecture](diagrams/zerto_classic.svg){: caption="Zerto migration for VMware Workloads on {{site.data.keyword.Bluemix_notm}} Classic (VCF) architecture" caption-side="bottom"}

### Deployment of Zerto for IBM Cloud VCF for VPC
{: #zerto-deploymentvpc}

#### Architecture of Zerto on prem
{: #zerto-deploymentvpc-architecturevpconprem}

There are no differences for the on-premise architecture to migrate to the IBM Cloud VCF on VPC or to an IBM Cloud VCF on Classic offering. In fact, the architecture is the same and includes the following:

* Zerto Virtual Manager Applicance (ZVMA): a Linux-based virtual appliance featuring microservices for security and authentication, logging, and management. The ZVM Appliance runs on a secure Linux operating system, managing replication and orchestrating recovery operations.
* Zerto Virtual Replication Appliances (VRAs): Installed, from the ZVM console, to each ESXi host to replicate data continuously from the source to the target VRA.
* WAN Connection: Secure VPN or Direct Link connection between on-premises and IBM Cloud.

#### Architecture of Zerto on IBM Cloud VCF for VPC
{: #zerto-deploymentvpc-architecturevpcvcf}

There is no automation to install Zerto on an VCF for VPC instance, so all the components need to be manually installed:

* Zerto Virtual Manager Appliance (ZVMA): deployed into the Management overlay networks, managing replication and orchestrating recovery operations. It needs to access to public network to access the Call Home on Zerto for registration.
* Zerto VRAs: Installed on each ESXi hosts within the VCF environment.
* Transit Gateway: deployed and connected to the VMware VPC to allow connectivity between the VPC and the on-premise network via Direct Link

The following image is the migration pattern architecture for VMware workloads on {{site.data.keyword.Bluemix_notm}} VCF on VPC.

![Zerto Migration Architecture](diagrams/zerto_vpc.svg){: caption="Zerto migration for VMware Workloads on {{site.data.keyword.Bluemix_notm}} VPC (VCF) architecture" caption-side="bottom"}

## 4. VMware Cloud Director Availability (VCDA)
{: #overview-vcda}

VCDA is a VMware-native migration tool designed for cloud service providers and enterprises using VMware Cloud Director on IBM Cloud. It offers an integrated approach for disaster recovery and migration. Key benefits include the following:

* Designed for multi-tenant environments, making it a great choice for Managed Service Providers (MSPs).
* Automated replication and recovery ensure smooth migrations.
* Offers self-service capabilities for enterprises to manage their workloads.
* Recommended for businesses already using VMware Cloud Director.

### IBM Cloud VCDA Overview
{: #vcda-ibmcloud-overview}

The VMware Cloud Director Availability solution enables migration from on-premises to VMware Cloud Foundation as a Service as a Service (VCFaaS) at both the virtual machine and at the vApp level. 

The VCDA service is included by default in all multi-tenant virtual data centers (VDCs) and optionally included in your single-tenant VCFaaS Cloud Director site order at no charge. For a VCDA disaster recovery configuration, a monthly charge is incurred per protected virtual machine (VM).

IBM Cloud for IBMCloud VCFaaS with VCDA supports several migration scenarios:

- Migrate vCenter virtual machine workloads from on-premises and vCenter Server environments to VMware Cloud Foundation (VCF) as a Service over the public or private IBM network.
- Migrate workloads from VCF as a Service single-tenant and multi-tenant instances to another VCF as a Service instance.

For more details, see [VMware Cloud Foundation as a Service](/docs/vmware-service?topic=vmware-service-tenant-vcda)

IBM provides public instance endpoints with VCDA. Endpoints are used to access the VCDA web interface and also to migrate workloads. You can request new endpoints for private connections for an additional charge. With private endpoints, you can migrate workloads into VCF as a Service by using the IBM Cloud private network to improve consistency and security. Cloud-to-cloud migrations from both VMware Shared and from VCF as a Service to VCF as a Service are over the private network. See [Adding and deleting private instance endpoints with VCDA](/docs/vmware-service?topic=vmware-service-vcda-adding-deleting-private-ep).

### VCFaaS service models
{: #vcda-deployment}

IBM Cloud for VMware Cloud Foundation (VCF) as a Service (VCFaaS) has two service models:

Single-tenant - Dedicated infrastructure to host your virtual data centers (VDCs).
Multi-tenant  - Shared infrastructure to host your VDCs.

VCFaaS multi-tenant instances are deployed to all supported regions by IBM. You create your VDCs on the IBM managed infrastructure. VCFaaS single-tenant instances are provisioned by your organization. For both service models, IBM performs the configuration, hosting, operations, and lifecycle management of the VMware by Broadcom software so you can quickly deploy your VMware-based cloud computing environments.

For more details, see [VCF as a Service overview](/docs/vmwaresolutions?topic=vmwaresolutions-vmware-aas-overview). To understand the VMware Cloud Director and VMware Cloud Director Availability Versions for VCFaaS, see [VCF as a Service BOM](https://cloud.ibm.com/docs/vmware-service?topic=vmware-service-vmaas-bom).

### Key VCDA components
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

### Pre-requisites
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

### VCDA Architecture
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

### Conclusions
{: #vcda-conclusion}

Migrating VMware workloads to IBM Cloud VCFaaS using VCDA provides a robust and flexible solution for enterprises seeking to migrate workloads from source vSphere environments to IBM Cloud VCFaaS for re-hosting application workloads with cloud agility. With VCDA, you can migrate workloads quickly and easily from vSphere environments to IBM Cloud VCFaaS with options to host your VMware workloads on an IBM managed single-tenant or multi-tenant instance.

### References:
{: #vcda-reference}
- [Getting started with VCF as a Service](/docs/vmware-service?topic=vmware-service-getting-started)
- [What is VMware Cloud Director Availability](https://techdocs.broadcom.com/us/en/vmware-cis/cloud-director/availability/4-7/what-is-vcda.html){: external}

## 5. PrimaryIO
{: #overview-primaryio}

PrimaryIO offers a unique approach to workload migration and disaster recovery, focusing on reducing data transfer costs and accelerating time to cloud. Key benefits include the following:

* Selective data migration, reducing bandwidth and storage costs.
* Works efficiently for large-scale VMware migrations.
* Offers both lift-and-shift and re-platforming options.
* Best for enterprises looking to optimize cloud economics while migrating workloads.

### PrimaryIO Overview
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

### Key Benefits 
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

#### Protection of on-premise and migrated VMs
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

### Migration Considerations and Requirements
{: #primaryio-ibmcloudclassic-migration-requirement}

When planning a migration to IBM Cloud using PrimaryIO, consider the following:

- Network Connectivity: Data integrity, reliability and speed will be a function of the connectivity between the migration source VMs and the IBM Cloud target site. This must be in place prior to migration.
- Resource Allocation: The necessary credentialing as well as compute, network and storage resources must be properly provisioned in IBM Cloud in order to assure that anticipated performance of the migrated VMs in IBM Cloud.
- Compatibility: On prem VMs including edge security must be provisioned in a compatible IBM Cloud environment.
- Minimal Impact Planning: Methodology coupled with resource allocation needs to be well-planned in order to minimize impact to the applications, and by extension to the business dependent on those applications.

### Migration to IBM Cloud Classic Environment
{: #primaryio-ibmcloudclassic}

#### Architecture of PrimaryIO platform on IBM Cloud
{: #primaryio-ibmcloudclassic-prioarchitecture}

In the source environment, a VMware Installation Bundle (VIB) is installed on all ESXi hosts in a cluster to be migrated or protected by DRaaS/RRaaS. The VAIO filter coordinates with a block-sending agent responsible for sending new (initial) or changed blocks to a receiver agent running in the customer’s target site in IBM Cloud. Upon receipt of workload data, those blocks are committed to storage. The metadata keeping track of what VMs are being migrated (and potentially protected) and where the VM data resides are all kept in the SaaS control plane - an IBM Cloud-native Red Hat Openshift Kubernetes application running in IBM Cloud VPC. The PrimaryIO architecture is a truly modern application reflecting the state-of-the-art, designed with an in-depth knowledge of VMware, IBM Cloud and cloud-native design.

#### Architecture of PrimaryIO platform on IBM Cloud VMware Solutions (VCF for Classic)
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


### Migration to IBM Cloud VPC environment
{: #primaryio-vpc}

PrimaryIO has no significant architectural differences distinguishing IBM Cloud VPC from its IBM Cloud Classic offering. In fact, the SaaS platform is the same, whether on Cloud Classic or VPC. Due to differences between Classic and VPC, there are infrastructure and functional differences between migrated VMs in the two cloud environments. The single most significant difference between a Classic and VPC migration is the bare metal configuration options, coupled with the time it takes to implement configuration changes in the target account. The SLAs are purely a function of the IBM Cloud infrastructure limitations.

#### Architecture of PrimaryIO platform on IBM Cloud
{: #primaryio-vpc-prioarchitecturevpc}

In the source environment, a VMware Installation Bundle (VIB) is installed on all ESXi hosts in a cluster to be migrated or protected by DRaaS/RRaaS. The VAIO filter coordinates with a block-sending agent responsible for sending new (initial) or changed blocks to a receiver agent running in the customer’s target site in IBM Cloud. Upon receipt of workload data, those blocks are committed to storage. The metadata keeping track of what VMs are being migrated (and potentially protected) and where the VM data resides are all kept in the SaaS control plane - an IBM Cloud-native Red Hat Openshift Kubernetes application running in IBM Cloud VPC. The PrimaryIO architecture is a truly modern application reflecting the state-of-the-art, designed with an in-depth knowledge of VMware, IBM Cloud and cloud-native design.

#### Architecture of PrimaryIO platform on IBM Cloud VMware Solutions (VCF for VPC)
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

<<<<<<< Updated upstream
<<<<<<< Updated upstream
#### Migration Considerations and Requirements
{: #primaryio-vpc-migrations}

When planning a migration to IBM Cloud VPC using PrimaryIO, consider the following:

- Network Connectivity: Data integrity, reliability and speed will be a function of the connectivity between the migration source VMs and the IBM Cloud target site. This must be in place prior to migration.
- Resource Allocation: The necessary credentialing as well as compute, network and storage resources must be properly provisioned in IBM Cloud in order to assure that anticipated performance of the migrated VMs in IBM Cloud.
- Compatibility: On prem VMs including edge security must be provisioned in a compatible IBM Cloud environment.
- Minimal Impact Planning: Methodology coupled with resource allocation needs to be well-planned in order to minimize impact to the applications, and by extension to the business dependent on those applications.

#### References
=======
=======
>>>>>>> Stashed changes
### References
>>>>>>> Stashed changes
{: #primaryio-references}

PrimaryIO references are listed below:

* [PrimaryIO](https://www.primaryio.com/){: external}
* [ProtectIO DRaaS Managed Service](https://cloud.ibm.com/catalog/services/protectio-draas-managed-service)
* [ConvertIO VMware Workload Migration and Conversion](https://cloud.ibm.com/catalog/services/convertio-vmware-workload-migration-and-conversion)
* [VMware Cloud Migration Services](https://cloud.ibm.com/catalog/services/vmware-cloud-migration-services)

## Choosing the Right Migration Approach
{: #overview-approach}

The ideal migration strategy depends on your organization's priorities, whether it’s minimizing downtime, ensuring data protection, or optimizing costs. The table below is a high-level comparison:

| **Migration Option** | **Best For**                          | **Key Features**                            |
|----------------------|---------------------------------------|---------------------------------------------|
| VMware HCX           | Live migration, hybrid cloud          | vMotion, bulk migration, WAN optimization   |
| Veeam                | Backup-driven migration               | Secure backups, ransomware protection       |
| Zerto                | Disaster recovery, near-zero downtime | Continuous replication, failover & failback |
| VCDA                 | Multi-tenant cloud environments       | VMware-native integration, self-service     |
| PrimaryIO            | Cost-optimized migration              | Selective data transfer, cloud efficiency   |

## Conclusion
{: #overview-conclusion}

Migrating VMware workloads to IBM Cloud requires strategic planning and the right tools to ensure seamless execution. Whether you prioritize live migration with VMware HCX, disaster recovery with Zerto, backup-first migration with Veeam, native VMware integration with VCDA, or cost-efficient migration with PrimaryIO, IBM Cloud provides a flexible and scalable platform to support your business needs.

For CTOs and CIOs, selecting the optimal migration approach ensures that your cloud journey aligns with business agility, operational continuity, and financial goals. By leveraging the right tools, enterprises can confidently transition to IBM Cloud and unlock the full potential of VMware in the cloud era.
