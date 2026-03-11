# Scenario 10: Security Incident (Critical Priority)

## Ticket Summary
- **Submitted by:** IT Staff / Monitoring System
- **Help Topic:** Security Concern
- **SLA:** SEV-A (Critical)
- **Priority:** Emergency
- **Assigned To:** Systems Administration / Level II

## Problem Description
A monitoring alert flags that a user account is showing login attempts from an unusual location or at unusual hours. This may indicate a compromised account requiring immediate investigation and remediation.

## Steps Taken to Resolve

### Step 1: Ticket Triage
- Screenshot: Ticket as it appears in the agent queue — set immediately to SEV-A / Emergency
- Observations: Note the 1-hour SLA clock, critical priority assignment
- Actions: Confirm Emergency priority and SEV-A SLA are applied

### Step 2: Immediate Response — Account Lockdown
- Screenshot: AD account disabled in ADUC
- Actions: Immediately disable the affected user account in Active Directory to prevent further unauthorized access

### Step 3: Investigation — Security Event Log Analysis
- Screenshot: Security Event Log on the DC showing Event IDs 4624 (successful logon) and 4625 (failed logon)
- Actions: Review Security Event Logs for suspicious logon events, document timestamps, source IPs, and logon types. Build a timeline of the incident.

### Step 4: Remediation
- Screenshot: Account re-enabled with new password (or kept disabled pending further review)
- Actions: After verifying the account is safe, either re-enable with a forced password reset or keep disabled pending further investigation. Document the decision rationale.

### Step 5: Resolution & Closure
- Screenshot: The closed ticket showing a detailed incident timeline
- Actions: Document the complete timeline, actions taken, findings, and any recommendations for preventing recurrence

## Key Takeaways
[What does this scenario demonstrate about IT support workflows?]
