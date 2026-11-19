# Project 32 — Evil Twin Exposure Assessment — Defensive Lab

**Level:** Intermediate | **Estimated time:** 3–4 hours

> **Defensive, authorized lab only.** This project uses owned AP/controller configuration, synthetic event records, and authorized test clients. It does not include rogue AP deployment, SSID impersonation, credential harvesting, deauthentication, or disruptive frame injection.

## Objective

Assess client and infrastructure defenses against lookalike SSIDs using configuration review, synthetic controller events, and user-awareness controls only.

## Scope and prerequisites

- Owned AP/controller and isolated lab SSID.
- Synthetic clients, controller logs, and vendor-provided simulator/historical sanitized events.
- **Tools:** Wireless controller, WIDS, client profile settings, awareness materials.
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

1. Inventory approved SSIDs, BSSIDs, certificate trust requirements, and client auto-join settings.
2. Review WIDS rules for lookalike SSIDs and unauthorized AP classification.
3. Use synthetic event records or a vendor-provided simulator to validate alert generation; do not broadcast an impersonating AP.
4. Verify enterprise clients validate server certificates and users are trained not to accept unexpected portals/certificates.
5. Document response steps for suspected lookalike SSIDs and neighboring-network false positives.

Read-only review example:

```bash
Review trusted SSID profiles and WIDS lookalike/duplicate-BSSID alert rules
```

Use synthetic events or vendor simulation for validation. Do not deploy an impersonating AP, collect third-party traffic, or disrupt clients.

## Step 3 — Expected observations

A defensive control matrix for SSID trust, certificate validation, auto-join, detection alerts, and incident handling.

## Step 4 — Risk analysis

Users may connect to lookalike networks if client trust and certificate validation are weak. Document evidence source, confidence, affected SSID/AP, operational impact, false positives, and monitoring gaps. A simulated event is not evidence of a live incident.

## Step 5 — Remediation and validation

Use managed Wi-Fi profiles, strict certificate validation, disable risky auto-join behavior, tune WIDS detection, and train users.

Validate with a controlled synthetic event or approved lab client, confirm alert routing and analyst ownership, and record closure evidence. Preserve a rollback plan for configuration changes.

## Simulated training illustrations

> Fictional defensive training illustrations only—not actual controller alerts, live wireless traffic, or evidence of a real assessment.

![Project 32 lab configuration — simulated training illustration](screenshots/01-lab-overview.svg)

![Project 32 defensive validation — simulated training illustration](screenshots/02-assessment-workflow.svg)

![Project 32 findings and response — simulated training illustration](screenshots/03-findings-remediation.svg)

## Evidence and deliverables

- Authorization, exact SSID/BSSID scope, exclusions, and stop conditions.
- Sanitized AP/controller/WIDS configuration, firmware, and tool versions.
- Synthetic event details, timestamps, alert routing, triage notes, and configuration diffs.
- Finding register, false-positive notes, remediation owner, and retest status.
- No PSKs, passwords, private keys, real client identifiers, or third-party traffic in Git.

## Framework references

- NIST SP 800-153; Wi-Fi Alliance enterprise security guidance
- [NIST SP 800-153](https://csrc.nist.gov/pubs/sp/800/153/final)
- [NIST SP 800-92 — Guide to Computer Security Log Management](https://csrc.nist.gov/pubs/sp/800/92/final)

## Completion checklist

- [ ] Written authorization and lab scope confirmed
- [ ] Defensive controls and telemetry baseline recorded
- [ ] Synthetic validation completed without disruption
- [ ] Evidence sanitized and limitations stated
- [ ] Response and remediation documented
- [ ] Alert workflow retested and owner assigned
