# Known Limitations and Interpretation Notes

1. Sysmon Event ID 255 recorded driver queue overflow and dropped events after the driver queue reached its configured limit. Telemetry completeness was affected during that period.
2. The EC2 host uses UTC while Windows uses India Standard Time (UTC+05:30). Preserve timezone context when correlating events. The detection result screenshots show Splunk-rendered bucket times; consult raw event timestamps for exact sequencing.
3. The failed-then-successful logon rule aggregates events into 10-minute buckets. It detects co-occurrence for the same account and host in a bucket; it does not prove that the successful logon followed the failures.
4. The group membership detection covers additions to security-enabled global, local and universal groups. Inspect the group in each event before classifying it as privileged. The captured Administrators event does not resolve the member SID to an account name.
5. PowerShell execution is a behavioural signal, not proof of malicious activity. Review command line and surrounding process, user, file and network context.
6. The confirmed Splunk implementation is centered on one Windows 11 Pro endpoint. Active Directory Server, Kali Linux and Atomic Red Team are shown as planned extensions, not as verified deployed components.
7. The alert configuration evidence shows only the Multiple Failed Logon alert's scheduled type, five-minute cron and 10-minute search range. Trigger actions, severity, throttling and expiration are not visible and are not asserted.
8. Dashboard metrics are a Last 24 hours snapshot and will change with incoming events and time-range selection.
