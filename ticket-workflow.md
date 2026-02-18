# 🎫 Ticket Workflow & Lifecycle

## Full Ticket Lifecycle

```
  USER REPORTS ISSUE
         │
         ▼
  ┌──────────────┐
  │  New-Ticket  │ ◄── Auto-generates HD-XXXX ID
  │  .ps1        │     Sets SLA timer
  └──────┬───────┘     Assigns to technician
         │             Sends email notification
         ▼
    ┌─────────┐
    │  OPEN   │
    └────┬────┘
         │
         ▼
  ┌──────────────┐
  │Update-Ticket │
  │  .ps1        │
  └──────┬───────┘
         │
    ┌────▼─────────────────────┐
    │                          │
    ▼                          ▼
┌───────────┐          ┌────────────┐
│ IN PROGRESS│         │  ESCALATED │
└─────┬──────┘         └─────┬──────┘
      │                      │
      │    Reassign to        │
      │    senior tech ───────┘
      │
      ▼
┌──────────────┐
│   RESOLVED   │ ◄── Technician documents fix
└──────┬───────┘
       │
       ▼
┌──────────────┐
│Close-Ticket  │ ◄── Logs resolution time
│  .ps1        │     Archives ticket JSON
└──────┬───────┘     Emails user confirmation
       │
       ▼
┌──────────────┐
│   CLOSED     │ → Moved to C:\HelpDesk\Archive\
└──────────────┘
```

## SLA Timers by Priority

```
┌──────────────┬────────────┬──────────────────────────────────┐
│  Priority    │  SLA Time  │  Example Scenarios               │
├──────────────┼────────────┼──────────────────────────────────┤
│  CRITICAL    │  1 hour    │  Server down, network outage,    │
│              │            │  security incident               │
├──────────────┼────────────┼──────────────────────────────────┤
│  HIGH        │  4 hours   │  Can't log in, email not working,│
│              │            │  key application down            │
├──────────────┼────────────┼──────────────────────────────────┤
│  MEDIUM      │  8 hours   │  Printer not working, software   │
│              │            │  install, slow computer          │
├──────────────┼────────────┼──────────────────────────────────┤
│  LOW         │  24 hours  │  General questions, new desk     │
│              │            │  setup, non-urgent requests      │
└──────────────┴────────────┴──────────────────────────────────┘
```

## Ticket File Structure (JSON)

```
C:\HelpDesk\
├── Tickets\           ← Active tickets (Open, In Progress, Escalated)
│   ├── HD-0001.json
│   ├── HD-0002.json
│   └── ...
├── Archive\           ← Closed tickets
│   ├── HD-0001.json   (moved here on Close-Ticket)
│   └── ...
├── Logs\              ← Monthly log files
│   ├── helpdesk-2026-02.log
│   ├── password-resets-2026-02.log
│   ├── onboarding-2026-02.log
│   └── offboarding-2026-02.log
├── Reports\           ← Daily generated reports
│   └── daily-report-2026-02-17.txt
└── Offboarding\       ← Offboarding documentation
    └── jdoe-20260217.txt
```

## Sample Ticket JSON

```json
{
  "TicketID": "HD-0042",
  "Status": "In Progress",
  "Priority": "High",
  "Category": "Account",
  "CreatedAt": "2026-02-17 09:15:00",
  "SLADue": "2026-02-17 13:15:00",
  "User": "jsmith",
  "UserDisplay": "John Smith",
  "UserEmail": "jsmith@corp.local",
  "Department": "IT",
  "Description": "Cannot log into workstation after password expiry",
  "AssignedTo": "helpdesk",
  "History": [
    {
      "Timestamp": "2026-02-17 09:15:00",
      "Action": "Ticket created",
      "By": "helpdesk_admin",
      "Note": "Priority: High | Category: Account"
    },
    {
      "Timestamp": "2026-02-17 09:22:00",
      "Action": "Status: Open → In Progress",
      "By": "tech01",
      "Note": "Calling user to assist with password reset"
    }
  ]
}
```
