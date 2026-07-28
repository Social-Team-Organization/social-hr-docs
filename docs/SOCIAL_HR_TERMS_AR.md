# Social HR — Arabic Terminology Map

Arabic UI/product terminology for **Social HR**, mapped from the English glossary
[`SOCIAL_HR_TERMS_GLOSSARY.md`](./SOCIAL_HR_TERMS_GLOSSARY.md).

Use this when localizing the tenant HR app, control plane, or training materials.
Prefer the Arabic in the **Arabic** column for every occurrence of the same English
term. Notes explain choices that differ from literal translation or need MENA HR context.

**Conventions used here**

- Saudi/GCC HR SaaS wording where a choice exists
- Check-In / Check-Out → تسجيل الحضور / تسجيل الانصراف
- Attendance → الحضور والانصراف (module); punch actions stay تسجيل الحضور/الانصراف
- Tenant (technical) → مستأجر (Tenant); product UI for the customer org → مؤسسة / عميل when clearer
- Timesheet → سجل الوقت
- Keep English in parentheses for technical codes when helpful

---

## Table of contents

1. [Master index (A–Z)](#master-index-az)
2. [Platform & tenancy](#1-platform--tenancy)
3. [Global chrome / navbar](#2-global-chrome--navbar)
4. [Dashboard tiles & panels](#3-dashboard-tiles--panels)
5. [Sidebar modules](#4-sidebar-modules)
6. [Settings (gear)](#5-settings-gear--general-settings)
7. [Geofencing / Work Type location policies](#6-geofencing--work-type-location-policies)
8. [Face check-in / re-enroll](#7-face-check-in--re-enroll)
9. [Employee profile tabs](#8-employee-profile-tabs)
10. [Project module — detailed terms](#9-project-module--detailed-terms)

---

## Master index (A–Z)

All unique English terms from the glossary with one Arabic form each.

| English | Arabic | Notes |
|---------|--------|-------|
| 360 Feedback | تقييم 360 درجة | Multi-rater feedback cycles |
| About | نبذة | Profile tab alias |
| Accessibility Restriction | قيود الوصول | Not a11y/screen-reader; controls who can see charts/features |
| Active (presence / is_active) | نشط | Soft-archive opposite of inactive |
| Activity | النشاط | Sidebar module |
| Activity Tracking | تتبع النشاط | Desktop monitoring policy |
| Allow clock-in from anywhere | السماح بتسجيل الحضور من أي مكان | Location policy `allow_anywhere` |
| Allowance & Deduction | البدلات والخصومات | Profile tab |
| Allowances | البدلات | Payroll earnings components |
| Announcements | الإعلانات | Dashboard panel |
| Archive | أرشفة | Soft-hide via `is_active` |
| Asset Batches | دفعات الأصول | Lots / procurement batches |
| Asset History | سجل الأصول | Assignment history |
| Asset Request | طلب أصل | FAB / assets |
| Asset Requests To Approve | طلبات الأصول بانتظار الموافقة | Dashboard queue |
| Asset View | عرض الأصول | Catalog / inventory |
| Assets | الأصول | Module + profile tab |
| Assigned Leave | الإجازات المخصصة | Leave balances assigned |
| Attendance | الحضور والانصراف | Module / concept |
| Attendance Activities | أنشطة الحضور | Raw in/out punch log |
| Attendance Analytics | تحليلات الحضور والانصراف | Dashboard charts |
| Attendance Break Point | عتبة التحقق من الحضور | Validation threshold — not a “breaking point” |
| Attendance Location Check | التحقق من موقع الحضور | Geofence audit record |
| Attendance Request | طلب حضور | Correction request |
| Attendance Requests | طلبات الحضور | Sidebar list |
| Attendance To Validate | حضور بانتظار التحقق | Dashboard queue |
| Attendances | سجلات الحضور والانصراف | All attendance records |
| Audit | التدقيق | Control-plane section |
| Bank Info / Bank Information | البيانات البنكية | Profile tab |
| Biometric Attendance | الحضور بالبصمة | Settings toggle |
| Biometric Devices | أجهزة البصمة | Hardware clock-in |
| Block clock-in | حظر تسجيل الحضور | Location policy `block_clock_in` |
| Bonus Point Setting | إعداد نقاط المكافأة | PMS settings |
| Bonus Points | نقاط المكافأة | Profile / PMS |
| Bypass geofence | تجاوز السياج الجغرافي | Employee work-info flag |
| Cancelled | ملغى | Project status |
| Candidate Reject Reason | سبب رفض المرشح | Recruitment setting |
| Candidate Self Tracking | تتبع المرشح الذاتي | Candidates track application |
| Candidates | المرشحون | Recruitment |
| Candidates Started Onboarding | مرشحون بدأوا التهيئة | Dashboard tile |
| Candidates view | عرض المرشحين | Onboarding context |
| Check In/Check Out (setting) | تسجيل الحضور/الانصراف | Feature enable setting |
| Check-In | تسجيل الحضور | Navbar clock-in |
| Check-Out | تسجيل الانصراف | Navbar clock-out |
| Company Leaves | إجازات الشركة | Recurring org-wide leave days |
| Compensatory Leave | إجازة تعويضية | Comp-off from OT |
| Compensatory Leave Requests | طلبات الإجازة التعويضية | Comp-off requests |
| Completed | مكتمل | Status (project / task / timesheet) |
| Configuration | إعدادات النظام | Sidebar Configuration menu (distinct from gear General Settings) |
| Contract | العقد | Salary contract |
| Control plane | لوحة التحكم | Public-schema staff console |
| Create Asset Request | إنشاء طلب أصل | FAB |
| Create Attendance Request | إنشاء طلب حضور | FAB |
| Create Leave Request | إنشاء طلب إجازة | FAB |
| Create Reimbursement | إنشاء طلب استرداد / صرف | FAB reimbursement/encashment |
| Create Shift Request | إنشاء طلب وردية | FAB |
| Create Ticket | إنشاء تذكرة | FAB Help Desk |
| Create Work Type Request | إنشاء طلب نوع عمل | FAB |
| Dashboard | لوحة المعلومات | Module home / overview |
| Dashboard Charts | مخططات لوحة المعلومات | FAB jump to analytics |
| Date & Time Format | تنسيق التاريخ والوقت | Settings |
| Deductions | الخصومات | Payroll |
| Delete | حذف | Hard delete |
| Department | القسم | Org unit |
| Department Chart | مخطط الأقسام | Headcount by department |
| Department Managers | مديرو الأقسام | Help Desk setting |
| Desktop | سطح المكتب | Navbar status chip |
| Desktop agent | وكيل سطح المكتب | Electron monitoring agent (technical) |
| Desktop App | تطبيق سطح المكتب | Social HR Desktop App |
| Disciplinary Action Type | نوع الإجراء التأديبي | Settings catalog |
| Disciplinary Actions | الإجراءات التأديبية | Employee module |
| Document Requests | طلبات المستندات | Employee module |
| Documents | المستندات | Profile tab |
| Employee | الموظف | Person / module |
| Employee Bonus Point | نقاط مكافأة الموظف | PMS ledger |
| Employee Permission | صلاحيات الموظف | Settings |
| Employee Shift | وردية الموظف | Shift definition |
| Employee Shift Schedule | جدول ورديات الموظف | Schedule rules |
| Employee Tags | وسوم الموظفين | Tag catalog |
| Employee Type | نوع الموظف | Full-time, contract, … |
| Employee Weekday Work Type | نوع عمل الموظف حسب أيام الأسبوع | Per-weekday override |
| Employee Work Information | معلومات عمل الموظف | Dashboard completeness panel |
| Employees | الموظفون | Directory |
| Employees Chart | مخطط الموظفين | Workforce chart |
| Encashments & Reimbursements | صرف الإجازات والمصروفات | Leave encashment + expenses |
| End stage | المرحلة النهائية | Project stage flag `Is end stage` |
| Exit Process | عملية إنهاء الخدمة | Offboarding checklist |
| Expired | منتهي | Project/task status |
| Face Check-In | تسجيل الحضور بالتعرف على الوجه | Webcam identity at clock-in |
| Face Re-enroll Requests | طلبات إعادة تسجيل التعرف على الوجه | Admin queue |
| Face Registration | تسجيل التعرف على الوجه | Enroll face templates |
| FAQs | الأسئلة الشائعة | Help Desk |
| Federal Tax | الضريبة الاتحادية | Where used |
| Feedback Status | حالة التقييم | PMS chart |
| Feedback To Answers | تقييمات بانتظار الرد | Dashboard queue |
| Field | ميداني | Work type preset |
| Gdrive Backup | النسخ الاحتياطي على Google Drive | Optional setting |
| Gender Chart | مخطط الجنس | Diversity chart |
| General Settings | الإعدادات العامة | Org-wide basics |
| Geo & Face Config | إعداد الموقع والوجه | Geofence + face geo config |
| Geofence | السياج الجغرافي | Lat/long/radius circle |
| Grace Time | فترة السماح | Late minutes before penalty |
| Groups & Permissions | المجموعات والصلاحيات | Profile tab |
| Heartbeat | نبضة | Desktop app periodic ping |
| Help Desk | مكتب المساعدة | Support module |
| Helpdesk Tags | وسوم مكتب المساعدة | Ticket tags |
| Hired Candidates | المرشحون المعيّنون | Dashboard |
| History | السجل | Change history |
| History Tags | وسوم السجل | Audit tag catalog |
| Holidays | العطل الرسمية | Public/org holidays |
| Hour Account | حساب الساعات | OT / hour bank (not Timesheet) |
| Hours Chart | مخطط الساعات | Worked-hours chart |
| Hours Spent | الساعات المستغرقة | Timesheet field `HH:MM` |
| Hybrid | هجين | Work type preset |
| Idle | خمول | Activity: no input |
| In Progress | قيد التنفيذ | Fast across project/task/timesheet |
| Inactive | غير نشط | Archived (`is_active=False`) |
| Interview | المقابلات | Recruitment |
| IP Restriction | تقييد عنوان IP | Attendance allowlist |
| Is end stage | مرحلة نهائية | Boolean on project stage |
| Job Positions | المسميات الوظيفية | Under departments |
| Job Role | الدور الوظيفي | Linked to positions |
| Key Result Status | حالة النتائج الرئيسية | PMS chart |
| Key Results | النتائج الرئيسية | Measurable KRs |
| Languages | اللغات | UI language switcher |
| Late Come Early Out | التأخر والانصراف المبكر | Late/early tracking |
| LDAP Configuration | إعداد LDAP | Optional AD sync |
| Leave | الإجازات | Module / profile tab |
| Leave Allocation Request | طلب تخصيص إجازة | Extra leave balance request |
| Leave Allocation Request To Approve | طلبات تخصيص إجازة بانتظار الموافقة | Dashboard |
| Leave Requests | طلبات الإجازة | Approver view |
| Leave Requests To Approve | طلبات إجازة بانتظار الموافقة | Dashboard |
| Leave Types | أنواع الإجازات | Annual, sick, … |
| LinkedIn Integration | تكامل LinkedIn | Recruitment setting |
| Loan / Advanced Salary | القروض والسلف | Payroll |
| Location policy | سياسة الموقع | Per work type clock-in rule |
| Mail Automations | أتمتة البريد | Event-triggered email |
| Mail Log | سجل البريد | Emails about employee |
| Mail Server | خادم البريد | SMTP / Outlook Mail |
| Mail Templates | قوالب البريد | Reusable email bodies |
| Manager decision | قرار المدير | Paid / Unpaid / Meeting on review |
| Media / uploads | الوسائط / الملفات المرفوعة | Schema-prefixed paths |
| Meeting (activity decision) | اجتماع | Review segment classification |
| Meetings | الاجتماعات | PMS 1:1 / performance meetings |
| Module / modules | الوحدة / الوحدات | Plan entitlements |
| Modules | الوحدات | Control-plane section |
| Multiple Approvals | الموافقات المتعددة | Multi-step approval chains |
| My Activity | نشاطي | Employee desktop activity |
| My Attendances | حضوري | Own attendance |
| My Leave Requests | طلبات إجازتي | Own leave |
| My Profile | ملفي الشخصي | Self profile |
| New | جديد | Project status |
| New Joining This Week | انضمام جديد هذا الأسبوع | Dashboard tile |
| New Joining Today | انضمام جديد اليوم | Dashboard tile |
| Note | ملاحظة | Free-form HR notes |
| Notifications / All Notifications | الإشعارات / كل الإشعارات | Tray |
| Objective Status | حالة الأهداف | PMS chart |
| Objectives | الأهداف | PMS goals |
| Office | مكتبي | Work type preset |
| Offline Employees | موظفون غير متصلين | Presence panel |
| On Hold | معلّق | Project status paused |
| On Leave | في إجازة | Dashboard panel |
| Onboarding | التهيئة | New-hire process (formerly also الالتحاق; product preference is التهيئة) |
| Onboarding view | عرض التهيئة | Onboarding board |
| Online Employees | موظفون متصلون | Presence panel |
| Open Jobs | الوظائف المفتوحة | Active openings |
| Organization Chart | الهيكل التنظيمي | Reporting structure |
| Outlook Mail | بريد Outlook | Optional mail app |
| Overall Leave | ملخص الإجازات | Leave summary filters |
| Overtime To Approve | عمل إضافي بانتظار الموافقة | Dashboard queue |
| Paid | مدفوع | Manager decision on review |
| Payslip Auto Generation | إنشاء قسائم الراتب تلقائياً | Payroll setting |
| Payslips | قسائم الراتب | Generated pay statements |
| Penalty Account | حساب الجزاءات | Late-related penalties |
| Performance | الأداء | PMS module / profile |
| Period | الفترة | Review period / cycle |
| Personal Info / Personal Information | المعلومات الشخصية | Profile tab |
| Pipeline | مسار التوظيف | Hiring funnel (Recruitment Pipeline) |
| Plan | الباقة | Subscription package |
| Plan & modules | الباقة والوحدات | Entitlements |
| Policies | السياسات | Company policy documents |
| Productivity score | درجة الإنتاجية | Activity indicator — not payslip |
| Profile | الملف الشخصي | Navbar / employee |
| Project | مشروع | Core entity |
| Project Manager / Project Managers | مدير المشروع / مديرو المشروع | M2M leads |
| Project Member / Project Members | عضو المشروع / أعضاء المشروع | Contributors |
| Project Stage | مرحلة المشروع | Kanban column |
| Project statuses | حالات المشروع | See §9 |
| Projects | المشاريع | Sidebar menu |
| Public schema | المخطط العام | Control-plane DB schema |
| Question Template | قالب الأسئلة | 360 / feedback templates |
| Quick Action FAB | زر الإجراءات السريعة | Floating action button |
| Recruitment | التوظيف | Module |
| Recruitment Analytics | تحليلات التوظيف | Dashboard |
| Recruitment Pipeline | مسار التوظيف | Kanban by stage |
| Recruitment Survey | استبيان التوظيف | Candidate surveys |
| Remote | عن بُعد | Work type / WFH |
| Request and Allocation | الطلب والتخصيص | Assets issue/return |
| Require inside office geofence | يتطلب التواجد داخل السياج الجغرافي للمكتب | `require_inside_geofence` |
| Resignation Letters | خطابات الاستقالة | Offboarding |
| Restrict Leaves | تقييد الإجازات | Peak-season leave rules |
| Restrictions | القيود | Leave application restrictions |
| Review / Review required | مراجعة / يتطلب مراجعة | Long idle segment |
| Rotating Shift | وردية متناوبة | Pattern definition |
| Rotating Shift Assign | تعيين الوردية المتناوبة | Assignment |
| Rotating Work Type | نوع عمل متناوب | Pattern definition |
| Rotating Work Type Assign | تعيين نوع العمل المتناوب | Assignment |
| Schema | مخطط قاعدة البيانات | Technical isolation (not UI) |
| Screenshots | لقطات الشاشة | Optional activity captures |
| Settings | الإعدادات | Gear hub |
| Shift | الوردية | Work schedule shift |
| Shift Request | طلب وردية | Temporary shift change |
| Shift Requests | طلبات الورديات | Sidebar |
| Shift Requests To Approve | طلبات وردية بانتظار الموافقة | Dashboard |
| Skill Zone | مجمع المهارات | Candidate/talent pool, not a geographic zone (alt. بنك المواهب) |
| Skills | المهارات | Recruitment skill catalog |
| Stages | المراحل | Pipeline / project stages |
| Subdomain | النطاق الفرعي | Tenant hostname |
| Suspended / cancelled tenant | مؤسسة موقوفة / ملغاة | Blocks HR login (customer-facing) |
| Task | مهمة | Work item |
| Task Manager / Task Managers | مدير المهمة / مديرو المهمة | Task ownership |
| Task Member / Task Members | عضو المهمة / أعضاء المهمة | Assignees |
| Task statuses | حالات المهمة | See §9 |
| Tasks | المهام | Sidebar menu |
| Team Activity | نشاط الفريق | Manager activity view |
| Tenant | مستأجر (Tenant) | Technical tenancy; UI: مؤسسة / عميل |
| Tenant HR app | تطبيق الموارد البشرية للمؤسسة | Subdomain product (customer-facing) |
| Ticket Type | نوع التذكرة | Help Desk categories |
| Tickets | التذاكر | Support tickets |
| Timesheet | سجل الوقت | Hours log — progress, not approval |
| Timesheet statuses | حالات سجل الوقت | In Progress / Completed only |
| To Do | للإنجاز | Task status default |
| Todo (default stage) | للقيام به (Todo) | Default first project stage |
| Total Strength | إجمالي القوى العاملة | Active headcount tile |
| Track Late Come & Early Out | تتبع التأخر والانصراف المبكر | Settings toggle |
| Tracking required for clock-in | التتبع مطلوب لتسجيل الحضور | Activity policy |
| Un-Archive | إلغاء الأرشفة | Restore soft-hidden |
| Unpaid | غير مدفوع | Manager decision on review |
| User Group | مجموعة المستخدمين | Permission groups |
| Work Records | سجلات العمل | Day-level payroll-oriented matrix |
| Work Type | نوع العمل | Office / Remote / Hybrid / Field |
| Work Type & Shift | نوع العمل والوردية | Profile tab |
| Work Type Request | طلب نوع عمل | Temporary type for dates |
| Work Type Requests | طلبات نوع العمل | Sidebar |
| Work Type Requests To Approve | طلبات نوع عمل بانتظار الموافقة | Dashboard |

---

## 1. Platform & tenancy

| English | Arabic | Notes |
|---------|--------|-------|
| Tenant | مستأجر (Tenant) | Technical isolation unit; in product copy prefer **مؤسسة** or **عميل** for the customer org |
| Schema | مخطط قاعدة البيانات | Not a UI label; PostgreSQL schema |
| Subdomain | النطاق الفرعي | e.g. `acme.example.com` |
| Public schema | المخطط العام | Control-plane data |
| Control plane | لوحة التحكم | Staff: Overview, Tenants, Plans, Modules, Audit |
| Overview | نظرة عامة | Control-plane home |
| Tenants | المستأجرون / المؤسسات | Control-plane list; UI may say المؤسسات |
| Plans | الباقات | Subscription packages |
| Modules | الوحدات | Entitled HR apps |
| Audit | التدقيق | Staff action audit |
| Tenant HR app | تطبيق الموارد البشرية للمؤسسة | Full product on tenant subdomain (customer-facing) |
| Plan & modules | الباقة والوحدات | Subscription entitlements |
| Plan | الباقة | Subscription tier |
| Module entitlement | استحقاق الوحدة | Plan ± overrides |
| Suspended tenant | مؤسسة موقوفة | Blocks normal HR login (customer-facing) |
| Cancelled tenant | مؤسسة ملغاة | Lifecycle / billing (customer-facing) |
| Media / uploads | الوسائط / الملفات المرفوعة | Paths prefixed with schema name |
| Desktop agent | وكيل سطح المكتب | Electron agent (technical) |
| Social HR Desktop App | تطبيق Social HR لسطح المكتب | Product name — keep Social HR |
| Company (removed) | — | No Company model; do not translate as شركة switcher |

---

## 2. Global chrome / navbar

| English | Arabic | Notes |
|---------|--------|-------|
| Check-In | تسجيل الحضور | Navbar clock-in |
| Check-Out | تسجيل الانصراف | Navbar clock-out |
| Desktop | سطح المكتب | Status chip near check-in |
| Languages | اللغات | Language switcher |
| All Notifications | كل الإشعارات | Tray / sidebar |
| Notifications | الإشعارات | In-app alerts |
| Settings | الإعدادات | Gear → settings hub |
| Profile | الملف الشخصي | User menu |
| Quick Action | إجراء سريع | FAB label |
| Quick Action FAB | زر الإجراءات السريعة | Floating button |

### Quick Action FAB items

| English | Arabic | Notes |
|---------|--------|-------|
| Create Attendance Request | إنشاء طلب حضور | Fix missed punches |
| Create Leave Request | إنشاء طلب إجازة | Time off |
| Create Shift Request | إنشاء طلب وردية | Temporary schedule change |
| Create Work Type Request | إنشاء طلب نوع عمل | e.g. Remote for a day |
| Create Reimbursement | إنشاء طلب استرداد / صرف | Expense or leave encashment |
| Create Asset Request | إنشاء طلب أصل | Hardware / equipment |
| Create Ticket | إنشاء تذكرة | Help Desk |
| Dashboard Charts | مخططات لوحة المعلومات | Jump to analytics |

---

## 3. Dashboard tiles & panels

### Headcount tiles

| English | Arabic | Notes |
|---------|--------|-------|
| New Joining Today | انضمام جديد اليوم | Joiners whose date is today |
| New Joining This Week | انضمام جديد هذا الأسبوع | Weekly hiring pulse |
| Total Strength | إجمالي القوى العاملة | Active headcount |

### People & communication

| English | Arabic | Notes |
|---------|--------|-------|
| Announcements | الإعلانات | Company notices |
| On Leave | في إجازة | Currently on approved leave |
| Employee Work Information | معلومات عمل الموظف | Incomplete work-info panel |

### Presence

| English | Arabic | Notes |
|---------|--------|-------|
| Offline Employees | موظفون غير متصلين | Not marked online |
| Online Employees | موظفون متصلون | Live session presence |

### Approval queues

| English | Arabic | Notes |
|---------|--------|-------|
| Leave Requests To Approve | طلبات إجازة بانتظار الموافقة | |
| Leave Allocation Request To Approve | طلبات تخصيص إجازة بانتظار الموافقة | Extra leave days |
| Work Type Requests To Approve | طلبات نوع عمل بانتظار الموافقة | e.g. Remote |
| Shift Requests To Approve | طلبات وردية بانتظار الموافقة | |
| Attendance To Validate | حضور بانتظار التحقق | Before payroll |
| Overtime To Approve | عمل إضافي بانتظار الموافقة | |
| Feedback To Answers | تقييمات بانتظار الرد | 360 / PMS |
| Asset Requests To Approve | طلبات الأصول بانتظار الموافقة | |

### Recruitment & attendance analytics

| English | Arabic | Notes |
|---------|--------|-------|
| Recruitment Analytics | تحليلات التوظيف | Hiring funnel charts |
| Hours Chart | مخطط الساعات | Worked hours |
| Hired Candidates | المرشحون المعيّنون | Recent hires |
| Candidates Started Onboarding | مرشحون بدأوا التهيئة | Recruit → onboard |
| Overall Leave | ملخص الإجازات | Today / Week / Month / Year |
| Attendance Analytics | تحليلات الحضور والانصراف | Day / Weekly / Monthly |
| Today | اليوم | Filter |
| This Week | هذا الأسبوع | Filter |
| This Month | هذا الشهر | Filter |
| This Year | هذه السنة | Filter |
| Day | يومي | Attendance analytics filter |
| Weekly | أسبوعي | Filter |
| Monthly | شهري | Filter |
| Date range | نطاق التاريخ | Filter |

### Workforce composition charts

| English | Arabic | Notes |
|---------|--------|-------|
| Gender Chart | مخطط الجنس | Permission-gated |
| Department Chart | مخطط الأقسام | Org shape |
| Employees Chart | مخطط الموظفين | Workforce overview |

### Performance status charts

| English | Arabic | Notes |
|---------|--------|-------|
| Objective Status | حالة الأهداف | PMS |
| Key Result Status | حالة النتائج الرئيسية | Goal execution |
| Feedback Status | حالة التقييم | 360 completion |

---

## 4. Sidebar modules

### Recruitment

| English | Arabic | Notes |
|---------|--------|-------|
| Recruitment | التوظيف | Module |
| Dashboard | لوحة المعلومات | Recruitment KPIs |
| Recruitment Pipeline | مسار التوظيف | Kanban by stage |
| Recruitment Survey | استبيان التوظيف | Screening templates |
| Candidates | المرشحون | Applicant records |
| Interview | المقابلات | Interview schedules |
| Open Jobs | الوظائف المفتوحة | Active openings |
| Stages | المراحل | Pipeline stage definitions |
| Skill Zone | مجمع المهارات | Candidate/talent pool, not a geographic zone (alt. بنك المواهب) |
| Candidate Self Tracking | تتبع المرشح الذاتي | Settings |
| Candidate Reject Reason | سبب رفض المرشح | Settings |
| Skills | المهارات | Settings catalog |
| LinkedIn Integration | تكامل LinkedIn | Settings |

### Onboarding

| English | Arabic | Notes |
|---------|--------|-------|
| Onboarding | التهيئة | New-hire process |
| Onboarding view | عرض التهيئة | Process board |
| Candidates view | عرض المرشحين | Onboarding context |

### Employee

| English | Arabic | Notes |
|---------|--------|-------|
| Employee | الموظف | Module |
| Profile | الملف الشخصي | Current user |
| Employees | الموظفون | Directory |
| Document Requests | طلبات المستندات | Ask for uploads |
| Shift Requests | طلبات الورديات | |
| Work Type Requests | طلبات نوع العمل | WFH / field days |
| Rotating Shift Assign | تعيين الوردية المتناوبة | |
| Rotating Work Type Assign | تعيين نوع العمل المتناوب | |
| Disciplinary Actions | الإجراءات التأديبية | |
| Policies | السياسات | Policy documents |
| Organization Chart | الهيكل التنظيمي | Reporting tree |

### Attendance

| English | Arabic | Notes |
|---------|--------|-------|
| Attendance | الحضور والانصراف | Module name |
| Dashboard | لوحة المعلومات | Manager analytics |
| Biometric Devices | أجهزة البصمة | Hardware |
| Attendances | سجلات الحضور والانصراف | All records |
| Attendance Requests | طلبات الحضور | Corrections |
| Hour Account | حساب الساعات | OT / hour bank — not Timesheet |
| Work Records | سجلات العمل | Day-level payroll matrix |
| Attendance Activities | أنشطة الحضور | Raw punch trail |
| Late Come Early Out | التأخر والانصراف المبكر | |
| My Attendances | حضوري | Self-service |

### Activity

| English | Arabic | Notes |
|---------|--------|-------|
| Activity | النشاط | Module |
| My Activity | نشاطي | Employee day view |
| Team Activity | نشاط الفريق | Manager view |
| Desktop App | تطبيق سطح المكتب | Setup / diagnostics |

#### Activity tracking policy terms

| English | Arabic | Notes |
|---------|--------|-------|
| Activity Tracking | تتبع النشاط | Settings → Attendance |
| Heartbeat | نبضة | Periodic desktop ping |
| Idle | خمول | After `idle_after_seconds` |
| Review | مراجعة | Longer idle segment |
| Review required | يتطلب مراجعة | Manager must classify |
| Manager decision | قرار المدير | On review segment |
| Paid | مدفوع | Counts as paid time |
| Unpaid | غير مدفوع | Does not count as paid |
| Meeting | اجتماع | Classified as meeting |
| Screenshots | لقطات الشاشة | Optional captures |
| Productivity score | درجة الإنتاجية | Not a payslip field |
| Tracking required for clock-in | التتبع مطلوب لتسجيل الحضور | Policy toggle |

### Leave

| English | Arabic | Notes |
|---------|--------|-------|
| Leave | الإجازات | Module |
| Dashboard | لوحة المعلومات | Leave analytics |
| My Leave Requests | طلبات إجازتي | Self-service |
| Leave Requests | طلبات الإجازة | Approver view |
| Leave Types | أنواع الإجازات | Annual, sick, … |
| Assigned Leave | الإجازات المخصصة | Balances |
| Leave Allocation Request | طلب تخصيص إجازة | Extra allocation |
| Compensatory Leave Requests | طلبات الإجازة التعويضية | Comp-off |

### Payroll

| English | Arabic | Notes |
|---------|--------|-------|
| Payroll | الرواتب | Module |
| Dashboard | لوحة المعلومات | Period overview |
| Contract | العقد | Salary contract |
| Allowances | البدلات | Earnings |
| Deductions | الخصومات | Deductions |
| Payslips | قسائم الراتب | Pay statements |
| Payslip | قسيمة الراتب | Singular |
| Loan / Advanced Salary | القروض والسلف | Recoverable payouts |
| Encashments & Reimbursements | صرف الإجازات والمصروفات | Non-salary payouts |
| Federal Tax | الضريبة الاتحادية | Where used |

### Performance (PMS)

| English | Arabic | Notes |
|---------|--------|-------|
| Performance | الأداء | PMS module |
| Dashboard | لوحة المعلومات | |
| Objectives | الأهداف | Goals |
| 360 Feedback | تقييم 360 درجة | Multi-rater |
| Meetings | الاجتماعات | 1:1 / performance |
| Key Results | النتائج الرئيسية | KRs under objectives |
| Employee Bonus Point | نقاط مكافأة الموظف | Points ledger |
| Period | الفترة | Review cycle |
| Question Template | قالب الأسئلة | Feedback questions |

### Offboarding

| English | Arabic | Notes |
|---------|--------|-------|
| Offboarding | إنهاء الخدمة | Module |
| Dashboard | لوحة المعلومات | Exit overview |
| Exit Process | عملية إنهاء الخدمة | Checklist / stages |
| Resignation Letters | خطابات الاستقالة | Formal intake |

### Assets

| English | Arabic | Notes |
|---------|--------|-------|
| Assets | الأصول | Module |
| Dashboard | لوحة المعلومات | Asset KPIs |
| Asset View | عرض الأصول | Catalog |
| Asset Batches | دفعات الأصول | Lots |
| Request and Allocation | الطلب والتخصيص | Issue and return |
| Asset History | سجل الأصول | Assignment history |
| Asset Request | طلب أصل | Employee request |

### Help Desk

| English | Arabic | Notes |
|---------|--------|-------|
| Help Desk | مكتب المساعدة | Module |
| FAQs | الأسئلة الشائعة | Self-help |
| Tickets | التذاكر | Support tickets |
| Ticket | تذكرة | Singular |
| Ticket Type | نوع التذكرة | Categories |
| Helpdesk Tags | وسوم مكتب المساعدة | Tags |
| Department Managers | مديرو الأقسام | Help-desk routing |

### Project (menu)

| English | Arabic | Notes |
|---------|--------|-------|
| Project | مشروع | Module / entity — see §9 |
| Dashboard | لوحة المعلومات | Project/task metrics |
| Projects | المشاريع | Manage projects |
| Tasks | المهام | Cross-project tasks |
| Timesheet | سجل الوقت | Hours log; **not** approval |

### Configuration (sidebar)

| English | Arabic | Notes |
|---------|--------|-------|
| Configuration | إعدادات النظام | Sidebar Configuration menu; gear hub stays الإعدادات العامة (General Settings) |
| Multiple Approvals | الموافقات المتعددة | Multi-step chains |
| Mail Templates | قوالب البريد | Email bodies |
| Mail Automations | أتمتة البريد | Event-triggered |
| Holidays | العطل الرسمية | Calendar |
| Company Leaves | إجازات الشركة | Recurring org-wide non-working days |
| Restrict Leaves | تقييد الإجازات | Peak-season rules |

---

## 5. Settings (gear / general settings)

### General

| English | Arabic | Notes |
|---------|--------|-------|
| General Settings | الإعدادات العامة | Org-wide basics |
| Employee Permission | صلاحيات الموظف | Permission matrix |
| Accessibility Restriction | قيود الوصول | Not a11y/screen-reader; who can see charts/features |
| User Group | مجموعة المستخدمين | Groups |
| Date & Time Format | تنسيق التاريخ والوقت | Display formats |
| History Tags | وسوم السجل | Audit tags |
| Mail Server | خادم البريد | SMTP |
| Outlook Mail | بريد Outlook | If Outlook app installed |
| Gdrive Backup | النسخ الاحتياطي على Google Drive | Optional |
| LDAP Configuration | إعداد LDAP | Optional AD sync |

### Base

| English | Arabic | Notes |
|---------|--------|-------|
| Department | القسم | Org departments |
| Job Positions | المسميات الوظيفية | Under departments |
| Job Role | الدور الوظيفي | Linked to positions |

### Recruitment (settings)

| English | Arabic | Notes |
|---------|--------|-------|
| Candidate Self Tracking | تتبع المرشح الذاتي | |
| Candidate Reject Reason | سبب رفض المرشح | |
| Skills | المهارات | |
| LinkedIn Integration | تكامل LinkedIn | |

### Employee (settings)

| English | Arabic | Notes |
|---------|--------|-------|
| Work Type | نوع العمل | Includes Location policy |
| Rotating Work Type | نوع عمل متناوب | Patterns |
| Employee Shift | وردية الموظف | Start/end times |
| Rotating Shift | وردية متناوبة | Patterns |
| Employee Shift Schedule | جدول ورديات الموظف | Schedule rules |
| Employee Type | نوع الموظف | Full-time, contract, … |
| Disciplinary Action Type | نوع الإجراء التأديبي | Catalog |
| Employee Tags | وسوم الموظفين | Tag catalog |

### Attendance (settings)

| English | Arabic | Notes |
|---------|--------|-------|
| Track Late Come & Early Out | تتبع التأخر والانصراف المبكر | On/off |
| Attendance Break Point | عتبة التحقق من الحضور | Validation threshold — not a “breaking point” |
| Check In/Check Out | تسجيل الحضور/الانصراف | Enable navbar/web |
| Face Check-In | تسجيل الحضور بالتعرف على الوجه | Webcam verify |
| Face Re-enroll Requests | طلبات إعادة تسجيل التعرف على الوجه | Admin queue |
| Grace Time | فترة السماح | Late minutes before penalty |
| Biometric Attendance | الحضور بالبصمة | Enable flag |
| IP Restriction | تقييد عنوان IP | Allowlist |
| Geo & Face Config | إعداد الموقع والوجه | Circles + face geo |
| Activity Tracking | تتبع النشاط | Desktop policy |

### Leave (settings)

| English | Arabic | Notes |
|---------|--------|-------|
| Restrictions | القيود | Past-leave / apply rules |
| Compensatory Leave | إجازة تعويضية | Comp-off from OT |

### Payroll (settings)

| English | Arabic | Notes |
|---------|--------|-------|
| Payslip Auto Generation | إنشاء قسائم الراتب تلقائياً | Schedule/auto-create |

### Performance (settings)

| English | Arabic | Notes |
|---------|--------|-------|
| Bonus Point Setting | إعداد نقاط المكافأة | Award rules |

### Help Desk (settings)

| English | Arabic | Notes |
|---------|--------|-------|
| Department Managers | مديرو الأقسام | Map depts to HD managers |
| Ticket Type | نوع التذكرة | Categories |
| Helpdesk Tags | وسوم مكتب المساعدة | Ticket tags |

---

## 6. Geofencing / Work Type location policies

### Concepts

| English | Arabic | Notes |
|---------|--------|-------|
| Geofence | السياج الجغرافي | Lat, long, radius (meters) |
| Work Type | نوع العمل | Default or via Work Type Request |
| Location policy | سياسة الموقع | Clock-in rule when geofence active |
| Attendance Location Check | التحقق من موقع الحضور | Audit of evaluation |
| Started (geofence) | مفعّل / بدأ | Geofence must be started to enforce |

### Preset work types

| English | Arabic | Notes |
|---------|--------|-------|
| Office | مكتبي | Require inside office geofence |
| Remote | عن بُعد | Clock-in from anywhere (WFH) |
| Hybrid | هجين | Mix; often weekday overrides |
| Field | ميداني | Field sales / site visits |

### Location policies (UI wording)

| English | Arabic | Notes |
|---------|--------|-------|
| Require inside office geofence | يتطلب التواجد داخل السياج الجغرافي للمكتب | Code: `require_inside_geofence` |
| Allow clock-in from anywhere | السماح بتسجيل الحضور من أي مكان | Code: `allow_anywhere` |
| Block clock-in | حظر تسجيل الحضور | Code: `block_clock_in` |

### Key policy fields

| English | Arabic | Notes |
|---------|--------|-------|
| Location policy | سياسة الموقع | On Work Type |
| Bypass geofence | تجاوز السياج الجغرافي | On employee work information |
| Employee Weekday Work Type | نوع عمل الموظف حسب أيام الأسبوع | e.g. Friday = Remote |
| Work Type Request | طلب نوع عمل | Approved temporary override |
| Geo & Face Config | إعداد الموقع والوجه | Define and start/stop geofence |

---

## 7. Face check-in / re-enroll

| English | Arabic | Notes |
|---------|--------|-------|
| Face Registration | تسجيل التعرف على الوجه | Enroll templates |
| Face Check-In | تسجيل الحضور بالتعرف على الوجه | Webcam at clock-in |
| Face Re-enroll Requests | طلبات إعادة تسجيل التعرف على الوجه | Reset / re-capture |
| Geo & Face Config | إعداد الموقع والوجه | Combined geo/face setup |

---

## 8. Employee profile tabs

| English | Arabic | Notes |
|---------|--------|-------|
| My Profile | ملفي الشخصي | Self view |
| Personal Info | المعلومات الشخصية | Edit forms often use this |
| Personal Information | المعلومات الشخصية | Alias |
| About | نبذة | Alias on some views |
| Bank Info | البيانات البنكية | Short form |
| Bank Information | البيانات البنكية | Full form |
| Work Type & Shift | نوع العمل والوردية | Includes bypass geofence |
| Attendance | الحضور والانصراف | History on profile |
| Face Registration | تسجيل التعرف على الوجه | Face template enroll (distinct from fingerprint biometric) |
| Leave | الإجازات | Balances & requests |
| Payroll | الرواتب | Payslip/contract snapshot |
| Allowance & Deduction | البدلات والخصومات | Gross-to-net components |
| Penalty Account | حساب الجزاءات | e.g. late-related |
| Documents | المستندات | Files & requests |
| History | السجل | Change audit |
| Assets | الأصول | Assigned assets |
| Performance | الأداء | PMS snapshot |
| Groups & Permissions | المجموعات والصلاحيات | Access control |
| Note | ملاحظة | Internal HR notes |
| Mail Log | سجل البريد | Emails about employee |
| Bonus Points | نقاط المكافأة | PMS rewards |

---

## 9. Project module — detailed terms

### Menu

| English | Arabic | Notes |
|---------|--------|-------|
| Dashboard | لوحة المعلومات | Metrics for managers |
| Projects | المشاريع | Create/manage projects |
| Tasks | المهام | Cross-project work |
| Timesheet | سجل الوقت | Progress status only — not approval |

### Core entities & fields

| English | Arabic | Notes |
|---------|--------|-------|
| Project | مشروع | Named initiative |
| Name | الاسم | Project field |
| Description | الوصف | Project / timesheet |
| File | ملف | Attachment |
| Status | الحالة | Entity status |
| Project Manager | مدير المشروع | Lead |
| Project Managers | مديرو المشروع | M2M |
| Project Member | عضو المشروع | Contributor |
| Project Members | أعضاء المشروع | M2M |
| Project Stage | مرحلة المشروع | Kanban column |
| Stage | مرحلة | Short form |
| Title | العنوان | Stage / task title |
| Sequence | الترتيب | Stage order |
| Todo | للقيام به (Todo) | Default first stage |
| End stage | المرحلة النهائية | Exactly one per project |
| Is end stage | مرحلة نهائية | Boolean flag |
| Task | مهمة | Work item |
| Task Manager | مدير المهمة | Task ownership |
| Task Managers | مديرو المهمة | |
| Task Member | عضو المهمة | Assignee |
| Task Members | أعضاء المهمة | |
| Timesheet | سجل الوقت | Time entry |
| Employee | الموظف | Timesheet field |
| Date | التاريخ | Timesheet field |
| Hours Spent | الساعات المستغرقة | Must be `HH:MM` |
| Reporting manager | المدير المباشر | Access context |

### Project statuses

| Code | English (UI) | Arabic |
|------|--------------|--------|
| `new` | New | جديد |
| `in_progress` | In Progress | قيد التنفيذ |
| `completed` | Completed | مكتمل |
| `on_hold` | On Hold | معلّق |
| `cancelled` | Cancelled | ملغى |
| `expired` | Expired | منتهي |

### Task statuses

| Code | English (UI) | Arabic |
|------|--------------|--------|
| `to_do` | To Do | للإنجاز |
| `in_progress` | In Progress | قيد التنفيذ |
| `completed` | Completed | مكتمل |
| `expired` | Expired | منتهي |

### Timesheet statuses (not approval)

| Code | English (UI) | Arabic | Notes |
|------|--------------|--------|-------|
| `in_Progress` | In Progress | قيد التنفيذ | Entry still open |
| `completed` | Completed | مكتمل | Entry finished |

There is **no timesheet approval** in this product. Do not translate status as «بانتظار الموافقة».

### Archive vs delete

| English | Arabic | Notes |
|---------|--------|-------|
| Archive | أرشفة | Soft-hide (`is_active`) |
| Un-Archive | إلغاء الأرشفة | Restore to active lists |
| Delete | حذف | Permanent remove |
| Active | نشط | `is_active=True` |
| Inactive | غير نشط | Archived |

### Permissions (plain roles)

| English | Arabic | Notes |
|---------|--------|-------|
| Project menu | قائمة المشاريع | App perms or membership |
| view_project | عرض المشروع | Permission code — keep English in tech docs |
| view_task | عرض المهمة | Permission code |
| view_timesheet | عرض سجل الوقت | Permission code |
| Project Manager | مدير المشروع | Elevated on that project |
| Project Member | عضو المشروع | Day-to-day contributor |
| Task Manager | مدير المهمة | Task-level ownership |
| Task Member | عضو المهمة | Assigned worker |

### Project terms quick table

| English | Arabic | Notes |
|---------|--------|-------|
| Project | مشروع | Initiative with dates, people, stages |
| Project Manager | مدير المشروع | Lead with management access |
| Project Member | عضو المشروع | Contributor |
| Project Stage | مرحلة المشروع | Kanban; optional single end stage |
| Todo stage | مرحلة «للقيام به» | Default first stage |
| Task | مهمة | Work item in a stage |
| Timesheet | سجل الوقت | Hours on project/task for a date |
| Archive | أرشفة | Soft-deactivate |
| Timesheet status | حالة سجل الوقت | In Progress / Completed only |

---

## Consistency cheat sheet

| English family | Stick to this Arabic |
|----------------|----------------------|
| Check-In / Check-Out | تسجيل الحضور / تسجيل الانصراف |
| Attendance (module) | الحضور والانصراف |
| Leave | الإجازات |
| Payroll / Payslip | الرواتب / قسيمة الراتب |
| Timesheet vs Hour Account | سجل الوقت vs حساب الساعات |
| Project / Task / Stage | مشروع / مهمة / مرحلة |
| Work Type / Shift | نوع العمل / الوردية |
| Geofence | السياج الجغرافي |
| Configuration (sidebar) vs General Settings (gear) | إعدادات النظام vs الإعدادات العامة |
| Face Check-In | تسجيل الحضور بالتعرف على الوجه |
| Desktop App | تطبيق سطح المكتب |
| Announcements | الإعلانات |
| In Progress (any entity) | قيد التنفيذ |
| Tenant (tech) vs org (UI) | مستأجر (Tenant) vs مؤسسة / عميل |

---

## Related docs

- [SOCIAL_HR_TERMS_GLOSSARY.md](./SOCIAL_HR_TERMS_GLOSSARY.md) — English product glossary (source)
- [CONTROL_PLANE.md](./CONTROL_PLANE.md) — public schema staff console

---

*Arabic map aligned to English terms in `SOCIAL_HR_TERMS_GLOSSARY.md`. Prefer one Arabic form per English term across the product.*
