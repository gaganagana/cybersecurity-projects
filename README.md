# Cybersecurity & Threat Detection Projects

[![SIEM](https://img.shields.io/badge/SIEM-ELK%20Stack-005571.svg?logo=elastic)](https://www.elastic.co/)
[![Elasticsearch](https://img.shields.io/badge/Search-Elasticsearch-005571.svg?logo=elasticsearch)](https://www.elastic.co/elasticsearch)
[![Kibana](https://img.shields.io/badge/Visualization-Kibana-E8488B.svg?logo=kibana)](https://www.elastic.co/kibana)
[![Logstash](https://img.shields.io/badge/Pipeline-Logstash-005571.svg?logo=logstash)](https://www.elastic.co/logstash)
[![Beats](https://img.shields.io/badge/Agents-Winlogbeat%20%7C%20Filebeat-00BFB3.svg)](https://www.elastic.co/beats/)

Hands-on cybersecurity implementations, centralized security information and event management (SIEM) pipelines, log monitoring, and threat detection systems developed through professional certifications (Unlox Edge, Tata Insights Forage) and academic research.

---

## 🛡️ Featured: Centralized Log Monitoring & Threat Detection System (ELK Stack)

### 📌 Project Overview
A centralized SIEM and log monitoring infrastructure designed to ingest, process, store, and visualize security events from distributed Windows and Linux endpoints to rapidly detect unauthorized access attempts and suspicious system activities.

### 🏗️ Architecture & Data Flow

```text
  Windows Endpoints                   Linux Endpoints
   (Winlogbeat)                        (Filebeat)
         │                                  │
         └─────────────────┬────────────────┘
                           │
                           ▼
                  Logstash Pipeline
              (Filter, Parse & Enrich)
                           │
                           ▼
                  Elasticsearch Cluster
               (Indexing & Storage Engine)
                           │
                           ▼
                 Kibana Dashboard & SIEM
            (KQL Queries, Visualizations, Alerts)
```

### ⚙️ Core Components & Tools

| Component | Role in Pipeline |
| :--- | :--- |
| **Elasticsearch** | High-performance search and analytics engine for storing and querying indexed security logs. |
| **Logstash** | Centralized data processing pipeline that ingests logs, applies filters, parses timestamps, and routes structured events. |
| **Kibana** | Centralized SIEM management console providing interactive security dashboards, KQL search, and alert rules. |
| **Winlogbeat** | Lightweight shipper installed on Windows hosts to stream Windows Security Event logs (Event IDs 4624, 4625, etc.). |
| **Filebeat** | Lightweight shipper on Linux hosts collecting `/var/log/auth.log`, system syslog, and SSH authentication events. |

---

## 🔍 Key Detection Capabilities & Rule Sets

- **Brute Force & Multiple Failed Logins**: Detection rules configured to trigger high-severity alerts when repeated failed login attempts occur within a condensed time window.
- **SSH Authentication Monitoring**: Real-time tracking of successful and failed SSH connection attempts across Linux servers.
- **Centralized Security Dashboard**: Visual metrics tracking authentication trends, top targeted usernames, source IP distributions, and active alert severity levels.

---

## 📸 Implementation Dashboards & Evidence

The complete project report and high-resolution setup screenshots are located in [`Major-Project-ELK`](./Major-Project-ELK):
- Detailed Project Report: [`ELK-Centralized-Log-Monitoring-Threat-Detection-Report.pdf`](./Major-Project-ELK/ELK-Centralized-Log-Monitoring-Threat-Detection-Report.pdf)
- Visual Artifacts:
  - Ubuntu Network Adapter Configuration
  - Elasticsearch & Kibana Setup
  - Custom Data View Configurations
  - Kibana Security Monitoring Dashboard
  - Threat Detection Rule Definitions
  - Multiple Failed Login Alert Details

---

## 📜 Certifications Grounding This Work

- **Cybersecurity Analyst Job Simulation** — *Tata Insights (Forage)*
- **Unlox Edge Certification – Cyber Security (Course Completion)** — *Credential ID: UNXCS-2026-9339*
- **Unlox Edge Certification – Cyber Security (Internship & Project-Based Learning)** — *Credential ID: UNXCS-INT-9339*
