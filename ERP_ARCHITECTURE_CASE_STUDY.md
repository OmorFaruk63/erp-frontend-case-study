# Enterprise ERP Frontend Architecture (Case Study)

**Engineer:** Omor Faruk | Frontend Engineer  
**Status:** Confidential Internal Suite (NDA Protected)  
**Core Stack:** React 19, TypeScript 5.9, Vite 7, TanStack Router & Query, Zustand, MUI X-DataGrid, Zod  

---

## ⚡ 30-Second Executive Summary
Architected a modular, reactive enterprise frontend supporting Human Resource Management (HRM), Biometric Attendance, and Payroll Automation. Built for high-density data management with sub-second table rendering (<1.2s view loads) and granular 4-tier Role-Based Access Control (RBAC).

---

## 📊 Measurable Impact

| Metric | Achievement | Engineering Mechanism |
| :--- | :--- | :--- |
| **Initial View Load** | **< 1.2s** | Route-level code splitting via TanStack Router & Vite 7 |
| **Table Scroll FPS** | **60 FPS** | DOM virtualization on 5,000+ records via MUI X-DataGrid |
| **Form Error Rate** | **30% reduction** | Multi-step state decoupling with React Hook Form + Zod |
| **Report Export Time** | **< 800ms** | Client-side ExcelJS & jsPDF (0 backend server queue load) |
| **Route Access Leaks**| **0%** | TanStack Router `beforeLoad` auth guards & `<PermissionGate>` |

---

## 🏗️ Architectural Diagram

```
[ TanStack Router (Type-Safe RBAC Guards) ]
              │
  ┌───────────┼───────────┐
  ▼           ▼           ▼
[ HRM ]    [ UMS ]   [ Payroll ]
  └───────────┬───────────┘
              │
  ┌───────────┴───────────┐
  ▼                       ▼
[ TanStack Query v5 ]   [ Zustand v5 ]
(Server Data & Cache)   (Client UI State)
              │
              ▼
    [ Axios Interceptors ]
   (JWT Bearer, Auto-Refresh)
```

---

## 🛠️ 3 Core Engineering Challenges Solved

### 1. DOM Bloat in Massive Data Tables
- **Problem:** Scrolling 3,000+ attendance records caused 180ms frame drops.
- **Solution:** Integrated `@mui/x-data-grid` DOM virtualization, memoized cell renderers (`React.memo`), and debounced search filters by 400ms.

### 2. Multi-Step Onboarding Form Validation
- **Problem:** Heavy form drop-offs across personal, bank, and departmental transfer steps.
- **Solution:** Orchestrated forms using `react-hook-form` and schema-driven `zod` validation, preserving draft state across stepper navigation.

### 3. Server-Free Report Generation
- **Problem:** Heavy server queues when 1,000+ employees generated monthly pay-slips.
- **Solution:** Offloaded document rendering to client-side Web APIs using `exceljs` and `jspdf-autotable`.

---

*Notice: Proprietary endpoints, company identifiers, and sensitive employee PII have been anonymized in compliance with NDA agreements.*
