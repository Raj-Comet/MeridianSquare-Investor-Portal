# MeridianSquare Investor Portal

## Overview

A React + Vite + TypeScript application for a regulated real asset tokenization platform, focusing on investor onboarding and property listing. The platform targets UAE first, then US markets.

**Technology Stack:**
- React 18.2 with TypeScript
- Vite (fast build tool)
- Bootstrap 5.3 (CSS framework)
- React Router 6 (client-side routing)
- Mock API service (backend abstraction layer)

## Project Structure

```
src/
├── components/
│   ├── common/                 # Reusable UI components (Button, FormInput, etc.)
│   │   ├── FormInput.tsx       # Text input with validation
│   │   ├── FormSelect.tsx      # Dropdown select
│   │   ├── Button.tsx          # Enhanced button with loading state
│   │   ├── Alert.tsx           # Alert/notification component
│   │   ├── Loading.tsx         # Loading spinner
│   │   ├── PageContainer.tsx   # Standard page wrapper
│   │   └── index.ts            # Centralized exports
│   ├── features/               # Feature-specific components
│   │   ├── PropertyCard.tsx    # Individual property listing card
│   │   └── FilterPanel.tsx     # Property filters sidebar
│   └── layout/
│       └── Header.tsx          # Navigation header with user menu
├── pages/
│   ├── HomePage.tsx            # Landing page
│   ├── SignUpPage.tsx          # User registration
│   ├── EmailVerificationPage.tsx
│   ├── LoginPage.tsx           # User authentication
│   ├── PropertyListPage.tsx    # Main property grid with filters
│   └── KYCStatusPage.tsx       # KYC verification status
├── services/
│   └── api.service.ts          # Mock API client with data persistence
├── types/
│   └── index.ts                # TypeScript interfaces
├── utils/
│   └── helpers.ts              # Utility functions (formatting, validation)
├── theme/
│   ├── theme-variables.scss    # Design tokens (colors, spacing, typography)
│   └── index.scss              # Bootstrap imports + minimal customizations
├── App.tsx                     # Main component with routing
└── main.tsx                    # Application entry point
```

## Quick Start

### Prerequisites
- Node.js 18+ and npm/yarn
- Git (optional, for version control)

### Installation

```bash
# Navigate to project directory
cd e:\MeridianSquare\ Investor\ Portal

# Install dependencies
npm install

# Start development server
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview
```

The application will open at `http://localhost:3000`

### Demo Credentials

For testing the login flow:
- **Email:** Any email you used during signup
- **Password:** `Password123` (or any password entered during signup)

The demo also provides a quick-fill button on the login page.

## Core Features

### ✅ Implemented (Required Scope)

#### 1. **Onboarding Flow**
- **Sign Up Page** (`/signup`)
  - First name, last name, email, password
  - Password strength validation (8+ chars, uppercase, lowercase, number)
  - Terms & conditions acceptance
  - Mock API integration with sessionStorage persistence
  
- **Email Verification** (`/verify-email`)
  - OTP entry (6-digit code)
  - Resend OTP with countdown timer
  - Email persistence from signup flow
  
- **Login Page** (`/login`)
  - Email and password authentication
  - Remember me checkbox
  - Forgot password link (UI placeholder)
  - Demo credentials helper

#### 2. **Property Listing Page**
- **Grid Layout** (`/properties`)
  - Responsive grid (2 columns on desktop, 1 on mobile)
  - Property cards with images, key metrics
  - Load more pagination
  
- **Property Cards**
  - Property type badge
  - Occupancy indicator overlay
  - Min investment and current yield at a glance
  - Expected yield and available units
  - "View Details" button
  
- **Filtering System**
  - Location filter (Dubai, Abu Dhabi, New York, San Francisco)
  - Country filter (UAE, US)
  - Property type filter (Residential, Commercial, Mixed-Use)
  - Price range inputs (Min/Max Investment)
  - Yield range inputs (Min/Max %)
  - Apply/Reset buttons
  - Mobile-responsive (collapsible on small screens)
  - Results summary counter

### ✅ Implemented (Optional Scope)

#### 3. **KYC Status Page**
- **Status Display** (`/kyc-status`)
  - Current verification status (Pending, In Progress, Approved, Rejected)
  - Status-specific messaging and color indicators
  - Timeline visualization showing verification steps
  - Next action buttons based on status
  
#### 4. **Authentication & Routing**
- Protected routes (property listing, KYC require login)
- Automatic login redirect for authenticated users
- Session persistence using localStorage/sessionStorage

## API Integration

The `ApiService` provides mock endpoints for:
- User authentication (sign up, login, verify OTP)
- Property listing with filters and pagination
- KYC status checking

Data is persisted in `sessionStorage` for demo purposes. In a real application:
- Replace API calls with actual backend URLs
- Use proper authentication tokens (JWT)
- Implement real data persistence

## CSS/Theme Governance

See [THEME_GOVERNANCE.md](./THEME_GOVERNANCE.md) for comprehensive CSS architecture and design system.

**Key Points:**
- Single source of truth: `src/theme/theme-variables.scss`
- Bootstrap variables are overridden globally
- No component-specific CSS files (Bootstrap utilities only)
- Future-ready for white-label theming

## Component Architecture

See [ARCHITECTURE.md](./ARCHITECTURE.md) for detailed component structure and reusability strategy.

**Hierarchy:**
```
App (Router setup)
├── Header (Navigation)
├── Pages (Route targets)
│   ├── HomePage
│   ├── SignUpPage
│   ├── PropertyListPage
│   │   ├── FilterPanel (Feature)
│   │   └── PropertyCard x N (Feature)
│   └── ...
└── Footer
```

## Performance Considerations

See [PERFORMANCE.md](./PERFORMANCE.md) for detailed optimization strategies.

**Key Strategies:**
- React component memoization for list rendering
- Pagination to limit DOM nodes
- CSS-based layout (no JS recalculations)
- Mock API delay simulation for realistic network testing

## Responsive Design

Breakpoints follow Bootstrap 5:
- **xs**: 0px (mobile)
- **sm**: 576px
- **md**: 768px (tablet)
- **lg**: 992px (desktop)
- **xl**: 1200px (large desktop)

Components adapt automatically using Bootstrap grid system.

## Styling Approach

All styling uses **Bootstrap utility classes** exclusively:
- No custom CSS files in components
- No CSS-in-JS
- Consistent with Bootstrap design system
- Easy to theme by modifying variables in `theme/`

**Example:**
```jsx
// ✅ DO: Bootstrap utilities only
<div className="row g-4 mb-4">
  <div className="col-md-6">
    <div className="card p-3 border-0 shadow-sm">
      {/* content */}
    </div>
  </div>
</div>

// ❌ DON'T: Custom CSS
<div style={{ display: 'flex', gap: '1rem', marginBottom: '1rem' }}>
  {/* content */}
</div>
```

## Development Workflow

### Adding a New Component

1. Create component in appropriate folder (`components/common/` or `components/features/`)
2. Use only Bootstrap classes for styling
3. Import and export from folder's `index.ts`
4. Use TypeScript interfaces for props

### Adding a New Page

1. Create page in `src/pages/`
2. Add route in `App.tsx`
3. Protect route with `<ProtectedRoute>` if needed
4. Use `<PageContainer>` for consistent spacing

### Available Utilities

See `src/utils/helpers.ts`:
- `formatCurrency()` - Format prices with country-specific currency
- `formatPercentage()` - Format yield values
- `validateEmail()` - Email format validation
- `validatePassword()` - Password strength validation
- `getInitials()` - Extract name initials
- `truncateText()` - Truncate long strings
- `debounce()` - Debounce function calls

## Browser Support

- Chrome/Edge 90+
- Firefox 88+
- Safari 14+
- Mobile browsers (iOS Safari 14+, Chrome Mobile)

## Next Steps (Production Readiness)

1. **Backend Integration**
   - Replace `ApiService` mock calls with real API endpoints
   - Implement JWT token authentication
   - Add real data persistence

2. **KYC Integration**
   - Integrate third-party KYC provider (e.g., Onfido, IDology)
   - Document embedded flow implementation

3. **Security**
   - Implement CSRF protection
   - Add content security policy headers
   - Implement rate limiting
   - Secure token storage (HttpOnly cookies)

4. **Performance**
   - Implement code splitting by route
   - Add image optimization
   - Lazy load components
   - Implement service worker for offline support

5. **Analytics**
   - Add conversion tracking
   - Implement error logging
   - Add performance monitoring

6. **Testing**
   - Add unit tests (Jest + React Testing Library)
   - Add E2E tests (Cypress or Playwright)
   - Add visual regression testing

## File Sizes

Current bundle size (uncompressed):
- Main app: ~150KB
- Bootstrap: ~180KB
- Total: ~330KB (gzipped: ~80KB)

## License

Proprietary - MeridianSquare Global

## Support

For questions or issues, contact: support@meridiansquare.com
#   M e r i d i a n S q u a r e - I n v e s t o r - P o r t a l  
 