# Project 37 — Wireless Controller Security Assessment

**Level:** Advanced | **Estimated time:** 4–6 hours

> **Authorized enterprise lab only.** Review only infrastructure you own or are explicitly authorized to assess. Use sanitized configuration exports and approved test clients; do not disrupt production wireless services.

## Objective

Assess controller management interfaces, administrative roles, APIs, certificates, logging, backups, and configuration drift.

## Scope and prerequisites

- Approved AP/controller/mesh estate and named management interfaces.
- Sanitized configuration exports, asset inventory, and authorized test clients.
- **Tools:** Wireless controller admin, SNMPv3, syslog, TLS inspection, config backup.
- Record authorization, sites, SSIDs/BSSIDs, AP models/firmware, controller versions, client types, and maintenance windows.
- Define exclusions, change approvals, rollback, and emergency contacts.

## Step 1 — Establish architecture and baseline

Document topology, management plane, SSID profiles, identity services, VLANs, firmware, and operational dependencies. Confirm that all collected exports are sanitized and approved for use.

```bash
ip -br link
 iw dev
nmcli -f DEVICE,TYPE,STATE,CONNECTION device status
```

## Step 2 — Assessment workflow

1. Inventory controller versions, management interfaces, HA peers, and administrative accounts.
2. Review MFA, RBAC, API token scope/expiry, SSH/HTTPS settings, and management network restrictions.
3. Verify SNMPv3 and protected log forwarding; disable insecure legacy management services.
4. Inspect backup encryption, access, retention, and restore testing.
5. Compare controller configuration templates with deployed AP groups and record drift.

Read-only review example:

```bash
Review controller admin roles, API tokens, SNMPv3, and syslog configuration
```

Adapt to the vendor platform. Do not perform disruptive RF tests or change production settings outside approved change control.

## Step 3 — Expected observations

A controller hardening checklist with admin roles, interfaces, API controls, logging, backups, and drift results.

## Step 4 — Risk analysis

Controller compromise can affect many APs, SSIDs, client policies, and wireless access decisions. Record affected site/AP group, evidence source, confidence, business impact, dependencies, and limitations. Distinguish a documented configuration deviation from a validated security impact.

## Step 5 — Remediation and validation

Restrict management access, enforce MFA/RBAC, rotate scoped API credentials, protect backups, and monitor config changes.

Implement through approved change control. Validate using configuration diffs, controller status, synthetic clients, and approved failover procedures. Keep a tested rollback path.

## Simulated training illustrations

> Fictional enterprise WLAN training illustrations only—not genuine controller screenshots, live RF captures, or evidence of an actual assessment.

![Project 37 architecture baseline — simulated training illustration](screenshots/01-lab-overview.svg)

![Project 37 authorized validation — simulated training illustration](screenshots/02-assessment-workflow.svg)

![Project 37 findings and remediation — simulated training illustration](screenshots/03-findings-remediation.svg)

## Evidence and deliverables

- Authorization, site/AP/SSID scope, exclusions, and approved change windows.
- Sanitized topology, configuration exports, firmware inventory, and tool versions.
- Validation results, configuration diffs, timestamps, and synthetic client observations.
- Risk-ranked finding register, remediation owners, dependencies, rollback, and retest status.
- No credentials, private keys, real client identifiers, or sensitive production topology in Git.

## Framework references

- NIST SP 800-153; CIS Controls; vendor controller security guides
- [NIST SP 800-153](https://csrc.nist.gov/pubs/sp/800/153/final)
- [CIS Controls](https://www.cisecurity.org/controls)

## Completion checklist

- [ ] Authorization and enterprise scope confirmed
- [ ] Architecture and baseline documented
- [ ] Configuration reviewed safely
- [ ] Evidence sanitized and limitations stated
- [ ] Remediation, owners, and rollback recorded
- [ ] Retest and operational sign-off completed
