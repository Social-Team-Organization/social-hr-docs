# Platform

![Control plane (platform staff) vs tenant HR workspace (customer users) — two surfaces, one product](./assets/control-plane-vs-tenant.png)

Social HR has two distinct experiences: the **[control plane](./PLATFORM.md)** for Social HR [platform operators](./ROLES_AND_PERMISSIONS.md#platform-operator), and the **[tenant HR workspace](./PLATFORM.md)** for each customer organization's users.

Understanding this split is essential for sales demos, onboarding, and support — staff actions in the control plane directly affect what customer users see in their workspace.

> **At a glance**
>
> | Surface | Who | Web address | Purpose |
> |---------|-----|-------------|---------|
> | Marketing site | Prospects | Primary domain | Learn about Social HR |
> | **Control plane** | Platform staff | Primary domain `/dashboard/` | Manage tenants, plans, audit |
> | **Tenant workspace** | Customer users | Customer subdomain | Day-to-day HR operations |

---

## Two surfaces, one product

| Surface | Who uses it | Purpose |
|---------|-------------|---------|
| **Marketing site** | Prospects, evaluators | Understand Social HR; request demo or trial |
| **[Control plane](./PLATFORM.md)** | Social HR platform staff | Manage customers, [plans](./PLANS.md), [modules](./MODULES.md), audit |
| **[Tenant HR workspace](./PLATFORM.md)** | Customer organization's users | Day-to-day HR operations |

These are **separate login experiences**. A platform staff account does not automatically work inside a customer workspace, and vice versa. See [Design Decisions — Separate platform and customer experiences](./DESIGN_DECISIONS.md#separate-platform-and-customer-experiences).

---

## Control plane

The control plane is the operations dashboard on Social HR's primary domain. [Platform operators](./ROLES_AND_PERMISSIONS.md#platform-operator) use it to run the SaaS business.

### What platform staff can do

| Area | Capabilities |
|------|--------------|
| **Overview** | High-level metrics and recent activity |
| **Tenants** | Create, view, edit, and delete customer workspaces |
| **Plans** | Define [subscription tiers](./PLANS.md) and which [modules](./MODULES.md) each tier includes |
| **Modules** | View the catalog of available HR modules |
| **Audit** | Review staff actions on the control plane |

### Tenant management actions

When creating or editing a customer workspace, platform staff configure:

- **Company name** — displayed to the customer
- **[Subdomain](./PLATFORM.md)** — determines the workspace web address
- **[Plan](./PLANS.md)** — Trial, Standard, Enterprise, or custom configuration
- **Status** — trial, active, past due, suspended, or cancelled
- **[Module overrides](./PLATFORM.md)** — force specific modules on or off regardless of plan

Walkthrough: [Use Cases — Provision a new customer trial](./USE_CASES.md#provision-a-new-customer-trial).

### Tenant lifecycle statuses

| Status | What customer users experience |
|--------|-------------------------------|
| **Trial** | Full access to modules included in the trial [plan](./PLANS.md#trial) |
| **Active** | Normal operation |
| **Past due** | Access continues (grace period — managed manually today) |
| **Suspended** | Login blocked with a message; data retained |
| **Cancelled** | Login blocked; data retained until deletion |

Suspension and cancellation take effect on the customer's next login attempt — authenticated users are signed out and shown an explanatory message. Policy: [Account access](./POLICIES.md#account-access-and-entitlements).

### Opening a customer workspace

From the control plane, staff can open a customer's HR workspace directly — useful for support and verification after [plan changes](./PLANS.md#upgrading-and-downgrading) or [provisioning](./PLATFORM.md).

---

## Tenant HR workspace

Each customer organization accesses Social HR through its own [subdomain](./PLATFORM.md). This is the full HR application where employees, managers, and HR staff do their daily work.

![Tenant data isolation — each workspace is a self-contained environment](./assets/tenant-isolation.png)

### What tenant users see

The workspace includes:

- **Sidebar navigation** — HR [modules](./MODULES.md) enabled by the customer's [plan](./PLANS.md) (and any [overrides](./PLANS.md#per-customer-module-overrides))
- **Dashboard** — role-aware tiles: headcount, announcements, approval queues, analytics
- **Navbar** — check-in/check-out, quick actions, language switcher, notifications
- **Settings** — organization configuration (departments, [work types](./FEATURES.md#geofencing-and-work-type-location-policies), policies, mail, permissions)
- **Employee profiles** — comprehensive tabs for personal info, attendance, leave, payroll, documents, and more

### What tenant users do not see

- Other customers' data or workspaces
- Control plane screens (tenants, plans, platform audit)
- [Modules](./MODULES.md) not included in their [plan](./PLANS.md) — hidden from navigation and blocked even by direct URL
- A company switcher — each workspace represents one organization ([Design Decisions — No company switcher](./DESIGN_DECISIONS.md#no-company-switcher))

### Module visibility

When a customer's plan changes (for example, Trial → Standard), new modules appear in the sidebar on the next page load. No re-provisioning or data migration is required.

[Per-tenant module overrides](./PLANS.md#per-customer-module-overrides) allow platform staff to pilot features (enable [activity tracking](./MODULES.md#activity-tracking) on a trial customer) or restrict features (disable [projects](./MODULES.md#projects) for a specific customer on Standard).

---

## Users and authentication

| User type | Where they log in | Scope |
|-----------|-------------------|-------|
| **Platform staff** | Primary domain staff login | Control plane only |
| **Tenant admin** | Customer subdomain login | Full HR workspace administration |
| **HR, managers, employees** | Customer subdomain login | Based on assigned [permissions](./ROLES_AND_PERMISSIONS.md) |

Each customer workspace maintains its **own user accounts**. A user in one workspace cannot authenticate in another — even if they use the same email address, accounts are separate.

The first [tenant admin](./ROLES_AND_PERMISSIONS.md#tenant-admin) is created during workspace [provisioning](./PLATFORM.md). Additional users are managed inside the HR application through employee records and permission groups.

---

## Data and file isolation

![Data isolation policy — each tenant's data and files stay completely separate](./assets/data-isolation-policy.png)

All customer data — employees, attendance, payslips, uploaded documents, activity screenshots — lives entirely within that customer's workspace. Files uploaded by one customer are stored in a namespace reserved for that customer.

Platform staff can see customer metadata (name, plan, status, subdomain) in the control plane but **do not browse customer HR records** from the control plane interface. Full policy: [Data isolation and privacy](./POLICIES.md#data-isolation-and-privacy).

---

## Demo workspace

Social HR can point marketing CTAs to a shared demo workspace so evaluators can explore the product without [provisioning](./PLATFORM.md) a trial. Demo configuration is set at the platform level.

---

## Related documents

- [Overview](./OVERVIEW.md) — product summary
- [Plans](./PLANS.md) — what each tier includes
- [Roles & Permissions](./ROLES_AND_PERMISSIONS.md) — who does what in each surface
- [Use Cases — Platform operator](./USE_CASES.md#platform-operator-scenarios) — provisioning and upgrade scenarios
- [Policies — Data isolation](./POLICIES.md#data-isolation-and-privacy) — isolation rules
- [Design Decisions — Separate experiences](./DESIGN_DECISIONS.md#separate-platform-and-customer-experiences) — why two surfaces exist
