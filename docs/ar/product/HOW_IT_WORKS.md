# كيف يعمل النظام

شرح مفاهيمي لكيفية ترابط [وحدات](./MODULES.md) Social HR وكيف تسير العمليات في النظام — من التوظيف إلى إنهاء الخدمة، ومن تسجيل الحضور إلى قسيمة الراتب.

لا تتضمن هذه الصفحة تفاصيل تقنية. التركيز على **ما الذي يحدث**، **بأي ترتيب**، و**من يشارك**.

> **نظرة سريعة**
>
> | المسار | الفكرة الأساسية |
> |--------|-----------------|
> | **سجل الموظف** | محور يرتبط به معظم الوحدات |
> | **يوم العمل** | تسجيل الحضور → السياسات → العمل → تسجيل الانصراف |
> | **سلسلة الراتب** | Attendance → التحقق → Work Records → Payroll |
> | **Activity** | يرتبط بجلسة الحضور؛ **لا يغيّر** الراتب |

---

## سجل الموظف كمحور مركزي {#the-employee-record-as-hub}

يرتبط تقريباً كل شيء في Social HR **بسجل الموظف**. عند انضمام شخص إلى المؤسسة، يُنشأ ملف موظف (مباشرة أو عبر [Recruitment](./MODULES.md#recruitment) → [Onboarding](./MODULES.md#onboarding)). يصبح هذا السجل نقطة الارتكاز لـ:

- جدول العمل (Shift، [نوع العمل](./FEATURES.md#geofencing-and-work-type-location-policies))
- [Attendance](./MODULES.md#attendance) و [Leave](./MODULES.md#leave)
- عقد [Payroll](./MODULES.md#payroll)
- أهداف [Performance (PMS)](./MODULES.md#performance-pms)
- [Assets](./MODULES.md#assets) المخصّصة
- العضوية في [Projects](./MODULES.md#projects)
- تذاكر [Helpdesk](./MODULES.md#helpdesk)
- عملية [Offboarding](./MODULES.md#offboarding)

![ترابط الوحدات — سجل الموظف في المركز، وتتدفق البيانات إلى Attendance و Leave و Payroll وغيرها](../../product/assets/module-connections.png)

*سجل الموظف في المركز. Leave يؤثر على Attendance؛ Attendance المُحقَّق يغذّي Payroll. Geofencing و Face Check-In يتحكمان في Attendance؛ Activity يرتبط دون أن يحدد الراتب.*

---

## دورة الحياة من التوظيف إلى إنهاء الخدمة {#hire-to-retire-lifecycle}

![دورة حياة الموظف من Recruitment عبر Onboarding والعمل اليومي والراتب والتطوير والمغادرة](../../product/assets/hire-to-retire.png)

### مرحلة بمرحلة

| المرحلة | [الوحدة](./MODULES.md) | ما الذي يحدث |
|---------|--------|--------------|
| **الاستقطاب** | [Recruitment](./MODULES.md#recruitment) | نشر الوظيفة، تقدّم المرشحون، مراحل المسار |
| **الاختيار** | Recruitment | المقابلات، التقييمات، قرار التعيين |
| **التهيئة** | [Onboarding](./MODULES.md#onboarding) | لوحات مهام لـ HR و IT والموظف الجديد |
| **التوظيف** | [Employees](./MODULES.md#employees) | الملف نشط؛ يُعيَّن الهيكل التنظيمي |
| **الجدولة** | Employees + Configuration | Shift، نوع العمل، التعيينات المتناوبة |
| **العمل** | Attendance + ملحقات | تسجيل الحضور/الانصراف يومياً مع الموقع أو الوجه أو Activity اختيارياً |
| **الإجازات** | [Leave](./MODULES.md#leave) | الطلبات، الموافقات، خصم الأرصدة |
| **الراتب** | [Payroll](./MODULES.md#payroll) | العقد + Attendance المُحقَّق → قسيمة الراتب |
| **التطوير** | [Performance (PMS)](./MODULES.md#performance-pms) | الأهداف، دورات التقييم، نقاط المكافأة |
| **الدعم** | Helpdesk و Assets و Projects | احتياجات تشغيلية موازية لـ HR الأساسي |
| **المغادرة** | [Offboarding](./MODULES.md#offboarding) | الاستقالة، إرجاع الأصول، إلغاء التفعيل |

سيناريو تفصيلي: [Use Cases — التوظيف عبر المسار](./USE_CASES.md#hire-through-the-pipeline).

---

## مسار يوم العمل {#daily-work-flow}

![يوم العمل — تسجيل الحضور صباحاً حتى تسجيل الانصراف مع تتبع Activity](../../product/assets/daily-workday.png)

### الصباح: بدء العمل {#morning-starting-work}

1. يفتح الموظف Social HR (الويب أو تطبيق سطح المكتب)
2. ينقر **Check-In** في شريط التنقل
3. يقيّم النظام السياسات بالترتيب:
   - هل [Geofencing](./FEATURES.md#geofencing-and-work-type-location-policies) مفعّل؟ → التحقق من الموقع وفق [سياسة الموقع](./FEATURES.md#geofencing-and-work-type-location-policies) لنوع العمل
   - هل [Face Check-In](./FEATURES.md#face-check-in) مفعّل؟ → التحقق من الهوية عبر كاميرا الويب
   - هل [Activity Tracking](./FEATURES.md#activity-tracking-desktop-monitoring) مطلوب؟ → التأكد من اتصال تطبيق سطح المكتب
4. ينجح تسجيل الحضور → يُنشأ [سجل حضور](./MODULES.md#attendance)
5. إذا كان تطبيق سطح المكتب يعمل → تبدأ جلسة Activity

### خلال اليوم

- يعمل الموظف؛ يرسل تطبيق سطح المكتب [نبضات](./FEATURES.md#geofencing-and-work-type-location-policies) Activity (إن كان مفعّلاً)
- يُصنَّف وقت الخمول تلقائياً؛ الخمول الطويل يُعلَّم لمراجعة المدير
- قد يقدّم الموظف [إجراءات سريعة](./FEATURES.md#quick-actions) (إجازة، تغيير نوع العمل، استرداد/صرف)
- يرى المدير طوابير الموافقة في [لوحة المعلومات](./FEATURES.md#dashboard)

### نهاية اليوم

1. ينقر الموظف **Check-Out**
2. يُكمل سجل الحضور بوقت الانصراف
3. تُغلق جلسة Activity
4. يمكن للموظف عرض ملخص النشاط اليومي و[درجة الإنتاجية](./FEATURES.md#geofencing-and-work-type-location-policies)

سيناريو: [Use Cases — تسجيل الحضور من المكتب](./USE_CASES.md#clock-in-from-the-office).

---

## تحديد نوع العمل {#work-type-resolution}

عند تفعيل [Geofencing](./MODULES.md#geofencing)، يجب على النظام تحديد **نوع العمل المطبّق اليوم** قبل التحقق من الموقع.

![أولوية تحديد نوع العمل — طلب معتمد، تخصيص يوم الأسبوع، تعيين متناوب، ثم الافتراضي](../../product/assets/work-type-resolution.png)

**ترتيب الأولوية:**

1. **[طلب نوع عمل](./FEATURES.md#geofencing-and-work-type-location-policies)** معتمد لليوم (أعلى أولوية)
2. **تخصيص يوم الأسبوع** (مثلاً: الجمعة = Remote)
3. **تعيين نوع عمل متناوب**
4. **نوع العمل الافتراضي** في سجل الموظف

ثم تُطبَّق [سياسة الموقع](./FEATURES.md#geofencing-and-work-type-location-policies) → السماح أو رفض تسجيل الحضور.

**مثال — موظف هجين (الإثنين–الخميس مكتب، الجمعة عن بُعد):**

- نوع العمل الافتراضي: Hybrid (يتطلب السياج الجغرافي)
- تخصيص يوم الأسبوع: الجمعة → Remote (السماح من أي مكان)
- الخميس: يجب التواجد داخل السياج الجغرافي للمكتب
- الجمعة: يمكن تسجيل الحضور من أي مكان

**تجاوز مؤقت:** يقدّم الموظف طلب نوع عمل لـ «Remote يوم الخميس» → يوافق المدير → يُطبَّق Remote يوم الخميس بغض النظر عن الافتراضي الأسبوعي.

سيناريو: [Use Cases — سيناريو متعدد الأدوار لموظف هجين](./USE_CASES.md#cross-persona-scenario-hybrid-employee). السياسة: [سياسات Geofencing](./POLICIES.md#geofencing-and-location).

---

## مصادر Attendance وسلطة الراتب {#attendance-sources-and-pay-authority}

يمكن لعدة طرق إنشاء Attendance أو التحكم فيه، لكن **سجلات Attendance تحدد Payroll**:

![Attendance هو مصدر الراتب — Geofencing و Face يتحكمان في تسجيل الحضور؛ Activity يرتبط دون تأثير على قسيمة الراتب](../../product/assets/attendance-pay-authority.png)

| المصدر | الدور | تأثير الراتب |
|--------|------|--------------|
| Check-In/Check-Out في شريط التنقل | ينشئ سجلات Attendance | **المصدر الأساسي للراتب** |
| [Geofencing](./FEATURES.md#geofencing-and-work-type-location-policies) | يسمح أو يرفض تسجيل الحضور | بوابة فقط — لا حساب راتب |
| [Face Check-In](./FEATURES.md#face-check-in) | يتحقق من الهوية قبل تسجيل الحضور | بوابة فقط |
| [Biometric Devices](./MODULES.md#biometric-devices) | البصمة/الجهاز ينشئ Attendance | ينشئ سجلات Attendance |
| [تطبيق Activity لسطح المكتب](./FEATURES.md#activity-tracking-desktop-monitoring) | يراقب التواجد خلال الجلسة | **لا تأثير مباشر على قسيمة الراتب** |
| [Leave](./MODULES.md#leave) المعتمد | يعلّم أيام الإجازة | يقلّل أيام العمل في Payroll |
| [Work Records](./MODULES.md#attendance) | مصفوفة يومية | تغذّي حسابات Payroll |

**المبدأ الأساسي:** [تتبع Activity](./FEATURES.md#activity-tracking-desktop-monitoring) يوفّر إشرافاً. يصنّف المدير وقت الخمول غير الواضح (مدفوع / غير مدفوع / اجتماع)، لكن الخمول **لا يقلّل** ساعات Attendance أو مبالغ قسيمة الراتب تلقائياً.

المبرر: [Design Decisions — Attendance يحدد الراتب](./DESIGN_DECISIONS.md#attendance-drives-pay-activity-provides-oversight).

---

## سلسلة Leave → Attendance → Payroll {#leave--attendance--payroll-chain}

![موافقة Leave تتدفق إلى Work Records في Attendance ثم إنشاء قسائم الراتب في Payroll](../../product/assets/payroll-cycle.png)

| الخطوة | من | ما الذي يحدث |
|--------|-----|--------------|
| 1 | الموظف | يقدّم طلب إجازة بالتواريخ والنوع |
| 2 | المدير | يوافق أو يرفض من طابور لوحة المعلومات |
| 3 | النظام | يخصم رصيد الإجازة؛ يعلّم الموظف «في إجازة» لتلك التواريخ |
| 4 | Attendance | تظهر أيام الإجازة في مصفوفة Work Records |
| 5 | أخصائي الرواتب | يشغّل إنشاء قسائم الراتب للفترة |
| 6 | النظام | يطبّق تعديلات Leave على حسابات قسيمة الراتب |
| 7 | الموظف | يعرض قسيمة الراتب في ملفه (إن سُمح) |

مخطط مسار Leave: [رسم توضيحي لمسار Leave](../../product/assets/leave-workflow.png).

[الإجازة التعويضية](./FEATURES.md#leave-management) (عند التفعيل) تربط العمل الإضافي من [حساب الساعات](./MODULES.md#attendance) في Attendance بأرصدة Leave.

---

## مسار تتبع Activity {#activity-monitoring-flow}

![تتبع Activity على سطح المكتب — نبضات، تصنيف الخمول، مراجعة المدير، إغلاق الجلسة عند Check-Out](../../product/assets/activity-monitoring.png)

1. يثبّت الموظف Social HR Desktop ويسجّل الدخول
2. يسجّل الحضور (الويب أو التطبيق)
3. يرسل تطبيق سطح المكتب نبضات على فترات منتظمة
4. يصنّف النظام الوقت: نشط، خمول، أو يتطلب مراجعة
5. عند تجاوز الخمول عتبة المراجعة → يرى المدير المقطع في **نشاط الفريق**
6. يصنّف المدير: **مدفوع**، **غير مدفوع**، أو **اجتماع**
7. يسجّل الموظف الانصراف → تُغلق جلسة Activity
8. **ساعات Attendance لا تتغيّر** بقرارات Activity

سيناريو: [Use Cases — تصنيف مقطع خمول طويل](./USE_CASES.md#classify-a-long-idle-activity-segment).

---

## Recruitment → Onboarding → Employee {#recruitment--onboarding--employee}

![مسار Recruitment يتصل بمهام Onboarding وسجل الموظف الكامل](../../product/assets/recruitment-onboarding.png)

| الانتقال | المحفّز | النتيجة |
|----------|---------|---------|
| مرشح في المسار | ينقل مسؤول التوظيف عبر المراحل | سجلات المقابلات والتقييمات |
| تم التعيين | الوصول لمرحلة Hired | ينتقل المرشح إلى لوحة Onboarding |
| اكتمال Onboarding | انتهاء المهام | يُنشأ أو يُكمل سجل الموظف |
| HR اليومي | الموظف نشط | يبدأ Attendance و Leave و Payroll وغيرها |

تعرض لوحة المعلومات جسوراً بين الوحدات: «المرشحون المعيّنون»، «مرشحون بدأوا التهيئة».

---

## Projects مقابل Attendance {#projects-vs-attendance}

هذان المفهومان منفصلان عن قصد:

| المفهوم | الوحدة | الغرض |
|---------|--------|-------|
| **ساعات المكتب** | [Attendance](./MODULES.md#attendance) | متى عمل الموظف — يحدد الراتب |
| **ساعات المشروع** | [Projects](./MODULES.md#projects) | الوقت على مهام محددة — مقاييس تسليم المشروع |

يسجّل الموظف Attendance (للراتب) ويسجّل بشكل منفصل ساعات **سجل الوقت** على مهام المشروع (لتتبع التسليم). ساعات المشروع **لا تتطلب** موافقة المدير — الحالة تعكس التقدّم فقط.

المبرر: [Design Decisions — وقت المشروع منفصل عن Attendance](./DESIGN_DECISIONS.md#project-time-separate-from-attendance-time). سيناريو: [Use Cases — تسجيل وقت المشروع](./USE_CASES.md#log-project-time).

---

## تغييرات الباقة وظهور الوحدات {#plan-changes-and-module-visibility}

[Plans](./PLANS.md) لا تغيّر كيفية ترابط الوحدات داخلياً. تتحكم في **الظهور والوصول**:

- ترقية الباقة → تظهر وحدات جديدة في الشريط الجانبي → يهيئها العميل
- تخفيض الباقة أو تعطيل وحدة → تُخفى من التنقل وتُحظر
- تُحفظ بيانات الوحدات المعطّلة

[التخصيصات لكل عميل](./PLANS.md#per-customer-module-overrides) يمكنها تفعيل وحدات خارج الباقة (تجربة) أو تعطيل وحدات ضمن الباقة (قيود).

---

## إعدادات تؤثر على عدة وحدات {#configuration-affecting-multiple-modules}

إعدادات المؤسسة في قسم **Configuration** تؤثر على عدة وحدات دفعة واحدة:

| الإعداد | الوحدات المتأثرة |
|---------|------------------|
| العطل الرسمية | حسابات [Leave](./MODULES.md#leave)، [Attendance](./MODULES.md#attendance) |
| إجازات الشركة | أنماط أيام عدم العمل على مستوى المؤسسة |
| تقييد الإجازات | يمنع طلبات Leave في نطاقات تاريخية |
| الموافقات المتعددة | سلاسل موافقة متعددة الخطوات لـ Leave وطلبات أخرى |
| قوالب البريد | إشعارات البريد عبر جميع الوحدات |

يُعدّ مسؤولو HR هذه الإعدادات مرة واحدة؛ تنتشر آثارها إلى Leave و Attendance ورسائل Recruitment وغيرها.

---

## مستندات ذات صلة

- [Modules](./MODULES.md) — وصف كل وحدة
- [Features](./FEATURES.md) — قدرات الميزات بالتفصيل
- [Use Cases](./USE_CASES.md) — سيناريوهات سردية
- [Policies](./POLICIES.md) — القواعد التي تحكم هذه المسارات
- [Plans](./PLANS.md) — توفر الوحدات حسب الباقة
