# Tech Guidelines – FlatRace

## Übersicht
Dieses Dokument definiert die technischen Entscheidungen, Architekturprinzipien und Entwicklungsstandards für FlatRace. Es dient als Leitfaden für alle technischen Entscheidungen und stellt sicher, dass das gesamte Team konsistent entwickelt.

## Tech Stack Entscheidungen

### Frontend
**Framework:** React 18+ mit TypeScript
- **Begründung:** Starke TypeScript-Unterstützung, große Community, bewährte Patterns
- **State Management:** Redux Toolkit + RTK Query
- **Routing:** React Router v6
- **UI Framework:** Material-UI (MUI) v5
- **Build Tool:** Vite
- **Language:** TypeScript 5.0+

### Backend & Database
**Platform:** Supabase (PostgreSQL + Auth + Storage + Edge Functions)
- **Begründung:** Vollständiger BaaS-Stack, RLS Security, skalierbar, günstig für MVP
- **Database:** PostgreSQL 15+ mit PostGIS für Geodaten
- **Auth:** Supabase Auth (E-Mail/Passwort + Google OAuth)
- **Storage:** Supabase Storage für Exports und Assets
- **Edge Functions:** Supabase Edge Runtime für Serverless-Funktionen

### Entwicklung & DevOps
**Version Control:** Git mit GitHub
**CI/CD:** GitHub Actions
**Hosting:** Vercel (Frontend) + Supabase (Backend)
**Monitoring:** Sentry für Error Tracking, Vercel Analytics
**Testing:** Jest + React Testing Library + Playwright (E2E)

### Zusätzliche Tools
**API Client:** Axios für HTTP-Requests
**Charts:** Chart.js oder Recharts für Community-Vergleich
**Forms:** React Hook Form + Yup für Validierung
**i18n:** react-i18next für Internationalisierung
**PDF Generation:** Puppeteer (Server) oder jsPDF (Client)

---

## Architekturprinzipien

### 1. Separation of Concerns
- **Frontend:** UI-Komponenten, User Experience, Client-State
- **Backend:** Business Logic, Data Persistence, Security
- **Database:** Data Integrity, Performance, Security

### 2. API-First Design
- Alle Features beginnen mit API-Design
- RESTful Endpunkte mit klarer Dokumentation
- Versionierte APIs mit Deprecation-Strategie

### 3. Security by Design
- Row Level Security (RLS) für alle Daten
- Input Validation auf allen Ebenen
- Principle of Least Privilege
- DSGVO-konform von Anfang an

### 4. Performance First
- Lazy Loading für alle Routen
- Code Splitting für große Bundles
- Caching-Strategien für Community-Daten
- Optimistische UI-Updates

### 5. Mobile-First Responsive
- Mobile-optimierte UI von Anfang an
- Progressive Web App (PWA) Fähigkeiten
- Touch-optimierte Interaktionen

### 6. Accessibility (A11y)
- WCAG 2.1 AA Compliance
- Screen Reader Support
- Keyboard Navigation
- High Contrast Support

---

## Frontend Guidelines

### Komponenten-Architektur
```
src/
├── components/           # Wiederverwendbare Komponenten
│   ├── ui/              # Basis-UI-Komponenten (Button, Input, etc.)
│   ├── forms/           # Form-spezifische Komponenten
│   ├── charts/          # Chart-Komponenten
│   └── layout/          # Layout-Komponenten
├── pages/               # Page-Komponenten (Routes)
├── hooks/               # Custom React Hooks
├── lib/                 # Utilities und Konfiguration
├── types/               # TypeScript Type Definitions
├── constants/           # Konstanten und Enums
└── styles/              # Global Styles und Theme
```

### State Management
- **Local State:** useState/useReducer für Komponenten-State
- **Server State:** RTK Query für API-Daten
- **Global State:** Redux Toolkit nur für komplexe App-State
- **Form State:** React Hook Form für Formulare

### Naming Conventions
```typescript
// Komponenten: PascalCase
export const PropertyCard = () => { ... }

// Hooks: camelCase mit 'use' Prefix
export const usePropertyData = () => { ... }

// Types: PascalCase mit 'Type' Suffix
export type PropertyType = { ... }

// Enums: PascalCase
export enum PropertyStatus { ... }

// Konstanten: UPPER_SNAKE_CASE
export const MAX_FILE_SIZE = 10 * 1024 * 1024
```

### Error Handling
```typescript
// Custom Error Hook
const useErrorHandler = () => {
  const [error, setError] = useState<Error | null>(null)

  const handleError = (error: Error) => {
    console.error('Error:', error)
    setError(error)
    // Sentry logging
    Sentry.captureException(error)
  }

  return { error, handleError, clearError: () => setError(null) }
}
```

---

## Backend Guidelines

### API Design Principles
- **RESTful:** Ressourcen-orientierte URLs
- **Versioned:** `/v1/` Prefix für alle Endpunkte
- **Consistent:** Einheitliche Response-Formate
- **Documented:** OpenAPI/Swagger Dokumentation

### Database Design
- **Normalized:** Vermeidung von Redundanzen
- **Indexed:** Performance-optimierte Indizes
- **Constrained:** Foreign Keys und Constraints
- **Audited:** Änderungsprotokolle für wichtige Daten

### Edge Functions
```typescript
// supabase/functions/export-pdf/index.ts
import { serve } from 'https://deno.land/std@0.168.0/http/server.ts'
import puppeteer from 'https://deno.land/x/puppeteer@16.2.0/mod.ts'

serve(async (req) => {
  const { propertyId, template } = await req.json()

  // PDF Generation Logic
  const browser = await puppeteer.launch()
  const page = await browser.newPage()

  // Generate PDF
  const pdf = await page.pdf({
    format: 'A4',
    printBackground: true
  })

  return new Response(pdf, {
    headers: { 'Content-Type': 'application/pdf' }
  })
})
```

---

## Database Guidelines

### Schema Design
```sql
-- Properties Table
CREATE TABLE properties (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id UUID NOT NULL REFERENCES auth.users(id) ON DELETE CASCADE,
  title VARCHAR(255) NOT NULL,
  location_geo GEOGRAPHY(POINT),
  location_address JSONB,
  area_m2 DECIMAL(8,2),
  rooms DECIMAL(3,1),
  year_built INTEGER,
  energy_type VARCHAR(50),
  energy_class VARCHAR(10),
  amenities JSONB DEFAULT '[]'::jsonb,
  condition VARCHAR(20),
  purchase_price DECIMAL(12,2),
  rent_monthly DECIMAL(10,2),
  operating_costs JSONB,
  status VARCHAR(20) DEFAULT 'draft',
  visibility VARCHAR(20) DEFAULT 'private',
  tags TEXT[] DEFAULT '{}',
  created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW(),
  updated_at TIMESTAMP WITH TIME ZONE DEFAULT NOW()
);

-- Row Level Security
ALTER TABLE properties ENABLE ROW LEVEL SECURITY;

CREATE POLICY "Users can view own properties" ON properties
  FOR SELECT USING (auth.uid() = user_id);

CREATE POLICY "Users can insert own properties" ON properties
  FOR INSERT WITH CHECK (auth.uid() = user_id);
```

### Performance Optimizations
```sql
-- Indizes für häufige Queries
CREATE INDEX idx_properties_user_status ON properties(user_id, status);
CREATE INDEX idx_properties_location ON properties USING GIST(location_geo);
CREATE INDEX idx_properties_area ON properties(area_m2);

-- Materialized View für Community Stats
CREATE MATERIALIZED VIEW community_stats_aggregated AS
SELECT
  region_key,
  metric_key,
  COUNT(*) as sample_size,
  AVG(metric_value) as mean,
  STDDEV(metric_value) as std_dev,
  PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY metric_value) as median
FROM community_stats
GROUP BY region_key, metric_key;

-- Refresh alle 6 Stunden
REFRESH MATERIALIZED VIEW CONCURRENTLY community_stats_aggregated;
```

### Data Migration
```sql
-- Migration Script Template
BEGIN;

-- Add new column
ALTER TABLE properties ADD COLUMN new_field VARCHAR(100);

-- Update existing data
UPDATE properties SET new_field = 'default_value' WHERE new_field IS NULL;

-- Add constraint
ALTER TABLE properties ALTER COLUMN new_field SET NOT NULL;

-- Update schema version
INSERT INTO schema_versions (version, description) VALUES ('1.2.0', 'Add new_field to properties');

COMMIT;
```

---

## DevOps & Deployment

### CI/CD Pipeline
```yaml
# .github/workflows/deploy.yml
name: Deploy
on:
  push:
    branches: [main, develop]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-node@v3
        with:
          node-version: '18'
      - run: npm ci
      - run: npm run test
      - run: npm run build

  deploy:
    needs: test
    runs-on: ubuntu-latest
    steps:
      - uses: amondnet/vercel-action@v25
        with:
          vercel-token: ${{ secrets.VERCEL_TOKEN }}
          vercel-org-id: ${{ secrets.VERCEL_ORG_ID }}
          vercel-project-id: ${{ secrets.VERCEL_PROJECT_ID }}
```

### Environment Management
```bash
# .env.example
# Frontend Environment Variables
VITE_SUPABASE_URL=https://your-project.supabase.co
VITE_SUPABASE_ANON_KEY=your-anon-key
VITE_APP_ENV=development

# Supabase Environment Variables
SUPABASE_SERVICE_ROLE_KEY=your-service-role-key
SUPABASE_JWT_SECRET=your-jwt-secret
DATABASE_URL=postgresql://user:pass@host:5432/db
```

### Monitoring Setup
```typescript
// src/lib/sentry.ts
import * as Sentry from '@sentry/react'

Sentry.init({
  dsn: import.meta.env.VITE_SENTRY_DSN,
  environment: import.meta.env.VITE_APP_ENV,
  integrations: [
    new Sentry.BrowserTracing({
      tracePropagationTargets: ['localhost', 'https://api.flatrace.com'],
    }),
    new Sentry.Replay(),
  ],
  tracesSampleRate: 1.0,
  replaysSessionSampleRate: 0.1,
  replaysOnErrorSampleRate: 1.0,
})
```

---

## Performance Guidelines

### Frontend Performance
- **Bundle Size:** < 300KB gzipped für Initial Load
- **First Contentful Paint:** < 2 Sekunden
- **Largest Contentful Paint:** < 2.5 Sekunden
- **Cumulative Layout Shift:** < 0.1

### Optimierungstechniken
```typescript
// Lazy Loading für Routes
const PropertyPage = lazy(() => import('./pages/PropertyPage'))

<Route path="/property/:id" element={
  <Suspense fallback={<PropertySkeleton />}>
    <PropertyPage />
  </Suspense>
} />

// Code Splitting für große Libraries
const ChartComponent = lazy(() => import('./components/ChartComponent'))

// Image Optimization
import { getOptimizedImageUrl } from './lib/imageUtils'

const optimizedUrl = getOptimizedImageUrl(imageUrl, { width: 400, height: 300, quality: 80 })
```

### Caching Strategy
```typescript
// RTK Query Cache Configuration
export const apiSlice = createApi({
  baseQuery: fetchBaseQuery({
    baseUrl: '/api',
    prepareHeaders: (headers, { getState }) => {
      const token = (getState() as RootState).auth.token
      if (token) {
        headers.set('authorization', `Bearer ${token}`)
      }
      return headers
    },
  }),
  endpoints: (builder) => ({
    getCommunityStats: builder.query({
      query: ({ region, metric }) => `community/stats?region=${region}&metric=${metric}`,
      keepUnusedDataFor: 24 * 60 * 60 * 1000, // 24 hours
    }),
  }),
})
```

---

## Security Guidelines

### Authentication & Authorization
```typescript
// Supabase Auth Integration
import { createClient } from '@supabase/supabase-js'

const supabase = createClient(
  import.meta.env.VITE_SUPABASE_URL,
  import.meta.env.VITE_SUPABASE_ANON_KEY,
  {
    auth: {
      autoRefreshToken: true,
      persistSession: true,
      detectSessionInUrl: true
    }
  }
)

// Protected Route Component
const ProtectedRoute = ({ children }: { children: React.ReactNode }) => {
  const { user, loading } = useAuth()

  if (loading) return <LoadingSpinner />
  if (!user) return <Navigate to="/login" />

  return <>{children}</>
}
```

### Data Validation
```typescript
// Input Validation Schema
import * as yup from 'yup'

export const propertySchema = yup.object().shape({
  title: yup.string().required('Titel ist erforderlich').min(2, 'Mindestens 2 Zeichen'),
  area_m2: yup.number().required('Wohnfläche ist erforderlich').positive('Muss positiv sein'),
  rooms: yup.number().required('Zimmeranzahl ist erforderlich').min(1, 'Mindestens 1 Zimmer'),
  location_address: yup.object().shape({
    street: yup.string().required('Straße ist erforderlich'),
    zip: yup.string().required('PLZ ist erforderlich').matches(/^[0-9]{4,5}$/, 'Ungültige PLZ'),
    city: yup.string().required('Stadt ist erforderlich'),
  }),
})

// API Validation Middleware
export const validatePropertyData = (data: any) => {
  try {
    return propertySchema.validateSync(data, { abortEarly: false })
  } catch (error) {
    throw new ValidationError('Invalid property data', error.errors)
  }
}
```

### XSS Prevention
```typescript
// Sanitize HTML Input
import DOMPurify from 'dompurify'

const sanitizeInput = (input: string): string => {
  return DOMPurify.sanitize(input, {
    ALLOWED_TAGS: [], // Keine HTML-Tags erlaubt
    ALLOWED_ATTR: [],
  })
}

// Safe InnerHTML
const SafeHtml = ({ html }: { html: string }) => {
  const sanitizedHtml = useMemo(() => DOMPurify.sanitize(html), [html])
  return <div dangerouslySetInnerHTML={{ __html: sanitizedHtml }} />
}
```

---

## Testing Strategy

### Testing Pyramid
- **Unit Tests:** 70% - Komponenten, Hooks, Utilities
- **Integration Tests:** 20% - API-Integrationen, Workflows
- **E2E Tests:** 10% - Kritische User Journeys

### Testing Tools
```typescript
// Jest Configuration
// jest.config.js
module.exports = {
  testEnvironment: 'jsdom',
  setupFilesAfterEnv: ['<rootDir>/src/test/setup.ts'],
  moduleNameMapping: {
    '\\.(css|less|scss|sass)$': 'identity-obj-proxy',
    '\\.(jpg|jpeg|png|gif|svg)$': '<rootDir>/src/test/__mocks__/fileMock.js',
  },
  collectCoverageFrom: [
    'src/**/*.{ts,tsx}',
    '!src/**/*.d.ts',
    '!src/test/**',
  ],
  coverageThreshold: {
    global: {
      branches: 80,
      functions: 80,
      lines: 80,
      statements: 80,
    },
  },
}
```

### Test Examples
```typescript
// Unit Test für Hook
import { renderHook, act } from '@testing-library/react'
import { usePropertyForm } from '../hooks/usePropertyForm'

describe('usePropertyForm', () => {
  it('should initialize with empty form', () => {
    const { result } = renderHook(() => usePropertyForm())

    expect(result.current.formData).toEqual({
      title: '',
      area_m2: 0,
      rooms: 0,
    })
  })

  it('should update form data', () => {
    const { result } = renderHook(() => usePropertyForm())

    act(() => {
      result.current.updateField('title', 'Test Property')
    })

    expect(result.current.formData.title).toBe('Test Property')
  })
})

// Integration Test für API
import { rest } from 'msw'
import { setupServer } from 'msw/node'
import { render, screen, waitFor } from '@testing-library/react'
import { PropertyList } from '../components/PropertyList'

const server = setupServer(
  rest.get('/api/properties', (req, res, ctx) => {
    return res(ctx.json([
      { id: '1', title: 'Property 1', area_m2: 85 },
      { id: '2', title: 'Property 2', area_m2: 120 },
    ]))
  })
)

describe('PropertyList', () => {
  beforeAll(() => server.listen())
  afterEach(() => server.resetHandlers())
  afterAll(() => server.close())

  it('should load and display properties', async () => {
    render(<PropertyList />)

    await waitFor(() => {
      expect(screen.getByText('Property 1')).toBeInTheDocument()
      expect(screen.getByText('Property 2')).toBeInTheDocument()
    })
  })
})
```

### E2E Testing
```typescript
// Playwright Test
import { test, expect } from '@playwright/test'

test.describe('Property Creation Flow', () => {
  test('should create property successfully', async ({ page }) => {
    // Login
    await page.goto('/login')
    await page.fill('[data-testid="email"]', 'test@example.com')
    await page.fill('[data-testid="password"]', 'password')
    await page.click('[data-testid="login-button"]')

    // Navigate to create property
    await page.click('[data-testid="create-property"]')

    // Fill form
    await page.fill('[data-testid="title"]', 'Test Property')
    await page.fill('[data-testid="area"]', '85')
    await page.fill('[data-testid="rooms"]', '3')

    // Submit
    await page.click('[data-testid="submit"]')

    // Verify success
    await expect(page.locator('[data-testid="success-message"]')).toBeVisible()
    await expect(page.locator('[data-testid="property-title"]')).toContainText('Test Property')
  })
})
```

---

## Code Quality Standards

### Code Style
```json
// .eslintrc.js
module.exports = {
  root: true,
  env: { browser: true, es2020: true },
  extends: [
    'eslint:recommended',
    '@typescript-eslint/recommended',
    'plugin:react/recommended',
    'plugin:react/jsx-runtime',
    'plugin:react-hooks/recommended',
  ],
  ignorePatterns: ['dist', '.eslintrc.js'],
  parser: '@typescript-eslint/parser',
  plugins: ['react-refresh'],
  rules: {
    'react-refresh/only-export-components': [
      'warn',
      { allowConstantExport: true },
    ],
    '@typescript-eslint/no-unused-vars': ['error', { argsIgnorePattern: '^_' }],
    'prefer-const': 'error',
    'no-var': 'error',
  },
}
```

### Pre-commit Hooks
```json
// package.json
{
  "husky": {
    "hooks": {
      "pre-commit": "lint-staged"
    }
  },
  "lint-staged": {
    "*.{ts,tsx}": [
      "eslint --fix",
      "prettier --write",
      "jest --findRelatedTests --passWithNoTests"
    ],
    "*.{json,md}": [
      "prettier --write"
    ]
  }
}
```

### Documentation Standards
```typescript
/**
 * Hook for managing property form state and validation
 *
 * @param initialData - Optional initial form data
 * @returns Form state and handlers
 *
 * @example
 * ```typescript
 * const { formData, updateField, submitForm } = usePropertyForm({
 *   title: 'My Property',
 *   area_m2: 85
 * })
 * ```
 */
export const usePropertyForm = (initialData?: Partial<Property>) => {
  // Implementation
}
```

---

## Monitoring & Observability

### Application Monitoring
```typescript
// Performance Monitoring
import { getCLS, getFID, getFCP, getLCP, getTTFB } from 'web-vitals'

getCLS(console.log)
getFID(console.log)
getFCP(console.log)
getLCP(console.log)
getTTFB(console.log)

// Error Boundary
class ErrorBoundary extends React.Component {
  componentDidCatch(error: Error, errorInfo: React.ErrorInfo) {
    Sentry.captureException(error, { contexts: { react: errorInfo } })
  }

  render() {
    if (this.state.hasError) {
      return <ErrorFallback />
    }
    return this.props.children
  }
}
```

### Business Metrics
```typescript
// Analytics Events
import { Analytics } from './lib/analytics'

const trackPropertyCreated = (property: Property) => {
  Analytics.track('property_created', {
    property_id: property.id,
    area_m2: property.area_m2,
    rooms: property.rooms,
    location: property.location_address.city,
  })
}

const trackCommunityComparison = (propertyId: string, metrics: string[]) => {
  Analytics.track('community_comparison_viewed', {
    property_id: propertyId,
    metrics_viewed: metrics,
    timestamp: new Date().toISOString(),
  })
}
```

---

## Migration & Refactoring Guidelines

### Breaking Changes
1. **Version bump** in package.json
2. **Deprecation warnings** für alte APIs
3. **Migration guide** in CHANGELOG.md
4. **Gradual rollout** mit Feature Flags
5. **Rollback plan** dokumentiert

### Refactoring Process
1. **Identify** technische Schulden
2. **Create** technische Spezifikation
3. **Test** Auswirkungen
4. **Implement** schrittweise
5. **Monitor** Performance-Metriken
6. **Document** Änderungen

---

## Team Collaboration

### Code Review Guidelines
- **Mandatory** für alle Pull Requests
- **Automated checks** müssen passieren
- **Cross-functional reviews** für komplexe Features
- **Knowledge sharing** durch Pair Programming
- **Constructive feedback** mit konkreten Vorschlägen

### Knowledge Management
- **Architecture Decision Records** (ADRs) für wichtige Entscheidungen
- **Playbooks** für wiederkehrende Aufgaben
- **Runbooks** für Incident Response
- **Documentation** immer up-to-date halten

---

## Conclusion

Diese Tech Guidelines dienen als lebendes Dokument und werden regelmäßig aktualisiert. Bei Fragen oder Unklarheiten:
1. **Check existing documentation** first
2. **Discuss with team** for clarifications
3. **Update documentation** when decisions are made
4. **Follow established patterns** for consistency

**Letzte Aktualisierung:** Dezember 2024
**Verantwortlich:** Tech Lead / Architecture Team

