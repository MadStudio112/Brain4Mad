# Datenmodell – FlatRace

## Übersicht
Das FlatRace-Datenmodell basiert auf dem Konzept des "Typenscheins" – einer standardisierten, einseitigen Immobilienübersicht mit Community-Vergleich. Das Modell ist für Supabase (PostgreSQL) optimiert und folgt dem Owner-Pattern für Datenschutz.

## Kern-Entities

### 1. Users (Supabase Auth)
**Basis:** Supabase Auth System
- `id` (UUID, Primary Key)
- `email` (VARCHAR, Unique)
- `created_at` (TIMESTAMP)
- `updated_at` (TIMESTAMP)
- **Metadaten:** `full_name`, `phone`, `company` (optional)

**Beziehungen:**
- 1:N zu `properties` (ein Nutzer kann mehrere Objekte haben)
- 1:N zu `exports` (Export-Historie)
- 1:N zu `ratings` (Bewertungen abgeben)

### 2. Properties (Immobilien)
**Haupttabelle für alle Immobiliendaten**
- `id` (UUID, Primary Key)
- `user_id` (UUID, Foreign Key zu users.id)
- `title` (VARCHAR, Objektbezeichnung)
- `created_at` (TIMESTAMP)
- `updated_at` (TIMESTAMP)

**Grunddaten:**
- `location_geo` (GEOGRAPHY, PostGIS für Geocoding)
- `location_address` (JSONB: street, city, zip, country)
- `area_m2` (NUMERIC, Wohnfläche)
- `rooms` (NUMERIC, Zimmeranzahl)
- `year_built` (INTEGER, Baujahr)

**Ausstattung & Details:**
- `energy_type` (VARCHAR, Heizungsart)
- `energy_class` (VARCHAR, Energieeffizienzklasse)
- `amenities` (JSONB, Ausstattungsmerkmale)
- `condition` (VARCHAR, Zustand: excellent/good/fair/poor)

**Kosten & Kennzahlen:**
- `purchase_price` (NUMERIC, Kaufpreis)
- `rent_monthly` (NUMERIC, Miete)
- `operating_costs` (JSONB, Betriebskosten-Details)

**Status & Metadaten:**
- `status` (VARCHAR: draft/published/archived)
- `visibility` (VARCHAR: private/public/community)
- `tags` (TEXT[], Suchbegriffe)

### 3. Operating Costs (Betriebskosten)
**Detaillierte Kostenaufschlüsselung**
- `id` (UUID, Primary Key)
- `property_id` (UUID, Foreign Key zu properties.id)
- `period` (VARCHAR: monthly/quarterly/yearly)
- `created_at` (TIMESTAMP)

**Kostenkategorien (JSONB):**
```json
{
  "heating": {"amount": 150, "unit": "€/month"},
  "electricity": {"amount": 80, "unit": "€/month"},
  "water": {"amount": 45, "unit": "€/month"},
  "garbage": {"amount": 25, "unit": "€/month"},
  "maintenance": {"amount": 100, "unit": "€/month"},
  "insurance": {"amount": 60, "unit": "€/month"},
  "total": {"amount": 460, "unit": "€/month"}
}
```

### 4. Community Stats (Aggregierte Vergleichsdaten)
**Anonymisierte Community-Daten für Normalverteilung**
- `id` (UUID, Primary Key)
- `region_key` (VARCHAR, PLZ oder Stadtteil)
- `metric_key` (VARCHAR, z.B. "area_m2", "rent_monthly")
- `sample_size` (INTEGER, Anzahl Datensätze)
- `updated_at` (TIMESTAMP)

**Verteilungsdaten (JSONB):**
```json
{
  "mean": 85.5,
  "median": 82.0,
  "std_dev": 25.3,
  "min": 25.0,
  "max": 180.0,
  "quartiles": [65.0, 82.0, 105.0],
  "distribution_type": "normal"
}
```

### 5. Exports (Generierte Dokumente)
**Export-Historie und Status**
- `id` (UUID, Primary Key)
- `property_id` (UUID, Foreign Key zu properties.id)
- `user_id` (UUID, Foreign Key zu users.id)
- `type` (VARCHAR: "typenschein", "expose", "sas360")
- `format` (VARCHAR: "pdf", "html")
- `status` (VARCHAR: "pending", "processing", "completed", "failed")
- `file_url` (VARCHAR, Download-Link)
- `metadata` (JSONB, Export-Parameter)
- `created_at` (TIMESTAMP)
- `completed_at` (TIMESTAMP)

### 6. Ratings (Bewertungen, v2+)
**Dienstleister-Bewertungen**
- `id` (UUID, Primary Key)
- `user_id` (UUID, Foreign Key zu users.id)
- `subject_type` (VARCHAR: "service_provider", "property")
- `subject_id` (UUID, Referenz-ID)
- `score` (INTEGER, 1-5 Sterne)
- `comment` (TEXT, Bewertungstext)
- `category` (VARCHAR: "quality", "reliability", "communication")
- `created_at` (TIMESTAMP)

## Beziehungen & Constraints

### Hierarchische Struktur
```
Users (1) ←→ (N) Properties (1) ←→ (N) Operating Costs
    ↓                              ↓
    ↓                              ↓
(N) Exports                    (N) Community Stats (via Aggregation)
    ↓
(N) Ratings
```

### Referentielle Integrität
- `properties.user_id` → `users.id` (CASCADE DELETE)
- `operating_costs.property_id` → `properties.id` (CASCADE DELETE)
- `exports.property_id` → `properties.id` (CASCADE DELETE)
- `exports.user_id` → `users.id` (CASCADE DELETE)
- `ratings.user_id` → `users.id` (CASCADE DELETE)

### RLS (Row Level Security) Policies
- **Users:** Nur eigene Daten lesen/bearbeiten
- **Properties:** Owner kann CRUD, Community nur anonymisierte Aggregats
- **Operating Costs:** Owner kann CRUD
- **Exports:** Owner kann lesen, erstellen
- **Community Stats:** Alle können lesen (öffentlich)
- **Ratings:** Alle können lesen, Owner kann CRUD

## Datenflüsse & Schnittstellen

### 1. Typenschein-Generierung
```
Property Data → Validation → Typenschein Template → Export Engine → PDF/HTML
```

### 2. Community-Vergleich
```
Property Metrics → Region Lookup → Community Stats → Normal Distribution → Chart Data
```

### 3. Betriebskosten-Analyse
```
Operating Costs → Aggregation → Community Comparison → Deviation Calculation → Report
```

### 4. Export-Pipeline
```
Export Request → Queue → Processing → Storage → Notification → Download
```

## Performance-Optimierungen

### Indizes
- `properties(user_id, status)` - Schnelle Nutzer-Objekte
- `properties(location_geo)` - Geospatial-Suchen
- `community_stats(region_key, metric_key)` - Schnelle Community-Lookups
- `exports(user_id, created_at)` - Export-Historie

### Materialized Views
- `community_stats_aggregated` - Vorberechnete Verteilungen
- `property_summary` - Häufig abgefragte Objektdaten

### Caching-Strategie
- Community-Stats: 24h TTL
- Property-Details: 1h TTL (bei Änderungen invalidieren)
- Export-Status: Real-time (WebSocket)

## Datenschutz & DSGVO

### Anonymisierung
- Community-Stats: Mindestens n=10 für Aggregation
- Keine Rückschlüsse auf Einzelobjekte möglich
- Regionen mit zu wenig Daten werden zusammengefasst

### Datenlöschung
- User löschen → Alle zugehörigen Daten löschen
- Property löschen → Operating Costs, Exports löschen
- Community-Stats bleiben (anonymisiert)

### Audit-Trail
- Alle Änderungen an Properties werden protokolliert
- Export-Historie für Compliance
- User-Aktivitäten für Support

## Erweiterbarkeit (v2+)

### Neue Entity-Typen
- `portfolios` - Objekt-Sammlungen
- `comparisons` - Objekt-Vergleiche
- `templates` - Export-Vorlagen

### Erweiterte Metriken
- `market_trends` - Zeitreihen-Daten
- `neighborhood_stats` - Umgebungsdaten
- `investment_metrics` - ROI-Berechnungen

### Integration
- `external_sources` - Daten von Partnern
- `webhooks` - Real-time Updates
- `api_keys` - Drittanbieter-Zugriff

## Implementierungsnotizen

### Supabase-spezifisch
- RLS-Policies für alle Tabellen
- Edge Functions für Export-Processing
- Real-time Subscriptions für Export-Status
- Storage Buckets für PDF-Dateien

### Migration-Strategie
- Schema-Versionierung über `schema_version` Tabelle
- Backward-kompatible Änderungen
- Daten-Migration-Skripte für Breaking Changes

### Monitoring
- Query-Performance über pg_stat_statements
- RLS-Policy-Hits über Custom Metrics
- Export-Queue-Länge über Prometheus
