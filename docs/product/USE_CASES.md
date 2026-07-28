# Use Cases

Real-world scenarios showing how different people accomplish their jobs in Social HR. Written as narratives — not step-by-step technical instructions.

Personas map to [roles and permissions](./ROLES_AND_PERMISSIONS.md) within the product, not separate product SKUs.

![Role hierarchy — platform operator, tenant admin, HR, manager, employee, and specialists](./assets/roles-hierarchy.png)

> **At a glance — personas**
>
> | Persona | Where they work | Start reading |
> |---------|-----------------|---------------|
> | [Platform operator](#platform-operator-scenarios) | [Control plane](./PLATFORM.md) | Provision trial |
> | [Tenant HR admin](#tenant-hr-admin-scenarios) | Customer workspace | Configure geofencing |
> | [Manager](#manager-scenarios) | Customer workspace | Approve leave |
> | [Employee](#employee-scenarios) | Customer workspace + desktop app | Clock in |
> | [Recruiter](#recruiter-scenarios) | Customer workspace | Hire pipeline |
> | [Payroll specialist](#payroll-specialist-scenarios) | Customer workspace | Monthly payslip run |

---

## Personas

| Persona | Where they work | Primary goals |
|---------|-----------------|---------------|
| **[Platform operator](./ROLES_AND_PERMISSIONS.md#platform-operator)** | [Control plane](./GLOSSARY.md#platform-terms) dashboard | [Provision](./GLOSSARY.md#platform-terms) workspaces, assign [plans](./PLANS.md), manage account status |
| **[Tenant HR admin](./ROLES_AND_PERMISSIONS.md#tenant-admin)** | Customer HR workspace | Configure organization, policies, permissions |
| **[Manager](./ROLES_AND_PERMISSIONS.md#manager)** | Customer HR workspace | Approve requests, validate attendance, review activity |
| **[Employee](./ROLES_AND_PERMISSIONS.md#employee)** | Customer HR workspace (+ optional desktop app) | Clock in, request leave, view payslips |
| **[Recruiter](./ROLES_AND_PERMISSIONS.md#recruiter)** | Customer HR workspace | Run hiring pipeline |
| **[Payroll specialist](./ROLES_AND_PERMISSIONS.md#payroll-specialist)** | Customer HR workspace | Contracts, payslips, reimbursements |

---

## Platform operator scenarios

### Provision a new customer trial

A sales representative closes a deal with Acme Corp for a 30-day evaluation. The platform operator logs into the [control plane](./PLATFORM.md), opens **Tenants → Create**, enters "Acme Corp" with [subdomain](./GLOSSARY.md#platform-terms) `acme`, and selects the **[Trial plan](./PLANS.md#trial)**.

Within moments, Acme's isolated workspace exists at `acme.socialhr.com` with [Employees](./MODULES.md#employees), [Attendance](./MODULES.md#attendance), [Leave](./MODULES.md#leave), and [Face Check-In](./MODULES.md#face-check-in) enabled. The operator shares the URL and initial admin credentials with Acme's HR director.

**Outcome:** Acme has a fully isolated HR workspace with core modules — no technical setup required from the customer.

Related: [Overview — Multi-tenant SaaS](./OVERVIEW.md#multi-tenant-saas-in-plain-terms), [Platform — Control plane](./PLATFORM.md#control-plane).

### Upgrade a customer to Standard

After Acme's trial succeeds, they sign a Standard plan contract. The platform operator opens Acme's tenant record, changes the plan from Trial to Standard, and saves.

On Acme's next login, their HR team sees [Recruitment](./MODULES.md#recruitment), [Payroll](./MODULES.md#payroll), [Activity Tracking](./MODULES.md#activity-tracking), [Projects](./MODULES.md#projects), and other Standard modules appear in the sidebar. No data migration or re-provisioning was needed.

**Outcome:** Instant feature expansion. Acme's HR admin now configures payroll contracts and activity policies.

Related: [Plans — Upgrading](./PLANS.md#upgrading-and-downgrading).

### Suspend a non-paying account

Beta Ltd misses payment. The platform operator sets Beta's status to **Suspended**. The next time any Beta user tries to use Social HR, they are signed out and see a message explaining the account is suspended.

Beta's data remains intact. When payment is received, the operator sets status back to **Active** and users can log in normally.

**Outcome:** Access blocked immediately; data preserved for reactivation.

Policy: [Account access — Suspended](./POLICIES.md#account-access-and-entitlements).

### Enable geofencing for an Enterprise pilot

Gamma Inc is on [Enterprise](./PLANS.md#enterprise) and wants [geofencing](./MODULES.md#geofencing) immediately, but their plan already includes it. The operator confirms the plan assignment and notifies Gamma's HR admin to configure office coordinates under Settings → Geo & Face Config.

If Gamma were on Standard, the operator could add a [module override](./PLANS.md#per-customer-module-overrides) to force geofencing on before a plan upgrade.

**Outcome:** Module available; customer configures location rules themselves.

---

## Tenant HR admin scenarios

### Configure office geofencing

Acme Corp has mostly office workers and wants to ensure employees clock in from the office. The HR admin:

1. Confirms [Geofencing](./MODULES.md#geofencing) is available ([Enterprise plan](./PLANS.md#enterprise))
2. Opens Settings → Geo & Face Config, sets office coordinates and a 200-meter radius, and activates the [geofence](./GLOSSARY.md#workforce-visibility-terms)
3. Reviews [work types](./GLOSSARY.md#workforce-visibility-terms): Office requires inside geofence; Remote allows anywhere
4. Assigns most employees the Office work type on their work information

![Office geofence vs remote work type at check-in](./assets/geofencing.png)

**Outcome:** Office employees must be within the geofence circle to check in. Remote employees can check in from anywhere. Every location check is logged.

Feature: [Geofencing](./FEATURES.md#geofencing-and-work-type-location-policies). Flow: [Work type resolution](./HOW_IT_WORKS.md#work-type-resolution).

### Enable desktop activity monitoring

Acme wants visibility into remote work patterns. The HR admin:

1. Confirms [Activity Tracking](./MODULES.md#activity-tracking) is available ([Standard plan](./PLANS.md#standard))
2. Opens Settings → Attendance → Activity Tracking
3. Sets idle threshold to 5 minutes and review threshold to 15 minutes
4. Enables optional screenshots with 5-minute intervals
5. Shares the Desktop App install link with employees
6. Communicates the policy: activity monitoring is for oversight; [attendance still drives pay](./DESIGN_DECISIONS.md#attendance-drives-pay-activity-provides-oversight)

**Outcome:** Employees install the desktop app. Managers use Team Activity to review idle segments and classify them.

Feature: [Activity tracking](./FEATURES.md#activity-tracking-desktop-monitoring).

### Enable face check-in

Acme wants to reduce buddy-punching at the office. The HR admin:

1. Confirms [Face Check-In](./MODULES.md#face-check-in) is available (included on all plans)
2. Enables Face Check-In in settings
3. Optionally turns on enforcement so every check-in requires verification
4. Communicates to employees: complete Face Registration on your profile before your next check-in

![Face enrollment and verification at check-in](./assets/face-checkin.png)

**Outcome:** Employees enroll their face once. Subsequent check-ins verify identity via webcam before recording attendance.

Feature: [Face check-in](./FEATURES.md#face-check-in).

### Set up hybrid work patterns

Acme allows work-from-home on Fridays. The HR admin:

1. Creates or confirms Remote work type with "allow anywhere" policy
2. Sets employee default work type to Hybrid (requires geofence Mon–Thu)
3. Adds weekday override: Friday → Remote for affected employees

**Outcome:** Monday through Thursday, employees must be in the office to check in. Friday, they can check in from home without a daily request.

Flow: [How It Works — Work type resolution](./HOW_IT_WORKS.md#work-type-resolution).

---

## Manager scenarios

### Approve remote work for one day

Sarah usually works from the office but needs to work from home next Tuesday for a home repair. She submits a **[Work Type Request](./GLOSSARY.md#workforce-visibility-terms)** for Remote on that date.

Her manager sees the request in the dashboard **Work Type Requests To Approve** queue, reviews it, and approves. On Tuesday, Sarah's [effective work type](./GLOSSARY.md#workforce-visibility-terms) is Remote — she can check in from anywhere.

**Outcome:** Temporary policy override without changing Sarah's permanent work type.

### Validate attendance before payroll

Payroll runs on the 25th. The manager opens the dashboard **Attendance To Validate** queue, reviews flagged records from the past month — late arrivals, missing check-outs, correction requests — and approves or sends back each one.

The payroll specialist then runs payslip generation knowing attendance has been reviewed.

![Attendance validation feeds payroll cycle](./assets/payroll-cycle.png)

**Outcome:** Manager sign-off on time records before compensation is calculated.

Flow: [Leave → attendance → payroll](./HOW_IT_WORKS.md#leave--attendance--payroll-chain).

### Classify a long idle activity segment

Ahmed was clocked in but his desktop app shows 45 minutes of idle time flagged as "review required." His manager opens **Team Activity**, finds the segment, and learns Ahmed was in a client call not captured by keyboard activity.

The manager classifies the segment as **Meeting** (paid). Ahmed's attendance hours are unchanged — the classification is for activity reporting, not payroll adjustment.

**Outcome:** Manager judgment applied to ambiguous idle time without automatic pay changes.

Policy: [Activity tracking — Idle pay](./POLICIES.md#activity-tracking).

---

## Employee scenarios

### Clock in from the office

Fatima arrives at the Acme office. She opens Social HR on her phone, allows location access, and taps **Check-In**. The system confirms she is inside the office geofence and records her attendance.

If she were outside the geofence, she would see an error with the distance and could submit a work type request for remote work instead.

Daily flow: [How It Works — Morning](./HOW_IT_WORKS.md#morning-starting-work).

### Clock in with face verification

Omar completed [face registration](./GLOSSARY.md#workforce-visibility-terms) last week. At check-in, his webcam activates, captures his face, and the system matches it against his enrolled templates. Match confirmed — attendance recorded.

If verification fails, Omar can retry or submit a re-enrollment request for HR review.

### Request leave and track balance

Layla needs three days off next month. She taps the [quick action](./FEATURES.md#quick-actions) button → **Create Leave Request**, selects "Annual Leave," picks her dates, and submits.

Her manager approves from the dashboard. Layla's balance decreases by three days. On those dates, she appears on the dashboard "On Leave" list and does not need to check in.

![Leave request approval workflow](./assets/leave-workflow.png)

Feature: [Leave management](./FEATURES.md#leave-management).

### Use the desktop app while working

Khalid installs Social HR Desktop, logs in, and checks in. The app runs in the background, sending activity heartbeats. He can view **My Activity** to see his daily timeline and [productivity score](./GLOSSARY.md#workforce-visibility-terms).

At end of day, he checks out — both attendance and activity session close.

![Daily workday from check-in through check-out](./assets/daily-workday.png)

### Log project time

Nour worked four hours on the website redesign project. She opens **Project → Timesheet**, selects the project and task, enters four hours, and marks it completed.

These hours are for project tracking only — her attendance check-in/out from earlier drives her pay.

Rationale: [Design Decisions — Project time separate](./DESIGN_DECISIONS.md#project-time-separate-from-attendance-time).

---

## Recruiter scenarios

### Hire through the pipeline

The HR team opens a "Software Engineer" [recruitment drive](./MODULES.md#recruitment) with stages: Applied, Phone Screen, Technical Interview, Offer, Hired.

Candidates move through the kanban pipeline. Interviews are scheduled and outcomes recorded. When a candidate reaches "Hired," they move to the [onboarding](./MODULES.md#onboarding) board.

After onboarding tasks complete, a full employee record exists — ready for attendance, leave, and payroll setup.

![Recruitment → onboarding → employee record](./assets/recruitment-onboarding.png)

**Outcome:** Seamless path from applicant to employee without duplicate data entry.

Flow: [How It Works — Recruitment → onboarding](./HOW_IT_WORKS.md#recruitment--onboarding--employee).

---

## Payroll specialist scenarios

### Monthly payslip run

It is the 25th. The payroll specialist confirms:

- [Attendance](./MODULES.md#attendance) records for the period are validated by managers
- Employment contracts are active
- No pending leave adjustments

They open the [Payroll](./MODULES.md#payroll) dashboard and generate payslips. The system applies each employee's contract, allowances, deductions, validated work records, and leave adjustments.

Employees view their payslips on their profile Payroll tab.

![Payroll cycle — attendance to payslip](./assets/payroll-cycle.png)

**Outcome:** Compensation calculated from validated attendance and configured contracts.

Feature: [Payroll](./FEATURES.md#payroll).

---

## Cross-persona scenario: hybrid employee

**Setup (HR admin):**

- Default work type: Hybrid (requires geofence)
- Weekday override: Friday → Remote
- Executive has [bypass geofence](./GLOSSARY.md#workforce-visibility-terms) flag for international travel

**Monday (employee):**

- Must be inside office geofence to check in
- Desktop app tracks activity during the day

**Friday (employee):**

- [Effective work type](./GLOSSARY.md#workforce-visibility-terms) is Remote — check in from home
- No geofence check applied

**Thursday (executive traveling):**

- Bypass geofence flag allows check-in regardless of location
- Audit log records the bypass

**End of month (manager + payroll):**

- Manager validates all attendance
- Payroll specialist generates payslips from validated records

Visual: [Work type resolution](./assets/work-type-resolution.png). Policy: [Geofencing policies](./POLICIES.md#geofencing-and-location).

---

## Related documents

- [Roles & Permissions](./ROLES_AND_PERMISSIONS.md) — who can do what
- [Features](./FEATURES.md) — capability details behind these scenarios
- [Policies](./POLICIES.md) — rules that govern behavior
- [How It Works](./HOW_IT_WORKS.md) — module connections
- [Modules](./MODULES.md) — module catalog
- [Plans](./PLANS.md) — plan tiers referenced in scenarios
