# Azure Fundamentals Capstone Project  
### Building a Secure Multi-VNet Cloud Environment on Microsoft Azure

![Architecture Diagram](./Azure%20Fundamentals%20Capstone%20Project%20Seyi.PNG)

---

## 📌 Project Overview  
This project demonstrates the design and deployment of a **secure multi-VNet Azure environment**, built as part of an Azure Fundamentals capstone. It follows best practices in **network segmentation**, **identity management**, **private connectivity**, and **zero-trust principles**.

The environment includes:

- A **Hub–Spoke VNet architecture**
- Azure **Bastion** for secure VM access (no public IPs)
- Azure **Key Vault** with managed identity access
- Azure **Storage Account** using **private endpoints** (no public exposure)
- Network Security Groups (NSGs) controlling traffic flow
- Private VM-to-VM connectivity across VNets using **VNet Peering**

This repo contains all documentation, architecture diagrams, and screenshots to verify the deployment.

---

## 🧱 Architecture Components  

### **1. Hub VNet (VNet1)**
- Subnet: `nimbus-hub-subnet`
- VMs:  
  - `vm-hub-1`  
  - `vm-hub-2`
- Attached: NSG
- Peering to Spoke VNet

### **2. Spoke VNet (VNet2)**
- Subnet: `nimbus-spoke-subnet`
- VM:  
  - `vm-spoke-1`
- Attached: NSG
- Houses the **private Storage Account endpoint**

### **3. Security Services**
- **Azure Bastion** → SSH access to all VMs without public IPs  
- **Azure Key Vault** → Secrets stored securely, accessible only via Managed Identity  
- **NSGs** → Rules for SSH from Bastion, ICMP between VNets, and deny-all defaults  

### **4. Storage**
- **Private Endpoint Only** (Public network access = Disabled)
- Blob container used for file uploads (`test.txt`)

---

## 🔐 Key Security Features

### **Zero Public Exposure**
- No VM has a public IP  
- Bastion handles all SSH traffic  
- Storage Account is private-only  
- Key Vault access restricted to managed identity

### **Restricted Network Flows**
- SSH: Allowed **only** from Azure Bastion  
- ICMP traffic allowed within VNets for testing  
- Deny-all catch rules at bottom of NSGs  

### **Identity-First Architecture**
- Key Vault is accessed using **Managed Identity**, not credentials  
- No secrets stored on VMs or hard-coded  

---

## 📸 Screenshots Included

All verification screenshots are stored in:

Nimbus_Capstone_Screenshots.zip

yaml
Copy code

They demonstrate:

- VNet peerings  
- NSG rule configurations  
- Private endpoint settings  
- Storage access disabled  
- Key Vault secrets  
- Bastion terminal session  
- VM list showing no public IPs  

---

## 📂 Repository Structure

azure-fundamentals-capstone/
│── Azure Fundamentals Capstone Project Seyi.PNG # Architecture diagram
│── Azure Fundamentals Capstone Project Seyi.drawio # Editable diagram
│── Nimbus Azure Fundamentals Capstone Project.docx # Full project report
│── Nimbus_Capstone_Screenshots.zip # Screenshot evidence
│── README.md # Project documentation

yaml
Copy code

---

## 🧪 Connectivity Tests Performed

### ✔ SSH from Bastion  
Connected to `vm-hub-1` successfully.

### ✔ Private ICMP Tests  
From `vm-hub-1`:
ping 10.0.1.5 # vm-hub-2
ping 10.1.1.4 # vm-spoke-1

yaml
Copy code
Both returned valid replies, confirming:

- VNet peering  
- NSG rules  
- Private routing  

---

## 🛠 Azure Services Used

- **Azure Virtual Networks (Hub & Spoke)**
- **VNet Peering**
- **Azure Bastion**
- **Azure Storage (Blob)**
- **Private Endpoints**
- **Azure Key Vault**
- **Managed Identities**
- **NSGs (Network Security Groups)**

---

## 🚀 Deployment Skills Demonstrated  

This project demonstrates fundamental cloud engineering and DevOps-aligned skills, including:

- Infrastructure design following Hub–Spoke topology  
- Secure access patterns using Bastion  
- Identity-based security using Managed Identity  
- Private service access (no public endpoints)
- Environment hardening with NSGs  
- Effective cloud documentation & verification  

---

## 👤 Author  
**Oluwaseyi Adesegun Bello**  
DevOps Engineer · MSc Human-Centred AI  
Security+ Certified · Azure · Terraform · Kubernetes · Linux  
GitHub: https://github.com/seyiabello  
LinkedIn: https://www.linkedin.com/in/oluwaseyi-bello-2653a2215/

