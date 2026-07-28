# نظرة عامة

![Social HR — منصة موارد بشرية سحابية متعددة المستأجرين مع مساحات عمل معزولة لكل مؤسسة](../../product/assets/social-hr-overview.png)

Social HR منصة **موارد بشرية متعددة المستأجرين (multi-tenant)** مبنية للمؤسسات التي تريد مساحة HR متكاملة — من التوظيف إلى Payroll — مع [عزل بيانات](./POLICIES.md#data-isolation-and-privacy) قوي لكل عميل.

تحصل كل مؤسسة عميلة على **[مساحة عمل مستأجر (tenant workspace)](./PLATFORM.md)** مخصّصة لها، تُفتح عبر عنوان ويب فريد ([النطاق الفرعي — subdomain](./PLATFORM.md)). الموظفون والمديرون وفرق HR يعملون داخل تلك المساحة. [مشغّلو منصة](./PLATFORM.md) Social HR يديرون حسابات العملاء من [لوحة التحكم (Control plane)](./PLATFORM.md) — لوحة عمليات منفصلة.

> **نظرة سريعة**
>
> | | |
> |---|---|
> | **النموذج** | مؤسسة واحدة = مساحة عمل معزولة = نطاق فرعي واحد |
> | **النطاق** | توظيف ← إعداد ← إدارة ← دفع ← تطوير ← إنهاء خدمة |
> | **ما يميّزنا** | [Geofencing](./FEATURES.md#geofencing-and-work-type-location-policies)، [Face Check-In](./FEATURES.md#face-check-in)، [Activity Tracking](./FEATURES.md#activity-tracking-desktop-monitoring)، واجهة عربية أولاً |
> | **مصدر الأجر** | [الحضور والانصراف (Attendance)](./MODULES.md#attendance) — وليس ساعات نشاط سطح المكتب |

---

## ماذا يقدّم Social HR

Social HR يغطي دورة حياة الموظف كاملة. راجع [كيف يعمل — من التوظيف إلى إنهاء الخدمة](./HOW_IT_WORKS.md#hire-to-retire-lifecycle) للرحلة من البداية للنهاية.

| المرحلة | [الوحدات](./MODULES.md) | القدرات |
|---------|-------------------------|---------|
| **التوظيف (Hire)** | [Recruitment](./MODULES.md#recruitment) | مسارات، مرشحون، مقابلات |
| **الإعداد (Onboard)** | [Onboarding](./MODULES.md#onboarding) | لوحات مهام منظّمة للموظفين الجدد |
| **الإدارة (Manage)** | [Employees](./MODULES.md#employees) | الدليل، الهيكل التنظيمي، المستندات، الطلبات |
| **تتبّع الوقت** | [Attendance](./MODULES.md#attendance)، [Leave](./MODULES.md#leave) | تسجيل الحضور/الانصراف، [Geofencing](./FEATURES.md#geofencing-and-work-type-location-policies)، [التحقق بالوجه](./FEATURES.md#face-check-in)، [نشاط سطح المكتب](./FEATURES.md#activity-tracking-desktop-monitoring) |
| **الأجر (Pay)** | [Payroll](./MODULES.md#payroll) | العقود، كشوف الرواتب، البدلات، الخصومات |
| **التطوير (Develop)** | [Performance (PMS)](./MODULES.md#performance-pms) | الأهداف، دورات التقييم |
| **الدعم (Support)** | [Helpdesk](./MODULES.md#helpdesk)، [Assets](./MODULES.md#assets)، [Projects](./MODULES.md#projects) | التذاكر، المعدات، تتبّع التسليم |
| **إنهاء الخدمة (Exit)** | [Offboarding](./MODULES.md#offboarding) | عمليات خروج منظّمة |

[الباقات (Plans)](./PLANS.md) تحدّد أي [وحدات](./PLATFORM.md) يمكن لكل عميل استخدامها. يمكن لـ [مشغّلي المنصة](./ROLES_AND_PERMISSIONS.md#platform-operator) أيضاً تفعيل أو تعطيل وحدات فردية لكل عميل عبر [تجاوزات الوحدات (module overrides)](./PLATFORM.md).

---

## لمن Social HR

### المشترون والمُقيّمون

قادة الموارد البشرية والعمليات الذين يقارنون منصات HR. رسالة Social HR الأساسية: **مؤسسة واحدة، مساحة عمل معزولة، عنوان ويب واحد** — بلا قاعدة بيانات مشتركة بين العملاء، وبلا مبدّل شركة داخل التطبيق. راجع [قرارات التصميم — مساحة عمل معزولة](./DESIGN_DECISIONS.md#isolated-workspace-per-customer).

### مشغّلو المنصة

فريق Social HR الذي [يُنشئ](./PLATFORM.md) مساحات عمل العملاء، ويُعيّن [باقات الاشتراك](./PLANS.md)، ويراقب حالة الحسابات، ويدعم دورة حياة المستأجر. التفاصيل: [المنصة](./PLATFORM.md)، [حالات الاستخدام — مشغّل المنصة](./USE_CASES.md#platform-operator-scenarios).

### مستخدمو المستأجر (المؤسسات العميلة)

| الدور | الاحتياجات الأساسية | اقرأ المزيد |
|------|---------------------|-------------|
| **مسؤولو HR** | إعداد الهيكل التنظيمي، السياسات، الصلاحيات | [الوحدات](./MODULES.md)، [السياسات](./POLICIES.md) |
| **المديرون** | الموافقة على الطلبات، التحقق من الحضور، مراجعة النشاط | [الأدوار — المدير](./ROLES_AND_PERMISSIONS.md#manager)، [حالات الاستخدام](./USE_CASES.md#manager-scenarios) |
| **الموظفون** | تسجيل الحضور/الانصراف، طلب الإجازات، عرض كشوف الرواتب | [المزايا — Attendance](./FEATURES.md#attendance-and-check-in)، [حالات الاستخدام — الموظف](./USE_CASES.md#employee-scenarios) |
| **مسؤولو التوظيف** | إدارة مسارات التوظيف | [الوحدات — Recruitment](./MODULES.md#recruitment) |
| **أخصائيو Payroll** | العقود، كشوف الرواتب، المصروفات | [الوحدات — Payroll](./MODULES.md#payroll)، [المزايا — Payroll](./FEATURES.md#payroll) |

---

## SaaS متعدد المستأجرين بلغة مبسّطة {#multi-tenant-saas-in-plain-terms}

**Multi-tenant** يعني أن تثبيت Social HR واحداً يخدم مؤسسات عميلة كثيرة. **العزل (Isolation)** يعني أن بيانات كل مؤسسة منفصلة تماماً — موظفو الشركة أ لا يرون ولا يصلون لسجلات الشركة ب.

![كل مؤسسة عميلة تعمل في مساحة عمل آمنة ومعزولة — البيانات لا تختلط بين المستأجرين](../../product/assets/tenant-isolation.png)

*كل مؤسسة عميلة تعمل في مساحة عمل آمنة خاصة بها. البيانات والملفات وحسابات المستخدمين لا تختلط بين العملاء.*

### كيف يؤثر ذلك على المستخدمين

1. **لكل عميل [نطاق فرعي (subdomain)](./PLATFORM.md)** — مثلاً `acme.socialhr.com` يوجّه إلى مساحة عمل Acme Corp.
2. **البيانات لا تختلط أبداً** — كل مساحة عمل مستقلة. لا يمكن لعميل تصفّح موظفي أو كشوف رواتب أو حضور عميل آخر. تفاصيل السياسة: [عزل البيانات](./POLICIES.md#data-isolation-and-privacy).
3. **[الباقات (Plans)](./PLANS.md) تتحكم بالمزايا** — مستويات الاشتراك تحدّد أي [وحدات HR](./MODULES.md) تظهر في الشريط الجانبي.
4. **فريق المنصة يعمل بشكل منفصل** — الإنشاء، وحالة الفوترة، وتغييرات الباقة تتم في [لوحة التحكم (Control plane)](./PLATFORM.md)، وليس داخل مساحات HR للعملاء.

---

## ما يميّز Social HR

إلى جانب وحدات HR القياسية، يضيف Social HR قدرات موجهة لإدارة القوى العاملة الحديثة. الأوصاف الكاملة: [المزايا](./FEATURES.md).

| القدرة | فائدة للمستخدم | رسم |
|--------|----------------|-----|
| **[Geofencing](./FEATURES.md#geofencing-and-work-type-location-policies)** | فرض قواعد الموقع عند تسجيل الحضور حسب [نوع العمل (Work Type)](./FEATURES.md#geofencing-and-work-type-location-policies) | ![Geofencing](../../product/assets/geofencing.png) |
| **[Face Check-In](./FEATURES.md#face-check-in)** | تحقق اختياري من الهوية عبر الكاميرا قبل Attendance | ![Face Check-In](../../product/assets/face-checkin.png) |
| **[Activity Tracking](./FEATURES.md#activity-tracking-desktop-monitoring)** | تطبيق سطح المكتب يتتبّع الحضور، وقت الخمول، ولقطات شاشة اختيارية | ![Activity Tracking](../../product/assets/activity-monitoring.png) |
| **سياسات موقع نوع العمل** | قواعد مرنة — ليست مجرد «عن بُعد نعم/لا» — مع تجاوزات مؤقتة عبر [طلبات نوع العمل](./FEATURES.md#geofencing-and-work-type-location-policies) | [كيف يعمل — حل نوع العمل](./HOW_IT_WORKS.md#work-type-resolution) |
| **واجهة عربية أولاً** | واجهة عربية افتراضياً مع مصطلحات HR سعودية/خليجية متسقة | [المزايا — التدويل](./FEATURES.md#internationalization-arabic-first) |
| **[استحقاقات حسب الباقة (Plan-based entitlements)](./PLANS.md)** | بيع مستويات؛ تفعيل/تعطيل وحدات لكل عميل دون إعادة إنشاء | ![مقارنة الباقات](../../product/assets/plans-comparison.png) |

> **مهم:** [الحضور والانصراف (Attendance)](./MODULES.md#attendance) يبقى **المصدر المعتمد لساعات الأجر**. [Activity Tracking](./FEATURES.md#activity-tracking-desktop-monitoring) يوفّر إشرافاً لكنه لا يغيّر Payroll تلقائياً. راجع [قرارات التصميم — الحضور يحدد الأجر](./DESIGN_DECISIONS.md#attendance-drives-pay-activity-provides-oversight).

---

## ما لا يفعله Social HR حالياً {#what-social-hr-does-not-do-today}

فجوات صريحة — مفيدة للمبيعات وتخطيط التطبيق. مذكورة أيضاً في [السياسات — سياسات غير مطبّقة صراحة](./POLICIES.md#explicit-non-policies-known-gaps).

| الفجوة | الوضع الحالي |
|--------|--------------|
| **الفوترة الآلية** | لا تكامل مع معالج دفع؛ تُدار حالة الحساب يدوياً في [لوحة التحكم (Control plane)](./PLATFORM.md) |
| **حدود المقاعد** | حدود عدد الموظفين في الباقة مخزّنة لكن غير مُطبَّقة في المنتج |
| **انتهاء Trial تلقائياً** | مدة Trial للمعلومات؛ التحويل إلى مدفوع تغيير حالة يدوي |
| **تقارير عبر العملاء** | لا تحليلات تمتد على مساحات عمل متعددة |
| **عدة شركات في مساحة واحدة** | كل مساحة عمل = مؤسسة واحدة؛ لا يوجد مبدّل شركة |

---

## العلامة والتجربة

Social HR يقدّم نفسه **واضحاً، إنسانياً، وواثقاً تشغيلياً**:

- الموقع التسويقي يشرح المنتج بسرعة — [عزل المستأجر](./POLICIES.md#data-isolation-and-privacy) مذكور بوضوح.
- لوحة [Control plane](./PLATFORM.md) أداة عمليات عملية: كثيفة بما يكفي لإدارة الحسابات، هادئة بما يكفي للثقة.
- تطبيق HR للمستأجر يتبع مسارات HR القياسية مع **العربية كلغة افتراضية**.

التصميم البصري يستخدم درجات ورقية دافئة مع نص أزرق مخضر عميق ولون Ember للإجراءات الأساسية.

---

## مستندات ذات صلة

- [المنصة](./PLATFORM.md) — Control plane مقابل مساحة HR للمستأجر
- [الباقات](./PLANS.md) — مستويات الاشتراك والوحدات
- [المزايا](./FEATURES.md) — أوصاف تفصيلية للقدرات
- [كيف يعمل](./HOW_IT_WORKS.md) — مسارات دورة الحياة وترابط الوحدات
- [الوحدات](./MODULES.md) — دليل الوحدات
