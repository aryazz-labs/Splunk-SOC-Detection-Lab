# Curated Evidence Index

This folder contains only the screenshots selected from the user's reviewed evidence. The earlier rejected screenshot collection has not been carried into this package. Images are retained as supplied; filenames are descriptive for repository navigation.

| File | What it demonstrates |
|---|---|
| `environment/01-sysmon-service-running.png` | PowerShell output showing the Sysmon service running. |
| `ingestion/02-windows-security-eventcode-summary.png` | Security event ingestion with EventCode counts in `windows_security`. |
| `ingestion/03-expanded-failed-logon-event-4625.png` | Expanded Windows Security 4625 event and failure details. |
| `ingestion/04-sysmon-event-ingestion.png` | Sysmon Operational search returning Event ID 1 process-creation events. |
| `detections/05-multiple-failed-logons.png` | SPL and three qualifying result groups (5, 5 and 8 failed attempts). |
| `detections/06-failed-then-successful-logon.png` | SPL and two qualifying groups with 5 failures and 1 success each in the same 10-minute bucket. |
| `detections/07-new-user-account-created.png` | SPL and two Event ID 4720 results; visible account `SOC_LabCreated`, actor `beezl`. |
| `detections/08-privileged-group-membership-change.png` | SPL and five group-change results; visible Event ID 4732 for built-in Administrators. |
| `detections/09-powershell-process-execution.png` | SPL and 117 Sysmon PowerShell process-creation results. |
| `alerts/10-multiple-failed-logon-schedule.png` | Scheduled alert, five-minute cron and 10-minute search range. Other alert settings are not visible. |
| `dashboard/11-soc-security-monitoring-dashboard.pdf` | Full dashboard snapshot with KPI, trend and event-detail panels. |

## Evidence not included

No screenshot was supplied for the Splunk home page, Universal Forwarder `outputs.conf`, a consolidated enabled-alert listing, a triggered-alert record or dashboard editor. These are not represented as captured evidence in this package.
