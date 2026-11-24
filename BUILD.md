# بناء ملف APK

## قبل البدء (مهم)
افتح www/index.html وابحث عن السطر الذي يبدأ بـ `const PUB=` واستبدله بالسطر الذي يعطيك إياه admin.html (المفتاح العام). بدون هذا لن تعمل أكواد التفعيل.

## الطريقة 1: بدون برامج (GitHub، مجاني)
1. أنشئ حساباً في github.com ثم مستودعاً جديداً (Private).
2. ارفع كل محتويات هذا المجلد إلى المستودع (Add file ← Upload files). تأكد من رفع مجلد .github أيضاً.
3. افتح تبويب Actions ← Build APK ← Run workflow.
4. بعد 4 إلى 8 دقائق افتح التشغيل الناجح ونزّل aluminum-calc-apk من قسم Artifacts. بداخله app-debug.apk.
5. أرسله للعملاء. على الجوال يسمح المستخدم بـ «التثبيت من مصدر غير معروف» ثم يثبّت.

## الطريقة 2: على جهازك (يلزم Node 20 وJDK 17 وAndroid Studio)
npm install
npx cap add android
npx cap sync android
cd android && ./gradlew assembleDebug
الملف: android/app/build/outputs/apk/debug/app-debug.apk

## النشر على Google Play
ملف debug للتجربة والتوزيع المباشر فقط. للنشر على المتجر تحتاج AAB موقّع: افتح مجلد android في Android Studio ← Build ← Generate Signed Bundle.

## أيقونة التطبيق
بعد npx cap add android ضع أيقونة 1024x1024 في assets/icon.png ثم: npm i -D @capacitor/assets && npx capacitor-assets generate --android
