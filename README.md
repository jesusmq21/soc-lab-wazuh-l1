# soc-lab-wazuh-l1
SOC Level 1 lab using Wazuh for log monitoring and incident detection
This project demonstrates a functional *SOC Level 1 laboratory* focused on log monitoring, alert detection, and incident analysis using *Wazuh*.

The lab simulates *insider threat behaviors* on a Linux endpoint instead of external penetration testing, aligning with real SOC operations.

## 🧠 Skills Demonstrated
- Log analysis (auth.log, syslog)
- Alert triage and validation
- Incident classification (SOC L1)
- Documentation and escalation procedures
- Linux security monitoring

## 🏗️ Architecture
- *SOC Server:* Ubuntu Server 22.04  
  - Wazuh Manager  
  - OpenSearch  
  - Wazuh Dashboard  

- *Monitored Endpoint:* Kali Linux  
  - Wazuh Agent  
  - SSH enabled  
  - rsyslog configured  

## 🚨 Documented Incidents
- SSH Brute Force Detection
- Misuse of sudo privileges (in progress)

## 📂 Repository Structure
See folders for incident reports, screenshots, and playbooks.

## 👤 Author
*Jesús Eduardo Machuca Quintero*  
SOC Analyst L1 (Junior) – Portfolio Project
