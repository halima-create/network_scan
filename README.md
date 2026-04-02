# network_scan
# Target Assessment: 10.84.107.20

## 1. Project Overview
This repository contains reconnaissance data and enumeration logs for the target IP **10.84.107.20**. The primary goal is to map the attack surface and identify potential misconfigurations in network services.



## 2. Scan Results Summary
**Scan Date:** 2026-04-02  
**Target:** `10.84.107.20`  
**Scope:** Ports 1-1024

### Found Services
| Port | Service | State | Potential Risk |
| :--- | :--- | :--- | :--- |
| 53 | DNS | **OPEN** | Zone Transfers (AXFR), Cache Poisoning, Information Leakage |



## 3. Detailed Enumeration

### DNS (Port 53)
Initial findings suggest an active DNS service. Further testing is required to determine the software version and whether it allows unauthorized zone transfers.

**Next Commands to Execute:**
```bash
# Version Detection
nmap -sV -p 53 10.84.107.20

# Test for Zone Transfer (AXFR)
dig axfr @10.84.107.20 [domain_if_known]

# Check for DNS Recursion
nmap -p 53 --script dns-recursion 10.84.107.20
