# 🏢 MeridianSquare Investor Portal

> A modern, production-ready React application for regulated real asset tokenization and investor onboarding.

[![React](https://img.shields.io/badge/React-18.2-blue?logo=react)](https://react.dev)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.1-blue?logo=typescript)](https://www.typescriptlang.org)
[![Vite](https://img.shields.io/badge/Vite-4.4-purple?logo=vite)](https://vitejs.dev)
[![Bootstrap](https://img.shields.io/badge/Bootstrap-5.3-7952B3?logo=bootstrap)](https://getbootstrap.com)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)

---

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Quick Start](#quick-start)
- [Project Structure](#project-structure)
- [Architecture](#architecture)
- [Available Scripts](#available-scripts)
- [Configuration](#configuration)
- [Documentation](#documentation)
- [Contributing](#contributing)
- [License](#license)

---

## 🎯 Overview

MeridianSquare Investor Portal is a comprehensive React + TypeScript + Vite application designed for regulated real asset tokenization. The platform enables institutional investors to:

- **Onboard** securely with email verification and KYC
- **Discover** real estate investment opportunities across UAE and US
- **Filter** properties by location, price, yield, and type
- **Verify** identity status through a streamlined KYC process

**Target Markets:** UAE (primary), USA (secondary)

**Key Characteristics:**
- ✅ Production-grade code quality (TypeScript strict mode)
- ✅ Enterprise-ready architecture (component reusability)
- ✅ Design system governance (single source of truth)
- ✅ Responsive design (mobile to desktop)
- ✅ Accessibility-first (WCAG compliant)

---

## ✨ Features

### Core Features (100% Complete)

#### 🔐 **User Onboarding**
- **Sign Up Flow**
  - Multi-field form: first name, last name, email, password
  - Real-time password strength validation (8+ chars, mixed case, numbers)
  - Terms & conditions acceptance
  - Form-level and field-level error handling
  - Mock API integration with persistent storage

- **Email Verification**
  - OTP verification (6-digit code)
  - Resend countdown timer
  - Email confirmation persistence
  - Error recovery

- **Secure Login**
  - Email + password authentication
  - Session persistence (localStorage)
  - Remember me functionality
  - Demo quick-fill for testing
  - Forgot password UI (extensible)

#### 🏠 **Property Discovery**
- **Property Listing Grid**
  - Responsive grid layout (2 cols → 1 col on mobile)
  - High-quality property cards with images
  - Key financial metrics (price, yield, occupancy)
  - Load-more pagination
  - Results counter

- **Advanced Filtering**
  - 5 filter types: Location, Country, Type, Price Range, Yield Range
  - Real-time filter application
  - Clear/Reset functionality
  - Mobile-responsive sidebar (collapsible)
  - 6 mock properties with realistic data

- **Property Cards Display**
  - Property name and location
  - Type badge (Residential/Commercial/Mixed-Use)
  - Min investment requirement
  - Current yield percentage
  - Expected yield projection
  - Available units count
  - Occupancy rate with visual overlay
  - Click-through actions

#### ✔️ **KYC Verification**
- **Status Dashboard** (`/kyc-status`)
  - Current verification status display
  - Color-coded status indicators
  - Step-by-step timeline visualization
  - Status-specific action buttons
  - Email/support contact information

### Enhanced Features (Optional)

- 🏡 **Responsive Design**
  - Mobile: 375px - 568px
  - Tablet: 569px - 1024px
  - Desktop: 1025px+
  - Touch-friendly interfaces

- 🎨 **Institutional Design**
  - Deep navy primary (#0d2847)
  - Professional teal secondary (#00a8a8)
  - Clean typography (system fonts)
  - Consistent spacing and shadows

- 🔒 **Protected Routes**
  - Authentication-required pages
  - Automatic redirect to login
  - Session timeout handling

---

## 🛠 Tech Stack

| Layer | Technology | Version | Purpose |
|-------|-----------|---------|---------|
| **Runtime** | Node.js | 18+ | JavaScript runtime |
| **Frontend Framework** | React | 18.2 | UI library with hooks |
| **Language** | TypeScript | 5.1 | Type-safe JavaScript |
| **Build Tool** | Vite | 4.4 | Lightning-fast bundler |
| **Routing** | React Router | 6.14 | Client-side navigation |
| **CSS Framework** | Bootstrap | 5.3 | Responsive components |
| **Package Manager** | npm | 9.8+ | Dependency management |

### Key Dependencies

```json
{
  "react": "^18.2.0",
  "react-dom": "^18.2.0",
  "react-router-dom": "^6.14.0",
  "bootstrap": "^5.3.0",
  "axios": "^1.4.0"
}
```

### Development Dependencies

```json
{
  "typescript": "^5.1.6",
  "@types/react": "^18.2.14",
  "@types/react-dom": "^18.2.6",
  "@vitejs/plugin-react": "^4.0.0",
  "vite": "^4.4.5",
  "sass": "^1.66.0"
}
```

---

## 🚀 Quick Start

### Prerequisites

- **Node.js** 18.0.0 or higher
- **npm** 9.8.0 or higher (or yarn/pnpm)
- **Git** (for version control)

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/Raj-Comet/MeridianSquare-Investor-Portal.git
cd MeridianSquare-Investor-Portal

# 2. Install dependencies
npm install

# 3. Start development server
npm run dev

# 4. Open in browser
# Navigate to: http://localhost:3000
```

### Build for Production

```bash
# Compile TypeScript and build with Vite
npm run build

# Preview production build locally
npm run preview
```

### Available Scripts

```bash
npm run dev       # Start dev server with HMR
npm run build     # Production build (TypeScript + Vite)
npm run preview   # Preview production build
npm run type-check # Check TypeScript types
npm run lint      # Run ESLint
```

### Testing the Application

#### Demo Credentials

```
Email:    demo@example.com
Password: Password123
```

#### Test Flows

1. **Sign Up Flow**
   - Click "Sign Up"
   - Fill: John Doe | john@example.com | Password123
   - Verify 6-digit OTP (any 6 digits work in demo)
   - Login with those credentials

2. **Property Discovery**
   - Login with demo credentials
   - Browse 6 mock properties
   - Try filters: location, country, price, yield
   - Click "View Details" on a property

3. **KYC Status**
   - Click user avatar → "View KYC Status"
   - See verification timeline

---

## 📁 Project Structure

```
MeridianSquare-Investor-Portal/
├── src/
│   ├── components/
│   │   ├── common/                    # Reusable UI components
│   │   │   ├── FormInput.tsx         # Text input with validation
│   │   │   ├── FormSelect.tsx        # Select dropdown
│   │   │   ├── Button.tsx            # CTA button with loading state
│   │   │   ├── Alert.tsx             # Dismissible alerts
│   │   │   ├── Loading.tsx           # Spinner component
│   │   │   ├── PageContainer.tsx     # Page layout wrapper
│   │   │   └── index.ts              # Barrel exports
│   │   │
│   │   ├── features/                 # Feature-specific components
│   │   │   ├── PropertyCard.tsx      # Individual property display
│   │   │   ├── FilterPanel.tsx       # Property filter controls
│   │   │   └── index.ts              # Barrel exports
│   │   │
│   │   ├── layout/
│   │   │   ├── Header.tsx            # Navigation bar
│   │   │   └── index.ts              # Barrel exports
│   │   │
│   │   └── index.ts                  # Component barrel exports
│   │
│   ├── pages/                         # Page components (routes)
│   │   ├── HomePage.tsx              # Landing page
│   │   ├── SignUpPage.tsx            # User registration
│   │   ├── EmailVerificationPage.tsx # OTP verification
│   │   ├── LoginPage.tsx             # User authentication
│   │   ├── PropertyListPage.tsx      # Main discovery page
│   │   ├── KYCStatusPage.tsx         # Verification status
│   │   └── index.ts                  # Barrel exports
│   │
│   ├── services/
│   │   └── api.service.ts            # Mock API client
│   │
│   ├── types/
│   │   └── index.ts                  # TypeScript interfaces
│   │
│   ├── utils/
│   │   └── helpers.ts                # Helper functions
│   │
│   ├── theme/
│   │   ├── theme-variables.scss      # Design tokens (SINGLE SOURCE OF TRUTH)
│   │   └── index.scss                # Bootstrap import + customization
│   │
│   ├── App.tsx                       # Router setup
│   ├── main.tsx                      # React entry point
│   └── index.html                    # HTML template
│
├── public/                           # Static assets
├── dist/                             # Production build (generated)
│
├── Configuration & Dotfiles
├── .env.example                      # Environment variables template
├── .gitignore                        # Git ignore rules
├── tsconfig.json                     # TypeScript config
├── vite.config.ts                    # Vite config
├── package.json                      # Dependencies & scripts
│
└── Documentation
    ├── README.md                     # This file
    ├── ARCHITECTURE.md               # Component design & hierarchy
    ├── THEME_GOVERNANCE.md           # CSS system & design tokens
    ├── PERFORMANCE.md                # Optimization strategies
    ├── AI_USAGE.md                   # AI tool review
    ├── FEATURES_CHECKLIST.md         # Feature completion status
    └── SUBMISSION.md                 # Project deliverables
```

---

## 🏗 Architecture

### Component Hierarchy

```
App (Router)
├── Layout Layer
│   └── Header (Navigation + Auth)
│
├── Page Layer (Routes)
│   ├── HomePage (/), LoginPage (/login), SignUpPage (/signup)
│   ├── EmailVerificationPage (/verify-email)
│   ├── PropertyListPage (/properties) [Protected]
│   │   ├── FilterPanel (Feature)
│   │   └── PropertyCard x N (Feature)
│   └── KYCStatusPage (/kyc-status) [Protected]
│
└── Common Components (Reusable)
    ├── FormInput, FormSelect
    ├── Button, Alert, Loading
    └── PageContainer
```

### Data Flow

```
User Input
    ↓
Component State (React Hooks)
    ↓
API Service (Mock → Real Backend)
    ↓
Data Persistence (sessionStorage/localStorage)
    ↓
Component Re-render
    ↓
UI Update
```

### Layered Reusability

| Layer | Components | Reuse | Location |
|-------|-----------|-------|----------|
| **Common** | 8 | 20+ times | `src/components/common/` |
| **Feature** | 2 | 3-5 times | `src/components/features/` |
| **Layout** | 1 | Per page | `src/components/layout/` |
| **Pages** | 6 | Once each | `src/pages/` |

---

## 🎨 CSS / Theme Governance

**See:** [THEME_GOVERNANCE.md](./THEME_GOVERNANCE.md)

The application uses a **Single Source of Truth** approach for all styling:

- **Theme File:** `src/theme/theme-variables.scss`
- **Strategy:** SCSS variables override Bootstrap defaults
- **Consumption:** Bootstrap utilities in components (no custom CSS)
- **Scalability:** White-label ready - create new theme files per client

### Design System

**Colors:**
- Primary: Deep Navy (#0d2847) - Trust, stability
- Secondary: Professional Teal (#00a8a8) - Innovation
- Success: Clinical Green (#10a944)
- Danger: Regulatory Red (#d32f2f)

**Typography:**
- Font Stack: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto...
- Base: 0.9375rem (15px)
- Weights: 400 (normal), 500 (medium), 600 (bold)

**Spacing:** 1rem base unit (16px)
- Scale: 0, 0.25, 0.5, 1, 1.5, 2, 3 rem

---

## 📄 Available Documentation

| Document | Purpose | Read Time |
|----------|---------|-----------|
| **README.md** | Setup and quick start | 10 min |
| **ARCHITECTURE.md** | Component design & scaling | 15 min |
| **THEME_GOVERNANCE.md** | CSS system & design tokens | 20 min |
| **PERFORMANCE.md** | Optimization strategies | 15 min |
| **AI_USAGE.md** | AI tool integration review | 20 min |
| **FEATURES_CHECKLIST.md** | Feature completion status | 10 min |
| **SUBMISSION.md** | Project deliverables overview | 15 min |

---

## 🔒 Security Considerations

### Current (Demo)
- ✅ Password strength validation (client-side)
- ✅ Email format validation
- ✅ Form sanitization
- ℹ️ Mock API (no real authentication)

### Production Implementation
- 🔄 Replace mock API with real backend
- 🔄 Implement JWT token management
- 🔄 Add HTTPS/SSL enforcement
- 🔄 Implement CORS policies
- 🔄 Add rate limiting
- 🔄 Secure sensitive data (never store in localStorage)

---

## 📊 Performance

**Bundle Size:**
- HTML: 0.80 KB (gzipped: 0.45 KB)
- CSS: 233.57 KB (gzipped: 32.21 KB)
- JS: 200.20 KB (gzipped: 62.86 KB)

**Optimization Strategies:**
- React component memoization
- Pagination (6 items per page)
- CSS-based layouts (no JS recalculations)
- Lightweight dependencies

---

## 🌐 Browser Support

| Browser | Min Version | Support |
|---------|-------------|---------|
| Chrome | 90+ | ✅ Full |
| Firefox | 88+ | ✅ Full |
| Safari | 14+ | ✅ Full |
| Edge | 90+ | ✅ Full |
| Mobile Safari | 14+ | ✅ Full |

---

## 🔄 API Integration

### Mock API Structure

The `ApiService` provides mock endpoints for:

```typescript
// Authentication
signUp(request: SignUpRequest): Promise<ApiResponse<AuthResponse>>
verifyOTP(email: string, otp: string): Promise<ApiResponse<{verified: boolean}>>
login(request: LoginRequest): Promise<ApiResponse<AuthResponse>>

// Properties
getProperties(filters?: PropertyFilters): Promise<ApiResponse<PropertyListResponse>>
getPropertyById(id: string): Promise<ApiResponse<Property>>

// KYC
getKYCStatus(): Promise<ApiResponse<KYCStatus>>
startKYC(): Promise<ApiResponse<string>>
```

### Real Backend Integration

To connect to a real backend:

1. Update `VITE_API_URL` in `.env.local`
2. Replace API service endpoints
3. Implement proper JWT token management
4. Add error handling & retry logic

---

## 🚀 Deployment

### Deploy to Vercel (Recommended)

```bash
# 1. Push to GitHub (already done)
git push origin main

# 2. Go to https://vercel.com
# 3. Click "New Project"
# 4. Import "MeridianSquare-Investor-Portal"
# 5. Vercel auto-detects Vite + deploys
# ✅ Done! Your app is live
```

### Environment Variables

Create `.env.local` in project root:
```env
VITE_API_URL=https://api.meridianquare.com
VITE_API_DELAY=300
VITE_ENABLE_DEMO_MODE=true
```

---

## 🤝 Contributing

### Development Workflow

```bash
# 1. Create feature branch
git checkout -b feature/your-feature

# 2. Make changes
# 3. Commit with clear messages
git commit -m "feat: add new property filter"

# 4. Push and create PR
git push origin feature/your-feature
```

### Code Style

- **TypeScript:** Strict mode enabled
- **Formatting:** Use project's ESLint config
- **Components:** Functional components with hooks
- **Naming:** PascalCase for components, camelCase for functions

---

## 📝 License

MIT License - See LICENSE file for details

---

## 📞 Support

**Issues & Questions:**
- GitHub Issues: https://github.com/Raj-Comet/MeridianSquare-Investor-Portal/issues
- Email: support@meridianquare.com

---

## 🎓 Learning Resources

- [React Docs](https://react.dev)
- [TypeScript Handbook](https://www.typescriptlang.org/docs/)
- [Vite Guide](https://vitejs.dev/guide/)
- [Bootstrap 5 Docs](https://getbootstrap.com/docs/5.3/)
- [React Router Docs](https://reactrouter.com/)

---

## 📈 Roadmap

### Phase 2 (Backend Integration)
- [ ] Real authentication with JWT
- [ ] Database integration (PostgreSQL/MongoDB)
- [ ] Real KYC provider (Onfido/IDology)
- [ ] Payment processing (Stripe/PayPal)

### Phase 3 (Features)
- [ ] Investment transaction flow
- [ ] Portfolio dashboard
- [ ] Document management
- [ ] Admin dashboard

### Phase 4 (Scale)
- [ ] Multi-language support (AR, EN)
- [ ] Mobile app (React Native)
- [ ] Analytics integration
- [ ] Advanced reporting

---

**Built with ❤️ by the MeridianSquare Team**

**Last Updated:** April 28, 2026  
**Version:** 1.0.0
