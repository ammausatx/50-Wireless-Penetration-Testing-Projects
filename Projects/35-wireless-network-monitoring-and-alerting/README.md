# Project 35 — Wireless Network Monitoring and Alerting

**Level:** Intermediate | **Estimated time:** 3–4 hours

> **Defensive, authorized lab only.** This project uses owned AP/controller configuration, synthetic event records, and authorized test clients. It does not include rogue AP deployment, SSID impersonation, credential harvesting, deauthentication, or disruptive frame injection.

## Objective

Build a monitoring baseline for WLAN health, authentication, configuration drift, and security events with actionable alert thresholds.

## Scope and prerequisites

- Owned AP/controller and isolated lab SSID.
- Synthetic clients, controller logs, and vendor-provided simulator/historical sanitized events.
- **Tools:** Wireless controller, SNMPv3/API, syslog, SIEM, dashboard.
- Record authorization, SSID/BSSID scope, AP/controller firmware, sensor coverage, test window, and stop conditions.
- Do not transmit disruptive frames or interact with third-party networks/users.

## Step 1 — Establish the defensive baseline

Export AP/controller configuration, approved device inventory, alert rules, and relevant log sources. Confirm time synchronization and management-plane access controls.

```bash
ip -br link
 iw dev
nmcli -f DEVICE,TYPE,STATE,CONNECTION device status
```

## Step 2 — Defensive assessment workflow

1. Define critical metrics: AP availability, client association failures, authentication errors, firmware drift, rogue AP alerts, and PMF coverage.
2. Configure secure log forwarding and time synchronization for the lab controller/APs.
3. Create dashboard panels and alert rules using synthetic test events.
4. Validate alert severity, routing, deduplication, acknowledgement, and escalation.
5. Document retention, access control, privacy minimization, and periodic review.

Read-only review example:

```bash
Review controller syslog destinations and confirm TLS/SNMPv3 monitoring settings
```

Use synthetic events or vendor simulation for validation. Do not deploy an impersonating AP, collect third-party traffic, or disrupt clients.

## Step 3 — Expected observations

A monitoring dashboard specification with metrics, thresholds, alert routes, retention, and test evidence.

## Step 4 — Risk analysis

Missing or unactionable telemetry delays detection of misconfiguration, unauthorized access, and availability incidents. Document evidence source, confidence, affected SSID/AP, operational impact, false positives, and monitoring gaps. A simulated event is not evidence of a live incident.

## Step 5 — Remediation and validation

Centralize protected logs, use actionable thresholds, assign owners, retain evidence appropriately, and exercise alert response.

Validate with a controlled synthetic event or approved lab client, confirm alert routing and analyst ownership, and record closure evidence. Preserve a rollback plan for configuration changes.

## Simulated training illustrations

> Fictional defensive training illustrations only—not actual controller alerts, live wireless traffic, or evidence of a real assessment.

![Project 35 lab configuration — simulated training illustration](screenshots/01-lab-overview.svg)

![Project 35 defensive validation — simulated training illustration](screenshots/02-assessment-workflow.svg)

![Project 35 findings and response — simulated training illustration](screenshots/03-findings-remediation.svg)

## Evidence and deliverables

- Authorization, exact SSID/BSSID scope, exclusions, and stop conditions.
- Sanitized AP/controller/WIDS configuration, firmware, and tool versions.
- Synthetic event details, timestamps, alert routing, triage notes, and configuration diffs.
- Finding register, false-positive notes, remediation owner, and retest status.
- No PSKs, passwords, private keys, real client identifiers, or third-party traffic in Git.

## Framework references

- NIST SP 800-153; NIST SP 800-92; CIS Controls
- [NIST SP 800-153](https://csrc.nist.gov/pubs/sp/800/153/final)
- [NIST SP 800-92 — Guide to Computer Security Log Management](https://csrc.nist.gov/pubs/sp/800/92/final)

## Completion checklist

- [ ] Written authorization and lab scope confirmed
- [ ] Defensive controls and telemetry baseline recorded
- [ ] Synthetic validation completed without disruption
- [ ] Evidence sanitized and limitations stated
- [ ] Response and remediation documented
- [ ] Alert workflow retested and owner assigned
