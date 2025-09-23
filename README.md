#  Lab Project: Simulated Network Attack and Defense using OPNSense

This project presents a **realistic simulation of cyberattacks and defensive countermeasures** using professional penetration testing tools and open-source firewall technologies.  
We replicate real-world attack scenarios, observe system behavior under threat, and deploy robust protections via **OPNSense + Suricata**.


 **[Download_Attack_Report_OPNSense.docx](Attack_Report_OPNSense.docx)**  

---

##  Objectives

- Simulate a **real-world attack** from an external network on DMZ-hosted services
- Monitor and detect malicious activity using OPNSense
- Implement firewall rules to **block and isolate** hostile traffic
- Enable and configure IDS (Suricata) for live threat detection
- Evaluate effectiveness of defense based on logs, traffic, and outcomes

---

##  Lab Network Architecture

A fully isolated lab environment was deployed using three virtual machines:

| Host           | Role                            |
|----------------|---------------------------------|
| **Kali Linux** | Attacker (external host)        |
| **Ubuntu**     | Target (in DMZ zone)            |
| **OPNSense**   | Firewall, Router, IDS/IPS layer |

The network is segmented into **WAN / LAN / DMZ**, with OPNSense as the central node for routing and filtering.

---

##  Simulated Attacks

###  Service Recon & Access Attempt

- `nmap -A` was used from Kali Linux to scan services exposed by the DMZ target.
- Open ports like `80` and `53` were identified and probed.
- **Result:** All connections were blocked, and the attempts were logged by OPNSense.

>  Attack was detected in Live View monitoring  
>  No data was transferred — OPNSense successfully neutralized the attempt

---

###  ICMP Flood (DoS Simulation)

- A high-frequency **ICMP flood (ping flood)** was launched to simulate Denial of Service
- Thousands of ICMP requests per second were sent from the attacker
- The target system was stress-tested under load

**Result:**
- OPNSense filtered and dropped most packets based on the configured rules
- Suricata flagged and logged suspicious traffic
- The target remained stable and operational

>  Defense handled DoS-level stress efficiently

---

##  Defense Implementation

###  OPNSense Firewall Rules

- Custom firewall policies to restrict external access to DMZ
- ICMP, HTTP, and port-based filtering applied
- Interface-based segmentation to isolate zones

###  Suricata IDS

- Enabled with Deep Packet Inspection (DPI)
- Signature-based rules triggered on flood behavior
- Alerts logged in the OPNSense dashboard and system logs

---

##  Outcome

- Both attacks were **successfully detected, documented, and mitigated**
- Logs and screenshots provide full evidence of blocked attempts
- The system remained resilient under load
- Demonstrates the power of combining firewall and IDS technologies

---
##  Full Report with Screenshots

A detailed lab report is included in the repository, covering:

- Attack setup and execution
- Firewall and IDS/IPS configuration
- Results of threat mitigation
- Step-by-step screenshots

 **[Download_Attack_Report_OPNSense.docx](Attack_Report_OPNSense.docx)**  

---

##  Conclusion

This lab demonstrated the effectiveness of using **OPNSense** and **Suricata** to detect and block network attacks in a segmented environment.

Two simulated attacks were conducted:

-  Targeted service scan from Kali Linux  
-  ICMP flood (DoS-style attack)

**Key Results:**

-  Unauthorized traffic was successfully blocked by OPNSense firewall rules  
-  Suricata detected and logged suspicious activity in real time  
-  The target system (Ubuntu in DMZ) remained stable throughout the attacks  
-  Most malicious packets were filtered before reaching the destination

---

-  ## ⚠️ Legal Disclaimer

>  **Warning:** All tests were performed in a controlled and isolated environment.  
>  Do not perform similar actions on real networks without explicit permission.  
>  This project is for **educational and ethical purposes only**.
