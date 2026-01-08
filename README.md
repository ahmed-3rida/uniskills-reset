# UniSkills Password Reset Web Interface

هذا الموقع يستقبل روابط إعادة تعيين كلمة المرور من Supabase ويحولها إلى deep links لفتح التطبيق مباشرة.

## كيفية العمل

1. المستخدم يطلب إعادة تعيين كلمة المرور من التطبيق
2. Supabase يرسل إيميل يحتوي على رابط يشير إلى هذا الموقع
3. الموقع يستقبل الـ tokens ويحولها إلى deep link
4. التطبيق يفتح تلقائياً مع شاشة إعادة تعيين كلمة المرور

## الرفع على Vercel

```bash
cd web_reset_password
vercel --prod
```

## إعداد Supabase

في إعدادات Supabase، يجب تعيين:
- Site URL: `https://your-domain.vercel.app`
- Redirect URLs: `https://your-domain.vercel.app/reset-password`

## Deep Link Schema

التطبيق يستخدم الـ schema التالي:
```
uniskills://reset-password?access_token=TOKEN&refresh_token=TOKEN&type=recovery
```