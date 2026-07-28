# Social HR — Product Documentation

![Social HR — cloud HR platform for multiple organizations](./assets/social-hr-overview.png)

Documentation for **product owners, HR leaders, sales, onboarding consultants, and business stakeholders** who need to understand Social HR as a product — what it does, who it is for, and how the pieces fit together.

This is **not** developer documentation. It explains capabilities, policies, and design choices in plain language without reference to code, infrastructure, or implementation details.

> **Visual documentation** — This section includes AI-generated illustrations in [`assets/`](./assets/) to explain concepts at a glance. Diagrams are product-focused, not technical architecture.

---

## Start here — by persona

| If you are… | Read in this order | You'll learn |
|-------------|-------------------|--------------|
| **Evaluator or buyer** | [Overview](./OVERVIEW.md) → [Features](./FEATURES.md) → [Plans](./PLANS.md) | What Social HR is, differentiators, and tier options |
| **HR director or admin** | [Modules](./MODULES.md) → [Policies](./POLICIES.md) → [Use Cases](./USE_CASES.md) | Day-to-day capabilities, rules, and real scenarios |
| **Implementation consultant** | [How It Works](./HOW_IT_WORKS.md) → [Roles & Permissions](./ROLES_AND_PERMISSIONS.md) → [Platform](./PLATFORM.md) | Flows, roles, and the platform vs workspace split |
| **Sales or onboarding** | [Platform](./PLATFORM.md) → [Plans](./PLANS.md) → [Use Cases](./USE_CASES.md) | Demo narrative, packaging, and customer stories |
| **Localization or training** | [Glossary](./GLOSSARY.md) | Terms and consistency rules |

---

## Who this is for

| Audience | Primary documents |
|----------|-------------------|
| Evaluators and buyers | [Overview](./OVERVIEW.md), [Features](./FEATURES.md), [Plans](./PLANS.md) |
| HR directors and admins | [Modules](./MODULES.md), [Policies](./POLICIES.md), [Use Cases](./USE_CASES.md) |
| Implementation consultants | [How It Works](./HOW_IT_WORKS.md), [Roles & Permissions](./ROLES_AND_PERMISSIONS.md) |
| Sales and onboarding | [Platform](./PLATFORM.md), [Plans](./PLANS.md), [Use Cases](./USE_CASES.md) |
| Localization and training | [Glossary](./GLOSSARY.md) |

---

## Document index

| Document | Description | Key visual |
|----------|-------------|------------|
| [OVERVIEW.md](./OVERVIEW.md) | What Social HR is, who it serves, multi-[tenant](./GLOSSARY.md#platform-terms) SaaS in plain terms | [Platform overview](./assets/social-hr-overview.png) |
| [PLATFORM.md](./PLATFORM.md) | [Control plane](./GLOSSARY.md#platform-terms) vs [tenant HR workspace](./GLOSSARY.md#platform-terms) — what each side sees | [Two surfaces](./assets/control-plane-vs-tenant.png) |
| [PLANS.md](./PLANS.md) | Trial, Standard, and Enterprise — [modules](./GLOSSARY.md#platform-terms) and known limits | [Plan comparison](./assets/plans-comparison.png) |
| [MODULES.md](./MODULES.md) | Each HR [module](./GLOSSARY.md#hr-modules) as a mini product page | [Module ecosystem](./assets/modules-ecosystem.png) |
| [FEATURES.md](./FEATURES.md) | Deep dives: attendance, [geofencing](./GLOSSARY.md#workforce-visibility-terms), [face check-in](./GLOSSARY.md#workforce-visibility-terms), [activity tracking](./GLOSSARY.md#workforce-visibility-terms) | Feature illustrations throughout |
| [HOW_IT_WORKS.md](./HOW_IT_WORKS.md) | Hire-to-retire flows; how [modules](./MODULES.md) connect | [Lifecycle journey](./assets/hire-to-retire.png) |
| [USE_CASES.md](./USE_CASES.md) | Personas and narrative scenarios | [Roles overview](./assets/roles-hierarchy.png) |
| [POLICIES.md](./POLICIES.md) | Rules organizations experience in the product | [Data isolation](./assets/data-isolation-policy.png) |
| [DESIGN_DECISIONS.md](./DESIGN_DECISIONS.md) | Why Social HR was built this way — rationale and user impact | — |
| [ROLES_AND_PERMISSIONS.md](./ROLES_AND_PERMISSIONS.md) | [Platform operator](./GLOSSARY.md#platform-terms), admin, HR, manager, employee | [Role hierarchy](./assets/roles-hierarchy.png) |
| [GLOSSARY.md](./GLOSSARY.md) | Business terms used across product documentation | — |

---

## Language

Social HR defaults to **Arabic** as the primary interface language. English and other locales are available via the language switcher. See [Features — Internationalization](./FEATURES.md#internationalization-arabic-first).

---

## Related

- [Overview](./OVERVIEW.md) — product introduction
- [Features](./FEATURES.md) — capability deep dives
- [How It Works](./HOW_IT_WORKS.md) — end-to-end flows
