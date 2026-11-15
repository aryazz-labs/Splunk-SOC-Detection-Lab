# Scheduled Alert Configuration

## Evidence available

The screenshot [`screenshots/alerts/10-multiple-failed-logon-schedule.png`](../screenshots/alerts/10-multiple-failed-logon-schedule.png) documents the edit view for **SOC - Multiple Failed Logon**.

The visible configuration is:

| Setting | Observed value |
|---|---|
| Alert type | Scheduled |
| Cron expression | `*/5 * * * *` — every five minutes |
| Search time range | Last 10 minutes |
| Alert description | Detects 5 or more failed logon attempts against an account within a 10-minute window (the screenshot text is partially clipped) |

This is the extent of what the supplied configuration screenshot establishes. It does **not** show the trigger condition, trigger actions, severity, throttling, expiration or sharing settings. Those values are not documented here.

## Named detection alerts

The lab contains saved SOC detection searches with these names:

- `SOC - Multiple Failed Logon`
- `SOC - Failed Logons Followed by Successful Logon`
- `SOC - New User Account Created`
- `SOC - Privileged Group Membership Change`
- `SOC - PowerShell Process Execution`

The detection search names and SPL are included in the detection evidence. This document does not claim that all five alert schedules or their trigger actions were independently captured in the supplied screenshot set.

## Time-window consideration

The failed-logon detections aggregate events into 10-minute buckets. The screenshot for the Multiple Failed Logon alert shows a 10-minute search range and a five-minute schedule. The overlapping lookback is suitable for evaluating the configured 10-minute bucket at five-minute intervals, subject to Splunk's search-time and scheduling behaviour.

## Evidence limitation

An alert's saved name or schedule does not, by itself, prove that it triggered or generated a notification. A triggered-alert record or action log would be needed to make that claim. No unshown trigger action, severity or throttle setting is assumed in this repository.
