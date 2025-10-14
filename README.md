# 🛰️ Automated ISP Infrastructure Deployment
**End-to-End Network Automation with Ansible, EVE-NG, and MPLS L3VPN**

---

## 🌐 Topology Overview


Each PE supports multiple customer VRFs (e.g., `Cust_A`, `Cust_B`), forming end-to-end **L3VPN connectivity** across the MPLS backbone.

---

## 🚀 Project Summary

This project automates a complete **ISP-grade MPLS L3VPN network** using **Ansible** and **EVE-NG**.

From Layer 3 interfaces to BGP VPNv4 peering, all configurations are provisioned dynamically through **idempotent Ansible playbooks**.  
The goal is to simulate a service-provider backbone with **OSPF, MPLS, MP-BGP, and VRFs**, while minimizing manual configuration time.

---

## ⚙️ Features Automated

| Feature                    | Description                                                               |
|----------------------------|---------------------------------------------------------------------------|
| **Interface Provisioning** | Assigns IP addresses and enables core/edge interfaces automatically       |
| **OSPF Configuration**     | Builds dynamic OSPF adjacencies and router-IDs per device                 |
| **MPLS Enablement**        | Activates `mpls ip` and `mpls ldp autoconfig` on all OSPF interfaces      |
| **VRF Deployment**         | Creates customer VRFs with RD / RT and assigns CE-facing interfaces       |
| **VRF OSPF Process**       | Runs per-VRF OSPF instances and exchanges routes with PEs                 |
| **MP-BGP Setup**           | Configures vpnv4 address-family, extended communities, and redistribution |
| **Idempotent Design**      | Uses `match: line` and host_vars for repeatable runs                      |
| **ARA Integration**        | Visualizes playbook runs and device configuration state                   |

---

## 🧰 Tools & Environment

| Tool           | Version / Details |
|----------------|------------------------------------------|
| **Ansible**    | 2.17 + (`cisco.ios` collection)          |
| **EVE-NG**     | Community Edition with Cisco IOL routers |
| **Python**     | 3.13 (virtual environment)               |
| **ARA**        | For playbook result tracking             |
| **Network OS** | Cisco IOS 15.x                           |
| **OS**         | macOS / Linux                            |

---

## 🪜 Quick Start

### 1️⃣ Clone the repository
```bash
git clone https://github.com/AshokKumarReddyNaguri24/Automating_Network_Infrastructure.git
cd Automating_Network_Infrastructure
ansible-galaxy collection install cisco.ios
'''


