<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<style>
  * { margin: 0; padding: 0; box-sizing: border-box; }
  body {
    background: #0d1117;
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    padding: 40px;
    font-family: 'Segoe UI', Arial, sans-serif;
  }
  .diagram {
    background: #0d1117;
    border: 2px solid #30363d;
    border-radius: 12px;
    padding: 32px;
    width: 860px;
  }
  .title {
    text-align: center;
    color: #58a6ff;
    font-size: 22px;
    font-weight: bold;
    margin-bottom: 6px;
  }
  .subtitle {
    text-align: center;
    color: #8b949e;
    font-size: 13px;
    margin-bottom: 32px;
  }
  .top-row {
    display: flex;
    gap: 20px;
    justify-content: center;
    margin-bottom: 0;
  }
  .box {
    border-radius: 10px;
    overflow: hidden;
    flex: 1;
    max-width: 260px;
  }
  .box-header {
    padding: 12px 16px;
    font-size: 14px;
    font-weight: bold;
    color: white;
    text-align: center;
  }
  .box-body {
    background: #161b22;
    padding: 16px;
    border-left: 2px solid;
    border-right: 2px solid;
    border-bottom: 2px solid;
    border-radius: 0 0 10px 10px;
  }
  .box-body ul { list-style: none; }
  .box-body ul li { color: #e6edf3; font-size: 13px; padding: 4px 0; }
  .box-body ul li::before { content: "✦ "; }
  .box-body .scripts { margin-top: 10px; padding-top: 10px; border-top: 1px solid #30363d; }
  .box-body .scripts p { color: #8b949e; font-size: 11px; font-family: 'Consolas', monospace; padding: 2px 0; }
  .blue .box-header { background: #1f6feb; }
  .blue .box-body { border-color: #1f6feb; }
  .blue li { color: #79c0ff; }
  .green .box-header { background: #238636; }
  .green .box-body { border-color: #3fb950; }
  .green li { color: #7ee787; }
  .orange .box-header { background: #bd561d; }
  .orange .box-body { border-color: #f0883e; }
  .orange li { color: #ffa657; }
  .bottom-box { background: #161b22; border: 2px solid #bc8cff; border-radius: 10px; overflow: hidden; }
  .bottom-box .box-header { background: #6e40c9; padding: 14px; font-size: 15px; text-align: center; color: white; font-weight: bold; }
  .bottom-box .inner { display: flex; gap: 24px; padding: 20px 28px; }
  .bottom-col p { color: #e6edf3; font-size: 13px; padding: 5px 0; }
  .bottom-col p::before { content: "✦ "; color: #bc8cff; }
</style>
</head>
<body>
<div class="diagram">
  <div class="title">🖥️ Help Desk Automation Suite</div>
  <div class="subtitle">PowerShell · Active Directory · Windows Server 2022</div>
  <div class="top-row">
    <div class="box blue">
      <div class="box-header">🎫 TICKET SYSTEM</div>
      <div class="box-body">
        <ul>
          <li>Create ticket</li>
          <li>Update status</li>
          <li>Assign / Escalate</li>
          <li>Close &amp; archive</li>
          <li>SLA tracking</li>
        </ul>
        <div class="scripts">
          <p>New-Ticket.ps1</p>
          <p>Update-Ticket.ps1</p>
          <p>Get-Ticket.ps1</p>
          <p>Close-Ticket.ps1</p>
        </div>
      </div>
    </div>
    <div class="box green">
      <div class="box-header">👤 USER LIFECYCLE</div>
      <div class="box-body">
        <ul>
          <li>Onboarding</li>
          <li>Offboarding</li>
          <li>Role changes</li>
          <li>AD provisioning</li>
          <li>Group assignment</li>
        </ul>
        <div class="scripts">
          <p>New-Employee.ps1</p>
          <p>Remove-Employee.ps1</p>
        </div>
      </div>
    </div>
    <div class="box orange">
      <div class="box-header">🔐 SELF-SERVICE</div>
      <div class="box-body">
        <ul>
          <li>Password reset</li>
          <li>Account unlock</li>
          <li>Email notify</li>
          <li>Identity verify</li>
          <li>Auto temp password</li>
        </ul>
        <div class="scripts">
          <p>Reset-UserPassword.ps1</p>
          <p>Unlock-UserAccount.ps1</p>
        </div>
      </div>
    </div>
  </div>
  <div style="display:flex;justify-content:center;height:50px;align-items:center;position:relative;">
    <div style="width:2px;height:50px;background:#30363d;"></div>
    <div style="position:absolute;bottom:0;width:0;height:0;border-left:8px solid transparent;border-right:8px solid transparent;border-top:10px solid #30363d;"></div>
  </div>
  <div class="bottom-box">
    <div class="box-header">📊 LOGGING &amp; REPORTING</div>
    <div class="inner">
      <div class="bottom-col">
        <p>All actions logged with timestamps</p>
        <p>Daily summary report emailed to management</p>
      </div>
      <div class="bottom-col">
        <p>Full audit trail preserved</p>
        <p>SLA tracking &amp; breach alerts</p>
      </div>
    </div>
  </div>
</div>
</body>
</html>






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
