# Features

Detailed descriptions of Social HR's major capabilities — especially those that differentiate the product from standard HR platforms.

Each feature section covers: **what it is**, **who uses it**, **typical workflow**, **benefits**, and **limitations**.

For UI label definitions, see the [Glossary](./GLOSSARY.md).

> **At a glance — Social HR differentiators**
>
> | Feature | [Plan](./PLANS.md) | Pay impact |
> |---------|------|------------|
> | [Workspace isolation](#multi-tenant-workspace-isolation) | All | — |
> | [Attendance & check-in](#attendance-and-check-in) | All | **Authoritative pay source** |
> | [Geofencing](#geofencing-and-work-type-location-policies) | Enterprise | Gates check-in only |
> | [Face check-in](#face-check-in) | All | Gates check-in only |
> | [Activity tracking](#activity-tracking-desktop-monitoring) | Standard+ | Oversight only — no auto pay change |
> | [Arabic-first UI](#internationalization-arabic-first) | All | — |

Module catalog: [Modules](./MODULES.md).

---

## Multi-tenant workspace isolation

![Each customer organization has its own isolated workspace — data never mixes](./assets/tenant-isolation.png)

### What it is

Each customer organization operates in a fully isolated [HR workspace](./GLOSSARY.md#platform-terms) with its own web address, user accounts, and data. No customer can access another customer's information.

### Who uses it

All users — this is the foundational architecture, not an optional feature.

### Typical workflow

1. [Platform operator](./ROLES_AND_PERMISSIONS.md#platform-operator) [provisions](./GLOSSARY.md#platform-terms) workspace with [subdomain](./GLOSSARY.md#platform-terms)
2. Customer users log in at their unique address
3. All data, files, and settings remain within that workspace
4. Platform staff manage metadata from the [control plane](./PLATFORM.md) only

### Benefits

- Strong data privacy and compliance posture
- Clear mental model: one organization = one workspace
- No confusion from company switchers or shared databases

### Limitations

- Each workspace is one organization — no multi-company within a single workspace
- Cross-customer analytics are not available
- Users need separate accounts if they work for multiple Social HR customers

Policy: [Data isolation](./POLICIES.md#data-isolation-and-privacy). Rationale: [Design Decisions — Isolated workspace](./DESIGN_DECISIONS.md#isolated-workspace-per-customer).

---

## Attendance and check-in

![Employees can check in via web, mobile, or face verification — all methods feed attendance records](./assets/attendance-checkin.png)

### What it is

The system for recording when employees start and stop work. [Attendance](./GLOSSARY.md#attendance-and-pay-terms) is the **authoritative source for pay hours** — all [payroll](./FEATURES.md#payroll) calculations derive from validated attendance records.

### Who uses it

| Role | Actions |
|------|---------|
| **Employees** | Check in and out daily via navbar or attendance screens |
| **Managers** | Validate attendance before payroll runs |
| **HR administrators** | Configure rules, grace times, IP restrictions |
| **Payroll specialists** | Rely on validated records for payslip generation |

### Typical workflow

1. Employee clicks **Check-In** in the navbar when starting work
2. System may apply [location](#geofencing-and-work-type-location-policies), [face](#face-check-in), or [activity](#activity-tracking-desktop-monitoring) policies before recording
3. Attendance row is created with timestamp
4. Employee clicks **Check-Out** when finishing
5. Managers review flagged records in the "Attendance To Validate" queue
6. Validated records feed the [work records](./GLOSSARY.md#attendance-and-pay-terms) matrix used by payroll

Daily flow: [How It Works — Daily work flow](./HOW_IT_WORKS.md#daily-work-flow).

### Benefits

- Single source of truth for worked hours
- Multiple clock-in methods (web, face, biometric, desktop app)
- Manager validation workflow before payroll
- Correction requests for missed or incorrect punches

### Limitations

- Activity monitoring idle time does not automatically reduce attendance hours
- [Project timesheet](./MODULES.md#projects) hours are separate and do not feed payroll
- Validation is a workflow step — not all organizations may require it before every payroll run

Module: [Attendance](./MODULES.md#attendance). Policy: [Attendance policies](./POLICIES.md#attendance).

---

## Geofencing and work-type location policies

![Office geofence requires on-site check-in; remote work types allow check-in from anywhere](./assets/geofencing.png)

### What it is

Location enforcement at clock-in based on where an employee is allowed to work, determined by their **[work type](./GLOSSARY.md#workforce-visibility-terms)** (Office, Remote, Hybrid, Field) and an optional office [geofence](./GLOSSARY.md#workforce-visibility-terms) circle.

### Who uses it

| Role | Actions |
|------|---------|
| **HR administrators** | Configure office coordinates, radius, and work type policies |
| **Employees** | Experience location checks at check-in |
| **Managers** | Approve [work type requests](./GLOSSARY.md#workforce-visibility-terms) for temporary remote days |

### Typical workflow

1. HR admin sets office geofence (latitude, longitude, radius) and activates it
2. Each work type has a [location policy](./GLOSSARY.md#workforce-visibility-terms):
   - **Require inside geofence** — must be within the office circle
   - **Allow anywhere** — no location restriction
   - **Block clock-in** — cannot clock in at all
3. When employee checks in, the system determines their **[effective work type](./GLOSSARY.md#workforce-visibility-terms)** for that day (see [How It Works — Work type resolution](./HOW_IT_WORKS.md#work-type-resolution))
4. Location policy is applied; check-in succeeds or fails with an explanation
5. Every evaluation is logged for audit

**Preset defaults:**

| Work type | Default location policy |
|-----------|------------------------|
| Office | Require inside geofence |
| Remote | Allow anywhere |
| Hybrid | Require inside geofence |
| Field | Allow anywhere |

HR admins can customize policies on any work type.

### Benefits

- Flexible rules — not just "remote on/off"
- Temporary overrides via work type requests (e.g., "work from home Friday")
- Per-employee [bypass geofence](./GLOSSARY.md#workforce-visibility-terms) for executives or special cases
- Full audit trail of location decisions

### Limitations

- Requires [Enterprise plan](./PLANS.md#enterprise) (or override) and HR admin configuration
- Geofence must be activated — inactive geofence allows all check-ins
- Requires device location permission from the employee's browser or desktop app
- Geofencing gates clock-in only; it does not calculate pay hours

Scenario: [Use Cases — Configure office geofencing](./USE_CASES.md#configure-office-geofencing). Module: [Geofencing](./MODULES.md#geofencing).

---

## Face check-in

![Face registration (3 captures) then live verification at each check-in — templates stored, not photos](./assets/face-checkin.png)

### What it is

Optional webcam identity verification before attendance is recorded. Employees enroll their face once; subsequent check-ins compare a live capture against enrolled templates.

### Who uses it

| Role | Actions |
|------|---------|
| **Employees** | Enroll via profile Face Registration tab; verify at check-in |
| **HR administrators** | Enable/disable and optionally enforce face verification |
| **Managers** | Handle re-enrollment requests when verification fails |

### Typical workflow

1. HR admin enables Face Check-In in settings
2. Employee completes [face registration](./GLOSSARY.md#workforce-visibility-terms) (minimum three successful captures)
3. At check-in, employee's webcam captures frames
4. System compares against enrolled templates
5. Match above threshold → standard check-in proceeds
6. Failed match → employee can retry or submit a re-enrollment request

### Benefits

- Reduces buddy-punching and proxy clock-in
- Privacy-conscious: stores mathematical face templates, not photos
- Optional — can be enabled without enforcing on every check-in
- Available on all plans including Trial

### Limitations

- Requires webcam access and adequate lighting
- Separate infrastructure needed for face processing (managed by platform operators)
- Enrollment requires minimum three usable templates
- Does not replace attendance — it gates the clock-in action only

Scenario: [Use Cases — Enable face check-in](./USE_CASES.md#enable-face-check-in). Module: [Face Check-In](./MODULES.md#face-check-in).

---

## Activity tracking (desktop monitoring)

![Desktop app sends heartbeats; managers review idle segments and classify as Paid, Unpaid, or Meeting](./assets/activity-monitoring.png)

### What it is

The Social HR Desktop app monitors employee presence at their computer — keyboard and mouse activity, idle time, active window, and optional screenshots. Managers review activity timelines and classify extended idle periods.

### Who uses it

| Role | Actions |
|------|---------|
| **Employees** | Install and run the desktop app while working |
| **Managers** | Review team activity, classify [review segments](./GLOSSARY.md#workforce-visibility-terms) |
| **HR administrators** | Configure idle thresholds, screenshot settings, retention |

### Typical workflow

1. Employee installs Social HR Desktop and logs in
2. At check-in, the app begins sending periodic [heartbeats](./GLOSSARY.md#workforce-visibility-terms)
3. System classifies time into segments:
   - **Active** — keyboard/mouse input detected
   - **Idle** — no input for configured threshold (default: 5 minutes)
   - **Review required** — idle exceeds review threshold (default: 15 minutes)
4. Optional screenshots captured at intervals when enabled
5. Manager sees review segments and decides: **Paid**, **Unpaid**, or **Meeting**
6. [Productivity score](./GLOSSARY.md#workforce-visibility-terms) calculated for informational display
7. At check-out, activity session closes

> **Pay authority:** Activity monitoring does **not** automatically change [attendance](./GLOSSARY.md#attendance-and-pay-terms) or payroll. Managers classify ambiguous idle time; [attendance remains the pay source](./DESIGN_DECISIONS.md#attendance-drives-pay-activity-provides-oversight).

### Benefits

- Visibility into remote and hybrid work patterns
- Manager judgment on ambiguous idle time (lunch vs. unproductive)
- Optional screenshots for compliance or coaching
- Links to attendance session for context

### Limitations

- Does not automatically change payroll
- Productivity score is informational only, not on payslips
- Requires desktop app installation and employee cooperation
- Screenshot retention is configurable (default 30 days)
- Policy can encourage desktop app at clock-in but enforcement is guidance-level

Scenario: [Use Cases — Classify idle activity segment](./USE_CASES.md#classify-a-long-idle-activity-segment). Module: [Activity Tracking](./MODULES.md#activity-tracking).

---

## Leave management

![Leave request submitted → manager approves → balance updated → reflected in attendance and payroll](./assets/leave-workflow.png)

### What it is

Complete time-off management — leave types, balances, requests, multi-step approvals, and integration with attendance and payroll.

### Who uses it

| Role | Actions |
|------|---------|
| **Employees** | Request leave via quick action or Leave module |
| **Managers** | Approve or reject from dashboard queue |
| **HR administrators** | Configure types, balances, holidays, restrictions |

### Typical workflow

1. HR defines leave types (annual, sick, unpaid, etc.) with rules
2. Employees receive allocated balances
3. Employee submits leave request with dates and type
4. Approval workflow runs (single or multi-step via Configuration)
5. Approved leave deducts balance and appears on dashboard "On Leave"
6. Leave days reflected in attendance work records
7. Payroll uses leave data in payslip calculations

Chain: [How It Works — Leave → attendance → payroll](./HOW_IT_WORKS.md#leave--attendance--payroll-chain).

### Benefits

- Configurable approval chains
- Compensatory leave from overtime (when enabled)
- Holiday and company leave integration
- Dashboard visibility of who is out today

### Limitations

- Restrict leave rules can block applications in date ranges — HR must configure carefully

Module: [Leave](./MODULES.md#leave). Policy: [Leave policies](./POLICIES.md#leave).

---

## Payroll

![Validated attendance and contracts flow into payslip generation](./assets/payroll-cycle.png)

### What it is

Compensation processing — employment contracts, payslip generation, allowances, deductions, loans, and reimbursements.

### Who uses it

| Role | Actions |
|------|---------|
| **Payroll specialists** | Run monthly payslip generation, manage contracts |
| **HR administrators** | Configure tax and deduction rules |
| **Employees** | View own payslips on profile (when permitted) |

### Typical workflow

1. HR sets up employment contracts with salary structures
2. [Attendance](./GLOSSARY.md#attendance-and-pay-terms) is validated for the pay period
3. Payroll specialist generates payslips (manually or via scheduled job)
4. System applies allowances, deductions, leave adjustments, and tax
5. Employees access payslips on their profile Payroll tab
6. Encashments and reimbursements processed through Payroll module or quick actions

### Benefits

- Integrated with attendance and leave — no duplicate data entry
- Scheduled payslip generation option
- Reimbursement workflow via quick action

### Limitations

- Requires validated attendance for accurate calculations
- Automated payslip scheduling depends on platform background job configuration
- No external accounting system integration documented as standard

Scenario: [Use Cases — Monthly payslip run](./USE_CASES.md#monthly-payslip-run). Module: [Payroll](./MODULES.md#payroll).

---

## Recruitment and onboarding

![Recruitment pipeline → onboarding tasks → complete employee record](./assets/recruitment-onboarding.png)

### What it is

End-to-end hiring: job openings, candidate pipeline, interviews, and structured new-hire onboarding boards.

### Who uses it

| Role | Actions |
|------|---------|
| **Recruiters** | Manage pipeline, schedule interviews |
| **Hiring managers** | Review candidates, participate in interviews |
| **HR administrators** | Configure stages, surveys, skill zones |
| **New hires** | Complete onboarding tasks |

### Typical workflow

1. Create recruitment drive with pipeline stages
2. Add candidates; move through kanban pipeline
3. Schedule interviews; record outcomes
4. Hire candidate → moves to onboarding board
5. Complete onboarding tasks → employee record created for day-to-day HR

Lifecycle: [How It Works — Hire to retire](./HOW_IT_WORKS.md#hire-to-retire-lifecycle).

### Benefits

- Seamless hire-to-employee transition
- Dashboard analytics: recruitment pipeline, hired candidates, onboarding progress
- Skill zones and surveys for structured assessment

### Limitations

- Available on [Standard and Enterprise](./PLANS.md#standard) plans only (not default Trial)
- External job board integrations depend on configuration

Modules: [Recruitment](./MODULES.md#recruitment), [Onboarding](./MODULES.md#onboarding).

---

## Performance management (PMS)

### What it is

Goals, key results, 360-degree feedback, and performance review cycles.

### Who uses it

- **Employees** — set and track objectives and key results
- **Managers** — review progress, conduct feedback cycles
- **HR administrators** — configure periods, question templates, bonus points

### Key capabilities

- Objectives and key results (OKRs)
- 360 feedback with customizable question templates
- Performance meetings and review periods
- Bonus points ledger
- Dashboard charts for objective and feedback status

Module: [Performance (PMS)](./MODULES.md#performance-pms).

---

## Quick actions

### What it is

A floating action button (FAB) in the navbar providing shortcuts to common employee requests.

### Available shortcuts

- Attendance request (correction)
- Leave request
- Shift request
- Work type request
- Reimbursement
- Asset request
- Helpdesk ticket
- Dashboard chart navigation

### Benefits

Reduces navigation friction for everyday employee self-service tasks. Scenario: [Use Cases — Request leave](./USE_CASES.md#request-leave-and-track-balance).

---

## Dashboard

### What it is

Role-aware home screen with tiles, approval queues, and analytics charts.

### What users see (based on role and permissions)

- Headcount and announcements
- Who is on leave today
- Employee presence (online/offline)
- Approval queues: leave, attendance validation, overtime, assets, feedback, work type requests
- Analytics: recruitment pipeline, attendance trends, performance objectives

Role details: [Roles & Permissions](./ROLES_AND_PERMISSIONS.md).

---

## Internationalization (Arabic-first)

### What it is

Social HR defaults to **Arabic** as the primary interface language, with English and other locales available via the navbar language switcher.

### Why it matters

- First-run experience matches Saudi/GCC HR users
- Consistent Arabic terminology across the product (e.g. check-in → تسجيل الحضور, check-out → تسجيل الانصراف)
- Core HR terms use established MENA HR wording

### For training and localization

Use the [Glossary](./GLOSSARY.md) for standard product terms and Arabic equivalents where listed.

Rationale: [Design Decisions — Arabic as default](./DESIGN_DECISIONS.md#arabic-as-the-default-language).

---

## Optional integrations

Available per customer configuration (not core Social HR modules):

| Integration | Purpose |
|-------------|---------|
| Biometric hardware | Fingerprint/face device clock-in — [Biometric Devices module](./MODULES.md#biometric-devices) |
| LDAP | Directory authentication |
| Outlook mail | Calendar and mail integration |
| Cloud backup | Scheduled data backup |
| Object storage | Media files in cloud storage |

These require customer-specific setup by HR administrators or platform operators.

---

## What Social HR explicitly does not do

| Gap | Impact for stakeholders |
|-----|-------------------------|
| Automated billing | Account status managed manually in [control plane](./PLATFORM.md) |
| Seat limit enforcement | Plan employee limits are informational only |
| Cross-customer reporting | No platform-wide analytics across workspaces |
| Activity → payroll automation | Managers must classify review segments; attendance drives pay |
| Multi-company switcher | One workspace = one organization |

Full list: [Policies — Explicit non-policies](./POLICIES.md#explicit-non-policies-known-gaps).

---

## Related documents

- [Modules](./MODULES.md) — module catalog with mini product pages
- [Policies](./POLICIES.md) — rules governing these features
- [Use Cases](./USE_CASES.md) — scenarios by persona
- [How It Works](./HOW_IT_WORKS.md) — end-to-end flows
- [Design Decisions](./DESIGN_DECISIONS.md) — why features were built this way
- [Glossary](./GLOSSARY.md) — key terms
