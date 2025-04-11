---

copyright:
  years: 2024
lastupdated: "2025-04-11"

keywords:

subcollection: hcx-migration-vmware

---

{{site.data.keyword.attribute-definition-list}}


# Migrate with Zerto
{: #zerto}

Migrating VMware Workloads to IBM Cloud Using Zerto

## Overview of Zerto on IBM Cloud
{: #zertooverview}

Zerto is a disaster recovery and migration solution that provides continuous data protection (CDP) for VMware workloads. It enables near-zero data loss and minimal downtime during migration by leveraging real-time replication, journal-based recovery, and automation.
It brings together disaster recovery and data protection across on-premises, hybrid, and multi-cloud environments. A single, unified, and automated recovery and data management semplifies the experience across all virtualized or cloud-based workloads.

Please visit thte following link for further reading on Zerto.

[ZertoX Overview on IBM Cloud](https://www.ibm.com/products/zerto)


Key Features and Benefits

1.  Continuous data protection – Use agent-less, non-disruptive continuous data replication with journaling versus snapshots. 
2.  Built-in WAN optimization and encryption – The Zerto appliance replicates every change generated in real time to the target journal. 
3.  Data storage - A long-term retention repository allows you to store data for years on cost-effective Cloud Object Storage.
4.  Native VMware and Zerto – The management server integrates with any hypervisor management platform. 
5.  Semplified deployment – An all-in-one cloud appliance combines management and replication components.


On IBM Cloud, Zerto automatic deployment is supported on VMware Cloud Foundation for Classic - Automated instances and can be deployed as an add-on service to the VCF instance. 

### Architecture of Zerto on IBM Cloud
{: #zertoarchitecture}

In the IBM Cloud environment, the architecture involves deploying the Zerto Virtual Manager (ZVM) server that is key management component that controls everything other than the actual replication of data. The ZVMs need to be installed both in the client's on-premises infrastructure and on IBM Cloud and then paired.
Moreover, a Virtual Replication Appliance (VRA) needs to be installed in each hypervisor host where VMs are to be moved from or to. The VRA manages the replication of data from the on prem to the IBM Cloud by adjusting the compression level according to CPU usage. [learn more](https://help.zerto.com/bundle/Admin.VC.HTML/page/The_Zerto_Solution_Architecture.htm){: external}.


## Architecture of Zerto for IBM Cloud VMware Cloud Foundation for Classic
{: #zertodeploymentclassic}

### Architecture of Zerto on the on prem Site
{: #zertoarchitectureclassiconprem}

The on prem site architecture includes:

Zerto Virtual Manager Applicance (ZVMA): a Linux-based virtual appliance featuring microservices for security and authentication, logging, and management. The ZVM Appliance runs on a secure Linux operating system, managing replication and orchestrating recovery operations.

Zerto Virtual Replication Appliances (VRAs): To be installed, from the ZVM console, on each ESXi host to replicate data continuously from the 

WAN Connection: Secure VPN or Direct Link connection between on-premises and IBM Cloud.

### Architecture of Zerto on IBM Cloud VCF Side
{: #zertoarchitectureclassicvcf}

On IBM Cloud VCF, the architecture involves:

Zerto Virtual Manager (ZVM): Installed on a Microsoft Windows 2019 VSI on Classic, managing replication and orchestrating recovery operations. The installation os the ZVM is automated on IBM Cloud and can be done by simply adding the Zerto service to the VCF instance. 

Zerto Virtual Replication Appliances (VRAs): Installed on each ESXi host to replicate data continuously. They are deployed by IBM Cloud the automation only into the default cluster.  

One portable private IP address for the Zerto Virtual Manager

One private portable subnet dedicated to the VRA deployment

The following image is the migration pattern architecture for VMware workloads on {{site.data.keyword.Bluemix_notm}} VCF on Classic - Automated.

![Zerto Migration Architecture](diagrams/zerto_classic.svg){: caption="Zerto migration for VMware Workloads on {{site.data.keyword.Bluemix_notm}} Classic (VCF) architecture" caption-side="bottom"}


### Migration Considerations and Requirements
{: #zertomigrationclassicconsiderations}

-   Network Connectivity: Establish IBM Cloud Direct Link or VPN for seamless connectivity. On IBM Cloud Classic, the Direct Link or the VPN, can terminate to a Virtual Router Appliance (for example Juniper vSRX) to be deployed as Edge Cluster in the VMWare environment.
The Zerto Virtual Manager needs to connect the Call Home feature for Zerto, on public internet. This requires to configure it by using a proxy or NAT connection to the public network. Also, the Zerto replication doesn't support Network Address Translation (NAT) traversal. Establishing connectivity between the IBM Cloud Zerto instance and your own data center might require customization of routes on the Zerto Virtual Manager appliances or Zerto Virtual Replication Appliances (VRAs) on either side.
-   Storage & Compute Resources: Ensure IBM Cloud has enough capacity to handle incoming workloads. The VRA appliances alone require 100GB of disk themselves. 
-   RPO & RTO Requirements: Define acceptable recovery point and recovery time objectives.
-   Testing & Validation: Perform test failovers before production migration.


## Deployment of Zerto for IBM Cloud VMware Cloud Foundation for VPC
{: #zertodeploymentvpc}

### Architecture of Zerto on the on prem Site
{: #zertoarchitecturevpconprem}

There is are no differences for the on prem architecture to migrate to IBM Cloud VPC or to IBM Cloud Classic offering. In fact, the architecture  is the same and includes:

Zerto Virtual Manager Applicance (ZVMA): a Linux-based virtual appliance featuring microservices for security and authentication, logging, and management. The ZVM Appliance runs on a secure Linux operating system, managing replication and orchestrating recovery operations.

Zerto Virtual Replication Appliances (VRAs): To be installed, from the ZVM console, on each ESXi host to replicate data continuously from the 

WAN Connection: Secure VPN or Direct Link connection between on-premises and IBM Cloud.

### Architecture of Zerto on IBM Cloud VCF Side
{: #zertoarchitecturevpcvcf}

Zerto is not supported as an add on service on VCF for VPC so there is no automation and all the components need to be manually installed.

Zerto Virtual Manager Appliance (ZVMA): deployed into the Management overlay networks, managing replication and orchestrating recovery operations. It needs to access to public network to access the Call Home on Zerto for registration.

Zerto VRAs: Installed on each ESXi hosts within the VCF environment.

Transit Gateway: deployed and connected to the VMWAre VPC to allow connectivity between the VPC and the on-prem network via Direct Link

The following image is the migration pattern architecture for VMware workloads on {{site.data.keyword.Bluemix_notm}} VCF on VPC.

![Zerto Migration Architecture](diagrams/zerto_vpc.svg){: caption="Zerto migration for VMware Workloads on {{site.data.keyword.Bluemix_notm}} VPC (VCF) architecture" caption-side="bottom"}

## Migration Considerations and Requirements
{: #zertomigrationvpcconsiderations}

-   Network Connectivity: implement appropriate networking configurations to ensure secure and efficient data transfer between on-premises systems and the IBM Cloud VCF environment. In VPC the Direct Link will terminate into an instance of the Transit Gateway and a virtual firewall appliance on VPC (for example the Fortinet's FortiGate Next Generation Firewall) can be deployed into the VPC to control the network traffic.
-   Storage Optimization: vSAN cluster (over the NVMe drives on the bare metal servers) needs to have enough capacity to handle incoming workloads.
-   Security & Compliance: Align with regulatory requirements for data protection.
-   Automation & Monitoring: Leverage IBM Cloud monitoring tools for monitoring the infrastucture

## Conclusions
{: #conclusions}

Migrating VMware workloads to IBM Cloud using Zerto offers a seamless, low-downtime solution with continuous replication and automated failover. Organizations can leverage IBM Cloud for scalable, resilient disaster recovery while ensuring high availability of critical applications. Planning, testing, and optimizing network and storage configurations are crucial for a successful migration. 
