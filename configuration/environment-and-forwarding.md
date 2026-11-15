# Environment and Forwarding Notes

## Splunk server
- Ubuntu 24.04 EC2 instance.
- Splunk Enterprise 10.6.1.1 installed under `/opt/splunk`.
- Receiving port: TCP 9997.
- Splunk Web: TCP 8000, accessed through SSH local forwarding.
- Do not expose ports 8000, 8089, or 9997 publicly.

## Windows endpoint
- Windows 11 Pro VM.
- Splunk Universal Forwarder installed under `C:\Program Files\SplunkUniversalForwarder\`.
- Forwarding destination: `192.168.56.1:9997`.
- Sysmon 15.22 installed and running.
- Existing Sysmon configuration preserved to avoid disrupting the separate Wazuh lab.

## Index and sourcetypes
- Index: `windows_security`
- Security: `WinEventLog:Security`
- Sysmon: `XmlWinEventLog:Microsoft-Windows-Sysmon/Operational`

## Time
The EC2 host is configured for UTC. Windows is configured for India Standard Time (UTC+05:30). Do not alter timestamps manually when correlating events; use timezone-aware event times.
