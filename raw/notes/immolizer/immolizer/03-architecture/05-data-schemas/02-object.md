



```json

{

        "Heizungsart": {
        "id": "heizungsart",
        "description": "Technische Art der Wärmeversorgung",
        "values": [
            { "id": "hz_zentral", "label": "Zentralheizung", "icon": "icon-heat-central", "description": "Zentrale Heizungsanlage für das gesamte Gebäude" },
            { "id": "hz_etage", "label": "Etagenheizung", "icon": "icon-heat-floor", "description": "Heizung pro Wohnung" },
            { "id": "hz_fb", "label": "Fußbodenheizung", "icon": "icon-heat-floor", "description": "Heizung über Bodenflächen" },
            { "id": "hz_fw", "label": "Fernwärme", "icon": "icon-heat-district", "description": "Anschluss an Fernwärmenetz" },
            { "id": "hz_ofen", "label": "Ofenheizung", "icon": "icon-heat-stove", "description": "Individuelle Einzelöfen" },
            { "id": "hz_wp", "label": "Wärmepumpe", "icon": "icon-heat-pump", "description": "Moderne Wärmepumpentechnik" }
        ]
        },

        "Energieträger": {
        "id": "energietraeger",
        "description": "Verwendeter Primärenergieträger",
        "values": [
            { "id": "et_gas", "label": "Gas", "icon": "icon-gas", "description": "Gasversorgung" },
            { "id": "et_oel", "label": "Öl", "icon": "icon-oil", "description": "Ölheizung" },
            { "id": "et_strom", "label": "Strom", "icon": "icon-electric", "description": "Direktstrom" },
            { "id": "et_fw", "label": "Fernwärme", "icon": "icon-district-heat", "description": "Fernwärmeanschluss" },
            { "id": "et_wp", "label": "Wärmepumpe", "icon": "icon-heat-pump", "description": "Strombetriebene Wärmepumpe" },
            { "id": "et_holz", "label": "Holz/Pellets", "icon": "icon-wood", "description": "Biogener Brennstoff" },
            { "id": "et_solar", "label": "Solar", "icon": "icon-solar", "description": "Solarenergie" },
            { "id": "et_geo", "label": "Geothermie", "icon": "icon-geo", "description": "Erdwärme" }
        ]
        },

        "Ausrichtung": {
        "id": "ausrichtung",
        "description": "Himmelsrichtung",
        "values": [
            { "id": "n", "label": "N", "icon": "icon-north", "description": "Nord" },
            { "id": "no", "label": "NO", "icon": "icon-ne", "description": "Nordost" },
            { "id": "o", "label": "O", "icon": "icon-east", "description": "Ost" },
            { "id": "so", "label": "SO", "icon": "icon-se", "description": "Südost" },
            { "id": "s", "label": "S", "icon": "icon-south", "description": "Süd" },
            { "id": "sw", "label": "SW", "icon": "icon-sw", "description": "Südwest" },
            { "id": "w", "label": "W", "icon": "icon-west", "description": "West" },
            { "id": "nw", "label": "NW", "icon": "icon-nw", "description": "Nordwest" }
        ]
        },

        "Besitzverhältnisse": {
        "id": "besitzverhaeltnisse",
        "description": "Rechtsform der Nutzung",
        "values": [
            { "id": "eig", "label": "Eigentum", "icon": "icon-owner", "description": "Volles Eigentum" },
            { "id": "we", "label": "Wohnungseigentum", "icon": "icon-condo", "description": "Eigentumswohnung" },
            { "id": "erb", "label": "Erbbaurecht", "icon": "icon-lease", "description": "Langfristiges Nutzungsrecht" },
            { "id": "pacht", "label": "Pacht", "icon": "icon-leasehold", "description": "Zeitlich begrenzte Nutzung" }
        ]
        },

}