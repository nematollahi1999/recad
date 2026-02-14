# 📘 RECAD: Master Documentation

**Version:** 1.1
**Status:** Architecture Phase
**Stack:** Laravel 11 (Headless) + SvelteKit 2 (SPA) + Tailwind CSS
**Target Market:** K-12 Schools, Language Institutes, Educational Complexes

---

## 1. Executive Summary

RECAD is a high-performance, multi-tenant School Management System (SMS). It utilizes a unique "Workspace" architecture allowing users to manage or join multiple educational entities from a single account. The platform features an RTL-first design (Persian/Arabic support) and a freemium business model with shared administrative access.

---

## 2. Technical Architecture & Security

### Backend (Laravel 11 API-Only)

- **Multi-tenancy:** Workspace-based scoping using Global Scopes and `workspace_id`.
- **Authentication:** Laravel Sanctum with custom OTP (One-Time Password) logic.
- **Session Security:**
  - **Single-Session Enforcement:** Database stores `current_session_id` and `last_login_ip`.
  - **Conflict Logic:** New logins invalidate previous tokens to prevent account sharing.
- **Media Handling:** Spatie Media Library for avatars and documents.

### Frontend (SvelteKit 2.0 SPA)

- **State Management:** **Store-in-Context** pattern. Context is used to provide SSR-safe, reactive stores for Auth, Workspace details, and Permissions.
- **Styling:** Tailwind CSS with logic-based RTL support (Logical Properties).
- **UI System:** "Glassmorphism Lite" (Subtle blurs, soft shadows, Indigo-600 primary).

---

## 3. Administrator Dashboard Specification

### 3.1 Shared Access & Sub-Users

- **Owner Role:** Full billing and workspace control.
- **Sub-User Invite:** Admin invites via Mobile/Email. If the user exists, the workspace is added to their switcher; if not, an account is created via OTP.
- **RBAC:** Permissions are fetched on login and stored in the Svelte Context for real-time UI gating.

### 3.2 Freemium Logic

- **Free Tier:** Limited students (e.g., 50), 1 Admin seat, basic reporting.
- **Pro Tier:** Unlimited students, multiple staff seats, advanced analytics, custom branding.
- **UI Gating:** "Locked" features are visible but grayed out with upgrade triggers.

---

## 4. Core Functional Modules

### M1: Auth & Onboarding

- **Flow:** Mobile/Email OTP → Profile Setup → Workspace Creation.
- **Default Dev OTP:** `1234`.

### M2: The Command Center (Dashboard)

- **Triple-Column View:** (1) Notifications, (2) Timeline Engine, (3) Live Attendance.
- **Timeline Engine:** Vertical calendar showing the "heartbeat" of the school in real-time.

### M3: Academic Management

- **Grading Systems:** Support for Iranian 6-3-3 (Descriptive for Primary, 0-20 for Secondary) and International Letter grades.
- **Scheduling:** Smart conflict detection for teachers and rooms.

### M4: Finance & Tuition

- **Student Ledgers:** Installment tracking and automated debt reminders.
- **Payroll:** Tracking staff hours and basic salary generation.

---

## 5. Implementation Roadmap

### Phase 1: Foundation (Backend)

- [ ] Database Schema: Workspaces, Users, Roles, Pivot tables.
- [ ] OTP Auth Service: Request/Verify logic.
- [ ] Session Locking Middleware: IP and Session ID verification.
- [ ] Multi-tenant Scoping: Logic to isolate data per Workspace.

### Phase 2: Core Shell (Frontend)

- [ ] Svelte Context Setup: `authContext` and `workspaceContext`.
- [ ] Dual-Sidebar Layout: Primary (Slim) + Secondary (Wide).
- [ ] RTL/LTR Toggle: Logic for Tailwind logical properties.
- [ ] Workspace Switcher: Component for multi-workspace navigation.

### Phase 3: Administrative Features

- [ ] Sub-user Invitation System: Token generation and invite emails/SMS.
- [ ] Permission Matrix: UI for assigning roles to staff.
- [ ] Freemium Guards: `FeatureGuard.svelte` component for gating Pro features.

### Phase 4: Academic Workflows

- [ ] Student/Teacher CRUD.
- [ ] Course & Grade Mapping.
- [ ] Timeline Engine: Real-time daily class tracker.

### Phase 5: Financials & Reports

- [ ] Student Ledger implementation.
- [ ] PDF Report Card generation.
- [ ] "SIDA" Export: Excel export compatible with Iranian Ministry of Education systems.

---

## 6. Iranian Education System Context

- **Primary:** 6 Years (Descriptive Grading: Very Good, Good, etc.).
- **Secondary:** 3+3 Years (Numeric Grading: 0-20).
- **Institutes:** Term-based (Starter, Elementary, etc.) with level-up logic.

---

## 7. Project README (For GitHub)

```markdown
# 📘 RECAD: Next-Gen School Management System

**RECAD** is a high-performance, multi-tenant SMS designed for the modern educational landscape.

### 🛠️ Tech Stack

- **Backend:** Laravel 11 (Headless API).
- **Frontend:** SvelteKit 2.0 (SPA Mode) + Tailwind CSS.
- **Security:** OTP Auth + Single-Session IP Locking.

### ✨ Key Features

- **Multi-Tenant:** Manage multiple schools from one account.
- **Shared Access:** Invite staff with granular permissions.
- **RTL-First:** Designed natively for Persian/Arabic environments.
- **Freemium:** Built-in feature gating and subscription tiers.

### 🚀 Getting Started

1. **Backend:** `composer install`, `php artisan migrate`, `php artisan serve`.
2. **Frontend:** `pnpm install`, `pnpm dev`.
3. **Login:** Use any mobile number with OTP `1234` (Dev Mode).
```
