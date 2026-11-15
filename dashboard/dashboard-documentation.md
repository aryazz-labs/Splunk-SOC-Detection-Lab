# SOC Security Monitoring Dashboard

**Dashboard title:** SOC Security Monitoring Dashboard  
**Description:** Centralized monitoring dashboard for Windows Security events, account activity, privilege changes and PowerShell execution.

## Panel inventory

### KPI panels
- Total Indexed Events
- Failed Logons
- Successful Logons
- New User Accounts
- Privileged Group Changes
- PowerShell Executions

### Trend and investigation panels
- Failed Logons Over Time
- Top Targeted User Accounts
- Recent Windows Security Events
- Account & Privilege Changes
- PowerShell Execution Activity

## Captured snapshot

The attached dashboard PDF shows the global time range set to **Last 24 hours**. Values visible in that snapshot:

| Panel | Snapshot value |
|---|---:|
| Total Indexed Events | 41,861 |
| Failed Logons | 27 |
| Successful Logons | 390 |
| New User Accounts | 2 |
| Privileged Group Changes | 5 |
| PowerShell Executions | 66 |

These numbers describe only the captured dashboard view. They will change as new events arrive and as the selected time range changes; they should not be presented as permanent totals or as detection accuracy metrics.

## Evidence

See [`screenshots/dashboard/11-soc-security-monitoring-dashboard.pdf`](../screenshots/dashboard/11-soc-security-monitoring-dashboard.pdf) for the full dashboard capture. It includes the KPI panels, failed-logon trend, top targeted accounts and recent event tables.
