# 👤 Onboarding & Offboarding Process Flow

## New Employee Onboarding Flow

```
  HR SUBMITS NEW HIRE INFO
         │
         ▼
  ┌─────────────────────────────────────────────────────┐
  │              New-Employee.ps1                       │
  └─────────────────────────────────────────────────────┘
         │
         ├── STEP 1: Generate Username
         │          Format: FirstInitial + LastName (e.g. jdoe)
         │          Auto-increments if duplicate (jdoe2)
         │
         ├── STEP 2: Validate Manager in AD
         │          Checks SamAccountName exists
         │
         ├── STEP 3: Create AD Account
         │   ┌──────────────────────────────────────┐
         │   │  SamAccountName  : jdoe              │
         │   │  UPN             : jdoe@corp.local    │
         │   │  OU Path         : OU=IT,OU=Users...  │
         │   │  Password        : Temp (force change)│
         │   │  Home Drive      : H: → \\DC01\homes\ │
         │   │  Manager         : Linked in AD       │
         │   └──────────────────────────────────────┘
         │
         ├── STEP 4: Assign Security Groups
         │   ┌──────────────────────────────────────────────┐
         │   │  IT Dept   → GRP-IT, GRP-VPN, GRP-RDP       │
         │   │  HR Dept   → GRP-HR, GRP-FileShare-Read      │
         │   │  Finance   → GRP-Finance, GRP-FileShare-Read │
         │   │  All Depts → DL-AllStaff (email list)        │
         │   └──────────────────────────────────────────────┘
         │
         ├── STEP 5: Create Home Directory
         │          \\DC01\HomeDirectories\jdoe\
         │          ACL: Full control for user only
         │
         └── STEP 6: Send Welcome Email
                    To: jdoe@corp.local
                    Contains: username, temp password, instructions
```

## Employee Offboarding Flow

```
  HR/MANAGER SUBMITS OFFBOARDING REQUEST
         │
         ▼
  ┌─────────────────────────────────────────────────────┐
  │              Remove-Employee.ps1                    │
  └─────────────────────────────────────────────────────┘
         │
         ├── CONFIRMATION PROMPT (type 'YES' to proceed)
         │
         ├── STEP 1: Disable AD Account
         │          Disable-ADAccount → account immediately inaccessible
         │
         ├── STEP 2: Randomize Password
         │          20-char random password → prevents any re-access
         │
         ├── STEP 3: Strip All Group Memberships
         │          Removes from ALL security + distribution groups
         │          Preserves Domain Users (primary group)
         │
         ├── STEP 4: Update Description
         │          "DISABLED - Resignation - 2026-02-17 - Ticket: HD-0099"
         │
         ├── STEP 5: Move to Disabled OU
         │          OU=Disabled,OU=_CORP,DC=CORP,DC=LOCAL
         │          Kept for 90 days before deletion (audit trail)
         │
         ├── STEP 6: Check Active Sessions
         │          Alert if user currently logged in
         │
         └── STEP 7: Generate & Send Offboarding Report
                    Saved: C:\HelpDesk\Offboarding\jdoe-20260217.txt
                    Emailed to: helpdesk@corp.local
```

## Offboarding Checklist (IT Responsibilities)

```
┌─────────────────────────────────────────────────────────┐
│  IT OFFBOARDING CHECKLIST                               │
├─────────────────────────────────────────────────────────┤
│  [✓] AD account disabled (automated)                    │
│  [✓] Password randomized (automated)                    │
│  [✓] Security groups removed (automated)                │
│  [✓] Account moved to Disabled OU (automated)           │
│  [ ] VPN certificate revoked (manual)                   │
│  [ ] MFA tokens deactivated (manual)                    │
│  [ ] Shared mailbox access removed (manual)             │
│  [ ] File transfer to manager completed (manual)        │
│  [ ] Device wiped and returned to IT (manual)           │
│  [ ] Badge/access card deactivated (manual - Facilities)│
└─────────────────────────────────────────────────────────┘
```
