
# Aprilia RSV Tuono 1000 (2002–2005, IE E2) – Kraftstoffpumpen-Stecker und Relaisüberblick

## Pinbelegung des Kraftstoffpumpen-Steckers (inkl. Kabelfarben und Nennwerte)

Der 4-polige Anschluss der Kraftstoffpumpe enthält sowohl die Stromversorgung der Pumpe als auch die Leitungen des Tankinhaltsensors. Die Pins sind wie folgt belegt:

- **Pin 1 (Plus zur Pumpe)** – **Rot** (R): +12 V Einspeisung für die Kraftstoffpumpe (kommt vom Kraftstoffpumpen-Relais).
- **Pin 2 (Masse zur Pumpe)** – **Blau** (B): Masseleitung der Pumpe (führt zum Fahrzeug-Massepunkt).
- **Pin 3 (Sensor)** – **Orange/Schwarz** (Ar/N): Signal vom Kraftstoffstandsensor (Reserveschalter) zum Kombiinstrument (Kraftstoff-Reserveanzeige).
- **Pin 4 (Sensor-Masse)** – **Blau/Schwarz** (B/N): Masse-Rückleitung des Kraftstoffstandsensors (am Kabelbaum mit Masse verbunden).

**Nennwerte:** Der Kraftstoffstandsensor ist ein thermistorbasierter Sensor. Bei vollem Tank beträgt sein Widerstand typischerweise unter **14 Ω**, während er bei leerem Tank auf **240–400 Ω** ansteigt. Diese Widerstandswerte entsprechen den Schwellen für die Reserveanzeige (bei hoherem Widerstand leuchtet die Reserveleuchte). Die Kraftstoffpumpe selbst wird mit 12 V betrieben und über eine 15 A-Sicherung abgesichert. Im Betrieb fließt typischerweise ein Strom von einigen Ampere durch die Pumpe (bei blockierter Pumpe kann das Relais heiß werden). Die Förderleistung der Pumpe entspricht dem benötigten Einspritzdruck (ca. 3 bar).

## Relaispositionen, Bezeichnungen und Schaltung (Fuel Pump, Engine Stop, Starter)

Im Sicherungssystem der RSV Tuono 1000 sind drei Relais relevant, die unter der Sitzbank im Heckbereich nahe Batterie und ECU (Steuergerät) angeordnet sind. Im Schaltplan werden diese meist als **R1, R2, R3** gekennzeichnet. Laut Schaltplan-Legende sind dies:

- **R1 – Engine Stop Relay (Motor-Stopp-Relais)** – zuständig für die Hauptstromversorgung des Motorsteuerkreises.
- **R2 – Fuel Pump Relay (Kraftstoffpumpen-Relais)** – schaltet die Spannungsversorgung der Kraftstoffpumpe.
- **R3 – Starter Relay (Anlassrelais)** – Hochstrom-Relais (Anlasserschütz) zur Verbindung von Batterie und Anlasser.

Jedes Relais ist ein Wechselrelais (Spule und ein Schließerkontakt). Nachfolgend die Funktionen, Ansteuerung und Kabelfarben der einzelnen Relais im Überblick:

### Motor-Stopp-Relais (R1) – **Engine Stop Relay**

**Funktion:** Dieses Relais schaltet die Zündung/Injection hauptseitig frei oder ab. Ist das Relais angezogen, werden das Motorsteuergerät (ECU) sowie Einspritzventile, Zündspulen und das Kraftstoffpumpen-Relais mit Batteriespannung versorgt. Fällt es ab, wird die Motorsteuerung stromlos geschaltet – der Motor geht aus (vergleichbar mit dem Killschalter). Damit ist R1 ein zentrales Sicherheitselement im **Kill-/Not-Aus-Kreis**.

**Ansteuerung & Sicherheitsverschaltung:** Das R1 wird nur aktiviert, wenn **Zündung und Kill-Schalter auf „Ein“** stehen _und_ alle Sicherheitsbedingungen erfüllt sind. Die Relais-Spule erhält +12 V über das Zündschloss und den Kill-Schalter (geschaltetes Zündplus, Kabelfarbe meist **Orange (Ar)**) und wird auf der Masse-Seite nur durchgeschaltet, wenn **Seitenständer oben** _oder_ **Leerlauf eingelegt** ist. Diese Masseführung erfolgt über ein Diodenmodul und den Seitenständerschalter/Leerlaufschalter: bei ausgeklapptem Ständer und eingelegtem Gang unterbricht der Seitenständerschalter den Massepfad, sodass R1 abfällt. Im Leerlauf oder bei eingeklapptem Ständer ist der Massepfad geschlossen (Kabelfarbe im Schaltplan oft **hellblau** oder **grau** für den Ständer-Signalweg). Ein **Umfallsensor** (Neigungsschalter) beeinflusst ebenfalls die Motorabschaltung: Im Falle eines Sturzes signalisiert der Sensor der ECU, die Kraftstoffzufuhr zu stoppen; die ECU lässt daraufhin das Motor-Stopp-Relais abfallen bzw. schaltet Einspritzung/Zündung ab.

**Schaltung & Pins:** R1 hat typischerweise vier Anschlussklemmen: zwei für die Spule und zwei für den Schließerkontakt. Die **Spule** wird wie oben beschrieben von Zünd+/Kill (+12 V, z.B. Kabel Farbe Orange) gegen Masse über Seitenständer/Diode angesteuert. Der **Schließerkontakt** von R1 verbindet die Batterieversorgung mit den nachfolgenden Stromkreisen: Eingang ist Dauerplus (über Hauptsicherung 30 A) bzw. Zündplus, Ausgang geht auf die **Sekundärsicherungen** für die Motorsteuerung. Konkret versorgt der Ausgang von R1 zwei 15 A-Stromkreise: einen für Einspritzventile, Zündspulen und weitere Aktuatoren (**Sicherung „E“ 15 A** laut Schaltplan) und einen zweiten für den Anlassersteuerkreis und die Pumpe (**Sicherung „D“ 15 A für Fuel Pump, Starter Relay, etc.**). Die Kabel am Relaiskontakt sind entsprechend: Eingang meist Rot oder Rot/Weiß (vom Batterie-/Zündkreis), Ausgang z.B. **Orange/Grün** oder **Orange/Weiß**, welches zu den Sicherungen führt (Kabelbündel zum Sicherungskasten).

**Position:** R1 befindet sich unter der Sitzbank in der hinteren Relaishalterung, typischerweise das _vordere_ oder _rechte_ der kleinen Relais (die baugleichen R1 und R2 sitzen nebeneinander in Gummihalterungen).

### Kraftstoffpumpen-Relais (R2) – **Fuel Pump Relay**

**Funktion:** Dieses Relais versorgt die Kraftstoffpumpe mit Strom, wenn es von der ECU freigegeben wird. Nach Einschalten der Zündung zieht R2 für einige Sekunden an, um die Pumpe vorzupumpen (Prime-Funktion), und während des Motorlaufs hält die ECU das Relais ebenfalls angezogen, damit Kraftstoffdruck anliegt. Bei abgeschaltetem Motor oder bei Sicherheitsabschaltung (z.B. Umkippen) fällt R2 ab und die Pumpe stoppt sofort.

**Ansteuerung:** Die Spule des Kraftstoffpumpen-Relais erhält ihre +12 V ebenfalls aus dem Zündstromkreis. Da R2 _hinter_ dem Motor-Stopp-Relais liegt, ist dessen Spulenzuleitung nur aktiv, wenn R1 angezogen hat (d.h. Zündung/Kill ok). Konkret kommt die Versorgung der R2-Spule von der Sekundärsicherung (15 A, Kreis D) für Pumpe/Anlasser. Die **Masse-Seite der R2-Spule wird durch das Motorsteuergerät (ECU) gesteuert**: Die ECU schaltet den entsprechenden Ausgangstransistor nach Masse, um das Relais anzuziehen. Somit kann die ECU die Pumpe zeitgesteuert ein- und ausschalten. Die Kabelfarben der Spulenanschlüsse sind meist: +12 V Spulenzuführung **Orange** oder **Braun** (entsprechend dem geschalteten Plus aus R1/Fuse D), und der vom ECU kommende Steuerdraht ist oft **weiß/schwarz** oder **blau/schwarz** (entspricht dem Pin am ECU-Stecker, z.B. Pin 16 am 16-poligen Stecker laut Werkstatthandbuch – dieser wird von der ECU gegen Masse geschaltet).

**Schaltung & Pins:** Der **Schließerkontakt** von R2 verbindet den 12 V-Versorgungsstrom (vom Sicherungskasten) mit der Pumpe. **Eingang** ist die Zuleitung von der 15 A-Sicherung D (Kabel z.B. **Rot** oder **Weiß/Rot** vom Verteiler), **Ausgang** ist die Leitung zur Kraftstoffpumpen-Baugruppe. Die Ausgangsleitung hat die Farbe **Rot (R)** und geht zum Pin 1 des Pumpensteckers (Plusleitung Pumpe). Die **Masseleitung** der Pumpe (Pin 2, **Blau**) ist direkt an der Fahrzeugmasse angeschlossen, nicht über das Relais geführt. R2 hat ebenfalls vier Pins: zwei Spulenanschlüsse (+12 V und ECU-Masse) und zwei Kontaktanschlüsse (Einspeisung von Sicherung -> Ausgabe zur Pumpe).

**Querverbindungen:** Da die ECU das Relais steuert, hängt R2 vom korrekten Signal des **Kurbelwellenpositionssensors** (Pickup) ab: die ECU aktiviert die Pumpe nur, wenn ein Drehimpuls erkannt wird oder für das initiale Vorfördern. Im Fehlerfall (z.B. Umkippsignal vom Neigungssensor) deaktiviert die ECU die Masse für R2, wodurch die Pumpe abschaltet.

**Position:** R2 sitzt direkt neben R1 unter der Sitzbank. Oft sind R1 und R2 baugleiche Relais (12 V/20–30 A Nennstrom) und in einem gemeinsamen Halter untergebracht. Welches das Pumpenrelais ist, erkennt man an den Kabelfarben: das Pumpenrelais hat am Ausgang ein rotes Kabel, das zum Pumpenstecker führt. In Zweifelsfall spürt man beim Einschalten der Zündung ein _Klicken_ von R2 und hört gleichzeitig das Surren der Pumpe.

### Anlasserrelais (R3) – **Starter Relay**

**Funktion:** Dieses Relais ist ein Starter-Schütz, das bei Betätigung des Starterknopfs die Batterie direkt mit dem Anlasser verbindet. Es handelt sich um ein Hochstrom-Relais (typ. 150 A Schaltstrom). Wenn R3 schließt, fließt der hohe Anlasserstrom vom Pluspol der Batterie zum Anlasser-Motor. Bei nicht betätigtem Starterknopf trennt R3 den Anlasser vom Strom, um ein unbeabsichtigtes Anlassen zu verhindern.

**Ansteuerung:** Die Spule von R3 liegt ebenfalls im Steuerstromkreis, der nur aktiv ist, wenn **R1 angezogen** hat (Zündung an, Killschalter ok). Die +12 V für die Starterrelais-Spule kommt vom Motor-Stopp-Relais-Ausgang über die Sicherung D (gemeinsamer Kreis mit Pumpe). Die Masse-Schaltung der Spule erfolgt über den **Starterknopf und den Kupplungsschalter/Leerlaufschalter**: Drückt der Fahrer den Anlasserknopf, wird der Stundenkreis der Spule gegen Masse geschlossen, **sofern entweder Leerlauf anliegt oder der Kupplungshebel gezogen ist**. Konkret ist in Reihe zum Startknopf noch der Kupplungsschalter geschaltet (bei eingelegtem Gang muss die Kupplung gezogen sein). Ist der Seitenständer ausgeklappt und ein Gang eingelegt, verhindert bereits R1 das Anlaufen – das Starterrelais bekommt dann keine Spannung. Die Kabelfarben: Die Spule von R3 erhält z.B. ein **Orange/Weiß** (oder **Braun/Gelb**) Kabel von der Sicherung D (geschaltetes Plus von R1), und der Abgang vom Starterknopf zur Masse ist häufig **Hellblau** oder **Gelb/Grün** (dieser geht über den Kupplungsschalter an Masse). Im Schaltplan der RSV Mille ist der Starterknopf-Stromkreis ebenfalls mit dem **Neutralanzeiger** und dem Diodenmodul verbunden, um Starten nur bei erfüllten Bedingungen zu erlauben.

**Schaltung & Pins:** R3 hat zwei große Anschlussklemmen (Schraubanschlüsse) für den **Schließerkontakt**: **Eingang** direkt von der Batterie (+12 V, über das dicke rote Batteriekabel, abgesichert durch die 30 A-Hauptsicherung) und **Ausgang** zum Anlasser (dickes Kabel zum Startermotor). Daneben besitzt es zwei kleinere Steckkontakte für die **Spule** (Steuerstrom): diese sind über einen 2-poligen Stecker mit dem Kabelbaum verbunden (meist zweifarbige dünnere Drähte, siehe oben). Wenn die Spule erregt wird, zieht der Schütz an und verbindet die beiden dicken Klemmen, wodurch der Anlasser dreht. Im Stromlaufplan ist das Starterrelais zwischen Sicherung D und Anlasser eingezeichnet.

**Position:** Das Starterrelais (R3) ist üblicherweise nicht im Relaiskasten, sondern separat nahe der Batterie montiert (oft an der Batteriehalterung oder Rahmen). Bei der RSV Tuono sitzt es im Heck rechts neben oder hinter der Batterie. Es ist an seinen zwei dicken Anschlusskabeln (Batteriekabel und Anlasserleitung) leicht zu erkennen.

## Integration ins Sicherheitssystem und Explosionszeichnung-Referenz

Alle drei Relais arbeiten zusammen, um den Start- und Kraftstoffkreislauf nur bei sicheren Betriebsbedingungen zu schließen. Das **Motor-Stopp-Relais (R1)** bildet dabei das zentrale **Sicherheits- und Abschaltglied** („Kill Relay“): Es erhält seine Steuerenergie über Zündschloss und Killschalter und wird durch Seitenständer- und Umfallsensor bedingt. Nur wenn R1 anzieht, erhalten **R2 (Pumpe)** und **R3 (Starter)** überhaupt Spannung. R2 wiederum wird von der ECU abhängig von Motordrehimpulsen aktiviert, und R3 nur durch den Startertaster bei eingelegtem Leerlauf oder gezogener Kupplung. Durch diese Staffelung stellen Zündschloss, Killschalter, Seitenständerschalter, Leerlaufschalter, Kupplungsschalter sowie der Neigungssensor gemeinsam sicher, dass die Kraftstoffzufuhr und der Anlasser **nur in sicheren Situationen** arbeiten. Im Schaltplan sind die Querbeziehungen ersichtlich – z.B. speist R1 die Sicherungen D und E für die nachfolgenden Stromkreise, und das Diodenmodul verknüpft Seitenständer- und Leerlaufsignal für die Start-/Stopplogik.

In der **Explosionszeichnung „Batterie – Pompa benzina – ECU“ (EasyParts)** sind die Komponenten im Heck der Maschine dargestellt. Man erkennt dort die Batterie und Massekabel, den Sicherungskasten, das Motorsteuergerät (ECU) sowie die Relais und die Kraftstoffpumpen-Einheit. Insbesondere sind R1 und R2 als zwei kleine Würfelrelais an der Halterung unterhalb der ECU zu sehen, während R3 (Starterrelais) als größeres Bauteil mit Anschlusskabeln in der Nähe der Batterie sitzt. Diese Darstellung erleichtert das Auffinden der Relais am Fahrzeug und zeigt deren räumliche Anordnung im Zusammenhang mit Pumpe, Batterie und Steuergerät.

**Quellen:** Die oben genannten Informationen sind dem Schaltplan der Aprilia RSV Tuono (Modell 2002–2005) und Wartungshandbüchern entnommen. Die Pinbelegung und Kabelfarben des Kraftstoffpumpensteckers sind durch Aprilia-Unterlagen und Erfahrungswerte bestätigt. Nennwerte des Tankgebers laut Aprilia Werkstatthandbuch. Die Relaisbeschaltung und Sicherheitslogik folgen der Werksdokumentation und dem Schaltplan (Sekundärsicherungen D & E, Diode-Modul). Diese technische Übersicht fasst die relevanten Details für die RSV Tuono 1000 IE (E2) zusammen und ordnet die Kabelfarben den jeweiligen Relais-Pins und Funktionen zu, um Fehlersuche und Verständnis des Sicherheitssystems zu erleichtern.


### 🔧 1. **Relaisblock bei Batterie/ECU**

- **Position**: Unter dem Sitz, direkt bei der Batterie, sind die drei relevanten Relais:
    - **Fuel Pump Relay**
    - **Engine-Stop Relay**
    - **Starter Relay**
- **Test**: Relais mit identischem danebenliegendem tauschen (z. B. Pumpe ↔ Starter). Wenn danach die Pumpe summt → Relais defekt.
- **Alternative**: Pumpe direkt bestromen (siehe Punkt 4) – läuft sie, liegt’s am Relais oder dessen Ansteuerung (ECU, Sicherheitsschaltungen).

---

### 🔌 2. **Pumpenstecker: 12 V bei Key-On?**

- **Stecker**: Unter dem Tank an der Kraftstoffleitung, meist 2-polig (Plus und Masse zur Pumpe).
- **Messen**:
    - Zündung **ein**, Benzinpumpe sollte kurz anlaufen (**„primen“**).
    - Prüfe zwischen beiden Kontakten auf 12 V.
    - Wenn **kein Strom**, Ursache in Relais, Sicherung, Seitenständer, Not-Aus oder ECU-Sperre.

---

### ⚡ 3. **Stromaufnahme prüfen (~3,9 A bei Lauf)**

- **Stromzange**: Um das Pluskabel zur Pumpe legen.
- **Messwert**:
    - **~3,9 A = normal**
    - **0 A = offen (Leitung, Relais, Unterbrechung)**
    - **>6 A oder keine Bewegung = blockierte Pumpe**
- Hinweis: Nur sinnvoll, wenn du 12 V anliegen hast und die Pumpe läuft oder laufen soll.

---

### 🔋 4. **Direktversorgung mit 12 V (abgesichert)**

- **Ziel**: Test, ob Pumpe mechanisch ok ist.
- **Vorgehen**:
    - Stecker zur Pumpe **abziehen**.
    - Mit einer **externen 12 V-Quelle (z. B. Batterie)** direkt auf die Pins gehen.
        - Achtung: **Sicherung 7,5–10 A** dazwischen schalten!
    - Pumpe sollte dann **hörbar laufen/summen**.
- Ergebnis:
    - **Pumpe läuft** → Ursache liegt in der ECU- oder Relaissteuerung.
    - **Pumpe läuft nicht** → Pumpe selbst defekt.

# Aprilia RSV Tuono 1000 (2002–2005) startet nicht: systematische Fehlersuche

## Executive Summary

Wenn die Kiste nicht startet, ist das in der Praxis fast immer **eins von drei Themen**: **(1) Spannung bricht beim Start ein (Batterie/Übergangswiderstände/Masse), (2) der Starterkreis schaltet nicht sauber (Starterrelais/Anlasser/Sprag), (3) ECU bekommt kein plausibles “Start-Freigabe”-Signal (Immobilizer/Sicherheitsschalter/RPM-Signal)**. Die Reihenfolge ist wichtig: **Erst Stromversorgung/Starterkreis sauber abklären**, _dann_ Zündung/Kraftstoff. Auf dem V990 brauchst du beim Starten richtig Strom – das Werkstatthandbuch nennt für den Startermotor **~120 A beim Start**. 

Die **schnellste, belastbare** Diagnose-Logik ist:

1. **Dash/Lichter normal?** → Wenn nein: Hauptsicherung, Batterie, Masse.
2. **Drückst du Start und es dreht NICHT (kein oder nur “Klack”)?** → Batterie unter Last + Starterrelais + Masse/Plus-Kabel prüfen (90% Trefferquote).
3. **Es dreht, aber zündet nicht (“orgelt”)?** → Immobilizer-Lampe, Pumpen-Prime, Zündfunke, RPM-Sensor (Kurbelwellensignal) priorisieren.
4. **Es dreht “frei”/Krach/Metall-Klonk?** → Sprag/Anlasserfreilauf und/oder Starterritzel/Mechanik.

**Sollwerte, die dir sofort sagen, ob die Richtung stimmt:**

- Batterie (allgemein): **~12,7 V** voll nach Standzeit; unter **12,4 V** ist sie nicht fit genug für Fehlersuche (und du jagst Geister). 
- Belastungstest: Standard-Load-Test gilt als “ok”, wenn nach 15 s bei 50% CCA die Spannung **> 9,6 V** bleibt. 
- Lade-/Reglersystem: im Werkstatthandbuch **13,8 V bei 4000 rpm** an den Batteriepolen. 
- Einspritzanlage: **3,5 bar Druck an den Injektoren** (Regler/Pressure-Referenz). 
- RPM-Sensor (Kurbelwellensignal): **0,7–1,1 kΩ** und beim Drehen **~1–2 V AC**. 
- Bank-Angle (Tip-Over): **~62 kΩ in Einbaulage**, **0 Ω bei 90° gekippt** (darf im Betrieb nicht “kippen”). 

Wichtig und direkt: Der V990 hat **keine Hydrostößel**. Ventilspiel wird über **Shims** eingestellt. Wenn Ventile zu eng sind (v. a. Einlass), startet er kalt schlecht bis gar nicht. Das Ventilspiel-Soll ist **Einlass 0,11–0,18 mm**, **Auslass 0,22–0,29 mm**. 

## Schnellcheck vor Ort

1. **Killswitch auf RUN**, Seitenständer hoch, Neutral-Lampe an (oder Kupplung ziehen).
2. **Batteriespannung nach Standzeit messen**: Ziel ~12,7 V; unter 12,4 V zuerst laden/ersetzen. 
3. **Spannung beim Startknopf messen** (Multimeter bleibt dran): fällt sie brutal ab (≈ <10 V), ist die Batterie/der Kontaktkram das Problem (nicht “die ECU”). (Load-Test-Referenz > 9,6 V @ 15 s/50% CCA). 
4. **Hauptsicherungen checken (2×30 A)** + Aux-Sicherungen (A–F). 
5. **Hörtest Zündung EIN**: Summt die Benzinpumpe kurz? Wenn nein: Pumpenkreis/Fuse D/I/ECU-Fault. (Fuel-pump faults sind im Diagnosesystem vorgesehen). 
6. **Starterrelais**: kommt beim Drücken ein klares “Klack”? Wenn ja, aber kein Drehen → Hochstromseite prüfen (Spannung _vor_ und _nach_ Relais).
7. **Masseband/Pluskabel**: wackeln → wenn Startverhalten sich ändert: Übergangswiderstand.
8. **Immobilizer-Lampe beobachten**: Blinkmuster “Key not recognised” = zuerst Schlüssel/Antenne, nicht Kraftstoff. 
9. **Zündfunke-Test an einer Kerze** (sauber gegen Masse): Wenn kein Funke → zuerst RPM-Sensor/ECU-Freigaben checken.
10. **Wenn sie orgelt, aber nicht anspringt**: Kerzen raus → sind sie nass (abgesoffen) oder trocken (kein Sprit)? Danach zielgerichtet weiter.

## Systematische Fehlersuche nach Symptomklasse

|Symptomklasse|Was das _meist_ ist|Was du als Erstes misst/prüfst|
|---|---|---|
|Tot: kein Dash/keine Kontrolleuchten|Hauptsicherung/ Batteriepol ab/ Masse ab|Batteriespannung, Hauptsicherungen 30 A (H/I)|
|Dash ok, Startknopf → nichts (nicht mal Klack)|Startfreigabe fehlt (Killswitch/Kupplung/Seitenständer/ECU) oder Steuerkreis|Killswitch, Kupplungsschalter, Seitenständer, ECU/Diag, Relais-Steuerspannung|
|Dash ok, Startknopf → Klack, aber Anlasser dreht nicht|Batterie bricht ein / Starterrelais Kontakte / Masse/Plus-Kabel|Batterie unter Last, Spannungsabfall über Relais/Kabel, Massepunkt|
|Anlasser dreht, Motor zündet nicht|Kein Sprit (Pumpe/3,5 bar fehlt) oder kein Zündsignal (RPM-Sensor) oder Immobilizer|Pumpen-Prime, Fehlercodes (Fuel pump o/c), Funke, RPM-Sensor 0,7–1,1 kΩ, AC 1–2 V|
|Anlasser “spinnt”, dreht frei / harte Klonks|Sprag (Anlasserfreilauf) / Mechanik|Geräuschbild + Sichtprüfung Startertrieb; bei schwacher Batterie oft “kaputt-georgelt” (Praxis)|

Minimal-Werkzeug, mit dem du 80% erschlägst: Multimeter, Starthilfekabel/Jump-Pack, 10er/13er Schlüssel, Kontaktspray + kleine Drahtbürste, Zündkerzenschlüssel.

## Fehlerquellen und kurze Lösungsansätze nach Systemen

Die Tabellen sind bewusst “Werkstatt-tauglich”: Symptom → Messung → Entscheidung. Priorität meint: **wie wahrscheinlich + wie schnell & billig**.

### Elektrische Versorgung, Sicherungen, Masse, Relais, Starterrelais

|Fehlerquelle|Symptome|Prüfung (Reihenfolge, Werkzeug, Sollwerte)|Schnelle Maßnahmen / Werkstatt-Kriterium|Prio|Zeit|
|---|---|---|---|---|---|
|Batterie schwach / hoher Innenwiderstand|Klackern, Display reset, langsames Orgeln|1) Ruhespannung nach Standzeit ~12,7 V; <12,4 V = erst laden.  2) Load-Test: >9,6 V nach 15 s @ 50% CCA.  3) Beachte: Starter zieht ~120 A.|Laden mit geeignetem Ladegerät; wenn Spannung unter Last einbricht → Batterie ersetzen. Wenn sie nach Laden rasch <12 V fällt: fertig, tauschen.|Hoch|5–20 min|
|Batteriepole/Schrauben locker/oxidiert|Alles “wirkt” ok, aber Start sporadisch|Sicht + “Wackeltest”; Spannungsabfall messen: Batterie + zu Relais Eingang, Batterie – zu Motormasse während Start|Reinigen, richtig festziehen, Polfett; Massepunkt blank machen|Hoch|10–20 min|
|Hauptsicherung(en) durch (H/I je 30 A)|Tot oder teils tot (kein Einspritz-/ECU-Leben)|Sicherungen H/I ziehen, durchmessen; sind 30 A.|Tauschen; wenn sofort wieder fliegt: Kurzschluss → nicht weiter probieren → Werkstatt/gezielte Fehlersuche|Hoch|5–10 min|
|Aux-Sicherungen A–F defekt|Bestimmte Verbraucher tot (Pumpe, ECU, Starterrelais etc.)|Fuse-Plan: D versorgt u. a. Speed sensor, **fuel pump**, relay, starter; E versorgt coils/injectors etc.|Richtige Sicherung ersetzen; wenn wieder fliegt → Kurzschluss/Stecker scheuert|Hoch|5–10 min|
|Masseband Motor/Frame hochohmig|Startrelais klackt, Starter lahm, Kabel warm|Spannungsabfall: Batterie– zu Motorgehäuse beim Start; alles >0,3–0,5 V Drop ist verdächtig (Praxis).|Masseband demontieren, blank machen, wieder fest; wenn Kabel/Lasche heiß: ersetzen|Hoch|15–30 min|
|Starterrelais (Leistungskontakte verbrannt)|Klack, aber kein/seltenes Drehen; ggf. ECU-Fault “Starter relay open”|1) Spannung vor/nach Relais beim Drücken; 2) ECU kann starter relay open/short-c als Fehler führen.|Relais ersetzen. Wenn Relais heiß wird oder “klebt”: sofort ersetzen (Brandrisiko).|Hoch|10–30 min|
|“Killswitch”/Stop-Schalter Kontaktproblem|Startknopf tot, manchmal geht’s|ECU sieht Stop switch als Digitaleingang.  Kontakt prüfen; evtl. Spannungsversorgung bricht über Schalter weg|Reinigen/mehrfach schalten; wenn intern oxidiert: ersetzen|Medium|10–30 min|
|Ladekreis/Regler/Stator lädt nicht → Batterie leer|Läuft nach Überbrücken, danach wieder tot; Spannung sinkt beim Fahren|Bei laufendem Motor: 13,8 V @ 4000 rpm Soll.  Stator: ~75 VAC @ 4000 rpm (abgezogen), Wicklung ~0,4 Ω (Handbuchwerte).|Wenn Laden mies: erst Stecker/Übergänge (siehe “brown connector”), dann Regler/Stator messen.|Hoch|20–60 min|

**Aprilia-typisch (und relevant für “startet nicht”)**: Der sog. **braune Stecker** im Ladekreis kann durch Widerstand heiß werden, “hochohmig” werden und dir die Batterie leerfahren; das ist in der Szene ein Klassiker. In einem praxisnahen Thread wird beschrieben, dass ein Stecker “hoch resistiv” werden kann und so Stator/Regler schädigt; außerdem: bei 500 W-Systemen läuft dauerhaft viel Strom, und schon kleine Übergangswiderstände führen zu Hitze/Meltdown. 

### Starter/Anlasser, Magnetschalter, Stromaufnahme, Kabel, Verschleiß

|Fehlerquelle|Symptome|Prüfung (Sollwerte)|Schnelle Maßnahmen / Werkstatt-Kriterium|Prio|Zeit|
|---|---|---|---|---|---|
|Anlasser selbst verschlissen (Bürsten/Lager)|Dreht schwer, extrem hoher Geräuschpegel, Spannung fällt, Kabel werden warm|Strommesszange: deutlich >120 A + langsame Drehzahl = mechanisch/elektrisch schwergängig (Handbuch nennt ~120 A Startaufnahme).|Anlasser ausbauen, am Bench testen; bei Verschleiß revidieren/ersetzen|Medium|60–180 min|
|Pluskabel Batterie → Starterrelais → Starter hochohmig|Relais klackt, Starter zu schwach|Spannungsabfall pro Segment messen unter Startlast|Kabelsatz/Ösen erneuern; Übergänge blank und fest|Hoch|20–60 min|
|Sprag/Anlasserfreilauf rutscht (“Anlasser dreht frei”)|Starter heult, Motor dreht nicht mit / “Klonk”/Metallgeräusche|Beobachtung + Geräuschbild; häufig nach vielen Startversuchen mit schwacher Batterie (“kaputt-georgelt”).|Nicht weiter orgeln. Das ist dann mechanisch: Sprag/Trieb. Werkstatt oder sauberer Eigenjob.|Medium|Diagnose 10 min|

## Zündsystem, Impulsgeber, ECU/Fehlercodes

|Fehlerquelle|Symptome|Prüfung (Werkzeug/Sollwerte)|Schnelle Maßnahmen / Werkstatt-Kriterium|Prio|Zeit|
|---|---|---|---|---|---|
|Zündkerzen defekt/abgesoffen|Orgeln ohne Zündung; Kerzen nass/schwarz|Kerzentyp/Gap: NGK DCPR9E, 0,6–0,7 mm.  Funkenprobe gegen Masse|Kerzen trocknen/ersetzen; wenn ständig nass: Fuel/Startlogik prüfen|Medium|15–30 min|
|Zündspulen defekt oder Steckkontakt|Kein/inkonsistenter Funke|Primärwiderstände 0,40–1,15 Ω (Handbuch).  Stecker/Kabel prüfen|Stecker reinigen; Spule tauschen wenn klar außerhalb Spec oder temp.-abhängig ausfällt|Medium|20–60 min|
|RPM-Sensor (Kurbelwellensignal) defekt / Kabelbruch|Dreht, aber springt nicht an; ggf. Fehler “Engine rpm signal missing (P0336)”|Widerstand **0,7–1,1 kΩ**, Output **1–2 V AC** beim Drehen.  Fehlerlogik: “engine does not start if error present” nach mehreren Versuchen.|Steckverbindung prüfen (Öl/Schmutz), Kabel auf Scheuerstellen; wenn Werte falsch: ersetzen|Hoch|20–45 min|
|Camshaft sensor fehlt|Oft startet er trotzdem (Notlauf), aber Fehler wird gesetzt|Handbuch: Hall-Sensor, 12 V Supply, Square-wave Output.|Nicht primär, wenn _gar nichts_ startet; nach RPM-Sensor prüfen|Niedrig|20–45 min|
|ECU meldet “Battery voltage low/high”, “ECU not initialised”, CAN-line Fehler|Startfreigabe spinnt, Warnlampen odd|Fehlerseite im Diagnosesystem: Battery voltage low/high, ECU not initialised, CAN line.|Erst Batterie/Kontakte fixen; ECU-Initialisierung/Mapping nur wenn sauberer Strom vorhanden|Medium|30–120 min|

## Kraftstoffsystem, Einspritzung, Druck, Filter

|Fehlerquelle|Symptome|Prüfung (Werkzeug/Sollwerte)|Schnelle Maßnahmen / Werkstatt-Kriterium|Prio|Zeit|
|---|---|---|---|---|---|
|Benzinpumpe läuft nicht an|Kein Summen bei Zündung EIN; kein Start|ECU/Fault: “Fuel pump o/c” (open circuit/earthed) oder “Fuel pump short-c”.  Sicherung D + Hauptsicherung I prüfen (Injection loads).  Pumpenstrom im Handbuch: **~3,9 A**.|Stecker/Leitung am Tank prüfen; wenn Pumpe tot: ersetzen|Hoch|15–60 min|
|Zu wenig Kraftstoffdruck / Filter zu|Springt kurz an und stirbt; zündet nicht trotz Funke; mageres “Patschen”|Druckreferenz: **3,5 bar an den Injektoren**.  Druckmessung nur mit passendem Adapter/Gauge sinnvoll|Filter/Leitungen prüfen; bei Druckthemen: Werkstatt oder sauberes Mess-Setup|Medium|30–120 min|
|Injektoren elektrisch offen / Steckproblem|Dreht, kein Start; Kerzen trocken|Injektorwiderstand **13,8–15,2 Ω**; Versorgung 12 V.|Stecker, Kabel, Sicherung E (injectors/coils) prüfen.|Medium|20–60 min|
|Kraftstoff alt / Wasser im Sprit|Startet schlecht, läuft rau, stirbt; nach Standzeit schlimmer|Wenn der Sprit lange steht: Geruch/Farbe; bei Zweifel ablassen/erneuern|Herstellerempfehlung (allgemein): Kraftstoff möglichst innerhalb ~30 Tage verbrauchen (für konstante Volatilität), sonst stabilisieren.|Medium|30–90 min|

## Luftansaugung, Kompression, Ventiltrieb, mechanische Ursachen

|Fehlerquelle|Symptome|Prüfung|Schnelle Maßnahmen / Werkstatt-Kriterium|Prio|Zeit|
|---|---|---|---|---|---|
|Luftfilter komplett zugesetzt / Airbox Problem|Startet, nimmt kein Gas, stirbt|Sichtprüfung Airbox/Filter|Reinigen/Filter ersetzen|Niedrig|15–30 min|
|Bank angle / Tip-over Sensor falsche Lage/defekt|Motor wird “abgeschnitten”, manchmal kein Start|Widerstand: **62 kΩ in Einbaulage**, **0 Ω bei 90°**.  Montagehinweis: soll Motor bei Umkippen abschalten.|Richtig montieren; wenn Werte spinnen: ersetzen|Medium|15–30 min|
|Stepper Motor (Kaltstart/Leerlaufsteller) hängt|Startet kalt mies oder dreht sofort absurd hoch|Phase Resistance **50 Ω**.|Stecker prüfen; Reinigung/Diagnose per Tester sinnvoll|Niedrig|30–90 min|
|Ventilspiel zu eng (keine Hydros!)|Kaltstart schlecht, warm besser; ungleichmäßige Kompression|Ventilspiel-Soll: **Einlass 0,11–0,18 mm**, **Auslass 0,22–0,29 mm**; Shims tauschen wenn außerhalb.|Das ist Werkstatt-/Shim-Job. Wenn du’s nicht routiniert machst: Werkstatt.|Medium|3–8 h|
|Niedrige Kompression / große Differenz v/h|Orgeln ohne Anspringen; “pufft”|Kompression messen (warm wäre ideal). Praxiskriterium: **beide Zylinder nahe beieinander (≤10% Unterschied)**; absolute Werte schwanken stark je nach Tester. (Community sieht oft ~14 bar bei gesunden V990, Kontext beachten.)|Wenn Differenz groß: Leakdown/Mechanik → Werkstatt|Niedrig–Medium|1–2 h|
|Steuerzeiten/Timing-Kette übergesprungen (selten, aber hart)|Backfire in Airbox, keine Kompression, ungewöhnliche Geräusche|Nur mechanisch sauber prüfbar (Deckel/Marken)|Nicht weiter starten → Folgeschäden vermeiden → Werkstatt|Niedrig|2–6 h|

## Sicherheitsunterbrechungen, Immobilizer, ECU-Diagnose und Flowchart

### Sicherheitsschalter & Startfreigaben

Diese Tuono hängt die Startlogik stark an ECU/Instrument. Das Handbuch beschreibt u. a.:

- ECU sieht **Seitenständer**, **Kupplung**, **Stop-Schalter** als Digitaleingänge. 
- Bei CAN-Problemen kann das Kombiinstrument Symptome zeigen (Warnlampen an, Neutral aus, Spannung “9.0V”, Temp “Err”). 
- Starten wird nur freigegeben, wenn ECU das V990-Modell über ein CAN-Acknowledge vom Instrument erkennt. 

**Pragmatischer Check**: Wenn Neutral-/Seitenständer-Anzeige “komisch” ist oder das Dash offensichtlich Unsinn zeigt, jag nicht Benzinpumpe und Kerzen – **CAN/Instrument/Stecker zuerst**.

### Wegfahrsperre/Immobilizer

Das Handbuch ist eindeutig: **ohne korrekt erkannten Transpondercode kein Start.**   
Diagnose über die Immobilizer-LED:

- aus = Immobilizer off
- blinkt ~alle 3 s = “armed”/Diebstahlschutz aktiv
- blinkt ~jede 1 s = **Key not recognised** 

Messwert: Immobilizer-Antenne **~14 Ω**.   
Neue Schlüssel anlernen: laut Handbuch nur mit **Master Key/Authorised Dealers** (also: Werkstatt). 

### ECU-Fehlercodes / Diagnose

Das System kennt explizite Fehlereinträge, die für “startet nicht” Gold sind:

- Fuel pump o/c / short-c 
- Engine rpm signal missing (P0336) inkl. Hinweis, dass der Motor bei vorhandenem Fehler nach mehreren Startversuchen **nicht startet** 
- Battery voltage low/high 
- Starter relay open/short-c 
- CAN line fault 

Für “Enable devices” (Pumpe, Injektoren, Spulen etc.) ist im Handbuch die Nutzung eines Diagnosetesters vorgesehen. 

### Vereinfachte Schaltlogik als Skizze

**Hochstrompfad (dreht der Starter?):** Batterie (+) → Hauptsicherung(en) → Starterrelais (Kontakt) → Startermotor → Motormasse → Batterie (–).  
(Handbuchdaten: Starteraufnahme ~120 A). 

**Steuerpfad (darf er starten?):** Startknopf/Killswitch/Sicherheitsschalter → ECU → Starterrelais (Steuersignal) → Relais zieht an.

### Mermaid-Flowchart zur Fehlersuche

mermaid

Kopieren

```
flowchart TD
  A[Zündung EIN] --> B{Dash/Lampen normal?}
  B -- Nein --> B1[Batterie + Hauptsicherungen + Masse prüfen]
  B -- Ja --> C{Immobilizer "Key not recognised"?}
  C -- Ja --> C1[Spare Key, Antenne/Stecker, 14Ω prüfen; Dealer falls Key-Anlernen]
  C -- Nein --> D{Startknopf: Anlasser dreht?}
  D -- Nein --> D1{Hört man Starterrelais-Klick?}
  D1 -- Nein --> D2[Startfreigaben: Killswitch, Seitenständer, Kupplung/Neutral, Steuerkreis]
  D1 -- Ja --> D3[Batterie unter Last + Spannungsabfall über Relais/Kabel + Masse; Relais testen/ersetzen]
  D -- Ja --> E{Benzinpumpe primt kurz?}
  E -- Nein --> E1[Sicherung D/I, Pumpenkreis, ECU-Fault "Fuel pump o/c", Pumpenstrom ~3.9A]
  E -- Ja --> F{Zündfunke vorhanden?}
  F -- Nein --> F1[RPM-Sensor 0.7-1.1kΩ + 1-2VAC; Spulen 0.40-1.15Ω; ECU-Faults]
  F -- Ja --> G{Kerzen nass?}
  G -- Ja --> G1[Abgesoffen: Pause, Kerzen trocknen; nicht endlos orgeln (Sprag-Risiko)]
  G -- Nein --> H[Spritdruck/Filter: 3.5 bar Referenz; Injektorwiderstand 13.8-15.2Ω; Kompression/Mechanik]
```

## Referenzwerte und Messmethoden, die sich bewährt haben

- **Batterie-Kapazität laut Handbuch:** 12 V – 10 Ah. 
- **Ruhespannung (Orientierung):** ADAC gibt für 100% Ladezustand ~12,70 V (Konventionell) und zeigt, dass <12,0 V “muss geladen werden” ist. 
- **Belastungstest:** Yuasa beschreibt den Standard-Load-Test (50% CCA für 15 s) und bewertet die Batterie als “ok”, wenn sie **>9,6 V** bleibt. 
- **Starteraufnahme:** ~120 A beim Start (V990). 
- **Ladespannung:** 13,8 V @ 4000 rpm an den Batteriepolen. 
- **Stator/Gererator:** 75 VAC @ 4000 rpm (abgeklemmt), Wicklungen ~0,4 Ω. 
- **RPM-Sensor:** 0,7–1,1 kΩ; Output 1–2 V AC beim Drehen. 
- **Injektor:** 13,8–15,2 Ω; Druckreferenz 3,5 bar. 
- **Zündspulen:** 0,40–1,15 Ω (Handbuchmesspunkte). 
- **Bank-Angle:** 62 kΩ normal / 0 Ω bei 90°. 
- **Ventilspiel:** Einlass 0,11–0,18 mm; Auslass 0,22–0,29 mm. 
- **Wichtig zu Kälte & Batterie:** ADAC betont, dass im Winter durch Verbraucher und Temperatur die Ladungsbilanz schlechter wird und Batterien bei Minusgraden langsamer laden/mehr Probleme machen. 
- **Kraftstoffalter:** Briggs & Stratton empfiehlt allgemein, Kraftstoff in Mengen zu kaufen, die innerhalb **~30 Tage** verbraucht werden, um die “fuel freshness and volatility” zu behalten. 
- **Tip-Over Switch als reale Ursache:** AP Workshops beschreibt den Sinn der Tip-Over-Funktion: Motor wird bei Umkippen abgeschaltet; falsche Montage = unnötige No-Start-Themen. 

Wenn du mir sagst, **welches Symptom es bei dir exakt ist** (tot / klack / orgelt / dreht frei) und welche **Spannungen du gemessen hast** (Ruhespannung + Startknopf-Minimum), können wir das Ganze auf 3–5 konkrete Prüfungen runterbrechen und du musst nicht “auf Verdacht” Teile tauschen.

# Gabelölwechsel bei der Aprilia RSV Tuono 1000 (2002–2005)

## Anleitung: Gabelöl wechseln ohne Ausbau der Gabelholme

Ein vollständiger Gabelölwechsel lässt sich grundsätzlich auch bei eingebauten Gabelholmen durchführen. Zwar ist für einen _kompletten_ Service (mit Reinigung aller Komponenten) das Ausbauen und Zerlegen der Gabel empfehlenswert, doch ein einfacherer Ölwechsel ist **ohne Ausbau** möglich. Wichtig ist dabei sorgfältiges Arbeiten, um beide Holme gleichmäßig und sauber zu befüllen. Gehen Sie in etwa wie folgt vor:

1. **Motorrad sichern und entlasten:** Stellen Sie die Aprilia auf einen **Montageständer** (vorn an der Gabelbrücke oder zentral unterm Motor), sodass das Vorderrad entlastet ist. Das Bike muss **senkrecht und stabil** stehen, damit das Öl gleichmäßig ablaufen kann und beim Befüllen beide Holme exakt gleich befüllt werden können.
2. **Vorbereitung an der Gabel:** Lösen Sie oben an den Gabelbrücken die Klemmungen (nur leicht, damit sich die Stopfen drehen lassen) und schrauben Sie dann **die Gabelstopfen (Gabelkappen) oben** vorsichtig heraus. Achtung: Eventuelle Vorspannung der Gabelfedern vorher ganz herausdrehen, dann stehen die Kappen nicht unter Federdruck. Legen Sie Lappen um die Öffnungen, um Lack und Verkleidung vor Öl zu schützen.
3. **Altes Öl ablassen:** Es gibt nun zwei Methoden, um das alte Öl im eingebauten Zustand abzulassen:
    - **Ablassen über die unteren Ventile:** Am **unteren Ende** der Gabelholme sitzen die **Schrauben der Druckstufendämpfung** (Inbusschrauben/Sechskant mit Einstellschraube). Drehen Sie zuerst die **Druckstufen-Einstellschraube** ganz heraus (merken Sie sich zuvor die Klicks/Umdrehungen) – so steht das Nadelventil offen. Anschließend können Sie mit einem Schlüssel (z.B. 14 mm) den **gesamten Ventileinsatz** unten herausschrauben. Halten Sie ein Auffanggefäß bereit und lassen Sie das alte Gabelöl **vollständig auslaufen**. Durch das Öffnen der oberen Stopfen strömt Luft nach und erleichtert das Ablaufen.
    - **Ablassen durch Auspumpen von oben:** Alternativ (falls Sie den unteren Ventileinsatz nicht entfernen wollen) können Sie das Öl auch durch die obere Öffnung absaugen oder **auspumpen**. Dazu die **Gabelfeder entnehmen** (Gabel weit ausfahren, Feder herausheben) und den Holm mehrmals langsam zusammen- und auseinanderziehen. Dadurch wird Öl nach oben befördert und kann z.B. mit einer großen Spritze/Schlauch abgesaugt oder vorsichtig ausgekippt werden. Diese Methode ist allerdings etwas unordentlicher und u.U. bleibt mehr Restöl im System zurück – sofern möglich, ist das **Ablassen über die unteren Schrauben** vorzuziehen.
4. **Altes Öl vollständig entfernen (Spülen):** Nachdem das Öl abgelaufen ist, sollten Sie die letzten Reste und Ablagerungen _ausspülen_. Dazu etwas **frisches dünnes Gabelöl** (oder spezielles Gabelreinigungsöl) in jeden Holm geben, die Gabel mehrmals langsam durchpumpen und das Spülöl wiederum ablaufen lassen. Wiederholen Sie dies ggf. mehrmals, bis die austretende Flüssigkeit relativ klar ist. Beachten Sie, dass ohne komplettes Zerlegen nicht sämtlicher _Schmodder_ (Abrieb, Schmutz, Feuchtigkeit) entfernt wird; wirklich hartnäckige Ablagerungen sitzen unten im Dämpfungseinsatz und lassen sich nur durch Demontage und manuelles Reinigen (z.B. mit Bremsenreiniger und Lappen) entfernen. Ein Spülvorgang verbessert aber die Situation deutlich.
5. **Gabel wieder verschließen und neu befüllen:** Schrauben Sie nun die **unteren Ventile** wieder ein (mit neuer Dichtung falls vorhanden) und ziehen Sie sie vorsichtig _snug_ fest. Drehen Sie die Druckstufen-Einsteller zurück in ihre ursprüngliche Position. Anschließend **befüllen Sie von oben** pro Holm das _vorgesehene frische Gabelöl_. Starten Sie mit einer etwas geringeren Menge (z.B. ~400 ml) und **entlüften Sie die Gabel**: dazu die Holme mehrfach langsam ganz eintauchen und ausfahren, damit das Öl in alle Kammern (auch ins Cartridge) gelangt und eingeschlossene Luftblasen entweichen. Nun **Gabel **komplett** einfedern** (ggf. Feder dazu entfernen) und den **Ölstand (Luftpolster)** exakt einstellen (Details dazu siehe Abschnitt _Ölmenge und Luftpolster_ unten). Zum Schluss Federn (sofern ausgebaut) wieder einsetzen, Gabelkappen aufschrauben und alle gelösten Klemmschrauben mit Drehmoment anziehen.

**Hinweis:** Ein solcher Ölwechsel im eingebauten Zustand ist als **„quick & dirty“-Methode** praktikabel, um z.B. testweise eine andere Ölviskosität zu probieren oder das Öl nach längerer Zeit zu tauschen. Allerdings ersetzt er keine komplette Gabelrevision. Bei sehr alter Gabel (viele Jahre/hohe Laufleistung) ist es ratsam, die Holme einmal auszubauen, zu zerlegen und gründlich zu reinigen (inkl. Tausch der Dichtringe), da sich über Jahre einiges an Ablagerungen festsetzt. Für den **regelmäßigen Wartungsintervall** (oft ca. alle 2 Jahre oder ~20.000 km) genügt jedoch meist der beschriebene Ölwechsel.

## Empfohlenes Gabelöl (Hersteller & Viskosität)

Aprilia schreibt für die originale Showa-USD-Gabel ein **Gabelöl der Viskosität SAE 7.5W** vor. Im Handbuch wird als Referenz **AGIP (eni) Fork 7.5W** genannt – dieses Öl hat eine kinematische Viskosität von etwa ~35 cSt und ist ein guter Ausgangspunkt für die Serienabstimmung. In der Praxis haben sich jedoch verschiedene hochwertige Gabelöle bewährt, je nach gewünschtem Ansprechverhalten:

- **Motul Fork Oil Factory Line 5W (Light):** Ein synthetisches Ester-Gabelöl, speziell entwickelt für moderne **Showa USD-Gabeln**. Ein 5W-Öl von Motul (oder ähnlicher Qualität) hat in der Regel etwas geringere Viskosität als das originale 7.5W und kann das Ansprechverhalten auf kleine Unebenheiten verbessern. Viele Fahrer der RSV/Tuono verwenden 5W-Öl, da 10W ihnen zu straff erscheint. Motul bietet zudem ein **Fork Oil 10W (Medium)** an – durch Mischen von 5W und 10W im Verhältnis 1:1 kann man rechnerisch ~7.5W erzielen, falls 7.5W als Fertigmischung nicht verfügbar ist.
- **Öhlins Fork Oil 5W (oder 7.5W):** Öhlins bietet sehr hochwertige Gabelöle an. Das **Öhlins 5W** hat etwa ~19 cSt (also dünner als viele andere 5W) und wurde für Öhlins-Gabeln entwickelt, kann aber auch in Showa-Gabeln verwendet werden, wenn ein sehr sensibles Ansprechen gewünscht ist. Für etwas mehr Dämpfung kann man alternativ Öhlins 10W (ca. 47 cSt) mischen oder ein **7.5W-Öl** eines anderen Herstellers wählen.
- **Andere bewährte Marken:** **Liqui Moly** (Fork Oil 5W / 10W), **Bel-Ray** (High Performance Fork Oil 5W, 7W, 10W) oder **Castrol Fork Oil 10W** sind ebenfalls verbreitet. Wichtig ist weniger der Markenname als die passende **Viskosität**: Experten empfehlen für die Showa-Gabel ein Öl mit ca. **30–35 cSt** @40°C (entspricht in etwa einem mittleren 5W bis leichten 10W, je nach Hersteller). Die **W-Angabe ist nicht genormt** und kann zwischen Herstellern variieren; daher orientiert man sich am besten an bekannten Produkten. Beispielsweise liegt Motul Factory Line **5W** bei ~15 cSt (recht dünn), während man für ~35 cSt eher ein „7.5W“ oder dünnes 10W benötigt. Oft hilft es, Erfahrungsberichte zu lesen: So wurde z.B. bei einer SL1000 Falco (gleiche Gabel) das ab Werk eingefüllte Showa 10W-Öl als zu zäh empfunden – nach dem Wechsel auf **5W** war die Gabel deutlich schluckfreudiger, mit weniger hartem Rebound-Dämpfungsverhalten.

**Zusammengefasst:** Für **Sport und Alltag** mit seriennaher Abstimmung hat sich **SAE 5W** von einem hochwertigen Hersteller als Verbesserung des Ansprechverhaltens bewährt. Wer jedoch eher straffere Dämpfung bevorzugt (z.B. bei **stärkeren Gabelfedern** oder häufigem **Soziusbetrieb/Trackdays**), kann auch zu einem **7.5W–10W** Öl greifen. In jedem Fall sollten **beide Holme mit exakt demselben Öl** befüllt werden. Unterschiedliche Ölsorten oder -alter zwischen linkem/rechtem Holm führen zu ungleichmäßigem Dämpfungsverhalten und sind zu vermeiden.

## Spülen der Gabel – ist das sinnvoll?

**Ja, Spülen kann sinnvoll sein**, vor allem wenn die Gabel längere Zeit nicht gewartet wurde oder das Öl stark verschmutzt ist. Beim Spülen geht es darum, **möglichst das gesamte alte Öl und abgesetzte Rückstände** (Abriebpartikel, Kondenswasser-Schlamm, etc.) aus der Gabel zu entfernen, bevor neues Öl eingefüllt wird. Vorgehen und Hinweise zum Spülen:

- **Spülmedium:** Am einfachsten nimmt man dazu etwas **frisches Gabelöl niedriger Viskosität** (z.B. das gleiche Öl, das man einfüllt, oder ein sehr dünnes „0W“-Stoßdämpferöl). Alternativ wurde früher auch mit **Petroleum oder Diesel** gespült – davon raten aber viele ab, da Lösungsmittel Gummidichtungen angreifen können. Wenn Sie doch Petroleum verwenden, achten Sie darauf, **alle Reste vollständig zu entfernen** und nicht zu lange einwirken zu lassen. **Bremsenreiniger** ist nur bei komplett zerlegter Gabel zu empfehlen, da er sehr stark entfettet (wenn verwendet, anschließend Teile leicht einölen).
- **Vorgehen beim Spülen:** Nachdem das alte Öl abgelaufen ist, füllen Sie **eine kleine Menge (z.B. 50–100 ml) Spülöl** in jeden Holm und betätigen die Gabel mehrmals über den gesamten Federweg. Dadurch gelangt das Spülöl in alle Bereiche und bindet Schmutz. Lassen Sie dann das Spülöl ablaufen und begutachten Sie die Farbe. Diesen Vorgang können Sie **mehrfach wiederholen**, bis das ablaufende Öl **relativ klar** herauskommt. Eine Werkstatt spült ausgebauten Gabelholme oft im Teilewaschgerät und mit Druckluft, aber im Heimgebrauch reicht _Durchpumpen_ und Ablaufenlassen.
- **Grenzen des Spülens:** Beachten Sie, dass ohne das Cartridge/Dämpfungselement auszubauen **ein Rest an Ablagerungen** in der Gabel verbleiben kann. Insbesondere _unter_ dem Dämpfungskolben und in Ecken des Gabelfußes können Schmutzreste haften bleiben, die durchs Spülen allein nicht vollständig herauskommen. Das ist jedoch meist unkritisch, solange der Großteil des alten Öls und Schlamms entfernt wurde. Spülen verbessert die Ölqualität im System deutlich, ersetzt aber **keine Grundreinigung**. Wenn die Gabel z.B. aufgrund undichter Simmerringe ohnehin zerlegt wird, sollten alle Komponenten gründlich gereinigt werden (mit Lappen und z.B. Isopropanol/Bremsenreiniger). Für den routinemäßigen Ölwechsel genügt jedoch das beschriebene Ausspülen mit frischem Öl.

**Fazit:** Spülen ist beim Gabelölwechsel **empfehlenswert**, vor allem wenn die Gabel lange nicht geöffnet wurde. Es kostet etwas extra Öl und Zeit, erhöht aber die Chance, dass **kein altes Restöl** das frische Öl verunreinigt. So bleibt die Dämpfung gleichmäßiger und das neue Öl hält länger seine Performance.

## Ölmenge und Luftpolster einstellen

Bei der RSV Tuono (Showa-Gabel) wird die **Ölmenge pro Holm** mit rund **520 ml** angegeben, allerdings ist dieser Wert ein Richtwert für komplett trockene, leere Gabeln. Wichtiger als die Milliliter-Angabe ist das **exakte Einstellen des Ölstandes (Luftpolsters)** in jedem Holm, damit links und rechts identisch viel Öl eingefüllt ist und die Gabel symmetrisch arbeitet. Gehen Sie folgendermaßen vor:

- **Vorgegebener Ölstand:** Laut Aprilia-Werkstatthandbuch soll der Ölstand bei der Showa-Telegabel bei etwa **120 mm Luftpolster** liegen. Das bedeutet: bei vollständig _eingefedertem_ Holm (Gabel ganz zusammengedrückt) und **ohne Feder** soll der Abstand vom oberen Rohrende bis zum Ölspiegel 120 mm betragen (± ein paar mm Toleranz). Einige Handbücher nennen einen Wert von ~85 mm _mit_ eingesetzter Feder – das entspricht in etwa dem gleichen Luftpolster, da die Feder im Öl steht und Volumen verdrängt. Zur Sicherheit misst man aber üblicherweise **ohne Feder**, da so exakter und reproduzierbarer.
- **Messung des Luftpolsters:** Um den Ölstand korrekt zu messen, muss die Gabel **komplett eingefedert** sein. Im ausgebauten Zustand drückt man den Holm ganz zusammen; im eingebauten Zustand kann man das Motorrad vorne verzurren/absenken oder die Feder entnehmen. Verwenden Sie am besten einen **Ölstandsmesser** (Spritze mit Messrohr) oder einen **Meterstab**/Zollstock. Messen Sie vom Rand des Standrohres senkrecht nach unten bis zum Ölspiegel. Ist der Wert zu niedrig (Luftpolster zu groß), füllen Sie etwas Öl nach; ist der Wert zu klein, saugen Sie etwas Öl ab. Arbeiten Sie mit Ruhe, bis in beiden Holmen **genau derselbe Ölstand** erreicht ist.
- **Ölmenge in ml:** Zur Orientierung: Ein Luftpolster um 120 mm entspricht bei der Showa-Gabel ungefähr **450–500 ml Öl pro Holm** (je nach komplett trocken vs. noch Restöl). In einem Praxisbeispiel kamen etwa **460 ml** pro Holm zum Einsatz, um ~60 mm Luftpolster mit Feder zu erzielen (entspricht ~120 mm ohne Feder). **Race-Tech** empfiehlt für diese Gabel (bei sportlicher Abstimmung) sogar nur **80 mm Luftpolster** mit 5W-Öl – dies würde rund **500+ ml** erfordern und ergibt eine progressivere Dämpfung im letzten Federwegsdrittel (mehr Öl = kleineres Luftpolster = mehr Luftfederwirkung). Für die Straße und Originalfeder ist das jedoch nicht nötig. Halten Sie sich am besten an die Herstellerangabe (~120 mm ohne Feder) oder ggf. an erprobte Werte aus Foren, wenn Sie das Setup leicht anpassen möchten.

**Zusammenfassend:** Pro Gabelholm werden etwa **0,5 Liter Gabelöl** benötigt. Entscheidend ist, den **Ölstand exakt per Luftpolster** einzustellen – beide Seiten gleich und auf den Sollwert. Eine Abweichung von ein paar Millimetern ist tolerabel, aber größere Unterschiede beeinflussen die Feder-Dämpfer-Charakteristik. Nehmen Sie sich für das Einstellen des Ölstands Zeit; es ist der letzte wichtige Schritt, bevor die Gabel wieder verschlossen wird. Mit korrektem Ölstand und frischem, passendem Gabelöl wird Ihre Tuono-Gabel wieder straff und fein ansprechen!

**Quellen:** Motorrad-Foren und technische Unterlagen (Aprilia Werkstatthandbuch, Louis/Heavy Tuned Datenbank etc.) wurden zur Ermittlung der Angaben herangezogen. Insbesondere Erfahrungsberichte aus der Aprilia-Community lieferten hilfreiche Tipps zum Ölwechsel ohne Ausbau, zur Wahl der Ölviskosität und zur Bestimmung von Ölmenge/Luftpolster. Diese Informationen sowie bewährte Produktempfehlungen (Motul, Öhlins, AGIP etc.) sorgen dafür, dass der Gabelölwechsel auch in DIY-Durchführung gelingt. Viel Erfolg beim Schrauben!