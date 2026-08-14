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

Die übrigen drei zeigen Varianten mit Schutzleiter, Gehäuse und Anwendungsteil
und sind noch nicht sicher zuzuordnen. **Der Menübaum aus Abschnitt C wird sie
auflösen** — die Bezeichnungen dort gehören gegen diese sechs Bilder gehalten.

### Neu: eingebauter Drucker

Rechts neben der Anzeige sitzt ein **Papierschacht mit Sichtfenster**, darin
ein bedruckter Streifen. Lesbar ist darauf **`Klasse:1`** — also die
Schutzklasse des Prüflings. Das Gerät **druckt Prüfprotokolle selbst aus.**

Folgen für die weitere Arbeit:

- Der Ausdruck ist eine **eigene Ausgabeschnittstelle** neben der Anzeige und
  zeigt Dinge, die auf vier Zeilen nicht passen. Ein Probeausdruck in
  Abschnitt F ist deshalb wertvoll — er liefert das vollständige Protokollformat.
- **Papier und Farbband/Thermokopf sind Verschleißteile.** Vor ausgiebigem
  Drucken klären, welches Papier passt und ob noch Vorrat da ist.
- Ob der Drucker der einzige Ausgabeweg ist oder daneben eine Datenschnittstelle
  existiert, ist offen — die Rückwand ist noch nicht aufgenommen (Abschnitt E).

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

### Die Netzleitung ist fest — damit ist der Kaltgeräte-Stecker geklärt

Das Gerät hat **keinen Kaltgeräte-Netzeingang**, sondern eine fest
angeschlossene Netzleitung mit Zugentlastung auf der Rückwand. Der
Kaltgeräte-Einbaustecker auf der **Front** kann damit nichts anderes sein als
das, was Piktogramm 3 zeigt: der Anschluss für die **Leitungsprüfung**.

Die früher offengelassene Möglichkeit, es handle sich um den Netzeingang des
µP601 selbst, ist damit **widerlegt.**

### `Summer/Buzzer` abschaltbar

Ein eigener Schalter für die akustische Rückmeldung. Das ist ein Hinweis auf
den vorgesehenen Einsatz: In einem Prüfablauf mit Handgriffen am Prüfling
quittiert ein Summer jeden Schritt, ohne dass man auf die Anzeige sehen muss —
und in einer ruhigen Umgebung schaltet man ihn ab.

- [ ] Steht der Schalter derzeit auf `Ein` oder `Aus`?
- [ ] Wann summt das Gerät — Tastendruck, Schrittende, Fehler?

### Was Abschnitt A noch offen lässt

- [ ] **Typenschild** vollständig — Seriennummer, Baujahr, Anschlusswerte.
      Auf der Rückwand ist keines zu sehen; vermutlich auf der Unterseite
- [ ] Zuordnung von **`F1`**
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

**Ergebnis:**

> _(noch nicht aufgenommen)_

---

## Was danach offen bleibt

Fragen, die sich von außen **nicht** klären lassen und für später vorgemerkt
sind — sie rechtfertigen für sich genommen noch kein Öffnen:

- Aufbau der Elektronik: welcher Mikroprozessor steckt hinter dem „µP"
- Wo der Softwarestand liegt (EPROM gesockelt?) und ob er sicherbar ist
- Aufbau der Schaltmatrix für die Fehlerbedingungen
- Bedeutung des Zusatzes `-1` in `µP 601-1`
