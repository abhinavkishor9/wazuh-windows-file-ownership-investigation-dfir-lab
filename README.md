# wazuh-windows-file-ownership-investigation-dfir-lab
## Overview

This Digital Forensics and Incident Response (DFIR) lab demonstrates how Windows file ownership changes can be investigated using native Windows Security logs and Wazuh.

Unlike Sysmon-based investigations, this lab relies entirely on Windows Security Event Logs, Event Viewer, PowerShell, Windows File Security, and Wazuh Discover to reconstruct file ownership modification activity.

The investigation also demonstrates how Windows records object permission changes and object access events while highlighting that different Windows builds may generate different Security Event IDs during ownership modification.

---

# Executive Summary

This investigation focused on analyzing Windows file ownership modification using native Windows Security logging and Wazuh.

The investigation included:

- Creating a test file
- Enabling File System auditing
- Modifying file ownership
- Investigating Security Event IDs 4670 and 4663
- Validating events using Event Viewer
- Verifying events using PowerShell
- Searching events in Wazuh Discover
- Confirming successful event ingestion
- Correlating Windows and Wazuh evidence

The investigation emphasizes structured DFIR methodology by validating endpoint evidence before relying solely on SIEM results.

---

# Learning Objectives

- Understand Windows file ownership and object permissions.
- Investigate Windows object permission changes.
- Validate Security events using Event Viewer.
- Verify events using PowerShell.
- Investigate ownership changes using Wazuh Discover.
- Confirm successful log ingestion.
- Reconstruct a file ownership modification timeline.

---

# Skills Demonstrated

- Windows DFIR Investigation
- Windows Security Log Analysis
- File Ownership Investigation
- Object Permission Analysis
- Event Viewer Analysis
- PowerShell Event Validation
- Wazuh Discover Investigation
- Windows Event Correlation
- Timeline Reconstruction
- Digital Evidence Documentation
- DFIR Troubleshooting
- MITRE ATT&CK Mapping

---

# Tools Used

- Wazuh Dashboard (Discover)
- Windows Event Viewer
- Windows PowerShell
- Windows File Security
- Windows Security Event Log
- Wazuh Agent

---

# Lab Environment

| Component | Details |
|-----------|---------|
| SIEM | Wazuh 4.12 |
| Endpoint | Windows 11 Pro |
| Server | Oracle Linux 9 |
| Investigation Type | Windows DFIR |
| Event Source | Windows Security Log |
| Sysmon | Not Used |

---

# Investigation Scenario

Ownership of a Windows test file was modified.

As the DFIR analyst, the objectives were to determine:

- Which file ownership changed
- Which account performed the modification
- Whether Windows generated Security events
- Whether Wazuh collected the activity
- How the ownership change could be reconstructed

---

# Investigation Workflow

1. Verify Wazuh agent connectivity.
2. Enable File System auditing.
3. Create a test file.
4. Modify file ownership.
5. Review Windows Security logs.
6. Validate events using Event Viewer.
7. Verify events using PowerShell.
8. Investigate activity using Wazuh Discover.
9. Confirm event ingestion.
10. Correlate investigative findings.

---

# MITRE ATT&CK Mapping

| Tactic | Technique | ID |
|---------|-----------|----|
| Defense Evasion | File and Directory Permissions Modification | T1222.001 |

### Why File Ownership Investigations Matter

Attackers frequently modify file ownership or permissions to gain unauthorized access, maintain persistence, or interfere with forensic investigations. Monitoring ownership-related Security events enables analysts to detect suspicious permission modifications and validate administrative actions.

---

# Evidence Collected

- Test File
- Windows Security Event Log
- Event Viewer
- PowerShell Validation
- Wazuh Discover
- archives.json (ingestion verification)

---

# Evidence Correlation

| Evidence Source | Information Obtained | Investigation Value |
|-----------------|---------------------|--------------------|
| Test File | Ownership modification | Investigation baseline |
| Event Viewer | Security Events 4670 & 4663 | Primary evidence |
| PowerShell | Event validation | Independent verification |
| Wazuh Discover | Collected events | SIEM validation |

---

# Investigation Findings

- File System auditing was enabled successfully.
- File ownership was modified.
- Windows generated Security Event IDs 4670 and 4663.
- Event ID 4656 was not generated on the test system.
- Event generation was validated using Event Viewer and PowerShell.
- Wazuh successfully collected the ownership modification events.
- The investigation successfully reconstructed the ownership change timeline.

---

# Key Takeaways

- Windows builds may generate different Security events during ownership changes.
- Event IDs 4670 and 4663 provided sufficient forensic evidence.
- Event Viewer and PowerShell should always validate Windows event generation.
- Wazuh Discover centralizes ownership-related investigations.
- Correlating multiple evidence sources improves DFIR accuracy.

---
