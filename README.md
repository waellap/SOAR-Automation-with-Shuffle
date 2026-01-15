# SOAR-Automation-with-Shuffle



##  Objective
Automate SOAR using  Shuffle, Wazuh, and TheHive.

The objective of this SOAR project is to design and implement an automated Security Operations Center workflow that detects security events, enriches alerts with threat intelligence, and streamlines incident handling using Wazuh, Shuffle, and TheHive. It aims to reduce manual analyst effort and improve response time by automating alert escalation, case creation, analyst notification, and response actions using these integrated tools.

### Skills Learned
Monitor security events, automate incident response, and use SIEM and SOAR tools to handle alerts more efficiently.

- SOC Automation & SOAR Fundamentals – Understanding how automated security workflows operate end to end.

- SIEM Configuration & Log Analysis – Using Wazuh to collect, analyze, and correlate endpoint security events.

- Incident Response & Case Management – Managing alerts and investigations using TheHive.

- Workflow Orchestration – Designing and implementing automated playbooks in Shuffle.

- Threat Intelligence Enrichment – Enriching alerts with external IOC sources (e.g., IPs, hashes).

- API & Webhook Integration – Connecting multiple security tools through REST APIs and webhooks.

- Alert Triage & Analysis – Evaluating alerts, prioritizing incidents, and making response decisions.

- Basic Endpoint Security & Detection Engineering – Understanding how endpoint events trigger detections and responses.

- Networking & System Integration – Troubleshooting communication between distributed security components.

- Real-World SOC Operations – Gaining practical experience with detection, escalation, and response workflows used in modern SOC environments.

### Tools Used
Wazuh, Shuffle, TheHive, Internet Threat Intelligence APIs, and Email Notification/Webhooks.

- SIEM & endpoint agent: collects logs, detects threats, and generates alerts.
- SOAR: orchestrates workflows, triggers actions, enriches alerts, and sends to IR.
- Incident Response / Case Management: stores incidents/cases for analysis.
- (e.g., VirusTotal) used by Shuffle to enrich IOCs.
- Used by Shuffle to notify analysts or external systems.



## The Diagram Demonstration.

1 - Windows 10 sends events to - Wazuh manager triggers alerts and performs actions, then 3- Shuffle receives Wazuh alerts & send responsive action. 4- ONSIT enriches IOCs 5- TheHive creates alerts in case management 6- Email sends emails and responsive actions.

<img src="https://imgur.com/qmgVlWV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />




##  Lab Photo Demonstration.

### Steps
1- Installation
- Installing Windows 10, which will be the agent, then downloading  and configuring Sysmon and Wazuh agent within it.
<img src="https://imgur.com/e2S5h3h.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://imgur.com/CIJr26w.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://imgur.com/M1nxNL0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />


-I installed TheHive and Wazuh server in my Ubuntu virtual machine. The Hive has four prerequisite components (Java, Cassandra, Elastic Search, and TheHive).

<img src="https://imgur.com/yoQFIFx.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://imgur.com/h1sSLRT.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<br />
<br />


-Creating the HTTP.Server.

<img src="https://imgur.com/8LWykK9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />


-Turning down the malware detector in Windows Defender.


<img src="https://imgur.com/zxRYS7f.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />


-Connecting to the server and choosing the exe file, aka (malware folder).


<img src="https://imgur.com/loAu4PC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />


-Download the exe file (Resume.pdf.exe) and run it


<img src="https://imgur.com/bcXDOsy.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />


-After running the malware folder, checking it through the cmd by running Netstat -anob. Then The 
connection is established

<img src="https://imgur.com/L6SZByZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />



-Ingesting the sysmon and creating an index called endpoint 
-Setting->index->new index-> endpoint->Apps->Search and reporting->index endpoint.


<img src="https://imgur.com/Fp16zSS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />



-Searching for the malware name (Resume.pdf.exe), I found 13 events.

<img src="https://imgur.com/yd4OxpT.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />


-I use process guid in the search menu and found 5 events. I clean up the query and looked into the statistics.


<img src="https://imgur.com/G9rWjyY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
