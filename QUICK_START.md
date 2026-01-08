# دليل البدء السريع - إعادة تعيين كلمة المرور

## خطوات سريعة للتشغيل

### 1. نشر الموقع
```bash
cd web_reset_password
npx vercel --prod
```

### 2. نسخ الرابط
بعد النشر، انسخ الرابط من Vercel (مثل: `https://uniskills-reset-abc123.vercel.app`)

### 3. تحديث التطبيق
في `lib/services/supabase_service.dart`:
```dart
redirectTo: 'https://YOUR-VERCEL-URL.vercel.app/reset-password'
```

### 4. تحديث Supabase
في لوحة تحكم Supabase:
- Authentication > URL Configuration
- أضف الرابط في Redirect URLs

### 5. اختبار
```bash
flutter pub get
flutter run
```

## اختبار سريع
1. اطلب إعادة تعيين كلمة المرور من التطبيق
2. افتح الإيميل
3. اضغط على الرابط
4. يجب أن يفتح التطبيق تلقائياً

## ملاحظات
- اختبر على جهاز حقيقي وليس simulator
- تأكد من تثبيت التطبيق أولاً
- الموقع يعمل على جميع المتصفحات