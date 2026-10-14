# সফল বাজারি Admin Panel — সেটআপ (বাংলা)

## ফাইল
- `/admin.html`: লগইন, পণ্য যোগ/এডিট, স্টক, পণ্য দেখানো/লুকানো, অর্ডার দেখা ও status পরিবর্তন।
- `/supabase-schema.sql`: ডেটাবেস টেবিল ও নিরাপত্তা policy।
- `/supabase-config.js`: Supabase project URL ও public anon/publishable key বসানোর জায়গা।

## চালু করার ধাপ
1. https://supabase.com/dashboard এ সাইন আপ করে একটি Free project তৈরি করুন।
2. Project → SQL Editor → New query খুলুন; `supabase-schema.sql`-এর সম্পূর্ণ SQL পেস্ট করে Run করুন।
3. Authentication → Users থেকে আপনার নিজের ইমেইল দিয়ে user তৈরি করুন (শক্তিশালী পাসওয়ার্ড ব্যবহার করুন)।
4. SQL Editor-এ চালান, ইমেইল বদলে দিন:
   `update public.profiles set is_admin = true where lower(email) = lower('YOUR_EMAIL_HERE');`
5. Project Settings → API থেকে Project URL ও anon/publishable key কপি করে `supabase-config.js`-এ `url` ও `anonKey`-তে বসান। **service_role/secret key কখনো কপি করবেন না।**
6. GitHub-এ commit করুন; Vercel auto-deploy যুক্ত না থাকলে Vercel dashboard-এ নতুন deployment তৈরি/সোর্স সংযোগ করুন।
7. `https://sofol-bazaari.vercel.app/admin.html` খুলে লগইন করুন।

## গুরুত্বপূর্ণ
- Supabase Free-তে usage limits আছে; দীর্ঘদিন নিষ্ক্রিয় থাকলে project pause হতে পারে।
- Vercel Hobby plan-এর বর্তমান fair-use শর্ত commercial ecommerce-কে অনুমোদন নাও করতে পারে; বাস্তব বিক্রির আগে Vercel-এর plan/terms যাচাই করুন। এই সেটআপটি আগে prototype/testing-এর জন্য ব্যবহার করুন।
- Admin password, service_role key, database password কখনো GitHub-এ দেবেন না।
