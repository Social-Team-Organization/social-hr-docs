# Overview

![Social HR — multi-tenant cloud HR platform with isolated workspaces per organization](./assets/social-hr-overview.png)

Social HR is a **multi-tenant human resources platform** built for organizations that want a complete HR workspace — hiring through payroll — with strong [data isolation](./POLICIES.md#data-isolation-and-privacy) per customer.

Each customer organization gets its **own dedicated [tenant workspace](./GLOSSARY.md#platform-terms)** accessed through a unique web address ([subdomain](./GLOSSARY.md#platform-terms)). Employees, managers, and HR staff work inside that workspace. Social HR [platform operators](./GLOSSARY.md#platform-terms) manage customer accounts from a separate [control plane](./PLATFORM.md) operations dashboard.

> **At a glance**
>
> | | |
> |---|---|
> | **Model** | One organization = one isolated workspace = one subdomain |
> | **Scope** | Hire → onboard → manage → pay → develop → exit |
> | **Differentiators** | [Geofencing](./FEATURES.md#geofencing-and-work-type-location-policies), [face check-in](./FEATURES.md#face-check-in), [activity monitoring](./FEATURES.md#activity-tracking-desktop-monitoring), Arabic-first UI |
> | **Pay authority** | [Attendance](./GLOSSARY.md#attendance-and-pay-terms) — not desktop activity hours |

---

## What Social HR does

Social HR covers the full employee lifecycle. See [How It Works — Hire to retire](./HOW_IT_WORKS.md#hire-to-retire-lifecycle) for the end-to-end journey.

| Phase | [Modules](./MODULES.md) | Capabilities |
|-------|---------|--------------|
| **Hire** | [Recruitment](./MODULES.md#recruitment) | Pipelines, candidates, interviews |
| **Onboard** | [Onboarding](./MODULES.md#onboarding) | Structured new-hire task boards |
| **Manage** | [Employees](./MODULES.md#employees) | Directory, org structure, documents, requests |
| **Track time** | [Attendance](./MODULES.md#attendance), [Leave](./MODULES.md#leave) | Check-in/out, [geofencing](./FEATURES.md#geofencing-and-work-type-location-policies), [face verification](./FEATURES.md#face-check-in), [desktop activity](./FEATURES.md#activity-tracking-desktop-monitoring) |
| **Pay** | [Payroll](./MODULES.md#payroll) | Contracts, payslips, allowances, deductions |
| **Develop** | [Performance (PMS)](./MODULES.md#performance-pms) | Objectives, feedback cycles |
| **Support** | [Helpdesk](./MODULES.md#helpdesk), [Assets](./MODULES.md#assets), [Projects](./MODULES.md#projects) | Tickets, equipment, delivery tracking |
| **Exit** | [Offboarding](./MODULES.md#offboarding) | Structured exit processes |

[Plans](./PLANS.md) determine which [modules](./GLOSSARY.md#platform-terms) each customer can use. [Platform operators](./ROLES_AND_PERMISSIONS.md#platform-operator) can also enable or disable individual modules per customer via [module overrides](./GLOSSARY.md#platform-terms).

---

## Who Social HR is for

### Buyers and evaluators

HR and operations leaders comparing HR platforms. Social HR's core story: **one organization, one isolated workspace, one web address** — no shared database between customers, no in-app company switcher. See [Design Decisions — Isolated workspace](./DESIGN_DECISIONS.md#isolated-workspace-per-customer).

### Platform operators

Social HR staff who [provision](./GLOSSARY.md#platform-terms) customer workspaces, assign [subscription plans](./PLANS.md), monitor account status, and support the tenant lifecycle. Details: [Platform](./PLATFORM.md), [Use Cases — Platform operator](./USE_CASES.md#platform-operator-scenarios).

### Tenant users (customer organizations)

| Role | Primary needs | Learn more |
|------|---------------|------------|
| **HR administrators** | Configure org structure, policies, permissions | [Modules](./MODULES.md), [Policies](./POLICIES.md) |
| **Managers** | Approve requests, validate attendance, review activity | [Roles — Manager](./ROLES_AND_PERMISSIONS.md#manager), [Use Cases](./USE_CASES.md#manager-scenarios) |
| **Employees** | Clock in/out, request leave, view payslips | [Features — Attendance](./FEATURES.md#attendance-and-check-in), [Use Cases — Employee](./USE_CASES.md#employee-scenarios) |
| **Recruiters** | Run hiring pipelines | [Modules — Recruitment](./MODULES.md#recruitment) |
| **Payroll specialists** | Contracts, payslips, reimbursements | [Modules — Payroll](./MODULES.md#payroll), [Features — Payroll](./FEATURES.md#payroll) |

---

## Multi-tenant SaaS in plain terms

**Multi-tenant** means one Social HR installation serves many customer organizations. **Isolation** means each organization's data is completely separate — employees in Company A cannot see or access Company B's records.

![Each customer organization operates in its own secure, isolated workspace — data never mixes between tenants](./assets/tenant-isolation.png)

*Each customer organization operates in its own secure workspace. Data, files, and user accounts never mix between customers.*

### How this works for users

1. **Each customer gets a [subdomain](./GLOSSARY.md#platform-terms)** — for example, `acme.socialhr.com` routes to Acme Corp's workspace.
2. **Data never mixes** — each workspace is self-contained. There is no way for one customer to browse another's employees, payslips, or attendance. Policy details: [Data isolation](./POLICIES.md#data-isolation-and-privacy).
3. **[Plans](./PLANS.md) control features** — subscription tiers determine which HR [modules](./MODULES.md) appear in the sidebar.
4. **Platform staff operate separately** — provisioning, billing status, and plan changes happen in the [control plane](./PLATFORM.md), not inside customer HR workspaces.

---

## What makes Social HR distinctive

Beyond standard HR modules, Social HR adds capabilities aimed at modern workforce management. Full descriptions: [Features](./FEATURES.md).

| Capability | User benefit | Visual |
|------------|--------------|--------|
| **[Geofencing](./FEATURES.md#geofencing-and-work-type-location-policies)** | Enforce location rules at clock-in based on [work type](./GLOSSARY.md#workforce-visibility-terms) | ![Geofencing](./assets/geofencing.png) |
| **[Face check-in](./FEATURES.md#face-check-in)** | Optional webcam identity verification before attendance | ![Face check-in](./assets/face-checkin.png) |
| **[Activity monitoring](./FEATURES.md#activity-tracking-desktop-monitoring)** | Desktop app tracks presence, idle time, optional screenshots | ![Activity monitoring](./assets/activity-monitoring.png) |
| **Work-type location policies** | Flexible rules — not just "remote on/off" — with temporary overrides via [work type requests](./GLOSSARY.md#workforce-visibility-terms) | [How It Works — Work type resolution](./HOW_IT_WORKS.md#work-type-resolution) |
| **Arabic-first interface** | Default Arabic UI with consistent Saudi/GCC HR terminology | [Features — Internationalization](./FEATURES.md#internationalization-arabic-first) |
| **[Plan-based entitlements](./PLANS.md)** | Sell tiers; turn modules on or off per customer without re-provisioning | ![Plans comparison](./assets/plans-comparison.png) |

> **Important:** [Attendance](./GLOSSARY.md#attendance-and-pay-terms) remains the **authoritative source for pay hours**. [Activity monitoring](./FEATURES.md#activity-tracking-desktop-monitoring) provides oversight but does not automatically change payroll. See [Design Decisions — Attendance drives pay](./DESIGN_DECISIONS.md#attendance-drives-pay-activity-provides-oversight).

---

## What Social HR does not do today

These are honest gaps — useful for sales and implementation planning. Also listed in [Policies — Explicit non-policies](./POLICIES.md#explicit-non-policies-known-gaps).

| Gap | Current state |
|-----|---------------|
| **Automated billing** | No payment processor integration; account status is managed manually in the [control plane](./PLATFORM.md) |
| **Seat limits** | Plan employee limits are stored but not enforced in the product |
| **Automatic trial expiry** | Trial duration is informational; conversion to paid is a manual status change |
| **Cross-customer reporting** | No analytics spanning multiple customer workspaces |
| **Multi-company within one workspace** | Each workspace is one organization; there is no company switcher |

---

## Brand and experience

Social HR presents as **clear, human, and operationally confident**:

- The marketing site explains the product quickly — [tenant isolation](./POLICIES.md#data-isolation-and-privacy) is stated plainly.
- The [control plane](./PLATFORM.md) dashboard is a practical operations tool: dense enough to manage accounts, quiet enough to trust.
- The tenant HR app follows standard HR workflows with **Arabic as the default language**.

Visual design uses warm paper tones with deep teal text and an ember accent for primary actions.

---

## Related documents

- [Platform](./PLATFORM.md) — control plane vs tenant workspace
- [Plans](./PLANS.md) — subscription tiers and modules
- [Features](./FEATURES.md) — detailed capability descriptions
- [How It Works](./HOW_IT_WORKS.md) — lifecycle flows and module connections
- [Modules](./MODULES.md) — module catalog
- [Glossary](./GLOSSARY.md) — key terms
