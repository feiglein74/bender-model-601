# Funktionsaufnahme von außen — Bender µP601

Ziel: verstehen und belegen, **was das Gerät kann**, ohne es zu öffnen.
Das Gerät läuft (Einschalttest 2026-08-14) und ist damit selbst die beste
Quelle — ein Handbuch ist öffentlich nicht auffindbar (`../QUELLEN.md`).

Reihenfolge ist bewusst gewählt: erst festhalten, was ohne Netzspannung
sichtbar ist, dann der laufende Betrieb, dann Messungen. Jeder Abschnitt hat
ein Feld für das Ergebnis; eingetragen wird, was tatsächlich beobachtet wurde,
nicht was erwartet wurde.

---

## Sicherheit

Ein Sicherheitstester nach IEC 60601-1 tut im Betrieb genau das, wovor man
sonst warnt: er **legt Netzspannung auf die Prüfsteckdose**, trennt gezielt
Schutz- und Netzleiter auf und erzeugt für die Isolationsprüfung **Gleich­spannung
in der Größenordnung 500 V**.

- Prüfsteckdose im Betrieb wie eine spannungsführende Steckdose behandeln.
- Vor der Isolationsprüfung wissen, was am Prüfling hängt — 500 V DC zerstören
  Elektronik, Überspannungsableiter und Y-Kondensatoren reagieren darauf.
- Fehlerbedingung „Netzleiter offen" heißt: der Prüfling verliert im laufenden
  Betrieb einen Pol. Nichts anschließen, dem das schadet.
- Nach jeder Messung Entladung abwarten, bevor umgesteckt wird.
- Gerät steht auf einem Tisch, nicht auf dem Schoß, Prüfling gesichert.

---

## Erwartungsrahmen: Was ein Prüfgerät nach IEC 60601-1 leisten muss

Kein Befund, sondern der Raster, gegen den die Menüpunkte gehalten werden.
Wenn ein Punkt im Gerät fehlt, ist **das** der interessante Befund.

### Messgrößen

| Messung | Worum es geht |
|---|---|
| **Schutzleiterwiderstand** | Widerstand Netzstecker-Schutzkontakt ↔ berührbares Metall; Prüfstrom typisch mehrere Ampere |
| **Isolationswiderstand** | typisch 500 V DC, Netzteil ↔ Gehäuse bzw. ↔ Anwendungsteil |
| **Erdableitstrom** | Strom über den Schutzleiter zur Erde |
| **Gehäuseableitstrom** | Strom vom berührbaren Gehäuse zur Erde |
| **Patientenableitstrom** | Strom über das Anwendungsteil zum Patienten |
| **Patientenhilfsstrom** | Strom zwischen zwei Teilen desselben Anwendungsteils |
| **Netzspannung am Anwendungsteil** | Anwendungsteil wird gegen Netzspannung geprüft |
| **Ersatzableitstrom** | rechnerisches Ersatzverfahren statt Messung am Netz |

### Bedingungen, unter denen gemessen wird

- **Normalbedingung** und **Erst-Fehler-Bedingung**
- Erst-Fehler: **Schutzleiter offen**, **Netzleiter offen**, **Phase vertauscht**
- Der schlechteste Wert gilt als Ergebnis

### Klassifizierung des Prüflings

- **Schutzklasse I** (mit Schutzleiter) und **Schutzklasse II** (schutzisoliert)
- **Anwendungsteile Typ B, BF, CF** — bestimmen die zulässigen Grenzwerte
- Geräte ohne Anwendungsteil

### Bekannt für dieses Gerät

Aus dem DS601-Datenblatt bereits belegt: **einphasig**, **menügeführt**,
Fehlerbedingungen „Netzleiter offen" und „Phase vertauscht" vorhanden,
Prüfsteckdose und Prüfspitze vorhanden, Softwarestände `ID..xxxXX`.
Für Drehstromprüflinge gibt es im Menü einen eigenen Eintrag.

---

## Erwartung für die noch unbetretenen Messzweige

`Nur Messung` gliedert sich in **Schutzleiter**, **Isolation** und
**Ableitstrom** (`MENUEBAUM.md`, `[S26]`). Der erste ist erkundet. Was in den
beiden anderen zu erwarten ist — als Vorhersage formuliert, damit das
Durchgehen des Menüs sie prüfen kann.

### Isolation — Widerstand bei hoher Prüfspannung

Gemessen wird der **Isolationswiderstand** mit einer **Gleichspannung in der
Größenordnung 500 V**, angezeigt in **MΩ**. Der Prüfling ist dabei **nicht in
Betrieb.**

Zu erwartende Messstrecken:

| Von | Gegen | Prüft |
|---|---|---|
| Netzteil (L und N gebrückt) | Schutzleiter | Isolation bei Schutzklasse I |
| Netzteil | berührbares Gehäuse | Isolation bei Schutzklasse II |
| Netzteil | Anwendungsteil | Trennung Netz ↔ Patient |
| Anwendungsteil | Gehäuse / Erde | Trennung des Anwendungsteils |

Die Aussage ist eine andere als bei der Schutzleiterprüfung: Dort geht es um
einen Weg, der **da sein muss**, hier um Wege, die **nicht da sein dürfen.**
Die hohe Prüfspannung deckt Isolationsfehler auf, die bei Netzspannung noch
nicht durchschlagen, aber im Begriff sind es zu tun — Feuchtigkeit,
Kriechwege, gealterte Isolierstoffe.

⚠️ **500 V DC zerstören Elektronik.** Überspannungsableiter, Y-Kondensatoren
und Netzfilter sprechen an oder werden beschädigt. Deshalb ist dieser
Prüfschritt bei modernen Geräten oft ausdrücklich **nicht** anzuwenden — und
für eigene Versuche nur an einem Prüfling, dem nichts passieren kann.

### Ableitstrom — was im Betrieb tatsächlich fließt

Hier läuft es umgekehrt: **kleine Ströme, gemessen in µA**, unter
Bedingungen, die dem Betrieb entsprechen oder ihn nachbilden. Erwartet werden:

| Messgröße | Was fließt |
|---|---|
| **Erdableitstrom** | Strom, der über den Schutzleiter zur Erde abfließt |
| **Gehäuse-/Berührungsstrom** | Strom von berührbarem Metall zur Erde — mit der **Prüfspitze** angetastet |
| **Patientenableitstrom** | Strom über das Anwendungsteil zum Patienten — über die **zehn grünen Buchsen** |
| **Patientenhilfsstrom** | Strom **zwischen** zwei Anwendungsteil-Anschlüssen |

Dazu die **Verfahren**, in denen DIN VDE 0751 sich von der IEC unterscheidet:

- **Direktmessung** — der Prüfling läuft an der Prüfsteckdose, der tatsächlich
  fließende Strom wird gemessen. Realistisch, aber aufwendiger und mit
  Netzspannung am Prüfling.
- **Ersatzableitstrommessung** — der Prüfling bleibt **stromlos**. Zwischen den
  gebrückten Netzkontakten und Gehäuse bzw. Anwendungsteil wird eine
  Prüfspannung angelegt und der Strom gemessen. Sicherer und in der
  Wiederholungsprüfung üblich.
- **Differenzstromverfahren** — gemessen wird die Differenz zwischen Hin- und
  Rückleiter; was fehlt, fließt anderswohin ab.

Ob dieses Gerät alle drei kennt, ist offen — **es zu erfahren, ist einer der
Gründe, den VDE-Zweig vollständig durchzugehen.**

⚠️ Bei der **Direktmessung** trennt das Gerät gezielt den Schutzleiter auf, um
die Erst-Fehler-Bedingung herzustellen. Das berührbare Gehäuse des Prüflings
kann in diesem Moment Spannung führen — der gemessene Strom ist begrenzt, aber
er ist da. Kein unbeaufsichtigter Aufbau, nichts anfassen, während die Messung
läuft.

### Warum beides nötig ist

Isolationsmessung und Ableitstrommessung ersetzen einander nicht:

- Die **Isolationsmessung** findet Schwächen, die noch keinen Strom führen —
  sie sieht das Problem von morgen.
- Die **Ableitstrommessung** erfasst, was heute tatsächlich fließt,
  einschließlich der Ströme durch Entstörkondensatoren, die völlig
  bestimmungsgemäß da sind und trotzdem begrenzt bleiben müssen.

Ein Gerät kann die eine Prüfung bestehen und die andere nicht — deshalb stehen
beide in der Norm.

---

## A — Gerät im Ruhezustand, Netzstecker gezogen

- [ ] **Typenschild** vollständig: Typbezeichnung, Sachnummer, Seriennummer,
      Baujahr, Anschlusswerte, Prüf- und Konformitätszeichen, Herstelleranschrift
      → bekannt: `Bender µP 601-1`, `B928161`
- [ ] **Weitere Aufkleber**: Kalibrier-/Prüfplaketten mit Datum, Inventarnummern
      des Vorbesitzers, Service-Aufkleber, Softwarestand-Aufkleber
- [ ] **Frontplatte**: Beschriftung jeder Buchse und jeder Taste, wörtlich
- [x] **Anzeige**: **4 Zeilen, Zeichendisplay** (2026-08-14, gesichtet).
      Spaltenzahl geschätzt 20 — **noch nicht ausgezählt**.
      Offen: Bauart (LCD/VFD), Hintergrundbeleuchtung.
      → 4×20 wäre die übliche Bauform dieser Gerätegeneration
      (HD44780-kompatibles Zeichenmodul). Bestätigung durch Auszählen der
      längsten angezeigten Zeile: 16, 20 oder 40 Zeichen sind gut
      unterscheidbar. Für die Menükartierung in Abschnitt C ist die exakte
      Spaltenzahl nützlich, weil Bender die Beschriftungen darauf abgekürzt
      haben wird.
- [x] **Bedienelemente** (2026-08-14) — zwei Gruppen, alles in Folientechnik:

      **Neben dem Display: 3 Kontexttasten (Softkeys).** Unbeschriftet, jeweils
      mit einem Strich auf eine Displayzeile zeigend; ihre Bedeutung steht in
      der Anzeige.

      **Separate Folientastatur:**

      | Taste | Funktion |
      |---|---|
      | **Nummernblock** | alphanumerisch nach Telefonbelegung, siehe unten |
      | **START** | **belegt: Rücksprung zum Startbildschirm** — nicht der Messungsstart, wie zunächst vermutet |
      | **F** | **belegt: öffnet ein kontextabhängiges Menü** — vom Startbildschirm aus die Sprachauswahl |
      | **↑ / ↓** | Blättern in Listen, Auswahl, ziffernweises Verstellen (noch nicht belegt) |

      ⚠️ **Beobachtung 2026-08-14: Tastendrücke gehen gelegentlich verloren.**
      Beim Blättern in der Prüflingsdatenbank hat `↑` nicht auf jeden Druck
      reagiert. Mögliche Ursachen, noch nicht unterschieden:

      - **alternde Folientastatur** — bei einem Gerät dieses Alters die
        naheliegendste; Kontaktfolien werden mit den Jahren unzuverlässig
      - **Entprellung oder Wiederholsperre** der Firmware, die zu schnelle
        Eingaben verwirft
      - Bedienfehler, zu kurzer oder zu weit am Rand gesetzter Druck

      - [ ] Betrifft es **alle** Tasten oder nur einzelne? Systematisch
            durchprobieren und notieren, welche auffällig sind
      - [ ] Hilft langsameres Drücken? Dann spricht es für die Firmware
      - [ ] Hilft ein anderer Druckpunkt auf derselben Taste? Dann für die Folie

      **Folge für alle Aufnahmen:** Zählungen nie aus der Zahl der
      Tastendrücke ableiten, sondern aus dem, was auf der Anzeige steht.

      **Alle sieben Bedientasten sind LED-hinterleuchtet** — die drei Softkeys
      ebenso wie `START`, `F`, `↑` und `↓` (belegt 2026-08-14). Die LED zeigt
      an, **ob die Taste im gerade angezeigten Bildschirm etwas bewirkt.**

      Das ist mehr als eine Bedienhilfe: Zusammen mit dem `>` in der Anzeige
      macht es die Bedienoberfläche **selbstdokumentierend** — auf jedem
      Bildschirm ist ohne Ausprobieren ablesbar, welche Wege es gibt. Für die
      Kartierung in `MENUEBAUM.md` ist das die Vollständigkeitsprobe.

      Der Nummernblock ist nach Auskunft der Fotos **nicht** LED-hinterleuchtet
      — zu bestätigen.

      Offen: Lage des Netzschalters, weitere Bedienelemente außerhalb der
      beiden Tastengruppen.
- [ ] **Prüfsteckdose**: Bauform, Ausführung, Beschriftung
- [ ] **Messbuchsen**: Prüfspitze, Anwendungsteil-/Patientenanschlüsse — Anzahl,
      Bauform, Farbe, Beschriftung
- [ ] **Rückwand**: Netzanschluss, Sicherungshalter mit Aufdruck, Schnittstellen,
      Typenschild, Lüftungsöffnungen
- [ ] **Zubehör**, das mitgekommen ist: Kabel, Prüfspitzen, Adapter, Koffer,
      Unterlagen — jedes Teil mit Beschriftung
- [ ] Fotos von allem in `../bilder/`

**Ergebnis (2026-08-14) — anhand zweier Fotos der Verkaufsanzeige**

Quelle: `../bilder/verkaufsanzeige/frontplatte_detail.webp` (Nahaufnahme der
Frontplatte) und `.../geraet_gesamt_mit_zubehoer.webp` (Gerät geöffnet, mit
Zubehör). Nicht selbst aufgenommen, deshalb nicht im Repository.

⚠️ **Vorbehalt:** Es ist nicht gesichert, dass die Fotos genau dieses Exemplar
zeigen. Alles hier ist am eigenen Gerät gegenzuprüfen — insbesondere
Seriennummer, Softwarestand und Zubehörumfang.

### Offizielle Gerätebezeichnung

Auf der Frontplatte steht, in dieser Anordnung:

```
BENDER              µP  SAFETY TESTER
Medical Division        Model   601
```

Das Gerät heißt also **„µP Safety Tester Model 601"**, Hersteller ist die
**Medical Division** von Bender. Die Beschriftung `µP 601-1` und die Typnummer
`B928161` stammen vom Typenschild und sind davon zu unterscheiden.

Der Zusatz **Medical Division** ist ein eigenständiger Befund: das Gerät ist
nicht allgemeine Elektroprüftechnik, sondern von vornherein für den
Medizinbereich gebaut. Das deckt sich mit IEC 60601-1 aus dem DS601-Datenblatt.

### Bauform

**Tragbarer Koffer mit aufklappbarem Deckel.** Im Oberteil sitzen Anzeige,
Anschlüsse und Drucker, im **Deckel die Tastatur**. Metallrahmen mit
Verschlüssen, Tragegriff, dazu eine lederne Dokumententasche auf dem Gehäuse.

### Bestätigte Anschlüsse

| Anzahl | Art | Befund |
|---|---|---|
| 1 | **Schuko-Prüfsteckdose** | dunkel, versenkt, links auf der Front |
| 1 | **Kaltgeräte-Einbaustecker mit Stiften** | daneben — **Leitungsprüfung bestätigt** |
| 10 | **Sicherheitsbuchsen grün**, 4 mm | **einzeln durchnummeriert `1` bis `10`**, in drei Reihen (1–4 / 5–7 / 8–10) |
| 1 | **Sicherheitsbuchse gelb**, 4 mm | am Ende der Reihe, darunter das **Erdungszeichen** |

### Berichtigung: die gelbe Buchse ist doch die Erde

Unter der gelben Buchse steht das **Erdungssymbol**. Die Deutung „Masse/Erde"
war damit richtig, meine Gegenrede vom selben Tag falsch. Sie bleibt oben
stehen, weil zwei der drei Argumente weiterhin gelten — nur nicht als Beleg
gegen die Erde:

- Die Farbüberlegung war ein Fehlschluss. Bender kennzeichnet hier nicht einen
  Schutzleiter im Sinne der Installationsnorm, sondern setzt eine
  **Bezugsbuchse** farblich von den zehn Messbuchsen ab. Gelb steht für
  „anders als die grünen", nicht für „grün-gelb".
- Die Prüfspitze, die ich stattdessen vermutet hatte, existiert und liegt im
  Zubehör (siehe unten) — sie hat nur einen anderen Anschlussweg.

Offen bleibt, **wogegen** diese Erde bezogen ist: Schutzkontakt der
Prüfsteckdose, Schutzkontakt des eigenen Netzanschlusses oder ein interner
Messbezugspunkt. Das entscheidet der Durchgangstest unten.

### Die zehn grünen Buchsen sind einzeln nummeriert

`1` bis `10`, jede einzeln beschriftet — also **keine gebündelte Sammelklemme**,
sondern zehn getrennt geführte Anschlüsse. Das ist die Voraussetzung für den
**Patientenhilfsstrom** (Messung zwischen zwei Teilen desselben Anwendungsteils)
und passt zur Zehnerzahl eines EKG-Anwendungsteils.

Ob sie im Gerät tatsächlich getrennt sind oder nur getrennt herausgeführt und
intern gebrückt, bleibt der Messung vorbehalten.

### Sechs Piktogramme über der Frontplatte

Über den Anschlüssen liegt eine Reihe von **sechs orangefarbenen
Schaltbildern** — je ein Messaufbau, gerahmt. Sie sind faktisch die
Kurzfassung des Funktionsumfangs. Lesbare Beschriftungen: `MΩ`, `µA`, `Ω`,
`L  N  PE`, `1 … 10`, sowie Stecker-, Steckdosen- und Erdungssymbole.

Eindeutig zuzuordnen sind bisher:

| Nr. | Bild | Deutung |
|---|---|---|
| 3 | eine **Hand hält zwei Kabelenden**, darunter Steckdose und Kupplung mit `Ω` | **Leitungsprüfung** — erklärt den Kaltgeräte-Einbaustecker |
| 5 | Stecker mit Erde, `MΩ` und `µA`, darunter Steckdose mit `L  N  PE` | **Isolationswiderstand** und **Ableitstrom** |
| 6 | Stecker mit Erde, Kasten mit `1 … 10` und `µA` | **Patientenableitstrom** über die zehn Buchsen |

Die übrigen drei zeigen Varianten mit Schutzleiter, Gehäuse und Anwendungsteil.

### 🔑 Die Piktogramme sind hinterleuchtet (belegt 2026-08-14)

**Sie sind keine gedruckten Beschriftungen, sondern Anzeigen.** Beim Start
einer Messung leuchtet das zugehörige Schaltbild auf — belegt an Piktogramm 3
(Hand mit zwei Kabelenden), das bei der Schutzleiterprüfung einer abnehmbaren
Zuleitung aufleuchtete (`MENUEBAUM.md`, `[S29]`).

Damit ist die Frontplatte ein **Schaltbild-Display**: Der Anwender sieht nicht
nur einen Zahlenwert auf vier Zeilen, sondern die zugehörige Beschaltung als
Bild — welche Buchsen beteiligt sind, wo aufgetrennt wird, wogegen gemessen
wird. Für ein Gerät mit so kleinem Textdisplay eine elegante Lösung, und ein
Stück Bedienphilosophie: Das Gerät erklärt den Messaufbau, statt ihn nur zu
benennen.

**Praktische Folge: Die Piktogramme sind vollständig entschlüsselbar**, ohne
Handbuch — man muss nur notieren, welches Bild bei welchem Menüpfad aufleuchtet.

| Nr. | Bild | Zuordnung |
|---|---|---|
| 1 | Stecker, Erde, gestricheltes Feld mit Erde | offen |
| 2 | Stecker mit Erde, Pfeil zur Steckdose mit `Ω` | vermutlich **Schutzleiter → Gehäuse** |
| 3 | **Hand hält zwei Kabelenden**, Steckdose und Kupplung mit `Ω` | **belegt: Schutzleiter → Zuleitung** (abnehmbare Netzleitung) |
| 4 | Feld mit Erde, Pfeil zur Steckdose | offen |
| 5 | Stecker mit Erde, `MΩ` und `µA`, `L  N  PE` | vermutlich **Isolation** |
| 6 | Stecker mit Erde, Kasten `1 … 10` mit `µA` | vermutlich **Ableitstrom, Anwendungsteil** |

- [ ] Tabelle beim weiteren Messen vervollständigen
- [ ] Leuchtet immer genau eines, oder mehrere gleichzeitig?
- [ ] LEDs oder Glühlampen? Bei Glühlampen wäre das ein künftiges
      Verschleißthema.

### Neu: eingebauter Drucker

Rechts neben der Anzeige sitzt ein **Papierschacht mit Sichtfenster**, darin
ein bedruckter Streifen. Lesbar ist darauf **`Klasse:1`** — also die
Schutzklasse des Prüflings. Das Gerät **druckt Prüfprotokolle selbst aus.**

### Bauart: kein Thermodrucker (belegt 2026-08-14)

**Prüfung am vorhandenen Ausdruck:** Ein auf etwa 300 °C aufheizender
Lötkolben in Papiernähe hinterlässt **keine Spur.** Thermopapier hätte sich
weit darunter geschwärzt — meist ab 60–90 °C.

**Direkte Thermografie ist damit ausgeschlossen.** Zusammen mit dem
Sichteindruck bleibt ein **Anschlagdrucker (Nadeldrucker)** die schlüssige
Deutung.

Streng genommen offen bleibt nur noch der **Thermotransferdruck** — er nutzt
zwar Hitze, überträgt aber Farbe von einem Band auf Normalpapier und bestünde
diese Probe ebenfalls. In einem Einbaudruckwerk von etwa 1990 ist er weniger
üblich als ein Nadelwerk.

- [ ] **Letzte Unterscheidung, ohne Werkzeug:** Die **Rückseite des Papiers
      befühlen.** Ein Anschlagdruckwerk hinterlässt eine fühlbare **Prägung**,
      Thermotransfer nicht.

**Praktisch ändert das wenig** — beide Bauarten haben ein **Farbband als
Verschleißteil** und liefern **dauerhafte Ausdrucke.** Damit gilt gesichert:

- **Die Ausdrucke verblassen nicht.** Ein früher hier notierter Hinweis,
  Ausdrucke wegen Verblassens sofort zu fotografieren, war **falsch** und ist
  gegenstandslos. Fotografieren bleibt gute Dokumentation, aber ohne Zeitdruck.
- **Verschleißteile sind Farbband und Druckwerk**, nicht das Papier. Nach über
  dreißig Jahren nicht selbstverständlich zu ersetzen; Farbbänder trocknen aus,
  Nadeln brechen.
- **Jeder Ausdruck kostet Substanz.** Ausdrucke bewusst setzen, nicht beiläufig.
- Das Gerät braucht **Normalpapier**, kein Spezialpapier — Nachschub ist damit
  kein Problem, solange Rollenbreite und Kern passen.

- [ ] Rollenbreite und Kerndurchmesser messen, für den Fall des Nachkaufs

### Vermutung: Nadelwerk mit erschöpfter Endlos-Farbbandkassette

Arbeitsvermutung (2026-08-14): ein **Nadeldruckwerk mit umlaufender
Farbbandkassette**, deren Band **ausgeschrieben** ist. Dafür spricht ein
blasses Schriftbild bei ansonsten sauberem Zeichenaufbau.

**Das wäre der günstigste denkbare Verschleißfall.** Einbaudruckwerke dieser
Größe und Zeit verwenden fast durchweg genormte Endloskassetten — die
verbreitetste Familie stammt von Epson (`ERC`-Reihe, etwa `ERC-05`, `ERC-09`,
`ERC-22`), verbaut in unzähligen Registrierkassen, Taxametern, Waagen und
Messgeräten. **Ein guter Teil dieser Kassetten wird bis heute hergestellt**,
weil der Bestand an Altgeräten groß ist. Preislich bewegt sich das im Bereich
weniger Euro.

### Das Druckwerk ist ein herausnehmbares Modul (belegt 2026-08-14)

**Zwei Rändelschrauben von vorn, und der Drucker ist draußen.** Er ist als
wartbare Baugruppe konstruiert, nicht fest eingebaut.

Auf `../bilder/verkaufsanzeige/frontplatte_detail.webp` ist das rechts
erkennbar: eine **eigene, abgesetzte Frontplatte** mit **Rändelschraube**,
darunter ein **Sichtfenster mit gezahnter Abrisskante** und dem Papierstreifen
(`Klasse:1`). Die zweite Schraube liegt außerhalb des Bildausschnitts.

Das ist folgenreicher, als es klingt:

- **Farbband und Papier sind ohne Öffnen des Geräts erreichbar.**
- **Typenschild und Aufdrucke des Druckwerks werden lesbar**, sobald es
  herausgezogen ist — damit auch Hersteller und Typnummer, die zum Datenblatt
  führen.
- **Es muss eine Steckverbindung zur Hauptplatine geben**, sonst ließe sich das
  Modul nicht entnehmen. Damit liegt die Frage „**wie bekommt das Druckwerk
  seine Zeichen?**" an einem **zugänglichen Steckverbinder** — nicht irgendwo
  auf einer Platine im Inneren. Ein Zeichenstrom ließe sich dort abgreifen,
  ohne das Gerät selbst zu öffnen.

⚠️ Vor dem Herausziehen **Netzstecker ziehen.**

- [ ] Bauform und Polzahl des Steckverbinders notieren
- [ ] Aufdrucke auf Druckwerk und Farbbandkassette vollständig aufnehmen
- [ ] Fotos → `../bilder/`

**Nächster Schritt:**
- [ ] **Aufdruck der Kassette vollständig notieren** — Hersteller, Typnummer,
      Farbe. Das ist die Bestellnummer; danach lässt sich unmittelbar suchen.
- [ ] Ist ein **Aufdruck am Druckwerk selbst** lesbar (Epson `M-…`, Seiko,
      Citizen)? Der führt zum Datenblatt des Werks — und beantwortet nebenbei
      die offene Frage, **wie das Werk seine Zeichen bekommt** (siehe unten),
      ohne dass etwas aufgeschraubt werden muss.

**Wenn ein frisches Band eingelegt ist**, lohnt sich der eine geplante
Probeausdruck eines Datensatzes deutlich mehr: sauber lesbar, und als
Vergleichsvorlage für das, was später über die RS-232 ankommt.

Ein blasses Schriftbild ist übrigens **kein** Hinweis auf ein defektes
Druckwerk. Erst wenn ganze Punktzeilen fehlen, ist eine Nadel gebrochen — und
das lässt sich am vorhandenen Ausdruck bereits prüfen.

- [ ] Fehlen im Schriftbild durchgehend einzelne Punktzeilen?

### Offen: Wie bekommt der Drucker seine Zeichen?

Unabhängig von der Bauart ist die **Anbindung** noch ungeklärt — bekommt das
Druckwerk fertige **Zeichen** von der Hauptplatine, oder wird der **Druckkopf
direkt** angesteuert? Das war ursprünglich die Frage, die über den Aufwand des
Auslesevorhabens entschied (`STAND.md`).

Durch die RS-232 ist sie für das Vorhaben **nicht mehr kritisch**, bleibt aber
für das Verständnis des Geräts interessant — und wird beim Öffnen mit einem
Blick auf die Verbindung zum Druckwerk zu beantworten sein.

### Der Drucker ist die eigentliche Ausgabe des Geräts

**Die gespeicherten Messdaten lassen sich ausschließlich ausdrucken**, nicht
auf der Anzeige durchblättern (`MENUEBAUM.md`, `[S14]`). Bei vier Zeilen zu
etwa zwanzig Zeichen ist das folgerichtig — ein vollständiger Prüfbericht
passt dort nicht hinein.

Damit ist der Drucker kein Beiwerk, sondern der Hauptausgabeweg. Und damit
wird die **RS-232 auf der Rückwand** (Abschnitt E) zum einzigen
verschleißfreien Zugang zu den Daten des Geräts.

- [ ] Welches Papier passt, und ist Vorrat vorhanden?
- [ ] Zustand des Farbbands — kräftiges oder blasses Schriftbild?
- [ ] Fehlen im Schriftbild einzelne Punktzeilen? Das wäre eine gebrochene
      Nadel und ein Befund, den man am besten früh kennt.

### Tastatur — vollständig gelesen

Die Tastatur im Deckel ist **alphanumerisch nach Telefonbelegung**:

```
7 STU    8 VWX    9 YZ/          START
4 JKL    5 MNO    6 PQR          F
1 ABC    2 DEF    3 GHI          ↑
0        .        C              ↓
```

Damit lassen sich **Buchstaben eingeben**, nicht nur Ziffern — Prüflinge können
also mit Klartextnamen verwaltet werden. `C` ist Löschen/Korrektur.
Die drei Kontexttasten neben der Anzeige sind auf den Fotos als drei grüne
Felder rechts des Displays erkennbar, mit Strichen zu den Displayzeilen.

### Zubehör auf dem Foto

- **rund zehn rote Messleitungen** mit 4-mm-Steckern → passend zu den zehn
  grünen Buchsen
- eine **Prüfspitze** mit türkisem Griff und Metallspitze
- **Prüfklemmen/Abgreifer**, schwarz und rot
- **Netzleitung**, hell
- eine Leitung mit **Rundsteckverbinder und Überwurfmutter** — Verwendung offen,
  könnte zur Rückwand gehören
- kleiner Zettel/Etikett, unlesbar

Beim eigenen Gerät ist zu prüfen, ob dieses Zubehör vollständig mitgekommen ist.

**Nicht vorhanden: der Drehstrom-Adapter DS601** (Stand 2026-08-14). Damit
entfällt die Prüfung dreiphasiger Prüflinge — sie steht in diesem Projekt nicht
an und ist beim Kartieren nur insoweit interessant, als das Menü vermutlich
einen entsprechenden Eintrag anbietet, der ins Leere führt.

Das **DS601-Datenblatt bleibt trotzdem die Leitquelle** (`../QUELLEN.md`): Es
ist bislang der einzige öffentlich auffindbare Beleg, dass der µP601 existiert,
und alles, was über Bauart und Zweck des Geräts dokumentarisch gesichert ist,
stammt daraus. Praktisch zweitrangig, dokumentarisch erstrangig.

### Rückwand — aufgenommen 2026-08-14

Quelle: `../bilder/verkaufsanzeige/rueckwand.webp`

| Element | Beschriftung | Bemerkung |
|---|---|---|
| **Sub-D-Buchse, 25-polig** | **`V.24/RS-232C`**, darüber **`BAUD 4800`** | **Datenschnittstelle vorhanden** — siehe Abschnitt E |
| Rundes rotes Bauteil | **`F1`**, Aufdruck `16` | Zuordnung offen: Sicherung, Melder oder Taster |
| Wippschalter | **`Summer/Buzzer`** · **`Ein/On`** / **`Aus`** | akustische Rückmeldung abschaltbar |
| **Lüfter** mit Schutzgitter, mittig | — | aktive Belüftung; passt zu einem Gerät, das Prüfströme im Amperebereich liefert |
| Sicherungshalter, Schraubkappe | **`2A/250V`** | Geräteabsicherung |
| Lüftungsschlitze | — | oberer Rand |
| **Fest angeschlossene Netzleitung** mit Zugentlastung | — | siehe unten |

### Die eigene Stromversorgung läuft über eine feste Leitung

**Zur Vermeidung eines Missverständnisses:** Der µP601 hat sehr wohl einen
Kaltgeräte-Einbaustecker — aber **auf der Front, und als Prüfanschluss.**
Seine *eigene* Stromversorgung bezieht er über eine **fest angeschlossene
Netzleitung** mit Zugentlastung auf der Rückwand.

Damit ist die früher offengelassene Möglichkeit widerlegt, der Stecker auf der
Front sei der Netzeingang des Geräts. Er ist das, was Piktogramm 3 zeigt: der
Anschluss für die **Leitungsprüfung.**

### Warum die Leitungsprüfung in der Medizintechnik einen eigenen Prüfschritt hat

Abnehmbare **Geräteanschlussleitungen** sind in Kliniken und Praxen ein
eigenständiges Prüfobjekt, und das aus praktischen Gründen:

- Sie werden **häufiger bewegt, getreten und eingeklemmt** als das Gerät selbst
  — Betten, Rollstative, fahrbare Geräte.
- Sie sind **austauschbar und wandern zwischen Geräten.** Eine Leitung, die
  gestern an einem geprüften Gerät hing, hängt heute an einem anderen.
- Ein unterbrochener **Schutzleiter in der Zuleitung** hebt die Schutzmaßnahme
  eines Schutzklasse-I-Geräts vollständig auf, ohne dass die Funktion des
  Geräts darunter leidet — der Fehler bleibt also unbemerkt.

Deshalb hat der µP601 dafür einen eigenen Anschluss und einen eigenen
Prüfschritt: Schuko-Stecker der Leitung in die **Prüfsteckdose**,
Kupplungsende auf den **Kaltgeräte-Einbaustecker**, und das Gerät misst über
die geschlossene Schleife.

- [ ] Im Menü nachsehen, wie dieser Prüfschritt heißt, und welche Größen er
      misst — Durchgang allein, oder auch Isolation und Widerstandswert

### `Summer/Buzzer` abschaltbar

Ein eigener Schalter für die akustische Rückmeldung. Das ist ein Hinweis auf
den vorgesehenen Einsatz: In einem Prüfablauf mit Handgriffen am Prüfling
quittiert ein Summer jeden Schritt, ohne dass man auf die Anzeige sehen muss —
und in einer ruhigen Umgebung schaltet man ihn ab.

- [ ] Steht der Schalter derzeit auf `Ein` oder `Aus`?
- [ ] Wann summt das Gerät — Tastendruck, Schrittende, Fehler?

### Typenschild — aufgenommen 2026-08-14

Quelle: `../bilder/verkaufsanzeige/typenschild.webp`

```
BENDER ⚡  µP 601-1
SICHERHEITSTESTER / SAFETY - TESTER

Schutzklasse / Protection class:        I
Nennspannung / Rated voltage:           U_N  = AC 48…62 Hz 230 V
Leistungsaufnahme / Rated supply power: P_in  = 150 VA
Ausgangsleistung / Rated output power:  P_out = 3680 VA
Betriebsart / Operation class:          DB / continuous

Artikel-Nr. / Art. no.: B928161
Werk-Nr. / Serial-no.:  600521        IVM 429 D
```

Daneben ein zweiter Aufkleber:

```
Quality System Certified · Det Norske Veritas · ISO 9001
BENDER
Dipl.-Ing. W. Bender GmbH+CoKG
Postf. 1161 · D-35301 Grünberg
Tel. (06401) 807-0 · Fax 807259
```

Sowie eine **Prüfplakette „Nächster Prüftermin"** mit den Jahresfeldern
`98 · 99 · 00 · 01 · 02 · 03` und Monatsfeldern `1`–`12`, gekennzeichnet im
Bereich der frühen Jahre. Das Gerät stand also **Ende der 1990er im
regelmäßigen Prüfumlauf** — es war Betriebsmittel, nicht Reserve.

### Was das Typenschild klärt

**1. `IVM 429 D` steht auf dem Typenschild** — neben der Werk-Nummer.

Damit ist die Deutung entschieden: **keine Angabe des Vorbesitzers**
(Hypothese B ist erledigt), sondern eine **werkseitige Kennung der
Geräteausführung**, die das Gerät auch beim Einschalten anzeigt. Das
abschließende `D` als Sprachkennung fügt sich weiterhin.

**2. `P_out = 3680 VA` = 230 V × 16 A.**

Die Ausgangsleistung ist exakt die Anschlussleistung eines 16-A-Stromkreises.
Sie ist keine erzeugte Leistung, sondern die **Durchleitung zur
Prüfsteckdose** — das Gerät darf einen Prüfling bis 16 A versorgen. Das deckt
sich mit dem DS601-Datenblatt („maximal 16 A pro Phase") und mit dem
gemessenen Schutzleiter-Prüfstrom von 16 A.

**3. `P_in = 150 VA`** ist der Eigenverbrauch — rund 0,65 A. Damit ist auch die
Rückwand erklärt:

| Element | Wofür |
|---|---|
| Sicherung **2 A / 250 V** | die **Geräteelektronik**, passend zu 150 VA |
| **`F1`**, rotes Bauteil mit Aufdruck `16` | naheliegend: **16-A-Schutzschalter für die Prüfsteckdose** — der Strompfad zum Prüfling, den die 2-A-Sicherung nicht abdecken kann |

Damit ist die offene Frage zu `F1` mit hoher Wahrscheinlichkeit beantwortet.
Es wären zwei getrennte Schutzorgane für zwei getrennte Strompfade — logisch
und bei Prüfgeräten üblich.

- [ ] Aufdruck von `F1` aus der Nähe lesen und bestätigen

**4. `48…62 Hz`** — das Gerät arbeitet an 50- wie an 60-Hz-Netzen.

**5. `DB / continuous`** — Dauerbetrieb, keine Einschaltdauerbegrenzung für
das Gerät selbst. Für den **Prüfschritt** gilt das nicht: 16 A durch einen
Prüfling sind naturgemäß kurzzeitig.

### 🔑 Datierung: frühestens Juli 1993

Die Herstelleranschrift trägt die **fünfstellige Postleitzahl `D-35301`**.
Fünfstellige Postleitzahlen gelten in Deutschland **seit dem 1. Juli 1993.**

**Damit ist das Gerät frühestens von Mitte 1993** — die vorherige Schätzung
„etwa 1990–1993", abgeleitet aus den Normausgaben von 1988 und 1990, ist nach
unten zu korrigieren. Zusammen mit der Prüfplakette (Jahresfelder ab `98`)
ergibt sich ein Bild: **gebaut in den 1990er Jahren, in Betrieb bis mindestens
Anfang der 2000er.**

Der Firmenname **Dipl.-Ing. W. Bender GmbH + Co KG** ist die historische
Firmierung des heutigen Bender GmbH & Co. KG.

### Was Abschnitt A noch offen lässt
- [ ] Lage des **Netzschalters** — auf der Rückwand ist keiner erkennbar,
      der einzige Wippschalter gehört zum Summer
- [ ] Kalibrier- und Inventaraufkleber
- [ ] Beschriftung **neben** den sechs Piktogrammen und um den Drucker herum
- [ ] Lage des Netzschalters
- [ ] Papiervorrat und Papiertyp des Druckers
- [ ] eigene Fotos in `../bilder/`, unabhängig von der Verkaufsanzeige

### Durchgangstests — ohne Öffnen, ohne Netz

Mit einem Ohmmeter, **Netzstecker gezogen**:

- [ ] gelbe Buchse ↔ Schutzkontakt der Schuko-Prüfsteckdose
- [ ] gelbe Buchse ↔ Schutzkontakt des eigenen Netzsteckers
- [ ] grüne Buchsen untereinander (1↔2, 1↔3, … stichprobenartig)
- [ ] grüne Buchsen ↔ gelbe Buchse
- [ ] Schutzkontakt Prüfsteckdose ↔ Schutzkontakt Kaltgeräte-Einbaustecker

⚠️ **Wichtige Einschränkung:** In einem Sicherheitstester sind diese Anschlüsse
über **Relais** geführt. Im ausgeschalteten Zustand sind die Relais abgefallen,
gemessen wird also nur die **Ruhelage**. „Kein Durchgang" beweist deshalb
**keine** Trennung — es kann schlicht ein offenes Relais dazwischenliegen.
Umgekehrt ist ein *gefundener* Durchgang eine harte Aussage.

---

## B — Einschalten und Startbildschirm

- [ ] Was steht beim Start auf der Anzeige — **wörtlich**, Zeile für Zeile
- [ ] **Softwarestand / Versionsnummer**
- [ ] Läuft ein **Selbsttest**? Was wird angezeigt, wie lange dauert er
- [ ] Wird ein **Kalibrierdatum** oder eine Betriebsstundenzahl genannt
- [ ] Erscheint eine Fehler- oder Warnmeldung
- [ ] Verhalten der Anzeige: Kontrast, Ausfälle einzelner Segmente/Pixel

**Ergebnis (2026-08-14, erste Beobachtung — noch nicht vollständig):**

Der Startbildschirm zeigt

- den **Namen des früheren Besitzers**
- **oben rechts** die Zeichenfolge **`IVM429 D`**

Noch nicht aufgenommen: der vollständige Wortlaut aller vier Zeilen, die
genaue Position jeder Angabe, Selbsttest, Kalibrierdatum.

### 🔑 Das Gerät prüft beim Einschalten die Lage seines eigenen Netzsteckers

**Befund 2026-08-15:** Beim Einschalten stellt der µP601 fest, **welcher Stift
seines eigenen Schuko-Steckers die Phase führt.** Steckt der Stecker
„falsch herum", fordert er auf, **auszuschalten und den Stecker zu drehen.**

- [ ] Wortlaut der Meldung wörtlich notieren
- [ ] Was zeigt er, wenn die Lage stimmt — eine Bestätigung, oder gar nichts?
- [ ] Prüft er auch bei jedem Einschalten neu, oder merkt er sich etwas?

### Warum das für dieses Gerät zwingend ist

Ein Schuko-Stecker ist **umkehrbar** — er passt in beiden Lagen, und damit
liegt L mal am einen, mal am anderen Stift. Für die meisten Geräte ist das
belanglos. Für einen Sicherheitstester ist es die Grundlage von allem:

**1. Die Fehlerbedingungen sind seitenabhängig.** Das Gerät stellt im
Prüfablauf gezielt Erst-Fehler her — das DS601-Datenblatt nennt
**„Netzleiter offen"** und **„Phase vertauscht"**. Beide Begriffe setzen
voraus, dass das Gerät weiß, **welcher Leiter die Phase ist.** „Netzleiter
offen" bedeutet je nach Seite etwas völlig anderes: Wird N aufgetrennt, liegt
der Prüfling weiter an Potential; wird L aufgetrennt, ist er spannungsfrei.
Ein Gerät, das das verwechselt, misst Unsinn und meldet trotzdem „bestanden".

**2. Ableitströme sind auf die Phase bezogen.** Die Ströme, die über Gehäuse,
Schutzleiter und Anwendungsteil abfließen, stammen aus der Netzspannung gegen
Erde. Welcher der beiden Leiter diese Spannung führt, bestimmt Größe und
Bewertung des Messwerts.

**3. „Phase vertauscht" lässt sich nur herstellen, wenn eine Ausgangslage
bekannt ist.** Das Gerät dreht L und N an der **Prüfsteckdose** um — dazu muss
es die eigene Einspeisung kennen.

### Die Bauentscheidung dahinter

Bender hätte das intern lösen können: zwei zusätzliche Relais in der eigenen
Zuleitung, die bei falscher Lage umschalten. Stattdessen **meldet das Gerät
und verlangt einen Handgriff.**

Das ist die konservativere Lösung, und für ein Prüfgerät die richtige. Ein
Relais in der eigenen Netzzuleitung wäre ein Bauteil, dessen Versagen
unbemerkt bliebe und **jede folgende Messung still verfälschen** würde. Ein
Hinweis auf der Anzeige kann nicht klemmen.

Es passt zur Haltung, die das ganze Gerät zeigt: Lieber einen definierten
Zustand verlangen, als stillschweigend ausgleichen.

### Wie es das vermutlich feststellt — und was daraus folgt

Naheliegend ist eine **Spannungsmessung beider Netzleiter gegen den
Schutzleiter**. Im TN- oder TT-Netz liegt N nahe Erdpotential, L auf etwa
230 V gegen Erde. Der Unterschied ist eindeutig und mit einfachen Mitteln zu
erfassen.

Daraus folgen zwei Dinge, die im Alltag zählen:

- **Die Prüfung setzt einen funktionierenden Schutzleiter voraus.** Ohne
  brauchbaren Erdbezug ist keine Aussage möglich. Damit prüft das Gerät
  nebenbei **die Steckdose, an der es selbst hängt** — verweigert es an einer
  bestimmten Dose beharrlich den Dienst, lohnt der Blick auf deren
  Installation.
- **An einem IT-Netz oder hinter einem Trenntransformator** führen beide
  Leiter kein definiertes Potential gegen Erde. Dort dürfte die Erkennung
  fehlschlagen — kein Defekt, sondern eine Betriebsgrenze.

- [ ] Verhält sich das Gerät an verschiedenen Steckdosen gleich?
- [ ] Meldet es etwas Eigenes, wenn der Schutzleiter fehlt?

### Der Besitzername ist ein programmierbares Feld

Dass der Voreigentümer auf dem Startbildschirm steht, heißt: das Gerät
**speichert einen frei einzugebenden Betreibertext**. Dafür ist die
alphanumerische Tastatur da. Zwei Folgerungen:

- Es gibt irgendwo im Menü eine Stelle, an der dieser Text bearbeitet wird —
  ein guter Anker beim Kartieren in Abschnitt C.
- Der Text steht mit hoher Wahrscheinlichkeit auch im **Protokollausdruck**,
  als Kopfzeile. Das ließe sich am Drucker prüfen.

⚠️ **Den Text nicht überschreiben.** Er gehört zum Auslieferungszustand des
gebrauchten Geräts und ist die einzige Spur zur Herkunft — vergleichbar dem
Vorbesitzer-Hinweis, über den im Vorgängerprojekt die Gerätegeschichte
rekonstruiert wurde.

**Datenschutz:** Handelt es sich um eine **Einrichtung** (Klinik, Werkstatt,
Firma), darf der Name hier stehen und ist als Rechercheansatz brauchbar. Ist es
eine **natürliche Person**, gehört der Name nicht ins Repository — dann hier
nur „Personenname, lokal notiert" vermerken.

**Wortlaut:**

> _(noch nicht eingetragen — erst nach obiger Unterscheidung)_

### `IVM429 D` — Deutung offen

Position oben rechts, also abgesetzt vom Betreibertext. Zwei Lesarten:

**A — Softwarestand.** Die wahrscheinlichere. Eine kurze alphanumerische
Kennung in der oberen Bildschirmecke ist die übliche Stelle für die
Firmware-Version. Das abschließende **`D`** wäre dann die **Sprachvariante
(Deutsch)** — Bender liefert seine Geräte mehrsprachig aus.

Dazu passt, dass das DS601-Datenblatt Softwarestände ausdrücklich als
Verträglichkeitsbedingung führt:

> Achtung / Caution — Drehstromadapter nur in Verbindung mit
> Software-Versionen `ID..xxxXX` benutzen.

`ID..xxxXX` ist dort ein Platzhaltermuster, kein konkreter Stand; es belegt
aber, dass Bender Softwarestände in genau solchen kurzen Buchstaben-Ziffern-
Codes führt. Ob `IVM429 D` demselben Schema folgt, ist damit **nicht** bewiesen.

**B — Teil der Besitzerangabe.** Ein Abteilungs- oder Inventarkürzel des
Vorbesitzers, das mit in den Betreibertext eingegeben wurde. Weniger
wahrscheinlich, weil es räumlich abgesetzt steht.

### Tests, die das entscheiden

- [ ] Gibt es im Menü einen Eintrag „Version", „Software", „Info", „Gerät"?
      Erscheint dort dieselbe Zeichenfolge → **A bestätigt**
- [ ] Steht `IVM429 D` auch auf einem **Protokollausdruck**? Wo — im Kopf beim
      Betreibernamen oder in einer Fußzeile?
- [ ] Ist der Betreibertext editierbar, **ohne** dass `IVM429 D` mitwandert?
      → **A bestätigt**, B widerlegt
- [ ] Gibt es einen **Aufkleber mit Softwarestand** am Gehäuse oder auf der
      Rückwand? Bender beklebt Geräte damit häufig
- [ ] **Sprachprobe — jetzt gefahrlos durchführbar.** Am 2026-08-14 belegt:
      `F` auf dem Startbildschirm öffnet die Sprachauswahl **Englisch /
      Deutsch**, Auswahl über zwei Softkeys. Der Rückweg ist damit bekannt,
      die Umschaltung folgenlos.

      **Ablauf:** auf Englisch schalten → Startbildschirm ansehen → wird aus
      `IVM429 D` ein `IVM429 E` / `IVM429 GB` o. ä.?

      | Ergebnis | Schluss |
      |---|---|
      | Buchstabe ändert sich mit der Sprache | `D` = Sprachkennung, `IVM429` = Softwarestand → **A bestätigt** |
      | Zeichenfolge bleibt unverändert | `D` gehört fest zur Version, oder es ist doch Hypothese B |

      Danach **zurück auf Deutsch** — der Menübaum wird durchgehend auf
      Deutsch kartiert (Projektsprache, und die deutschen Bezeichnungen lassen
      sich mit den Bender-Unterlagen abgleichen).

      Dass es überhaupt eine Sprachumschaltung gibt, stützt Hypothese A schon
      für sich: ein mehrsprachig ausgeliefertes Gerät braucht eine
      Sprachkennung im Softwarestand.

**Warum das wichtig ist** — und warum es das auch ohne den DS601 bleibt:

Der **DS601 gehört nicht zum vorhandenen Zubehör** (Stand 2026-08-14). Die
Verträglichkeitsfrage aus dem Datenblatt ist damit **praktisch gegenstandslos**;
Drehstromprüfung steht nicht an. Der Softwarestand bleibt trotzdem zu klären:

- Er ist die **Bezugsgröße für alles, was hier über den Funktionsumfang
  festgehalten wird.** Ein Menübaum ohne Angabe, zu welchem Stand er gehört,
  ist für Dritte nur die halbe Aussage — spätere Stände können anders aussehen.
- Er ist die **einzige Kennung, unter der sich ein Softwarestand überhaupt
  benennen lässt**, falls die Firmware je gesichert wird.
- Bei einer Anfrage an Bender oder einen Kalibrierdienst ist er nach der
  Sachnummer die **zweitwichtigste Angabe**.

---

## C — Menübaum vollständig kartieren

**Das ist der Kern dieser Aufnahme.** Ohne Handbuch ist der Menübaum die
Funktionsbeschreibung des Geräts.

### Was die Bedienung vorgibt

Bedient wird über **drei Kontexttasten neben einem vierzeiligen Display**
(Abschnitt A). Daraus folgt die Struktur jedes Bildschirms — und damit das
Aufnahmeformat:

- Von vier Zeilen sind **drei mit je einer Taste belegt**. Die vierte trägt
  aller Wahrscheinlichkeit nach Titel, Status oder Messwert.
- **Welche der vier Zeilen unbelegt ist, gehört als Erstes festgestellt** —
  oben oder unten. Das ist die Grundform der gesamten Bedienoberfläche.
- Jeder Bildschirm ist damit ein Tripel aus höchstens drei Auswahlmöglichkeiten.
  In tieferen Ebenen wird eine davon fast sicher „zurück" bedeuten.
- Ein Menübaum mit drei Optionen pro Ebene wird **tief statt breit**. Auf
  Sackgassen und Wiederholungen achten: derselbe Bildschirm kann über mehrere
  Wege erreichbar sein.

**Aufnahmeformat** — pro Bildschirm alle vier Zeilen wörtlich, mit Markierung,
welche Zeile zu welcher Taste gehört, und wohin die Taste führt. Zum Beispiel:

```
[Bildschirm 1 — Grundzustand nach dem Einschalten]
Zeile 1:  <Text>            (keine Taste)
Zeile 2:  <Text>   ← Taste 1  → führt zu Bildschirm 2
Zeile 3:  <Text>   ← Taste 2  → führt zu Bildschirm 7
Zeile 4:  <Text>   ← Taste 3  → führt zu Bildschirm 12
```

Weil die Zeilen kurz sind, wird Bender die Beschriftungen abgekürzt haben —
deshalb **wörtlich** abschreiben, samt Abkürzungspunkten und Sonderzeichen.
Die Auflösung der Abkürzungen ergibt sich später aus dem Zusammenhang.

### Nachtrag (2026-08-14): Es gibt eine vollständige Tastatur

Die Überlegungen oben entstanden, als nur die drei Softkeys bekannt waren.
Mit dem Fund der zweiten Tastengruppe — **Nummernblock, Start, F, ↑, ↓** —
sind zwei davon zu berichtigen:

**Berichtigt: „höchstens drei Auswahlmöglichkeiten pro Bildschirm".**
Mit **↑/↓** kann eine Liste länger sein als die Anzeige. Die drei Softkeys
sind dann keine Begrenzung der Optionen, sondern nur die drei gerade
sichtbaren. Beim Kartieren deshalb **auf jedem Bildschirm ↑ und ↓ betätigen**
und prüfen, ob weitere Einträge nachrücken — sonst bleibt der halbe Menübaum
unentdeckt. Damit fällt auch die Vermutung „tief statt breit"; der Baum kann
ebenso gut flach und lang sein.

**Berichtigt: „Schnittstelle ist der einzige Weg für Dateneingabe".**
Der Nummernblock erledigt das direkt am Gerät. Abschnitt E bleibt wertvoll,
aber nicht mehr notgedrungen.

**Neu hinzugekommen — die Taste `F`.** Eine Funktions- oder Umschalttaste ist
der übliche Ort für Sonderfunktionen und Tastenkombinationen, und damit auch
für **Service- und Kalibriermenüs**. Das ist interessant, aber genau deshalb:

⚠️ **`F` erst systematisch erkunden, wenn der normale Menübaum kartiert und
die Daten des Vorbesitzers gesichert sind (Abschnitt D).** Blind Kombinationen
zu probieren — besonders `F` beim Einschalten gehalten — kann in einem
Servicemodus landen, der Kalibrierwerte oder den Speicher berührt. Zuerst
notieren, was `F` im Normalbetrieb allein bewirkt.

### Erste Befunde zur Bedienlogik (2026-08-14)

| Beobachtung | Bedeutung |
|---|---|
| **`START` kehrt zum Startbildschirm zurück** | Die Taste ist eine **Heim-/Abbruchtaste**, kein Messungsauslöser. Ob sie *im Prüfablauf* zusätzlich startet, ist offen. |
| **`F` vom Startbildschirm → Sprachauswahl** (Englisch / Deutsch) | `F` ist keine Umschalttaste, sondern öffnet ein **kontextabhängiges Menü**. Was `F` tut, hängt davon ab, wo man steht. |
| Die Auswahl erfolgt über **2 der 3 Softkeys** | Bestätigt: die Softkeys zeigen nur die *gerade gültigen* Optionen; nicht belegte bleiben leer. |

**Das Wichtigste daran: es gibt einen sicheren Rückweg.** Mit `START` kommt man
aus jeder Lage zum Startbildschirm zurück. Damit ist das Kartieren des
Menübaums risikoarm — man kann sich nicht verlaufen, und jeder Zweig lässt sich
vom selben definierten Ausgangspunkt neu anlaufen.

Daraus folgt das Vorgehen: **jeden Zweig vom Startbildschirm aus anlaufen**,
bis zum Ende verfolgen, mit `START` zurück, nächster Zweig. Kein
Rückwärtstasten durch Ebenen, keine Zweifel darüber, wo man gerade ist.

**Zwei Menüwege sind zu kartieren, nicht einer:**

1. der Weg über die **drei Softkeys** vom Startbildschirm aus
2. der Weg über **`F`** — und zwar `F` an *jeder* Stelle des Baums, weil es
   kontextabhängig ist. Ein `F` tiefer im Baum zeigt etwas anderes als
   `F` auf dem Startbildschirm.

Beim Notieren deshalb festhalten, **von wo aus** `F` gedrückt wurde.

### Vorgehen

Jeden Menüpunkt aufrufen, Beschriftung wörtlich notieren, eine Ebene
tiefer gehen, mit `START` zurück. Nichts bestätigen, was eine Messung startet
oder etwas speichert — dazu Abschnitt F. Bei Unsicherheit `START` drücken
und notieren.

- [ ] Oberste Ebene vollständig durchgehen
- [ ] Jede Ebene darunter, bis nichts Neues mehr kommt
- [ ] **Prüfschritte / Prüfabläufe**: welche Messungen bietet das Gerät an
- [ ] **Klassifizierung**: Schutzklasse, Anwendungsteil-Typ, Drehstromgerät
- [ ] **Grenzwerte**: nach welcher Norm, einstellbar oder fest
- [ ] **Einstellungen**: Sprache, Datum/Uhrzeit, Schnittstelle, Drucker, Kontrast
- [ ] **Speicher- und Datenfunktionen**: Prüflingsverwaltung, Protokolle
- [ ] **Service-/Kalibriermenü** — falls vorhanden: nur ansehen, **nichts ändern**
- [ ] Versteckte Menüs? Tastenkombination beim Einschalten (erst notieren, was
      normal passiert, bevor experimentiert wird)

Ergebnis als Baum festhalten, Einrückung = Ebene, Beschriftungen wörtlich.

**Ergebnis:**

> _(noch nicht aufgenommen)_

---

## D — Daten des Vorbesitzers

Ein Gerät aus dem Klinikbetrieb hat gespeicherte Prüflinge und Protokolle.
Das sagt, wofür es benutzt wurde — und ist unwiederbringlich, wenn es beim
Herumprobieren gelöscht wird.

- [ ] Sind Prüflinge oder Protokolle gespeichert? Wie viele
- [ ] Ältestes und jüngstes Datum → Betriebszeitraum des Geräts
- [ ] Wie sieht ein Datensatz aus: welche Felder, welche Messwerte
- [ ] Auslesen und sichern, **bevor** eigene Prüfungen gefahren werden

⚠️ **Keine Löschfunktion aufrufen, kein Speicher zurücksetzen, kein
Werksreset.** Das ist die einzige Kopie.

Hinweis Datenschutz: Prüfprotokolle aus dem Klinikbetrieb können Standort- und
Personennamen enthalten. Solche Daten gehören nicht ins Repository — für die
Analyse reicht Struktur und Zeitraum.

**Ergebnis:**

> _(noch nicht aufgenommen)_

---

## E — Schnittstelle

Falls das Gerät eine Datenschnittstelle hat, ist das der größte Hebel dieser
ganzen Aufnahme: sie ist rein passiv erschließbar und liefert Struktur, an die
man über die Anzeige nie kommt.

### Belegt (2026-08-14): Es gibt eine RS-232

Auf der Rückwand sitzt eine **25-polige Sub-D-Buchse**, beschriftet
**`V.24/RS-232C`**, darüber **`BAUD 4800`**.

**Das ist der wichtigste Einzelbefund dieser ganzen Aufnahme.** Konsequenzen:

- Der eingebaute Drucker ist **nicht** die einzige Datenausgabe. Es gibt einen
  zweiten, elektrischen Weg aus dem Gerät heraus.
- Das **Vorhaben „Displaymodul für den Ausdruck"** (`STAND.md`) wird damit
  ungleich einfacher: kein Abgreifen eines Druckkopfsignals, sondern ein
  serieller Datenstrom, der sich mit handelsüblichen Mitteln mitschneiden lässt.
- Die **Übertragungsrate steht auf der Rückwand**: `4800`. Sie muss nicht
  erraten werden.
- Beim Vorgängerprojekt (UNIMET 1000 ST) war die RS-232 vollständig
  dokumentiert, mit Prüfschritten und Befehlen als Zahlencodes. Ob der µP601
  ebenfalls Befehle **entgegennimmt** oder nur sendet, ist offen.

### Nächste Schritte an der Schnittstelle

- [x] Bauform und Beschriftung — 25-polig, `V.24/RS-232C`, `BAUD 4800`
- [ ] **Buchse oder Stecker?** Auf dem Foto sieht es nach einer Buchse mit
      Stiften aus — vor dem Kabelkauf am Gerät nachsehen
- [ ] **Belegung ermitteln.** Bei 25-poligem V.24 ist die Norm-Belegung zu
      erwarten (TxD 2, RxD 3, GND 7), aber nicht garantiert
- [ ] Bietet das **Menü** Übertragungsparameter an? Datenbits, Parität,
      Stoppbits, Handshake — die `4800` allein reicht nicht.
      **Erwartungswert für ein Gerät dieser Zeit: 8N1 oder 7E1.**
      Zu suchen im `F`-Zweig, wo auch Uhr und Messdatenverwaltung liegen
      (`MENUEBAUM.md`, `[S06]`)
- [ ] **Passiv mitschneiden**, während ein Selbsttest oder eine Messung läuft.
      Nur empfangen, nichts senden — das ist der risikoloseste erste Versuch
- [ ] Sendet das Gerät **dasselbe wie auf dem Papier**, oder ein eigenes Format?
- [ ] Reagiert es auf empfangene Zeichen?

⚠️ Der **Pegel ist echtes V.24** (±12 V), kein TTL. Ein USB-RS-232-Adapter mit
Pegelwandler gehört dazu; ein direkt angeschlossener Mikrocontroller-UART wird
beschädigt.

Falls sich ein Befehlssatz zeigt, entsteht daraus ein eigenes Dokument
`RS232_PROTOKOLL.md` nach dem Muster des Vorgängerprojekts.

Beim UNIMET 1000ST war die RS-232 vollständig dokumentiert (Prüfschritte und
Befehle als Zahlencodes). Ob der µP601 etwas Ähnliches kann, ist offen — er
ist eine andere Baureihe. Falls ja, entsteht daraus ein eigenes Dokument
`RS232_PROTOKOLL.md` nach dem Muster des Vorgängerprojekts.

**Ergebnis:**

> _(noch nicht aufgenommen)_

---

## F — Messungen an einem harmlosen Prüfling

Erst wenn A bis E aufgenommen sind. Ziel ist nicht, etwas zu prüfen, sondern
zu sehen, **wie das Gerät einen Prüfablauf führt** und welche Werte es ausgibt.

Prüfling wählen, dem nichts passieren kann:

- **Geeignet:** einfaches Schutzklasse-I-Gerät mit Metallgehäuse und ohne
  Elektronik — Tischlampe mit Metallfuß, alte Bohrmaschine, Wasserkocher.
  Der Schutzleiterwiderstand ist daran gut nachvollziehbar.
- **Ungeeignet:** alles mit Schaltnetzteil, Mikrocontroller oder
  Überspannungsschutz. Die Isolationsprüfung mit 500 V DC kann es beschädigen,
  und die Y-Kondensatoren verfälschen den Ableitstrom.
- **Auf keinen Fall:** medizinische Geräte, an denen etwas hängt, oder Geräte,
  deren Ausfall teuer wird.

- [ ] Prüfablauf einmal vollständig durchlaufen, jeden Schritt notieren
- [ ] Welche Messwerte mit welcher Einheit und Auflösung erscheinen
- [ ] Welche Grenzwerte das Gerät ansetzt und wie es Bestehen/Nichtbestehen meldet
- [ ] Wie die Fehlerbedingungen eingeleitet werden (automatisch oder Handgriff)
- [ ] Ergebnisse mit den Grenzwerten der IEC 60601-1 vergleichen — stimmt der
      Erwartungsrahmen oben?
- [ ] Leerlaufmessung ohne Prüfling zum Vergleich

**Ergebnis — erste Messung am 2026-08-14**

### Schutzleiterprüfung einer Geräteanschlussleitung

Über einen Menüpfad gefunden, der **nur die Leitung** prüft — also der
Prüfschritt zu Piktogramm 3 auf der Frontplatte.

| | |
|---|---|
| **Messwert** | **0,109 Ω** |
| Prüfling | Geräteanschlussleitung (Schuko ↔ Kaltgerätekupplung) |
| Beobachtung | **Die Leitung wird während der Messung deutlich warm.** |

- [ ] Menüpfad dorthin nachtragen und in `MENUEBAUM.md` einordnen
- [ ] Nennt das Gerät den **Prüfstrom**? Und einen **Grenzwert**?
- [ ] Meldet es Bestanden / Nicht bestanden, oder nur den Zahlenwert?
- [ ] Kabellänge und Querschnitt notieren — ohne sie ist der Messwert nicht
      einzuordnen

### Einordnung des Messwerts

**0,109 Ω ist ein unauffälliger Wert für eine Netzleitung.** Er setzt sich
zusammen aus dem Leiterwiderstand und den Übergangswiderständen an Stecker,
Kupplung und den Kontakten des Prüfgeräts.

Zur Größenordnung: Kupfer hat rund **0,0175 Ω·mm²/m**. Für den Schutzleiter
einer Leitung ergibt das

| Querschnitt | Widerstand je Meter |
|---|---|
| 0,75 mm² | ≈ 0,023 Ω/m |
| 1,0 mm² | ≈ 0,018 Ω/m |
| 1,5 mm² | ≈ 0,012 Ω/m |

Bei einer kurzen Leitung liegt der Leiteranteil damit deutlich unter dem
Messwert — der Rest sind Übergangswiderstände, was normal ist. Bei einer
langen Leitung kann der Leiteranteil den Wert dagegen fast allein erklären.
**Deshalb gehören Länge und Querschnitt zum Messwert dazu**, sonst ist er
nicht zu beurteilen.

Den maßgeblichen **Grenzwert** setzt nicht die Faustregel, sondern das Gerät
selbst — nachzulesen in `Grenzwerteingabe` (`MENUEBAUM.md`, `[S16]`).

### Warum die Leitung warm wird — das ist Absicht

Die Erwärmung belegt einen **hohen Prüfstrom**, und der ist bei dieser Messung
vorgeschrieben. Der Grund ist einleuchtend, sobald man ihn einmal gehört hat:

> Ein Schutzleiter, dessen Litze zu neunzig Prozent durchtrennt ist, zeigt
> einem gewöhnlichen Ohmmeter mit wenigen Milliampere **einen tadellosen
> Wert.** Die verbliebenen Drähte reichen für die Messung — aber nicht für den
> Fehlerstrom, den sie im Ernstfall führen müssten.

Erst ein Prüfstrom in der Größenordnung mehrerer Ampere bringt einen solchen
Restquerschnitt zum Vorschein: Der Spannungsabfall steigt messbar, die Stelle
erwärmt sich. **Die Erwärmung ist also kein Nebeneffekt, sondern der Sinn des
Verfahrens.**

Dass das Gerät diese Ströme liefert, erklärt zugleich zwei Beobachtungen von
der Aufnahme der Baugruppen: den **Lüfter** auf der Rückwand und die
**Absicherung mit 2 A** trotz kurzzeitig hoher Prüfströme — die Energie kommt
aus einem Transformator, nicht direkt aus dem Netz.

### Vorsicht bei dieser Messung

⚠️ **Während der Messung nichts bewegen.** Das Datenblatt des DS601 warnt
ausdrücklich davor, dass **„durch den hohen Messstrom Relaiskontakte […]
zerstört werden"** können, wenn während der Messung Erschütterungen auftreten.
Das gilt sinngemäß für die Kontakte im µP601 selbst und für Stecker und
Kupplung des Prüflings: Wackeln unter Last brennt Kontakte an.

⚠️ **Nicht unnötig wiederholen.** Jede Messung belastet Stromquelle,
Relaiskontakte und Prüfling. Für die Aufnahme genügt ein sauberer Durchgang je
Prüfschritt.

⚠️ **Die Leitung ausgelegt prüfen, nicht aufgewickelt.** Nicht wegen der
Induktivität — die liegt bei 50 Hz und wenigen Metern im Milliohm-Bereich und
ist gegenüber 0,109 Ω bedeutungslos. Sondern wegen der **Wärmeabfuhr**: Im
Bund addiert sich die Verlustwärme, die ausgelegt einfach abgestrahlt würde.

### Die Erwärmung selbst ist ein Diagnosemittel

Wenn die Leitung ohnehin warm wird, lohnt es, sie **unmittelbar nach der
Messung abzutasten:**

- **Gleichmäßig warm** → die Verlustleistung verteilt sich über die ganze
  Länge, der Leiter ist durchgehend in Ordnung.
- **Eine Stelle deutlich wärmer** → dort sitzt ein erhöhter Widerstand:
  angebrochene Litze, kalte Klemmstelle im Stecker, Quetschung. **Genau der
  Fehler, für den das Hochstromverfahren gemacht ist** — und er lässt sich mit
  der Hand orten, ohne weiteres Gerät.

Ein Gesamtwert im grünen Bereich schließt eine solche Stelle nicht aus: Ein
paar zusätzliche Milliohm gehen im Messwert unter, machen sich thermisch aber
bemerkbar.

- [ ] Bei künftigen Leitungsprüfungen die Leitung ausgelegt lassen und
      hinterher entlangtasten. Auffälligkeiten hier notieren.

### Gemessen: Der Prüfstrom beträgt 16 A (2026-08-14)

Mit der Stromzange am Prüfkabel erfasst: **16 A.**

Damit ist die Erwärmung vollständig erklärt:

| Größe | Wert |
|---|---|
| Prüfstrom | **16 A** |
| Widerstand der Leitung | 0,109 Ω |
| **Verlustleistung in der Leitung** | `I²·R` = **≈ 28 W** |
| **Spannungsabfall über die Leitung** | `I·R` = **≈ 1,74 V** |

28 W in einer Netzleitung sind erheblich — mehr als eine kleine Lötkolbenspitze.
Dass die Leitung „richtig warm" wird, ist damit keine Auffälligkeit, sondern
Arithmetik.

**Was daraus über die Quelle folgt:** Bei 1,74 V Abfall über den Prüfling muss
die Leerlaufspannung der Quelle nur wenige Volt betragen. Die aufgenommene
Leistung liegt damit in der Größenordnung von 30 bis 60 VA — bequem innerhalb
der **2 A / 250 V**, mit denen das Gerät abgesichert ist. Das bestätigt die
Annahme einer **Niederspannungs-Hochstromwicklung am Transformator.**

Es erklärt zugleich, warum die Prüfung **kurz** sein muss: Bei 16 A ist eine
Dauermessung weder für den Trafo noch für die Relaiskontakte zumutbar.

**Stromart: Wechselstrom** (bestätigt 2026-08-14). Der Prüfstrom ist
**16 A AC**.

Das passt zur einfachsten denkbaren Bauweise: eine **Niederspannungswicklung
des Netztransformators, über Relais direkt auf den Prüfkreis geschaltet.**
Kein Gleichrichter, keine Regelung, keine Siebung — der Strom stellt sich aus
Wicklungsspannung und Prüflingswiderstand ein. Robust, und für ein Gerät von
1990 die naheliegende Lösung.

Streng genommen misst das Gerät damit eine **Impedanz**, nicht einen reinen
Widerstand. Bei 50 Hz und Werten um 0,1 Ω ist der induktive Anteil einer
Netzleitung jedoch vernachlässigbar — der angezeigte Wert ist praktisch der
Wirkwiderstand.

Nebenbei fügt sich die Zahl ins Gesamtbild: Prüfsteckdose, Leitungsprüfung und
Prüfstrom liegen alle in der **16-A-Welt** eines gewöhnlichen Schuko-Stromkreises.
Auch das DS601-Datenblatt nennt für Prüflinge „maximal 16 A (pro Phase)".
**Das Gerät nennt den Prüfstrom nirgends.** Es zeigt ausschließlich den
**Widerstandswert** an und druckt ihn aus (belegt 2026-08-14).

Damit ist die Zangenmessung **die einzige Quelle für diese Angabe** — sie steht
weder auf der Anzeige noch im Ausdruck, und ein Handbuch, das sie nennen
könnte, existiert nicht. Ein Befund, den es ohne eigene Messung nicht gäbe.

- [ ] Dauer der Strombeaufschlagung grob stoppen

### Jede Messung wird gedruckt — lässt sich das abschalten?

Der Messwert wird **automatisch ausgedruckt**. Beim Erkunden der Prüfschritte
kostet das Farbband, ohne dass der Ausdruck jedes Mal gebraucht würde.

- [ ] Gibt es eine Einstellung, den Ausdruck zu **unterdrücken**? Zu suchen im
      `F`-Zweig (`MENUEBAUM.md`, `[S06]`) oder als eigener Punkt im
      Prüfablauf.
- [ ] Falls nicht: Beim weiteren Kartieren Prüfschritte **nur einmal**
      auslösen und die Anzeige abschreiben, statt Messungen zu wiederholen.
- [ ] Druckt auch der Zweig **`Nur Messgerät`** (`[S17]`)? Falls dort nicht
      gedruckt wird, ist er nicht nur datenbankschonend, sondern auch
      farbbandschonend — und damit erst recht der richtige Ort zum Erproben.

### Vorhaben: Prüfstrom mit der Stromzange messen

Um die Überschlagsrechnung durch einen Messwert zu ersetzen, soll der
Prüfstrom mit einer **Stromzange** erfasst werden — an einem Prüfkabel, dessen
Adern einzeln geführt, aber isoliert sind, sodass die Zange um **einen**
Leiter gelegt werden kann.

**Erst der billigere Versuch, bevor etwas gebaut wird:**

Bei der Prüfung einer Geräteanschlussleitung fließt der Prüfstrom **nur durch
den Schutzleiter** der Leitung — vom Schutzkontakt der Prüfsteckdose durch die
Leitung zum Kaltgeräte-Einbaustecker und im Gerät zurück. **L und N der
Leitung führen dabei nichts.**

Damit hebt sich in der Leitung nichts auf, und die Zange sollte **um das
gesamte Kabel gelegt** bereits den vollen Prüfstrom anzeigen.

- [ ] **Zuerst das ungeteilte Prüfkabel umfassen.** Zeigt die Zange etwas an,
      erübrigt sich der Aufbau.
- [ ] Erst wenn dabei nichts oder ein zu kleiner Wert erscheint, ein Kabel mit
      einzeln geführten Adern anfertigen.

**Fallstricke bei der Messung:**

| Punkt | Worauf zu achten ist |
|---|---|
| **AC oder DC?** | Ist der Prüfstrom **Gleichstrom**, zeigt eine gewöhnliche AC-Zange (Stromwandler) **nichts** an. Dann wird eine Zange mit **Hall-Sensor** gebraucht. Ein Ausschlag von null bei gleichzeitig warmem Kabel ist also selbst ein Befund: dann ist es DC. |
| **Kurze Messdauer** | Der Prüfschritt dauert nur Sekunden. **MAX-/Peak-Hold** einschalten, sonst ist die Anzeige vorbei, bevor sie steht. |
| **Messbereich** | Auf 10–30 A einstellen, nicht auf Milliampere. |
| **Nur ein Leiter** | Umfasst die Zange Hin- und Rückleiter, hebt sich das Feld auf und sie zeigt null. |

⚠️ **Ein Prüfkabel mit einzeln geführten Adern gehört ausschließlich zur
Schutzleiterprüfung.** Dort liegt nur Niederspannung an. Käme dasselbe Kabel in
einem Prüfschritt zum Einsatz, bei dem das Gerät **Netzspannung auf die
Prüfsteckdose** legt, wären getrennt geführte L- und N-Adern eine ernste
Gefahr. Ein solches Kabel deshalb **deutlich kennzeichnen** und getrennt von
den übrigen Messleitungen aufbewahren.

---

## Was danach offen bleibt

Fragen, die sich von außen **nicht** klären lassen und für später vorgemerkt
sind — sie rechtfertigen für sich genommen noch kein Öffnen:

- Aufbau der Elektronik: welcher Mikroprozessor steckt hinter dem „µP"
- Wo der Softwarestand liegt (EPROM gesockelt?) und ob er sicherbar ist
- Aufbau der Schaltmatrix für die Fehlerbedingungen
- Bedeutung des Zusatzes `-1` in `µP 601-1`
