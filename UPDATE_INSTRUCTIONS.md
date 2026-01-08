# تعليمات التحديث - إصلاح مشكلة الـ code parameter

## المشكلة التي تم حلها

كان الموقع يبحث عن `access_token` فقط، لكن Supabase يرسل `code` parameter في روابط إعادة تعيين كلمة المرور.

## التحديثات المطلوبة

### 1. رفع التحديثات على Vercel

```bash
cd web_reset_password
vercel --prod
```

### 2. تحديث التطبيق

```bash
flutter pub get
flutter run
```

## ما تم تحديثه

### في الموقع (`public/index.html`):
- ✅ إضافة دعم للـ `code` parameter
- ✅ تحديث التحقق من صحة الرابط
- ✅ تحديث إنشاء deep link للتطبيق
- ✅ تحديث التحميل التلقائي للتطبيق

### في التطبيق:
- ✅ تحديث `DeepLinkService` للتعامل مع `code`
- ✅ إضافة `exchangeCodeForSession` في `SupabaseService`
- ✅ تحسين معالجة الأخطاء

## اختبار التحديث

1. ارفع التحديثات على Vercel
2. شغل التطبيق المحديث
3. اطلب إعادة تعيين كلمة المرور
4. افتح الرابط من الإيميل
5. يجب أن يعمل الآن بدون مشاكل!

## الرابط الجديد سيعمل مع:

- `https://uniskills-reset.vercel.app/reset-password?code=d56e1549-8c22-4493-bcc7-351a058a901c`
- `https://uniskills-reset.vercel.app/reset-password?access_token=TOKEN&refresh_token=TOKEN`

## Deep Link الجديد:

- `uniskills://reset-password?code=CODE&type=recovery`
- `uniskills://reset-password?access_token=TOKEN&refresh_token=TOKEN&type=recovery`

---

🎉 **المشكلة محلولة!** الآن الموقع يدعم كلاً من `code` و `access_token` parameters.