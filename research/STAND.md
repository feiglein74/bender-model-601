# Arbeitsstand — Bender Model 601

> **Einstiegspunkt des Projekts.** Neue Befunde hinten anfügen, Datum
> voranstellen. Widerlegte Annahmen als Nachtrag markieren, nicht löschen.

## Ausgangslage (2026-08-14)

Gebraucht erworbenes Gerät, äußerlich **intakt** — im Gegensatz zum
Vorgängerprojekt (Bender UNIMET 1000 ST, defekt und umgebaut).

**Einschalttest bestanden (2026-08-14): das Gerät läuft einwandfrei.**
Damit ist die Ausgangslage eine völlig andere als beim Vorgänger — es gibt
keinen Fehler zu suchen. Ziel ist, den **Funktionsumfang zu verstehen und von
außen zu belegen**, ohne das Gerät zu zerlegen. Vorgehen und Checklisten:
`FUNKTIONSAUFNAHME.md`.

Noch nicht geöffnet. Das bleibt vorerst so.

**Einziger Mangelbefund bisher (2026-08-14): Korrosion im Batteriefach.**
Zwei Kontakte vollständig oxidiert, grün-blau — ausgelaufene Zelle. Das ist
der einzige Punkt, der nicht warten sollte, weil Elektrolyt weiterarbeitet
und an Litzen und Leiterbahnen entlangkriecht. Vorgehen und offene Fragen:
`BATTERIE.md`.

## Geräteidentifikation (2026-08-14) — geklärt

**Frontplattenaufdruck:** `BENDER Medical Division — µP SAFETY TESTER Model 601`
**Typenschild:** `Bender µP 601-1` · **Typnummer:** `B928161`

Das Gerät stammt aus der **Medical Division** von Bender — es ist keine
allgemeine Elektroprüftechnik, sondern von vornherein für den Medizinbereich
gebaut. Bauform: tragbarer Koffer, Tastatur im Deckel, **eingebauter
Protokolldrucker**. Einzelheiten der Frontplatte in `FUNKTIONSAUFNAHME.md`,
Abschnitt A.

Das Gerät ist ein **Bender µP601 — Sicherheitstester**, ein 1-Phasen-Prüfgerät
zur Überprüfung von Prüflingen **nach IEC 60601-1** (Sicherheit medizinischer
elektrischer Geräte). Hersteller ist damit **Bender GmbH & Co. KG, Grünberg**;
die Typnummer `B928161` folgt dem bekannten Bender-Sachnummernschema (`B9…`).

### Belegt durch das Datenblatt des Drehstrom-Adapters DS601

`docs/bender/DS601_Drehstromadapter_deen.pdf`, Dokumentnummer **BP 609002 /
09.2006**. Wörtlich:

> Der Drehstrom-Adapter DS601 dient in Verbindung mit dem BENDER-Prüfsystem
> UNIMET® 1000/1100ST **oder dem Sicherheitstester μP601** zur Überprüfung von
> 3-phasigen Prüflingen nach IEC 60601-1.

> Da das UNIMET® 1000/1100ST bzw. der µP601 ein **1-Phasen-Gerät** ist, werden
> mittels Drehstrom-Adapter DS601 zwei Phasen an dem Sicherheitstester
> vorbeigeführt […]

Daraus abgeleitet — alles noch am Gerät zu bestätigen:

| Befund | Grundlage |
|---|---|
| einphasiges Prüfgerät | DS601-Datenblatt, wörtlich |
| Prüfungen nach IEC 60601-1 | DS601-Datenblatt, wörtlich |
| **menügeführte Software** („Drehstromgeräte im Menü von […] µP601 auswählen") | DS601-Datenblatt |
| **Prüfsteckdose** für den Prüfling, **Prüfspitze** | Prüfaufbau-Schaubild |
| Softwarestände tragen Kennungen der Form `ID..xxxXX` | Warnhinweis im Schaubild |
| 2006 noch im Zubehörprogramm geführt | Datum des Datenblatts |

Die Fehlerbedingungen „Netzleiter offen" und „Phase vertauscht" sind im
Prüfablauf des µP601 vorgesehen — auch das nennt das DS601-Datenblatt.

Der Zusatz **`-1`** in `µP 601-1` ist noch ungeklärt: Variante, Ausbaustufe
oder Baureihenindex. Das DS601-Datenblatt kennt nur „µP601".

### Vom Gerät selbst bestätigt (2026-08-14)

Die oberste Menüebene ist eine **Betriebsartenwahl zwischen zwei Normen**
(`MENUEBAUM.md`, `[S02]`):

- **`IEC 601-1:1988`**
- **`DIN VDE 0751T1/90`**

Zwei Schlüsse daraus:

**Der Gerätename ist die Norm.** `IEC 601-1` — in der alten Zählweise, nicht
als `IEC 60601-1` wie im DS601-Datenblatt von 2006. Die anfängliche Vermutung
zur „601" ist damit nicht mehr Deutung, sondern belegt.

**Datierung auf etwa 1990–1993.** Die neuere der beiden Normausgaben ist von
1990; ein Gerät wird nicht für Normen gebaut, die es noch nicht gibt. Das passt
zu Zeichendisplay, Folientastatur, eingebautem Drucker und einer mit
AA-Zellen gepufferten Uhr.

### Nachtrag zur ersten Recherche

Die folgenden vier Hypothesen entstanden, bevor die Beschriftung bekannt war.
Sie bleiben stehen, weil eine davon halb zutraf und die anderen erklären, warum
die erste Suche ins Leere lief.

**Zutreffend war Hypothese B, aber nur zur Hälfte:** die „601" verweist
tatsächlich auf die Norm IEC 601 (heute IEC 60601) — und ist *zugleich* die
echte Typbezeichnung. **A, C und D sind widerlegt:** kein Zahlendreher, kein
fremder Hersteller, keine bloße Sachnummer.

Die Bezeichnung „Model 601" allein ließ sich in der ersten Web-Recherche
(2026-08-14) **keinem Bender-Produkt zuordnen.**

Die Prüftechnik-Reihe von Bender GmbH & Co. KG (Grünberg) heißt UNIMET® und
umfasst laut Herstellerseiten und Handbüchern:

| Modell | bekannt aus |
|---|---|
| UNIMET 300ST | Handbuch, bentron.de-Archiv |
| UNIMET 400ST | Produktübersicht |
| UNIMET 610ST | aktuelle Bender-Produktseite (DGUV V3, Maschinen/Betriebsmittel) |
| UNIMET 800ST / 810ST | Handbuch de/en |
| UNIMET 1000ST / 1100ST | Handbuch, Vorgängerprojekt |

Ein **601ST** taucht darin nicht auf. Denkbare Erklärungen, alle noch unbelegt:

- **A — es ist ein UNIMET 610ST.** Zahlendreher beim Ablesen; das Modell
  existiert und liegt im selben Zahlenraum.
- **B — die „601" verweist auf die Norm,** nicht auf eine Typnummer.
  IEC 601 ist der frühere Name der IEC 60601 (Sicherheit medizinischer
  elektrischer Geräte). Ältere Prüfgeräte mehrerer Hersteller sind danach
  benannt (z. B. Netech LKG 601, Fluke 601PRO).
- **C — anderer Hersteller.** „Bender" könnte auf dem Gerät für etwas anderes
  stehen als für Bender GmbH & Co. KG.
- **D — Sach-/Bestellnummer** statt Modellbezeichnung.

## Vorhaben nach Abschluss der Aufnahme

**Ein Modul, das den Ausdruck aufnimmt und anzeigt, statt ihn auf Papier zu
drucken** (Ziel formuliert 2026-08-14).

Die Begründung trägt: Der eingebaute Drucker ist derzeit die **einzige bekannte
Datenausgabe** des Geräts. Papier, Farbband oder Thermokopf sind
Verschleißteile, für die es nach über dreißig Jahren keinen selbstverständlichen
Nachschub gibt. Ein Modul, das den Druckdatenstrom abgreift, würde jedes
Protokoll dauerhaft sichern — und das Gerät bliebe unverändert.

### Es wird einfacher als gedacht: das Gerät hat eine RS-232

**Befund vom 2026-08-14, aus dem Rückwandfoto:** Auf der Rückwand sitzt eine
25-polige Sub-D-Buchse, beschriftet **`V.24/RS-232C`**, darüber
**`BAUD 4800`**.

Damit ist die entscheidende Frage beantwortet, **bevor** sie zum Problem wurde:

- Der Drucker ist **nicht** die einzige Datenausgabe.
- Es muss **kein Druckkopfsignal** abgegriffen und in Text zurückverwandelt
  werden — das war der aufwendige Fall, und er entfällt.
- Es bleibt ein serieller Datenstrom, der sich mit einem
  USB-RS-232-Adapter mitschneiden lässt. Die Übertragungsrate steht auf dem
  Gehäuse.

**Das Vorhaben schrumpft damit von „Reverse Engineering einer
Druckeransteuerung" auf „Datenstrom mitlesen und darstellen".**

Nächste Schritte dazu in `FUNKTIONSAUFNAHME.md`, Abschnitt E. Offen sind vor
allem die restlichen Übertragungsparameter (Datenbits, Parität, Handshake) —
zu suchen im `F`-Zweig des Menüs — und die Frage, ob das Gerät auch Befehle
entgegennimmt oder nur sendet.

Bis dahin gilt trotzdem: **Papier sparen.** Jeder Ausdruck, der jetzt entsteht,
sollte fotografiert werden — Thermopapier verblasst.

## Einordnung: Vorgänger der UNIMET-Reihe

Der µP601 gehört **nicht** zur UNIMET-Reihe. Er wird im DS601-Datenblatt als
eigenständiger „Sicherheitstester" neben dem „Prüfsystem UNIMET® 1000/1100ST"
geführt — zwei getrennte Produkte am selben Zubehör.

Bekannte Bender-Prüftechnik zum Vergleich, keine davon eine „601":
UNIMET 300ST, 301ST, 400ST, 610ST, 800ST/810ST, 1000ST/1100ST.

**Für das Vorgängerprojekt (UNIMET 1000 ST) heißt das: technisch nicht
übertragbar.** Gemeinsam ist nur das Zubehör und die Norm, nicht die Bauart.
Der 1000 ST ist ein PC-basiertes System (x86-Modul, DOS, Anwendung auf
Flash-Datenträger). Ob der µP601 überhaupt einen PC enthält oder ein
klassischer Mikrocontroller-Aufbau ist, ist offen — das „µP" im Namen steht
für „Mikroprozessor" und deutet eher auf Letzteres.

## Unterlagen — Stand der Beschaffung

**Gefunden (1):**

| Dokument | Ablage |
|---|---|
| DS601 Drehstrom-Adapter, BP 609002 / 09.2006, de/en | `docs/bender/DS601_Drehstromadapter_deen.pdf` |

**Nicht gefunden — Bedienungshandbuch des µP601.** Gesucht wurde am 2026-08-14:

- Websuche in mehreren Formulierungen (`µP601`, `uP601`, `µP 601-1`, `B928161`)
- Wayback-CDX über `bentron.de` (vollständige Liste, 250 Einträge) — enthält
  ausschließlich UNIMET-Unterlagen, nichts zum µP601
- Wayback-CDX über `bender.de` — Treffer nur moderne Assets, kein µP601-Dokument
- Regionale Bender-Seiten (`bender-uk.com` führt das DS601-Blatt)

Das Gerät ist offenkundig **älter als der archivierte Webbestand**. Die
Sachnummer `B928161` erzeugt keinen einzigen Web-Treffer.

### Noch nicht ausgeschöpft

- **Bender direkt anfragen** unter Nennung von `B928161` und der Seriennummer.
  Bender pflegt einen Service für abgekündigte Geräte; die Sachnummer ist
  intern eindeutig.
- **ELMTEC** (Kalibrierdienst, kalibriert Bender-Prüftechnik) — kennt alte
  Baureihen aus der Praxis.
- **Kliniktechnik / Medizintechnik-Werkstätten**, in denen das Gerät lief.
- Kleinanzeigen- und Auktionsarchive mit Gerätefotos.
