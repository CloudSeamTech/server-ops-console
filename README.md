# Server Ops Console

A planned browser-based console for managing Windows and Linux servers from an authorized workstation on the management network.

## Interface

Use a violet-to-slate gradient and translucent server cards. On the left, show Discover Servers, Windows and Linux pools, Active Directory, and quick actions for the selected server. The center-right pane contains Activity and interactive SSH tabs, with the target identity pinned above the output. The bottom action bar includes Check Updates, Install Updates, SCAP Scan, Vulnerability Scan, Export Scan Results, and Reboot.

## Operator workflows

- **Discovery and inventory.** Scan authorized subnets. Keep candidates separate from enrolled servers. Verify the server identity, classify it by authenticated OS information, and display the last authenticated heartbeat.
- **Updates.** Preview and install updates on selected Windows servers using their configured update source or on supported Linux servers using dnf. Record per-server results and reboot requirements.
- **Reboot.** Pick one enrolled server with a fresh heartbeat. Show its exact hostname and IP, require confirmation, and recheck identity and heartbeat at execution. Verify that the server returns with a new boot time.
- **Scans and exports.** Run a selected OpenSCAP profile without remediation or submit a vulnerability scan to an approved scanner. Show completion and credentialed coverage. Download the selected server's latest completed reports individually or as a ZIP. Show dates and distinguish older reports from newer failed or running jobs.
- **Quick diagnostics.** Provide health snapshots, recent errors, service status, disk usage, DNS and service-port checks, and TLS expiration. Confirm service restarts and verify service recovery.
- **Active Directory.** Diagnose account lockouts and password status. Delegate unlock rights to the appropriate role and confirm the exact account before acting.
- **Terminal and SSH.** Stream redacted output from every action into Activity, tagged with the target and job. Offer approved commands with autocomplete. Open interactive SSH in a separate tab with its own permission, strict host-key verification, and an operator-selected identity through a local SSH agent connector.

## Security and first milestone

Enforce role and target authorization in the management service. Use constrained Windows remoting and narrowly scoped Linux commands for quick actions. Keep credentials out of logs and source control. Audit changes, report exports, and SSH session lifecycle events.

Start in the lab with discovery, verified enrollment, authenticated heartbeats, and a dry-run reboot picker. Test stale heartbeats, wrong targets, unauthorized access, and interrupted jobs before enabling live operations.

This repository starts with the specification. The application and integrations are planned.
