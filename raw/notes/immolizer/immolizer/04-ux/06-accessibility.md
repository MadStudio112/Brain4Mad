# Accessibility Guidelines – FlatRace

## Übersicht
Dieses Dokument definiert die Accessibility-Standards (A11y) für FlatRace. Alle Features müssen WCAG 2.1 AA Standards erfüllen, um eine inklusive Nutzererfahrung zu gewährleisten.

## WCAG 2.1 AA Compliance

### Prinzip 1: Wahrnehmbar (Perceivable)
**Richtlinie 1.1: Textalternativen**
- Alle Bilder müssen aussagekräftige Alt-Texte haben
- Icons müssen screen reader kompatible Labels haben
- Charts und Graphen müssen textuelle Alternativen bieten

**Richtlinie 1.3: Anpassbar**
- Inhalte müssen in verschiedenen Formaten präsentiert werden können
- Semantische HTML-Struktur für Screen Reader
- Logische Lesereihenfolge unabhängig vom visuellen Layout

**Richtlinie 1.4: Unterscheidbar**
- Farbkontrast mindestens 4.5:1 für normalen Text, 3:1 für großen Text
- Text muss ohne Farbe allein verständlich sein
- Fokus-Indikatoren müssen deutlich sichtbar sein

### Prinzip 2: Bedienbar (Operable)
**Richtlinie 2.1: Tastaturzugänglich**
- Alle Interaktionen müssen per Tastatur möglich sein
- Keine Tastatur-Fallen (z.B. Modal ohne Escape)
- Logische Tab-Reihenfolge

**Richtlinie 2.2: Ausreichend Zeit**
- Keine zeitkritischen Aktionen ohne Möglichkeit zur Verlängerung
- Möglichkeit, automatisch ablaufende Inhalte zu stoppen
- Warnung vor Zeitüberschreitungen

**Richtlinie 2.3: Anfälle**
- Keine blinkenden Inhalte mit Frequenz > 3 Hz
- Möglichkeit, Animationen zu deaktivieren

### Prinzip 3: Verständlich (Understandable)
**Richtlinie 3.1: Lesbar**
- Sprache des Dokuments muss klar angegeben sein
- Ungewöhnliche Wörter und Abkürzungen müssen erklärt werden
- Leseniveau nicht höher als untere Sekundarstufe

**Richtlinie 3.2: Vorhersehbar**
- Navigationsmechanismen bleiben konsistent
- Komponenten mit gleicher Funktion sehen gleich aus
- Keine unerwarteten Kontextänderungen

**Richtlinie 3.3: Hilfestellung bei Eingaben**
- Klare Labels für alle Formularfelder
- Hilfetexte bei Fehlern
- Möglichkeit zur Fehlerbehebung und -vermeidung

### Prinzip 4: Robust (Robust)
**Richtlinie 4.1: Kompatibel**
- Validierung aller HTML- und CSS-Strukturen
- Unterstützung für assistierende Technologien
- Klare, konsistente DOM-Struktur

---

## Technische Implementierung

### HTML Accessibility Best Practices

```html
<!-- Semantische Struktur -->
<header role="banner">
  <nav role="navigation" aria-label="Hauptnavigation">
    <ul>
      <li><a href="/dashboard" aria-current="page">Dashboard</a></li>
      <li><a href="/properties">Immobilien</a></li>
      <li><a href="/community">Community</a></li>
    </ul>
  </nav>
</header>

<main role="main">
  <h1>Meine Immobilien</h1>

  <!-- Formular mit Labels -->
  <form aria-labelledby="property-form">
    <fieldset>
      <legend id="property-form">Immobilie hinzufügen</legend>

      <div>
        <label for="property-title">Titel der Immobilie</label>
        <input
          id="property-title"
          type="text"
          aria-describedby="title-help"
          required
        />
        <span id="title-help">z.B. "3-Zimmer-Wohnung München"</span>
      </div>

      <div>
        <label for="property-area">Wohnfläche (m²)</label>
        <input
          id="property-area"
          type="number"
          min="1"
          max="10000"
          step="0.1"
          aria-describedby="area-unit"
          required
        />
        <span id="area-unit">Quadratmeter</span>
      </div>
    </fieldset>
  </form>
</main>

<footer role="contentinfo">
  <p>&copy; 2024 FlatRace</p>
</footer>
```

### ARIA Attribute Guidelines

```typescript
// Screen Reader Announcements
const announceToScreenReader = (message: string) => {
  const announcement = document.createElement('div')
  announcement.setAttribute('aria-live', 'polite')
  announcement.setAttribute('aria-atomic', 'true')
  announcement.className = 'sr-only'
  announcement.textContent = message

  document.body.appendChild(announcement)

  setTimeout(() => {
    document.body.removeChild(announcement)
  }, 1000)
}

// Loading States
const LoadingButton = ({ loading, children, ...props }) => (
  <button
    {...props}
    aria-disabled={loading}
    aria-describedby={loading ? 'loading-status' : undefined}
  >
    {children}
    {loading && (
      <span id="loading-status" className="sr-only">
        Wird geladen, bitte warten
      </span>
    )}
  </button>
)

// Error States
const ErrorMessage = ({ error, fieldId }) => (
  <div
    id={`${fieldId}-error`}
    role="alert"
    aria-live="polite"
    className="error-message"
  >
    {error}
  </div>
)
```

### Keyboard Navigation

```typescript
// Custom Keyboard Handlers
const useKeyboardNavigation = () => {
  const [focusedIndex, setFocusedIndex] = useState(0)

  const handleKeyDown = (event: KeyboardEvent, items: any[]) => {
    switch (event.key) {
      case 'ArrowDown':
        event.preventDefault()
        setFocusedIndex(prev => Math.min(prev + 1, items.length - 1))
        break
      case 'ArrowUp':
        event.preventDefault()
        setFocusedIndex(prev => Math.max(prev - 1, 0))
        break
      case 'Enter':
      case ' ':
        event.preventDefault()
        // Handle selection
        break
      case 'Escape':
        // Close dropdown/modal
        break
    }
  }

  return { focusedIndex, handleKeyDown }
}

// Skip Links
const SkipLinks = () => (
  <nav className="skip-links" aria-label="Schnellnavigation">
    <a href="#main-content" className="skip-link">
      Zum Hauptinhalt springen
    </a>
    <a href="#navigation" className="skip-link">
      Zur Navigation springen
    </a>
    <a href="#search" className="skip-link">
      Zur Suche springen
    </a>
  </nav>
)
```

---

## Chart & Data Visualization Accessibility

### Chart Accessibility Best Practices

```typescript
// Accessible Chart Component
const AccessibleChart = ({ data, title, description }) => {
  const chartId = useId()

  return (
    <figure role="img" aria-labelledby={`${chartId}-title`} aria-describedby={`${chartId}-desc`}>
      <figcaption id={`${chartId}-title`} className="sr-only">
        {title}
      </figcaption>
      <div id={`${chartId}-desc`} className="sr-only">
        {description}
      </div>

      {/* Visual Chart */}
      <ChartComponent
        data={data}
        aria-hidden="true" // Screen readers ignorieren das visuelle Chart
      />

      {/* Text Alternative */}
      <div className="chart-data-table" aria-label="Chart data in tabular format">
        <table>
          <caption>{title}</caption>
          <thead>
            <tr>
              <th>Kategorie</th>
              <th>Wert</th>
              <th>Prozent</th>
            </tr>
          </thead>
          <tbody>
            {data.map(item => (
              <tr key={item.category}>
                <td>{item.category}</td>
                <td>{item.value}</td>
                <td>{item.percentage}%</td>
              </tr>
            ))}
          </tbody>
        </table>
      </div>
    </figure>
  )
}

// Community Stats Chart
const CommunityStatsChart = ({ propertyValue, distribution }) => {
  const description = `
    Normalverteilung der Wohnflächen in dieser Region.
    Mittelwert: ${distribution.mean} m²,
    Ihre Immobilie: ${propertyValue} m²,
    Position: ${propertyValue < distribution.mean ? 'Unter' : 'Über'} dem Durchschnitt.
    ${Math.abs(propertyValue - distribution.mean)} m² vom Mittelwert entfernt.
  `

  return (
    <AccessibleChart
      data={distribution.data}
      title="Community Wohnflächen-Vergleich"
      description={description}
    />
  )
}
```

### Data Table Accessibility

```typescript
// Accessible Data Table
const AccessibleDataTable = ({ data, columns }) => {
  const tableId = useId()

  return (
    <div className="table-container">
      <table
        id={tableId}
        role="table"
        aria-label="Immobilien Vergleichstabelle"
        aria-describedby={`${tableId}-summary`}
      >
        <caption id={`${tableId}-summary`}>
          Vergleich von {data.length} Immobilien nach {columns.length} Kriterien
        </caption>

        <thead>
          <tr role="row">
            {columns.map(column => (
              <th
                key={column.key}
                scope="col"
                role="columnheader"
                aria-sort={column.sortable ? 'none' : undefined}
              >
                {column.label}
                {column.sortable && <span className="sr-only">, sortierbar</span>}
              </th>
            ))}
          </tr>
        </thead>

        <tbody>
          {data.map((row, rowIndex) => (
            <tr key={row.id} role="row">
              {columns.map(column => (
                <td
                  key={column.key}
                  role="gridcell"
                  headers={`${tableId}-${column.key}`}
                >
                  {column.render ? column.render(row[column.key], row) : row[column.key]}
                </td>
              ))}
            </tr>
          ))}
        </tbody>
      </table>

      {/* Pagination mit Screen Reader Support */}
      <nav aria-label="Tabellennavigation">
        <ul className="pagination">
          <li>
            <button
              aria-label="Vorherige Seite"
              disabled={currentPage === 1}
            >
              ← Zurück
            </button>
          </li>
          <li aria-current="page">
            Seite {currentPage} von {totalPages}
          </li>
          <li>
            <button
              aria-label="Nächste Seite"
              disabled={currentPage === totalPages}
            >
              Weiter →
            </button>
          </li>
        </ul>
      </nav>
    </div>
  )
}
```

---

## Formulare & Interaktionen

### Form Accessibility Best Practices

```typescript
// Accessible Form with Validation
const AccessibleForm = () => {
  const [errors, setErrors] = useState({})
  const [touched, setTouched] = useState({})

  const handleSubmit = async (event) => {
    event.preventDefault()

    // Announce form submission to screen readers
    announceToScreenReader('Formular wird übermittelt')

    try {
      await submitForm(formData)
      announceToScreenReader('Formular erfolgreich übermittelt')
    } catch (error) {
      announceToScreenReader('Fehler beim Übermitteln des Formulars')
      setErrors(error.validationErrors)
    }
  }

  return (
    <form onSubmit={handleSubmit} noValidate aria-labelledby="form-title">
      <h2 id="form-title">Immobilie hinzufügen</h2>

      <FormField
        id="title"
        label="Titel"
        type="text"
        required
        error={errors.title}
        touched={touched.title}
        onBlur={() => setTouched(prev => ({ ...prev, title: true }))}
        aria-describedby={errors.title ? 'title-error' : 'title-help'}
        helperText="z.B. '3-Zimmer-Wohnung München'"
      />

      <FormField
        id="area"
        label="Wohnfläche"
        type="number"
        unit="m²"
        required
        error={errors.area}
        touched={touched.area}
        onBlur={() => setTouched(prev => ({ ...prev, area: true }))}
        aria-describedby={errors.area ? 'area-error' : 'area-help'}
        helperText="In Quadratmetern"
      />

      <button
        type="submit"
        aria-describedby="submit-help"
        disabled={isSubmitting}
      >
        {isSubmitting ? 'Wird gespeichert...' : 'Speichern'}
      </button>
      <div id="submit-help" className="sr-only">
        Speichert die Immobilie und zeigt eine Erfolgsmeldung an
      </div>
    </form>
  )
}

// Form Field Component
const FormField = ({
  id,
  label,
  type = 'text',
  required,
  error,
  touched,
  helperText,
  unit,
  ...props
}) => (
  <div className="form-field">
    <label htmlFor={id}>
      {label}
      {required && <span className="required" aria-label="erforderlich">*</span>}
      {unit && <span className="sr-only"> in {unit}</span>}
    </label>

    <div className="input-wrapper">
      <input
        id={id}
        type={type}
        required={required}
        aria-invalid={error && touched ? 'true' : 'false'}
        aria-describedby={
          error && touched ? `${id}-error` :
          helperText ? `${id}-help` : undefined
        }
        {...props}
      />
      {unit && <span className="unit" aria-hidden="true">{unit}</span>}
    </div>

    {helperText && !error && (
      <div id={`${id}-help`} className="helper-text">
        {helperText}
      </div>
    )}

    {error && touched && (
      <div
        id={`${id}-error`}
        className="error-message"
        role="alert"
        aria-live="polite"
      >
        {error}
      </div>
    )}
  </div>
)
```

### Modal & Dialog Accessibility

```typescript
// Accessible Modal
const AccessibleModal = ({ isOpen, onClose, title, children }) => {
  const modalRef = useRef()
  const [focusableElements, setFocusableElements] = useState([])

  useEffect(() => {
    if (isOpen) {
      // Focus trap implementation
      const focusable = modalRef.current.querySelectorAll(
        'button, [href], input, select, textarea, [tabindex]:not([tabindex="-1"])'
      )
      setFocusableElements(focusable)

      // Focus first element
      if (focusable.length > 0) {
        focusable[0].focus()
      }

      // Prevent body scroll
      document.body.style.overflow = 'hidden'
    } else {
      document.body.style.overflow = 'unset'
    }

    return () => {
      document.body.style.overflow = 'unset'
    }
  }, [isOpen])

  const handleKeyDown = (event) => {
    if (event.key === 'Escape') {
      onClose()
    }

    if (event.key === 'Tab') {
      // Tab trapping
      const firstElement = focusableElements[0]
      const lastElement = focusableElements[focusableElements.length - 1]

      if (event.shiftKey) {
        if (document.activeElement === firstElement) {
          event.preventDefault()
          lastElement.focus()
        }
      } else {
        if (document.activeElement === lastElement) {
          event.preventDefault()
          firstElement.focus()
        }
      }
    }
  }

  if (!isOpen) return null

  return (
    <div
      className="modal-overlay"
      role="dialog"
      aria-modal="true"
      aria-labelledby="modal-title"
      aria-describedby="modal-description"
      onKeyDown={handleKeyDown}
    >
      <div className="modal-content" ref={modalRef}>
        <header>
          <h2 id="modal-title">{title}</h2>
          <button
            onClick={onClose}
            aria-label="Modal schließen"
            className="close-button"
          >
            ×
          </button>
        </header>

        <div id="modal-description" className="sr-only">
          {description}
        </div>

        <main>
          {children}
        </main>
      </div>
    </div>
  )
}
```

---

## Testing & Quality Assurance

### Accessibility Testing Checklist

```typescript
// Automated Accessibility Tests
describe('Accessibility Tests', () => {
  it('should have proper heading hierarchy', () => {
    const headings = screen.getAllByRole('heading')
    const levels = headings.map(h => parseInt(h.tagName.charAt(1)))

    // Check for proper hierarchy (no skipping levels)
    for (let i = 1; i < levels.length; i++) {
      expect(levels[i]).toBeLessThanOrEqual(levels[i - 1] + 1)
    }
  })

  it('should have alt text for all images', () => {
    const images = screen.getAllByRole('img')
    images.forEach(img => {
      expect(img).toHaveAttribute('alt')
      expect(img.getAttribute('alt')).not.toBe('')
    })
  })

  it('should have proper form labels', () => {
    const inputs = screen.getAllByRole('textbox')
    inputs.forEach(input => {
      const label = screen.getByLabelText(input.name || input.id)
      expect(label).toBeInTheDocument()
    })
  })

  it('should be keyboard navigable', () => {
    // Test tab order and keyboard interactions
    const focusableElements = screen.getAllByRole('button', 'link', 'textbox')
    expect(focusableElements.length).toBeGreaterThan(0)
  })

  it('should have sufficient color contrast', () => {
    // This would typically be tested with a visual regression tool
    // or accessibility testing service like axe-core
    const { container } = render(<Component />)
    const results = axe(container)
    expect(results.violations).toHaveLength(0)
  })
})
```

### Manual Testing Checklist

#### Keyboard Navigation
- [ ] Alle interaktiven Elemente sind per Tab erreichbar
- [ ] Tab-Reihenfolge ist logisch
- [ ] Keine Tastatur-Fallen vorhanden
- [ ] Enter/Space funktionieren für Buttons
- [ ] Escape schließt Modals/Dropdowns

#### Screen Reader
- [ ] Alle wichtigen Inhalte werden vorgelesen
- [ ] Form Labels sind korrekt assoziiert
- [ ] Live Regions funktionieren für Status-Updates
- [ ] ARIA Labels sind aussagekräftig
- [ ] Landmark Roles sind korrekt gesetzt

#### Visual Accessibility
- [ ] Kontrast-Verhältnis ≥ 4.5:1
- [ ] Fokus-Indikatoren sind sichtbar
- [ ] Text ist ohne Farbe verständlich
- [ ] Inhalte skalieren bis 200%
- [ ] Keine blinkenden Inhalte > 3 Hz

---

## Tools & Resources

### Development Tools
- **axe-core**: Automated accessibility testing
- **WAVE**: Web accessibility evaluation tool
- **Lighthouse**: Performance and accessibility audits
- **Color Contrast Analyzer**: Contrast ratio checker
- **NVDA**: Screen reader für Windows testing

### Browser Extensions
- **WAVE Toolbar**: Accessibility evaluation
- **axe DevTools**: Real-time accessibility testing
- **Accessibility Insights**: Microsoft accessibility tools
- **Colorblindly**: Color blindness simulation

### Online Resources
- **WCAG Guidelines**: https://www.w3.org/TR/WCAG21/
- **A11Y Project**: https://www.a11yproject.com/
- **Inclusive Design Principles**: https://inclusivedesignprinciples.org/
- **WebAIM**: https://webaim.org/

---

## Implementation Roadmap

### Phase 1: Foundation (Q1 2024)
- [ ] ARIA Labels für alle Komponenten
- [ ] Semantische HTML-Struktur
- [ ] Keyboard Navigation Basics
- [ ] Color Contrast Audit

### Phase 2: Enhancement (Q2 2024)
- [ ] Screen Reader Optimierung
- [ ] Focus Management
- [ ] Form Accessibility
- [ ] Chart Accessibility

### Phase 3: Advanced (Q3-Q4 2024)
- [ ] Complex Interactions (Modals, Dropdowns)
- [ ] Dynamic Content
- [ ] Error Handling
- [ ] User Testing mit assistive Technologien

### Phase 4: Continuous Improvement
- [ ] Accessibility Audits
- [ ] User Feedback Integration
- [ ] Technology Updates
- [ ] Training & Awareness

---

## Success Metrics

### Quantitative Metrics
- **Lighthouse Accessibility Score:** ≥ 95
- **Manual Testing Coverage:** 100% aller User Flows
- **Color Contrast Compliance:** 100% aller Text-Elemente
- **Keyboard Navigation:** 100% aller Interaktionen

### Qualitative Metrics
- **Screen Reader Compatibility:** Positive Tests mit NVDA/JAWS
- **User Feedback:** Accessibility als Strength in Reviews
- **Support Tickets:** < 5% accessibility-bezogene Issues
- **Legal Compliance:** WCAG 2.1 AA Zertifizierung

---

## Team Responsibilities

### Developers
- Implement accessibility features während der Entwicklung
- Code Reviews mit Accessibility Checklist
- Unit Tests für Accessibility Features
- Documentation von Accessibility Patterns

### Designers
- Farbkontrast-Prüfung für alle Designs
- Fokus-States in allen Mockups
- Alternative Text für alle visuellen Elemente
- Touch Target Size Guidelines (44px minimum)

### Product Managers
- Accessibility Requirements in User Stories
- Priorisierung von Accessibility Features
- User Research mit Menschen mit Behinderungen
- Accessibility Budget in Projektplanung

### QA Testers
- Accessibility Testing in jedem Release
- Cross-Device und Cross-Assistive-Tech Testing
- Regression Testing für Accessibility Features
- Bug Reports mit Accessibility Context

---

## Legal & Compliance

### WCAG 2.1 AA Requirements
FlatRace verpflichtet sich zur Einhaltung der Web Content Accessibility Guidelines 2.1 Level AA. Dies umfasst:

- **Perceivable:** Inhalte müssen für alle Sinne zugänglich sein
- **Operable:** Benutzeroberflächen müssen bedienbar sein
- **Understandable:** Inhalte müssen verständlich sein
- **Robust:** Inhalte müssen zuverlässig funktionieren

### EU Accessibility Act
Als digitale Plattform unterliegt FlatRace dem EU Accessibility Act. Dies beinhaltet:
- Barrierefreie Nutzung für Menschen mit Behinderungen
- Konforme Dokumentation und Support
- Regelmäßige Accessibility Audits
- Transparente Berichterstattung über Compliance

### Monitoring & Reporting
- **Quarterly Audits:** Externe Accessibility Reviews
- **Annual Compliance Report:** Öffentliche Berichterstattung
- **Issue Tracking:** Dediziertes Accessibility-Backlog
- **Training:** Jährliche Accessibility-Schulungen für alle Teammitglieder

---

*Dieses Dokument wird kontinuierlich aktualisiert basierend auf neuen WCAG-Richtlinien, Technologien und Nutzer-Feedback.*



