 # osTicketing Help Desk Simulation — Home Lab Project

> A hands-on IT help desk simulation using osTicket, Windows Server 2025, and a domain-joined Windows 11 client. This project demonstrates real-world ticketing workflows, SLA management, and end-user support documentation skills.

---

## Environment Overview

| Component | Details |
|---|---|
| **Ticketing System** | osTicket (latest stable) on Incus container (Linux host) |
| **Domain Controller** | Windows Server 2025 with Active Directory (Users & OUs) |
| **Client Machine** | Windows 11 Pro, joined to the domain |

---

## Repository Structure

```
osticketing-help-desk-simulation/
│
├── README.md                          # Project overview (this file)
│
├── 01-environment-setup/
│   ├── README.md                      # Environment build documentation
│   ├── screenshots/
│   │   ├── incus-container-osticket.png
│   │   ├── osticket-dashboard-clean.png
│   │   ├── win-server-ad-users-ous.png
│   │   ├── win11-domain-join.png
│   │   └── network-topology-diagram.png
│   └── notes.md                       # IP addresses, credentials reference, container config
│
├── 02-osticket-administration/
│   ├── README.md                      # Admin panel configuration walkthrough
│   ├── screenshots/
│   │   ├── departments-created.png
│   │   ├── teams-created.png
│   │   ├── agents-created.png
│   │   ├── sla-plans-configured.png
│   │   ├── help-topics-configured.png
│   │   └── email-settings.png
│   └── config-summary.md             # Table of all configured settings
│
├── 03-ticket-lifecycle/
│   ├── README.md                      # Ticket lifecycle documentation
│   ├── scenarios/
│   │   ├── scenario-01-password-reset.md
│   │   ├── scenario-02-software-install.md
│   │   ├── scenario-03-network-connectivity.md
│   │   ├── scenario-04-new-hire-onboarding.md
│   │   ├── scenario-05-printer-issue.md
│   │   ├── scenario-06-vpn-access-request.md
│   │   ├── scenario-07-shared-drive-permissions.md
│   │   ├── scenario-08-hardware-failure.md
│   │   ├── scenario-09-email-not-syncing.md
│   │   └── scenario-10-security-incident.md
│   └── screenshots/
│       └── (ticket-specific screenshots organized by scenario)
│
├── 04-sla-and-priority-management/
│   ├── README.md                      # SLA tiers, escalation paths, priority matrix
│   └── screenshots/
│
├── 05-reporting-and-metrics/
│   ├── README.md                      # Dashboard metrics and KPIs
│   └── screenshots/
│
└── 06-lessons-learned/
    └── README.md                      # Reflections, challenges, what you'd do differently
```

---

## Phase 1 — Environment Setup (Document Everything)

### What to Configure

1. **Incus Container (osTicket host)**
   - Document the container's OS, resource allocation (CPU, RAM, disk), and network config (bridged/NAT).
   - Note the web server stack: Apache/Nginx, PHP version, MySQL/MariaDB version.
   - Screenshot the osTicket installer completion page and the clean admin dashboard.

2. **Windows Server 2025**
   - Document your AD structure: the domain name, OU hierarchy, and user accounts you created.
   - Create at least 3 OUs that mirror a real org, for example:
     - `OU=IT-Department`
     - `OU=Sales`
     - `OU=Human-Resources`
   - Create at least 6–8 user accounts spread across those OUs (these will be your simulated end users and agents).

3. **Windows 11 Client**
   - Screenshot the successful domain join.
   - Document that you can log in as different domain users from this machine (this is where you'll submit tickets from the "end user" perspective).

4. **Network Topology Diagram**
   - Create a simple diagram (draw.io, Excalidraw, or even ASCII art) showing how all three systems communicate.
   - Include IP addresses and hostnames.

### What to Capture (Screenshots & Notes)

- osTicket admin dashboard after fresh install
- Active Directory Users and Computers showing your OUs and users
- `ipconfig` / `ip a` output from each machine showing connectivity
- Successful domain join confirmation on Win11
- Browser accessing osTicket from the Win11 client

---

## Phase 2 — osTicket Administration

### 2A. Departments

Create departments that mirror your AD OUs. Example configuration:

| Department | Description | Manager |
|---|---|---|
| Help Desk / Level I Support | Frontline triage, password resets, basic troubleshooting | (Agent Name) |
| Systems Administration / Level II | Escalated issues, server/network, AD management | (Agent Name) |
| Management | Executive oversight, SLA violations, critical incidents | (Agent Name) |

**Document:** Screenshot each department's configuration page. Note the department's SLA, manager assignment, and any auto-assignment rules.

### 2B. Agents (Support Staff)

Map your AD users to osTicket agent roles. Create at least:

| Agent | Role | Department | AD Account |
|---|---|---|---|
| (Your Name) | Admin / Supreme Admin | All | yourname@domain.local |
| Jane Smith | Level I Technician | Help Desk | jsmith@domain.local |
| Bob Johnson | Level II Sysadmin | Systems Administration | bjohnson@domain.local |

**Document:** Screenshot the agent panel showing created agents, their department assignments, and permissions.

### 2C. Users (End Users / Customers)

Register osTicket user accounts that correspond to domain users who will "submit" tickets:

| User | Department (OU) | Email |
|---|---|---|
| Alice Williams | Sales | awilliams@domain.local |
| Carlos Reyes | Human Resources | creyes@domain.local |
| Dana Kim | Sales | dkim@domain.local |
| Eric Nguyen | IT Department | enguyen@domain.local |

**Document:** Screenshot the user directory in osTicket.

### 2D. SLA Plans

Create tiered SLAs that reflect real-world urgency:

| SLA Name | Grace Period | Schedule |
|---|---|---|
| SEV-A (Critical) | 1 hour | 24/7 |
| SEV-B (High) | 4 hours | 24/7 |
| SEV-C (Normal) | 8 hours | Business Hours (Mon–Fri, 8am–5pm) |

**Document:** Screenshot each SLA's configuration page. Explain in your README what types of issues map to each severity.

### 2E. Help Topics

Help Topics determine how tickets are categorized when users submit them:

| Help Topic                    | Priority  | Department             | SLA   |
| ----------------------------- | --------- | ---------------------- | ----- |
| Business Critical Outage      | Emergency | Systems Administration | SEV-A |
| Password Reset                | Normal    | Help Desk              | SEV-C |
| Software Installation Request | Normal    | Help Desk              | SEV-C |
| Network Connectivity Issue    | High      | Systems Administration | SEV-B |
| New Hire Onboarding           | Normal    | Help Desk              | SEV-C |
| Equipment Request             | Low       | Help Desk              | SEV-C |
| Access / Permissions Issue    | High      | Systems Administration | SEV-B |
| Security Concern              | Emergency | Systems Administration | SEV-A |

**Document:** Screenshot the Help Topics list and at least 2–3 individual topic configuration pages.

---

## Phase 3 — Ticket Lifecycle Scenarios

This is the core of the project. For each scenario, you will play both roles: submit the ticket as an end user, then switch to an agent to work and resolve it. Document every step.

### Template for Each Scenario

Use this structure for every scenario file in `03-ticket-lifecycle/scenarios/`:

```markdown
# Scenario [#]: [Title]

## Ticket Summary
- **Submitted by:** [End User Name]
- **Help Topic:** [Selected Help Topic]
- **SLA:** [Auto-assigned or manually set]
- **Priority:** [Emergency / High / Normal / Low]
- **Assigned To:** [Agent or Department]

## Problem Description
[Write 2–3 sentences describing the issue from the end user's perspective.
This is what they would type into the ticket form.]

## Steps Taken to Resolve

### Step 1: Ticket Triage
- Screenshot: Ticket as it appears in the agent queue
- Observations: Note the auto-assigned priority, SLA, and department
- Actions: Adjust priority/SLA/assignment if needed, document why

### Step 2: Initial Response
- Screenshot: Internal note or reply to user
- Actions: Describe what you communicated to the user and any initial
  troubleshooting steps

### Step 3: Troubleshooting / Resolution
- Screenshot: Any relevant work done on Win Server or Win11
  (e.g., AD password reset, Group Policy change, network config)
- Actions: Describe the technical steps taken to fix the issue

### Step 4: Resolution & Closure
- Screenshot: The closed ticket showing resolution notes
- Actions: Document the resolution summary and how you communicated
  it to the end user

## Key Takeaways
[1–2 sentences: What does this scenario demonstrate about IT support workflows?]
```

---

### Scenario Details

Below are the 10 scenarios to complete. Each one ties osTicket actions to real work on your Windows Server/Client environment.

#### Scenario 1 — Password Reset

- **User:** Alice Williams (Sales) submits a ticket saying she's locked out of her account.
- **Agent Actions:** Log into Win Server, open ADUC, locate Alice's account in the Sales OU, unlock the account and/or reset the password. Reply to the ticket with instructions. Close.
- **Why It Matters:** The single most common help desk ticket. Shows you can navigate AD.

#### Scenario 2 — Software Installation Request

- **User:** Carlos Reyes (HR) requests that Adobe Reader be installed on his workstation.
- **Agent Actions:** Log into the Win11 client as an admin (or via remote tools), install the software, verify it launches. Update the ticket with confirmation. Close.
- **Why It Matters:** Demonstrates software deployment and change documentation.

#### Scenario 3 — Network Connectivity Issue

- **User:** Dana Kim (Sales) reports she cannot access any network resources or the internet from her workstation.
- **Agent Actions:** Troubleshoot on Win11: check `ipconfig`, verify DNS points to the DC, test `ping` to the DC and gateway, check if the NIC is disabled. Document each step in the ticket's internal notes. Resolve and close.
- **Why It Matters:** Shows structured network troubleshooting methodology.

#### Scenario 4 — New Hire Onboarding

- **User:** HR (Carlos Reyes) submits a ticket requesting a new account for an incoming employee in the Sales department.
- **Agent Actions:** Create the new user in the Sales OU on Win Server, set the initial password to require change at first login, add to appropriate security groups, document the completed account info (minus the password) in the ticket. Close.
- **Why It Matters:** Demonstrates account provisioning workflows and inter-department coordination.

#### Scenario 5 — Printer Issue

- **User:** Eric Nguyen (IT) reports that the shared department printer is showing as offline and no one can print.
- **Agent Actions:** Check print server settings on Win Server (or local printer config on Win11), restart the Print Spooler service, verify the printer comes back online. Document the fix. Close.
- **Why It Matters:** Common help desk issue; shows service management on Windows.

#### Scenario 6 — VPN Access Request

- **User:** Alice Williams (Sales) requests VPN access to work remotely.
- **Agent Actions:** Verify with her manager (internal note), add Alice to the "VPN-Users" security group in AD, document the approval chain and group membership change. Close.
- **Why It Matters:** Demonstrates access control, approval workflows, and security group management.

#### Scenario 7 — Shared Drive / Permissions Issue

- **User:** Dana Kim (Sales) reports she cannot access the `\\server\Sales-Share` shared folder.
- **Agent Actions:** Check NTFS and share permissions on the Win Server, verify Dana's AD group memberships, fix the permission issue (e.g., add her to the "Sales-FileAccess" group). Document before/after. Close.
- **Why It Matters:** File share permissions are a daily reality in IT support. Shows NTFS/share permission troubleshooting.

#### Scenario 8 — Hardware Failure (Escalation Demo)

- **User:** Eric Nguyen reports his workstation randomly crashes with a blue screen.
- **Agent Actions (Level I):** Triage the ticket, gather info (Event Viewer logs, crash dump info), document findings in an internal note, then **escalate to Level II / Systems Administration** with a note explaining why.
- **Agent Actions (Level II):** Review the escalation notes, determine it's a hardware issue, document the recommendation (e.g., replace RAM, submit warranty claim). Update the ticket's priority to High. Close with resolution.
- **Why It Matters:** Demonstrates the escalation process between departments and tiers.

#### Scenario 9 — Email Not Syncing

- **User:** Carlos Reyes (HR) says his Outlook isn't receiving new emails since this morning.
- **Agent Actions:** Check the user's mailbox status (simulate by verifying connectivity), verify DNS and network settings, restart the Outlook profile, document each troubleshooting step. Close.
- **Why It Matters:** Shows methodical troubleshooting and user communication.

#### Scenario 10 — Security Incident (Critical Priority)

- **User:** You (as a monitoring system or IT staff) create a ticket flagging that a user account is showing login attempts from an unusual location or at unusual hours.
- **Agent Actions:** Immediately set to SEV-A / Emergency. Disable the affected account in AD. Check the Security Event Log on the DC for suspicious logon events (Event IDs 4625, 4624). Document all findings. Re-enable the account after verifying it's safe, or reset the password. Close with a detailed timeline.
- **Why It Matters:** Shows incident response fundamentals, security log analysis, and handling critical-priority tickets under SLA pressure.

---

## Phase 4 — SLA & Priority Management

After completing several scenarios, document how SLAs behaved:

- Screenshot a ticket that was within SLA and one that was approaching or past its deadline.
- Show how you changed a ticket's priority or SLA mid-lifecycle and explain why.
- Document the escalation path: Level I → Level II → Management, including how reassignment looks in osTicket.
- Create a simple **Priority Matrix** in your README:

| Priority | Example Issues | Response Time | Resolution Target |
|---|---|---|---|
| Emergency | Security breach, business-critical outage | 15 min | 1 hour |
| High | Network down for a department, permissions blocking work | 30 min | 4 hours |
| Normal | Software install, password reset, new hire setup | 1 hour | 8 hours |
| Low | Equipment request, non-urgent question | 4 hours | 24 hours |

---

## Phase 5 — Reporting & Metrics

Take screenshots of osTicket's built-in reporting dashboard and document:

- Total tickets created vs. resolved
- Average response time
- Tickets by department
- Tickets by Help Topic
- SLA compliance rate (how many were resolved within SLA)
- Any overdue tickets and why

If osTicket's built-in reports are limited, note that in your documentation and describe what KPIs you would track in a production environment.

---

## Phase 6 — Lessons Learned & Reflection

Write a final `README.md` in `06-lessons-learned/` covering:

1. **What went well** — Which parts of the setup and workflow felt natural?
2. **What was challenging** — Any configuration headaches, things that took longer than expected?
3. **What you would do differently** — If you were setting this up for a real team, what would you change?
4. **Skills demonstrated** — A clean summary list of everything this project proves you can do:
   - Deployed and configured osTicket on a Linux container
   - Managed Active Directory users, OUs, and security groups on Windows Server 2025
   - Simulated realistic help desk workflows across 10 ticket scenarios
   - Configured SLA tiers and escalation paths
   - Documented every step with screenshots and written procedures
   - Troubleshot network, software, permissions, and security issues on domain-joined Windows clients

---

## How to Present This to Employers

### On Your Resume

```
osTicketing Help Desk Simulation — Home Lab Project
- Deployed osTicket on a Linux container and integrated it with a Windows Server
  2025 Active Directory environment (domain controller + Windows 11 client).
- Configured departments, agents, SLA tiers (SEV-A/B/C), and help topics to
  mirror a production IT support structure.
- Simulated and documented 10 end-to-end ticket scenarios including password
  resets, account provisioning, network troubleshooting, permission management,
  escalations, and security incident response.
- Maintained detailed documentation with screenshots demonstrating ticket
  lifecycle management, SLA compliance, and cross-tier escalation workflows.
```

### On LinkedIn / In Interviews

Link directly to the GitHub repository. Walk interviewers through 2–3 scenarios that show range: one simple (password reset), one involving escalation (hardware failure), and one high-severity (security incident). Emphasize that you played both the user and agent roles, which shows you understand both sides of the support experience.

---

## Quick-Start Checklist

Use this to track your progress:

- [ ] Environment documented (screenshots of all three systems, network diagram)
- [ ] osTicket Admin Panel configured (departments, agents, users, SLAs, help topics)
- [ ] Scenario 1 completed and documented (Password Reset)
- [ ] Scenario 2 completed and documented (Software Install)
- [ ] Scenario 3 completed and documented (Network Connectivity)
- [ ] Scenario 4 completed and documented (New Hire Onboarding)
- [ ] Scenario 5 completed and documented (Printer Issue)
- [ ] Scenario 6 completed and documented (VPN Access Request)
- [ ] Scenario 7 completed and documented (Shared Drive Permissions)
- [ ] Scenario 8 completed and documented (Hardware Failure / Escalation)
- [ ] Scenario 9 completed and documented (Email Not Syncing)
- [ ] Scenario 10 completed and documented (Security Incident)
- [ ] SLA & priority management documented
- [ ] Reporting dashboard captured
- [ ] Lessons learned written
- [ ] Resume bullet points finalized
- [ ] Repository cleaned up and published to GitHub
