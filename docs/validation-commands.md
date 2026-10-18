# Reproducible validation commands

These are illustrative commands from the controlled lab. Run only on systems you own or are authorized to test. Paths may need to be adjusted.

## Windows PowerShell

```powershell
# Confirm active Sysmon configuration
C:\Tools\Sysmon\Sysmon64.exe -c

# Confirm relevant Sysmon events exist
Get-WinEvent -FilterHashtable @{
    LogName = 'Microsoft-Windows-Sysmon/Operational'
    Id = 3,11
} -MaxEvents 30 | Select-Object TimeCreated, Id, Message

# Check Wazuh agent service
Get-Service WazuhSvc

# Verify Wazuh agent is configured to read Sysmon
Select-String -Path 'C:\Program Files (x86)\ossec-agent\ossec.conf' -Pattern 'Microsoft-Windows-Sysmon/Operational' -Context 2,2
```

## Ubuntu / Docker

```bash
# Confirm Wazuh container health
cd ~/cyber-lab/wazuh-docker/single-node
docker compose ps

# Check registered agents
docker exec single-node-wazuh.manager-1 /var/ossec/bin/agent_control -l

# Check manager services
docker exec single-node-wazuh.manager-1 /var/ossec/bin/wazuh-control status

# Test local rule syntax (use exit code as confirmation)
docker exec single-node-wazuh.manager-1 /var/ossec/bin/wazuh-analysisd -t

# Look for a case marker in alert output; no match does NOT prove non-ingestion
docker exec single-node-wazuh.manager-1 sh -c \
  'grep -F "download-live-03.txt" /var/ossec/logs/alerts/alerts.json'
```

Never commit Wazuh secrets, Docker environment files with passwords, certificates, or full raw logs that may contain personal details.
