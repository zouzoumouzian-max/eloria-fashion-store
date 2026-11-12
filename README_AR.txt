ÉLORIA — ملفات تثبيت التطبيق (PWA)

ارفع الملفات التالية إلى نفس المجلد الذي يوجد فيه ملف HTML الرئيسي:
- manifest.json
- service-worker.js
- icon-192.png
- icon-512.png

مهم: هذه الملفات وحدها لا تكفي إذا لم تتم إضافة الربط داخل ملف HTML.

أضف داخل <head> في ملف HTML:
<link rel="manifest" href="./manifest.json">
<meta name="theme-color" content="#b94f78">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="default">
<link rel="apple-touch-icon" href="./icon-192.png">

وقبل </body> مباشرة أضف:
<script>
if ("serviceWorker" in navigator) {
  window.addEventListener("load", () => {
    navigator.serviceWorker.register("./service-worker.js")
      .catch((error) => console.error("ÉLORIA service worker:", error));
  });
}
</script>

لا تغيّر اسم ملف HTML الرئيسي إذا كان GitHub Pages يعتمد عليه كصفحة رئيسية؛ الأفضل أن يكون index.html.
إذا كان اسم الملف مختلفاً، أعد تسميته إلى index.html قبل الرفع.

بعد الرفع:
1. افتح رابط GitHub Pages في Chrome.
2. انتظر تحميل الموقع.
3. من قائمة Chrome اختر "إضافة إلى الشاشة الرئيسية" أو "Install app" إذا ظهرت.
4. إذا لم يظهر خيار التثبيت، تأكد أن الموقع يعمل عبر HTTPS وأن روابط الملفات صحيحة.

ملاحظة: Service Worker يوفر أساساً للتخزين المؤقت، لكن الصور الخارجية أو خدمات الإنترنت قد تحتاج اتصالاً.
