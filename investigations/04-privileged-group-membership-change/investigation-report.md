# Investigation: Privileged Group Membership Change

## Summary
The group-membership search returned five events. The displayed Event ID 4732 shows a member added to the built-in local `Administrators` group on `Windows-11-Pro` by actor `beezl`.

## Detection logic
The SPL searches Event IDs 4728, 4732 and 4756, covering additions to security-enabled global, local and universal groups. Analysts must inspect the group in each event to determine whether it is privileged.

## Evidence observed
| Field | Observed value |
|---|---|
| Matching events | 5 |
| Displayed event ID | 4732 |
| Host | Windows-11-Pro |
| Actor | beezl |
| Group | Administrators |
| Group domain | Builtin |
| Member account name | `-` (not resolved in the screenshot) |
| Member SID | `S-1-5-21-3727197404-726637916-3819908285-1003` |

The event message explicitly identifies the built-in Administrators group. The member is represented by a SID; the screenshot does not provide a resolved account name.

## Assessment
The displayed event is a local Administrators group membership addition and is security-relevant because membership can grant elevated local privileges. The evidence identifies the actor and group, but it does not establish whether the action was authorized or whether the member account was used afterwards.

## Follow-up checks
1. Resolve the member SID on the endpoint and confirm the account owner.
2. Verify whether `beezl` was authorized to modify local Administrators membership.
3. Review nearby account-creation and logon events.
4. If unauthorized, follow the organization's privilege-removal and incident-response procedures.

## MITRE ATT&CK context
**Potential mapping:** T1098 – Account Manipulation. This is a behavioural mapping for group membership modification.

## Disposition
**Local Administrators membership change observed; authorization and member identity require validation.**

## Evidence file
`../../screenshots/detections/08-privileged-group-membership-change.png`
