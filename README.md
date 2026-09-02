# 🏛️ Stellarium Planner V3.2 / V4.0

> **Daily Study Gazette & Execution Engine**  
> یک داشبورد تک‌فایلی (Single-File)، مدرن و ایزوله برای مدیریت زمان، برنامه‌ریزی روزانه، پومودورو و ردیابی پیشرفت کنکور ۱۴۰۵ / ۱۴۰۶ با زیبایی‌شناسی Dark Academia و Minimalist Eleganza.

---

## 📌 معرفی پروژه

**Stellarium Planner** یک وب‌اپلیکیشن بدون وابستگی به سرور (Zero-Dependency Single-File Web App) است که اختصاصاً برای داوطلبان کنکور و زبان‌آموزانی که نیازمند دقت بالا، مدیریت پارت‌های مطالعه و حفظ تمرکز ذهنی هستند طراحی شده است. این ابزار بدون نیاز به نصب یا پیکربندی پیچیده، تمام داده‌های کاربر را به صورت محلی در مرورگر ذخیره کرده و تجربه کاربری روان و سریعی را ارائه می‌دهد[cite: 1].

---

## ✨ ویژگی‌های کلیدی

* **📅 مدیریت برنامه‌ریزی ۷ روز هفته (Weekly Tab System):** تفکیک داده‌ها، پارت‌های آموزشی و وضعیت تیک‌زنی برای هر یک از روزهای هفته (شنبه تا جمعه) به صورت مستقل[cite: 1].
* **⏱️ موتور تایمر و حالت فوکوس (Active Session & Focus Mode):**
  * تایمر معکوس برای هر پارت مطالعاتی با قابلیت توقف، ادامه و بازنشانی[cite: 1].
  * مدال صریح تمرکز (Focus Overlay) همراه با ویژوالایزر پیشرفت و تایمر بزرگ جهت کاهش حواس‌پرتی[cite: 1].
  * علامت‌گذاری خودکار پارت در جدول پس از اتمام تایمر[cite: 1].
* **⌛ محاسبه‌گر زمان پویا (Dynamic Time Engine):** تنظیم ساعت شروع روز و استخراج و بروزرسانی بازه‌های زمانی تمام پارت‌های مطالعه بر اساس مدت زمان تعیین‌شده[cite: 1].
* **🎨 پالت‌های رنگی پریمیوم (4 Premium Palettes):**
  * ☕ **Classic Dark Academia** (پیش‌فرض)[cite: 1]
  * 🌲 **Emerald Velvet**[cite: 1]
  * 🌊 **Teal Indigo**[cite: 1]
  * 🔮 **Neon Violet**[cite: 1]
  * پشتیبانی کامل از حالت تاریک/روشن (Light / Dark Mode Toggle)[cite: 1].
* **📊 مرکز آمار و ردیابی پیشرفت (Progress & Metrics):**
  * محاسبه درصد پیشرفت روزانه و مجموع ساعات مطالعه تکمیل‌شده[cite: 1].
  * شمارش معکوس زنده تا زمان برگزاری کنکور ریاضی[cite: 1].
* **📝 یادداشت‌های سریع (Loqme / Quick Notes):** سیستم ثبت To-Do و یادداشت‌های کوچک روزانه با قابلیت علامت‌گذاری و حذف[cite: 1].
* **🔗 دسترسی سریع سفارشی (Quick Access Manager):** قابلیت اضافه، ویرایش و حذف لینک‌های سریع به سامانه‌ها و پنل‌های درسی (مانند کلاس‌های ماز، گوگل نوتبوک و...)[cite: 1].
* **🖨️ حالت چاپ اختصاصی (Print Stylesheet):** بهینه‌سازی شده برای خروجی گرفتن یا چاپ A4 افقی (Landscape) بدون عناصر زائد UI[cite: 1].

---

## 🛠️ تکنولوژی‌های به‌کاررفته

| بخش | تکنولوژی / کتابخانه |
| :--- | :--- |
| **Structure** | HTML5 (Semantic Structure)[cite: 1] |
| **Styling** | Pure CSS3 (CSS Variables, Flexbox, CSS Grid)[cite: 1] |
| **Typography** | Samim Font (فونت صمیم - راستیکردار)[cite: 1] |
| **Scripting** | Vanilla JavaScript (ES6+, IIFE Architecture)[cite: 1] |
| **Storage** | Browser `localStorage` API[cite: 1] |

---

## ⚙️ ساختار داده‌های محلی (LocalStorage Schema)

برنامه تمام حالت‌های اجرا را تحت کلیدهای زیر در `localStorage` نگهداری می‌کند:

| کلید | توضیحات |
| :--- | :--- |
| `stellarium_schedule_v4_{day}` | آرایه پارت‌های مطالعه مربوط به روز انتخاب شده (`sat`, `sun`, ...)[cite: 1] |
| `stellarium_checks_v4_{day}` | وضعیت تیک خوردن هر پارت در روز مربوطه[cite: 1] |
| `stellarium_start_time_v4_{day}` | ساعت شروع برنامه برای روز مربوطه[cite: 1] |
| `stellarium_notes_v3` | فهرست یادداشت‌ها و لقمه‌های ثبت‌شده[cite: 1] |
| `stellarium_quick_links_v1` | فهرست دکمه‌های دسترسی سریع سفارشی‌سازی‌شده[cite: 1] |
| `stellarium_mode_v3` | حالت تم تصویری (`dark` / `light`)[cite: 1] |
| `stellarium_palette_v3` | نام پالت رنگی فعال (`classic`, `emerald`, `teal`, `violet`)[cite: 1] |

---

## 🚀 راهنمای اجرا

این پروژه نیازی به نصب Node.js، NPM یا کامپایل ساختار ندارد.

1. مخزن را کلون کنید یا فایل `Stellarium Planner V3.2.html` را دانلود کنید[cite: 1]:
   ```bash
   git clone [https://github.com/your-username/stellarium-planner.git](https://github.com/your-username/stellarium-planner.git)
