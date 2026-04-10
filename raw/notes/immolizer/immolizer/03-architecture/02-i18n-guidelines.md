# i18n (Internationalisierung)

## 🎯 **Übersicht**

Die Applikation unterstützt mehrsprachige Inhalte mit automatischer Browser-Spracherkennung und Feature-spezifischen Übersetzungen.


🎯 Zusammenfassung
Die i18n.md wird in docs/00-meta/03-i18n.md erstellt und enthält:
Browser-Spracherkennung - Automatische Erkennung basierend auf localStorage, navigator und htmlTag
Feature-spezifische i18n - Jede Komponente hat ihren eigenen i18n/-Ordner
Globale Strings - Zentrale src/locales/ für übergreifende Texte
Entwicklungs-Workflow - Schritt-für-Schritt Anleitung für neue Features
Best Practices - Konsistente Struktur und Verwendung


---

## 📁 **Ordnerstruktur**

### **Globale Übersetzungen**

src/
├── locales/ # Globale Common-Strings
│ ├── de.json
│ └── en.json
└── i18n/
└── config.ts # i18n-Konfiguration


### **Feature-spezifische Übersetzungen**

src/components/
├── Landing/
│ └── i18n/ # Landing-spezifische Strings
│ ├── de.json
│ └── en.json
├── Auth/
│ └── i18n/ # Auth-spezifische Strings
│ ├── de.json
│ └── en.json
└── Rating/
└── i18n/ # Rating-spezifische Strings
│ ├── de.json
│ └── en.json


---

## 🔧 **Technische Implementierung**

### **1. Browser-Spracherkennung**

```typescript
// src/i18n/config.ts
import LanguageDetector from 'i18next-browser-languagedetector'

i18n
  .use(LanguageDetector)
  .init({
    detection: {
      order: ['localStorage', 'navigator', 'htmlTag'],
      lookupLocalStorage: 'teamchef-language',
      caches: ['localStorage']
    }
  })
```

**Erkennungsreihenfolge:**
1. **localStorage** - Benutzer-gespeicherte Präferenz
2. **navigator** - Browser-Spracheinstellung
3. **htmlTag** - HTML lang-Attribut

### **2. Feature-spezifische i18n**

```typescript
// src/i18n/config.ts
import commonDe from '../locales/de.json'
import landingDe from '../components/Landing/i18n/de.json'

i18n.init({
  resources: {
    de: { 
      common: commonDe.common,
      landing: landingDe
    },
    en: { 
      common: commonEn.common,
      landing: landingEn
    }
  }
})
```

---

## 📋 **Richtlinien & Best Practices**

### **1. Ordnerstruktur-Regeln**

✅ **Richtig:**
- Feature-spezifische Strings in `component/i18n/`
- Globale Strings in `src/locales/`
- Konsistente Dateinamen (`de.json`, `en.json`)

❌ **Falsch:**
- Strings direkt in Komponenten
- Vermischung von globalen und lokalen Strings

### **2. JSON-Struktur**

```json
// src/locales/de.json (Globale Strings)
{
  "common": {
    "buttons": {
      "save": "Speichern",
      "cancel": "Abbrechen",
      "submit": "Absenden"
    },
    "navigation": {
      "home": "Startseite",
      "matches": "Spiele",
      "profile": "Profil"
    }
  }
}
```

```json
// src/components/Landing/i18n/de.json (Feature-spezifisch)
{
  "hero": {
    "brand": "TEAMCHEF",
    "subtitle": "Objektive Fußballbewertung",
    "description": "Bewerte Teams und Spieler gemeinsam mit anderen Fans",
    "getStarted": "Jetzt starten",
    "login": "Anmelden"
  },
  "features": {
    "title": "Warum TEAMCHEF?",
    "objective": {
      "title": "Objektive Bewertung",
      "description": "5 klare Kriterien: Kraft, Ausdauer, Siegeswille, Teamwork und Intelligenz"
    }
  }
}