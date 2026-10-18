I'm pleased to share a cybersecurity project I've been working on: **Cybersecurity SIEM & Endpoint Detection Engineering Home Lab**.

I wanted to go beyond learning security tools and experience what it takes to investigate events, validate detections and troubleshoot monitoring gaps in a practical SOC environment.

I built a monitoring lab using Wazuh, Sysmon, Windows 11, Ubuntu, Docker and PowerShell.

One of my investigations involved generating a controlled PowerShell execution event, analysing Sysmon Event ID 1 and tracing the corresponding alert in Wazuh. I confirmed rule 92027 and mapped the activity to MITRE ATT&CK T1059.001.

In another investigation, I simulated an authorised local HTTP download and correlated Sysmon network connection and file creation events using ProcessGuid.

The biggest lesson came from troubleshooting.

I discovered that having security tools installed does not guarantee complete visibility. I had to investigate missing Sysmon telemetry, update monitoring configurations and validate the results. I also documented a custom Wazuh detection that did not generate a confirmed alert.

That experience reminded me of something important:

**A security alert tells us what was detected. A proper investigation helps us understand what happened, why it happened and whether it represents a threat.**

I've documented the architecture, commands, investigations, screenshots, troubleshooting and lessons learned on GitHub.

🔗 **Project:** https://github.com/AyoPro05/cybersecurity-siem-endpoint-lab

I'm continuing to strengthen my practical skills in SOC operations, threat detection, incident investigation and security engineering.

#Cybersecurity #SOCAnalyst #SecurityEngineering #Wazuh #Sysmon #BlueTeam #IncidentResponse #DetectionEngineering #MITREATTACK
