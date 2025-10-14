# 🛰️ Automated ISP Infrastructure Deployment
**End-to-End Network Automation with Ansible, EVE-NG and MPLS L3VPN**

---

## 🌐 Topology Overview
<img width="2880" height="1186" alt="image" src="https://github.com/user-attachments/assets/4f975881-d797-4dd5-875f-970096b88f02" />


Each PE supports multiple customer VRFs (e.g., `Cust_A`, `Cust_B`), forming end-to-end **L3VPN connectivity** across the MPLS backbone.

---

## 🚀 Project Summary

This project automates a complete **ISP-grade MPLS L3VPN network** using **Ansible** and **EVE-NG**.

From Layer 3 interfaces to BGP VPNv4 peering, all configurations are provisioned dynamically through **idempotent Ansible playbooks**.  
The goal is to simulate a service-provider backbone with **OSPF, MPLS, MP-BGP and VRFs**, while minimizing manual configuration time.

---

## ⚙️ Features Automated

| Feature                    | Description                                                               |
|----------------------------|---------------------------------------------------------------------------|
| **Interface Provisioning** | Assigns IP addresses and enables core/edge interfaces automatically       |
| **OSPF Configuration**     | Builds dynamic OSPF adjacencies and router-IDs per device                 |
| **MPLS Enablement**        | Activates `mpls ip` and `mpls ldp autoconfig` on all OSPF interfaces      |
| **VRF Deployment**         | Creates customer VRFs with RD / RT and assigns CE-facing interfaces       |
| **VRF OSPF Process**       | Runs per-VRF OSPF instances and exchanges routes with PEs                 |
| **MP-BGP Setup**           | Configures vpnv4 address-family, extended communities and redistribution |
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
```
### Edit device variables

Modify host-specific details in host_vars/Rx.yml:
```bash
interfaces:
  - name: FastEthernet0/0
    ip: 192.168.1.1
    mask: 255.255.255.252
ospf_process: 100
ospf_area: 0
```
### Run Playboks
```bash
ansible-playbook CE_OSPF.yml
ansible-playbook P_Config.yml
ansible-playbook PE_Config.yml
```
### Verify connectivity
```bash
show mpls ldp neighbor
show ip route vrf Cust_A
show bgp vpnv4 unicast all summary
```
### Repository Structure
```bash
├── ansible.cfg
├── CE_Config.yml
├── host_vars
│ ├── R1.yml
│ ├── R2.yml
│ ├── R3.yml
│ ├── R4.yml
│ ├── R5.yml
│ └── R6.yml
├── inventory.ini
├── MP-BGP.yml
├── Neig_check.yml
├── P_config.yml
├── PE_Config.yml
```
## 📊 ARA Integration (Ansible Run Analysis)

To monitor and visualize every playbook execution, this project integrates **[ARA](https://ara.recordsansible.org/)** — an Ansible callback plugin that logs, indexes and presents configuration runs via a web interface.

Once installed and configured:

```bash
pip install ara[server]
ara-manage runserver
```

### Learning Outcomes
•	Understand full ISP backbone design with OSPF + MPLS + BGP + VRF
•	Automate multi-stage configurations using Ansible loops and host_vars
•	Validate MPLS label propagation and L3VPN reachability
•	Deploy ECMP-based MPLS transport with minimal manual steps
•	Integrate ARA for post-run configuration tracking

### References
https://www.cisco.com/c/en/us/support/docs/multiprotocol-label-switching-mpls/mpls/13733-mpls-vpn-basic.html
[https://medium.com/r/?url=https%3A%2F%2Fara.recordsansible.org%2F](https://ara.recordsansible.org)
https://docs.ansible.com/ansible/latest/collections/cisco/ios/index.html
https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/iproute_ospf/command/iro-cr-book.html


### Author
Ashok Kumar Reddy Naguri
Graduate Student | Network Automation | CCNA | DevNet Associate
Boston, MA, USA
