# Policies

Rules and policies as organizations experience them in Social HR. These describe **what the system enforces**, **what administrators configure**, and **what the system explicitly does not do**.

Policies here reflect implemented behavior — not aspirational HR handbooks. [Tenant admins](./ROLES_AND_PERMISSIONS.md#tenant-admin) set thresholds and toggles; this document explains the resulting rules.

> **At a glance**
>
> | Policy area | Enforced by | Configured by |
> |-------------|-------------|---------------|
> | [Data isolation](#data-isolation-and-privacy) | Platform architecture | — |
> | [Account access](#account-access-and-entitlements) | [Control plane](./PLATFORM.md) status + [plan](./PLANS.md) | Platform operator |
> | [Geofencing](#geofencing-and-location) | Check-in evaluation | HR admin |
> | [Activity tracking](#activity-tracking) | Segment classification | HR admin + manager |
> | [Attendance & pay](#attendance) | Validation workflow | HR admin + manager |

Feature details: [Features](./FEATURES.md). Rationale: [Design Decisions](./DESIGN_DECISIONS.md).

---

## Data isolation and privacy

![Each tenant's data, files, and users stay completely separate — no cross-access between organizations](./assets/data-isolation-policy.png)

| Policy | What organizations experience |
|--------|------------------------------|
| **[Workspace isolation](./PLATFORM.md)** | Each customer organization's data is completely separate. No user in one workspace can see another workspace's employees, records, or files. |
| **File separation** | Uploaded documents, photos, and screenshots are stored in a namespace reserved for that organization. |
| **Separate user accounts** | Users in one workspace cannot log into another, even with the same email address. |
| **One organization per workspace** | There is no company switcher. Each workspace represents exactly one organization. |

Rationale: [Design Decisions — Isolated workspace](./DESIGN_DECISIONS.md#isolated-workspace-per-customer), [Files namespaced per customer](./DESIGN_DECISIONS.md#files-namespaced-per-customer).

Platform detail: [Platform — Data and file isolation](./PLATFORM.md#data-and-file-isolation).

---

## Account access and entitlements

| Policy | What organizations experience |
|--------|------------------------------|
| **Suspended account** | All users are signed out and cannot log in. Data is retained. Message explains the suspension. |
| **Cancelled account** | Same as suspended — login blocked, data retained until deletion. |
| **Disabled [module](./PLATFORM.md)** | Module hidden from navigation and inaccessible even via direct link. Data from that module is retained. |
| **[Plan](./PLANS.md) change** | Module visibility updates on next page load. No data loss from upgrades or downgrades. |
| **Face check-in without entitlement** | If [attendance](./MODULES.md#attendance) is enabled but [face check-in](./MODULES.md#face-check-in) is not on the plan, face verification features are unavailable. |

Scenario: [Use Cases — Suspend non-paying account](./USE_CASES.md#suspend-a-non-paying-account).

---

## Geofencing and location

| Policy | Rule |
|--------|------|
| **[Geofence](./FEATURES.md#geofencing-and-work-type-location-policies) inactive** | When geofencing is not activated by HR admin, all location checks pass — no enforcement. |
| **[Bypass geofence](./FEATURES.md#geofencing-and-work-type-location-policies)** | HR can flag individual employees to skip location checks entirely (executive travel, special arrangements). |
| **[Work type](./FEATURES.md#geofencing-and-work-type-location-policies) policy** | Each work type has one of three rules: require inside geofence, allow anywhere, or block clock-in. |
| **[Effective work type](./FEATURES.md#geofencing-and-work-type-location-policies)** | The system determines today's work type using: approved request → weekday override → rotating assignment → default. |
| **GPS required** | "Require inside geofence" denies check-in if the device does not provide location coordinates. |
| **Audit trail** | Every location evaluation is logged — success or failure — for review. |
| **Pay authority** | Geofencing gates check-in only. It does not calculate or modify pay hours. |

![Work type resolution determines which location policy applies at check-in](./assets/work-type-resolution.png)

**Default work type policies:**

| Work type | Default location policy |
|-----------|------------------------|
| Office | Require inside geofence |
| Remote | Allow anywhere |
| Hybrid | Require inside geofence |
| Field | Allow anywhere |

HR administrators can change policies on any work type after creation.

Feature: [Geofencing](./FEATURES.md#geofencing-and-work-type-location-policies). Module: [Geofencing](./MODULES.md#geofencing). Flow: [Work type resolution](./HOW_IT_WORKS.md#work-type-resolution).

---

## Face check-in

| Policy | Rule |
|--------|------|
| **Activation** | HR admin must enable face check-in in settings. |
| **[Enrollment minimum](./FEATURES.md#geofencing-and-work-type-location-policies)** | Employees must complete at least three successful face captures before verification works. |
| **Verification at check-in** | Live webcam capture compared against enrolled templates. |
| **Enforcement mode** | HR can optionally require face verification on every check-in. |
| **Privacy** | System stores mathematical face templates, not enrollment photos. |
| **Failed match** | Employee can retry or submit a re-enrollment request for HR review. |
| **Plan requirement** | Face check-in must be included in the organization's [plan](./PLANS.md) (available on all default plans). |

Feature: [Face check-in](./FEATURES.md#face-check-in). Rationale: [Design Decisions — Face verification](./DESIGN_DECISIONS.md#face-verification-as-an-optional-gate).

---

## Activity tracking

| Policy | Rule | Default |
|--------|------|---------|
| **One policy per organization** | Single activity tracking configuration applies to all employees. | Auto-created |
| **Idle classification** | No keyboard/mouse input for configured duration → [idle segment](./FEATURES.md#geofencing-and-work-type-location-policies). | 5 minutes |
| **Review required** | Idle exceeds review threshold → flagged for manager decision. | 15 minutes |
| **Idle pay** | Idle time does **not** automatically reduce [attendance](./MODULES.md#attendance) or payslip hours. | — |
| **[Manager decisions](./FEATURES.md#geofencing-and-work-type-location-policies)** | Review segments require classification: Paid, Unpaid, or Meeting. | — |
| **[Productivity score](./FEATURES.md#geofencing-and-work-type-location-policies)** | Calculated for display only — never appears on payslips. | — |
| **Screenshots** | Optional; can be disabled entirely. | Enabled, 5-minute interval |
| **Screenshot retention** | Screenshots older than configured days are deleted. | 30 days |
| **Clock-in coupling** | Organization can encourage desktop app use at check-in. | Off by default |
| **Session link** | Activity session automatically links to open attendance record when employee is clocked in. | Automatic |

![Activity monitoring — manager classifies review segments; attendance hours unchanged](./assets/activity-monitoring.png)

Feature: [Activity tracking](./FEATURES.md#activity-tracking-desktop-monitoring). Rationale: [Attendance drives pay](./DESIGN_DECISIONS.md#attendance-drives-pay-activity-provides-oversight).

---

## Attendance

| Policy | Rule |
|--------|------|
| **[Pay authority](./MODULES.md#attendance)** | Attendance records and [work records](./MODULES.md#attendance) are the source for payroll hour calculations. |
| **[Validation workflow](./MODULES.md#attendance)** | Managers review and validate attendance before payroll (organizational process). |
| **[Grace time](./MODULES.md#attendance)** | Configurable tolerance for late arrivals before flagging. |
| **IP restriction** | Optional allowlist — check-in only permitted from specified IP addresses. |
| **[Attendance request](./MODULES.md#attendance)** | Employees can request attendance corrections; managers approve or reject. |
| **[Biometric devices](./MODULES.md#biometric-devices)** | Hardware punches create attendance records directly ([Enterprise plan](./PLANS.md#enterprise)). |
| **[Hour account](./MODULES.md#attendance)** | Overtime tracked separately; can link to compensatory leave when enabled. |

![Attendance sources and pay authority — geofencing and face gate; activity does not affect pay](./assets/attendance-pay-authority.png)

Feature: [Attendance](./FEATURES.md#attendance-and-check-in). Module: [Attendance](./MODULES.md#attendance).

---

## Leave

| Policy | Rule |
|--------|------|
| **Approval workflow** | Leave requests require manager approval (single or multi-step). |
| **Multi-step approvals** | HR can configure additional approval levels via Configuration → Multiple Approvals. |
| **[Restrict leaves](./FEATURES.md#leave-management)** | HR can block leave applications during specific date ranges. |
| **[Company leave](./FEATURES.md#leave-management)** | Organization-wide recurring non-working patterns (e.g., summer Fridays). |
| **[Compensatory leave](./FEATURES.md#leave-management)** | Links to overtime from attendance hour account when feature is enabled. |
| **Holidays** | Configured holidays affect leave balance calculations and attendance work records. |
| **Balance deduction** | Approved leave deducts from employee's allocated balance for that leave type. |

Flow: [Leave → attendance → payroll](./HOW_IT_WORKS.md#leave--attendance--payroll-chain).

---

## Project timesheets

| Policy | Rule |
|--------|------|
| **No approval workflow** | Timesheet status (in progress, completed) reflects progress only — no manager approval step. |
| **Separate from payroll** | Project hours do **not** feed attendance or payslip calculations. |
| **Hours format** | Time entered as hours and minutes. |
| **Future dates blocked** | Cannot log time for future dates. |
| **Membership required** | Employee must be a project/task member or project manager to log time. |

Rationale: [Design Decisions — Project time separate](./DESIGN_DECISIONS.md#project-time-separate-from-attendance-time).

---

## Payroll

| Policy | Rule |
|--------|------|
| **Contract required** | Employee must have an active employment contract for payslip generation. |
| **Validated attendance** | Payroll calculations use validated attendance work records. |
| **Leave integration** | Approved leave days adjust payslip calculations. |
| **Scheduled generation** | Payslips can be generated on a schedule (typically monthly). |
| **Employee access** | Employees view own payslips on profile when permitted by role. |

Feature: [Payroll](./FEATURES.md#payroll). Scenario: [Monthly payslip run](./USE_CASES.md#monthly-payslip-run).

---

## Email and notifications

| Policy | Rule |
|--------|------|
| **Organization mail server** | HR admin can configure custom mail server in settings. |
| **Mail templates** | Configurable templates for notifications across modules. |
| **Mail automations** | Triggered emails for events (leave approved, ticket created, etc.). |
| **Async delivery** | Emails sent in background — not blocking the user's action. |

---

## Security (production)

| Policy | Rule |
|--------|------|
| **HTTPS** | All traffic encrypted in production. |
| **Secure sessions** | Web login uses secure session cookies. |
| **Desktop app authentication** | Desktop app uses token-based authentication separate from browser sessions. |

---

## Explicit non-policies (known gaps)

These are things Social HR **does not** enforce today:

| Gap | What this means for organizations |
|-----|-----------------------------------|
| **Automatic trial expiry** | Trial accounts do not auto-convert or expire. [Platform operators](./ROLES_AND_PERMISSIONS.md#platform-operator) manage status manually. |
| **Seat count limits** | [Plan](./PLANS.md) employee limits are stored but not enforced — no automatic blocking when exceeded. |
| **Activity → payroll automation** | Idle time never automatically reduces attendance hours or payslip amounts. |
| **Cross-customer analytics** | No reporting across multiple customer workspaces. |
| **Automated billing** | No payment processor — account status changes are manual. |
| **Timesheet approval** | [Project](./MODULES.md#projects) timesheets have no manager approval workflow. |

Also listed: [Overview — What Social HR does not do](./OVERVIEW.md#what-social-hr-does-not-do-today), [Plans — Plan limits](./PLANS.md#plan-limits--stored-but-not-enforced).

---

## Related documents

- [Features](./FEATURES.md) — capability details
- [Design Decisions](./DESIGN_DECISIONS.md) — why these policies exist
- [Plans](./PLANS.md) — entitlement rules
- [How It Works](./HOW_IT_WORKS.md) — policy application in workflows
- [Roles & Permissions](./ROLES_AND_PERMISSIONS.md) — who configures policies
