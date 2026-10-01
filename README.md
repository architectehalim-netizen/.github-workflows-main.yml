# TEKYACHANTIER - تحويل الصفحة إلى APK

## قبل كل شيء
افتح `www/index.html` وضع رابط السكربت (المنتهي بـ /exec) في هذا السطر:

    var API_URL = 'https://script.google.com/macros/s/XXXXXXXX/exec';

بدون هذا الرابط لن يعمل الدخول داخل التطبيق.

## الطريقة 1: بناء APK بدون تثبيت أي شيء (GitHub Actions)
1. أنشئ حساباً مجانياً على github.com ثم مستودعاً جديداً (New repository).
2. ارفع كل محتويات هذا المجلد إلى المستودع (Add file > Upload files)،
   مع مجلد `.github` (إذا كان مخفياً في ويندوز فعّل "إظهار الملفات المخفية").
3. افتح تبويب **Actions** > **Build APK** > **Run workflow**.
4. بعد نحو 5 دقائق افتح التشغيل المكتمل ونزّل **TEKYACHANTIER-apk** من قسم Artifacts.
   داخله ملف `app-debug.apk`.
5. انقله إلى الهاتف وثبّته (اسمح بالتثبيت من مصدر غير معروف).

## الطريقة 2: البناء على جهازك
المتطلبات: Node.js 20 و JDK 17 و Android Studio (أو Android SDK).

    npm install
    npx cap add android
    npx cap sync android
    cd android
    ./gradlew assembleDebug        (على ويندوز: gradlew.bat assembleDebug)

الملف الناتج: `android/app/build/outputs/apk/debug/app-debug.apk`

## الطريقة 3: مواقع التحويل الجاهزة
يمكنك أيضاً ضغط محتوى مجلد `www` (بحيث يكون index.html في الجذر) ورفعه إلى موقع
تحويل HTML إلى APK مثل WebIntoApp أو Median.

## بعد كل تعديل على الصفحة
عدّل `www/index.html` ثم أعد البناء. لا حاجة لتغيير أي ملف آخر.

## ملاحظة
هذا APK للتجربة والتوزيع الداخلي (موقّع بمفتاح التطوير). للنشر على Google Play
يلزم بناء نسخة release وتوقيعها بمفتاحك الخاص.
