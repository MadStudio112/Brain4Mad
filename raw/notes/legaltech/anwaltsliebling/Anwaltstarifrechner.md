---
title: "Anwaltstarifrechner"
type: "source"
source: "https://chatgpt.com/c/69124701-ecb0-8330-8eed-c46eb55675d5"
author:
published:
created: 2026-04-10
description: "ChatGPT ist dein KI-Chatbot für den Alltag. Führe mit der fortschrittlichsten KI Gespräche, um Ideen zu erforschen, Probleme zu lösen und schneller zu lernen."
tags:
  - "[raw"
  - "clipping]"
confidence: "low"
status: "draft"
---
Wir werden einen Anwaltstarif - Online - Rechner bauen - damit man die Honorare überprüfen kann. So einfach wie möglich html-js-css-json (?) Grundkonzept (bauen wir weiter aus): 1. Man gibt die Bemessungsgrundlage ein (z.B.: 100.000 €) 2. Man wählt eine Tarif (z.B.: TP6, TP8 lang 1/2,...) 3. Ergebnis wir angezeigt Analysiere mal: https://www.rechtsanwaelte.at/fileadmin/user\_upload/Gesetzestexte/RATG/ratg\_01042020.pdf Fragen: Wie würdest du die Daten bereitstellen bzw aus dem pdf bereitstellen? Was ist dein Plan - Vorschlag?

Kurzfassung: Ich würde die RATG-Tabellen einmalig kuratieren, in sauberes JSON gießen und den Rechner rein clientseitig (HTML/JS/CSS) rechnen lassen: Stückgebühren je Tarifpost, Stufenlogik, „vT“-Anteile, Kappungen, Rundung auf 10 Cent gemäß § 1 RATG. Die Bemessungsgrundlage gibst du ein, die Tarifpost wählst du, das Ergebnis und die Rechenwege werden angezeigt. [rechtsanwaelte.at](https://www.rechtsanwaelte.at/fileadmin/user_upload/Gesetzestexte/RATG/ratg_01042020.pdf)

## Daten aus dem PDF bereitstellen

- **Quelle und Stand mitschleppen:** `source`, `stand: "01.04.2020"`. [rechtsanwaelte.at](https://www.rechtsanwaelte.at/fileadmin/user_upload/Gesetzestexte/RATG/ratg_01042020.pdf)
- **Manuelle Extraktion statt OCR:** Die Tabellen in TP 1–3 und TP 5–9 sind klar strukturiert. Für MVP schneller und fehlerärmer als Parsen. Beispiele:
	- TP 1: Schriftsatz kurz, Stufen + Zuschläge „0,1 vT“ und „0,05 vT“, Cap 232,20 €. [rechtsanwaelte.at](https://www.rechtsanwaelte.at/fileadmin/user_upload/Gesetzestexte/RATG/ratg_01042020.pdf)
		- TP 2: Schriftsatz mittel und Tagsatzungen, Stufen + „0,5 vT“/„0,25 vT“, Caps 1 159,30 € bzw. 579,80 €. [rechtsanwaelte.at+1](https://www.rechtsanwaelte.at/fileadmin/user_upload/Gesetzestexte/RATG/ratg_01042020.pdf)
		- TP 3: Klage/Schriftsatz lang, Tagsatzungen, Berufung/Rekurs/OGH-Stufen mit vT-Zuschlägen und Caps. [rechtsanwaelte.at+2rechtsanwaelte.at+2](https://www.rechtsanwaelte.at/fileadmin/user_upload/Gesetzestexte/RATG/ratg_01042020.pdf)
		- TP 6: „Briefe anderer Art“ = 2× TP 5, Cap 154,90 €. [rechtsanwaelte.at](https://www.rechtsanwaelte.at/fileadmin/user_upload/Gesetzestexte/RATG/ratg_01042020.pdf)
		- TP 8: Besprechungen je angefangene **½ Stunde**, gestaffelt, <10 min = 0,4-Faktor, Cap 515,50 €. [rechtsanwaelte.at](https://www.rechtsanwaelte.at/fileadmin/user_upload/Gesetzestexte/RATG/ratg_01042020.pdf)
- **Rundungsregel:** Ergebnis auf volle 0,10 € runden (§ 1 Abs 1). [rechtsanwaelte.at](https://www.rechtsanwaelte.at/fileadmin/user_upload/Gesetzestexte/RATG/ratg_01042020.pdf)

## JSON-Schema (vorschlag)

Ein einheitliches, generisches Schema deckt alle TPs ab.

```markdown
{
  "meta": {
    "source": "RATG",
    "stand": "2020-04-01",
    "currency": "EUR",
    "rounding": "0.10"
  },
  "TP8": {
    "label": "Besprechungen je 1/2 h",
    "unit": "half_hour",
    "cap": 515.50,
    "steps": [
      {"upto": 70, "fee": 10.90},
      {"over": 70, "upto": 180, "fee": 15.90},
      {"over": 180, "upto": 360, "fee": 21.10},
      {"over": 360, "upto": 730, "fee": 26.00},
      {"over": 730, "upto": 1820, "fee": 39.00}
    ],
    "increments": [
      {"over": 1820, "upto": 20670, "step": 1450, "add": 8.20},
      {"over": 20670, "upto": 21800, "add": 8.20},
      {"over": 21800, "step": 1450, "add": 4.30}
    ],
    "multipliers": {
      "lt10min": 0.4,
      "30min": 1,
      "60min": 2
    }
  },
  "TP1": {
    "label": "Schriftsatz kurz",
    "unit": "per_item",
    "cap": 232.20,
    "steps": [
      {"over": 40, "upto": 70, "fee": 3.10},
      {"over": 70, "upto": 110, "fee": 5.50},
      {"over": 110, "upto": 180, "fee": 6.20},
      {"over": 180, "upto": 360, "fee": 6.70},
      {"over": 360, "upto": 730, "fee": 8.20},
      {"over": 730, "upto": 1090, "fee": 10.90},
      {"over": 1090, "upto": 1820, "fee": 11.90},
      {"over": 1820, "upto": 3630, "fee": 13.30},
      {"over": 3630, "upto": 5450, "fee": 15.90},
      {"over": 5450, "upto": 7270, "fee": 19.70},
      {"over": 7270, "upto": 10170, "fee": 26.00}
    ],
    "step_additions": [
      {"over": 10170, "upto": 34820, "step": 1450, "add": 3.10},
      {"over": 34820, "upto": 36340, "add": 3.10}
    ],
    "vt": [
      {"over": 36340, "upto": 363360, "permille": 0.1},
      {"over": 363360, "permille": 0.05}
    ]
  }
}
```

> **Interpretation „vT“:** 0,1 vT = 0,1 ‰ = 0,0001 × Mehrbetrag; 0,5 vT = 0,0005 × Mehrbetrag, usw. (Wortlaut bei TP-Tabellen). [rechtsanwaelte.at+1](https://www.rechtsanwaelte.at/fileadmin/user_upload/Gesetzestexte/RATG/ratg_01042020.pdf)

## Rechenengine (JS)

- `computeFee(tp, bg, options)`:
	1. passende **Stufe** finden → Grundgebühr,
		2. **step\_additions** und **increments** addieren,
		3. **vT-Anteile** auf den Mehrbetrag anwenden,
		4. **Multiplikator** für Dauer/Einheit (z. B. TP 8: 0,4 / 1 / 2),
		5. **Cap** anwenden,
		6. **Rundung** auf 0,10 €.
- Optional: **USt 20 %**, **Pauschalen/Barauslagen** als separate Zeilen, nicht im RATG-Ansatz enthalten.

## UI-Skizze

- **Input:** Bemessungsgrundlage (€), Auswahl Tarifpost, ggf. Dauer/Einheit.
- **Output:** Netto-Ansatz, Zwischenschritte, Cap-Hinweis, Rundung, optional USt + Summe.
- **Datenhaltung:** `ratg.json` im Projekt. Kein Backend nötig.

## Validierung

- **Unit-Tests** mit Beispielwerten pro TP und Grenzbereichen.
- **Visuelle Prüfzeile** „Quelle: RATG, Stand 01.04.2020“ unter dem Ergebnis. [rechtsanwaelte.at](https://www.rechtsanwaelte.at/fileadmin/user_upload/Gesetzestexte/RATG/ratg_01042020.pdf)

## Roadmap

1. MVP: TP 1, 2, 3A/B/C, 5–6, 7, 8, 9. (Zivil/außerstreitig + Standardaufwände). [rechtsanwaelte.at+6rechtsanwaelte.at+6rechtsanwaelte.at+6](https://www.rechtsanwaelte.at/fileadmin/user_upload/Gesetzestexte/RATG/ratg_01042020.pdf)
2. Erweiterungen: Auswahl „erste Stunde / weitere Stunde“ bei Tagsatzungen (TP 2/3), <10 min bei TP 8, Reisekosten TP 9 mit Parametern. [rechtsanwaelte.at+2rechtsanwaelte.at+2](https://www.rechtsanwaelte.at/fileadmin/user_upload/Gesetzestexte/RATG/ratg_01042020.pdf)
3. Langfristig: eigenes kleines JSON-„Registry“ je TP-Version, damit Rechtsstand änderbar bleibt.

Wenn du willst, setze ich dir daraus sofort ein minimales HTML/JS-Gerüst mit `ratg.json` für TP 8 und TP 1 als Start.

wichtig wäre mal das gesamte ratg.json für alle Anwendungsfälle Quellen: https://www.rechtsanwaelte.at/fileadmin/user\_upload/Gesetzestexte/RATG/ratg\_01042020.pdf https://www.oerak.at/fileadmin/user\_upload/Gesetzestexte/AHK/AHK\_01102024.pdf Vielleicht solltest du eine Deep Reseach machen um diese unterlagen zu analysieren um ein gute grundlage für die erstellung des json zu haben?

Ich habe dir eine erste, maschinenlesbare Basis gebaut: **RATG + AHK als JSON** mit Schema, TPs und AHK-Ansätzen.  

## Inhalt kurz

- **RATG (Stand 01.04.2020)**: TP 1, 2, 5, 6, 7, 8, 9 vollständig modelliert. TP 3A angelegt, Teiltabellen skizziert. Einheitssatz-Logik, Reise-/Zeitversäumnis enthalten. Werte z. B. TP 1 Tabelle inkl. Kappen und vT-Stufen (0,1 vT ab 36 340 €, 0,05 vT ab 363 360 €; Deckel 232,20 €). TP 2 Tabelle inkl. Zuschläge pro 1 450 € und vT-Stufen, Tagsatzungs-Deckel 1 159,30 €/579,80 €. TP 5/6 Beträge und „2×TP5“-Regel mit Kappe 154,90 €. TP 7 außer Kanzlei inkl. Halb-Stunden-Kappen und Verdopplung bei RA/RAA [rechtsanwaelte.at](https://www.rechtsanwaelte.at/fileadmin/user_upload/Gesetzestexte/RATG/ratg_01042020.pdf). TP 8 Besprechungen je ½ h inkl. Stufen und <10 Min-Faktor 0,4, Kappe 515,50 €. TP 9 Reisekosten inkl. Wegentschädigung 13,30 €/h [rechtsanwaelte.at](https://www.rechtsanwaelte.at/fileadmin/user_upload/Gesetzestexte/RATG/ratg_01042020.pdf). Rundung auf 0,10 € dokumentiert (§ 1 RATG).
- **AHK (Stand 01.10.2024)**: Vollständige **Bemessungsgrundlagen** für Zivil-/Verwaltung (Z 1–37) abgebildet, inkl. Formeln wie „3× Jahresbetrag“, Fixwerte und Sonderfälle.  
	**Straf-Ansätze** je ½ Stunde (Bezirks-, Einzelrichter-, Schöffen-, Geschworenen-, Haftverfahren) mit Pauschalen für Berufungen/Nichtigkeitsbeschwerden modelliert.  
	**Anwendung des RATG in Strafsachen (§ 10 AHK)** mit BMG-Stufen 7 800 €/18 000 €/27 600 €/33 200 € erfasst, inkl. TP-Mapping (TP 1, TP 3A/B, TP 7/2) und Streitgenossenzuschlag/Index-Zuschlag (§ 6 AHK).

## Plan für „vollständig“

1. **TP 3 komplettieren**: Teil A-Tabelle fortführen, Teil B/C Beträge und Verhandlungsregeln einpflegen, inkl. Wartezeit-Regel (¼ von TP 2 je ½ h) [rechtsanwaelte.at](https://www.rechtsanwaelte.at/fileadmin/user_upload/Gesetzestexte/RATG/ratg_01042020.pdf).
2. **Anmerkungen & Ausnahmen** pro TP als maschinenlesbare Flags (Kappungen, Zusammenrechnungen, Exekutions-Sonderregel bei TP 1).
3. **Einheitssatz (§ 23 RATG)** als berechenbare Option modellieren und AHK-Indexzuschlag (§ 6) als separate Funktion.
4. **Validierte Tests**: Rechenfälle je Stufe inkl. vT-Bereiche und AHK-Straf-Halbstunden.

Wenn du willst, erweitere ich die JSON jetzt um **TP 3 vollständig** und ergänze Tests sowie ein schlankes HTML/JS-MVP, das diese Datei lädt und Beträge live berechnet.

ja

Fertig. Ich habe **TP 3 vollständig** eingepflegt und ein **MVP-Frontend** erstellt.

- **JSON (RATG+AHK, TP 3 A/B/C komplett):**
	- TP 3 A: Bänder, 1 ‰/0,5 ‰ auf Mehrbetrag, Cap 15 454,20 €, Tagsatzung: 1. Std = Abschnitt I, jede weitere ½-Entlohnung mit Cap 7 727,20 €.
		- TP 3 B: Bänder, 1,25 ‰/0,625 ‰, Cap 19 317,80 €, Tagsatzung: 1. Std wie Abschnitt I, weitere ½-Entlohnung mit Cap 9 659,00 €. § 473a ZPO: ½ von Abschnitt I.
		- TP 3 C: Bänder, 1,5 ‰/0,75 ‰, Cap 23 181,30 €, Tagsatzung: 1. Std wie Abschnitt I, weitere ½-Entlohnung mit Cap 11 590,70 €. EuGH-Vorlageverhandlung = doppelter Betrag von Abschnitt II.
		- **Anmerkungen TP 3**: Wartezeit ¼ von TP 2 je ½ h (max 13,30 €) und Abberaumung ½ TP 2 (max 26,00 €); Zuschläge bei einstweiliger Verfügung. [rechtsanwaelte.at](https://www.rechtsanwaelte.at/fileadmin/user_upload/Gesetzestexte/RATG/ratg_01042020.pdf)
		- Bereits enthalten: TP 1, 2, 5–9 aus dem RATG und AHK-Grundlagen.
- **MVP-Rechner (HTML/JS, lädt obiges JSON):**  
	Eingabe BMG, Auswahl TP (inkl. TP 3 A/B/C), Berechnung mit Rechenweg, Rundung auf 0,10 € (§ 1 RATG). [rechtsanwaelte.at](https://www.rechtsanwaelte.at/fileadmin/user_upload/Gesetzestexte/RATG/ratg_01042020.pdf)

Nächster Schritt: Willst du, dass ich TP 4 vollständig ergänze und TP 2/3-Tagsatzungslogik in der UI auswählbar mache (erste Stunde/weitere Stunde, Wartezeit, Abberaumung)?

ja

Erledigt: **TP 4 ergänzt** und **UI für Verhandlung/Wartezeit/Abberaumung** freigeschaltet.

- **Datenbasis (RATG+AHK, v0.2.0):**  
	TP 4 nach RATG S. 16–17 (Privatanklage/MedienG, Anklagen 137,30 €/228,80 €, Anträge, Beweisanträge, Rechtsmittel, HV ½ h-Logik; Wartezeit/Abberaumung 6,70/13,30/26,00 €). [Rechtsanwälte Österreich](https://www.rechtsanwaelte.at/fileadmin/user_upload/Gesetzestexte/RATG/ratg_01042020.pdf)  
	TP 2 Wartezeit/Abberaumung integriert (¼-Satz je ½ h, Max 6,70 €; ½-Satz, Max 13,30 €). [Rechtsanwälte Österreich](https://www.rechtsanwaelte.at/fileadmin/user_upload/Gesetzestexte/RATG/ratg_01042020.pdf)  
	TP 3 Verhandlungs-Caps und Hinweise belassen (erste Stunde / weitere Stunde, EU-Vorlage doppelt). [Rechtsanwälte Österreich](https://www.rechtsanwaelte.at/fileadmin/user_upload/Gesetzestexte/RATG/ratg_01042020.pdf)  
	Rundung auf 0,10 € bleibt aktiv (§ 25 RATG). [Rechtsanwälte Österreich](https://www.rechtsanwaelte.at/fileadmin/user_upload/Gesetzestexte/RATG/ratg_01042020.pdf)  
	AHK Quelle hinterlegt (Index-/Zeitansatz-Regeln optional). [oerak.at](https://www.oerak.at/fileadmin/user_upload/Gesetzestexte/AHK/AHK_01102024.pdf?utm_source=chatgpt.com)
- **MVP+ Rechner (HTML/JS):**  
	Inputs: BMG, TP-Auswahl, Verhandlung (erste/weitere Stunde), Wartezeit-½ h, Abberaumung. Rechenweg wird ausgegeben.

Nächste Schritte:

1. TP 4-UI feingranular (alle Ziffern auswählbar, z. B. Rechtsmittel 1/10, 1,0, 1,5).
2. Einheitssatz (§ 23 RATG) als Option. [Rechtsanwälte Österreich](https://www.rechtsanwaelte.at/fileadmin/user_upload/Gesetzestexte/RATG/ratg_01042020.pdf)
3. AHK-Indexzuschlag (§ 6 AHK) und Streitgenossen-Zuschlag parametrisieren. [oerak.at](https://www.oerak.at/fileadmin/user_upload/Gesetzestexte/AHK/AHK_01102024.pdf?utm_source=chatgpt.com)
4. Unit-Tests für Band-Kanten und vT-Bereiche (TP 1–3).

ratg\_mvp\_plus.html

<iframe title="Vorschau" allow="midi" src="https://web-sandbox.oaiusercontent.com/?"></iframe>

2/2

Bereit.

- **Prototyp-UI:**  
	TP2/TP3 Verhandlung erste/weitere Stunde. TP4 komplett auswählbar. Globale Zuschläge: **Einheitssatz (§ 23 RATG)**, **AHK-Zuschlag (§ 6 AHK)**, **Streitgenossen**.
- **Datenbasis (JSON):**
- **Tests:**
- **Bundle (alles zusammen):**

Nächste Punkte:

- USt und Auslagen (TP 9) als Zusatzzeilen.
- Genauere Caps/Wartezeit-Logik nach Originalwortlaut pro TP.
- Vollständige Tabellenabdeckung für alle TP-Varianten und AHK-Fälle.

index.html

<iframe title="Vorschau" allow="midi" src="https://web-sandbox.oaiusercontent.com/?"></iframe>

tests.html

<iframe title="Vorschau" allow="midi" src="https://web-sandbox.oaiusercontent.com/?"></iframe>

Schreibe mal eine README.md die alles erklärt, mit Verweis auf die Datengrundlage (.pdf´s), damit ein Developer sich auskennt und alle weis

## RATG-Rechner — README

## Zweck

Ein schlanker, clientseitiger Rechner zur **Überprüfung von Anwaltskosten** nach **RATG** und **AHK**. Eingabe der **Bemessungsgrundlage (BMG)**, Auswahl der **Tarifpost (TP)**, Ausgabe des **Honorars** inkl. Rechenweg. Keine Serverkomponenten.

---

## Datenquellen

Bitte immer mitführen und im UI nennen:

- **RATG**: Rechtsanwaltstarifgesetz, Stand **01.04.2020**  
	PDF: `https://www.rechtsanwaelte.at/fileadmin/user_upload/Gesetzestexte/RATG/ratg_01042020.pdf`
- **AHK**: Allgemeine Honorar-Kriterien, Stand **01.10.2024**  
	PDF: `https://www.oerak.at/fileadmin/user_upload/Gesetzestexte/AHK/AHK_01102024.pdf`

> Hinweis: Die App bildet Tabellen und Regeln **maschinell** ab. Rechtstexte sind führend.

---

## Inhalte dieses Prototyps

Dateien im Projektroot:

- `index.html` – UI des Rechners
- `tests.html` – einfache Browser-Tests
- `ratg_ahk_2024-10_full_v0_3.json` – Datenbasis (RATG + AHK)
- Optionales ZIP: `ratg_rechner_prototyp_v0_3.zip` mit allen obigen Dateien

Downloads aus dieser Sitzung:

---

## Start

1. Repository/ZIP lokal ablegen.
2. `index.html` im Browser öffnen.
3. BMG eingeben, TP wählen, optional Verhandlung/Zuschläge setzen, **Berechnen**.

Tests: `tests.html` öffnen.

---

## Architektur

- **Rein clientseitig**: HTML + CSS + Vanilla JS.
- **Daten**: Eine JSON-Datei als „Single Source of Truth“.
- **Berechnung**: Im Browser, deterministisch, mit dokumentiertem Rechenweg.

---

## Datenformat (ratg\_ahk\_2024-10\_full\_v0\_3.json)

```markdown
{
  "meta": {
    "name": "RATG + AHK Datenbasis",
    "version": "0.3.0",
    "generated_at": "YYYY-MM-DDThh:mm:ssZ",
    "currency": "EUR",
    "rounding": 0.10,
    "legal_stand": { "RATG": "2020-04-01", "AHK": "2024-10-01" },
    "options": {
      "einheitssatz_default_pct": 0,
      "ahk_indexzuschlag_default_pct": 0,
      "streitgenossen_default_persons": 1,
      "streitgenossen_rule": "ab 2 Personen: +10%, jede weitere +5%"
    }
  },
  "RATG": {
    "TP1": { "...": "Schriftsatz kurz; Bänder, Zuschläge je 1.450 €, vT, Cap" },
    "TP2": { "...": "Schriftsatz mittel + Tagsatzungscaps; Warte-/Abberaumung-Logik" },
    "TP3": {
      "A": { "...": "umfangreiche Schriftsätze (Klage), vT 1,0‰ / 0,5‰, Caps" },
      "B": { "...": "Berufungen/Rekurse, vT 1,25‰ / 0,625‰, Caps" },
      "C": { "...": "Revision/OGH, vT 1,5‰ / 0,75‰, Caps, EU-Vorlage=2×" }
    },
    "TP4": { "...": "Privatanklage & MedienG; feste Sätze + 1/2-h-Logik + Warte/Abberaumung" },
    "TP5": { "...": "einfache Schreiben" },
    "TP6": { "...": "Briefe anderer Art = 2× TP5; Cap" },
    "TP7": { "...": "außerhalb der Kanzlei; je 1/2 h, ggf. Verdopplung" },
    "TP8": { "...": "Besprechungen je 1/2 h; Stufen, <10 min = 0,4; Cap" },
    "TP9": { "...": "Reise-/Zeitversäumnis; Wegentschädigung je Stunde" }
  },
  "AHK": {
    "zivil_und_verwaltung": { "...": "BMG-Definitionen/Fixes/Werte (z. B. 3× Jahresbetrag)" },
    "straf_und_disziplin": { "...": "Zeitansätze je 1/2 h; Pauschalen" },
    "straf_ahk_anwendung_ratg": { "...": "Mapping zu RATG-TP + BMG-Stufen" },
    "indexierung": { "...": "§ 6 AHK – Zuschlag/Indexlogik" },
    "zuschlaege": { "...": "Streitgenossen etc." },
    "auslagen": { "...": "§ 16 RATG, § 17 AHK" }
  }
}
```

### Kernelemente je TP

- `bands`: Grundgebühr für BMG-Intervalle.
- `increments`: Zuschläge ab Schwelle **je 1.450 €** oder Fix.
- `permille`: **vT** -Anteile (0,1‰ …) auf den **Mehrbetrag** in definierten Bereichen.
- `cap`: Kappungen je TP/Abschnitt.
- `hearings`: Verhandlungscaps und Multiplikatoren (TP2/TP3).
- TP-spezifische Regeln: <10-Min-Faktor, 2×TP5, etc.

---

## Rechenlogik

Reihenfolge in der Engine:

1. **Band** anhand BMG wählen → Grundbetrag.
2. **Increments** addieren:
	- per Step: `ceil((min(BMG, to) − from) / 1450) × add`
		- fix: einmaliger Zuschlag ab Schwelle
3. **vT** auf **Mehrbeträge** (‰-Sätze pro Bereich) addieren.
4. **Cap** anwenden.
5. **Verhandlung** (TP2/TP3):
	- erste Stunde = Grundbetrag, Cap „erste Stunde“
		- weitere Stunde = Faktor (meist 0,5) × Grundbetrag, Cap „weitere Stunde“
6. **Optionale Zuschläge**:
	- **Einheitssatz** (§ 23 RATG) in %
		- **AHK-Indexzuschlag** (§ 6 AHK) in %
		- **Streitgenossen**: 2 Personen = +10 %, jede weitere +5 %
7. **Rundung**: kaufmännisch auf **0,10 €**.

> USt und Auslagen werden nicht automatisch berechnet. Sie sind separat auszuweisen.

---

## UI-Bedienung

- **BMG** eingeben.
- **TP** wählen.
- Für **TP2/TP3**: Verhandlung „erste“ oder „weitere Stunde“ wählbar.
- Für **TP4**: konkrete Position (z. B. Rechtsmittel 1/10) und Anzahl 1/2-Stunden.
- **Optionale Zuschläge**: Einheitssatz, AHK-Zuschlag, Streitgenossen.
- **Berechnen** → Ergebnis + Rechenweg.

---

## Tests

`tests.html` führt einfache Checks im Browser aus:

- Band-Grenzwerte plausibel
- Monotonie unterhalb der ersten vT-Schwelle
- vT steigert Beträge bei größerer BMG
- Caps werden respektiert

Für produktive Nutzung: Jest/Playwright hinzufügen und Fälle pro TP/Schwelle abdecken.

---

## Erweiterung

- **Weitere TP**: Tabelle aus RATG übertragen → `RATG.TP…` ergänzen.
- **AHK-Fälle**: BMG-Ableitung als Utility, dann regulär RATG-Berechnung aufrufen.
- **USt/Auslagen**: Konfigurierbar je Fall; TP9-Parameterisieren (km-Satz, ÖPNV, Zeitversäumnis).
- **Mehrsprachigkeit**: UI-Strings kapseln, i18n JSON.
- **Validierung**: Grenzfälle je 1.450-Schritt, vT-Übergänge, Caps, <10-Min-Regel TP8.

---

## Beitragende Richtlinien

- Änderungen an Tabellen **quellenbelegt** committen.
- JSON-Schema einhalten, neue Felder dokumentieren.
- Tests für jede neue Stufe/Regel.
- Changelog pflegen, **Stand** der Rechtsgrundlage im `meta` aktualisieren.

---

## Rechtliches & Haftung

- Keine Rechtsberatung. Ergebnisse sind **unverbindliche Rechenhilfen**.
- Verbindlich sind **RATG/AHK** und die gerichtliche oder kammerrechtliche Praxis.
- Prüfe stets, ob die **Rechtsstände** im Projekt dem aktuellen PDF-Stand entsprechen.

---

## Lizenz

Nach Entscheidung des Projektinhabers. Üblich für Tools dieser Art: MIT für Code, **kein** Copyright-Transfer  
für Gesetzestexte; Gesetzestexte sind gemeinfrei, die PDFs als amtliche Werke zu behandeln, aber die **Quellenangabe ist Pflicht**.

---

## Kontakt

Bei Unklarheiten: konkrete TP, BMG, Rechtsstand und gewünschte Ausgabe nennen.

Kurz: **GK13 ist nicht RATG/AHK.** Das sind Positionen nach dem **Gerichtskommissärstarifgesetz (GKTG)**, Geschäftskreis **13 = Verlassenschaftsabhandlung**. Die gehören zur Notarin als Gerichtskommissärin, nicht zum Anwaltstarif.

Konsequenz:

- In deinem Screenshot sind die **3.531,00 €** GK13 keine RATG-Gebühren.
- Im Anwaltshonorar gehören solche Beträge höchstens als **Auslagen/Weiterverrechnung** ausgewiesen, nicht als eigene TP-Leistung.

Wenn du sie mitprüfen willst, brauchen wir zusätzlich ein **gktg.json** (GK01–GK13). Sag Bescheid, dann lege ich das Schema an und binde es als „Fremdkosten“ in den Rechner ein.

Was ist der Unterschied zwischen TP3A 3/2 und TP72 1/2?

Kurz:

- **TP3A 3/2** = **Tagsatzung nach TP 3A**: erste Stunde zum **vollen** TP-3A-Satz **+** eine weitere angefangene Stunde zum **halben** Satz ⇒ **1,5×** der nach BMG berechneten TP-3A-Entlohnung (mit den TP-3A-Caps für 1. und weitere Stunde).
- **TP7/2 1/2** = **Geschäft außerhalb der Kanzlei, Ziffer 2**: Abrechnung **je angefangene ½ Stunde** nach TP 7; Bemessungsbasis ist TP 6, **bei persönlicher Durchführung durch den Anwalt verdoppelt**. Es gelten die TP-7-½-Stunden-Kappen.

Praktische Abgrenzung:

- **Gerichtlicher Termin** (z. B. gerichtliche Befundaufnahme/Ortstermin) ⇒ meist **TP3A** als Tagsatzung; „3/2“ bedeutet 1 Std voll + 1 weitere Stunde halb.
- **Außergerichtlicher Ortstermin/Wegegeschäft** ⇒ **TP7/2**; „1/2“ bedeutet ein **½-Stunden-Block** (ggf. doppelt, wenn der Anwalt selbst geht).

Rechenlogik:

- **TP3A 3/2**: Betrag = min(Grundbetrag\_TP3A, Cap\_1. Std) + min(0,5×Grundbetrag\_TP3A, Cap\_weitere Std); danach Rundung.
- **TP7/2 1/2**: Betrag = min(TP6-½h-Ansatz × Faktor, Cap\_½h); Faktor = 2 bei persönlicher Durchführung durch den Anwalt, sonst 1; danach Rundung.

TP8 lang 2/2 - 1385,8 € 1. Was bedeutet diese Position TP8 lang 2/2 mit dem Positionstext "Konferenz mit Kli"? 2. Auf welche Bemessungsgrundlage lässt die 1385,8 € bei TP8 lang 2/2 schließen, ungefähr?

1. Bedeutung
- **TP8** = Besprechungen aller Art. Abrechnung **je angefangene ½ Stunde**. **„lang“** heißt hier nur: keine <10-Min-Kurzmitteilung. **„2/2“** = zwei ½-Stunden-Blöcke derselben Besprechung. Rechtsgrundlage: TP8 mit ½-Stunden-Sätzen; <10 Min nur 0,4-Satz; **Cap 515,50 € je ½ h**. [rechtsanwaelte.at](https://www.rechtsanwaelte.at/fileadmin/user_upload/Gesetzestexte/RATG/ratg_01042020.pdf)
1. BMG-Ableitung aus 1.385,80 € bei „TP8 lang 2/2“
- 1.385,80 € ÷ 2 = **692,90 € je ½ h**. Das liegt **über dem gesetzlichen Cap 515,50 € je ½ h**. Rein aus RATG-TP8 kann ein ½-Stunden-Ansatz nicht höher als 515,50 € sein. Also müssen **Zuschläge** draufliegen (z. B. AHK-Indexzuschlag, Einheitssatz, Streitgenossen). [rechtsanwaelte.at](https://www.rechtsanwaelte.at/fileadmin/user_upload/Gesetzestexte/RATG/ratg_01042020.pdf)
- Die Zahl deutet darauf hin: **Basis** = 2 × 515,50 € = **1.031,00 €**; Differenz = **354,80 €** ⇒ **≈ +34,4 %** Zuschläge auf den RATG-Betrag.
- Damit die **Basis** überhaupt am Cap liegt, braucht die BMG nur „hinreichend hoch“ zu sein. Aus der TP8-Staffel ergibt sich: Ab **ca. 144.000 €** BMG erreicht der ½-Stunden-Ansatz die Cap-Zone; darüber bleibt die Basis pro ½ h bei 515,50 € (vor Zuschlägen). Ableitung aus den TP8-Stufen und 1.450-€-Schritten, nicht aus einem ausdrücklichen Schwellenwert im Gesetz. [rechtsanwaelte.at](https://www.rechtsanwaelte.at/fileadmin/user_upload/Gesetzestexte/RATG/ratg_01042020.pdf)

Kurz: „Konferenz mit Kli, TP8 lang 2/2“ = zwei halbe Stunden Besprechung. 1.385,80 € bedeutet sehr wahrscheinlich **Cap-BMG** plus **~34 % Zuschläge** auf den RATG-Betrag.

Ab ca. 144.000 € BMG erreicht der ½-Stunden-Ansatz die Cap-Zone; 1. Liste die Cap-Zonen auf 2. Gibt es unterschiede zwischen einer Bemessungsgrundlage von 195.000 € und 275.000 € bzgl der Bemessung des Honorars?

1. Cap-Zonen bei **TP8 (Besprechungen)**  
	Grundregel: **Cap je angefangene ½ Stunde = 515,50 €**. Kurzbesprechung **<10 min = 0,4×** des ½-Stunden-Betrags ⇒ **Cap 206,20 €**.  
	Die Cap greift ab **BMG ≥ 144.050 €**. Herleitung:  
	39,00 € + 13×8,20 € + 8,20 € + **85×4,30 € = 515,50 €** ⇒ Schwelle = 21.800 € + **85×1.450 € = 144.050 €**.  
	Daraus ergeben sich die „Zonen“ (alle Beträge netto, je Vorgang):
- **<10 min:** max **206,20 €** (gleich 0,4×515,50).
- **½ h (1/2):** max **515,50 €**.
- **1 h (2/2):** max **1.031,00 €**.
- **1½ h (3/2):** max **1.546,50 €**.
- Allgemein: **n/2 Stunden ⇒ n × 515,50 €**.  
	Hinweis: Die Cap gilt **pro ½-Stunden-Block**.
1. Unterschied 195.000 € vs. 275.000 € BMG  
	Nein, **kein Unterschied** im RATG-Grundbetrag. Beide BMG liegen deutlich **in der Cap-Zone**.  
	Ungecappte Ansatzwerte wären ca. **669,80 €** bzw. **906,30 €** je ½ h, werden aber jeweils auf **515,50 €** begrenzt. Für „TP8 lang 2/2“ ergibt das in beiden Fällen **1.031,00 €** als Basis.  
	Abweichungen entstehen nur, wenn du **prozentuale Zuschläge** (z. B. Einheitssatz, AHK, Streitgenossen) addierst; die hängen dann vom **Basisbetrag**, nicht mehr von der BMG.

## TP2, TP5, TP6, TP8 — kurz erklärt

## TP2 – Schriftsatz „mittel“ + Tagsatzung

**Wofür:** typische Anträge/Begründungen mittleren Umfangs; außerdem **Verhandlungen/Tagsatzungen**.  
**Einheit:** pro Schriftsatz bzw. pro Stunde Verhandlung.  
**Berechnung (Schriftsatz):** BMG → Tabellenband → Zuschläge je 1.450 € → vT-Anteile (0,5‰, danach 0,25‰) → Cap.  
**Verhandlung:**

- **1\. Stunde:** Entlohnung wie Abschnitt I (Cap **1.159,30 €**).
- **Weitere Stunde:** **0,5×** davon (Cap **579,80 €**).  
	**Sonderregeln:** Wartezeit nach 30 min = **¼ von TP2 je ½ h** (max **13,30 €** je ½ h). Abberaumung ohne rechtzeitige Verständigung = **½ TP2** (max **26,00 €**).

## TP5 – Einfache Schreiben

**Wofür:** kurze Mitteilungen, einfache E-Mails an Mandanten, kurze Begleitschreiben.  
**Einheit:** pro Stück.  
**Berechnung:** BMG → Tabellenband → Zuschläge je 1.450 € → Cap **77,70 €**.  
**Praxis-Hinweis:** „E-Mail an Klienten“ landet meist hier.

## TP6 – Briefe anderer Art

**Wofür:** „normale“ Briefe an Dritte, die **kein Gutachten/Vertrag** sind (z. B. Brief an Notar, Gegenseite, Behörde).  
**Einheit:** pro Stück.  
**Berechnung:** **2× TP5**, Cap **154,90 €**.  
**Praxis-Hinweis:** formelleres oder längeres Schreiben als TP5 → oft TP6.

## TP8 – Besprechungen

**Wofür:** Besprechungen/Telefonate/Konferenzen.  
**Einheit:** **je angefangene ½ Stunde**.  
**Berechnung:** BMG → Tabellenband + 1.450-€-Schritte → Cap **je ½ h = 515,50 €**.  
**<10 Minuten:** **0,4×** des ½-Stunden-Betrags → Cap **206,20 €**.  
**Mehrere Blöcke:** 1 h = **2/2** ⇒ max **1.031,00 €**; 1½ h = **3/2** ⇒ max **1.546,50 €**, usw.  
**Cap-Zone:** Ab ca. **144.050 € BMG** ist der ½-Stunden-Ansatz gedeckelt; darüber steigt der TP8-Grundbetrag nicht mehr, nur noch prozentuale Zuschläge (Einheitssatz, AHK-Zuschlag, Streitgenossen) verändern das Ergebnis.

---

## Schnellzuordnung im Alltag

- **Kurze Info an Mandanten:** TP5.
- **Formeller Brief an Notar/Gegenseite:** TP6.
- **Konferenz/Telefon mit Mandant/Gegenseite:** TP8, z. B. „lang 2/2“ = 1 h.
- **Gerichtstermin/Tagsatzung:** TP2 (oder TP3 bei umfangreichen Sachanträgen), 1. Std voll, jede weitere ½-Entlohnung.

Kurz und vollständig. RATG hat **TP1–TP9**. **TP10 gibt es im RATG nicht**; falls du „TP10“ siehst, stammt das aus einem anderen Tarif (z. B. Gerichts-/Firmenbuchgebühren), nicht aus dem RATG. [Rechtsanwälte Österreich](https://www.rechtsanwaelte.at/fileadmin/user_upload/Gesetzestexte/RATG/ratg_01042020.pdf)

## TP1 – kurze Schriftsätze

- Einsatz: kurze Anzeigen/Mitteilungen, Standardanträge.
- Ansatz: Tabellenband + Schritte je 1.450 €; darüber **0,1‰** bzw. **0,05‰** auf Mehrbeträge; **Cap 232,20 €**. [Rechtsanwälte Österreich](https://www.rechtsanwaelte.at/fileadmin/user_upload/Gesetzestexte/RATG/ratg_01042020.pdf)

## TP3 – umfangreiche Schriftsätze und Rechtsmittel

**Teil A (z. B. Klagen, umfangreiche Beantwortungen):** vT **1‰/0,5‰**, **Cap 15.454,20 €**. Verhandlungen: 1. Stunde bis **15.454,20 €**, weitere Stunde **½**, Cap **7.727,20 €**. [Rechtsanwälte Österreich](https://www.rechtsanwaelte.at/fileadmin/user_upload/Gesetzestexte/RATG/ratg_01042020.pdf)  
**Teil B (Berufungen/Rekurse/Beschwerden):** vT **1,25‰/0,625‰**, **Cap 19.317,80 €**. Verhandlungen: 1. Stunde bis **19.317,80 €**, weitere **½** bis **9.659,00 €**. [Rechtsanwälte Österreich](https://www.rechtsanwaelte.at/fileadmin/user_upload/Gesetzestexte/RATG/ratg_01042020.pdf)  
**Teil C (Revision/OGH):** vT **1,5‰/0,75‰**, **Cap 23.181,30 €**. Verhandlungen: 1. Stunde bis **23.181,30 €**, weitere **½** bis **11.590,70 €**; EuGH-Vorlage = doppelt. [Rechtsanwälte Österreich](https://www.rechtsanwaelte.at/fileadmin/user_upload/Gesetzestexte/RATG/ratg_01042020.pdf)

## TP4 – Privatanklage & Mediengesetz

- Fixbeträge für Anklagen: **BG-Vergehen 137,30 €**, sonstige Vergehen **228,80 €**; weitere Ziffern (Anträge, Rechtsmittel) und **½-Stunden-Logik** für HV/Beweisaufnahme und 2. Instanz. [Rechtsanwälte Österreich+1](https://www.rechtsanwaelte.at/fileadmin/user_upload/Gesetzestexte/RATG/ratg_01042020.pdf)
- Wartezeit/Abberaumung: ½-h-Wartezeit **6,70 €** bzw. **13,30 €** je nach Fall; Abberaumung **13,30 €** bzw. **26,00 €**. [Rechtsanwälte Österreich](https://www.rechtsanwaelte.at/fileadmin/user_upload/Gesetzestexte/RATG/ratg_01042020.pdf)

## TP7 – Geschäfte außerhalb der Kanzlei

- Einheit: **je angefangene ½ Stunde**.
- Ansatz: wie **TP6**, **Cap 154,90 €** je ½ h; wenn RA/Anwärter persönlich und erforderlich: **doppelt**, Cap **309,50 €** je ½ h. Zusätzlich **Zeitversäumnis nach TP9 Z 4** und ÖPNV-Kosten. [Rechtsanwälte Österreich](https://www.rechtsanwaelte.at/fileadmin/user_upload/Gesetzestexte/RATG/ratg_01042020.pdf)

## TP9 – Reisekosten und Zeitversäumnis

- Gilt bei Geschäften außerhalb des Kanzleiortes (> 2 km).
- Ersetzt werden:  
	**1)** Reisekosten (ÖPNV; falls nicht möglich, Kfz-Vergütung; sonst **Wegentschädigung 13,30 €/h**),  
	**2)** Verpflegung (ab 3 h Abwesenheit),  
	**3)** Nächtigung,  
	**4)** **Zeitversäumnis 25,10 €/h** außerhalb der für das Geschäft nötigen Zeit. [Rechtsanwälte Österreich](https://www.rechtsanwaelte.at/fileadmin/user_upload/Gesetzestexte/RATG/ratg_01042020.pdf)

## Hinweis zu „TP10“

Im RATG endet der Tarif bei **TP9**. Kein TP10 vorhanden. Prüfe die Quelle, oft handelt es sich um andere Gebührentarife. [Rechtsanwälte Österreich](https://www.rechtsanwaelte.at/fileadmin/user_upload/Gesetzestexte/RATG/ratg_01042020.pdf)

Mach jetzt bitte eine übersichtliche Tabelle die für unsere Datenbank ".json " als Grundlage dient Position Leistung/Bereich Kurzbeschreibung Beschreibung Einheit Berechnung TP1 kurze Anzeigen/Mitteilungen, Standardanträge Für bloße Anzeigen, Urkundenvorlagen und Mitteilungen an das Gericht. Also ganz einfache, formale Schriftsätze (oft rund 60–80 € pro Vorgang; je nach Streitwert). Tabellenband + Schritte je 1.450 €; darüber 0,1‰ bzw. 0,05‰ auf Mehrbeträge; Cap 232,20 € TP2 Tagsatzungen typische Anträge/Begründungen mittleren Umfangs; außerdem Verhandlungen / Tagsatzungen Honorar für die Teilnahme an einem Gerichtstermin (“Tagsatzung”). Für jede weitere halbe Stunde Wartezeit nach Beginn steht ein Viertel des Ansatzes zu, jedenfalls begrenzt. Hier wird jedes Erscheinen des Anwalts bei Gericht vergütet. Das Honorar richtet sich nach der Dauer und dem Streitwert. Wartezeiten werden separat abgerechnet, wenn nicht früh genug abberaumt. pro Schriftsatz bzw. pro Stunde Verhandlung BMG → Tabellenband → Zuschläge je 1.450 € → vT-Anteile (0,5‰, danach 0,25‰) → Cap Wartezeit nach 30 min = ¼ von TP2 je ½ h (max 13,30 € je ½ h). Abberaumung ohne rechtzeitige Verständigung = ½ TP2 (max 26,00 €) TP3 Bezieht sich meist auf bestimmte Rechtsmittel in Zivilverfahren und spezifische Verfahrenshandlungen, z. B. Berufungen und Rekurse, mit eigenem Ansatz je nach Streitwert. TP4 Für bestimmte Schriftsätze oder Anträge, z. B. in Medienverfahren oder andere spezifische Verfahren. Gilt für vorbereitende Anträge, Beweisanträge und ähnliches, häufig in Straf- und Medienrecht. TP5 Einfache Schreiben, E-Mails kurze Mitteilungen, einfache E-Mails an Mandanten, kurze Begleitschreiben Abrechnung für einfache Schreiben/E-Mails an Mandanten oder Gegner. Gilt für einfache und kurze Mitteilungen (“Email kurz”). Dazu zählen kompakte Mitteilungen, einfache E-Mails oder kurze Schreiben an Mandanten oder Gegner. Abrechnung meist pauschal pro Vorgang. „E-Mail an Klienten“ landet meist hier. pro Stück BMG → Tabellenband → Zuschläge je 1.450 € → Cap 77,70 € TP6 Umfangreiche Schriftsätze „normale“ Briefe an Dritte, die kein Gutachten / Vertrag sind (z. B. Brief an Notar, Gegenseite, Behörde) Für längere und aufwändige Schreiben wie umfangreiche Stellungnahmen, längere E-Mails oder Schriftsätze (“Email lang”). Umfasst ausführliche E-Mails oder lange Schriftsätze, etwa eine vertiefte Argumentation oder komplexe Sachverhaltsdarstellung. Abrechnung nach Umfang und Aufwand. pro Stück BMG → Tabellenband + 1.450-€-Schritte → Cap je ½ h = 515,50 €.<10 Minuten: 0,4× des ½-Stunden-Betrags → Cap 206,20 €. Cap-Zone: Ab ca. 144.050 € BMG ist der ½-Stunden-Ansatz gedeckelt; darüber steigt der TP8-Grundbetrag nicht mehr, nur noch prozentuale Zuschläge (Einheitssatz, AHK-Zuschlag, Streitgenossen) verändern das Ergebnis. TP7 TP8 Telefonate und Besprechungen Besprechungen / Telefonate / Konferenzen Für alle Besprechungen und Telefonate mit Mandanten, Gegnern usw.: TP8(K) für kurze Gespräche, TP8(L) für lange Gespräche/Besprechungen. Tarif für persönliche Gespräche oder Telefonate. Unterschieden wird nach Dauer: Bis 10 Minuten kurzer Ansatz (TP8K), ab 20 Minuten längerer Ansatz (TP8L). Gilt auch für Konferenzen. Berechnung häufig pro angefangene halbe Stunde. je angefangene ½ Stunde TP9

Hier ist die saubere, JSON-taugliche Übersicht. Spalten exakt wie gewünscht.

| Position | Leistung/Bereich | Kurzbeschreibung | Beschreibung | Einheit | Berechnung |
| --- | --- | --- | --- | --- | --- |
| **TP1** | Kurze Schriftsätze | kurze Anzeigen/Mitteilungen, Standardanträge | Bloße Anzeigen, einfache Mitteilungen und Urkundenvorlagen an das Gericht. | **pro Stück** | BMG → **Tabellenband** → **Zuschläge je 1.450 €** → **vT 0,1‰ / 0,05‰** auf Mehrbeträge → **Cap 232,20 €** |
| **TP2** | Schriftsatz „mittel“ **und** Tagsatzungen | typische Anträge/Begründungen mittleren Umfangs; Verhandlungen/Tagsatzungen | Schriftsätze mittleren Umfangs; bei Verhandlungen: 1. Stunde zum Abschnitt-I-Satz, jede weitere Stunde **½-Satz**. **Wartezeit** ab 30 min je begonnene ½ h = **¼ TP2**, **Abberaumung** = **½ TP2** (jeweils mit kleinen Caps). | **Schriftstück** bzw. **Stunde Verhandlung** | Schriftsatz: BMG → Band → 1.450-€-Schritte → **vT 0,5‰ / 0,25‰** → Cap. Verhandlung: **Cap 1.159,30 €** für 1. Stunde, **579,80 €** je weitere Stunde. |
| **TP3A** | Umfangreiche Schriftsätze | Klagen/umfangreiche Begründungen | Längere Sachanträge und umfangreiche Schriftsätze. Verhandlung: 1. Std voll, weitere Std **½**. | **pro Stück**; **Stunde Verhandlung** | BMG → Band → 1.450-€-Schritte → **vT 1,0‰ / 0,5‰** → **Cap 15.454,20 €**; Verhandlung-Caps: **1\. Std 15.454,20 €**, **weitere 7.727,20 €**. |
| **TP3B** | Rechtsmittel 1 | Berufungen/Rekurse/Beschwerden | Rechtsmittel in zweiter Instanz. Verhandlung: 1. Std voll, weitere **½**. | **pro Stück**; **Stunde Verhandlung** | BMG → Band → 1.450-€-Schritte → **vT 1,25‰ / 0,625‰** → **Cap 19.317,80 €**; Verhandlung-Caps: **1\. Std 19.317,80 €**, **weitere 9.659,00 €**. |
| **TP3C** | Rechtsmittel 2 | Revisionen/OGH | Rechtsmittel an Höchstgerichte; EuGH-Vorlage in der Verhandlung = **doppelter** Abschnitt-II-Betrag. | **pro Stück**; **Stunde Verhandlung** | BMG → Band → 1.450-€-Schritte → **vT 1,5‰ / 0,75‰** → **Cap 23.181,30 €**; Verhandlung-Caps: **1\. Std 23.181,30 €**, **weitere 11.590,70 €**. |
| **TP4** | Privatanklage & MedienG | fixe Sätze + ½-Stunden-Logik | Anklagen/Anträge nach MedienG; Rechtsmittel-Anteile (z. B. 1/10, 1,0, 1,5); HV/Beweisaufnahme **je ½ h**. Wartezeit/Abberaumung mit kleinen Fix-Caps. | **pro Stück**; **½-Stunde** | Fixbeträge (z. B. 137,30 €/228,80 €) bzw. Anteil vom Z-2-Satz; Verhandlungen: 1. ½ h = 1,0×, weitere ½ h = 0,5× des Z-2-Satzes; Wartezeit/Abberaumung nach TP4-Ziffern. |
| **TP5** | Einfache Schreiben, E-Mails | kurze Mitteilungen | Kurze E-Mails/Begleitschreiben an Mandanten, Gegner, Gericht. | **pro Stück** | BMG → Band → **1.450-€-Schritte** → **Cap 77,70 €**. |
| **TP6** | Briefe anderer Art | formellere Schreiben | Normale Briefe an Dritte, die **kein** Gutachten/Vertrag sind (z. B. an Notar/Behörde/Gegner). | **pro Stück** | **2 × TP5**, **Cap 154,90 €**. |
| **TP7** | Geschäfte außerhalb der Kanzlei | Wege-/Ortstermine | Tätigkeit außerhalb des Kanzleiortes. Abrechnung **je angefangene ½ h**. Bei persönlicher Durchführung durch den Anwalt und Erforderlichkeit: **doppelt**. Reisekosten/Zeitversäumnis nach **TP9** ergänzen. | **½-Stunde** | Ansatz wie **TP6 je ½ h**; **Cap 154,90 €** je ½ h, bei Verdoppelung **Cap 309,50 €** je ½ h. |
| **TP8** | Telefonate & Besprechungen | Konferenzen/Besprechungen/Telefonate | Alle Gespräche mit Mandant, Gegner etc. **<10 min** = **0,4×**. | **½-Stunde** | BMG → Band → 1.450-€-Schritte → **Cap je ½ h = 515,50 €**; **<10 min Cap = 206,20 €**. **Cap-Zone** ab ca. **144.050 €** BMG. |
| **TP9** | Reise- und Abwesenheitskosten | Fahrt-/Zeitkosten | Öffentliche Verkehrsmittel bzw. Kfz-Sätze gem. Dienstreisevorschrift; Verpflegung/Nächtigung bei längerer Abwesenheit; **Zeitversäumnis** je Stunde außerhalb der eigentlichen Geschäftsdauer. | **nach Aufwand**; **pro Stunde** | Erstattung **tatsächlicher Kosten**; Weg-/Zeitansätze nach TP9-Ziffern; separat zur Leistung nach TP7/Tagsatzungen. |

Hinweis für die JSON-Datenbank:

- `Einheit` als kontrolliertes Vokabular verwenden: `per_item`, `hour`, `half_hour`, `costs`.
- `Berechnung` wird im JSON granular modelliert: `bands[]`, `increments[]`, `permille[]`, `cap`, `hearings{first_hour_cap,further_hour_factor,further_hour_cap}`, TP-spezifische Flags (`lt10min_factor`, `two_times_tp5`, `double_if_by_lawyer`, …).
- Zuschläge wie **Einheitssatz**, **AHK-Zuschlag**, **Streitgenossen** sind **nicht** Teil der TP-Grundlogik und werden in der App als optionale Prozentaufschläge geführt.

“Wir müssen das Konzept noch einmal ein bisschen überarbeiten und die Strategie besprechen oder den Aufbau des Rechners. Und zwar habe ich mir gedacht, wir machen zwei Anwendungsbereiche. Einerseits quasi der Mandant oder der Easy und Expert oder Mandant und Anwalt. Und zwar müssen wir beim Mandanten einfach nur die leichte, also die Bemessungsgrundlage auswählen. Dann wählt er aus welchem Tarif TP3, dann hat er noch ein Feld, wo er auswählt halbe Stunde, eineinhalb Stunden oder so. Das Problem ist, dass in den meisten Rechnungen einfach immer steht TP3, halb, eineinhalb. Wir wollen ja, dass er anhand der Rechnung die Parameter quasi eingibt und dann ein Ergebnis präsentiert. Und die Zuschläge und so sind selten ausgewiesen. Beziehungsweise würde dann in einen Expert-Modus oder in den Anwaltsmodus einbauen, wie wir das dann auch immer nennen. Verstehst du, wie ich das meine?”

01:22

Verstanden. Du willst zwei Modi: einen **Mandantenmodus** und einen **Anwalts- bzw. Expertenmodus**.

Mandantenmodus:

- **Einfach:** Der Mandant gibt nur die **Bemessungsgrundlage** und wählt den **Tarif** (z. B. TP3) und die **Dauer** (½ Stunde, 1½ Stunden) aus.
- **Keine komplizierten Zuschläge:** Alles bleibt auf Basis der Grundgebühr. Zuschläge oder spezielle Aufschläge werden hier nicht gezeigt. Ergebnis = einfache Honorarabschätzung.

Expertenmodus (Anwalt):

- **Erweitert:** Hier kann der Anwalt oder Experte zusätzliche Parameter eingeben, z. B. **Einheitssatz**, **AHK-Zuschlag**, **Streitgenossen**, und andere Details.
- **Vollständige Berechnung:** Alle Zuschläge, Caps und Sonderregelungen werden berücksichtigt. Ergebnis = präzise, vollständige Honorarberechnung.

Kurz: Mandant sieht nur das Nötigste. Anwalt kann alles einstellen. Zwei Ansichten, ein Rechner. Die Strategie ist klar. Ich passe das Konzept entsprechend an.

Hier findest du Musteraufstellungen https://www.law-experts.at/rechtsanwalt-oesterreich Was könnte bei TP 6 +Inf. das "+Inf." bedeuten?

Hier findest du Musteraufstellungen https://www.law-experts.at/rechtsanwalt-oesterreich Was könnte bei TP 6 +Inf. das "+Inf." bedeuten?

6/6

Hier findest du Musteraufstellungen https://www.law-experts.at/rechtsanwalt-oesterreich Was könnte bei TP 6 +Inf. das "+Inf." bedeuten?

Hier findest du Musteraufstellungen https://www.law-experts.at/rechtsanwalt-oesterreich Was könnte bei TP 6 +Inf. das "+Inf." bedeuten?

Das „+ Inf.“ bei **TP6 +Inf.** scheint **nicht** vom Gesetzestext des Rechtsanwaltstarifgesetz (RATG) selbst vorgegeben zu sein — dort heißt es nur: „das Doppelte der in Tarifpost 5 festgesetzten Entlohnung, jedoch nie mehr als 154,90 €“. [rechtsanwaelte.at+1](https://www.rechtsanwaelte.at/fileadmin/user_upload/Gesetzestexte/RATG/ratg_01042020.pdf?utm_source=chatgpt.com)  
Ich kann aber eine plausible Erklärung liefern:

### Mögliche Bedeutung von „+ Inf.“

- Es könnte bedeuten **„ohne obere Begrenzung“** oder **„beliebige Bemessungsgrundlage (Inf = Infinity)“**, d. h. dass die Leistung **für sämtliche Streitwerte** gilt, unabhängig vom Wert.
- Es könnte darauf hinweisen, dass **der normale Band-/Stufenmechanismus** für TP6 hier **nicht mehr relevant ist**, sondern eine **Vereinbarung / Einzelfallfestsetzung** erfolgt („infinitesimal“).
- Es könnte eine **Praxis-Kennzeichnung** sein: z. B. „+Inf.“ = „Streitwert > …“ bzw. „Gilt für alle höheren Werte“, also eine Vereinfachung in der Musteraufstellung.

### Schlussfolgerung

Wenn du „TP6 +Inf.“ siehst, interpretiere ich es so:

- Leistung nach **TP6** („Briefe anderer Art“)
- **Bemessungsgrundlage beliebig hoch** („Inf.“ = keine obere Begrenzung im Beispiel)
- Der konkrete Betrag auf der Rechnung basiert dann auf dem Tarif oder einer **Einzelvereinbarung**, nicht strikt auf einer Band-Stufe aus dem Gesetz.

Wenn du möchtest, kann ich prüfen, ob dieser Zusatz („+Inf.“) in mehreren Rechnungsbeispielen auftaucht und wie Kanzleien ihn konkret verwenden.



---
---


# Anwaltstarifrechner (AT)

Ein modularer Rechner für österreichische Anwaltskosten auf Basis von RATG und AHK. Zwei Workflows: **Mandant** (einfach) und **Anwalt** (Expert). Ziel: transparente, nachvollziehbare Berechnung mit prüfbaren Zwischenschritten.

---

## 1. Ziele

- **Korrektheit**: Regeln aus RATG und AHK abbilden.
    
- **Nachvollziehbarkeit**: jede Position mit Quelle, Formel und Zwischenergebnissen.
    
- **Modularität**: Tarif-Engine entkoppelt von UI.
    
- **Portabilität**: als NPM‑Paket + REST API nutzbar.
    

---

## 2. Geltungsbereich

- Österreichisches **Rechtsanwaltstarifgesetz (RATG)** und **Allgemeine Honorar‑Kriterien (AHK)**.
    
- Fokus: Zivil-, Exekutions-, Außerstreit‑Konstellationen für typische Positionen (TP1–TP8 inkl. Einheitssatz §23). Strafrecht optional in Phase 2.
    
- **Honorarvereinbarungen** werden unterstützt, überschreiben aber RATG/AHK‑Berechnung.
    

---

## 3. Nutzer‑Modi

### 3.1 Mandant‑Modus (Easy)

Minimaler Input:

- Bemessungsgrundlage / Streitwert
    
- Verfahrenstyp (z. B. Zivilprozess, Außerstreit, Exekution)
    
- Tarifposition(en) als Auswahl (vorkonfiguriert)
    
- Zeitblöcke nur in vordefinierten Stufen (z. B. 0,5 h, 1,0 h, 1,5 h), wo relevant
    
- Ausgabe: Gesamtsumme, Netto/Brutto, Aufschlüsselung, Hinweis zu Einheitssatz vs. Nebenleistungen
    

### 3.2 Anwalt‑Modus (Expert)

Erweiterter Input:

- Exakte TP‑Auswahl inkl. Unterpositionen
    
- Zeit, Anzahl Schriftsätze/Briefe, Verhandlungstermine, Reisezeiten
    
- Einheitssatz nach §23 statt Nebenleistungen (toggle)
    
- Auslagen, Pauschalen, USt‑Optionen, allfällige Zuschläge
    
- Ausgabe: detailierte Positionsliste mit Quellenverweisen
    

---

## 4. Domänenmodell

**Kernobjekte**

- `Case`: Verfahren, Gericht, BG, Parteienstatus
    
- `TariffItem`: TP‑Code, Bezeichnung, Rechenregel, Grenzen/Deckel
    
- `Activity`: konkrete Leistung (z. B. Schriftsatz, Brief, Verhandlung), Felder: Menge, Dauer, Satzbezug
    
- `Charge`: monetäres Ergebnis einer Regelanwendung (Netto, USt, Brutto)
    
- `Policy`: Schalter (Einheitssatz aktiv, Honorarvereinbarung, AHK‑Leitwerte)
    
- `Ledger`: Liste aller `Charge` inkl. Meta (Quelle, Formel)
    

**Datenhaltung**

- `tariffs.json`: maschinenlesbare RATG‑Regeln je TP
    
- `ahk.json`: Leitlinien und Bandbreiten
    
- `lookups.json`: Tabellen (z. B. Streitwertstaffeln)
    

---

## 5. Rechenlogik

### 5.1 Grundschema

1. **Bemessungsgrundlage** ermitteln → Streitwertklasse
    
2. **Hauptleistung**: passende TP wählen und Grundsatz anwenden
    
3. **Nebenleistungen**: TP5/TP6/TP8 addieren **oder** **Einheitssatz (§23)** verwenden
    
4. **Auslagen** und Spesen hinzufügen (z. B. Pauschalen, Reisekosten)
    
5. **USt** berechnen
    
6. Optional: **Vorsteuer‑Rückersatz‑Hinweis** für Kostenersatzszenarien
    

### 5.2 Einheitssatz (§23 RATG)

- Wenn aktiv: ersetzt TP5/TP6/TP8 und Postgebühren im Inland.
    
- Alternative: statt Einheitssatz die einzelnen Nebenleistungen abrechnen.
    

### 5.3 Typische TP‑Logik (Beispiele)

- **TP1**: Eingabe/Erwiderung Schriftsatz, streitwertabhängig
    
- **TP3**: Rechtsgutachten/Begründung, teils Mehrfachsätze
    
- **TP5**: Akten- und Schriftwiedergabe, Seiten‑ oder Umfangsbezug, Deckel
    
- **TP6**: Briefe anderer Art, meist als Faktor auf TP5 mit Höchstbetrag
    
- **TP7**: Verhandlungstermin, Dauerbezug
    
- **TP8**: Kopien, Zustellungen, Porti etc.
    

### 5.4 Auslagen und USt

- Auslagen als eigene `Activity`‑Typen erfassen (Reise, Gerichtsgebühren, Zustellungen)
    
- USt 20 % auf RA‑Leistungen; Auslagen je nach Art netto oder durchlaufend
    

---

## 6. Regeln als DSL

Konfigurierbare Tarifregeln in JSON:

```json
{
  "TP6": {
    "label": "Briefe anderer Art",
    "base": { "ref": "TP5", "factor": 2 },
    "cap": { "amount": 138.90, "currency": "EUR", "per": "letter" },
    "includes": ["Briefe, die keine Gutachten/Verträge sind"],
    "excludes": ["Rechtsgutachten", "Vertragsurkunden"],
    "notes": ["Deckel pro Stück anwenden"],
    "sources": ["RATG:Anlage.TP6"]
  }
}
```

Ergänzend: Streitwertstaffeln, Mehrfachsätze, Zeit‑/Mengenbezüge.

---

## 7. Validierung

- Widerspruchsprüfung: Einheitssatz aktiv **vs.** Nebenleistungen
    
- Deckelprüfungen (z. B. TP6‑Höchstbetrag pro Brief)
    
- Pflichtfelder je TP
    
- Rundergebnisse: centgenau, kaufmännisch
    

---

## 8. API‑Schnittstellen

### 8.1 REST

- `POST /api/calc` → Input: Case + Activities + Policy → Output: Ledger + Summen
    
- `GET /api/tariffs` → aktuelle Tariftabelle
    
- `GET /api/tariffs/:tp` → Detailregel
    

### 8.2 NPM‑Paket

```ts
import { calculate, loadPolicies } from "@anwaltskosten/ratg";

const result = calculate(caseData, activities, policy);
console.log(result.total.gross);
```

---

## 9. UI‑Spezifikation

- **Mandant**: Wizard mit 3 Schritten, Defaults, Erklär‑Tooltips
    
- **Anwalt**: Tabelleneditor für Activities, Live‑Ledger, Quellennachweise
    
- Export: PDF‑Kostenübersicht, JSON‑Audit, CSV‑Positionen
    
- i18n: de‑AT primär, en sekundär
    
- A11y: Tastatur‑Navigation, klare Fehlermeldungen
    

---

## 10. Beispiel

**Fall**: Zivilverfahren, BG 195.000 €; Leistungen: 1 Schriftsatz (TP1), 2 Briefe (TP6), Verhandlung 1h (TP7); Policy: Einheitssatz **aktiv**.

Ablauf:

1. TP1 nach Streitwertklasse
    
2. TP7 nach Dauer
    
3. **Einheitssatz §23** ersetzt TP5/TP6/TP8 → keine separaten TP6‑Briefe
    
4. USt auf RA‑Leistungen, Auslagen separat
    

Ergebnisdarstellung: Hauptleistungen + Einheitssatz + USt = Brutto; Ledger mit Formeln.

---

## 11. Architektur

- **Core**: reine Funktionen, pure Rules‑Engine
    
- **Adapters**: Web, Node, CLI
    
- **Data**: versionierte Regelsätze (semver, changelog)
    
- **Compliance**: Quellen‑Resolver zeigt §/TP zur Position
    
- **Tests**: Snapshot‑Tests für Musterfälle, Golden‑Files
    

---

## 12. Datenquellen & Updates

- Regeln versionieren: `ratg-2025.01`, `ahk-2024.10`
    
- Updater‑Script crawlt Quellen, diff’t Texte, erstellt Prüf‑Reports
    
- Manuelle Freigabe mit Vier‑Augen‑Prinzip
    

---

## 13. Edge‑Cases

- Honorarvereinbarung > RATG: Vorrang der Vereinbarung
    
- Kostenersatz vs. Mandatsrechnung: unterschiedliche Ausweisung
    
- Vorsteuer‑Rückersatzhinweis im Kostenersatzfall
    
- Parser‑Toleranz für Notationen wie `TP6`, `TP 6`, `TP6 (2x)`, unbekannte Suffixe werden protokolliert und zur Klärung vorgeschlagen
    

---

## 14. Roadmap

- **MVP**: Zivil + Einheitssatz + TP1/3/7 + Basisauslagen, Mandant‑Wizard, PDF‑Export
    
- **Phase 2**: Vollständige Nebenleistungen, Strafrecht, Reisekosten, Reisestaffeln
    
- **Phase 3**: Gerichtskosten‑Interfaces, E‑AK‑Import, Schnittstelle zu Honorarvereinbarungen
    

---

## 15. Rechtlicher Hinweis

Der Rechner dient als **Planungs‑ und Schätztool**. Verbindlich sind Mandatsvereinbarungen, RATG/AHK sowie gerichtliche Kostenentscheidungen. Ergebnisse sind ohne Gewähr; Quellenstand wird je Release dokumentiert.