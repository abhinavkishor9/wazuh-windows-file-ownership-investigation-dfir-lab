# Investigation Notes

## Lab Summary

This investigation focused on analyzing Windows file ownership modification using native Windows Security logs and Wazuh Discover.

The investigation reconstructed ownership changes by correlating Windows File Security, Event Viewer, PowerShell, and Wazuh while validating Security Event IDs 4670 and 4663.

---

## Analyst Methodology

1. Verify Wazuh agent connectivity.
2. Enable File System auditing.
3. Create a test file.
4. Modify file ownership.
5. Review Windows Security logs.
6. Validate events using Event Viewer.
7. Verify events using PowerShell.
8. Search Wazuh Discover.
9. Confirm event ingestion.
10. Correlate evidence.
11. Document findings.

---

## Investigation Scenario

Ownership of a Windows test file was modified.

The investigation aimed to determine:

- Which file ownership changed.
- Which account performed the modification.
- Whether Windows generated Security events.
- Whether Wazuh collected the activity.
- How the activity could be reconstructed.

---

## Evidence Collected

### Evidence 1 – Test File

Collected:

- File ownership modification

Finding:

Established investigation baseline.

---

### Evidence 2 – Event Viewer

Collected:

- Security Event IDs 4670 and 4663

Finding:

Confirmed successful ownership modification.

---

### Evidence 3 – PowerShell Validation

Command Used

```powershell
Get-WinEvent -FilterHashtable @{
    LogName='Security'
    Id=4670,4663,4656
} -MaxEvents 20
```

Finding:

Validated Event IDs 4670 and 4663. Event ID 4656 was not generated on the endpoint.

---

### Evidence 4 – Wazuh Discover

Collected:

- Security Event IDs 4670 and 4663

Finding:

Confirmed successful event collection.

---

## DFIR Analysis

The investigation demonstrated how Windows Security logs can reconstruct file ownership modifications without requiring Sysmon.

Although Event ID 4656 was not generated, Event IDs 4670 and 4663 provided sufficient evidence to validate the ownership change and confirm successful collection by Wazuh.

---

## MITRE ATT&CK Mapping

| Tactic | Technique | ID |
|---------|-----------|----|
| Defense Evasion | File and Directory Permissions Modification | T1222.001 |

---

## Analyst Observations

- Windows builds may generate different ownership-related Security events.
- Event Viewer remains the authoritative Windows source.
- PowerShell provides rapid validation.
- Wazuh successfully collected Windows Security events.
- Multiple evidence sources improve investigation confidence.

---

## Conclusion

The investigation demonstrated how Windows file ownership modifications can be reconstructed using native Windows Security logs and Wazuh Discover while emphasizing structured validation, evidence correlation, and centralized SIEM analysis.
