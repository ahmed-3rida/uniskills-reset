# دليل نشر موقع إعادة تعيين كلمة المرور

## الخطوات المطلوبة

### 1. رفع الموقع على Vercel

```bash
cd web_reset_password
npx vercel --prod
```

أو يمكنك ربط المجلد بـ GitHub ونشره تلقائياً من Vercel Dashboard.

**ملاحظة**: الملفات موجودة في مجلد `public/` وVercel سيتعرف عليها تلقائياً.

### 2. تحديث إعدادات Supabase

في لوحة تحكم Supabase:

1. اذهب إلى **Authentication** > **URL Configuration**
2. أضف الرابط الجديد في **Redirect URLs**:
   ```
   https://your-domain.vercel.app/reset-password
   https://your-domain.vercel.app/
   ```

### 3. تحديث رابط الموقع في التطبيق

في ملف `lib/services/supabase_service.dart`، حديث الرابط:

```dart
redirectTo: 'https://your-actual-domain.vercel.app/reset-password'
```

### 4. إعداد Deep Linking في التطبيق

تأكد من تشغيل الأمر التالي لتحديث الـ dependencies:

```bash
flutter pub get
```

### 5. اختبار النظام

1. شغل التطبيق على الجهاز
2. اطلب إعادة تعيين كلمة المرور
3. افتح الإيميل واضغط على الرابط
4. يجب أن يفتح الموقع ثم يحول للتطبيق تلقائياً

## هيكل المشروع

```
web_reset_password/
├── public/
│   ├── index.html      # الصفحة الرئيسية
│   └── favicon.ico     # الأيقونة
├── vercel.json         # إعدادات Vercel
├── package.json        # معلومات المشروع
└── README.md          # دليل الاستخدام
```

## ملاحظات مهمة

- تأكد من أن التطبيق مثبت على الجهاز قبل الاختبار
- الـ deep link schema هو: `uniskills://reset-password`
- يمكن تخصيص اسم الـ schema في ملفات Android و iOS
- الموقع يعمل على جميع المتصفحات ويدعم الاتجاه من اليمين لليسار

## استكشاف الأخطاء

### إذا لم يفتح التطبيق:
1. تأكد من تثبيت التطبيق
2. تحقق من إعدادات الـ deep linking في Android/iOS
3. راجع logs التطبيق للأخطاء

### إذا لم يصل الإيميل:
1. تحقق من إعدادات SMTP في Supabase
2. تأكد من صحة الـ redirect URL
3. راجع spam folder

### إذا ظهرت أخطاء في الموقع:
1. تحقق من console المتصفح
2. تأكد من صحة الـ URL parameters
3. راجع Vercel logs j