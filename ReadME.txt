# PE Binary Analysis & Disassembler Tool

 وثيقة التوثيق والدليل التشغيلي للملف التنفيذي (PE x64 Assembly Document)

![Architecture](httpsimg.shields.iobadgeArchitecture-x86--64-blue)
![Platform](httpsimg.shields.iobadgePlatform-Windows-lightgrey)
![Compiler](httpsimg.shields.iobadgeCompiler-MSVC-purple)

---

## 📋 نبذة عن البرنامج (Overview)

هذا المشروع عبارة عن مكون تنفيذي منخفض المستوى (64-bit Windows Binary Component) مجمع باستخدام برمجيات Microsoft Visual C++. يضم البرنامج تعليمات تجميعية بمعمارية x86-64 مخصصة لإدارة مكدس الذاكرة، التفرعات الشرطية، وتفقد المؤشرات وآليات معالجة الاستثناءات (`C++ Exception Handling Unwinding`).

---

## ⚙️ المواصفات الفنية (Technical Specifications)

 المعيار  القيمة  الوصف 
 ---  --- 
 صيغة الملف (Format)  `Portable Executable (PE32+)` 
 المعمارية (Architecture)  `x86-64  AMD64` 
 نظام التشغيل  Windows (64-bit) 
 المجمع (Compiler)  Microsoft Visual CC++ (MSVC) 
 آليات الأمان (Security)  ASLR Enabled, DEPNX Compatible, Guard CF 

---

## 📁 هيكلية القطاعات (PE Section Layout)

يتكون الملف التنفيذي من القطاعات الرئيسية التالية

 `.text` قطاع التعليمات التنفيذية الرئيسية (Assembly Code).
 `.rdata` البيانات الثابتة للقراءة فقط وسلاسل النصوص وجداول الاستدعاء (Imports).
 `.data` المتغيرات العامّة المهيأة.
 `.pdata` جداول استثناءات x64 وإدارة المكدس (Unwind Info).
 `.rsrc` الموارد المدمجة (Icons, Version Info).

---

## 🛠️ كيفية الفحص والتفكيك (Analysis & Disassembly)

يمكنك فحص هذا الملف وتفكيكه باستخدام أدوات الهندسة العكسية والمعاينة التالية

```bash
# 1. فحص الترويسات باستخدام dumpbin
dumpbin headers program.exe

# 2. تفكيك قطاع التعليمات البرمجية
dumpbin disasm program.exe

# 3. التحقق من آليات الأمان
checksec --file=program.exe