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
- Installation
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

- Workflow
- Send the Mimikatz alert to shuffle.
- Shuffle receives the alerts and extract SHA256 hash from the file,
- checks the reputation score via VirusTotal,
- and lastly send an email to the analyst to investigate.  

-Creating My Workflow.
I open shuffle.io, I click on triggers, and I add a webhook.



<img src="https://imgur.com/hQKtvH4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://imgur.com/Jwz8nw8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<br />
<br />


-Then, within the Wazuh manager, I connected it to shuffle under nano/var/ossec/etc/ossec.conf and added the rule Id.


<img src="https://imgur.com/hnMd5Pt.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />


-After connecting it, I restart Wazuh and generate the Mimikatz telemetry.


<img src="https://imgur.com/ES0EEWP.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />


-Here are some events.


<img src="https://imgur.com/q3pjAAv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://imgur.com/B1vHkUw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />


-I opened ChatGPT, created Regex and pasted it.

<img src="https://imgur.com/IPDCpVe.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://imgur.com/ij8NcFd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://imgur.com/fztgPd8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />



-I created an account in VirusTotal and added it to my shuffle scan SHA256 hash.


<img src="https://imgur.com/sfHRq8X.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://imgur.com/6PzBejU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />



-Then connect TheHive to get the alert. I created a new organization and users for that organization to authenticate with Shuffle, 
and the alert will generate in TheHive. Also, I modified my cloud firewall.

<img src="https://imgur.com/BsTOhja.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://imgur.com/HPCIW08.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<img src="https://imgur.com/5GPTKrB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<br />
<br />


-I add the email in which the alert will be sent.


<img src="https://imgur.com/H6dflNh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://imgur.com/F0bH26U.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<br />
<br />

-Lastly, I added the mitigation technique from MITRE ATT&CK. The alert number is "T1003.".


<img src="https://imgur.com/8rhFOou.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

