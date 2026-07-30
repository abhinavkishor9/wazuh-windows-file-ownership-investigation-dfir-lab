# Investigation Timeline

| Time | Activity | Evidence |
|------|----------|----------|
| 09:00 | Verified Wazuh agent connectivity | agent_control |
| 09:05 | Enabled File System auditing | Local Security Policy |
| 09:10 | Created test file | Windows File System |
| 09:15 | Modified file ownership | File Properties |
| 09:20 | Reviewed Security Event IDs 4670 and 4663 | Event Viewer |
| 09:25 | Validated events using PowerShell | Get-WinEvent |
| 09:30 | Confirmed Wazuh agent status | agent_control |
| 09:35 | Verified event ingestion | archives.json |
| 09:40 | Investigated Wazuh Discover | Discover |
| 09:45 | Correlated findings | Documentation |

---

# Investigation Flow

Investigation Started

↓

Verified Agent Health

↓

Enabled File System Auditing

↓

Created Test File

↓

Modified File Ownership

↓

Reviewed Event Viewer

↓

Validated Using PowerShell

↓

Confirmed Event Ingestion

↓

Investigated Wazuh Discover

↓

Correlated Evidence

↓

Investigation Completed

---

# Summary

The investigation reconstructed Windows file ownership modification using native Windows Security logs and Wazuh Discover. The lab demonstrated successful generation and validation of Security Event IDs **4670** and **4663**, while documenting that **Event ID 4656 was not generated** on the test system. The investigation emphasized validating Windows logging, confirming Wazuh event collection, and correlating multiple evidence sources to produce a structured DFIR investigation.````
