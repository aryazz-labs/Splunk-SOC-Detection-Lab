# Investigation: New User Account Created

## Summary
The Event ID 4720 search returned two matching events. The displayed event records creation of the local account `SOC_LabCreated` on `Windows-11-Pro` by actor `beezl`.

## Detection logic
The SPL searches Windows Security Event ID 4720 and extracts the new account name and the subject account that performed the action.

## Evidence observed
| Field | Observed value |
|---|---|
| Event ID | 4720 |
| Host | Windows-11-Pro |
| Actor | beezl |
| Created account | SOC_LabCreated |
| Event message | A user account was created. |
| Search results | 2 events |

The event details show the subject account `beezl` and the new account `SOC_LabCreated`. The screenshot does not establish whether this account was subsequently used or assigned privileges.

## Assessment
The account-creation detection worked and surfaced the lab-created account. This is expected lab activity based on the account name and test context. The event alone does not establish unauthorized persistence or malicious intent.

## Follow-up checks
1. Confirm the account creation was authorized and identify its intended purpose.
2. Review group memberships and account properties.
3. Search for subsequent 4624 logons and other activity by `SOC_LabCreated`.
4. If unexpected, disable the account according to the incident-response process after validating business impact.

## MITRE ATT&CK context
**Potential mapping:** T1136.001 – Create Account: Local Account. The mapping describes the observed account-creation behaviour; it does not imply malicious use.

## Disposition
**Lab account creation observed; no confirmed compromise.**

## Evidence file
`../../screenshots/detections/07-new-user-account-created.png`
