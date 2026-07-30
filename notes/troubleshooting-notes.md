# Troubleshooting Notes

## Issue 1 — Event ID 4656 Not Generated

### Cause

The Windows build or audit configuration did not generate Event ID 4656 during the ownership modification.

### Resolution

Continue the investigation using Event IDs 4670 and 4663, which provided sufficient forensic evidence.

---

## Issue 2 — Ownership Change Events Not Generated

### Cause

File System auditing was not enabled or auditing was not configured on the test file.

### Resolution

Enable **Audit File System** and configure auditing on the file before repeating the ownership change.

---

## Issue 3 — No Results in Wazuh Discover

### Cause

Incorrect Event ID search, insufficient time range, or indexing delay.

### Resolution

Validate the events in Event Viewer first, then search:

```text
data.win.system.eventID:4670
```

and

```text
data.win.system.eventID:4663
```

using a wider time range.

---

## Issue 4 — PowerShell Returned No Results

### Cause

The Security log did not yet contain the generated events or the query searched too few records.

### Resolution

Increase `-MaxEvents` or query the Event IDs individually using `FilterHashtable`.

---

## Issue 5 — Verify Wazuh Agent Health

### Cause

If events do not appear in Discover, the Wazuh agent may not be communicating correctly.

### Resolution

Verify agent status:

```bash
sudo /var/ossec/bin/agent_control -i 001
```

---

## Issue 6 — Confirm Event Ingestion

### Cause

Windows generated the events, but Discover did not display them immediately.

### Resolution

Verify ingestion using:

```bash
grep '"eventID":"4670"' /var/ossec/logs/archives/archives.json
```

Repeat for Event ID **4663** if necessary.

---

# Lessons Learned

- Windows builds may generate different ownership-related Security events.
- Event IDs 4670 and 4663 were sufficient to reconstruct the investigation.
- Event Viewer should always validate Windows event generation before investigating Wazuh.
- Confirm event ingestion before assuming a Discover issue.
- Correlating Windows Security logs with Wazuh Discover provides a reliable workflow for investigating file ownership modifications.
