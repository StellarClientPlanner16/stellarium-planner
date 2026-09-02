# 🏛️ Stellarium Planner V3.2

> **The Daily Study Gazette & High-Density Execution Engine**  
> یک سیستم ایزوله، مینیمال و بدون وابستگی (Zero-Dependency Single-File Web App) برای مدیریت زمان، ردیابی جلسات مطالعه، تایمر فوکوس و آنالیز پیشرفت داوطلبان کنکور سراسری با طراحی نئوکلاسیک و آکادمیک.

---

## 📐 فلسفه طراحی و معماری (Architectural Overview)

Stellarium Planner با هدف حذف اصطکاک اجرای برنامه‌های سنگین مطالعاتی توسعه یافته است. این ابزار هیچ فریم‌ورک سنگین، موتور رندر خارجی یا درخواست شبکه (Network Overhead) اضافه ندارد. تمام محاسبات زمان‌بندی، ذخیره‌سازی وضعیت‌ها و مدیریت تایمر به صورت کاملاً ایزوله در مرورگر کاربر پردازش می‌شود.

┌────────────────────────────────────────────────────────────────────────┐
│                        Stellarium Execution Engine                     │
├──────────────────────────────────┬─────────────────────────────────────┤
│  Core Modules                    │  UI & Aesthetics                    │
│  ├── Dynamic Timeline Calculator │  ├── CSS Variable Palette Engine    │
│  ├── Multi-Day State Isolation   │  ├── Responsive Layout & Grid       │
│  ├── Session & Focus Timer Loop  │  └── Print Engine Optimization      │
│  └── LocalStorage Persistence    │                                     │
└──────────────────────────────────┴─────────────────────────────────────┘


---

## 🔥 ویژگی‌های کلیدی سیستم

### ۱. سیستم ایزوله برنامه‌ریزی هفته (Multi-Day Tab Engine)
* **تفکیک کامل وضعیت:** مدیریت مستقل داده‌ها، پارت‌های درسی و وضعیت چک‌باکس‌ها برای تمامی ۷ روز هفته (Sat تا Fri).
* **بارگذاری در لحظه:** سوئیچ میان روزها بدون بازخوانی صفحه و ذخیره‌سازی خودکار تغییرات در کلیدهای مجزای LocalStorage.

### ۲. تایمر جلسه فعال و مدال تمرکز (Active Session & Focus Overlay)
* **تایمر اختصاصی پارت‌ها:** امکان سنجش دقیق زمان هر پارت مطالعاتی با قابلیت توقف، ادامه و بازنشانی.
* **Focus Overlay:** صفحه سفارشی برای حذف حواس‌پرتی‌های بصری، نمایش تایمر با سایز بزرگ و ویژوالایزر پیشرفت.
* **ثبت خودکار:** علامت‌گذاری تیک اتمام پارت بلافاصله پس از به پایان رسیدن تایمر معکوس.

### ۳. موتور محاسباتی زمان پویا (Dynamic Time Engine)
* **ارزیابی خودکار زنجیره زمان:** با تغییر ساعت شروع روز (Start Time)، تمام بازه‌های زمانی پارت‌های درسی به صورت خودکار محاسبه و بروزرسانی می‌شوند.
* **دکمه‌های Preset:** دسترسی سریع به ساعات متداول شروع روز (۰۵:۰۰ تا ۰۷:۰۰).

### ۴. پالت‌های رنگی پریمیوم (Quad-Theme Engine)
سیستم شامل ۴ پالت رنگی با هماهنگی کامل در دو حالت Dark و Light است:
* ☕ **Classic Dark Academia:** تم اصلی بر پایه رنگ‌های کاغذی، مرکبی و آکادمیک.
* 🌲 **Emerald Velvet:** رنگ‌بندی بر پایه سبز زمردی و طلایی.
* 🌊 **Teal Indigo:** ترکیب آبی سورمه‌ای و اسکای بلو.
* 🔮 **Neon Violet:** پالت بنفش نئونی و آکادمیک مدرن.

### ۵. ردیاب پیشرفت و آمار زنده (Analytics & Metrics)
* **محاسبه هوشمند بازده:** محاسبه درصد پیشرفت روزانه و مجموع دقیق ساعات مطالعه تکمیل‌شده.
* **شمارش معکوس زنده:** شمارش معکوس تا زمان برگزاری کنکور سراسری ریاضی.

### ۶. مدیریت لینک‌های دسترسی سریع (Quick Access Manager)
* **سفارشی‌سازی کامل:** امکان اضافه، ویرایش و حذف لینک‌های کاربردی (پنل‌های کلاس آنلاین، منابع، ابزارهای یادگیری) به همراه ذخیره‌سازی محلی.

---

## 🛠️ مشخصات فنی (Technical Stack)

| کامپوننت | تکنولوژی / مشخصه فنی |
| :--- | :--- |
| **Architecture** | Single-File (HTML5 + CSS3 + Vanilla JS) |
| **Styling Core** | CSS Custom Properties, Flexbox, CSS Grid |
| **Scripting Pattern** | IIFE (Immediately Invoked Function Expression) / Encapsulated State |
| **Typography** | Samim Persian Font (via CDN) |
| **Persistence** | Browser LocalStorage API |
| **Print Optimization** | Dynamic @media print Stylesheet (A4 Landscape) |

---

## 💾 ساختار پایگاه داده محلی (LocalStorage Schema)

برنامه تمام داده‌های کاربر را تحت کلیدهای زیر در حافظه مرورگر سازماندهی می‌کند:

```json
{
  "stellarium_schedule_v4_{day}": [
    { "id": 1, "duration": 100, "title": "پارت مطالعه", "details": "توضیحات", "checkbox": true }
  ],
  "stellarium_checks_v4_{day}": { "1": true },
  "stellarium_start_time_v4_{day}": "05:00",
  "stellarium_notes_v3": [ { "text": "یادداشت سریع", "done": false } ],
  "stellarium_quick_links_v1": [ { "label": "عنوان", "url": "https://..." } ],
  "stellarium_mode_v3": "dark",
  "stellarium_palette_v3": "classic"
}
⚡ راهنمای سریع اجرا
۱. مخزن را کلون کنید:

Bash
git clone [https://github.com/your-username/stellarium-planner.git](https://github.com/your-username/stellarium-planner.git)
۲. فایل Stellarium Planner V3.2.html را مستقیماً درون هر مرورگر وب مدرن باز کنید. نیازی به Server، Node.js یا Build Step نیست.

📄 Licensure
توسعه‌یافته تحت مجوز MIT License. استفاده، تغییر و انتشار مجدد آن آزاد است.
