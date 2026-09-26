# Centralized Log Monitoring and Threat Detection System using ELK Stack

1. Project Type
Major Project

2. Overview

A centralized log monitoring and threat detection system designed to collect, analyze, and visualize security logs using the ELK Stack.

The project focuses on centralized monitoring of Windows and Linux security events and identifying suspicious activities such as failed login attempts and SSH login events.

3. Technologies

- Elasticsearch
- Logstash
- Kibana
- Winlogbeat
- Filebeat
- KQL

4. System Components

| Component | Purpose |
|---|---|
| Elasticsearch | Stores and searches collected logs |
| Logstash | Processes and forwards log data |
| Kibana | Provides log analysis, visualization, and dashboards |
| Winlogbeat | Collects Windows event logs |
| Filebeat | Collects Linux and system logs |

5. Key Areas

- Centralized log collection
- Windows and Linux log monitoring
- Failed login detection
- SSH login monitoring
- Security event analysis
- Kibana dashboards
- Threat detection
- Detection rule configuration

6. Project Workflow

Windows / Linux Endpoints
          ↓
   Winlogbeat / Filebeat
          ↓
       Logstash
          ↓
     Elasticsearch
          ↓
        Kibana
          ↓
Log Analysis & Visualization
          ↓
 Threat Detection & Alerts
