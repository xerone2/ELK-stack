
# **ELK Stack**

### **Overview**

This project leverages the ELK (Elasticsearch, Logstash, Kibana) stack and Fleet agents to monitor and analyze logs from both Linux and Windows servers. The setup allows for real-time detection of failed SSH and RDP authentication attempts and enables security analysis through Kibana dashboards.

---

## **Architecture Diagram**

A high-level diagrammatic view of the technical stack has been created, showcasing the connections between:

- **Elasticsearch Server** (Linux)
- **Fleet Server** (Linux)
- **Windows Server** (RDP exposed)
- **Linux Server**(SSH enabled)
- **Fleet Agents** on Linux and Windows servers
- **Kibana** for visualization

---

### **1. Elastic Server Setup**

- **Environment**: Linux-based server running Elasticsearch.
- **Role**: Centralized data storage and search engine for ingested logs.
- **Configuration**: 
  - Elasticsearch installed and configured.
  - Fleet server connected to ingest logs.
  - Limit firewall rules

---

### **2. Fleet Server Setup**

- **Environment**: Linux-based server running Fleet, connected to Elasticsearch.
- **Role**: Manage the Fleet agents deployed on client servers (both Linux and Windows).
- **Configuration**: 
  - Fleet server set up to communicate with the Elasticsearch server.
  - Fleet agents installed on endpoints (Linux and Windows servers).

---

**Note: ElasticSearch and Fleet servers are kept in a seperate VPC(Virtual Private CLoud) for additional layer of security.**

---

### **3. Windows Server Setup**

- **Environment**: Windows Server with RDP port exposed for remote access.
- **Role**: Monitor and log remote access attempts through RDP.
- **Configuration**: 
  - Fleet agent installed on Windows server.
  - Logs related to RDP authentication attempt from Windows Defender and Sysmon logs are being collected.

---

### **4. Linux Server Setup**

- **Environment**: Linux server with SSH enabled for remote access.
- **Role**: Monitor and log remote access attempts through SSH.
- **Configuration**: 
  - Fleet agent installed on Linux server.
  - Logs related to SSH authentication attempts are being collected.

---

### **5. Rules and Alerts Setup**

- Created custom rules and alerts in Kibana to detect:
  - **Failed SSH authentication attempts** from the Linux server.
  - **Failed RDP authentication attempts** from the Windows server.

- **Alerts** trigger on detection of unauthorized access, providing real-time insights into potential security incidents.

---

### **6. Log Investigation and Mapping**

- **Kibana** has been used for:
  - Visualizing failed SSH and RDP login attempts.
  - Mapping the geographic locations of unauthorized access attempts globally.
  - Investigating patterns of attacks or repeated attempts.

---

### **Next Steps**

- Integration of endpoint detection with elastic defend.
- Additional configuration of Fleet agents for enhanced log collection.
- Implementing data pipelines for further log processing, if required.
- Setting up advanced alerting mechanisms for proactive incident response.
- Fine-tuning dashboards and visualizations for better monitoring.

---

This covers the current progress of the ELK stack project. Further documentation will be added as more features are implemented.
