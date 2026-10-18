# Engineering findings and troubleshooting

| Symptom | Investigation | Action | Result |
|---|---|---|---|
| No Sysmon Event ID 3 | Sysmon config showed network monitoring disabled | Enabled a scoped `NetworkConnect` rule for port 8080 | Event ID 3 confirmed locally |
| No Sysmon Event ID 11 | No FileCreate filter for controlled directory | Added scoped `FileCreate` rule | Event ID 11 confirmed locally |
| No Case 003 Wazuh alert | Inspected agent status, manager, stock rules and alert storage | Added experimental rule 100100, restarted manager, reproduced event | No matching alert confirmed; root cause unresolved |
| Historical record absent in alerts | Wazuh archives empty; `logall=no`, `logall_json=no` | Avoided treating alert output as full event storage | Identified visibility limit; did not assert event never arrived |

## Lessons

1. Telemetry must be enabled and tested; installation alone is insufficient.
2. Use ProcessGuid rather than PID alone when reconstructing related events.
3. Normalize timestamps and account for local time versus UTC.
4. Logging, detection, alert generation and index visibility are distinct stages.
5. A missing alert is a hypothesis to investigate, not proof that an event did not occur.
6. The correct response to benign behavior is contextual assessment, not automatic containment.

## Validation boundary
This report does not certify a production detection pipeline. The lab successfully generated the relevant Sysmon telemetry; the custom Wazuh Case 003 alert remains unverified.
