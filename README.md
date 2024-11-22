# Introduction to SIEM and Splunk
## Definition of SIEM
- SIEM (Security Information and Event Management) is a software solution that combines real-time monitoring, analysis of security alerts, and long-term storage of security data. It provides organizations with insights to detect, respond to, and mitigate potential cybersecurity threats.

## Key Features of SIEM:
- Log Collection and Normalization: Aggregates logs from multiple systems and standardizes their format for easy analysis.
- Real-Time Monitoring and Alerts: Continuously monitors network traffic and generates alerts for suspicious activities.
- Incident Response Support: Correlates data to provide actionable insights for incident handling.
- Compliance Management: Assists with regulatory compliance by maintaining audit trails.
- Data Retention: Ensures long-term storage of event logs for forensic analysis.


# About Splunk
- Splunk is a popular SIEM tool used for monitoring, searching, analyzing, and visualizing machine-generated data in real-time. It is widely adopted for cybersecurity, IT operations, and business analytics.

## Key Features of Splunk:
- Indexing and Search: Processes large volumes of data and makes it searchable in real-time.
- Custom Dashboards: Offers user-friendly visualizations for trends, alerts, and reports.
- Advanced Analytics: Uses machine learning for anomaly detection and predictive insights.

## How Splunk Helps in Security:
Detects unusual patterns, e.g., brute force attacks or malware infections.
Provides insights for proactive security measures.


# Splunk SIEM Project
- This project demonstrates how to set up and utilize Splunk as a Security Information and Event Management (SIEM) tool. It provides a comprehensive guide, from installation to creating dashboards, showcasing Splunk's capabilities in data ingestion, threat detection, and analysis.

# Table of Contents
1. Installing Splunk
2. Splunk Apps
3. Data Ingestion and Parsing
4.Search Processing Language (SPL)
5. Demo: Splunk Commands
6- Creating Dashboards


# 1. Installing Splunk
## Steps:
- Download Splunk Enterprise (free trial) from the Splunk website.
- Installation walkthrough for:
  - Linux: Use wget to download the package, followed by dpkg or rpm commands to install.
  - Windows: Download the installer, run it, and follow the wizard.
- Post-installation:
  - Access Splunk Web at http://localhost:8000 using default credentials.
  - IMAGE 


## 2. Splunk Apps
- Navigate to Apps → Find more apps on Splunkbase → Install desired apps (e.g., Splunk Security Essential).
## 3. Data Ingestion and Parsing
- Ingesting Data:
  - Configure inputs for logs from sources like:
    - Syslog (Linux servers, firewalls)
    - Windows Event Logs (via Universal Forwarder)
    - Custom application logs (e.g., web servers).
- Parsing Logs:
- Ensure data is indexed and sourcetypes are set (e.g., dns logs).
- Use field extractions to structure log data.

## 4. Search Processing Language (SPL)
- Overview:
  - SPL enables querying ingested data for analysis:

### Search Processing Language SPL

- <b><ins>Search</b></ins>
  - Description: Retriees events from the index
  - For example: Search error
  - Result: It finds all events containing the word " error" 
- <b><ins>Timechart</b></ins>
  - Description: Create a time-based chart of results
  - For example: index=security sourcetype=firewall | timechart count by action
  - Result: It counts firewall actions over time, grouped by the action type.
- <b><ins>Stat</b></ins>
  - Description: Computes aggregate statistic over the events
  - For example: index= security sourcetype=firewall | stats cont by src_ip
  - Result: It counts events grouped by source IP address.




### Advanced Search Commands 

- <b><ins>Eval</b></ins>
  - Description: Calculates an expression and assigns the result to a new field. 
  - For example: Index=security | eval is_internal=if(src_ip LIKE “192.168.%”, “internal”, “external”).
  - Result: It creates a new field is_initernal to classify Ip addresses as internal or external
- <b><ins>transaction</b></ins>
  - Description: Groups events that are related into a single event. 
  - For example: index=secuitty | transaction startswith=”login” endswith=”logout” maxspan=30m 
  - Result: It groups login and logout events into transaction with a maximum span of 30 minutes. 
- <b><ins>Lookup</b></ins>
  - Description: Enriches events with data from external sources. 
  - For example: index=security | lookup geoip ip AS(autonomous system number)  src_ip OUTPUT country 
  - Result: It enrcihes events with geographic information based on the source IP address. 


### Reporting and visualization Commands

- <b><ins>Chart</b></ins>
  - Description: Generates a chart from the result
  - For example: index=security | chart count by src_ip, dest_ip
  - Result: It creates a chart  of event counts grouped by source and destination IP addresses.
- <b><ins>Table</b></ins>
  - Description: Displays result in a table format 
  - For example: index=security | table src_ip, dest_ip, action
  - Result: It displays source IP, destination IP and action in  a table. 
- <b><ins>Dedup</b></ins>
  - Description: Removes duplicate events from the results. . 
  - For example: index=security | dedup src_ip dest_ip
  - Result: It removes duplicates events based on source and destination IP addresses.

# 6. Creating Dashboards
- Steps:
  - Navigate to Dashboards → Create a new dashboard.
  - Add visualizations for:
    - Logon attempts by user.
    - Geographical distribution of access.
  - Example Visualization:
    - Line Chart: Trends over time for failed logins.
    - Heatmap: IP addresses flagged for suspicious activity.


# Splunk SIEM Log Analysis Projects
- This repository contains a collection of projects for analyzing various types of logs using Splunk SIEM. Each project provides a structured guide for uploading sample log files, performing analysis, and gaining insights into specific types of log data.

## Projects: 
1. [Analyzing DNS Logs Using Splunk SIEM:](https://github.com/JohnPaulPamintuan/JohnPaulPamintuan/issues/6) 
- This project provides a step-by-step guide for analyzing DNS (Domain Name System) log files using Splunk SIEM. It covers uploading sample log files, extracting relevant fields, analyzing DNS query patterns, detecting anomalies, and monitoring DNS traffic. 

2. [Analyzing HTTP Logs Using Splunk SIEM](https://github.com/JohnPaulPamintuan/JohnPaulPamintuan/issues/7):
 - This project outlines the process of analyzing HTTP (Hypertext Transfer Protocol) log files using Splunk SIEM. It covers uploading sample log files, extracting relevant fields, analyzing HTTP request patterns, detecting anomalies, and monitoring HTTP traffic.
