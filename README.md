# 🚨 SOC Automation Workflow: Wazuh + VirusTotal + n8n

This project automates Security Operations Center (SOC) workflows by integrating **Wazuh** (for file integrity monitoring), **VirusTotal** (for malware analysis), and **n8n** (for automation and alerting).  

It demonstrates how alerts from Wazuh can be automatically enriched and forwarded to security teams in real-time using VirusTotal intelligence and Discord/Gmail notifications.  

---

## 🔧 Features
- 📂 **File Integrity Monitoring (FIM):** Detects suspicious file changes (tested with EICAR).  
- 🔑 **Hash Extraction:** Automatically extracts MD5, SHA1, SHA256 from Wazuh alerts.  
- 🛡️ **VirusTotal Integration:** Queries file reputation and scan results.  
- 📩 **Alerting:** Sends formatted alerts to Gmail and Discord channels.  
- ⚡ **n8n Orchestration:** Fully automated with branching logic (Switch node).  

---

## 🖼 Workflow Diagram
Here’s the workflow in n8n:


<img width="1668" height="738" alt="workflow" src="https://github.com/user-attachments/assets/392e382e-b18e-4d37-b96a-2df9a06fc8b0" />


Here is the output generated on gmail and discord:


<img width="1486" height="770" alt="gmail_op" src="https://github.com/user-attachments/assets/8a9f2fbb-a95b-4425-95d6-619afdcd1424" />


<img width="1215" height="630" alt="discord_op" src="https://github.com/user-attachments/assets/ec9b8daa-0eb5-48a3-bfe6-2b715600fe61" />


---

## 🚀 How It Works
1. **Wazuh Agent** triggers alert (e.g., EICAR file creation or root login attempts).  
2. **Webhook Node (n8n)** receives the alert in JSON format.  
3. **JavaScript Function Nodes** parse alert data and extract file hashes.  
4. **HTTP Request Node** queries VirusTotal API with file hash.  
5. **Switch Node** decides routing based on severity/reputation.  
6. **Discord / Gmail Nodes** send final alerts to SOC team.  

---

## 📂 Repository Structure
