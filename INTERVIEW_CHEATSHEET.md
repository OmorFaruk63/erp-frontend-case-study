# Technical Interview Cheatsheet: ERP Frontend Project

Use this cheatsheet to confidently answer frontend interview questions regarding your `erp-fe` project.

---

## 1. The Opening Pitch (STAR Method)

**Question:** *"Can you tell me about this ERP project listed on your resume?"*

> **Answer:**  
> "Certainly! The ERP project is an enterprise-grade internal platform designed to streamline Human Resource Management (HRM), Attendance, Payroll, and User Access Control for corporate operations.
> 
> When I worked on the frontend, the core challenge was handling large amounts of data—like thousands of employee attendance records and complex multi-step onboarding processes—without lagging the browser. 
> 
> I built the frontend with **React 19, TypeScript, and Vite**, utilizing **TanStack Router** for type-safe navigation and **MUI X-DataGrid** with virtualization so users could filter and scroll through thousands of rows at a smooth 60 FPS. For data synchronization, I implemented **TanStack Query v5** to handle caching and background updates, while lightweight **Zustand** stores managed local UI states. 
> 
> I also integrated client-side report exports using **ExcelJS** and **jsPDF**, allowing users to generate formatted payroll slips instantly. The project is internal and NDA-protected, but the architecture successfully cut table render times to under 1.2 seconds and reduced form submission errors by over 30%."

---

## 2. Technical Deep-Dives

### Q1: *"Why did you use Vite + TanStack Router instead of Next.js?"*
- **Answer:**  
  "Because this is a private, authenticated enterprise application behind login screens, Search Engine Optimization (SEO) and public Server-Side Rendering (SSR) were not required. Vite gives us ultra-fast Hot Module Replacement (HMR) and instantaneous build times. Furthermore, TanStack Router provides 100% type-safe search parameters, route params, and loader functions, making it arguably superior for complex dashboard SPAs with heavy client-side state."

### Q2: *"How did you implement Role-Based Access Control (RBAC) in the frontend?"*
- **Answer:**  
  "We tackled it at two levels:
  1. **Route Level:** Inside TanStack Router's `beforeLoad` hook, we verify the user's role and permission tokens stored in memory/session. If unauthorized, they are immediately redirected to a 403 Forbidden or Dashboard view before route bundles are mounted.
  2. **Component Level:** We implemented a declarative `<PermissionGate required={['HR_ADMIN', 'PAYROLL_APPROVER']}>` wrapper. Action buttons (like 'Disburse Salary' or 'Delete Employee') only render if the authenticated user's scope matches, preventing unauthorized UI actions."

### Q3: *"How did you handle large data tables without performance degradation?"*
- **Answer:**  
  "We combined three techniques:
  1. **DOM Virtualization:** Using `@mui/x-data-grid`, only the visible rows and columns currently in viewport are rendered in the DOM.
  2. **Debounced Server-Side Querying:** As users type filters or search terms, requests are debounced by 400ms to avoid spamming the API.
  3. **Memoized Renderers:** Cell renderers (like status badges, avatar chips, and action popovers) are wrapped in `React.memo` to eliminate unnecessary re-renders when parent table state changes."

### Q4: *"How did you structure the project to maintain scalability?"*
- **Answer:**  
  "We followed a modular, feature-based architecture under `/src/modules/` (e.g., `hrm`, `ums`, `auth`, `profile`). Each module has its own `views`, `sections`, `schemas` (Zod), and `api` hooks. To ensure developers didn't cross-import internal utilities improperly, we added an atomic compliance verification script and ESLint boundary rules that run on pre-commit hooks via Husky."

### Q5: *"Why did you use both TanStack Query and Zustand?"*
- **Answer:**  
  "To maintain a clear boundary between **Server State** and **Client UI State**.
  - **TanStack Query** handles all asynchronous server state: API fetching, caching, deduplication, retry logic, and pagination query keys.
  - **Zustand** is reserved strictly for ephemeral UI state that does not belong on a server: sidebar toggle states, active modal drawers, and transient table filter presets."

---

## 3. What to do if asked for a live link during an interview:
- *"Since this is an enterprise internal application bound by NDA, the live company portal is restricted to internal corporate networks. However, I have documented the comprehensive architecture and key modules in my case study, and I can walk you through the codebase structure, state management, and component patterns right now."*
