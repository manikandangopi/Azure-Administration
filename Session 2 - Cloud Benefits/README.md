# Azure High Availability Architecture

High Availability (HA) in Azure ensures that applications and workloads remain resilient against failures at different levels — from server racks, to data centers, to entire regions.

---

## 1. High Availability vs Maximum Availability

| Layer                | Server/Application Tier             | Physical Infrastructure       |
|----------------------|-------------------------------------|-------------------------------|
| **Application Tier** | App Server 1, 2, 3 (VM1, VM2, VM3)  | Server1, Server2, Server3     |
| **Availability Set** | VM distribution across racks        | Rack1, Rack2, Rack3 (1 DC)    |
| **Availability Zone**| DC1, DC2, DC3                       | Physically separated DCs      |
| **Paired Region**    | Region1, Region2                    | Region-wide Disaster Recovery |

---

## 2. Detailed Breakdown

| Concept              | Analogy                | Real Azure Terms                | Purpose                                    |
|----------------------|------------------------|---------------------------------|--------------------------------------------|
| **Availability Set** | 3 racks in 1 room      | Rack1, Rack2, Rack3 (1 DC)      | Protect against **rack-level failure**      |
| **Availability Zone**| 3 rooms in 1 building  | DC1, DC2, DC3 in 1 region       | Protect against **datacenter failure**      |
| **Paired Region**    | 2 buildings in 2 cities| East US ↔ West US               | Protect against **regional outage (DR)**    |

---

## 3. Azure HA Options Comparison

| Feature                | Availability Set          | Availability Zone              | VM Scale Set                     |
|-------------------------|---------------------------|--------------------------------|----------------------------------|
| **High Availability Level** | Rack/host level       | Datacenter level               | Auto-scale & zone-level resilience |
| **SLA (2+ VMs)**       | 99.95%                   | 99.99%                         | 99.99% (with zones)              |
| **Fault Isolation**    | ✅ Yes                   | ✅ Yes                         | ✅ Yes (config dependent)        |
| **Auto Scaling**       | ❌ No                    | ❌ No                          | ✅ Yes                           |
| **VM Placement**       | Manual                   | Manual                         | Automated                        |
| **Load Balancer**      | Recommended              | Recommended                    | Required for public access       |
| **Cost**               | No extra cost            | Zone transfer costs may apply  | VM + autoscaling costs           |
| **Region Dependency**  | Single datacenter        | Multiple datacenters           | Region-wide                      |

---

## 4. Azure Regions

- A **region** is a geographic area containing one or more data centers.  
- Azure currently has **60+ regions globally**.  
- Benefits: latency optimization, redundancy, and compliance.  

**Examples of Regions**:
- East US → Virginia, USA  
- West Europe → Netherlands  
- Southeast Asia → Singapore  
- Central India → Pune, India  
- Japan East → Tokyo, Japan  

---

## 5. Availability Zones

An **Availability Zone** is a physically separated datacenter within an Azure region.  
Each zone is isolated but interconnected with **< 2 ms latency**.

### Core Features
- **Fault Isolation**: Independent power, cooling, and networking  
- **3 Zones per Region**: Minimum 3 per supported region  
- **Low-Latency**: < 2 ms between zones  
- **High Availability SLA**: 99.99% uptime with multi-zone deployments  
- **Zonal & Zone-Redundant**: Choose specific zone or spread across zones  

---

### Deployment Types

#### 1. Zone Deployment
- Manual placement into Zone 1, 2, or 3  
- Example: Web tier in Zone 1, DB in Zone 2  
- ✅ Pros: High control, zone-local latency  
- ❌ Cons: No auto-failover (if a zone fails, VM goes down)  

#### 2. Zone-Redundant Deployment
- Azure automatically replicates across multiple zones  
- Examples: Azure SQL DB (Business Tier), Zone-Redundant Storage (ZRS)  
- ✅ Pros: Built-in HA, automatic failover  
- ❌ Cons: Slightly higher cost, possible cross-zone latency  

---

### Service Support for Zones

| Service              | Zone Deployment | Zone-Redundant |
|----------------------|-----------------|----------------|
| **Virtual Machines** | ✅ Yes          | ❌ No (manual only) |
| **Azure SQL DB**     | ❌ No           | ✅ Yes (Zone-redundant config) |
| **Azure Storage**    | ✅ Yes (ZRS)    | ✅ Yes (ZRS – Zone-Redundant Storage) |

---

## 6. Availability Sets

An **Availability Set** is a **logical grouping of VMs** to ensure high availability by spreading them across **Fault Domains** and **Update Domains**.

### Key Components
| Term                | Description |
|---------------------|-------------|
| **Fault Domain**    | Physical hardware grouping (rack, power, network). Max: 3 |
| **Update Domain**   | Logical grouping for planned maintenance (patches, updates). Max: 20 |
| **Availability Set**| Container holding 2+ VMs spread across fault/update domains |

### Real-World Example
- Web App VMs (VM1, VM2) → Availability Set 1  
- SQL Backend VMs → Availability Set 2  
- If **Rack1 fails**, VM2 continues running  
- If Azure **patches VM1**, VM2 is unaffected  

**SLA**: 99.95% (with 2+ VMs in set)  

---

## 7. VM Scale Sets

A **VM Scale Set (VMSS)** is an Azure compute resource for **deploying and managing a group of load-balanced VMs** that can **auto-scale**.  

- Supports zone-level distribution (for resiliency).  
- Integrated with Azure Load Balancer or Application Gateway.  
- Key for elastic workloads (e.g., web apps, APIs, microservices).  
- SLA: 99.99% with zone distribution enabled.  

---

## Summary

- **Availability Set** → Rack-level HA (99.95%)  
- **Availability Zone** → Datacenter-level HA (99.99%)  
- **Paired Region** → Region-level DR  
- **VM Scale Sets** → Autoscaling + HA (99.99%)  

👉 Together, these ensure business continuity across hardware, datacenter, and region failures.
