نحوه‌ی استفاده (مرورگر)

```html
<script src="cupline.js"></script>
<script>
  const engine = new CUPLINE.Engine(canvas, true);
  const scene  = new CUPLINE.Scene(engine);
  // ... دقیقاً مثل Babylon، فقط با CUPLINE
</script>
```

برای تست سریع، فایل `test_cupline.html` را کنار `cupline.js` بگذار و در مرورگر باز کن (بهتر است با یک سرور محلی مثل `npx serve .` باز شود).

## تست‌هایی که انجام شد ✅

- `node --check cupline.js` — سینتکس کل فایل سالم است.
- اجرای واقعی بخش‌های Core تا GUI در محیط شبیه مرورگر: `CUPLINE` ساخته شد (۳٬۳۸۴ خروجی)، `BABYLON` تعریف‌نشده ماند و کلاس‌های `Engine, Scene, Vector3, WaterMaterial, GLTFFileLoader, GUI.AdvancedDynamicTexture, ...` همگی درست کار کردند.
- بخش‌های Inspector و Viewer برای اجرا به DOM واقعی مرورگر نیاز دارند؛ آن‌ها را با `test_cupline.html` در مرورگر تست کن.

## هشدارهای سازگاری ⚠️

1. این باندل برای استفاده با تگ `<script>` در مرورگر ساخته شده. در Node (`require`) به‌خاطر پشت‌سرهم بودن چند ماژول UMD و تغییر نام وابستگی‌ها (`cuplinejs`) ممکن است کار نکند.
2. فایل‌های صحنه‌ی قدیمی با پسوند `.babylon` حالا `.cupline` انتظار می‌رود.
3. بعضی قابلیت‌های lazy-load (مثل ادیتورهای Inspector/GUI Editor یا پروفایل‌های کنترلر WebXR) ممکن است بخواهند فایل‌هایی با نام `cupline.*` را از CDN پیش‌فرض لود کنند که آنجا وجود ندارند؛ اگر از آن‌ها استفاده می‌کنی باید فایل‌های تغییرنام‌یافته را روی هاست خودت بگذاری و آدرس CDN را تنظیم کنی.
