# Projekt anlegen


## Metadaten

Meta
Zustand
Energieklasse
Parkmöglichkeiten
Lift
Kühlung
Stockwerkslage
Nutzung
Bauweise
Ausstattung



## JSON Struktur

```json

{
    "Meta": {
        "Zustand": {
        "id": "zustand", 
        "description": "Erhaltungszustand des Objekts",
        "values": [
            { "id": "zustand_1", "label": "Neu/Erstbezug", "icon": "icon-new", "description": "Erstmalige Nutzung nach Fertigstellung oder vollständiger Sanierung" },
            { "id": "zustand_2", "label": "Kernsaniert", "icon": "icon-renovated", "description": "Grundlegend modernisiert (Elektrik, Sanitär, Dämmung etc.)" },
            { "id": "zustand_3", "label": "Gut", "icon": "icon-good", "description": "Gepflegter Zustand, keine wesentlichen Mängel" },
            { "id": "zustand_4", "label": "Renovierungsbedürftig", "icon": "icon-repair", "description": "Teilweise Modernisierungsbedarf" },
            { "id": "zustand_5", "label": "Sanierungsbedürftig", "icon": "icon-warning", "description": "Umfangreiche Sanierungen erforderlich"  }
        ]
        },
        "Energieklasse": {
        "id": "energieklasse",
        "description": "Energieeffizienzklasse gemäß EU-Label",
        "values": [
            { "id": "ek_aplus", "label": "A+", "icon": "icon-a-plus", "description": "Sehr geringe Energiekosten" },
            { "id": "ek_a", "label": "A", "icon": "icon-a", "description": "Sehr effizient" },
            { "id": "ek_b", "label": "B", "icon": "icon-b", "description": "Überdurchschnittlich effizient" },
            { "id": "ek_c", "label": "C", "icon": "icon-c", "description": "Durchschnittlicher Energieverbrauch" },
            { "id": "ek_d", "label": "D", "icon": "icon-d", "description": "Leicht erhöhter Energieverbrauch" },
            { "id": "ek_e", "label": "E", "icon": "icon-e", "description": "Hoher Energieverbrauch" },
            { "id": "ek_f", "label": "F", "icon": "icon-f", "description": "Sehr hoher Energieverbrauch" },
            { "id": "ek_g", "label": "G", "icon": "icon-g", "description": "Extrem ineffizient" },
            { "id": "ek_h", "label": "H", "icon": "icon-h", "description": "Keine Energieeffizienzangabe" }
        ]
        }, 

        "Parkmöglichkeiten": {
        "id": "parkmoeglichkeiten",
        "description": "Optionen für das Abstellen von Fahrzeugen",
        "values": [
            { "id": "park_aussen", "label": "Außenstellplatz", "icon": "icon-parking-outdoor", "description": "Stellplatz im Freien" },
            { "id": "park_carport", "label": "Carport", "icon": "icon-carport", "description": "Überdachter Stellplatz" },
            { "id": "park_garage", "label": "Garage", "icon": "icon-garage", "description": "Geschlossene Garage" },
            { "id": "park_tg", "label": "Tiefgarage", "icon": "icon-parking-underground", "description": "Stellplatz in Tiefgarage" }
        ]
        },

        "Lift": {
        "id": "lift",
        "description": "Aufzug im Gebäude",
        "values": [
            { "id": "ja", "label": "Ja", "icon": "icon-lift", "description": "Aufzug vorhanden" },
            { "id": "nein", "label": "Nein", "icon": "icon-no-lift", "description": "Kein Aufzug" }
        ]
        },

        "Kühlung": {
        "id": "kuehlung",
        "description": "Kühlungsmöglichkeiten",
        "values": [
            { "id": "keine", "label": "Keine", "icon": "icon-cool-none", "description": "Keine Kühlung" },
            { "id": "klima", "label": "Klimaanlage", "icon": "icon-ac", "description": "Mit Klimaanlage" },
            { "id": "wp", "label": "Kühlung über Wärmepumpe", "icon": "icon-cool-wp", "description": "Passive oder aktive Kühlung mit Wärmepumpe" }
        ]
        },

        "Stockwerkslage": {
        "id": "stockwerkslage",
        "description": "Relative Position im Gebäude",
        "values": [
            { "id": "souterrain", "label": "Souterrain", "icon": "icon-souterrain", "description": "Teilweise unter Erdgleiche" },
            { "id": "eg", "label": "EG", "icon": "icon-ground", "description": "Erdgeschoss" },
            { "id": "1og", "label": "1. OG", "icon": "icon-1st", "description": "Erstes Obergeschoss" },
            { "id": "2og", "label": "2. OG", "icon": "icon-2nd", "description": "Zweites Obergeschoss" },
            { "id": "3og", "label": "3. OG", "icon": "icon-3rd", "description": "Drittes Obergeschoss" },
            { "id": "4og", "label": "4. OG", "icon": "icon-4th", "description": "Viertes Obergeschoss" },
            { "id": "dg", "label": "DG", "icon": "icon-attic", "description": "Dachgeschoss" }
        ]
        },

        "Nutzung": {
        "id": "nutzung",
        "description": "Aktuelle oder geplante Nutzung",
        "values": [
            { "id": "eigen", "label": "Eigennutzung", "icon": "icon-use-own", "description": "Selbst bewohnt" },
            { "id": "vermietet", "label": "Vermietet", "icon": "icon-use-rented", "description": "Aktuell vermietet" },
            { "id": "ferien", "label": "Feriennutzung", "icon": "icon-use-holiday", "description": "Genutzt als Ferienimmobilie" }
        ]
        },

        "Bauweise": {
        "id": "bauweise",
        "description": "Art der Bauweise",
        "values": [
            { "id": "massiv", "label": "Massiv", "icon": "icon-brick", "description": "Massivbauweise" },
            { "id": "holz", "label": "Holz", "icon": "icon-wood", "description": "Holzbauweise" },
            { "id": "fertig", "label": "Fertigteil", "icon": "icon-prefab", "description": "Fertighausbauweise" },
            { "id": "misch", "label": "Mischbauweise", "icon": "icon-mix", "description": "Kombination verschiedener Bauweisen" }
        ]
        },

        "Ausstattung": {
        "id": "ausstattung",
        "description": "Merkmale der Ausstattung",
        "values": [
            { "id": "ebk", "label": "Einbauküche", "icon": "icon-kitchen", "description": "Vorhandene Einbauküche" },
            { "id": "balkon", "label": "Balkon/Terrasse", "icon": "icon-balcony", "description": "Außenbereich vorhanden" },
            { "id": "garten", "label": "Garten", "icon": "icon-garden", "description": "Privat- oder Gemeinschaftsgarten" },
            { "id": "keller", "label": "Keller", "icon": "icon-cellar", "description": "Kellerraum verfügbar" },
            { "id": "kamin", "label": "Kamin", "icon": "icon-fireplace", "description": "Kamin oder Ofen" },
            { "id": "smart", "label": "Smart-Home", "icon": "icon-smart-home", "description": "Smart-Home-Integration" }
        ]
        },

        "Einrichtung": {
        "id": "einrichtung",
        "description": "Grad der Möblierung",
        "values": [
            { "id": "leer", "label": "Unmöbliert", "icon": "icon-empty", "description": "Keine Möbel enthalten" },
            { "id": "teil", "label": "Teil-möbliert", "icon": "icon-part-furnished", "description": "Teilweise eingerichtet" },
            { "id": "voll", "label": "Voll-möbliert", "icon": "icon-full-furnished", "description": "Komplett eingerichtet" }
        ]
        },

        "Grundstücksform": {
        "id": "grundstuecksform",
        "description": "Form des Grundstücks",
        "values": [
            { "id": "rechteckig", "label": "Rechteckig", "icon": "icon-rect", "description": "Regelmäßiges, rechteckiges Grundstück" },
            { "id": "unregel", "label": "Unregelmäßig", "icon": "icon-irregular", "description": "Unregelmäßige Form" },
            { "id": "ecke", "label": "Eckgrundstück", "icon": "icon-corner", "description": "An Straßenecke gelegen" }
        ]
        },

        "Topographie": {
        "id": "topographie",
        "description": "Geländeverlauf des Grundstücks",
        "values": [
            { "id": "eben", "label": "Eben", "icon": "icon-flat", "description": "Flaches Gelände" },
            { "id": "hang", "label": "Hanglage", "icon": "icon-hill", "description": "Grundstück in Hanglage" }
        ]
        },

        "Lage": {
        "id": "lage",
        "description": "Geographische Angabe",
        "values": [
            { "id": "plz", "label": "PLZ", "icon": "icon-zip", "description": "Postleitzahl" },
            { "id": "ort", "label": "Ort", "icon": "icon-city", "description": "Stadt oder Gemeinde" },
            { "id": "land", "label": "Land", "icon": "icon-country", "description": "Land" },
            { "id": "strasse", "label": "Straße", "icon": "icon-street", "description": "Straßenname" },
            { "id": "hausnr", "label": "Hausnummer", "icon": "icon-number", "description": "Hausnummer" },
            { "id": "coords", "label": "Koordinaten", "icon": "icon-gps", "description": "GPS-Koordinaten" }
        ]
        },
    },
    "Objekt": {
    "Stammdaten": [
      { "id": "angebotsart", "label": "Angebotsart", "type": "enum", "options": ["Kauf", "Miete"], "icon": "icon-offer", "description": "Art des Angebots" },
      { "id": "baujahr", "label": "Baujahr", "type": "number", "min": 1800, "max": 2100, "icon": "icon-year", "description": "Baujahr der Immobilie" },
      { "id": "zustand", "ref": "Meta.Zustand", "icon": "icon-condition", "description": "Erhaltungszustand der Immobilie" },
      { "id": "zimmer", "label": "Zimmer", "type": "number", "min": 1, "max": 50, "step": 0.5, "icon": "icon-rooms", "description": "Anzahl der Zimmer" },
      { "id": "badezimmer", "label": "Badezimmer", "type": "number", "min": 0, "max": 20, "step": 1, "icon": "icon-bath", "description": "Anzahl der Badezimmer" },
      { "id": "parkplaetze", "label": "Parkplätze", "type": "number", "min": 0, "max": 20, "icon": "icon-parking", "description": "Anzahl der Parkplätze" },
      { "id": "lage_minimal", "ref": "Meta.Lage.Minimal", "icon": "icon-location", "description": "PLZ, Ort, Land" }
    ],

    "Wohnung": {
      "Basis": [
        { "use": "Stammdaten" },
        { "id": "wohnflaeche", "label": "Wohnfläche", "type": "number", "unit": "m²", "min": 10, "max": 2000, "step": 0.1, "icon": "icon-area", "description": "Wohnfläche in Quadratmetern" },
        { "id": "etage", "label": "Etage", "type": "number", "min": -1, "max": 50, "icon": "icon-floor", "description": "Stockwerk, in dem sich die Wohnung befindet" },
        { "id": "stockwerkslage", "ref": "Meta.Stockwerkslage", "icon": "icon-level", "description": "Relative Position im Gebäude" },
        { "id": "lift", "ref": "Meta.Lift", "icon": "icon-lift", "description": "Aufzug vorhanden?" },
        { "id": "ausrichtung", "ref": "Meta.Ausrichtung", "icon": "icon-compass", "description": "Himmelsrichtung" },
        { "id": "heizungsart", "ref": "Meta.Heizungsart", "icon": "icon-heating", "description": "Art der Heizung" },
        { "id": "energietraeger", "ref": "Meta.Energieträger", "icon": "icon-energy", "description": "Primärer Energieträger" },
        { "id": "energieklasse", "ref": "Meta.Energieklasse", "icon": "icon-energy-class", "description": "Energieeffizienzklasse" }
      ]
    },

    "Haus": {
      "Basis": [
        { "id": "wohnflaeche", "label": "Wohnfläche", "type": "number", "unit": "m²", "min": 30, "max": 3000, "step": 0.1, "icon": "icon-area", "description": "Wohnfläche in Quadratmetern" },
        { "id": "grundstuecksflaeche", "label": "Grundstücksfläche", "type": "number", "unit": "m²", "min": 50, "max": 100000, "step": 0.1, "icon": "icon-plot", "description": "Grundstücksfläche in Quadratmetern" },
        { "id": "grundstuecksform", "ref": "Meta.Grundstücksform", "icon": "icon-shape", "description": "Form des Grundstücks" },
        { "id": "topographie", "ref": "Meta.Topographie", "icon": "icon-hill", "description": "Geländeverlauf des Grundstücks" },
        { "id": "ausrichtung", "ref": "Meta.Ausrichtung", "icon": "icon-compass", "description": "Himmelsrichtung" },
        { "id": "heizungsart", "ref": "Meta.Heizungsart", "icon": "icon-heating", "description": "Art der Heizung" },
        { "id": "energietraeger", "ref": "Meta.Energieträger", "icon": "icon-energy", "description": "Primärer Energieträger" },
        { "id": "energieklasse", "ref": "Meta.Energieklasse", "icon": "icon-energy-class", "description": "Energieeffizienzklasse" }
      ]
    },

    "Grundstück": {
      "Basis": [
        { "use": "Stammdaten" },
        { "id": "angebotsart", "label": "Angebotsart", "type": "enum", "options": ["Kauf", "Pacht"], "icon": "icon-offer", "description": "Art des Angebots" },
        { "id": "grundstuecksflaeche", "label": "Grundstücksfläche", "type": "number", "unit": "m²", "min": 50, "max": 2000000, "step": 1, "icon": "icon-plot", "description": "Grundstücksfläche in Quadratmetern" },
        { "id": "widmung", "label": "Widmung/Zonierung", "type": "text", "icon": "icon-zone", "description": "Nutzung laut Flächenwidmungsplan" },
        { "id": "aufschliessung", "label": "Aufschließung", "type": "enum", "options": ["Nicht erschlossen", "Teil-erschlossen", "Voll erschlossen"], "icon": "icon-infra", "description": "Erschließungszustand" },
        { "id": "grundstuecksform", "ref": "Meta.Grundstücksform", "icon": "icon-shape", "description": "Form des Grundstücks" },
        { "id": "topographie", "ref": "Meta.Topographie", "icon": "icon-hill", "description": "Geländeverlauf des Grundstücks" },
        { "id": "lage_minimal", "ref": "Meta.Lage.Minimal", "icon": "icon-location", "description": "PLZ, Ort, Land" }
      ]
    }
  }
}
```



## Vorgabe

- Alles konsistent mit id, label, icon, description
- leicht internationalisierbar (statt label: "Neu" → label: {"de":"Neu","en":"New"})
- frontend-ready: du kannst direkt icon in CSS/SVG einhängen