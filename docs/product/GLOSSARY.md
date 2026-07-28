# Glossary

Business terms used in Social HR product documentation. For exhaustive UI-aligned definitions and Arabic translations, see the dedicated terminology references linked below.

![Social HR module ecosystem — key terms map to modules around the employee record](./assets/modules-ecosystem.png)

Product docs index: [README](./README.md). Module details: [Modules](./MODULES.md).

---

## Platform terms

| Term | Definition | Learn more |
|------|------------|------------|
| **Social HR** | Multi-tenant HR SaaS platform — hiring through payroll with workforce visibility extensions | [Overview](./OVERVIEW.md) |
| **[Tenant](./GLOSSARY.md) / customer workspace** | One customer organization's isolated HR environment | [Platform — Tenant workspace](./PLATFORM.md#tenant-hr-workspace) |
| **[Subdomain](./GLOSSARY.md)** | Unique web address for a customer workspace (e.g., `acme.socialhr.com`) | [Overview — Multi-tenant](./OVERVIEW.md#multi-tenant-saas-in-plain-terms) |
| **[Control plane](./GLOSSARY.md)** | Platform staff dashboard for managing customer workspaces, plans, and modules | [Platform](./PLATFORM.md) |
| **Tenant HR workspace** | Full HR application where customer users work daily | [Platform — Tenant workspace](./PLATFORM.md#tenant-hr-workspace) |
| **[Plan](./GLOSSARY.md)** | Subscription tier determining which modules a customer can use | [Plans](./PLANS.md) |
| **Module / [entitlement](./GLOSSARY.md)** | An HR capability (attendance, payroll, geofencing, etc.) enabled per plan | [Modules](./MODULES.md) |
| **[Module override](./GLOSSARY.md)** | Per-customer force-on or force-off of a specific module, regardless of plan | [Plans — Overrides](./PLANS.md#per-customer-module-overrides) |
| **[Provision](./GLOSSARY.md)** | Create a new customer workspace with subdomain, plan, and initial admin | [Use Cases — Provision trial](./USE_CASES.md#provision-a-new-customer-trial) |
| **[Platform operator](./GLOSSARY.md)** | Social HR staff who manage the control plane | [Roles — Platform operator](./ROLES_AND_PERMISSIONS.md#platform-operator) |

Arabic equivalents: [SOCIAL_HR_TERMS_AR.md](../SOCIAL_HR_TERMS_AR.md).

---

## Removed concepts

| Term | Status in Social HR |
|------|---------------------|
| **Company** (legacy) | Removed — each workspace is one organization |
| **Company switcher** | Removed — no switching between organizations within one login |

Rationale: [Design Decisions — No company switcher](./DESIGN_DECISIONS.md#no-company-switcher).

---

## HR modules

| Module | One-line definition | Detail |
|--------|---------------------|--------|
| **[Recruitment](./MODULES.md#recruitment)** | Hiring pipeline and candidate management | [Module page](./MODULES.md#recruitment) |
| **[Onboarding](./MODULES.md#onboarding)** | New-hire task boards | [Module page](./MODULES.md#onboarding) |
| **[Employees](./MODULES.md#employees)** | People directory and org structure | [Module page](./MODULES.md#employees) |
| **[Attendance](./MODULES.md#attendance)** | Check-in/out — **authoritative source for pay hours** | [Feature — Attendance](./FEATURES.md#attendance-and-check-in) |
| **[Leave](./MODULES.md#leave)** | Time off, balances, and approvals | [Feature — Leave](./FEATURES.md#leave-management) |
| **[Payroll](./MODULES.md#payroll)** | Contracts, payslips, allowances, deductions | [Feature — Payroll](./FEATURES.md#payroll) |
| **[Performance (PMS)](./MODULES.md#performance-pms)** | Objectives, key results, 360 feedback | [Module page](./MODULES.md#performance-pms) |
| **[Offboarding](./MODULES.md#offboarding)** | Structured employee exit processes | [Module page](./MODULES.md#offboarding) |
| **[Assets](./MODULES.md#assets)** | Company equipment inventory and allocation | [Module page](./MODULES.md#assets) |
| **[Helpdesk](./MODULES.md#helpdesk)** | Internal support tickets and FAQs | [Module page](./MODULES.md#helpdesk) |
| **[Projects](./MODULES.md#projects)** | Task management and timesheets (non-payroll hours) | [How It Works — Projects vs attendance](./HOW_IT_WORKS.md#projects-vs-attendance) |
| **[Face Check-In](./MODULES.md#face-check-in)** | Webcam identity verification at clock-in | [Feature — Face check-in](./FEATURES.md#face-check-in) |
| **[Biometric Devices](./MODULES.md#biometric-devices)** | Hardware fingerprint/face attendance terminals | [Module page](./MODULES.md#biometric-devices) |
| **[Geofencing](./MODULES.md#geofencing)** | Location-based clock-in rules | [Feature — Geofencing](./FEATURES.md#geofencing-and-work-type-location-policies) |
| **[Activity Tracking](./MODULES.md#activity-tracking)** | Desktop presence monitoring | [Feature — Activity tracking](./FEATURES.md#activity-tracking-desktop-monitoring) |
| **[Documents](./MODULES.md#documents)** | Employee document management workflows | [Module page](./MODULES.md#documents) |

[Plan availability](./PLANS.md#full-module-catalog) by tier.

---

## Workforce visibility terms

| Term | Definition | Arabic |
|------|------------|--------|
| **[Geofence](./GLOSSARY.md)** | Virtual circle around the office — must be activated by HR admin to enforce | [SOCIAL_HR_TERMS_AR.md](../SOCIAL_HR_TERMS_AR.md) |
| **[Work type](./GLOSSARY.md)** | Office, Remote, Hybrid, or Field — determines location policy | [SOCIAL_HR_TERMS_AR.md](../SOCIAL_HR_TERMS_AR.md) |
| **[Location policy](./GLOSSARY.md)** | Rule for a work type: require inside geofence, allow anywhere, or block clock-in | [Policies — Geofencing](./POLICIES.md#geofencing-and-location) |
| **[Bypass geofence](./GLOSSARY.md)** | Per-employee flag to skip location checks | [Policies — Geofencing](./POLICIES.md#geofencing-and-location) |
| **[Work type request](./GLOSSARY.md)** | Temporary approved change to work type for specific dates | [Use Cases — Approve remote work](./USE_CASES.md#approve-remote-work-for-one-day) |
| **[Effective work type](./GLOSSARY.md)** | The work type applied on a given day after resolving requests, weekday overrides, and defaults | [How It Works — Work type resolution](./HOW_IT_WORKS.md#work-type-resolution) |
| **[Face registration](./GLOSSARY.md)** | Employee enrolls face templates for future verification | [Feature — Face check-in](./FEATURES.md#face-check-in) |
| **[Face check-in](./GLOSSARY.md)** | Webcam identity verification before attendance is recorded | [Feature — Face check-in](./FEATURES.md#face-check-in) |
| **Desktop app / desktop agent** | Social HR Desktop application for activity monitoring | [Feature — Activity tracking](./FEATURES.md#activity-tracking-desktop-monitoring) |
| **[Heartbeat](./GLOSSARY.md)** | Periodic activity signal from the desktop app | [Policies — Activity tracking](./POLICIES.md#activity-tracking) |
| **[Idle segment](./GLOSSARY.md)** | Period with no keyboard/mouse input | [Policies — Activity tracking](./POLICIES.md#activity-tracking) |
| **[Review segment](./GLOSSARY.md)** | Idle period exceeding threshold, flagged for manager decision | [Use Cases — Classify idle segment](./USE_CASES.md#classify-a-long-idle-activity-segment) |
| **[Manager decision](./GLOSSARY.md)** | Classification of review segment: Paid, Unpaid, or Meeting | [Policies — Activity tracking](./POLICIES.md#activity-tracking) |
| **[Productivity score](./GLOSSARY.md)** | Derived activity metric — informational only, not on payslips | [Design Decisions — Attendance drives pay](./DESIGN_DECISIONS.md#attendance-drives-pay-activity-provides-oversight) |

---

## Attendance and pay terms

| Term | Definition | Arabic |
|------|------------|--------|
| **[Check-in / check-out](./GLOSSARY.md)** | Recording start and end of work | [تسجيل الحضور / تسجيل الانصراف](../SOCIAL_HR_TERMS_AR.md) |
| **[Attendance record](./GLOSSARY.md)** | Single check-in/check-out entry for a work period | [SOCIAL_HR_TERMS_AR.md](../SOCIAL_HR_TERMS_AR.md) |
| **[Work records](./GLOSSARY.md)** | Daily matrix of worked hours feeding payroll | [How It Works — Pay authority](./HOW_IT_WORKS.md#attendance-sources-and-pay-authority) |
| **[Hour account](./GLOSSARY.md)** | Overtime bank — separate from project timesheets | [Policies — Attendance](./POLICIES.md#attendance) |
| **[Attendance validation](./GLOSSARY.md)** | Manager review and approval of attendance records | [Use Cases — Validate attendance](./USE_CASES.md#validate-attendance-before-payroll) |
| **[Attendance request](./GLOSSARY.md)** | Employee correction request for missed or incorrect punches | [Features — Quick actions](./FEATURES.md#quick-actions) |
| **[Grace time](./GLOSSARY.md)** | Tolerance for late arrival before flagging | [Policies — Attendance](./POLICIES.md#attendance) |
| **[Pay source](./GLOSSARY.md)** | Attendance work records — the basis for payslip hour calculations | [Design Decisions — Attendance drives pay](./DESIGN_DECISIONS.md#attendance-drives-pay-activity-provides-oversight) |

---

## Leave terms

| Term | Definition |
|------|------------|
| **[Leave type](./GLOSSARY.md)** | Category of time off (annual, sick, unpaid, etc.) |
| **[Leave balance](./GLOSSARY.md)** | Remaining days available for a leave type |
| **[Leave request](./GLOSSARY.md)** | Employee application for time off |
| **[Leave allocation](./GLOSSARY.md)** | HR assignment of leave days to an employee |
| **[Compensatory leave](./GLOSSARY.md)** | Time off earned from overtime hours |
| **[Company leave](./GLOSSARY.md)** | Organization-wide recurring non-working pattern |
| **[Restrict leaves](./GLOSSARY.md)** | Date-range rules blocking leave applications |

Feature: [Leave management](./FEATURES.md#leave-management). Policy: [Leave policies](./POLICIES.md#leave).

---

## Project terms

| Term | Definition |
|------|------------|
| **[Project](./GLOSSARY.md)** | Container for related tasks and team members |
| **[Task](./GLOSSARY.md)** | Unit of work within a project |
| **[Timesheet](./GLOSSARY.md)** | Hours logged on a task — for project tracking, not payroll |
| **[Project manager](./GLOSSARY.md)** | Role controlling project access — separate from HR reporting manager |
| **[Archive](./GLOSSARY.md)** | Soft-hide a project or task without deleting |

Rationale: [Design Decisions — Project time separate](./DESIGN_DECISIONS.md#project-time-separate-from-attendance-time).

---

## Account status values

| Status | Meaning for customer users |
|--------|---------------------------|
| **Trial** | Evaluation period — full access to [plan](./PLANS.md) modules |
| **Active** | Normal operation |
| **Past due** | Grace period — access continues (managed manually) |
| **Suspended** | Login blocked — data retained |
| **Cancelled** | Login blocked — data retained until deletion |

Policy: [Account access](./POLICIES.md#account-access-and-entitlements).

---

## Full terminology references

For complete UI label definitions used in training, product copy audits, and localization:

| Document | Language | Scope |
|----------|----------|-------|
| [English product glossary](../SOCIAL_HR_TERMS_GLOSSARY.md) | English | Complete UI glossary: navbar, dashboard, settings, modules |
| [Arabic terminology map](../SOCIAL_HR_TERMS_AR.md) | Arabic | Saudi/GCC HR wording aligned to the English glossary |

Social HR defaults to **Arabic** as the primary interface language. Use the Arabic map for training materials and localization consistency (e.g., Check-In → تسجيل الحضور).

Feature: [Internationalization](./FEATURES.md#internationalization-arabic-first).

---

## Related documents

- [Overview](./OVERVIEW.md) — product introduction
- [Modules](./MODULES.md) — module descriptions
- [Features](./FEATURES.md) — capability details
- [Policies](./POLICIES.md) — rules and enforcement
- [How It Works](./HOW_IT_WORKS.md) — terms in context
- [Roles & Permissions](./ROLES_AND_PERMISSIONS.md) — who uses these concepts
