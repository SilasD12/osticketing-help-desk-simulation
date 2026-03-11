# osTicketing Help Desk Simulation

A full-cycle IT help desk simulation built in a home lab environment. This project demonstrates ticketing system administration, Active Directory management, SLA enforcement, and structured incident resolution across 10 real-world support scenarios.

---

## Environment

| Component | Details |
|---|---|
| **Ticketing System** | osTicket (latest stable) hosted on a Linux-based Incus container |
| **Domain Controller** | Windows Server 2025 running Active Directory with organizational units and user accounts |
| **Client Machine** | Windows 11 Pro, domain-joined |
| **Host OS** | Linux |

![Network Topology](01-environment-setup/screenshots/network-topology-diagram.png)

---

## osTicket Configuration

The osTicket instance was configured to reflect a production IT support structure:

**Departments** — Help Desk (Level I) for frontline triage and Systems Administration (Level II) for escalated issues, each with assigned managers and auto-routing rules.

**Agents & Users** — Support agents mapped to Active Directory accounts across departments. End users registered from domain accounts spanning Sales, HR, and IT organizational units.

**SLA Plans** — Three severity tiers enforcing response and resolution deadlines:

| SLA | Grace Period | Schedule |
|---|---|---|
| SEV-A (Critical) | 1 hour | 24/7 |
| SEV-B (High) | 4 hours | 24/7 |
| SEV-C (Normal) | 8 hours | Business hours |

**Help Topics** — Configured to auto-assign priority, department, and SLA based on issue type (e.g., "Business Critical Outage" routes to Systems Administration at SEV-A; "Password Reset" routes to Help Desk at SEV-C).

Full configuration details and screenshots are in [`02-osticket-administration/`](02-osticket-administration/).

---

## Ticket Scenarios

Each scenario was executed end-to-end: submitted from the end-user perspective on the Windows 11 client, then triaged, worked, and resolved from the agent perspective in osTicket. All troubleshooting was performed live against the Windows Server and client environments.

| # | Scenario | SLA | Key Skills |
|---|---|---|---|
| 1 | [Password Reset](03-ticket-lifecycle/scenarios/scenario-01-password-reset.md) | SEV-C | AD account unlock, ADUC navigation |
| 2 | [Software Installation](03-ticket-lifecycle/scenarios/scenario-02-software-install.md) | SEV-C | Remote software deployment, change documentation |
| 3 | [Network Connectivity](03-ticket-lifecycle/scenarios/scenario-03-network-connectivity.md) | SEV-B | DNS verification, NIC troubleshooting, structured diagnosis |
| 4 | [New Hire Onboarding](03-ticket-lifecycle/scenarios/scenario-04-new-hire-onboarding.md) | SEV-C | Account provisioning, security group assignment, OU placement |
| 5 | [Printer Issue](03-ticket-lifecycle/scenarios/scenario-05-printer-issue.md) | SEV-C | Print Spooler service management, printer configuration |
| 6 | [VPN Access Request](03-ticket-lifecycle/scenarios/scenario-06-vpn-access-request.md) | SEV-C | Approval workflows, AD security group management |
| 7 | [Shared Drive Permissions](03-ticket-lifecycle/scenarios/scenario-07-shared-drive-permissions.md) | SEV-B | NTFS/share permissions, group membership troubleshooting |
| 8 | [Hardware Failure](03-ticket-lifecycle/scenarios/scenario-08-hardware-failure.md) | SEV-B | Event Viewer analysis, Level I → Level II escalation |
| 9 | [Email Not Syncing](03-ticket-lifecycle/scenarios/scenario-09-email-not-syncing.md) | SEV-C | Outlook profile troubleshooting, DNS and connectivity checks |
| 10 | [Security Incident](03-ticket-lifecycle/scenarios/scenario-10-security-incident.md) | SEV-A | Account lockdown, Security Event Log analysis (4624/4625), incident timeline |

---

## Escalation & Priority Management

Tickets follow a defined escalation path based on severity and agent capability:

**Level I (Help Desk)** → **Level II (Systems Administration)** → **Management**

Scenario 8 demonstrates this in practice — a hardware failure that Level I triaged and documented before escalating to Level II with supporting Event Viewer evidence. Scenario 10 shows a critical-priority security incident handled under a 1-hour SLA with immediate account remediation.

Priority assignments, SLA adjustments made mid-ticket, and escalation rationale are documented within each scenario file.

---

## Reporting

Metrics captured from the osTicket dashboard after completing all scenarios:

- Tickets created vs. resolved
- Average response and resolution times
- SLA compliance rate
- Ticket distribution by department and help topic
- Overdue ticket analysis

Screenshots and observations are in [`05-reporting-and-metrics/`](05-reporting-and-metrics/).

---

## Repository Structure

```
├── 01-environment-setup/          # Infrastructure documentation and network diagram
├── 02-osticket-administration/    # Department, agent, SLA, and help topic configuration
├── 03-ticket-lifecycle/           # 10 documented ticket scenarios with screenshots
│   └── scenarios/
├── 04-sla-and-priority-management/  # Priority matrix and escalation documentation
├── 05-reporting-and-metrics/      # Dashboard captures and KPI analysis
└── 06-lessons-learned/            # Reflections and skills summary
```

---

## Skills Demonstrated

- osTicket deployment, configuration, and administration on Linux
- Active Directory user and group management on Windows Server 2025
- SLA tier design and enforcement across ticket priorities
- Structured troubleshooting for network, permissions, software, and security issues
- Ticket lifecycle management from submission through escalation to resolution
- Security incident response including event log analysis and account remediation
- Technical documentation with reproducible, screenshot-backed procedures
