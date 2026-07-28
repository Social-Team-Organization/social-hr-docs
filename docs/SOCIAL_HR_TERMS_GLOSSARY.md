# Social HR — Product Terms Glossary

English product glossary for **Social HR** (multi-tenant Horilla HRMS SaaS). Written for admins, HR, managers, and employees. Labels match the UI where possible.

**Audience:** tenant admins, HR, managers, employees  
**Scope:** tenant HR app (subdomain) plus a short control-plane overview  
**Tenancy note:** each customer organization is a **tenant** (PostgreSQL schema). There is no Company switcher — one company equals one tenant.

---

## Table of contents

1. [Glossary index (A–Z)](#glossary-index-az)
2. [Platform & tenancy](#1-platform--tenancy)
3. [Global chrome / navbar](#2-global-chrome--navbar)
4. [Dashboard tiles & panels](#3-dashboard-tiles--panels)
5. [Sidebar modules](#4-sidebar-modules)
6. [Settings (gear)](#5-settings-gear--general-settings)
7. [Geofencing / Work Type location policies](#6-geofencing--work-type-location-policies)
8. [Face check-in / re-enroll](#7-face-check-in--re-enroll)
9. [Employee profile tabs](#8-employee-profile-tabs)
10. [Project module — detailed terms](#9-project-module--detailed-terms)

---

## Glossary index (A–Z)

| Term | Section |
|------|---------|
| 360 Feedback | [Performance](#performance-pms) |
| Activity Tracking | [Activity](#activity), [Settings](#attendance-settings) |
| Allowances / Deductions | [Payroll](#payroll) |
| Announcements | [Dashboard](#3-dashboard-tiles--panels) |
| Archive (`is_active`) | [Project](#archive-vs-delete-is_active) |
| Asset Request | [Assets](#assets), [FAB](#quick-action-fab) |
| Attendance Location Check | [Geofencing](#6-geofencing--work-type-location-policies) |
| Attendance Request | [Attendance](#attendance), [FAB](#quick-action-fab) |
| Biometric Devices | [Attendance](#attendance) |
| Bypass geofence | [Geofencing](#key-policy-fields) |
| Check-In / Check-Out | [Navbar](#2-global-chrome--navbar) |
| Company Leaves | [Configuration](#configuration) |
| Control plane | [Platform](#1-platform--tenancy) |
| Desktop / Desktop App | [Navbar](#2-global-chrome--navbar), [Activity](#activity) |
| Encashments & Reimbursements | [Payroll](#payroll) |
| Exit Process | [Offboarding](#offboarding) |
| Face Check-In / Face Registration | [Face](#7-face-check-in--re-enroll) |
| Geofence | [Geofencing](#6-geofencing--work-type-location-policies) |
| Grace Time | [Settings](#attendance-settings) |
| Help Desk / Tickets | [Help Desk](#help-desk) |
| Holidays | [Configuration](#configuration) |
| Hour Account | [Attendance](#attendance) |
| Idle / Review (activity) | [Activity tracking terms](#activity-tracking-policy-terms) |
| Key Results | [Performance](#performance-pms) |
| Leave Allocation Request | [Leave](#leave) |
| Leave Types | [Leave](#leave) |
| Location policy | [Geofencing](#location-policies) |
| Mail Automations / Templates | [Configuration](#configuration) |
| Multiple Approvals | [Configuration](#configuration) |
| Objectives | [Performance](#performance-pms) |
| Office / Remote / Hybrid / Field | [Geofencing](#preset-work-types) |
| Onboarding | [Onboarding](#onboarding) |
| Payslips | [Payroll](#payroll) |
| Pipeline | [Recruitment](#recruitment) |
| Plan / Module entitlement | [Platform](#1-platform--tenancy) |
| Productivity score | [Activity tracking terms](#activity-tracking-policy-terms) |
| Project / Project Stage / Task / Timesheet | [Project](#9-project-module--detailed-terms) |
| Public schema vs tenant schema | [Platform](#1-platform--tenancy) |
| Quick Action FAB | [Navbar](#quick-action-fab) |
| Recruitment Survey / Skill Zone | [Recruitment](#recruitment) |
| Restrict Leaves | [Configuration](#configuration) |
| Rotating Shift / Work Type | [Employee](#employee) |
| Screenshots (activity) | [Activity tracking terms](#activity-tracking-policy-terms) |
| Shift Request / Work Type Request | [Employee](#employee), [FAB](#quick-action-fab) |
| Subdomain | [Platform](#1-platform--tenancy) |
| Tenant | [Platform](#1-platform--tenancy) |
| Work Records | [Attendance](#attendance) |
| Work Type | [Settings](#employee-settings), [Geofencing](#6-geofencing--work-type-location-policies) |

---

## 1. Platform & tenancy

| UI / term | What it is | Why it exists | Policies / settings | Who uses it |
|-----------|------------|---------------|---------------------|-------------|
| **Tenant** | One customer organization. Isolated in its own PostgreSQL **schema**. | Keeps each customer’s HR data separate. | Created via control plane or `provision_tenant`. Plan + module overrides control which apps appear. | Platform staff (create); tenant admins (use HR app) |
| **Schema** | Database namespace for one tenant (`search_path` set per request). | Technical isolation boundary — not a UI label. | Never browse or query across schemas. | Platform / developers |
| **Subdomain** | Hostname that routes to a tenant (e.g. `acme.example.com`). | Users land in the correct company’s HR app. | Domain records on the tenant (`Domain` model). | Everyone logging into that org |
| **Public schema** | Shared “control plane” data: tenants, domains, plans, modules. | Run the SaaS business separately from each customer’s HR data. | Served by public URLconf (marketing + `/dashboard/`). | Platform staff |
| **Control plane** | Staff console on the primary/public domain: Overview, Tenants, Plans, Modules, Audit. | Provision tenants, assign plans, audit staff actions. | Staff login (`is_staff`); not the tenant HR login. | Social HR operators |
| **Tenant HR app** | Full Horilla/Social HR product on the tenant subdomain. | Day-to-day HR for that organization. | Entitlements filter sidebar and block disabled URLs. | Employees, managers, HR, tenant admins |
| **Plan & modules** | Subscription package of enabled HR apps (attendance, leave, payroll, …). | Sell tiers; turn features on/off per tenant. | Plan modules ± per-tenant overrides; sidebar + middleware enforce. | Platform staff; affects all tenant users |
| **Suspended / cancelled tenant** | Tenant status that blocks normal HR login. | Enforce billing / lifecycle. | Entitlement middleware. | Platform staff |
| **Media / uploads** | Files (photos, documents, screenshots, project files). Paths are prefixed with the **current schema name**. | Keep uploads namespaced per tenant. | Local `MEDIA_*` or Cloudflare **R2** / S3-compatible storage via env. | All users who upload |
| **Desktop agent** | Electron **Social HR Desktop App** that sends heartbeats, idle/review segments, and optional screenshots. | Monitor desktop presence for activity; attendance remains the pay source. | **Activity Tracking** policy; JWT APIs under activity. | Employees (run app); managers/HR (review) |

There is **no Company model or company switcher**. Multi-company in upstream Horilla was replaced by multi-tenant schemas.

---

## 2. Global chrome / navbar

Top bar items available across the tenant HR app (visibility depends on permissions and enabled modules).

### Check-In / Check-Out

| | |
|--|--|
| **What** | Navbar control to clock in or clock out for the day. |
| **Why** | Record attendance without opening Attendance screens. |
| **Policies** | **Check In/Check Out** setting; geofence / work-type location policy; optional face check-in; optional **Activity Tracking** “tracking required for clock-in”; IP restriction; biometric devices. |
| **Who** | Employees (self); HR may validate later. |

### Desktop status chip

| | |
|--|--|
| **UI name** | **Desktop** (chip near check-in) |
| **What** | Shows whether the Social HR Desktop app is connected for monitoring. |
| **Why** | Employees see at a glance if activity tracking is live; click opens setup guidance. |
| **Policies** | Activity Tracking policy (`tracking_required_for_clock_in`, screenshots, intervals). |
| **Who** | Employees using desktop monitoring. |

### Languages

| | |
|--|--|
| **What** | Language switcher for the UI. |
| **Why** | Multilingual workforce. |
| **Who** | Any logged-in user. |

### Notifications

| | |
|--|--|
| **UI name** | **All Notifications** (tray / sidebar) |
| **What** | In-app alerts (approvals, mentions, system events). |
| **Why** | Keep users informed without email alone. |
| **Who** | All users. |

### Settings (gear)

| | |
|--|--|
| **What** | Opens **Settings** (`general-settings` and the settings hub). |
| **Why** | Configure org structure, attendance rules, permissions, integrations. |
| **Who** | Admins / users with settings permissions. See [§5](#5-settings-gear--general-settings). |

### Profile

| | |
|--|--|
| **What** | User menu: own profile, account actions. |
| **Why** | Quick access to personal HR data and logout. |
| **Who** | All users. |

### Quick Action FAB

Floating **Quick Action** button (bottom corner). Expands shortcuts:

| FAB item | What it is | Why | Who |
|----------|------------|-----|-----|
| **Create Attendance Request** | Request to add/correct attendance. | Fix missed punches without admin intervention. | Employee; manager/HR approve |
| **Create Leave Request** | Start a leave request. | Fast time-off ask from any page. | Employee |
| **Create Shift Request** | Request a shift change. | Temporary schedule change with approval. | Employee |
| **Create Work Type Request** | Request a temporary work type (e.g. Remote for a day). | WFH / field days; also affects geofence rules for those dates. | Employee |
| **Create Reimbursement** | Open reimbursement / encashment flow. | Expense or leave encashment claims. | Employee; payroll/HR process |
| **Create Asset Request** | Request company asset. | Hardware / equipment requests. | Employee; asset managers approve |
| **Create Ticket** | Open Help Desk ticket. | IT/HR support from anywhere. | Employee |
| **Dashboard Charts** | Jump to dashboard analytics views. | Quick path to charts without sidebar navigation. | Managers / HR (as permitted) |

---

## 3. Dashboard tiles & panels

Home dashboard cards. Exact titles below match UI English.

### Headcount tiles

| UI name | What it is | Why |
|---------|------------|-----|
| **New Joining Today** | Count of employees whose joining date is today. | Spot same-day joiners for onboarding/welcome. |
| **New Joining This Week** | Joiners in the current week. | Weekly hiring pulse. |
| **Total Strength** | Active headcount. | Org size at a glance. |

### People & communication panels

| UI name | What it is | Why | Who |
|---------|------------|-----|-----|
| **Announcements** | Company notices; create from the panel when permitted. | Broadcast policy or news. | HR/admin create; everyone reads |
| **On Leave** | Employees currently on approved leave. | Coverage and planning. | Managers / HR |
| **Employee Work Information** | List/search of employees with incomplete or pending work-info completeness (UI title). Sometimes described informally as employee progress toward complete profiles. | Drive data quality (dept, shift, etc.). | HR / reporting managers |

### Presence

| UI name | What it is | Why |
|---------|------------|-----|
| **Offline Employees** | Employees not currently marked online (session/presence). | See who is away from the system. |
| **Online Employees** | Employees currently online. | Live presence for managers. |

### Approval queues

| UI name | What it is | Why | Who |
|---------|------------|-----|-----|
| **Leave Requests To Approve** | Pending leave approvals. | Clear the leave backlog. | Managers / HR |
| **Leave Allocation Request To Approve** | Pending leave balance allocation requests. | Grant extra leave days with control. | HR / approvers |
| **Work Type Requests To Approve** | Pending work-type changes (e.g. Remote). | Approve temporary location/schedule type. | Managers / HR |
| **Shift Requests To Approve** | Pending shift changes. | Approve temporary shift moves. | Managers / HR |
| **Attendance To Validate** | Attendance rows awaiting validation. | Ensure punches are accurate before payroll. | Managers / HR |
| **Overtime To Approve** | Overtime awaiting approval. | Control OT cost. | Managers / HR |
| **Feedback To Answers** | Performance feedback waiting for answers. | Close 360 / feedback loops. | Employees / managers (PMS) |
| **Asset Requests To Approve** | Pending asset requests. | Allocate equipment responsibly. | Asset admins / managers |

### Recruitment & attendance analytics

| UI name | What it is | Why |
|---------|------------|-----|
| **Recruitment Analytics** | Hiring funnel / recruitment charts. | Track recruiting health. |
| **Hours Chart** | Worked-hours visualization. | Capacity and OT trends. |
| **Hired Candidates** | Recently hired candidates count/list. | Celebrate and track hires. |
| **Candidates Started Onboarding** | Candidates who entered onboarding. | Handoff from recruit to onboard. |
| **Overall Leave** | Leave summary (Today / This Week / This Month / This Year filters). | Leave load over time. |
| **Attendance Analytics** | Attendance charts (Day / Weekly / Monthly / Date range). | Absenteeism and presence trends. |

### Workforce composition charts

| UI name | What it is | Why |
|---------|------------|-----|
| **Gender Chart** | Headcount by gender. | Diversity snapshot (permission-gated). |
| **Department Chart** | Headcount by department. | Org shape. |
| **Employees Chart** | Employee distribution chart. | Workforce overview. |

### Performance status charts

| UI name | What it is | Why |
|---------|------------|-----|
| **Objective Status** | Breakdown of objective statuses. | PMS progress. |
| **Key Result Status** | Breakdown of KR statuses. | Goal execution. |
| **Feedback Status** | Breakdown of feedback cycle statuses. | 360 completion. |

---

## 4. Sidebar modules

Each entry: **UI English name**, plain meaning, purpose, related settings/policies, typical users.

### Recruitment

| UI name | What it is | Why | Policies / related | Who |
|---------|------------|-----|-------------------|-----|
| **Dashboard** | Recruitment KPIs and overview. | Manage hiring at a glance. | Module entitlement | Recruiters / HR |
| **Recruitment Pipeline** | Kanban of candidates by stage. | Move candidates through hiring stages. | Stages; stage managers | Recruiters, stage managers |
| **Recruitment Survey** | Question templates for candidate surveys. | Structured screening. | Survey permissions | Recruiters |
| **Candidates** | Candidate records. | Source of truth for applicants. | Reject reasons (settings) | Recruiters / HR |
| **Interview** | Interview schedules. | Coordinate interviewers. | Interviewer assignment | Interviewers, HR |
| **Recruitment** | Recruitment drives / job openings setup. | Define what you are hiring for. | LinkedIn Integration, Skills (settings) | Recruiters |
| **Open Jobs** | Public/open recruitments list. | Track active openings. | — | Recruiters / candidates (public side as configured) |
| **Stages** | Pipeline stage definitions. | Customize funnel steps. | Stage managers | Recruiters / admins |
| **Skill Zone** | Talent pool / skill-based candidate zones. | Reuse strong candidates later. | — | Recruiters |

Settings under Recruitment: **Candidate Self Tracking**, **Candidate Reject Reason**, **Skills**, **LinkedIn Integration**.

### Onboarding

| UI name | What it is | Why | Who |
|---------|------------|-----|-----|
| **Onboarding view** | Onboarding process board for new hires. | Convert hired candidates into ready employees. | HR / onboarding managers |
| **Candidates view** | Candidates in onboarding context. | Track who still needs onboarding tasks. | HR |

### Employee

| UI name | What it is | Why | Policies / related | Who |
|---------|------------|-----|-------------------|-----|
| **Profile** | Current user’s employee profile. | Self-service personal data. | Profile tabs | Employee |
| **Employees** | Directory / HR employee list. | Hire, edit, organize people. | Departments, job roles, tags, permissions | HR / managers (as permitted) |
| **Document Requests** | Ask employees for documents; track uploads. | Compliance and record keeping. | — | HR / managers |
| **Shift Requests** | Requests to change employee shift. | Temporary schedule changes with approval. | Employee Shift settings | Employees request; managers approve |
| **Work Type Requests** | Requests to change work type for dates. | WFH/field days; drives geofence for those dates. | Work Type location policy | Employees request; managers approve |
| **Rotating Shift Assign** | Assign rotating shift patterns. | Complex shift cycles. | Rotating Shift definitions | HR / managers |
| **Rotating Work Type Assign** | Assign rotating work-type patterns. | Alternating office/remote patterns. | Rotating Work Type | HR / managers |
| **Disciplinary Actions** | Record disciplinary cases. | Formal HR actions trail. | Disciplinary Action Type (settings) | HR |
| **Policies** | Company policy documents for employees. | Publish rules employees must acknowledge/read. | — | HR publish; employees read |
| **Organization Chart** | Visual reporting structure. | See who reports to whom. | Reporting manager on work info | Managers / HR / employees |

### Attendance

| UI name | What it is | Why | Policies / related | Who |
|---------|------------|-----|-------------------|-----|
| **Dashboard** | Attendance analytics for managers. | Spot late/absent trends. | Validation conditions | Managers / HR |
| **Biometric Devices** | Configure biometric hardware (if app installed). | Hardware clock-in. | Biometric Attendance enable | Admins |
| **Attendances** | All attendance records. | Source of truth for days worked. | Break point, grace, validate | HR / managers |
| **Attendance Requests** | Employee-submitted attendance corrections. | Self-service fix with approval. | — | Employees; approvers |
| **Hour Account** | Overtime / hour bank by year. | Track OT balances. | OT approve queue | HR / managers / employees |
| **Work Records** | Day-level work record matrix. | Payroll-oriented daily status. | — | HR / managers |
| **Attendance Activities** | Raw in/out activity log. | Audit punch trail. | — | HR |
| **Late Come Early Out** | Late arrival / early leave tracking. | Discipline and grace handling. | **Track Late Come & Early Out** setting | HR / managers |
| **My Attendances** | Employee’s own attendance. | Self-service history. | — | Employee |

### Activity

| UI name | What it is | Why | Policies / related | Who |
|---------|------------|-----|-------------------|-----|
| **My Activity** | Your desktop activity for a day (active / idle / review, screenshots, score). | Transparency for the employee. | Activity Tracking policy | Employee |
| **Team Activity** | Team members’ activity (managers / permitted users). | Supervise presence; decide Review segments. | Same policy; manager decisions Paid / Unpaid / Meeting | Managers / HR |
| **Desktop App** | Setup and diagnostics for the Electron agent. | Install/connect monitoring. | JWT heartbeat/screenshot APIs | Employee |

#### Activity tracking policy terms

| Term | What it is | Why |
|------|------------|-----|
| **Heartbeat** | Periodic ping from the desktop app (keyboard/mouse counts, idle seconds, app/window). | Build a timeline of presence. |
| **Idle** | Time classified idle after `idle_after_seconds` without input. | Flag inactivity; **does not auto-deduct pay**. |
| **Review** / **Review required** | Longer idle (`review_after_seconds`); manager must classify. | Human judgment for long gaps. |
| **Manager decision** | On a review segment: **Paid**, **Unpaid**, or **Meeting**. | Resolve whether time counts. |
| **Screenshots** | Optional periodic captures (retention days; tenant media/R2). | Visual audit trail when enabled. |
| **Productivity score** | Derived score from active vs idle/review and input activity. | Relative activity indicator — not a payslip field. |
| **Tracking required for clock-in** | Policy toggle: employees should use the desktop app when clocking in. | Tie presence monitoring to attendance start. |

Configured under Settings → Attendance → **Activity Tracking**.

### Leave

| UI name | What it is | Why | Policies / related | Who |
|---------|------------|-----|-------------------|-----|
| **Dashboard** | Leave analytics. | Capacity planning. | — | Managers / HR |
| **My Leave Requests** | Employee’s own leave requests. | Self-service time off. | Leave types, restrictions | Employee |
| **Leave Requests** | All leave requests (approver view). | Approve/reject leave. | Multiple Approvals | Managers / HR |
| **Leave Types** | Categories (annual, sick, …) and rules. | Standardize balances and eligibility. | Compensatory Leave setting | HR |
| **Assigned Leave** | Leave balances assigned to employees. | Entitlement tracking. | — | HR |
| **Leave Allocation Request** | Request extra leave allocation. | Exception grants. | Approval queue | Employees / HR |
| **Compensatory Leave Requests** | Comp-off requests (when enabled). | Convert OT to leave. | Compensatory Leave settings | Employees / HR |

*(Holidays / Company Leaves / Restrict Leaves also appear under [Configuration](#configuration); Leave sidebar may list them depending on permissions.)*

### Payroll

| UI name | What it is | Why | Policies / related | Who |
|---------|------------|-----|-------------------|-----|
| **Dashboard** | Payroll overview. | Period health check. | — | Payroll / HR |
| **Contract** | Employee salary contracts. | Legal/pay basis. | — | Payroll / HR |
| **Allowances** | Earnings components. | Structure gross pay. | — | Payroll |
| **Deductions** | Deduction components. | Structure net pay. | — | Payroll |
| **Payslips** | Generated payslips. | Deliver pay statements. | **Payslip Auto Generation** | Payroll; employees view own |
| **Loan / Advanced Salary** | Loans and salary advances. | Recoverable payouts. | — | Payroll / HR |
| **Encashments & Reimbursements** | Leave encashment and expense reimbursements. | Non-salary payouts. | — | Employees request; payroll process |
| **Federal Tax** | Federal tax configuration (where used). | Statutory withholding. | — | Payroll / admins |

### Performance (PMS)

| UI name | What it is | Why | Policies / related | Who |
|---------|------------|-----|-------------------|-----|
| **Dashboard** | PMS overview. | Performance health. | — | Managers / HR |
| **Objectives** | Goals assigned to people. | Align work to outcomes. | Periods | Managers / employees |
| **360 Feedback** | Multi-rater feedback cycles. | Holistic performance input. | Question Template | Employees / managers |
| **Meetings** | Performance / 1:1 meetings. | Structured conversations. | — | Managers / employees |
| **Key Results** | Measurable results under objectives. | Track progress to goals. | — | Managers / employees |
| **Employee Bonus Point** | Bonus points ledger. | Reward points tied to performance rules. | **Bonus Point Setting** | HR / managers |
| **Period** | Review periods (quarters, cycles). | Time-box goals and feedback. | — | HR / admins |
| **Question Template** | Templates for feedback questions. | Reusable 360 content. | — | HR |

### Offboarding

| UI name | What it is | Why | Who |
|---------|------------|-----|-----|
| **Dashboard** | Exit process overview. | Track leavers. | HR |
| **Exit Process** | Structured offboarding checklist/stages. | Consistent exits (assets, access, knowledge). | HR / managers |
| **Resignation Letters** | Resignation submissions. | Formal resignation intake. | Employees / HR |

### Assets

| UI name | What it is | Why | Who |
|---------|------------|-----|-----|
| **Dashboard** | Asset KPIs. | Stock and allocation health. | Asset admins |
| **Asset View** | Categories and assets catalog. | Inventory. | Asset admins |
| **Asset Batches** | Lots / batches of assets. | Bulk procurement tracking. | Asset admins |
| **Request and Allocation** | Employee requests and allocations. | Issue and return assets. | Employees request; admins allocate |
| **Asset History** | Assignment history. | Audit trail. | Asset admins |

### Help Desk

| UI name | What it is | Why | Policies / related | Who |
|---------|------------|-----|-------------------|-----|
| **FAQs** | Self-help articles. | Deflect common questions. | — | All users |
| **Tickets** | Support tickets. | Track issues to resolution. | Ticket Type, Helpdesk Tags, Department Managers | Employees create; agents resolve |

### Project

See the full [Project module](#9-project-module--detailed-terms) section. Menu items:

| UI name | Purpose (short) |
|---------|-----------------|
| **Dashboard** | Project/task metrics for managers. |
| **Projects** | Create and manage projects, stages, members. |
| **Tasks** | Cross-project task list / kanban work. |
| **Timesheet** | Log hours against project/task (**status is progress, not approval**). |

### Configuration

Sidebar **Configuration** (not the gear Settings hub):

| UI name | What it is | Why | Who |
|---------|------------|-----|-----|
| **Multiple Approvals** | Multi-step approval chains (esp. leave). | Require sequential approvers. | Admins / HR |
| **Mail Templates** | Reusable email body templates. | Consistent notifications. | Admins |
| **Mail Automations** | Event-triggered emails. | Automate outreach on HR events. | Admins |
| **Holidays** | Public/org holidays calendar. | Block or inform leave/attendance. | HR / admins |
| **Company Leaves** | Recurring company-wide leave days (e.g. every Friday pattern — product “company leave” concept). | Org-wide non-working patterns. | HR / admins |
| **Restrict Leaves** | Date ranges / rules that restrict leave applications. | Control peak-season leave. | HR / admins |

---

## 5. Settings (gear / general settings)

Opened from the navbar gear. Grouped as in `templates/settings.html`.

### General

| UI name | Purpose | Key knobs |
|---------|---------|-----------|
| **General Settings** | Org-wide basics (branding/time zone style settings as implemented). | Tenant defaults |
| **Employee Permission** | Assign Django permissions to employees. | Permission matrix |
| **Accessibility Restriction** | Feature accessibility flags (e.g. who can see certain charts). | Accessibility features |
| **User Group** | Permission groups. | Groups membership |
| **Date & Time Format** | Display formats. | Date/time patterns |
| **History Tags** | Tags for audit/history. | Tag catalog |
| **Mail Server** | SMTP / outbound mail (or **Outlook Mail** if Outlook app installed). | Primary mail config |
| **Gdrive Backup** | Google Drive backup (if installed). | Backup credentials |
| **LDAP Configuration** | LDAP/AD sync (if installed). | LDAP bind settings |

### Base

| UI name | Purpose | Key knobs |
|---------|---------|-----------|
| **Department** | Org departments. | Department list |
| **Job Positions** | Positions under departments. | Positions |
| **Job Role** | Roles linked to positions. | Roles |

### Recruitment (settings)

| UI name | Purpose |
|---------|---------|
| **Candidate Self Tracking** | Let candidates track application status. |
| **Candidate Reject Reason** | Standard reject reasons. |
| **Skills** | Skill catalog for recruitment. |
| **LinkedIn Integration** | LinkedIn job/candidate integration. |

### Employee (settings)

| UI name | Purpose | Key knobs |
|---------|---------|-----------|
| **Work Type** | Define work types (**Office**, **Remote**, etc.) including **Location policy**. | `location_policy` |
| **Rotating Work Type** | Rotating work-type patterns. | Pattern definitions |
| **Employee Shift** | Shift definitions (start/end). | Shift times |
| **Rotating Shift** | Rotating shift patterns. | Pattern definitions |
| **Employee Shift Schedule** | Schedules for shifts. | Schedule rules |
| **Employee Type** | Employment types (full-time, contract, …). | Types |
| **Disciplinary Action Type** | Types of disciplinary actions. | Action catalog |
| **Employee Tags** | Tags on employees. | Tag catalog |

### Attendance (settings)

| UI name | Purpose | Key knobs |
|---------|---------|-----------|
| **Track Late Come & Early Out** | Enable late/early tracking feature. | On/off tracking |
| **Attendance Break Point** | Validation condition thresholds. | Break/validation rules |
| **Check In/Check Out** | Enable navbar / web check-in-out. | Feature enable |
| **Face Check-In** | Browser webcam face verification for clock-in. | Enable/disable face check-in |
| **Face Re-enroll Requests** | Admin queue for employees who need face re-enrollment. | Approve re-enroll |
| **Grace Time** | Allowed late minutes before penalty. | Grace duration |
| **Biometric Attendance** | Enable biometric attendance integration. | Enable flag |
| **IP Restriction** | Allowed IPs for attendance actions. | IP allowlist |
| **Geo & Face Config** | Geofence circles + face-related geo config. | Lat/long/radius; start geofence |
| **Activity Tracking** | Desktop monitoring policy. | Idle/review thresholds, screenshot interval/retention, tracking required for clock-in |

### Leave (settings)

| UI name | Purpose |
|---------|---------|
| **Restrictions** | Past-leave / leave application restrictions. |
| **Compensatory Leave** | Comp-off from overtime settings. |

### Payroll (settings)

| UI name | Purpose |
|---------|---------|
| **Payslip Auto Generation** | Schedule/auto-create payslips. |

### Performance (settings)

| UI name | Purpose |
|---------|---------|
| **Bonus Point Setting** | Rules for awarding bonus points. |

### Help Desk (settings)

| UI name | Purpose |
|---------|---------|
| **Department Managers** | Map departments to help-desk managers. |
| **Ticket Type** | Ticket categories. |
| **Helpdesk Tags** | Tags on tickets. |

---

## 6. Geofencing / Work Type location policies

### Concepts

| Term | What it is | Why |
|------|------------|-----|
| **Geofence** | Circle (latitude, longitude, radius in meters) configured under **Geo & Face Config**. Must be **started** to enforce. | Ensure office workers clock in on site. |
| **Work Type** | Employee’s mode of work (default on work information, or temporary via **Work Type Request**). | Different roles need different location rules. |
| **Location policy** | Per work type: how clock-in behaves when geofencing is active. | One policy engine instead of hard-coding “remote vs office”. |
| **Attendance Location Check** | Audit record of a clock-in/out location evaluation (coords, distance, policy, pass/fail message). | Compliance and troubleshooting. |

### Preset work types

Seeded presets (admins may still edit policies):

| Work Type | Default location policy | Typical meaning |
|-----------|-------------------------|-----------------|
| **Office** | Require inside office geofence | Must be at office to clock in |
| **Remote** | Allow clock-in from anywhere | WFH |
| **Hybrid** | Require inside office geofence (default; customize as needed) | Mix of office/remote — often combined with weekday overrides |
| **Field** | Allow clock-in from anywhere | Field sales / site visits |

### Location policies

| Policy (UI wording) | Code | Behavior |
|---------------------|------|----------|
| **Require inside office geofence** | `require_inside_geofence` | Clock-in allowed only inside the active geofence (unless bypass). |
| **Allow clock-in from anywhere** | `allow_anywhere` | No geofence requirement. |
| **Block clock-in** | `block_clock_in` | Clock-in blocked for that work type while geofence is started. |

### Key policy fields

| Field / UI | What it does | Who sets it |
|------------|--------------|-------------|
| **Location policy** on Work Type | Default rule for that type. | Admin (Settings → Work Type) |
| **Bypass geofence** on employee work information | Employee may clock from anywhere even if type requires office. | HR / admin |
| **Employee Weekday Work Type** | Per-weekday override (e.g. Friday = Remote). | HR on employee work info |
| **Work Type Request** (approved) | Temporary type for date range — overrides default for those dates (including same-day WFH). | Employee requests; manager approves |
| **Geo & Face Config** | Define and start/stop geofence. | Admin |

**Important:** Attendance remains the source of pay. Geofencing only gates whether clock-in is allowed based on location policy.

---

## 7. Face check-in / re-enroll

| UI name | What it is | Why | Who |
|---------|------------|-----|-----|
| **Face Registration** | Profile tab / flow to enroll face templates for the employee. | Bind a biometric face to the person for web check-in. | Employee (self); HR may assist |
| **Face Check-In** | Settings toggle + navbar/browser webcam check-in path. | Verify identity at clock-in without hardware device. | Admin enables; employees use |
| **Face Re-enroll Requests** | Admin list of requests to reset/re-capture face data. | Handle glasses, appearance change, or failed matches. | Employee requests; admin approves |

Related: **Geo & Face Config** for combined geo/face setup. Requires the face-detection app to be installed and entitled.

---

## 8. Employee profile tabs

Labels differ slightly between **My Profile** and **Employee individual view**. Common tabs:

| UI name | What it is | Why | Who |
|---------|------------|-----|-----|
| **Personal Info** / **Personal Information** / **About** | Name, contact, demographics, personal details. | Identity and emergency data. | Employee / HR |
| **Bank Info** / **Bank Information** | Bank account for salary. | Payroll disbursement. | Employee / HR / payroll |
| **Work Type & Shift** | Default work type, shift, **bypass geofence**, weekday work types. | Schedule and location rules. | HR; employee may view |
| **Attendance** | Attendance history on the profile. | Quick manager view. | Managers / HR / employee |
| **Face Registration** | Enroll face for face check-in. | Biometric web attendance. | Employee |
| **Leave** | Leave balances and requests on profile. | Self-service leave snapshot. | Employee / HR |
| **Payroll** | Payslip/contract snapshot on profile. | Pay transparency (as permitted). | Employee / payroll |
| **Allowance & Deduction** | Assigned allowances and deductions. | Explain gross-to-net components. | Payroll / HR |
| **Penalty Account** | Penalties (e.g. late-related) tied to the employee. | Track disciplinary pay impacts. | HR |
| **Documents** | Employee documents and requests. | Compliance files. | Employee / HR |
| **History** | Change history. | Audit. | HR |
| **Assets** | Assets assigned to the employee. | Custody. | Employee / asset admin |
| **Performance** | PMS snapshot on profile. | Goals/feedback context. | Managers / employee |
| **Groups & Permissions** | Auth groups and permissions. | Access control. | Admins |
| **Note** | Free-form HR notes. | Internal comments. | HR |
| **Mail Log** | Emails sent regarding the employee. | Communication audit. | HR |
| **Bonus Points** | PMS bonus points on profile. | Rewards visibility. | Managers / employee |

Edit forms often use tabs **Personal Info** and **Bank Info** explicitly.

---

## 9. Project module — detailed terms

### Menu purposes

| Menu | Purpose |
|------|---------|
| **Dashboard** | High-level project and task metrics for managers, reporting managers, and project/task managers. |
| **Projects** | Create projects, set managers/members, dates, status, stages (kanban columns), archive. |
| **Tasks** | Manage tasks across projects: assignees, stage, status, files. |
| **Timesheet** | Employees log **Hours Spent** on a project/task for a date. Status means work progress, **not** an approval workflow. |

### Core entities

| Term | UI / field | What it is | Why |
|------|------------|------------|-----|
| **Project** | **Name**, description, dates, file, status | A body of work with members and stages. | Organize delivery and time logging. |
| **Project Manager** | **Project Managers** (M2M) | Employees who lead the project. | Elevated access to manage project/tasks/timesheets. |
| **Project Member** | **Project Members** (M2M) | Contributors on the project. | Can work tasks and log time when assigned. |
| **Project Stage** | Stage **Title**, sequence | Kanban column for tasks within a project. | Visual workflow. |
| **Todo** (default stage) | Auto-created **Todo** stage on new project | Default first stage (`sequence=1`, not end stage). | Every project starts with a backlog column. |
| **End stage** | **Is end stage** | Exactly one end stage allowed per project; typically where finished work lands. | Clear “done” column. |
| **Task** | **Title**, stage, dates, file, status | Unit of work on a project. | Execution tracking. |
| **Task Manager** | **Task Managers** | People responsible for the task. | Task-level ownership. |
| **Task Member** | **Task Members** | People doing the task. | Assignment. |
| **Timesheet** | **Project**, **Task**, **Employee**, **Date**, **Hours Spent**, **Status**, description | Time entry for a day. | Effort tracking (not payroll attendance). |

### Project statuses

| Code | UI label | Meaning |
|------|----------|---------|
| `new` | **New** | Just created / not started in earnest. |
| `in_progress` | **In Progress** | Active work. |
| `completed` | **Completed** | Finished successfully. |
| `on_hold` | **On Hold** | Paused. |
| `cancelled` | **Cancelled** | Abandoned. |
| `expired` | **Expired** | Past relevance / date-driven expiry semantics in product. |

### Task statuses

| Code | UI label | Meaning |
|------|----------|---------|
| `to_do` | **To Do** | Not started (default). |
| `in_progress` | **In Progress** | Being worked. |
| `completed` | **Completed** | Done. |
| `expired` | **Expired** | Past end date (system may set when end date is before today). |

Task end date must fall within the project’s start/end dates when those are set.

### Timesheet statuses (not approval)

| Code | UI label | Meaning |
|------|----------|---------|
| `in_Progress` | **In Progress** | Entry still open / work in progress. |
| `completed` | **Completed** | Entry finished. |

There is **no timesheet approval state** in this product. Managers do not “approve timesheets” the way they approve leave; status only reflects progress of the time entry.

**Hours Spent** must be `HH:MM`. Description is required. Date cannot be in the future. Employee must belong to the project (manager/member) and, if a task is set, to that task’s managers/members (or project managers/members).

### Archive vs delete (`is_active`)

| Action | What it does | When to use |
|--------|--------------|-------------|
| **Archive** / **Un-Archive** | Toggles `is_active` (soft hide). UI shows Archive when active, Un-Archive when inactive. | Keep history but remove from active lists. |
| **Delete** | Hard delete of the record (with confirm). | Remove mistaken or unwanted records permanently. |

Applies to projects and tasks via archive actions in the UI.

### Permissions overview (plain English)

Access is a mix of Django permissions and membership roles:

| You can typically… | If you are… |
|--------------------|-------------|
| See **Project** menu at all | In project app perms, **or** project/task manager/member on any item |
| Open **Dashboard** | `view_project` permission, reporting manager, project manager, or task manager |
| Open **Projects** | `view_project`, or any project/task manager or member role |
| Open **Tasks** | `view_task`, or project/task manager or member |
| Open **Timesheet** | `view_timesheet`, or project/task manager or member |
| Manage broadly | Users with project add/change/delete permissions (admins/HR-style roles) |
| Work day-to-day | Project/Task **Managers** and **Members** on the specific records |

Exact buttons still depend on object-level checks in views; membership is the practical key for most employees.

### Project terms quick table

| Term | One-line definition |
|------|---------------------|
| Project | Named initiative with dates, people, stages, status |
| Project Manager | Lead with management access |
| Project Member | Contributor on the project |
| Project Stage | Kanban column; optional single **end stage** |
| Todo stage | Default first stage created with the project |
| Task | Work item in a stage with its own managers/members/status |
| Timesheet | Hours logged by an employee on a project/task for a date |
| Archive | Soft-deactivate via `is_active` |
| Timesheet status | In Progress / Completed only — **not** an approval flag |

---

## Related docs

- [CONTROL_PLANE.md](./CONTROL_PLANE.md) — public schema staff console, plans, entitlements  
- Repository `AGENTS.md` — tenancy hard rules for developers  

---

*Labels verified against sidebar modules, `templates/settings.html`, dashboard templates, navbar/FAB templates, and models for project, activity, geofencing, and employee work information.*
