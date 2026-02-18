<img width="200" height="350" alt="image" src="https://github.com/user-attachments/assets/17d611a8-8511-40b4-bcc8-cebbcf02204a" />




# 🖥️ Help Desk Automation Suite

> A fully automated IT Help Desk system built with PowerShell, covering ticket management, user onboarding/offboarding, password resets, and automated email notifications — simulating a real enterprise IT support environment.

---

## 📋 Project Overview

This project automates the most common Help Desk tasks in a Windows/Active Directory environment. Every script is production-ready, logged, and follows enterprise IT best practices.

---

## 🗺️ System Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│                   HELP DESK AUTOMATION SUITE                        │
│                                                                     │
│  ┌─────────────────┐    ┌─────────────────┐    ┌────────────────┐  │
│  │   TICKET SYSTEM  │    │  USER LIFECYCLE  │    │  SELF-SERVICE  │  │
│  │                 │    │                 │    │                │  │
│  │ • Create ticket │    │ • Onboarding    │    │ • Pwd Reset    │  │
│  │ • Update status │    │ • Offboarding   │    │ • Account      │  │
│  │ • Assign/Escalate│   │ • Role changes  │    │   Unlock       │  │
│  │ • Close ticket  │    │ • AD provisioning│   │ • Email notify │  │
│  └────────┬────────┘    └────────┬────────┘    └───────┬────────┘  │
│           │                      │                     │           │
│           └──────────────────────┼─────────────────────┘           │
│                                  │                                  │
│                    ┌─────────────▼──────────────┐                  │
│                    │      LOGGING & REPORTING    │                  │
│                    │  • All actions logged       │                  │
│                    │  • Daily summary reports    │                  │
│                    │  • Email notifications      │                  │
│                    │  • Audit trail              │                  │
│                    └────────────────────────────┘                  │
└─────────────────────────────────────────────────────────────────────┘
```

---

## 📁 Repository Structure

```
helpdesk-automation/
├── tickets/
│   ├── New-Ticket.ps1              # Create a new support ticket
│   ├── Update-Ticket.ps1           # Update ticket status/notes
│   ├── Get-Ticket.ps1              # Query/search tickets
│   └── Close-Ticket.ps1            # Close and archive tickets
├── onboarding/
│   ├── New-Employee.ps1            # Full new hire onboarding
│   └── onboarding-template.csv    # New hire data template
├── offboarding/
│   └── Remove-Employee.ps1         # Full employee offboarding
├── password-reset/
│   ├── Reset-UserPassword.ps1      # Admin password reset
│   └── Unlock-UserAccount.ps1      # Unlock locked accounts
├── email/
│   └── Send-HDNotification.ps1     # Email notification engine
├── reports/
│   └── Get-DailyReport.ps1         # Daily helpdesk summary report
├── docs/
│   ├── setup-guide.md              # Setup and configuration guide
│   └── runbook.md                  # IT runbook / SOPs
└── screenshots/
    ├── ticket-workflow.md          # Ticket lifecycle diagram
    ├── onboarding-flow.md          # Onboarding process diagram
    └── dashboard.md                # Sample report output
```

---

## 🎫 Ticket System

```
TICKET LIFECYCLE
─────────────────────────────────────────────────────
New-Ticket.ps1          Creates ticket with auto ID
      │
      ▼
  [OPEN] ──► Update-Ticket.ps1 ──► [IN PROGRESS]
                                         │
                              ┌──────────┴──────────┐
                              ▼                     ▼
                         [ESCALATED]           [RESOLVED]
                              │                     │
                              └──────────┬──────────┘
                                         ▼
                                  Close-Ticket.ps1
                                         │
                                         ▼
                                     [CLOSED]
─────────────────────────────────────────────────────
All status changes logged to C:\HelpDesk\Logs\
```

---

## 👤 User Lifecycle Automation

| Script | What it Does |
|---|---|
| `New-Employee.ps1` | Creates AD account, sets groups, home drive, email, sends welcome email |
| `Remove-Employee.ps1` | Disables account, strips groups, archives mailbox, documents everything |
| `Reset-UserPassword.ps1` | Resets password, forces change at logon, notifies user |
| `Unlock-UserAccount.ps1` | Unlocks account, logs who/when, notifies user |

---

## 📊 Daily Report Sample

```
╔══════════════════════════════════════════════════════╗
║         HELP DESK DAILY REPORT — 2026-02-17          ║
╠══════════════════════════════════════════════════════╣
║  New Tickets Today    :  12                          ║
║  Tickets Resolved     :  9                           ║
║  Tickets Escalated    :  2                           ║
║  Avg Resolution Time  :  2.4 hours                   ║
╠══════════════════════════════════════════════════════╣
║  Password Resets      :  5                           ║
║  Account Unlocks      :  3                           ║
║  New Onboardings      :  1                           ║
║  Offboardings         :  0                           ║
╠══════════════════════════════════════════════════════╣
║  OPEN TICKETS         :  7                           ║
║  CRITICAL/P1          :  0                           ║
╚══════════════════════════════════════════════════════╝
```

---

## 🚀 Quick Start

```powershell
# Create a new ticket
.\tickets\New-Ticket.ps1 -User "jsmith" -Category "Hardware" -Priority "High" -Description "Monitor not working"

# Onboard a new employee
.\onboarding\New-Employee.ps1 -FirstName "Jane" -LastName "Doe" -Department "IT" -Manager "jsmith"

# Reset a password
.\password-reset\Reset-UserPassword.ps1 -Username "jsmith" -TicketID "HD-0042"

# Unlock an account
.\password-reset\Unlock-UserAccount.ps1 -Username "jsmith"

# Run daily report
.\reports\Get-DailyReport.ps1
```

---

## 📊 Skills Demonstrated

- **PowerShell Scripting** — Advanced automation, functions, error handling
- **Active Directory** — User lifecycle management via ADUC
- **SMTP/Email Automation** — Automated notifications and alerts
- **IT Service Management** — Ticket system, SLAs, escalation logic
- **Documentation** — Runbooks, SOPs, audit trails
- **Reporting** — Automated daily summaries and metrics

---

## 👤 Author

**GitHub:** [@Dm261416](https://github.com/Dm261416)
**Project Type:** IT Home Lab | Help Desk Automation | PowerShell
