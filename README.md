# azure-cyber-range
A multi-tier Azure cyber range demonstrating cloud network micro-segmentation, NSG configuration, and attack reconnaissance emulation. Validates zero-trust security controls and generates security telemetry for incident documentation.
# Azure Multi-Node Cyber Range & Network Segmentation Lab

## Executive Summary
This project demonstrates the deployment of a hardened, multi-node cloud-based cyber range within Microsoft Azure. The primary focus of this exercise was to establish strict network micro-segmentation between a public-facing frontend node (`cyber-range-vm`) and a secured internal backend node (`snet-internal`), validate Network Security Group (NSG) boundaries, and emulate reconnaissance to verify defensive posture.

---

## Architecture & Infrastructure
* **Resource Group**: `cyber-range-vm_group`
* **Frontend Node (`cyber-range-vm`)**: Ubuntu 24.04 LTS instance serving as the initial access point and testing platform. Configured with Azure Bastion access.
* **Backend Node (`snet-internal`)**: Internal Ubuntu 24.04 LTS instance (`10.0.1.4`) isolated within a private subnet.
* **Security Controls**: Azure Network Security Groups (NSGs) enforced to isolate subnets and restrict default traffic flows.
* **Runtime Stack**: Cloud Infrastructure (Azure VNets, Subnets, NSGs), Ubuntu 24.04 LTS (GNU/Linux Kernel Azure), and native Bash TCP/IP stack utilities (`nc`, `ping`).

---

## Attack Emulation & Reconnaissance
To validate internal segmentation and generate security telemetry, an attack simulation was executed from the frontend node targeting the internal backend address (`10.0.1.4`).

### Reconnaissance Execution
* **Methodology**: Utilized native TCP connection utilities (`nc`) to perform a multi-port sweep across common service ports (`22`, `80`, `443`, `3389`).
* **Observed Output**: 
  ```text
  c: connect to 10.0.1.4 port 22 (tcp) timed out: Operation now in progress
  c: connect to 10.0.1.4 port 80 (tcp) timed out: Operation now in progress
  c: connect to 10.0.1.4 port 443 (tcp) timed out: Operation now in progress
  c: connect to 10.0.1.4 port 3389 (tcp) timed out: Operation now in progress
