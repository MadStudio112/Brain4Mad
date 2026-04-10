# Idee 

**Projektname:** FlatRace 
**Version:** MVP 1.0  
**Stand:** 2025-08-16  


## 🎯 Ziel des Projekts

FLATRACE ist ein intelligentes Bewertungssystem für Immobilien – vergleichbar mit einem TÜV-Bericht oder medizinischen Blutbild.
Ziel ist es, durch standardisierte Daten und smarte Visualisierung eine objektive Vergleichbarkeit von Immobilien zu schaffen.

--- 

## 🧩 Hauptkomponenten & Features

### 🔧 Technisches Datenblatt („Typenschein“)

    - Standardisiertes PDF/HTML-Datenblatt mit:
    - Größe, Räume, Ausstattung, Baujahr, Bodenbeläge, Heizung etc.
    - Community-Vergleich (Normalverteilung / Benchmarks)
    - visuelle Aufbereitung: Charts, Icons, Farbcodes


### 📊 Dashboard

- Zentrale Analyseplattform für:

    - Vergleich mehrerer Immobilien
    - grafische Auswertung (z. B. Betriebskostenverlauf, M2-Preise, Verbrauch)
    - Community-Daten im Vergleich
    - User-basiertes Feedback (Anonymisierung optional)

### 📝 Exposé Generator

- Automatische Erstellung eines Exposés auf Basis der Daten
- KI-unterstützte Formulierungen (emotionale Sprache, Zielgruppen-Optimierung)
- Export als PDF/Print/Embed

### 💬 Bewertungsplattform für Dienstleister

- Integration von Anwalt, Gutachter, Handwerker etc.
- Bewertungen auf Basis echter Immobilienprojekte
- Sternebewertung + Text + anonymisierte Reports

### 💸 Betriebskosten-Analyse

- Betriebskosten individuell oder pauschal erfassen
- Vergleich mit regionalem Durchschnitt
- Berechnung nach Bewohnerzahl, M2, Heizsystem etc.

---

## 📦 Erweiterungsmodule (später)

- 📈 Baukostenrechner (Sanierung, Umbau, Schätzung)
- 🌍 Mehrsprachigkeit & Länderprofile (i18n)
- 🧠 KI-Hinweise & Plausibilitätscheck
- 📱 Mobile Web-App (PWA)

---

## 🧠 Zielgruppe

- Private Eigentümer & Mieter
- Hausverwaltungen, Investoren
- Gutachter & Sachverständige
- Immobilienplattformen (B2B)

---

## 🗂 Datenstruktur (Basis-Modelle)

- property_core (Objektdaten)
- property_features (Ausstattung)
- property_costs (Betriebskosten)
- property_rating (normierte Kriterien)
- user_profiles
- community_statistics

---

🔄 Workflows

- User füllt das Formular aus (FlatForm)
- System speichert Werte, berechnet Normalverteilung
- Dashboard zeigt Position im Vergleich
- Typenschein & Exposé werden generiert
- Optional: Community-Sharing, Dienstleister bewerten

---

## 🛠 Technologiestack (MVP)

- **Frontend:** React + Tailwind
- **Backend:** Supabase
- **Charting:** Recharts / Normalverteilung / Radar / Bar
- **Dateninput:** Formulare / JSON / Import via API
- **Export:** PDF, HTML, JSON
- **Deployment:** vercel