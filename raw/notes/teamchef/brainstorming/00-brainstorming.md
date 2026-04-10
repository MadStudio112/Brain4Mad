# 00 - Brainstorming

## Kurzbeschreibung

TEAMCHEF ist eine Web Applikation zur Bewertung von Skills bzw. Fähigkeiten im
Fußball. Benutzer können Sportler anhand von maximal 5 Leistungskriterien bewerten.
Schwarmintelligenz führt zu objektiven Leistungsbewertungen. Um Benutzern Anreiz
zur Bewertung zu geben, wird ein Gewinnspiel veranstaltet, bei dem der Gewinner
dem Durchschnitt am nächsten kommt. Es wird ein Ranking erstellt und Gewinne
werden nach dem Spiel, Turnier oder Saison verliehen.

## Namensgebung

Ich denke, "Skillers.app" ist ein kurzer, prägnanter und einprägsamer Name für
die Anwendung. Es klingt technologisch und modern, was gut zu einer
Bewertungsplattform passt. Es ist einfach zu merken und kann leicht verbreitet
werden. Insgesamt denke ich, dass es ein guter Name für die Anwendung ist.

## Struktur der App

Eine mögliche Struktur für die App könnte folgendermaßen aussehen:

1. Startseite: Hier kann der Benutzer eine Sportart aus einer Liste mit den
   meisten Fan-Interessen weltweit auswählen.
2. Land-Auswahl: Nachdem die Sportart ausgewählt wurde, kann der Benutzer das
   Land auswählen, in dem die Liga stattfindet.
3. Liga-Auswahl: Hier kann der Benutzer die Liga auswählen, die er interessiert.
4. Mannschaft-Auswahl: Hier kann der Benutzer eine Mannschaft auswählen, die er
   bewerten möchte.
5. Spieler-Auswahl: Hier kann der Benutzer entscheiden, ob er eine Mannschaft
   oder einzelne Spieler bewerten möchte.
6. Bewertung: Hier kann der Benutzer die Mannschaft oder die Spieler nach den
   Leistungskriterien bewerten.
7. Ergebnisse: Hier werden die Bewertungen aller Benutzer angezeigt und ein
   Ranking erstellt.

Diese Struktur sollte einfach und intuitiv zu bedienen sein, so dass der
Benutzer möglichst schnell seine Bewertung abgeben kann. Außerdem sollte das
Design ansprechend und modern sein, um die Aufmerksamkeit der Benutzer zu
gewinnen und das Interesse am Gewinnspiel zu wecken.

- Startseite mit Erklärung der Regeln und Automatische Sprachauswahl
  (basierend auf Browsereinstellungen)
- Benutzerregistrierung mit dem Plugin "Ultimate Member"
- Auswahl der Sportart
- Auswahl des Wettbewerbs (Liga, Turnier, etc.)
- Auswahl der Mannschaft
- Bewertung der Mannschaft
- Speicherung der Bewertungen in der Datenbank
- Anzeige der aktuellen Rankings
- Verwendung von Charts.js für die Datenvisualisierung
- Option zur Anzeige des eigenen Rankings
- Integration eines Gewinnspiels mit Belohnungen für die nächsten Bewertungen.

## Sportarten

Es gibt eine Vielzahl von Sportarten, die weltweit ein großes Faninteresse
aufweisen, aber hier sind einige der Sportarten, die als die mit dem meisten
Faninteresse angesehen werden:

1. Fußball: Fußball ist ohne Zweifel einer der populärsten Sportarten weltweit
   und hat eine enorme Anzahl von Anhängern und Fans.
2. Basketball: Basketball hat eine starke Fanbasis in Nordamerika, aber auch
   in anderen Teilen der Welt, insbesondere in Asien.
3. Cricket: Cricket ist besonders in Indien, Pakistan, Sri Lanka und England
   sehr beliebt.
4. Tennis: Tennis hat eine große und loyale Fanbasis in vielen Teilen der Welt,
   insbesondere in Europa und Nordamerika.
5. Volleyball: Volleyball ist ein sehr populärer Sport, insbesondere in Asien
   und Europa.

Dies sind nur einige der Sportarten, die weltweit ein großes Faninteresse
aufweisen. Es hängt jedoch auch davon ab, welche Region man betrachtet, da jede
Region ihre eigenen bevorzugten Sportarten hat.

Top 10 Sportarten mit den meisten Faninteressen weltweit:

1. Fußball (Soccer)
2. Basketball
3. Cricket
4. American Football
5. Rugby
6. Tennis
7. Volleyball
8. Tischtennis
9. Baseball
10. Handball.

## Bewertungsmethode

Eine Bewertung kann auf verschiedene Arten stattfinden, aber es ist wichtig,
eine einheitliche Bewertungsmethode zu wählen, um Vergleiche zwischen Spielern
oder Mannschaften zu erleichtern. Hier sind ein paar Optionen:

1. Star-Rating: Eine Bewertung von 1 bis 5 Sternen, wobei 5 Sterne die beste
   Bewertung sind. Dies ist eine einfache und intuitive Methode, die für eine
   breite Zielgruppe verständlich ist.
2. Slider: Ein Schieberegler kann verwendet werden, um eine Bewertung auf einer
   Skala von 1 bis 10 oder 1 bis 100 zu erfassen. Dies ist eine flexible Option,
   die es ermöglicht, eine größere Anzahl von Bewertungen zu erfassen, aber auch
   komplexer sein kann als eine einfache Sterne-Bewertung.
3. Schulnoten: Eine Bewertung von 1 bis 5 oder 1 bis 10, ähnlich wie Schulnoten,
   kann verwendet werden. Dies ist eine weit verbreitete Methode, die einfach
   zu verstehen ist, aber möglicherweise weniger flexibel als ein Schieberegler.

Es ist wichtig, die Bewertungsmethode so zu wählen, dass sie einfach und intuitiv
ist, damit Benutzer sie problemlos verwenden können, ohne lange Anleitungen oder
Schulungen zu benötigen.

## Datenfluss und Anwendungsfälle

1. **Registrierung eines Nutzers**
   - Daten werden in die **Users**Tabelle eingefügt.
   - Standardrolle: Fan.
2. Dashboard

### Bewertungen

- Ein Nutzer bewertet ein Team oder ein Spiel.
- Eintrag in die **Ratings**Tabelle mit Verweisen auf **Users**, **Teams** und **Matches**.

### Ranglisten

- Die **Ranking**Tabelle wird durch Berechnungen aus **Ratings** regelmäßig aktualisiert.

### Statistiken und Analysen

- Aggregierte Daten aus **Ratings** und **Matches** werden genutzt, um
  Teamleistungen und Spielerbewertungen darzustellen.

### Benachrichtigungen

- Änderungen in **Ranking** oder neue Matches lösen Einträge in der
  **Notifications**Tabelle aus.

Userflow

### 1. Benutzer sendet seine Bewertung (Ranking)

- _Aktion des Benutzers_: Ein Fan bewertet ein Team basierend auf verschiedenen
  Kriterien (z. B. Teamwork, Ausdauer). Diese Daten werden in der Datenbank
  gespeichert.
- _Tabellenaktualisierung_:
  - Eintrag in die Tabelle **Ratings**, wie im vorherigen Beispiel gezeigt.
  - Verknüpfung mit dem Benutzer, dem Team und dem Spiel.

### 2. Das Spiel endet

- _Spielstatus_: Sobald das Spiel vorbei ist, wird der Status in der
  **Matches**Tabelle auf "gespielt" gesetzt.
- _Bewertungsfrist_: Nutzer können bis 23:59 Uhr des Spieltages Bewertungen
  abgeben.

### 3. Automatisierte Auswertung um 0:00 Uhr

- _Skript zur Berechnung_:
  - Ein Cron-Job (z. B. in PHP) wird ausgeführt, um alle Bewertungen des Spiels
    auszuwerten.
  - Durchschnittswerte für jedes Bewertungskriterium werden berechnet:

    Durchschnitt = SUMME(rating_value) / ANZAHL(rating_value)

  - Ranking aktualisieren:
    - Jeder Benutzer erhält Punkte basierend darauf, wie nah seine Bewertungen
      am Community-Durchschnitt liegen. Beispiel:
      - Community-Durchschnitt für **Teamwork**: 8,2.
      - Bewertung des Benutzers: 8.
      - Differenz: |8,2 - 8| = 0,2 (niedrigere Differenz = mehr Punkte).
  - Speicherung in der Ranking-Tabelle:
    - Tabelle **Ranking** wird aktualisiert:
      - **total_score** (Gesamtpunktzahl) wird basierend auf den neuen
        Bewertungen aktualisiert.
      - **position** (Platzierung) wird neu berechnet.

### 4. Ergebnisse für den nächsten Tag

- Benachrichtigung der Nutzer:
  - Nutzer erhalten eine E-Mail oder In-App-Benachrichtigung:
    - _"Dein Ranking wurde aktualisiert! Du bist jetzt auf Platz 5 mit 124
      Punkten."_
- Anzeige der aktualisierten Rangliste:
  - Im Frontend wird die neue Rangliste angezeigt.
  - Nutzer können sehen, wie sie im Vergleich zur Community abgeschnitten haben.

### Zusammenfassung

1. Bewertungen werden bis 23:59 Uhr gespeichert.
2. Ein Cron-Job wertet alle Bewertungen aus und berechnet die neuen Rankings.
3. Nutzer werden über ihre Platzierung informiert, und das Ranking wird im Frontend aktualisiert.

## Design

![team.flat-race.eu-01-_quiz_(iPhone 6_7_8).gif](<https://prod-files-secure.s3.us-west-2.amazonaws.com/312f37ac-b83e-48b7-95bf-5dbbef8f4d3a/abf0c827-cede-49b8-876c-2ec59253ed71/team.flat-race.eu-01-_quiz_(iPhone_6_7_8).gif>)

![team.flat-race.eu_register_(iPhone 6_7_8) .gif](<https://prod-files-secure.s3.us-west-2.amazonaws.com/312f37ac-b83e-48b7-95bf-5dbbef8f4d3a/027088ac-ab0f-4cac-8f6f-da78c33498e3/team.flat-race.eu_register_(iPhone_6_7_8)_.gif>)

![team.flat-race.eu_quiz_quiz-submit_(iPhone 6_7_8).gif](<https://prod-files-secure.s3.us-west-2.amazonaws.com/312f37ac-b83e-48b7-95bf-5dbbef8f4d3a/12a40426-6243-4150-942f-1ac0bba46d36/team.flat-race.eu_quiz_quiz-submit_(iPhone_6_7_8).gif>)

![team.flat-race.eu_ranking_(iPhone 6_7_8) .gif](<https://prod-files-secure.s3.us-west-2.amazonaws.com/312f37ac-b83e-48b7-95bf-5dbbef8f4d3a/9813f065-7cb0-446a-92bb-3a3a4ce5b960/team.flat-race.eu_ranking_(iPhone_6_7_8)_.gif>)

![team.flat-race.eu_quiz_auswertung_(iPhone 6_7_8).gif](<https://prod-files-secure.s3.us-west-2.amazonaws.com/312f37ac-b83e-48b7-95bf-5dbbef8f4d3a/2f788ce6-c6f7-44e4-8ad8-5b1077f0a06e/team.flat-race.eu_quiz_auswertung_(iPhone_6_7_8).gif>)

![team.flat-race.eu_quiz_team-auswaehlen_(iPhone 6_7_8) .gif](<https://prod-files-secure.s3.us-west-2.amazonaws.com/312f37ac-b83e-48b7-95bf-5dbbef8f4d3a/700b646f-f50f-456d-8df1-34bb063d8edb/team.flat-race.eu_quiz_team-auswaehlen_(iPhone_6_7_8)_.gif>)

- Figma Screens

  [Figma Design System](https://www.figma.com/embed?embed_host=share&url=https%3A%2F%2Fwww.figma.com%2Ffile%2FB4drhY2HWrYVcqSRZOUWP2%2F%255B0.0%255D-MyDesignSystem%3Ftype%3Ddesign%26node-id%3D896%253A13272%26mode%3Ddesign%26t%3D4n83vYS2Qjen2kKR-1)

## Datenbankstruktur

Eine Möglichkeit könnte sein, eine Hauptdatenbanktabelle für die Sportarten und eine weitere Datenbanktabelle für jede einzelne Sportart zu erstellen. Die Tabelle für jede Sportart könnte dann die Länder, Ligen und Mannschaften beinhalten, die für diese Sportart relevant sind. Dann kann man für jeden Spieler eine weitere Tabelle erstellen, die seine individuellen Informationen, wie Namen, Positionen und Statistiken enthält. Die Bewertungen können in einer weiteren Tabelle gespeichert werden, die Verknüpfungen zu den jeweiligen Spielern und Sportarten hat. Auf diese Weise kann man die Daten einfach nach verschiedenen Kriterien filtern und auswerten.

- Tabellenstruktur
  Tabellenname: Sprachen
  - Spalte: ID (Primärschlüssel)
  - Spalte: Sprachcode
  - Spalte: Sprachname
  Tabellenname: Sportarten
  - Spalte: ID (Primärschlüssel)
  - Spalte: Sprachcode ( Fremdschlüssel auf Sprachen.ID)
  - Spalte: Sportartenname
  Tabellenname: Länder
  - Spalte: ID (Primärschlüssel)
  - Spalte: Sprachcode ( Fremdschlüssel auf Sprachen.ID)
  - Spalte: Landname
  Tabellenname: Ligen
  - Spalte: ID (Primärschlüssel)
  - Spalte: LandID (Fremdschlüssel auf Länder.ID)
  - Spalte: Sprachcode ( Fremdschlüssel auf Sprachen.ID)
  - Spalte: Ligename
  Tabellenname: Mannschaften
  - Spalte: ID (Primärschlüssel)
  - Spalte: LigaID (Fremdschlüssel auf Ligen.ID)
  - Spalte: Sprachcode ( Fremdschlüssel auf Sprachen.ID)
  - Spalte: Mannschaftsname
  Tabellenname: Spieler
  - Spalte: ID (Primärschlüssel)
  - Spalte: MannschaftID (Fremdschlüssel auf Mannschaften.ID)
  - Spalte: Sprachcode ( Fremdschlüssel auf Sprachen.ID)
  - Spalte: Spielername
  Tabellenname: Bewertungskriterien
  - Spalte: ID (Primärschlüssel)
  - Spalte: SportartID (Fremdschlüssel auf Sportarten.ID)
  - Spalte: Sprachcode ( Fremdschlüssel auf Sprachen.ID)
  - Spalte: Kriteriumsname
  Tabellenname: Spiele
  - Spalte: ID (Primärschlüssel)
  - Spalte: Mannschaft1ID (Fremdschlüssel auf Mannschaften.ID)
  - Spalte: Mannschaft2ID (Fremdschlüssel auf Mannschaften.ID)
  - Spalte: Spielzeit
  Tabellenname: Bewertungen
  - Spalte: ID (Primärschlüssel)
  - Spalte: SpielerID (Fremdschlüssel auf Spieler.ID)
  - Spalte: SpielID (Fremdschlüssel auf Spiele.ID)
  - Spalte: BewertungskriteriumID (Fremdschlüssel auf Bewertungskriterien.
- MySQL
  `Sports` table:
  - `id`: primary key
  - `name`: name of the sport (e.g. football, basketball, etc.)
  - `language`: language of the sport name (e.g. English, German, etc.)
  `Leagues` table:
  - `id`: primary key
  - `name`: name of the league (e.g. English Premier League, NBA, etc.)
  - `sport_id`: foreign key referencing `Sports` table
  - `country`: name of the country where the league is based
  `Teams` table:
  - `id`: primary key
  - `name`: name of the team
  - `league_id`: foreign key referencing `Leagues` table
  `Players` table:
  - `id`: primary key
  - `name`: name of the player
  - `team_id`: foreign key referencing `Teams` table
  `Ratings` table:
  - `id`: primary key
  - `player_id`: foreign key referencing `Players` table
  - `rating_criteria`: the name of the criteria being rated (e.g. shooting accuracy, dribbling, etc.)
  - `rating`: the actual rating given by the user (e.g. 4.7)
  - Table erstellen
    ````sql
    CREATE TABLE languages (
      id INT AUTO_INCREMENT PRIMARY KEY,
      language_name VARCHAR(255) NOT NULL,
      language_code VARCHAR(10) NOT NULL
    );

    INSERT INTO languages (language_name, language_code) VALUES
    ("Englisch", "en"),
    ("Deutsch", "de"),
    ("Italienisch", "it"),
    ("Französisch", "fr"),
    ("Spanisch", "es"),
    ("Portugiesisch", "pt"),
    ("Arabisch", "ar"),
    ("Mandarin", "zh"),
    ("Türkisch", "tr"),
    ("Hindi", "hi");

    CREATE TABLE sports (
      id INT AUTO_INCREMENT PRIMARY KEY,
      sport_name VARCHAR(255) NOT NULL,
      sport_code VARCHAR(255) NOT NULL
    );

    INSERT INTO sports (sport_name, sport_code) VALUES
      ('Fußball', 'soccer'),
      ('Basketball', 'basketball'),
      ('Cricket', 'cricket'),
      ('American Football', 'american_football'),
      ('Rugby', 'rugby'),
      ('Tennis', 'tennis'),
      ('Volleyball', 'volleyball'),
      ('Tischtennis', 'table_tennis'),
      ('Baseball', 'baseball'),
      ('Handball', 'handball');


    CREATE TABLE countries (
      country_id INT AUTO_INCREMENT PRIMARY KEY,
      country_name VARCHAR(100) NOT NULL,
      country_code VARCHAR(2) NOT NULL
    );

    INSERT INTO countries (country_name, country_code)
    VALUES
    ("Afghanistan", "AF"),
    ("Albania", "AL"),
    ("Algeria", "DZ"),
    ("Andorra", "AD"),
    ("Angola", "AO"),
    (...);

    CREATE TABLE sport_translations (
        sport_id INT,
        language_code VARCHAR(2),
        sport_name VARCHAR(255),
        PRIMARY KEY (sport_id, language_code),
        FOREIGN KEY (sport_id) REFERENCES sports(id),
        FOREIGN KEY (language_code) REFERENCES languages(code)
    );

    ```sql
    INSERT INTO `sports` (`id`, `sport_name`, `en_name`, `de_name`, `it_name`, `fr_name`, `es_name`, `pt_name`, `ar_name`, `zh_name`, `tr_name`, `hi_name`)
    VALUES
    (1, 'Fußball', 'Soccer', 'Fußball', 'Calcio', 'Football', 'Fútbol', 'Futebol', 'كرة القدم', '足球', 'Futbol', 'फुटबॉल'),
    (2, 'Basketball', 'Basketball', 'Basketball', 'Pallacanestro', 'Basket-ball', 'Baloncesto', 'Basquete', 'كرة السلة', '篮球', 'Basketbol', 'बास्केटबॉल'),
    (3, 'Cricket', 'Cricket', 'Cricket', 'Cricket', 'Cricket', 'Cricket', 'Cricket', 'كريكيت', '板球', 'Kriket', 'क्रिकेट'),
    (4, 'American Football', 'American Football', 'Americanischer Football', 'Football Americano', 'Football Américain', 'Fútbol Americano', 'Futebol Americano', 'كرة القدم الأمريكية', '美式足球', 'Amerikan Futbolu', 'अमेरिकी फुटबॉल'),
    (5, 'Rugby', 'Rugby', 'Rugby', 'Rugby', 'Rugby', 'Rugby', 'Rugbi', 'روغبي', '橄榄球', 'Rugbi', 'रग्बी'),
    (6, 'Tennis', 'Tennis', 'Tennis', 'Tennis', 'Tennis', 'Tenis', 'Tênis', 'تنس', '网球', 'Tenis', 'टेनिस'),
    (7, 'Volleyball', 'Volleyball', 'Volleyball', 'Pallavolo', 'Volley-ball', 'Vóley', 'Vôlei', 'كرة الطائرة', '排球', 'Voleybol', 'वॉलीबॉल'),
    (8, 'Tischtennis', 'Table Tennis', 'Tischtennis', 'Ping Pong', 'Tennis de Table', 'Tenis de Mesa', 'Tênis de Mesa', 'نوبيل', '乒乓球', 'Masa Tenisi', 'टेबल टेनि),
    (9, 'Baseball', 'Baseball', 'Baseball', 'Baseball', 'Baseball', 'Béisbol', 'Beisebol', 'بيسبول', '棒球', 'Beyzbol', 'बेसबॉल'),
    (10, 'Handball', 'Handball', 'Handball', 'Pallamano', 'Handball', 'Balonmano', 'Handebol', 'كرة اليد', '手球', 'Elle topu', 'हैंडबॉल');
    ````
    ```sql
    INSERT INTO sports (name, code)
    VALUES
      ('Baseball', 'baseball'),
      ('Handball', 'handball');
    ```
    ```

    ```
  - API
    ```sql
    $response = wp_remote_get( 'https://api.example.com/data?search=' . urlencode( $user_input ) );

    if ( is_wp_error( $response ) ) {
       // API-Abfrage ist fehlgeschlagen
       $error_message = $response->get_error_message();
       echo "Something went wrong: $error_message";
    } else {
       $api_data = json_decode( wp_remote_retrieve_body( $response ) );
       // Verarbeiten Sie die API-Daten weiter
    }

    ```
- Mehrsprachigkeit
  Hier ist eine Liste der 20 meistgesprochenen Sprachen weltweit:
  1. Mandarin (China)
  2. Spanisch (Spanien, Lateinamerika)
  3. Englisch (USA, Großbritannien, Australien, Kanada)
  4. Hindi (Indien)
  5. Arabisch (Nordafrika, Naher Osten)
  6. Portugiesisch (Portugal, Brasilien)
  7. Bengali (Bangladesh, Indien)
  8. Russisch (Russland)
  9. Japanisch (Japan)
  10. Punjabi (Indien, Pakistan)
  11. Javanese (Indonesien)
  12. Koreanisch (Südkorea)
  13. Deutsche (Deutschland, Österreich, Schweiz)
  14. Telugu (Indien)
  15. Marathi (Indien)
  16. Türkisch (Türkei)
  17. Vietnamesisch (Vietnam)
  18. Italiensich (Italien)
  19. French (Frankreich, Kanada)
  20. Gujrati (Indien)

## Bewertungsprozess

1. **Spiel auswählen:** Benutzer wählt ein aktives Spiel aus dem Spielplan
   (wm_2025_spielplan)
2. **Team auswählen:** Aus den verfügbaren Teams (wm_2025_teams) wird eine
   Mannschaft zur Bewertung ausgewählt
3. **Team bewerten:** Bewertung der ausgewählten Mannschaft anhand der
   definierten Kriterien
   1. 5 Kriterien
   2. Bewertung von 0 - 10 Punkten
4. **Bewertungsende:** Eine Stunde nach Spielende wird die Bewertungsphase
   automatisch beendet
5. **Siegerermittlung:** Nach Bewertungsende wird der Gewinner basierend auf der
   Genauigkeit der Bewertungen ermittelt
   1. Durchschnitt aller Bewertungen wird ermittelt
   2. Ermittlung des Gesamtrankings durch Abgleich der Benutzerbewertungen mit
      dem Gesamtdurchschnitt aller 5 Bewertungskriterien, gefolgt von einer
      Einzelauswertung jedes Kriteriums im Vergleich zum jeweiligen
      Kriteriumsdurchschnitt
6. Ranking

   Beispiel

   |                  | User | AVG  | Diff |
   | ---------------- | ---- | ---- | ---- |
   | **Kraft**        | 7    | 7,3  | 0,3  |
   | **Ausdauer**     | 5    | 6,8  | 1,8  |
   | **Siegeswillen** | 8    | 5,4  | 2,6  |
   | **Teamwork**     | 4    | 6,3  | 2,3  |
   | **Intelligenz**  | 9    | 7,5  | 1,5  |
   | GESAMT           | 33   | 33,3 | 8,5  |
   | Differenz gesamt | 0,3  |      |      |
   | Differenz Skills |      |      |      |

   **Zusatzpunkte (bleiben wie bisher):**

## Vereinfachtes Ranking-System

Das Ranking könnte nach folgendem Prinzip funktionieren:

1. **Punktedifferenz-System:**
   - Für jedes Kriterium wird die absolute Differenz zwischen Benutzerbewertung
     und Durchschnitt berechnet
   - Je geringer die Gesamtdifferenz, desto besser die Platzierung
2. **Beispiel für die Berechnung:**

   | Kriterium           | User | Durchschnitt | Differenz |
   | ------------------- | ---- | ------------ | --------- |
   | **Kraft**           | 8    | 7,1          | 0,9       |
   | **Ausdauer**        | 6    | 7,7          | 1,7       |
   | **Siegeswillen**    | 7    | 9,2          | 2,2       |
   | **Teamwork**        | 9    | 8,1          | 1,1       |
   | **Intelligenz**     | 9    | 8,6          | 0,4       |
   | **Gesamtdifferenz** |      |              | 6,3       |

3. **Gewinner-Ermittlung:**
   - Der Benutzer mit der niedrigsten Gesamtdifferenz gewinnt
   - Bei Gleichstand wird der frühere Bewertungszeitpunkt bevorzugt
4. **Meisterschaft**

   **Punktevergabe pro Spiel:**
   1. Platz: 25 Punkte
   2. Platz: 18 Punkte
   3. Platz: 15 Punkte
   4. Platz: 12 Punkte
   5. Platz: 10 Punkte
   6. Platz: 8 Punkte
   7. Platz: 6 Punkte
   8. Platz: 4 Punkte
   9. Platz: 2 Punkte
   10. Platz: 1 Punkt

   **Zusatzpunkte (bleiben wie bisher):**
   - Geringste Gesamtdifferenz im Spiel: +2 Punkte
   - Früheste vollständige Bewertung: +1 Punkt

   **Meisterschaftssieger wird wie bisher ermittelt durch:**
   - Höchste Gesamtpunktzahl über alle Spiele der Saison
   - Bei Punktegleichstand: Niedrigere Durchschnittsdifferenz über alle Spiele

   Dieses System belohnt sowohl die Genauigkeit der Bewertungen als auch die
   regelmäßige Teilnahme und bietet mehr Anreize für Spieler im Mittelfeld.

---

## Ende des Dokuments
