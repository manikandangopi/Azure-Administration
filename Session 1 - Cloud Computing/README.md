# Session 1 – Cloud Concepts and Benefits

## Topics Covered
1. Cloud Terminology  
2. Cloud Benefits  
   - High Availability  
   - Scalability  
   - Reliability  
   - Predictability  
   - Security and Governance  
   - Manageability  
3. Cloud Service Models  
4. Cloud Deployment Models  
5. Shared Responsibility Model  
6. Consumption-Based Model  
7. Cloud Characteristics  
8. Cloud Disadvantages  

---

## What is Cloud?
On-demand delivery of IT infrastructure and applications over the internet through a **Cloud Services Platform** using a **Pay-As-You-Go (PAYG)** pricing model.  

- Renting resources over the internet – e.g., Microsoft Azure.  
- Instead of buying and maintaining data centers, you **rent IT resources** such as servers, storage, networking, and applications.

---

## Cloud Concepts

| Concept               | Explanation |
|------------------------|-------------|
| **On-Demand Delivery** | Instant provisioning of resources like VMs, storage, databases, and networking, without manual procurement. |
| **Delivery via Internet** | Services are accessed remotely through the internet – typically over Public Cloud environments. |
| **Cloud Services Platform** | Cloud providers such as: <br> - Microsoft Azure <br> - Amazon Web Services (AWS) <br> - Google Cloud Platform (GCP) <br> - Oracle Cloud, IBM Cloud, etc. |
| **PAYG (Pay-As-You-Go)** | Utility-style billing based on actual consumption. <br> Example: Pay for VM usage per hour or per second. |
| **Cloud = Renting Resources** | Like renting power from a utility company, you rent compute, storage, and services from cloud providers. |

---

## Benefits of Cloud Computing

### 1. Trading CapEx for OpEx
| CapEx (Capital Expenditure) | OpEx (Operational Expenditure) |
|-----------------------------|--------------------------------|
| Heavy upfront investment in hardware (servers, storage, networking) | Pay-as-you-go model – billed monthly or annually |
| Own and manage physical infrastructure | No ownership – consume services as needed |
| **Example**: Before Azure: Buy servers & network equipment upfront.<br>Now: Use Azure resources and only pay for what you consume. | |

---

### 2. Benefit from Massive Economies of Scale
- Azure operates one of the **largest global cloud infrastructures**.  
- Microsoft negotiates bulk pricing for hardware, power, bandwidth.  
- Cost Benefit: Lower per-unit costs for compute, storage, and networking services.  
- **Example**: Shared use of a massive Azure data center reduces cost compared to building your own.

---

### 3. Stop Guessing Capacity
| Traditional IT | Azure Cloud |
|----------------|-------------|
| Overestimating = waste of resources | Auto-scale resources based on real usage |
| Underestimating = performance issues | Pay only for what you use, when you use it |

**Benefit:** Optimize cost + performance.  
No overprovisioning or capacity planning nightmares.

---

### 4. Go Global in Minutes
- Azure has **60+ regions worldwide** with local data centers.  
- Easily replicate environments across regions using templates or automation.  
- **Benefits:**
  - Reach global users with **low latency**.  
  - Comply with **data residency laws**.  
  - Improve performance using **regionally deployed apps**.  

---

### 5. Stop Spending on Data Center Maintenance
| Traditional On-Prem | Azure Cloud |
|---------------------|-------------|
| Own power, cooling, real estate, security, generators, UPS, etc. | Microsoft manages infrastructure for you |

**Benefit:**  
- No physical hardware to manage.  
- Reduced overhead costs.  
- IT teams focus on **innovation**, not infrastructure.

---

### 6. Increased Agility & Speed
| Traditional Provisioning | Azure Deployment |
|--------------------------|------------------|
| Takes weeks or months | Takes minutes |
| Manual setup | Automated with tools like ARM templates, Azure DevOps |

**Tools:**
- Azure Resource Manager (ARM)  
- Bicep Templates  
- Azure DevOps Pipelines  
- GitHub Actions  

**Benefit:**  
- Faster time to market  
- Rapid experimentation  
- Quickly respond to business changes  

---

## Note
- **Azure DevOps Pipelines** are sometimes referred to in the context of **Hybrid Cloud** scenarios, where automation supports both on-premises and cloud environments.

---
