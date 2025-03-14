---

copyright:
  years: 2024
lastupdated: "2025-03-14"

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

- Continuous data protection – Use agent-less, non-disruptive continuous data replication with journaling versus snapshots. 
- Built-in WAN optimization and encryption – The Zerto appliance replicates every change generated in real time to the target journal. 
- Data storage - A long-term retention repository allows you to store data for years on cost-effective Cloud Object Storage.
- Native VMware and Zerto – The management server integrates with any hypervisor management platform. 
- Semplified deployment – An all-in-one cloud appliance combines management and replication components.


On IBM Cloud, Zerto automatic deployment is supported on VMware Cloud Foundation for Classic - Automated instances and can be deployed as an add-on service to the VCF instance. 

## Deployment of Zerto for IBM Cloud VMware Cloud Foundation for Classic
{: #deploymentclassic}

### Architecture of Zerto on the on prem Site
{: #architectureclassiconprem}

The on prem site architecture includes:

Zerto Virtual Manager (ZVM): Installed on a Windows VM, managing replication and orchestrating recovery operations.

Zerto Virtual Replication Appliances (VRAs): Installed on each ESXi host to replicate data continuously.

WAN Connection: Secure VPN or Direct Link connection between on-premises and IBM Cloud.

### Architecture of Zerto on IBM Cloud VCF Side
{: #architectureclassicvcf}

On IBM Cloud VCF, the architecture involves:

Zerto Virtual Manager (ZVM): Installed on a Microsoft Windows 2019 VSI on Classic, managing replication and orchestrating recovery operations.

Zerto Virtual Replication Appliances (VRAs): Installed on each ESXi host to replicate data continuously. They are deployed only into the default cluster.

One portable private IP address for the Zerto Virtual Manager

One private portable subnet dedicated to the VRA deployment

### Migration Considerations and Requirements
{: #migrationclassic}

Network Connectivity: Establish IBM Cloud Direct Link or VPN for seamless connectivity. The Zerto Virtual Manager needs to connect the Call Home feature for Zerto, on public internet. This requires to configure it by using a proxy or NAT connection to the public network. Also, the Zerto replication doesn't support Network Address Translation (NAT) traversal. Establishing connectivity between the IBM Cloud Zerto instance and your own data center might require customization of routes on the Zerto Virtual Manager appliances or Zerto Virtual Replication Appliances (VRAs) on either side.

Storage & Compute Resources: Ensure IBM Cloud has enough capacity to handle incoming workloads. The VRA appliances alone require 100GB of disk themselves. 

RPO & RTO Requirements: Define acceptable recovery point and recovery time objectives.

Testing & Validation: Perform test failovers before production migration.


## Deployment of Zerto for IBM Cloud VMware Cloud Foundation for VPC
{: #deploymentvpc}

### Architecture of Zerto on the on prem Site
{: #architecturevpconprem}

The on prem site architecture includes:

Zerto Virtual Manager (ZVM): Installed on a Windows VM, managing replication and orchestrating recovery operations.

Zerto Virtual Replication Appliances (VRAs): Installed on each ESXi host to replicate data continuously.

WAN Connection: Secure VPN or Direct Link connection between on-premises and IBM Cloud.

### Architecture of Zerto on IBM Cloud VCF Side
{: #architecturevpcvcf}

Zerto is not supported as an add on service on VCF for VPC so there is no automation and all the components need to be manually installed.

Zerto VRAs: Installed on each ESXi hosts within the VCF environment.

Zerto Virtual Manager (ZVM): Installed on a Microsoft Windows 2019 VSI on VPC, deployed into the Management overlay networks, managing replication and orchestrating recovery operations. Access to public network to access the Call Home on Zerto is required

Transit Gateway: deployed and connected to the VMWAre VPC to allow connectivity between the VPC and the on-prem network via Direct Link


## Migration Considerations and Requirements
{: #migrationvpc}

Multi-Site Recovery: Plan for failover and failback between on-prem and IBM Cloud VCF.

Network Connectivity: implement appropriate networking configurations to ensure secure and efficient data transfer between on-premises systems and the IBM Cloud VCF environment
Storage Optimization: vSAN cluster (over the NVMe drives on the bare metal servers) needs to have enough capacity to handle incoming workloads.
Security & Compliance: Align with regulatory requirements for data protection.
Automation & Monitoring: Leverage IBM Cloud monitoring tools for monitoring the infrastucture

## Conclusions
{: #conclusions}

Migrating VMware workloads to IBM Cloud using Zerto offers a seamless, low-downtime solution with continuous replication and automated failover. Organizations can leverage IBM Cloud for scalable, resilient disaster recovery while ensuring high availability of critical applications. Planning, testing, and optimizing network and storage configurations are crucial for a successful migration. 
