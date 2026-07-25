# Week 4 — Enterprise Network Security and Access Control

**Intern:** Talha Asghar
**Registration No.:** NETB01-1565
**Program:** IT-Simplera Institute — Network Administration Internship
**Supervisor:** Jawad Qayum, Senior Network Administrator
**Submission Date:** 25 July 2026 | **Deadline:** 25 July 2026

## Overview

A 3-VLAN enterprise network (HR, Finance, IT) secured with Standard/Extended/Named ACLs, SSH-only management, and full Layer 2 hardening (Port Security, DHCP Snooping, BPDU Guard, Root Guard, PortFast) — designed, built, and verified in both GNS3 and Cisco Packet Tracer.

## Repository Structure

```
Week4/
├── README.md
├── Week4_Report.pdf              # Full report: design, ACL policy, configs, verification, troubleshooting
├── Week4_Lab.pkt                  # Cisco Packet Tracer project (add your .pkt file here)
├── gns3-project/                  # GNS3 project export (add your .gns3project here)
└── screenshots/
    ├── topology/                   # Full topology (both tools)
    ├── acl-verification/            # Standard/Extended/Named ACL enforcement tests
    ├── ssh-verification/            # Successful/refused SSH attempts
    ├── layer2-security/             # Port Security, DHCP Snooping, BPDU/Root Guard
    └── connectivity-tests/          # Ping/traceroute baseline confirming legitimate traffic works
```

**Note:** the assignment's "Tools Required" list only mentions GNS3, but the Deliverables and Submission Format both explicitly require a Cisco Packet Tracer file too — this repo includes both builds (Section 9 of the report covers the Packet Tracer rebuild).

## Security Policy Implemented

- **Standard ACL 10:** only the IT subnet (10.40.0.96/27) may SSH into any device.
- **Extended ACL 100 (HR):** blocks HR → Finance; allows HR → IT-Server on 80/443 only.
- **Extended ACL 110 (Finance):** blocks Finance → HR; allows Finance → IT-Server on 80/443 only.
- **Named ACL SERVER_ACCESS_POLICY:** IT subnet has full access everywhere; everyone else is limited to 80/443 on the IT-Server specifically.
- **Port Security:** MAC sticky learning, max 1-2 per port, mix of `restrict` and `shutdown` violation modes to compare both.
- **DHCP Snooping:** only the uplink to the real DHCP server is trusted; all access ports are untrusted.
- **BPDU Guard + PortFast:** on every access port.
- **Root Guard:** on the distribution switch's link toward the access switch, protecting the intentional root bridge.

Full IP addressing (VLSM, base `10.40.0.0/16`) and all device configs are in `Week4_Report.pdf`, Sections 3-7.

## Tools

GNS3 · Cisco Packet Tracer · PuTTY

## Related

- LinkedIn post: [insert your post link after publishing]
- Part of the IT-Simplera Institute Network Administration Internship program.
