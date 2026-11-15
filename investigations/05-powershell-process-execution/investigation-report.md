# Investigation: PowerShell Process Execution

## Summary
The Sysmon Event ID 1 search returned 117 matching PowerShell process-creation events in the displayed all-time search. The results expose process image paths and command lines for analyst review.

## Detection logic
The SPL searches the Sysmon Operational sourcetype, filters for Event ID 1, extracts `Image` and `CommandLine`, and retains events whose process image contains `powershell.exe`.

## Evidence observed
| Field | Observed value |
|---|---|
| Event source | Sysmon Operational |
| Event ID | 1 – Process Create |
| Host | Windows-11-Pro |
| Matching results | 117 |
| Visible process | `powershell.exe` |
| Visible command-line examples | PowerShell account enumeration and `secedit` configuration inspection commands |

The screenshot shows multiple command lines, including a query of local user accounts and commands exporting and reading local security policy settings. These commands can occur during legitimate administration and are not, by themselves, proof of malicious execution.

## Assessment
The search demonstrates endpoint process visibility and provides command-line context for triage. A count of 117 matching events is not a count of malicious events. The available screenshot does not establish parent process, user context, integrity level or the intent behind every command.

## Follow-up checks
1. Review the full command line, parent process, user, integrity level and process hash for each relevant event.
2. Correlate with nearby file, registry, network and authentication activity.
3. Determine whether the commands align with expected administration or lab activity.
4. Escalate only when additional context supports suspicious or unauthorized behaviour.

## MITRE ATT&CK context
**Potential mapping:** T1059.001 – Command and Scripting Interpreter: PowerShell. The mapping describes the execution mechanism, not malicious intent.

## Disposition
**PowerShell process telemetry validated; individual events require contextual triage.**

## Evidence file
`../../screenshots/detections/09-powershell-process-execution.png`
