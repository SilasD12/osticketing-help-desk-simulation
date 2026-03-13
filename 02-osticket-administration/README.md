# Phase 2: osTicket Administration

Full configuration details are documented in `config-summary.md`.

## Departments

| Department                        | Description                                                                                                                                             | Manager      |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ |
| Help Desk Level 1                 | Help Desk support for level 1 tickets,<br>such as common troubleshooting, password<br>resets, unlocking accounts, etc                                   | Oliver Brown |
| Systems Administration<br>Level 2 | Ticket resolution for escalated tickets that deal<br>with Active Directory management (creation of<br>users, moving of users, modifying OUs, GPOs, etc) | Emma Stone   |

![Departments](screenshots/departments-created.png)

## Agents

| Agent        | Role                 | Department                     |
| ------------ | -------------------- | ------------------------------ |
| Emma Stone   | Manager              | Systems Administrator Level II |
| Sarah Baker  | System Administrator | Systems Administrator Level II |
| Oliver Brown | Manager              | Help Desk Level 1              |
| May Fitz     | Help Desk Support    | Help Desk Level 1              |

![Agents](screenshots/agents-created.png)

## Users

| User         | OU         | Email                     |
| ------------ | ---------- | ------------------------- |
| Alice Smith  | Accounting | alicesmith@homelab.local  |
| Diana Prince | Accounting | dianaprince@homelab.local |
| Jack Smart   | Accounting | jacksmart@homelab.local   |
| Bob Jones    | Management | bobjones@homelab.local    |
| Jane Doe     | Management | janedoe@homelab.local     |
| John Smith   | Management | johnsmith@homelab.local   |
| Mark Strong  | Management | markstrong@homelab.local  |

## SLA Plans

| SLA | Grace Period | Schedule |
|---|---|---|
| SEV-A (Critical) | 1 hour | 24/7 |
| SEV-B (High) | 4 hours | 24/7 |
| SEV-C (Normal) | 8 hours | Business hours |

![SLA Plans](screenshots/sla-plans-configured.png)

## Help Topics

| Help Topic                 | Priority  | Department                      | SLA   |
| -------------------------- | --------- | ------------------------------- | ----- |
| Software Installation      | Normal    | Help Desk Level 1               | SEV-C |
| Network Connectivity Issue | High      | Systems Administration Level II | SEV-B |
| New Hire Onboarding        | Normal    | Help Desk Level 1               | SEV-C |
| Equipment Request          | Low       | Help Desk Level 1               | SEV-C |
| Access / Permission Issue  | High      | Systems Administration Level II | SEV-B |
| Security Concern           | Emergency | Systems Administration Level II | SEV-A |
| Business Critical Outage   | Emergency | Systems Administration Level II | SEV-A |
| Password Reset             | Normal    | Help Desk Level 1               | SEV-C |

![Help Topics](screenshots/help-topics-configured.png)
