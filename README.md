# Cybersecurity Log Monitoring Project – ELK Stack

> **Student Lab Project**  
> **Student:** Gagana C P  
> **Focus:** System log collection, SIEM concepts, and monitoring security events  

This is a practical learning project where I set up and tested a centralized log monitoring lab using the ELK Stack (Elasticsearch, Logstash, Kibana) and Beats. The goal was to understand how system security logs from Windows and Linux machines are collected, parsed, and monitored for suspicious activity.

---

## What I Was Trying to Learn

When managing servers or computers, checking logs individually on each machine is slow and difficult. In organizations, security teams use SIEM (Security Information and Event Management) tools to gather logs in one place so they can spot issues quickly.

I wanted to set up a practical lab environment to learn:
* How log shipping agents collect operating system events.
* How Logstash parses and structures raw logs.
* How Elasticsearch indexes logs for fast searching.
* How to write basic queries in Kibana to look for failed logins and security warnings.

---

## Lab Architecture

```text
[ Windows 10 / 11 Endpoint ]         [ Linux / Ubuntu Endpoint ]
   (Winlogbeat Agent)                   (Filebeat Agent)
           │                                    │
           │ Event ID 4624 / 4625               │ /var/log/auth.log
           ▼                                    ▼
       ┌────────────────────────────────────────────┐
       │             Logstash Pipeline              │
       │    (Filters, parses timestamps & fields)   │
       └─────────────────────┬──────────────────────┘
                             │
                             ▼
       ┌────────────────────────────────────────────┐
       │               Elasticsearch                │
       │             (Indexes log events)           │
       └─────────────────────┬──────────────────────┘
                             │
                             ▼
       ┌────────────────────────────────────────────┐
       │             Kibana Dashboard               │
       │       (Visualizations & KQL Search)        │
       └────────────────────────────────────────────┘
```

---

## What I Configured & Tested

1. **Windows Event Log Collection (Winlogbeat):**
   * Configured Winlogbeat on Windows to monitor the `Security` event channel.
   * Focused on specific Windows Security Event IDs:
     * **Event ID 4625:** An account failed to log on (wrong password or invalid user).
     * **Event ID 4624:** An account was successfully logged on.
     * **Event ID 4720:** A user account was created.

2. **Linux Authentication Logs (Filebeat):**
   * Installed Filebeat on an Ubuntu virtual machine to monitor `/var/log/auth.log`.
   * Collected SSH login attempts, `sudo` command executions, and authentication failures.

3. **Logstash Processing Pipeline:**
   * Configured an input listener to receive log events from Beats over port 5044.
   * Applied basic filter blocks to extract IP addresses, usernames, and event categories into structured fields.

4. **Kibana Dashboards & Querying:**
   * Built visual dashboard panels in Kibana showing:
     * Total failed vs. successful logins over time.
     * Top usernames targeted during failed login attempts.
     * Sources of authentication events.
   * Practiced writing KQL (Kibana Query Language) filters such as:
     ```text
     winlog.event_id: 4625 and user.name: "Administrator"
     ```

---

## What I Observed

* **Brute-Force Patterns:** During testing, repeated failed attempts with invalid passwords quickly stand out as sudden spikes on the Kibana timeline chart.
* **Log Volume:** Even a single machine generates a large volume of background logs, showing why filtering and field parsing in Logstash is important before indexing into Elasticsearch.

---

## What I Learned

* The practical difference between log shippers (Beats), log parsers (Logstash), search indexes (Elasticsearch), and visualization frontends (Kibana).
* How Windows records authentication events through numeric Event IDs.
* How to use Kibana to search through logs and identify patterns rather than scrolling through raw text files.

---

## Note on Project Scope

This is an educational lab project built on local/virtual machines to learn log management and SIEM fundamentals. It is not a commercial enterprise SOC deployment.
