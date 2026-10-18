# Interview brief

## Tell me about the lab
I designed a Windows endpoint monitoring lab with Sysmon and Wazuh running through an Ubuntu WSL2 and Docker environment. I investigated controlled PowerShell activity, correlated endpoint process, network and file events, and documented what the telemetry proved and what it did not.

## What was the hardest problem?
Network and file events were initially missing even though Sysmon was installed. I checked the active configuration rather than assuming the network operation failed, enabled the relevant Event ID 3 and 11 monitoring, repeated the test and confirmed the events locally. In Wazuh, I then separated the absence of an alert from proof of missing ingestion, because complete event archiving was disabled.

## What would you improve?
I would establish verifiable collection-to-alert testing with real event samples, use scoped archiving during validation, and only mark a custom rule operational after a positive match. I would also capture redacted screenshots as part of each case rather than afterward.

## How do you decide if PowerShell is malicious?
I assess parent process, command line, user, integrity, destination, related file activity and business/authorization context. PowerShell execution and ATT&CK mapping alone do not establish malicious intent.
