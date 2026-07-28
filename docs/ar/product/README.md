# Social HR — توثيق المنتج

![Social HR — منصة موارد بشرية سحابية لمؤسسات متعددة](../../product/assets/social-hr-overview.png)

توثيق **لمالكي المنتج، وقادة الموارد البشرية، والمبيعات، ومستشاري الإعداد، وأصحاب المصلحة** ممن يحتاجون فهم Social HR كمنتج — ماذا يفعل، ولمن يُقدَّم، وكيف تترابط الأجزاء.

هذا **ليس** توثيقاً للمطوّرين. يشرح القدرات والسياسات وقرارات التصميم بلغة واضحة دون الإشارة إلى الكود أو البنية التحتية أو تفاصيل التنفيذ.

> **توثيق بصري** — يتضمّن هذا القسم رسوماً توضيحية مُولَّدة بالذكاء الاصطناعي في [`assets/`](../../product/assets/) لشرح المفاهيم بسرعة. المخططات تركّز على المنتج، لا على البنية التقنية.

---

## ابدأ من هنا — حسب الدور

| إذا كنت… | اقرأ بهذا الترتيب | سوف تتعلّم |
|----------|-------------------|------------|
| **مُقيّماً أو مشترياً** | [نظرة عامة](./OVERVIEW.md) → [المزايا](./FEATURES.md) → [الباقات](./PLANS.md) | ما هو Social HR، وما يميّزه، وخيارات المستويات |
| **مدير موارد بشرية أو مسؤولاً** | [الوحدات](./MODULES.md) → [السياسات](./POLICIES.md) → [حالات الاستخدام](./USE_CASES.md) | القدرات اليومية، والقواعد، والسيناريوهات الواقعية |
| **مستشار تطبيق** | [كيف يعمل](./HOW_IT_WORKS.md) → [الأدوار والصلاحيات](./ROLES_AND_PERMISSIONS.md) → [المنصة](./PLATFORM.md) | المسارات، والأدوار، والفصل بين المنصة ومساحة العمل |
| **مبيعات أو إعداد** | [المنصة](./PLATFORM.md) → [الباقات](./PLANS.md) → [حالات الاستخدام](./USE_CASES.md) | سرد العرض التوضيحي، والتعبئة، وقصص العملاء |

---

## لمن هذا التوثيق

| الجمهور | المستندات الأساسية |
|---------|-------------------|
| المُقيّمون والمشترون | [نظرة عامة](./OVERVIEW.md)، [المزايا](./FEATURES.md)، [الباقات](./PLANS.md) |
| مديرو الموارد البشرية والمسؤولون | [الوحدات](./MODULES.md)، [السياسات](./POLICIES.md)، [حالات الاستخدام](./USE_CASES.md) |
| مستشارو التطبيق | [كيف يعمل](./HOW_IT_WORKS.md)، [الأدوار والصلاحيات](./ROLES_AND_PERMISSIONS.md) |
| المبيعات والإعداد | [المنصة](./PLATFORM.md)، [الباقات](./PLANS.md)، [حالات الاستخدام](./USE_CASES.md) |

---

## فهرس المستندات

| المستند | الوصف | رسم رئيسي |
|---------|-------|-----------|
| [OVERVIEW.md](./OVERVIEW.md) | ما هو Social HR، ولمن يُقدَّم، SaaS متعدد المستأجرين ([tenant](./PLATFORM.md)) بلغة مبسّطة | [نظرة عامة على المنصة](../../product/assets/social-hr-overview.png) |
| [PLATFORM.md](./PLATFORM.md) | [لوحة التحكم (Control plane)](./PLATFORM.md) مقابل [مساحة HR للمؤسسة (tenant workspace)](./PLATFORM.md) — ما يراه كل طرف | [سطحان للعمل](../../product/assets/control-plane-vs-tenant.png) |
| [PLANS.md](./PLANS.md) | Trial وStandard وEnterprise — [الوحدات](./PLATFORM.md) والحدود المعروفة | [مقارنة الباقات](../../product/assets/plans-comparison.png) |
| [MODULES.md](./MODULES.md) | كل [وحدة HR](./MODULES.md) كصفحة منتج مختصرة | [منظومة الوحدات](../../product/assets/modules-ecosystem.png) |
| [FEATURES.md](./FEATURES.md) | تعمّق: Attendance، [Geofencing](./FEATURES.md#geofencing-and-work-type-location-policies)، [Face Check-In](./FEATURES.md#geofencing-and-work-type-location-policies)، [Activity Tracking](./FEATURES.md#geofencing-and-work-type-location-policies) | رسوم توضيحية للمزايا |
| [HOW_IT_WORKS.md](./HOW_IT_WORKS.md) | مسارات Hire-to-retire؛ كيف تتصل [الوحدات](./MODULES.md) | [رحلة دورة الحياة](../../product/assets/hire-to-retire.png) |
| [USE_CASES.md](./USE_CASES.md) | شخصيات وسيناريوهات سردية | [نظرة على الأدوار](../../product/assets/roles-hierarchy.png) |
| [POLICIES.md](./POLICIES.md) | القواعد التي تختبرها المؤسسات في المنتج | [عزل البيانات](../../product/assets/data-isolation-policy.png) |
| [DESIGN_DECISIONS.md](./DESIGN_DECISIONS.md) | لماذا بُني Social HR بهذا الشكل — المبررات وتأثيرها على المستخدم | — |
| [ROLES_AND_PERMISSIONS.md](./ROLES_AND_PERMISSIONS.md) | [مشغّل المنصة](./PLATFORM.md)، المسؤول، HR، المدير، الموظف | [تسلسل الأدوار](../../product/assets/roles-hierarchy.png) |

---

## اللغة

Social HR يعتمد **العربية** كلغة الواجهة الأساسية. English ولغات أخرى متاحة عبر مبدّل اللغة. راجع [المزايا — التدويل (عربي أولاً)](./FEATURES.md#internationalization-arabic-first).

---

## مستندات ذات صلة

- [نظرة عامة](./OVERVIEW.md) — مقدمة المنتج
- [المزايا](./FEATURES.md) — شرح تفصيلي للقدرات
- [كيف يعمل](./HOW_IT_WORKS.md) — مسارات من البداية للنهاية
