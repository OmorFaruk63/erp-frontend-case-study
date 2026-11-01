# 🚀 Vercel Deployment & Quick Guide

আপনার কেস স্টাডি পেজটি সম্পূর্ণ প্রস্তুত। এটি Vercel-এ ডেপ্লয় করার নিয়ম এবং প্রজেক্টের সংক্ষিপ্ত বিবরণ নিচে দেওয়া হলো:

---

## ⚡ Vercel-এ ১ মিনিটে ডেপ্লয় করার নিয়ম

### পদ্ধতি ১: Vercel ড্যাশবোর্ড থেকে (সবচেয়ে সহজ - Drag & Drop বা GitHub)
1. আপনার GitHub-এ একটি নতুন পাবলিক/প্রাইভেট রিপোজিটরি তৈরি করুন (যেমন: `erp-architecture-showcase`)।
2. শুধু এই **`Case Study` ফোল্ডারের ফাইলগুলো** সেই রিপোজিটরিতে পুশ করুন।
3. [vercel.com](https://vercel.com)-এ লগইন করে **"Add New Project"** ক্লিক করে রিপোজিটরিটি সিলেক্ট করে **Deploy** চাপুন!
4. ব্যস! ২ সেকেন্ডেই আপনার কেস স্টাডির একটি ফ্রি লাইভ ডোমেন পেয়ে যাবেন (যেমন: `https://omor-erp-case-study.vercel.app`)।

### পদ্ধতি ২: Vercel CLI দিয়ে (যদি টার্মিনাল ভালোবাসেন)
টার্মিনালে এই কমান্ডটি চালান:
```bash
cd "/Users/omor-faruk/Documents/Office Project /new/Case Study"
npx vercel
```
সরাসরি লাইভ লিঙ্ক তৈরি হয়ে যাবে।

---

## 📸 স্ক্রিনশট কোথায় যোগ করবেন?
আপনার `erp-fe` প্রজেক্ট রান করে এই ৪টি নামের স্ক্রিনশট তুলে `screenshots/` ফোল্ডারে রাখুন:
1. `01-dashboard.png` (রুট: `/dashboard/admin-dashboard`)
2. `02-datagrid.png` (রুট: `/dashboard/employee-management`)
3. `03-form.png` (রুট: `/dashboard/add-new-employee`)
4. `04-payroll.png` (রুট: `/dashboard/payroll-management`)

---

## 📄 রেজুমেতে কোন লাইনটি বসাবেন?
```markdown
1. Enterprise Resource Planning (ERP) Suite | React 19, TypeScript, Vite, TanStack Router/Query, MUI
   🔒 Internal Enterprise App (NDA Protected) | 📄 [Architecture Case Study](https://YOUR-VERCEL-URL.vercel.app)
   • Architected modular ERP frontend (HRM, Payroll) with <1.2s load times and 60 FPS table virtualization over 5,000+ records.
   • Streamlined multi-step onboarding workflows using React Hook Form & Zod, cutting form submission errors by 30%.
   • Built client-side ExcelJS & jsPDF export engines, generating branded payslips instantly with zero server overhead.
```
