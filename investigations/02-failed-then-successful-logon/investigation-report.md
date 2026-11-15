# Investigation: Failed Logons Followed by Successful Logon

## Summary
The correlation search returned two qualifying result groups for `SOC_TestUser` on `Windows-11-Pro`. Each group contained five failed logons and one successful logon within the same 10-minute bucket.

## Detection logic
The SPL searches Security Event IDs 4625 and 4624, extracts the account names, bins events into 10-minute intervals, and returns groups with at least five failures and at least one success.

## Evidence observed
| Bucket time shown in Splunk | Host | Account | Failed attempts | Successful logons |
|---|---|---|---:|---:|
| 2026-11-15 01:10 | Windows-11-Pro | SOC_TestUser | 5 | 1 |
| 2026-11-15 04:30 | Windows-11-Pro | SOC_TestUser | 5 | 1 |

The search returned 408 raw matching events before aggregation in the displayed all-time search. The final statistics table contained the two qualifying groups above.

## Assessment
The detection identifies failure/success co-occurrence for the same account and 10-minute bucket. It does not establish that the successful logon occurred after the failures, that the failures caused the success, or that the account was compromised. Event-level timestamps and logon context must be reviewed to establish sequence.

## Follow-up checks
1. Open the underlying 4624 and 4625 records for both buckets and compare exact timestamps.
2. Review source address, logon type, workstation and authentication package.
3. Determine whether the successful logon was expected and authorized.
4. Correlate with endpoint process activity and account changes around the same time.

## MITRE ATT&CK context
**Potential mapping:** T1110 – Brute Force for repeated failures. A successful authentication may warrant checking for valid-account misuse, but this evidence alone does not justify concluding T1078 activity or account compromise.

## Disposition
**Lab correlation validated; sequence and legitimacy require raw-event review.**

## Evidence file
`../../screenshots/detections/06-failed-then-successful-logon.png`
