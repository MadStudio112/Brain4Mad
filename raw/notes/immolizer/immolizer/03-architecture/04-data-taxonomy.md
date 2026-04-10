

## Promopt

```yaml
task: Immobilien-Merkmale in EU-Portalen
goal: Erstellen einer standardisierten Attributliste für Immobilien ("Typenschein")
output_format: JSON

instructions:
  - Durchsuche die größten Immobilienplattformen in der EU (z. B. Immobilienscout24, Immowelt, Idealista, SeLoger, Rightmove, Zoopla, Immoweb, Funda, Otodom).
  - Sammle systematisch alle Merkmale/Kategorien, die eine Immobilie in Inseraten haben kann.
  - Normalisiere unterschiedliche Begriffe (z. B. "Living Area" = "Wohnfläche").
  - Strukturiere die Merkmale nach Clustern:
      * Basisdaten (ID, Typ, Status: Kauf/Miete, Preis)
      * Lage & Umgebung (Adresse, Region, Umgebungsinfos, Koordinaten)
      * Objektbeschreibung (Baujahr, Fläche, Anzahl Zimmer, Grundfläche, Stockwerke)
      * Ausstattung (Küche, Balkon, Heizung, Energieklasse, Smart-Home)
      * Kosten (Kaufpreis, Miete, Nebenkosten, Provision, Steuern)
      * Rechtliches (Eigentumsform, Energieausweis, Bauordnung, Genehmigungen)
      * Community/Markt (Vergleichspreis, Normalverteilung, Bewertungen)
  - Führe die Attribute zu einer priorisierten Liste zusammen: 
      * "hoch" = fast auf allen Plattformen vorhanden, entscheidend für Vergleichbarkeit
      * "mittel" = häufig, aber nicht kritisch
      * "niedrig" = nur bei Spezialfällen (Luxus, Gewerbe, Ferienwohnungen)
  - Formatiere das Ergebnis als JSON mit folgendem Schema:
    {
      "cluster": "Basisdaten",
      "attributes": [
        { "name": "Wohnfläche", "aliases": ["Living area", "Surface habitable"], "priority": "hoch" },
        { "name": "Zimmeranzahl", "aliases": ["Rooms", "Pièces"], "priority": "hoch" },
        ...
      ]
    }
  - Ziel: Definition eines europäischen "Immobilien-Typenscheins" für eine einseitige, visuelle Zusammenfassung mit Community-Vergleich (Normalverteilung).
```

## objekt_anlegen
```json

{
  "category": "objekt_anlegen",
  "description": "Grundlegende Objektdaten für neue Immobilie",
  "priority": 1,
  "fields": [
    {
      "key": "objektname",
      "label": "Objektname",
      "type": "text",
      "required": true,
      "placeholder": "z.B. Mein Projekt",
      "validation": {
        "minLength": 2,
        "maxLength": 100
      },
      "ui": {
        "component": "input",
        "icon": "info",
        "editable": true
      }
    },
    {
      "key": "besitzverhaeltnis",
      "label": "Besitzverhältnis",
      "type": "select",
      "required": true,
      "options": [
        {
          "value": "eigentum",
          "label": "Eigentum",
          "icon": "house-key"
        },
        {
          "value": "miete",
          "label": "Miete", 
          "icon": "house-rent"
        }
      ],
      "ui": {
        "component": "card-select",
        "layout": "horizontal"
      }
    },
    {
      "key": "objektart",
      "label": "Objektart",
      "type": "select",
      "required": true,
      "options": [
        {
          "value": "grundstueck",
          "label": "Grundstück",
          "icon": "dash",
          "price_per_m2": 365
        },
        {
          "value": "haus",
          "label": "Haus",
          "icon": "house",
          "price_per_m2": 2737
        },
        {
          "value": "wohnung",
          "label": "Wohnung",
          "icon": "apartment",
          "price_per_m2": 2299
        }
      ],
      "ui": {
        "component": "card-select",
        "layout": "horizontal",
        "show_price": true
      }
    },
    {
      "key": "lage",
      "label": "Lage",
      "type": "location_group",
      "required": true,
      "fields": [
        {
          "key": "bundesland",
          "label": "Bundesland",
          "type": "select",
          "options": ["Burgenland", "Wien", "Niederösterreich"]
        },
        {
          "key": "bezirk",
          "label": "Bezirk",
          "type": "select",
          "options": ["Eisenstadt (Stadt)", "Eisenstadt-Umgebung"]
        },
        {
          "key": "gemeinde",
          "label": "Gemeinde",
          "type": "select",
          "options": ["Zentrum", "Kleinhöflein", "St. Georgen"]
        }
      ],
      "ui": {
        "component": "location-cascade",
        "layout": "vertical"
      }
    },
    {
      "key": "plz",
      "label": "PLZ",
      "type": "text",
      "required": true,
      "default": "7000",
      "validation": {
        "pattern": "^[0-9]{4,5}$"
      },
      "ui": {
        "component": "input",
        "type": "number"
      }
    },
    {
      "key": "grundstuecksflaeche",
      "label": "Grundstücksfläche",
      "type": "number",
      "required": false,
      "unit": "m²",
      "validation": {
        "min": 0,
        "max": 100000
      },
      "ui": {
        "component": "input-with-unit",
        "icon": "document"
      }
    },
    {
      "key": "wohnflaeche",
      "label": "Wohnfläche",
      "type": "number",
      "required": true,
      "unit": "m²",
      "validation": {
        "min": 1,
        "max": 10000
      },
      "ui": {
        "component": "input-with-unit",
        "icon": "document"
      }
    },
    {
      "key": "preis",
      "label": "Preis",
      "type": "currency",
      "required": true,
      "unit": "EUR",
      "validation": {
        "min": 0,
        "max": 10000000
      },
      "ui": {
        "component": "price-input",
        "show_per_m2": true,
        "icon": "document"
      }
    }
  ],
  "ui": {
    "layout": "form",
    "navigation": {
      "back": true,
      "info": true,
      "save": true
    }
  }
}

```



```json
{
  "category": "betriebskosten",
  "priority": 1,
  "description": "Laufende Betriebskosten der Immobilie",
  "fields": [
    {
      "key": "heizkosten",
      "label": "Heizkosten",
      "type": "currency",
      "frequency": "monthly",
      "required": true,
      "validation": {
        "min": 0,
        "max": 10000,
        "pattern": "^\\d+(\\.\\d{2})?$"
      },
      "i18n": {
        "de": "Heizkosten",
        "en": "Heating Costs"
      }
    },
    {
      "key": "strom",
      "label": "Strom",
      "type": "currency",
      "unit": "EUR",
      "frequency": "monthly",
      "required": true,
      "validation": {
        "min": 0,
        "max": 5000
      },
      "i18n": {
        "de": "Strom",
        "en": "Electricity"
      }
    }
  ],
  "relationships": [
    {
      "type": "depends_on",
      "category": "energiebedarf",
      "description": "Heizkosten hängen vom Energiebedarf ab"
    }
  ],
  "community_analysis": {
    "enabled": true,
    "metrics": ["mean", "median", "std_dev", "percentiles"],
    "grouping": ["region", "property_type", "size_category"]
  }
}
```

## onboarding

{
  "form_property": {
    "name": { "label": "property.name", "type": "text", "default": "" },
    "ownership": {
      "label": "property.ownership",
      "type": "select",
      "options": ["property.ownership.ownership", "property.ownership.rent"]
    },
    "type": {
      "label": "property.type",
      "type": "select",
      "options": ["property.type.house", "property.type.apartment"]
    },
    "location": {
      "label": "property.location",
      "type": "location",
      "levels": ["state", "district", "region"]
    },
    "land_area": { "label": "property.land_area", "type": "number", "unit": "m²" },
    "living_area": { "label": "property.living_area", "type": "number", "unit": "m²" },
    "price": { "label": "property.price", "type": "number", "unit": "€" }
  }
}




{
  "property": {
    "name": "Name",
    "ownership": "Besitz",
    "ownership.ownership": "Eigentum",
    "ownership.rent": "Miete",
    "type": "Objektart",
    "type.house": "Haus",
    "type.apartment": "Wohnung",
    "location": "Lage",
    "land_area": "Grundstücksfläche",
    "living_area": "Wohnfläche",
    "price": "Preis"
  }
}
