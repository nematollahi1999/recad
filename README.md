📘 RECAD: Next-Gen School Management System
![alt text](https://img.shields.io/badge/Backend-Laravel_11-FF2D20?style=for-the-badge&logo=laravel)

![alt text](https://img.shields.io/badge/Frontend-SvelteKit_2.0-FF3E00?style=for-the-badge&logo=svelte)

![alt text](https://img.shields.io/badge/Styling-Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css)

![alt text](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)
RECAD is a high-performance, multi-tenant SMS designed for the modern educational landscape. Built for K-12 schools and language institutes, it simplifies complex administrative workflows through a sleek, RTL-first interface and a real-time command center.
✨ Key Features
🏢 Multi-Tenant Workspace Architecture
Manage or join multiple educational entities from a single account. Switch between a Language Institute and a K-12 School without re-logging.
🛡️ Secure Admin Dashboard
OTP-First Auth: Secure login via Mobile/Email OTP (Default: 1234 for Dev).
Shared Access: Owners can invite sub-users (Staff, Accountants) with granular permissions.
Single-Session Enforcement: Professional IP-locking to prevent account sharing.
Freemium Logic: Built-in feature gating (Free vs. Pro tiers) with contextual upsells.
🕒 The Command Center (M2)
Timeline Engine: A Google Calendar-style vertical strip showing live, upcoming, and held classes.
Real-Time Monitoring: Instant visibility into attendance counts and teacher status.
🌍 Localization & UX
RTL-First Design: Native support for Persian/Arabic using Tailwind logical properties.
Glassmorphism Lite: A modern UI with subtle blurs, soft shadows, and high white-space for reduced cognitive load.
Dual-Sidebar Navigation: Slim global switcher paired with wide module-specific navigation.
🛠️ Technical Stack
Backend (The Engine)
Framework: Laravel 11 (Headless API-mode).
Auth: Laravel Sanctum (Stateful & Token-based).
Media: Spatie Media Library (for educational resources and profile management).
Permissions: Custom RBAC with Spatie Permission logic.
Security: Single-session fingerprinting (IP + User Agent).
Frontend (The Experience)
Framework: SvelteKit 2.0 (SPA Mode).
State Management: Context-based Stores (SSR-safe, unique to each user session).
Styling: Tailwind CSS with logic-based RTL support.
Icons: Lucide Svelte.
🚀 Getting Started
Prerequisites
PHP 8.2+ & Composer
Node.js 20+ & PNPM/NPM
MySQL 8.0+
Backend Setup
code
Bash
cd backend
composer install
cp .env.example .env
php artisan key:generate
php artisan migrate --seed
php artisan serve
Frontend Setup
code
Bash
cd frontend
pnpm install
pnpm dev
📂 Architecture Overview
code
Text
├── backend (Laravel 11)
│ ├── app/Http/Middleware/ # Workspace & Session Locking logic
│ ├── app/Models/ # Multi-tenant scoped models
│ └── routes/api.php # Scoped API endpoints
│
└── frontend (SvelteKit 2.0)
├── src/lib/context/ # Permission & Workspace Contexts
├── src/lib/components/ # Glassmorphic UI components
└── src/routes/(admin)/ # Protected Administrator routes
🛡️ Security & Permissions
RECAD uses a Store-in-Context pattern for SvelteKit. Permissions are fetched once during the layout load and injected into the component tree, ensuring that:
Users only see what they are authorized to use.
Server-Side Rendering (SSR) remains safe from data leakage.
Feature gating (Free/Pro) is handled reactively.
🗺️ Roadmap

Phase 1: Foundation (Auth, OTP, Multi-tenancy).

Phase 2: The Core Shell (Dual-sidebar, RTL logic).

Phase 3: Academic Workflows (Grades, Classes, Timeline).

Phase 4: Financials & Reports (Tuition, PDF generation).

Phase 5: Mobile App (API-ready for React Native/Flutter).
📄 License
This project is licensed under the MIT License - see the LICENSE file for details.
📞 Contact & Support
Built with ❤️ for the educational community.
Founder: [Your Name/Handle]
Market: K-12 Schools, Language Institutes, Educational Complexes.
RECAD - Efficiency in Education.
