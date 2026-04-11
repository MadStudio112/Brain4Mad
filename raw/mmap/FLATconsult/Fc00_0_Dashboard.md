---
type: raw-mmap
map_id: "Fc00_0_Dashboard"
source: "01_input/FLATconsult/Fc00_0_Dashboard.mmap"
imported_at: 2026-04-11
node_count: 38
max_depth: 5
has_custom_props: true
has_links: true
has_notes: false
has_icons: true
icons:
  - PadlockLocked
custom_property_names:
  - "Benutzer"
  - "Domain"
  - "FTP-Benutzername"
  - "FTP-Server"
  - "Freifläche befestigt"
  - "Freifläche begrünt"
  - "Funktionsfläche"
  - "Grundstücksfläche"
  - "Hauptnutzfläche"
  - "Nebennutzfläche"
  - "PW"
  - "Port"
  - "Verzeichnis"
tags:
  - mmap/raw
  - mmap/FLATconsult
---

# FLATconsult

- **FLATconsult** ^oid-AkqquqNi
  - **CPaneel** ^oid-gk8l9Xic
    - **FTP-Konto** `Benutzer=MAD` `Domain=explore.mind-added-design.net` `PW=07MAD@explore05` `Verzeichnis=/home2/mindadde/explore.mind-added-design.net/` `FTP-Benutzername=MAD@explore.mind-added-design.net` `FTP-Server=ftp.mind-added-design.net` `Port=21` ^oid-LgcXgfxh
      - **MAD@consult.flat-race.eu** `PW=07MAD@consult05` [icon:PadlockLocked] ^oid-6ZZ7bcTP
    - **Schutz für Verzeichnis** ^oid-r0B5qjl6
      - **ME** [00_Dashboard.mmap](..\..\02_Projekte\10_EM\00_Dashboard.mmap) ^oid-j51v9yNU
        - **https://consult.flat-race.eu/ME/index.html** [401 Unauthorized](https://consult.flat-race.eu/ME/index.html) ^oid-GgTpeXlR
        - **.htaccess** [icon:PadlockLocked] ^oid-j8rCgBKw
          - **MAD** `PW=MAD@consult` [Htpasswd Generato](http://www.htaccesstools.com/htpasswd-generator/) [icon:PadlockLocked] ^oid-cTiY7R8M
          - **ME** `PW=` [Htpasswd Generato](http://www.htaccesstools.com/htpasswd-generator/) [icon:PadlockLocked] ^oid-KayuhXT8
  - **Dashboard** ^oid-WAWwSkvO
    - **Allgemein** ^oid-EslyYyV1
      - **Leistungsbeschreibung** ^oid-fiCz5AhP
      - **Stammdaten** ^oid-QaFUZlA1
      - **Flächen** ^oid-wM8oQZDk
      - **Rahmen** ^oid-YZvmnCha
    - **Planung** ^oid-EaOMzNiA
      - **Bestand** ^oid-TdAnnq0z
      - **Entwurf** ^oid-FNJjqUgT
      - **Einreichung** ^oid-BVPzlKDC
      - **Detailplan** ^oid-KKNOzcdc
    - **Timeline** ^oid-JubTO4TL
      - **Soll** ^oid-NQEdjANS
      - **Ist** ^oid-wDOwZAZR
    - **Fotos** ^oid-hzi0pPwu
      - **Bestand** ^oid-CNo4OG4J
      - **Bau** ^oid-sidshDus
      - **Neu** ^oid-uR7AZdNN
    - **Kosten** ^oid-35sqq3uo
      - **Budget** ^oid-0eEeZhBL
      - **Anschlag** ^oid-pZa3rcVC
      - **Abrechnung** ^oid-mcLOSlw0
    - **Korrespondenz** ^oid-tpcXI5tW
      - **Termin** ^oid-oCkPxyDU
      - **Email** ^oid-qoY6YCWz
      - **Telefon** ^oid-BcEttQZE
  - **Stammdaten** [Fc01_0_Stammdaten.mmap#xpointer(/descendant-or-self::ap:Topic[@OId='GE1uWqQwMESoRQFtyQxogg=='])](Fc01_0_Stammdaten.mmap#xpointer(/descendant-or-self::ap:Topic[@OId='GE1uWqQwMESoRQFtyQxogg=='])) ^oid-DJAchc4n
  - **Raumbuch** `Grundstücksfläche=1316` `Hauptnutzfläche=108.29` `Nebennutzfläche=76.92` `Funktionsfläche=3.39` `Freifläche befestigt=101.98` `Freifläche begrünt=1127` [Fc02_0_Flächen.mmap#xpointer(/descendant-or-self::ap:Topic[@OId='fU8Vc6LewUaCnfWcBIz+Cg=='])](Fc02_0_Flächen.mmap#xpointer(/descendant-or-self::ap:Topic[@OId='fU8Vc6LewUaCnfWcBIz+Cg=='])) ^oid-whZbg3d4

## Custom Property Index

| Property | Topic count |
|---|---|
| PW | 4 |
| Benutzer | 1 |
| Domain | 1 |
| Verzeichnis | 1 |
| FTP-Benutzername | 1 |
| FTP-Server | 1 |
| Port | 1 |
| Grundstücksfläche | 1 |
| Hauptnutzfläche | 1 |
| Nebennutzfläche | 1 |
| Funktionsfläche | 1 |
| Freifläche befestigt | 1 |
| Freifläche begrünt | 1 |
