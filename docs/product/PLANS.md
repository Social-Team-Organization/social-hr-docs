# Plans

![Trial, Standard, and Enterprise plan comparison — modules included at each tier](./assets/plans-comparison.png)

Social HR sells through **[subscription plans](./PLATFORM.md)** that bundle HR [modules](./MODULES.md). Each customer workspace is assigned one plan, which determines which features appear and are usable.

[Platform operators](./ROLES_AND_PERMISSIONS.md#platform-operator) can also apply **[per-customer module overrides](./PLATFORM.md)** to enable or disable specific modules outside the plan defaults — useful for pilots, custom deals, or temporary restrictions.

> **At a glance**
>
> | Plan | Best for | Module count (default) | Key add-ons vs previous tier |
> |------|----------|------------------------|------------------------------|
> | **Trial** | Evaluation, POC | 4 | Core HR: employees, attendance, leave, face check-in |
> | **Standard** | Growing organizations | 14 | Full HR ops + activity tracking, payroll, recruitment |
> | **Enterprise** | Location + hardware needs | 16 | [Geofencing](./MODULES.md#geofencing), [biometric devices](./MODULES.md#biometric-devices) |

---

## How plans work

When a customer opens their HR workspace:

1. The system looks up their assigned [plan](./PLATFORM.md) and loads its included [modules](./PLATFORM.md).
2. Any [per-customer overrides](#per-customer-module-overrides) are applied (force on, force off, or revert to plan default).
3. The resulting module set controls sidebar visibility and feature access.
4. Disabled modules are both **hidden and blocked** — users cannot reach them even with a direct link.

Plan changes take effect immediately on the customer's next request. No workspace re-provisioning is needed. See [How It Works — Plan changes](./HOW_IT_WORKS.md#plan-changes-and-module-visibility).

---

## Default plans

Social HR ships with three plan tiers. Platform staff can create additional plans or modify module assignments.

### Trial

**Purpose:** Evaluation and proof-of-concept for prospective customers.

**Typical modules included:**

| Module | Included |
|--------|----------|
| [Employees](./MODULES.md#employees) | ✓ |
| [Attendance](./MODULES.md#attendance) | ✓ |
| [Leave](./MODULES.md#leave) | ✓ |
| [Face Check-In](./MODULES.md#face-check-in) | ✓ |

**Not included in default trial:** Recruitment, onboarding, payroll, performance, offboarding, assets, helpdesk, projects, geofencing, biometric devices, activity tracking, documents.

Trial is the **default plan** for newly [provisioned](./PLATFORM.md) workspaces unless another plan is selected.

**Who benefits:** Sales teams running quick evaluations; HR leaders testing core attendance and leave before committing.

**Typical workflow:** [Use Cases — Provision a new customer trial](./USE_CASES.md#provision-a-new-customer-trial).

### Standard

**Purpose:** Full HR operations for most growing organizations.

**Includes everything in Trial, plus:**

| Module | Included |
|--------|----------|
| [Recruitment](./MODULES.md#recruitment) | ✓ |
| [Onboarding](./MODULES.md#onboarding) | ✓ |
| [Payroll](./MODULES.md#payroll) | ✓ |
| [Performance (PMS)](./MODULES.md#performance-pms) | ✓ |
| [Offboarding](./MODULES.md#offboarding) | ✓ |
| [Assets](./MODULES.md#assets) | ✓ |
| [Helpdesk](./MODULES.md#helpdesk) | ✓ |
| [Projects](./MODULES.md#projects) | ✓ |
| [Activity Tracking](./MODULES.md#activity-tracking) | ✓ |
| [Documents](./MODULES.md#documents) | ✓ |

**Not included in default Standard:** [Geofencing](./MODULES.md#geofencing), [Biometric Devices](./MODULES.md#biometric-devices).

**Who benefits:** Organizations needing hire-to-pay HR without location enforcement or hardware terminals.

**Typical workflow:** [Use Cases — Upgrade to Standard](./USE_CASES.md#upgrade-a-customer-to-standard).

### Enterprise

**Purpose:** Complete platform access including location enforcement and hardware integrations.

**Includes all 16 catalog modules:**

| Module | Included |
|--------|----------|
| All Standard modules | ✓ |
| [Geofencing](./MODULES.md#geofencing) | ✓ |
| [Biometric Devices](./MODULES.md#biometric-devices) | ✓ |

**Who benefits:** Organizations with office-based workforces needing [geofence](./FEATURES.md#geofencing-and-work-type-location-policies) enforcement, or those using fingerprint/face hardware terminals.

**Typical workflow:** [Use Cases — Configure office geofencing](./USE_CASES.md#configure-office-geofencing).

---

## Full module catalog

Sixteen modules are available across plans. See [Modules](./MODULES.md) for detailed descriptions of each.

| Module | Trial | Standard | Enterprise |
|--------|-------|----------|------------|
| [Employees](./MODULES.md#employees) | ✓ | ✓ | ✓ |
| [Attendance](./MODULES.md#attendance) | ✓ | ✓ | ✓ |
| [Leave](./MODULES.md#leave) | ✓ | ✓ | ✓ |
| [Face Check-In](./MODULES.md#face-check-in) | ✓ | ✓ | ✓ |
| [Recruitment](./MODULES.md#recruitment) | — | ✓ | ✓ |
| [Onboarding](./MODULES.md#onboarding) | — | ✓ | ✓ |
| [Payroll](./MODULES.md#payroll) | — | ✓ | ✓ |
| [Performance (PMS)](./MODULES.md#performance-pms) | — | ✓ | ✓ |
| [Offboarding](./MODULES.md#offboarding) | — | ✓ | ✓ |
| [Assets](./MODULES.md#assets) | — | ✓ | ✓ |
| [Helpdesk](./MODULES.md#helpdesk) | — | ✓ | ✓ |
| [Projects](./MODULES.md#projects) | — | ✓ | ✓ |
| [Activity Tracking](./MODULES.md#activity-tracking) | — | ✓ | ✓ |
| [Documents](./MODULES.md#documents) | — | ✓ | ✓ |
| [Geofencing](./MODULES.md#geofencing) | — | — | ✓ |
| [Biometric Devices](./MODULES.md#biometric-devices) | — | — | ✓ |

✓ = included in default plan seed. [Per-customer overrides](#per-customer-module-overrides) can change any assignment.

![Module ecosystem — employee at the center, HR modules orbiting](./assets/modules-ecosystem.png)

---

## Per-customer module overrides

Platform staff can override plan defaults for individual customers:

| Override | Effect |
|----------|--------|
| **Force on** | Module available even if not in the customer's plan |
| **Force off** | Module hidden and blocked even if in the customer's plan |
| **Clear override** | Revert to plan default |

**Common use cases:**

- Enable [activity tracking](./MODULES.md#activity-tracking) on a Trial customer for a pilot program
- Force [geofencing](./MODULES.md#geofencing) on for an Enterprise evaluation before plan upgrade
- Disable [projects](./MODULES.md#projects) for a customer who purchased Standard but does not need project management

Overrides take effect on the customer's next page load.

---

## Special module rules

### Face Check-In and Attendance

[Attendance](./MODULES.md#attendance) and [Face Check-In](./MODULES.md#face-check-in) are **separate entitlements**. If a customer has Attendance but not Face Check-In, face verification features are unavailable even though they share the attendance workflow. This allows customers to use attendance without deploying face verification infrastructure.

### Geofencing configuration vs entitlement

[Geofencing](./MODULES.md#geofencing) must be both **entitled** (on the plan or overridden on) **and configured** by the customer's HR admin (office coordinates, radius, activation). Entitlement alone does not enforce location rules. Policy: [Geofencing and location](./POLICIES.md#geofencing-and-location).

---

## Plan limits — stored but not enforced

These fields exist for future use but are **not actively enforced** in the product today:

| Limit | Status |
|-------|--------|
| **Maximum employees** | Stored on the plan; no automatic blocking when exceeded |
| **Trial duration (days)** | Informational; no automatic conversion or expiry |
| **Automated billing** | Not implemented; account status changes are manual |

Sales and onboarding teams should treat employee limits as **guidance for packaging**, not as hard product enforcement. Platform staff manage trial conversion and suspension manually through the [control plane](./PLATFORM.md).

---

## Upgrading and downgrading

### Upgrade (Trial → Standard → Enterprise)

1. Platform staff changes the plan in the [control plane](./PLATFORM.md).
2. New modules appear in the customer's sidebar immediately.
3. No data migration required — modules were always present in the product architecture.
4. Customer HR admin may need to configure new modules ([geofence](./FEATURES.md#geofencing-and-work-type-location-policies) coordinates, [activity policies](./FEATURES.md#activity-tracking-desktop-monitoring), [payroll](./FEATURES.md#payroll) contracts, etc.).

### Downgrade or suspension

1. Platform staff changes plan or sets status to suspended.
2. Removed modules disappear from navigation and become inaccessible.
3. Data from disabled modules is **retained** in the workspace.
4. Suspended customers cannot log in; data remains until reactivation or deletion.

Scenario: [Use Cases — Suspend a non-paying account](./USE_CASES.md#suspend-a-non-paying-account).

---

## Related documents

- [Modules](./MODULES.md) — what each module does
- [Platform](./PLATFORM.md) — how platform staff manage plans
- [Policies — Account access](./POLICIES.md#account-access-and-entitlements) — entitlement enforcement rules
- [Features](./FEATURES.md) — capability deep dives by module
- [Use Cases](./USE_CASES.md) — plan change scenarios
- [Platform](./PLATFORM.md) — plan, module, and entitlement context
