I recently completed a practical phase of my Cybersecurity SIEM & Endpoint Detection Home Lab using Wazuh, Sysmon, Windows 11, Ubuntu/WSL2, Docker and PowerShell.

My goal was to move beyond setting up tools and practise the thinking required in a real SOC investigation.

I worked through controlled PowerShell execution, local network activity and file creation, then investigated the evidence using Sysmon events, process IDs, ProcessGuid correlation and Wazuh rules. One of my biggest lessons came from troubleshooting: Sysmon was installed, but network and file creation events weren't initially enabled in its configuration. After correcting that, I was able to reproduce and correlate the endpoint activity.

I also discovered an important limitation. Even though the endpoint events were present, my experimental custom Wazuh rule did not produce a confirmed alert. I documented that gap rather than calling the detection successful without evidence.

My biggest takeaway: seeing an event, collecting it and generating a useful security alert are different things. A good analyst needs to know the difference and investigate with context, not assumptions.

I've documented the architecture, the investigation cases, the troubleshooting and the lessons learned on GitHub.

GitHub: [ADD YOUR REPOSITORY LINK AFTER PUBLISHING]

#CyberSecurity #SOCAnalyst #Wazuh #Sysmon #ThreatDetection #BlueTeam #SecurityEngineering #HomeLab
