\# Phishing Detection using SIEM (Splunk)



\## Overview

&#x20;This project simulates a real-world phishing attack scenario and demonstrates how a Security Operations Center (SOC) analyst can detect, analyze, and respond to phishing threats using SIEM tools.

&#x20;The project involves collecting phishing URLs, validating them using threat intelligence, creating a dataset, and analyzing it in Splunk to detect malicious activity and user compromise.



\## Objectives

\-Detect phishing emails and malicious URLs

\-Identify targeted users and compromised activity

\-Analyze phishing infrastructure (domains)

\-Build alerts for real-time detection

\-Visualize threats using dashboards



\## Tools \& Technologies Used

\-Splunk (SIEM)

\-Kali Linux

\-PhishTank (Phishing URL source)

\-VirusTotal (Threat Intelligence)



\## Project Workflow

&#x20; ### Data Collection

&#x20; -Collected phishing URLs from PhishTank

&#x20; -Gathered \~25–30 malicious URLs



\### Data Collection (PhishTank)

&#x20; !\[PhishTank Screenshot](screenshots/phishtank.png)



\### Threat Intelligence Validation

&#x20; -Validated selected URLs using VirusTotal

&#x20; -Confirmed phishing/malicious indicators



\###  URL Validation (VirusTotal)

&#x20; -!\[VirusTotal Result 1](screenshots/vt1.png)

&#x20; -!\[VirusTotal Result 2](screenshots/vt2.png)

&#x20; -!\[VirusTotal Result 3](screenshots/vt3.png)



&#x20;### Dataset Creation

&#x20; Created custom log dataset (phishing\_logs.csv)

&#x20; Included:

&#x20; - Sender email

&#x20; - Recipient

&#x20; - URL

&#x20; - Action (clicked/delivered)

&#x20;Added normal traffic logs to simulate real-world environment

&#x20;Duplicated selected phishing logs to simulate attack patterns



&#x20;### 📸 Dataset Preview

&#x20;  !\[Dataset Screenshot](screenshots/dataset.png)



&#x20;### 4. Data Ingestion (Splunk)

&#x20; -Uploaded dataset into Splunk

&#x20; -Created custom index: phishing\_logs



\### 5. Detection \& Analysis



&#x20;Key Queries Used:

&#x20;  

&#x20;1. All Logs

&#x20;index=phishing\_logs

&#x20;

&#x20;3. Phishing Click Detection

&#x20;index=phishing\_logs action="clicked"



&#x20;4. Suspicious Senders

&#x20;index=phishing\_logs 

&#x20;| stats count by email\_sender 

&#x20;| sort -count



&#x20;5. Top Targeted Users

&#x20;index=phishing\_logs action="clicked" 

&#x20;| stats count by recipient 

&#x20;| sort -count



&#x20;6. Top Malicious Domains

&#x20;index=phishing\_logs 

&#x20;| stats count by url 

&#x20;| sort -count



&#x20;## 📸 Detection Queries



&#x20;### Phishing Click Detection

&#x20;!\[Clicked Logs](screenshots/clicked.png)



&#x20;### Suspicious Senders

&#x20;!\[Senders](screenshots/senders.png)



&#x20;### Top Targeted Users

&#x20;!\[Users](screenshots/users.png)



&#x20;### Top Malicious Domains

&#x20;!\[Domains](screenshots/domains.png)

&#x20; 

&#x20;## 6. Alert Creation



\-Created alert: “Phishing Link Click Detected”

\-Trigger condition: when users click phishing links

\-Logged events for monitoring and response



\## 📸 Alert Configuration

!\[Alert Screenshot](screenshots/alert.png)



\## 7. Dashboard Creation



Built a SIEM Dashboard with the following panels:



\- Total Phishing Link Clicks

\- Top Targeted Users

\- Top Malicious Domains

\- Email Activity Overview

\- Screenshots





\## Include screenshots of:



\- PhishTank data collection

\- VirusTotal validation

\- Splunk queries

\- Alert configuration

\- Final dashboard



\## Final Dashboard



&#x20;## 📊 Final Dashboard

!\[Dashboard](screenshots/dashboard.png)



\## Key Learnings

\-Understanding phishing attack patterns

\-Working with SIEM tools (Splunk)

\-Writing detection queries (SPL)

\-Creating alerts for security incidents

\-Building dashboards for threat monitoring



