# API Standards – FlatRace

## Übersicht
Die FlatRace API folgt RESTful Prinzipien und ist für Supabase (PostgreSQL + Edge Functions) optimiert. Alle Endpunkte sind authentifiziert und folgen dem Owner-Pattern für Datenschutz.

## API-Konventionen

### Basis-URL
```
Production: https://api.flatrace.com/v1
Development: https://dev-api.flatrace.com/v1
Local: http://localhost:54321/v1
```

### HTTP-Methoden
- **GET** - Daten abrufen (immer idempotent)
- **POST** - Neue Ressourcen erstellen
- **PUT** - Ressourcen vollständig ersetzen
- **PATCH** - Ressourcen teilweise aktualisieren
- **DELETE** - Ressourcen löschen

### Status Codes
- **200** - Erfolgreich
- **201** - Erstellt
- **204** - Kein Inhalt (bei DELETE)
- **400** - Ungültige Anfrage
- **401** - Nicht authentifiziert
- **403** - Keine Berechtigung
- **404** - Nicht gefunden
- **422** - Validierungsfehler
- **429** - Rate Limit überschritten
- **500** - Server-Fehler

### Authentifizierung
```http
Authorization: Bearer <supabase-jwt-token>
```

### Rate Limiting
- **Authentifiziert:** 1000 Requests/Stunde
- **Community-Endpunkte:** 100 Requests/Stunde
- **Export-Endpunkte:** 50 Requests/Stunde

## Kern-Endpunkte

### 1. Authentication (Supabase Auth)

#### User Profile abrufen
```http
GET /auth/profile
```

**Response:**
```json
{
  "id": "uuid",
  "email": "user@example.com",
  "full_name": "Max Mustermann",
  "phone": "+49 123 456789",
  "company": "Makler GmbH",
  "created_at": "2024-01-15T10:30:00Z",
  "updated_at": "2024-01-15T10:30:00Z"
}
```

#### User Profile aktualisieren
```http
PATCH /auth/profile
Content-Type: application/json

{
  "full_name": "Max Mustermann",
  "phone": "+49 123 456789",
  "company": "Makler GmbH"
}
```

### 2. Properties (Immobilien)

#### Alle Properties eines Users abrufen
```http
GET /properties?status=published&limit=20&offset=0
```

**Query Parameters:**
- `status` - Filter nach Status (draft/published/archived)
- `visibility` - Filter nach Sichtbarkeit (private/public/community)
- `limit` - Anzahl Ergebnisse (max 100)
- `offset` - Pagination-Offset
- `sort` - Sortierung (created_at, updated_at, title)

**Response:**
```json
{
  "data": [
    {
      "id": "uuid",
      "title": "3-Zimmer-Wohnung München",
      "location_address": {
        "street": "Musterstraße 123",
        "city": "München",
        "zip": "80331",
        "country": "DE"
      },
      "area_m2": 85.5,
      "rooms": 3,
      "year_built": 1995,
      "energy_class": "B",
      "status": "published",
      "created_at": "2024-01-15T10:30:00Z",
      "updated_at": "2024-01-15T10:30:00Z"
    }
  ],
  "pagination": {
    "total": 15,
    "limit": 20,
    "offset": 0,
    "has_more": false
  }
}
```

#### Einzelnes Property abrufen
```http
GET /properties/{property_id}
```

#### Property erstellen
```http
POST /properties
Content-Type: application/json

{
  "title": "Neue Immobilie",
  "location_address": {
    "street": "Beispielstraße 456",
    "city": "Berlin",
    "zip": "10115",
    "country": "DE"
  },
  "area_m2": 120.0,
  "rooms": 4,
  "year_built": 2000,
  "energy_type": "gas",
  "energy_class": "A",
  "amenities": ["balcony", "elevator", "parking"],
  "condition": "good",
  "visibility": "private"
}
```

#### Property aktualisieren
```http
PATCH /properties/{property_id}
Content-Type: application/json

{
  "title": "Aktualisierter Titel",
  "area_m2": 125.0
}
```

#### Property löschen
```http
DELETE /properties/{property_id}
```

### 3. Operating Costs (Betriebskosten)

#### Betriebskosten für Property abrufen
```http
GET /properties/{property_id}/operating-costs
```

**Response:**
```json
{
  "data": {
    "id": "uuid",
    "period": "monthly",
    "costs": {
      "heating": {"amount": 150, "unit": "€/month"},
      "electricity": {"amount": 80, "unit": "€/month"},
      "water": {"amount": 45, "unit": "€/month"},
      "garbage": {"amount": 25, "unit": "€/month"},
      "maintenance": {"amount": 100, "unit": "€/month"},
      "insurance": {"amount": 60, "unit": "€/month"},
      "total": {"amount": 460, "unit": "€/month"}
    },
    "created_at": "2024-01-15T10:30:00Z"
  }
}
```

#### Betriebskosten aktualisieren
```http
PUT /properties/{property_id}/operating-costs
Content-Type: application/json

{
  "period": "monthly",
  "costs": {
    "heating": {"amount": 160, "unit": "€/month"},
    "electricity": {"amount": 85, "unit": "€/month"},
    "water": {"amount": 50, "unit": "€/month"},
    "garbage": {"amount": 30, "unit": "€/month"},
    "maintenance": {"amount": 110, "unit": "€/month"},
    "insurance": {"amount": 65, "unit": "€/month"},
    "total": {"amount": 500, "unit": "€/month"}
  }
}
```

### 4. Community Stats (Vergleichsdaten)

#### Community-Vergleich für Metrik abrufen
```http
GET /community/stats?region_key=80331&metric_key=area_m2&property_value=85.5
```

**Query Parameters:**
- `region_key` - PLZ oder Stadtteil
- `metric_key` - Metrik (area_m2, rent_monthly, rooms, etc.)
- `property_value` - Eigener Wert für Positionierung

**Response:**
```json
{
  "data": {
    "region_key": "80331",
    "metric_key": "area_m2",
    "sample_size": 156,
    "distribution": {
      "mean": 87.3,
      "median": 85.0,
      "std_dev": 28.7,
      "min": 25.0,
      "max": 180.0,
      "quartiles": [65.0, 85.0, 110.0]
    },
    "property_position": {
      "value": 85.5,
      "z_score": -0.06,
      "percentile": 48.2,
      "deviation_from_mean": -1.8,
      "deviation_percent": -2.1
    },
    "updated_at": "2024-01-15T10:30:00Z"
  }
}
```

#### Verfügbare Metriken abrufen
```http
GET /community/metrics
```

**Response:**
```json
{
  "data": [
    {
      "key": "area_m2",
      "name": "Wohnfläche (m²)",
      "unit": "m²",
      "description": "Gesamte Wohnfläche in Quadratmetern",
      "available_regions": 1247
    },
    {
      "key": "rent_monthly",
      "name": "Monatliche Miete",
      "unit": "€/Monat",
      "description": "Kaltmiete pro Monat",
      "available_regions": 892
    }
  ]
}
```

#### Verfügbare Regionen abrufen
```http
GET /community/regions?metric_key=area_m2&min_sample_size=10
```

**Query Parameters:**
- `metric_key` - Filter nach verfügbarer Metrik
- `min_sample_size` - Mindestanzahl Datensätze

### 5. Exports (Dokumente generieren)

#### Export erstellen
```http
POST /exports
Content-Type: application/json

{
  "property_id": "uuid",
  "type": "typenschein",
  "format": "pdf",
  "options": {
    "include_community": true,
    "language": "de",
    "template": "default"
  }
}
```

**Response:**
```json
{
  "data": {
    "id": "export-uuid",
    "status": "pending",
    "type": "typenschein",
    "format": "pdf",
    "created_at": "2024-01-15T10:30:00Z",
    "estimated_completion": "2024-01-15T10:32:00Z"
  }
}
```

#### Export-Status abrufen
```http
GET /exports/{export_id}
```

**Response:**
```json
{
  "data": {
    "id": "export-uuid",
    "status": "completed",
    "type": "typenschein",
    "format": "pdf",
    "file_url": "https://storage.flatrace.com/exports/export-uuid.pdf",
    "file_size": 245760,
    "created_at": "2024-01-15T10:30:00Z",
    "completed_at": "2024-01-15T10:31:45Z"
  }
}
```

#### Export-Historie abrufen
```http
GET /exports?limit=20&offset=0
```

### 6. Analytics & Tracking

#### Event tracken
```http
POST /analytics/events
Content-Type: application/json

{
  "event_type": "property_viewed",
  "property_id": "uuid",
  "metadata": {
    "source": "dashboard",
    "duration_seconds": 45
  }
}
```

#### User-Aktivitäten abrufen
```http
GET /analytics/activity?days=30
```

## Fehlerbehandlung

### Standard-Fehlerformat
```json
{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Ungültige Eingabedaten",
    "details": {
      "field": "area_m2",
      "issue": "Muss größer als 0 sein"
    },
    "request_id": "req-12345",
    "timestamp": "2024-01-15T10:30:00Z"
    }
}
```

### Häufige Fehlercodes
- **VALIDATION_ERROR** - Eingabedaten ungültig
- **NOT_FOUND** - Ressource nicht gefunden
- **PERMISSION_DENIED** - Keine Berechtigung
- **RATE_LIMIT_EXCEEDED** - Zu viele Anfragen
- **INSUFFICIENT_DATA** - Zu wenig Community-Daten
- **EXPORT_FAILED** - Export fehlgeschlagen

## Webhooks (v2+)

### Export-Status-Updates
```http
POST /webhooks/export-status
Content-Type: application/json

{
  "export_id": "uuid",
  "status": "completed",
  "file_url": "https://storage.flatrace.com/exports/export-uuid.pdf",
  "timestamp": "2024-01-15T10:31:45Z"
}
```

### Community-Stats-Updates
```http
POST /webhooks/community-update
Content-Type: application/json

{
  "region_key": "80331",
  "metric_key": "area_m2",
  "sample_size": 157,
  "timestamp": "2024-01-15T10:30:00Z"
}
```

## SDK & Client Libraries

### TypeScript/JavaScript
```typescript
import { FlatRaceClient } from '@flatrace/client'

const client = new FlatRaceClient({
  apiKey: 'your-api-key',
  baseUrl: 'https://api.flatrace.com/v1'
})

// Property erstellen
const property = await client.properties.create({
  title: 'Neue Immobilie',
  area_m2: 120.0,
  // ... weitere Felder
})

// Community-Vergleich
const stats = await client.community.getStats({
  regionKey: '80331',
  metricKey: 'area_m2',
  propertyValue: 85.5
})
```

### Python
```python
from flatrace import FlatRaceClient

client = FlatRaceClient(
    api_key='your-api-key',
    base_url='https://api.flatrace.com/v1'
)

# Property abrufen
property = client.properties.get('property-uuid')

# Export erstellen
export = client.exports.create(
    property_id='property-uuid',
    type='typenschein',
    format='pdf'
)
```

## Performance & Caching

### Caching-Strategien
- **Community-Stats:** 24h TTL (Redis)
- **Property-Details:** 1h TTL (bei Änderungen invalidieren)
- **Export-Status:** Real-time (WebSocket)
- **User-Profile:** 1h TTL

### Optimierungen
- **Pagination:** Max 100 Items pro Request
- **Selective Fields:** Nur benötigte Felder abrufen
- **Batch-Operations:** Mehrere Objekte in einem Request
- **Compression:** Gzip für alle Responses

## Monitoring & Observability

### Metriken
- Request/Response-Zeiten (p50, p95, p99)
- Fehlerraten nach Endpunkt
- Rate Limit Hits
- Cache Hit/Miss Ratios

### Logging
- Alle API-Requests (strukturiert)
- Fehler mit Stack Traces
- Performance-Metriken
- User-Agent und IP (anonymisiert)

### Alerts
- Fehlerrate > 5%
- Response-Zeit > 2s (p95)
- Rate Limit Überschreitungen
- Export-Fehler > 10%

## Versionierung & Migration

### API-Versionierung
- **URL-basiert:** `/v1/`, `/v2/`
- **Header-basiert:** `Accept: application/vnd.flatrace.v1+json`
- **Backward-kompatibel** für mindestens 6 Monate

### Breaking Changes
- Neue Pflichtfelder nur in neuen Versionen
- Alte Endpunkte bleiben funktional
- Migration-Guide für alle Änderungen
- Deprecation-Warnings 3 Monate vorher

## Sicherheit

### Input Validation
- Alle Eingaben werden validiert
- SQL-Injection-Schutz via Parameterized Queries
- XSS-Schutz via Content-Security-Policy
- Rate Limiting pro User/IP

### Data Privacy
- RLS-Policies für alle Tabellen
- Keine persönlichen Daten in Logs
- Audit-Trail für alle Änderungen
- DSGVO-konforme Datenlöschung

### API Security
- HTTPS-only (TLS 1.3)
- JWT-Token-Validierung
- CORS-Konfiguration
- Security Headers (HSTS, CSP, etc.)
