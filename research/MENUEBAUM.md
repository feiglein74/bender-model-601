# Menübaum — Bender µP Safety Tester Model 601

Aufnahme der Bedienoberfläche. Weil kein Handbuch existiert
(`../QUELLEN.md`), **ist dieses Dokument die Funktionsbeschreibung des Geräts.**

Softwarestand: `IVM429 D` (Startbildschirm oben rechts, Deutung siehe
`FUNKTIONSAUFNAHME.md` Abschnitt B) · Sprache: Deutsch

---

## Die Bedienoberfläche zeigt selbst an, was möglich ist

Zwei Eigenschaften des Geräts machen das Kartieren fast mechanisch:

**1. `>` markiert eine belegte Displayzeile.** Zeilen ohne `>` sind Titel,
Text oder Messwert. Man muss nicht raten, welcher Softkey etwas tut.

**2. Hinter *allen sieben* Tasten sitzen LEDs** — den drei Softkeys ebenso wie
`START`, `F`, `↑` und `↓` (belegt 2026-08-14). Sie zeigen an, welche Tasten im
gerade angezeigten Bildschirm **aktiv** sind.

Damit ist auf jedem Bildschirm **ohne Ausprobieren vollständig ablesbar, welche
Wege es gibt.** Das ist die verlässlichste Grundlage für eine lückenlose
Aufnahme — und zugleich die Probe: **leuchtet eine LED, deren Ziel nicht
notiert ist, fehlt ein Zweig.** Ein Bildschirm gilt erst als aufgenommen, wenn
zu jeder leuchtenden LED ein Ziel steht.

**Deshalb gehört der LED-Zustand aller sieben Tasten zu jedem Bildschirm.**

Nebenbefund: `>` und die Softkey-LEDs sagen dasselbe. Ob sie immer
übereinstimmen, ist im Vorbeigehen zu prüfen — eine leuchtende Softkey-LED
ohne `>` in der zugehörigen Zeile wäre ein interessanter Sonderfall.

---

## Tastenmodell — Arbeitsstand

`↑` und `↓` sind **keine Blättertasten**, sondern bewegen zwischen Ebenen:

| Ort | `↑` | `↓` |
|---|---|---|
| Startbildschirm `[S00]` | → ins Menü `[S02]` | → Selbsttest `[S03]` |
| Auswahlmenü `[S02]` | ○ dunkel | **zurück** |
| **Eingabemaske `[S10]`** | **Wert übernehmen** | ○ dunkel |

**Einheitliche Lesart (Stand 2026-08-14):**

> **`↑` = vorwärts** — eine Ebene hinein, oder eine Eingabe bestätigen.
> **`↓` = zurück** — eine Ebene heraus.
> **`START` = ganz nach Hause.**

Beides ist nur dort aktiv, wo es einen Weg gibt; die LED sagt es vorher. In
`[S02]` ist `↑` dunkel, weil die Auswahl über die Softkeys läuft. In der
Eingabemaske `[S10]` ist `↓` dunkel — **dort gibt es keinen Rückweg.**

Auf dem Startbildschirm gibt es kein „zurück" mehr; dort ist `↓` anderweitig
belegt, mit dem Selbsttest.

**Geklärt: `START` ist der Notausgang.** In der Eingabemaske `[S10]` leuchtet
die `START`-LED (belegt 2026-08-14). Eine begonnene Eingabe lässt sich also
verlassen, ohne sie mit `↑` zu übernehmen — man landet auf dem Startbildschirm.

Damit ist die Oberfläche vollständig verstanden und in jeder Lage sicher
bedienbar:

| Taste | Wirkung, überall gleich |
|---|---|
| `↑` | vorwärts — hinein oder bestätigen |
| `↓` | zurück — eine Ebene heraus |
| `START` | Abbruch, zurück zum Startbildschirm |
| `F` | Nebenebene zum aktuellen Bildschirm |
| Softkeys | die angezeigten Optionen |

**Keine Sackgassen, kein Zustand ohne Ausweg.** Das ist die Voraussetzung
dafür, auch die heiklen Zweige — Messdatenverwaltung, ein etwaiges
Servicemenü — gefahrlos ansehen zu können: Man kann jederzeit aussteigen,
ohne etwas zu bestätigen.

**Damit ist eine Frage wieder offen, die schon als geklärt galt:** Wie werden
Listen dargestellt, die länger sind als drei Einträge? Wenn `↑`/`↓` nicht
blättern, muss es einen anderen Weg geben — ein Softkey „weiter", der
Nummernblock zur Direktwahl, oder das Menü ist tatsächlich auf drei Einträge
je Bildschirm begrenzt und dafür **tief statt breit** gebaut.

**Beim ersten längeren Menü darauf achten.** Das entscheidet, wie der ganze
Baum geformt ist.

---

## Notation

```
[Kennung] Bildschirmname            (Weg dorthin)
  1  <Zeile 1 wörtlich>
  2> <Zeile 2 wörtlich>             → Ziel
  3> <Zeile 3 wörtlich>             → Ziel
  4  <Zeile 4 wörtlich>
  LED: START ● · F ● · ↑ ● · ↓ ○    (● leuchtet, ○ aus)
  F → Ziel · ↑ → Ziel · ↓ → Ziel
```

Regeln:

- **Alle vier Zeilen** notieren, auch leere — die Anordnung ist Teil des Befunds.
- **Wörtlich** abschreiben, samt Abkürzungspunkten, Doppelpunkten, Leerzeichen.
- **LED-Zustand aller vier Tasten** festhalten. Eine leuchtende LED ohne
  bekanntes Ziel ist ein unerledigter Zweig.
- Auf jedem Bildschirm **`↑` und `↓` antippen**, sofern ihre LED leuchtet, und
  das Ziel notieren — nach derzeitigem Stand sind das **Navigationstasten
  zwischen Ebenen**, keine Blättertasten (siehe unten).
- **`F` überall probieren**, wo seine LED leuchtet — es ist kontextabhängig.
- `START` führt aus jeder Lage zum Startbildschirm zurück. Jeden Zweig von dort
  aus neu anlaufen.
- Welche Softkey-Position (oben/Mitte/unten) zu welcher Zeile gehört,
  mit aufnehmen.

---

## [S00] Startbildschirm

**Erreicht:** nach dem Einschalten · aus jeder Lage mit `START`

```
  ?  <Name des früheren Betreibers>          ┐ genaue Zeilenzuordnung
  ?  …                                       ┘ noch nicht aufgenommen
  ?  … IVM429 D   (oben rechts)
  ?  …
  LED: START ● · F ● · ↑ ● · ↓ ●
```

**Abgänge — vollständig belegt (2026-08-14):**

| Bedienung | Ziel |
|---|---|
| **einer der drei Softkeys** | → `[S02]` Menü |
| **`↑`** | → `[S02]` Menü — derselbe Weg |
| **`↓`** | → `[S03]` **Selbsttest** |
| **`F`** | → `[S01]` Sprachauswahl |
| **`START`** | bleibt auf `[S00]`, siehe unten |

Bemerkenswert: **`↑` und die Softkeys führen zum selben Ziel.** Das Menü ist
also auf zwei Wegen erreichbar — ein Hinweis darauf, dass die Softkeys hier
nicht drei verschiedene Zweige öffnen, sondern gemeinsam „ins Menü" bedeuten.
Zu prüfen: Landen wirklich alle drei Softkeys auf demselben Bildschirm, oder
unterscheiden sie sich in der Vorauswahl?

### Was `START` auf dem Startbildschirm tut

Beobachtung (2026-08-14): `START` erneut gedrückt, obwohl `[S00]` bereits
angezeigt wird — **die LEDs von `F`, `↑` und `↓` gehen kurz aus und wieder an.**

Deutung des Beobachters: „sieht aus wie Reset". Plausibel, aber noch nicht
belegt. Zwei Lesarten, die dasselbe Blinken erzeugen:

- **A — Neustart der Anwendung.** `START` setzt das Gerät auf den
  Ausgangszustand zurück.
- **B — Neuaufbau des Bildschirms.** `START` ruft dieselbe Routine wie immer
  auf; dabei werden die LEDs gelöscht und neu gesetzt. Das Blinken wäre eine
  Nebenwirkung, kein Reset.

**Unterscheidende Tests:**

- [ ] Irgendwo eine Eingabe beginnen (Ziffern über den Nummernblock), dann
      `START` — ist die Eingabe verworfen? Bei A ja, bei B ebenfalls; kein
      Trennkriterium, aber gut zu wissen
- [ ] **Sprache auf Englisch stellen, dann `START`** — steht danach wieder
      Deutsch? Dann ist es ein echter Reset auf Vorgabewerte (**A**).
      Bleibt Englisch, ist es nur ein Rücksprung (**B**)
- [ ] Blendet die Anzeige beim Drücken vollständig aus, oder bleibt der Text
      stehen? Vollständiges Ausblenden spricht für A
- [ ] Läuft ein Selbsttest oder eine Startmeldung mit? Dann A

**Praktische Folge unabhängig davon:** `START` ist der zuverlässige Rückweg,
aber **nichts, worauf man beim Eingeben von Daten vertrauen sollte.** Beim
Kartieren gefahrlos benutzen — beim späteren Arbeiten mit Prüflingsdaten nicht
mitten in einer Eingabe drücken.

**Noch aufzunehmen:**

- [ ] Wortlaut aller vier Zeilen und ihre Zuordnung
- [ ] Tragen Zeilen ein `>`, und welche?
- [ ] Führen die drei Softkeys tatsächlich alle nach `[S02]`?

---

## [S01] Sprachauswahl

**Erreicht:** `F` von `[S00]`

```
  ?  <noch nicht aufgenommen>
  ?> deutsch          → stellt Deutsch ein
  ?> englisch         → stellt Englisch ein
  ?  <noch nicht aufgenommen>
  LED: noch nicht aufgenommen
```

**Belegt (2026-08-14):**

- Vier Zeilen, davon **zwei mit `>`** — Deutsch und Englisch.
- Auswahl über die beiden zugehörigen Softkeys; der dritte ist unbelegt.
- **Umschaltung funktioniert in beide Richtungen und ist folgenlos.**
  Man kann sich sprachlich nicht aussperren.

**Noch aufzunehmen:**

- [ ] Wortlaut aller vier Zeilen, insbesondere Zeile 1 und Zeile 4
- [ ] „deutsch/englisch", „Deutsch/English" oder „D/GB"? — wörtlich
- [ ] Welche Zeilen tragen das `>` — 2 und 3, oder 1 und 2?
- [ ] LED-Zustand
- [ ] Wohin führt die Auswahl — zurück nach `[S00]` oder bleibt der Bildschirm?
- [ ] **Ändert sich `IVM429 D` bei Englisch?** → `FUNKTIONSAUFNAHME.md` Abschn. B

---

## [S02] Menü

**Erreicht:** Softkey oder `↑` von `[S00]`

**Aufgenommen 2026-08-14:**

```
  1  Betriebsart:
  2  Prüfungen nach:
  3> IEC 601-1:1988          → [S04]
  4> DIN VDE 0751T1/90       → [S05]
  LED: Softkey Zeile 3 ● · Softkey Zeile 4 ● · START ● · F ● · ↑ ○ · ↓ ●
  F  → [S06]
```

**Vollständig aufgenommen.** Zu jeder leuchtenden LED steht ein Ziel:

| Taste | LED | Ziel |
|---|---|---|
| Softkey Zeile 3 | ● | `[S04]` IEC 601-1:1988 |
| Softkey Zeile 4 | ● | `[S05]` DIN VDE 0751T1/90 |
| `START` | ● | `[S00]` Startbildschirm |
| `F` | ● | `[S06]` — ein weiteres Menü |
| `↑` | ○ | — |
| `↓` | ● | `[S02]` → zurück nach `[S00]` |

`↑` ist **dunkel**: von hier aus geht es nicht weiter „hinein", die Auswahl
läuft über die Softkeys. Das bestätigt das Tastenmodell.

### Was dieser Bildschirm über den Aufbau sagt

**Die oberste Menüebene ist keine Funktionsauswahl, sondern eine
Betriebsartenwahl.** Man entscheidet zuerst, **nach welcher Norm** geprüft
wird; alles Weitere hängt daran.

Die Zeilen 1 und 2 sind zusammen die Überschrift („Betriebsart: / Prüfungen
nach:"), die Zeilen 3 und 4 die beiden Optionen. Eine Überschrift kann also
**über zwei Zeilen laufen** — auch das gehört zum wechselnden Layout.

Bestätigt sich damit außerdem: `↑` bedeutet **hinein/vorwärts**, `↓`
**heraus/zurück**. Auf `[S00]` führte `↑` ins Menü, hier ist es dunkel, weil
die Auswahl über die Softkeys läuft.

### Der Baum verzweigt sich sofort in zwei vollständige Hälften

Die beiden Normen sind **keine Beschriftungsvarianten desselben Ablaufs**,
sondern zwei verschiedene Prüfregime mit eigenen Prüfschritten, Messverfahren
und Grenzwerten:

| Betriebsart | Was dahinter steht |
|---|---|
| **IEC 601-1:1988** | Die internationale Grundnorm für die Sicherheit medizinischer elektrischer Geräte, Ausgabe 1988. Umfangreicheres Regime — Ableitströme unter Normal- und Erst-Fehler-Bedingung, Netzspannung am Anwendungsteil. |
| **DIN VDE 0751 Teil 1 / 90** | Die deutsche Norm für die **Wiederholungsprüfung** medizinischer Geräte im Betrieb, Ausgabe 1990. Praxisnäheres Regime mit eigenen Verfahren, u. a. Ersatzableitstrommessung, und eigenen Grenzwerten. |

**Folge für die Aufnahme: es sind zwei Teilbäume zu kartieren, nicht einer.**
Beide gehören dokumentiert — gerade die Unterschiede zwischen ihnen sind der
interessante Teil, weil sie zeigen, wie das Gerät zwei Normwelten in einer
Bedienoberfläche abbildet.

### Damit ist der Gerätename erklärt

Die Betriebsart **`IEC 601-1`** ist die Norm, nach der das Gerät benannt ist:
**µP Safety Tester Model 601**. Die früher aufgestellte Vermutung, die „601"
verweise auf die Norm, ist damit **vom Gerät selbst bestätigt** — und zwar in
der alten Zählweise `IEC 601-1`, nicht als `IEC 60601-1`, wie sie das
DS601-Datenblatt von 2006 verwendet.

### Datierung

Die neuere der beiden unterstützten Normausgaben ist von **1990**. Ein Gerät
wird nicht für Normen gebaut, die es noch nicht gibt — und ein Hersteller
ergänzt eine frische Norm zügig. Das legt die **Entstehung auf etwa 1990–1993**
und passt zu allem anderen: Zeichendisplay, Folientastatur, Nadel- oder
Thermodrucker, gepufferte Uhr mit AA-Zellen.

**Einordnung heute:** Beide Normausgaben sind längst abgelöst — DIN VDE 0751
durch DIN EN 62353 (VDE 0751-1). Für dieses Projekt ist das ohne Belang, weil
dokumentiert und nicht zertifiziert wird. Für eine Verwendung als Prüfmittel
wäre es der entscheidende Punkt.

### Noch aufzunehmen

- [ ] LED-Zustand von `START` und `F` auf diesem Bildschirm
- [ ] Was tut `F` von hier aus?
- [ ] Führen alle drei Softkeys von `[S00]` auf genau diesen Bildschirm?

---

## [S03] Selbsttest

**Erreicht:** `↓` von `[S00]`

**Durchgeführt 2026-08-14 — bestanden.**

```
  1  Systemselbsttest
  2  <leer>
  3  Bitte warten !
  4  <leer>
  LED: noch nicht aufgenommen
```

Der Test läuft **rein intern**: keine Handgriffe, kein Prüfling, keine
Verbindung nach außen. Die Anzeige bleibt während des Laufs stehen.

**Bemerkenswert an der Anzeige:** belegt sind **Zeile 1 und Zeile 3**, Zeile 2
und 4 bleiben leer. Die Zeilen sind also **nicht fest** in „drei Softkey-Zeilen
plus eine" aufgeteilt — das Layout wechselt je Bildschirm. Für die Kartierung
heißt das: die Zeilennummer immer mitschreiben, nie aus der Position schließen.

### Der Selbsttest druckt sein Ergebnis aus

Am Ende gibt der eingebaute Drucker ein Protokoll aus:

| Feld | Bedeutung |
|---|---|
| `Selbsttest bestanden` | Ergebnis |
| **Zeit** | aus der geräteinternen Uhr |
| **Datum** | aus der geräteinternen Uhr |
| **Nennspannung** | die Netzspannung, mit der das Gerät rechnet |
| **Gerätenummer** | Kennung des Geräts — Zuordnung noch offen |

Damit ist zugleich belegt: **der Drucker funktioniert und Papier ist vorhanden.**

### Was daraus folgt — drei Befunde

**1. Es gibt eine gepufferte Echtzeituhr.** Ein Gerät, das Zeit und Datum
druckt, hat eine Uhr, die im ausgeschalteten Zustand weiterläuft — also eine
**Batterie oder einen Akku**. Bei einem Gerät dieses Alters ist das der
wahrscheinlichste Verschleißpunkt überhaupt.

- [ ] **Stimmen die gedruckten Zeit- und Datumsangaben?**
      → **Ja:** Die Pufferung lebt. Bemerkenswert, und ein gutes Zeichen für
        den Gesamtzustand.
      → **Nein** (Nullwerte, Vorgabedatum, stehengebliebene Zeit): Die
        Pufferung ist erschöpft. Dann sind alle gespeicherten Datumsangaben
        mit Vorsicht zu lesen, und die Batterie wird zum Thema — auch weil
        auslaufende Zellen Leiterplatten zerstören.

Dieser Test kostet nichts und ist der wertvollste Zustandsbefund, der sich ohne
Öffnen gewinnen lässt.

**2. Die `Gerätenummer` ist noch nicht zugeordnet.**

- [ ] Ist sie identisch mit der **Seriennummer vom Typenschild**?
- [ ] Oder mit der **Sachnummer `B928161`**?
- [ ] Oder eine **frei vergebene Nummer des Betreibers**, im Menü einstellbar —
      dann gehört sie zum Auslieferungszustand des gebrauchten Geräts und darf
      nicht überschrieben werden, wie der Betreibertext.

**3. Die `Nennspannung` ist ein Einstellwert.** Wenn das Gerät sie ausdruckt,
kennt es sie — entweder fest eingestellt oder gemessen.

- [ ] Welcher Wert steht dort (`230 V`? `220 V`?)
- [ ] Ein Gerät aus der Zeit vor der Umstellung auf 230 V könnte noch auf
      **220 V** stehen. Das wäre ein Datierungshinweis und zugleich relevant
      für alle späteren Messwerte, weil Ableitstrom-Grenzwerte auf die
      Nennspannung bezogen sind.

### Noch aufzunehmen

- [ ] Wortlaut des Ausdrucks **vollständig und wörtlich**, Zeile für Zeile
- [ ] Dauer des Tests
- [ ] LED-Zustand während des Laufs — ist `START` aktiv, lässt er sich abbrechen?
- [ ] Was zeigt die Anzeige **nach** dem Test?
- [ ] Werden Einzelergebnisse geprüfter Baugruppen genannt, oder nur das
      Gesamturteil? Ein Selbsttest ist oft die einzige Stelle, an der ein Gerät
      etwas über seinen **inneren Aufbau** preisgibt — hier besonders wertvoll,
      weil das Gerät nicht geöffnet wird.
- [ ] Den Ausdruck **aufbewahren und fotografieren** — er ist das erste
      Dokument, das dieses Gerät selbst erzeugt hat

---

---

## [S04] Betriebsart „IEC 601-1:1988"

**Erreicht:** Softkey Zeile 3 von `[S02]` · **noch nicht betreten**

## [S05] Betriebsart „DIN VDE 0751T1/90"

**Erreicht:** Softkey Zeile 4 von `[S02]` · **noch nicht betreten**

## [S06] `F`-Menü der Betriebsartenwahl — die Verwaltungsebene

**Erreicht:** `F` von `[S02]` · **aufgenommen 2026-08-14**

```
  1  Betriebsart ?    57
  2> Messroutine              → [S07]
  3> Messdatenverwaltung      → [S08]
  4> Uhr                      → [S09]
  LED: noch nicht notiert
```

Damit ist die Arbeitsvermutung bestätigt: **`F` führt zur Verwaltungsebene.**
Der Hauptweg über die Softkeys führt zu den Messungen, `F` zu allem, was das
Gerät sonst noch kann. Alle drei Softkeys sind hier belegt — der erste
Bildschirm, der das ausnutzt.

### Zeile 1: `Betriebsart ?    57`

Eine **Statuszeile**, kein Menüpunkt — sie trägt kein `>`. Zwei Bestandteile,
beide noch zu deuten.

**`Betriebsart ?`** — das Fragezeichen liest sich als **„noch keine
Betriebsart gewählt"**. Passt zur Lage: Man ist über `F` aus der
Betriebsartenwahl `[S02]` herausgesprungen, ohne eine Norm zu wählen. Erwartung
für die Gegenprobe: **erst `IEC 601-1:1988` wählen, dann `F` drücken** — steht
dann statt des Fragezeichens die Norm da?

**`57`** — steht rechts in der Kopfzeile, an derselben Stelle, an der auf dem
Startbildschirm `IVM429 D` steht. Deutungen:

| Lesart | Gegenprobe |
|---|---|
| **Bildschirm- oder Funktionsnummer** — dann wären Menüpunkte über den Nummernblock **direkt anwählbar**, und die Frage nach langen Listen wäre beantwortet | Auf anderen Bildschirmen nachsehen: trägt jeder eine eigene Nummer? Eine Zahl eintippen — springt das Gerät? |
| **Zähler des Messdatenspeichers** — 57 gespeicherte Datensätze oder 57 freie Plätze | Mit dem Inhalt von `[S08]` vergleichen |
| **Kennzahl der Betriebsart** | Nach Wahl einer Norm erneut ansehen — ändert sich die Zahl? |

Die erste Lesart ist die folgenreichste: Ein Gerät mit Nummernblock und
nummerierten Bildschirmen braucht keine Blätterfunktion. **Das wäre die Antwort
auf die offene Frage, wie Listen mit mehr als drei Einträgen bedient werden.**

### Noch aufzunehmen

- [ ] LED-Zustand aller sieben Tasten
- [ ] Wohin führt `↓` von hier — nach `[S02]` zurück?
- [ ] Was tut `F` von hier aus? Gibt es eine dritte Nebenebene?
- [ ] Gegenprobe zu `Betriebsart ?`: erst Norm wählen, dann `F`
- [ ] Eine Zahl über den Nummernblock eintippen — reagiert das Gerät?

---

## [S07] Messroutine

**Erreicht:** Softkey Zeile 2 von `[S06]` · **noch nicht betreten**

Vermutlich der Einstieg in die eigentlichen Messungen — hier sollten sich die
**sechs Piktogramme der Frontplatte** wiederfinden
(`FUNKTIONSAUFNAHME.md`, Abschnitt A).

## [S08] Messdatenverwaltung

**Erreicht:** Softkey Zeile 3 von `[S06]` · **noch nicht betreten**

⚠️ **Der wichtigste noch offene Bildschirm des Projekts.** Hier entscheidet
sich, ob die Messdaten des Vorbesitzers erhalten sind — und damit, ob der
Speicher an der leeren Pufferbatterie hing (`BATTERIE.md`, Folge 2).

- [ ] Sind Datensätze vorhanden? Wie viele — und passt die Zahl zur `57`?
- [ ] Ältester und jüngster Eintrag; wegen der stehenden Uhr sind die Daten
      unzuverlässig, die **Reihenfolge** bleibt aussagekräftig
- [ ] Welche Felder hat ein Datensatz
- [ ] Lässt sich ein Datensatz **ausdrucken**? Dann wäre er gesichert

⚠️ **Nur ansehen.** In einer Datenverwaltung liegen Lösch- und
Rücksetzfunktionen. Nichts bestätigen, dessen Wirkung nicht feststeht — es ist
die einzige Kopie.

## [S09] Uhr

**Erreicht:** Softkey Zeile 4 von `[S06]` · **aufgenommen 2026-08-14**

```
  1  Uhrzeit ?
  2  <leer>
  3> Einstellen              → [S10]
  4> Anzeigen                → [S11]
  LED: noch nicht notiert
```

Ein Zwischenmenü — **nicht** die Uhranzeige selbst. Die Trennung von
`Einstellen` und `Anzeigen` ist bemerkenswert sauber: Man kann die Uhr
ansehen, ohne in den Eingabemodus zu geraten.

### Die Kopfzeile trägt den aktuellen Wert

`Uhrzeit ?` folgt demselben Muster wie `Betriebsart ?` in `[S06]`. Damit ist
das Bauprinzip der Oberfläche belegt:

> **Zeile 1 nennt das Thema des Bildschirms und den gerade gültigen Wert.
> Steht dort ein `?`, ist der Wert nicht gesetzt.**

Hier heißt das: Das Gerät **weiß selbst, dass seine Uhr nicht gestellt ist.**
Es zeigt keinen Fehler, sondern schlicht einen unbekannten Wert — dieselbe
nüchterne Konvention wie bei der noch nicht gewählten Betriebsart.

Nach dem Stellen sollte an dieser Stelle die Uhrzeit stehen. Gute Gegenprobe.

### Noch aufzunehmen

- [ ] LED-Zustand · Ziel von `↓` · Verhalten von `F`
- [ ] Trägt Zeile 1 rechts eine Zahl wie die `57` in `[S06]`?

---

## [S10] Uhr → Einstellen

**Erreicht:** Softkey Zeile 3 von `[S09]` · **Aufnahme begonnen 2026-08-14**

```
  1  SET:
  2    Y  M  D  H  MI  LY
  3      /  /  /  /  /  /
  4  <noch nicht aufgenommen>
  LED: ↑ ● (übernehmen) · ↓ ○ · übrige noch nicht notiert
```

**`↑` übernimmt den Wert** (belegt 2026-08-14). `↓` ist dunkel — aus der
Eingabemaske führt kein Rückweg. Wer hier hineingeht, geht vorwärts wieder
hinaus.

**Zeile 2 und 3 bilden zusammen eine Eingabemaske:** oben die Feldnamen, darunter
die Eingabestellen, durch `/` getrennt. Die Felder sind **leer** — es ist nichts
vorbelegt, auch nicht der Unsinn aus `[S11]`. Man gibt also alle sechs Werte
neu ein, statt bestehende zu korrigieren.

Das ist wieder ein Layout, das dem Softkey-Raster nicht folgt: eine
zweizeilige Tabelle mitten im Bildschirm.

### Die Feldliste

| Kürzel | Feld |
|---|---|
| `Y` | Year — Jahr |
| `M` | Month — Monat |
| `D` | Day — Tag |
| `H` | Hour — Stunde |
| `MI` | Minute |
| `LY` | **Leap Year — Schaltjahr** |

**Kein Sekundenfeld.** Beim Stellen werden die Sekunden vermutlich auf null
gesetzt — zu prüfen.

Die Reihenfolge `Y M D` deckt sich mit der Anzeige in `[S11]`, wo das Datum
als `(M/T)` beschriftet ist.

### `LY` — das Schaltjahr wird von Hand gesetzt

Das ist der aufschlussreichste Befund dieses Bildschirms, und er sagt etwas
über die **Hardware**, ohne dass das Gerät geöffnet werden muss.

Ein Gerät, das das Schaltjahr als **Eingabefeld** führt, **berechnet es
nicht aus der Jahreszahl.** Das ist die Signatur eines einfachen
Echtzeituhr-Bausteins, wie er um 1990 üblich war: Er zählt Jahre zweistellig
und führt einen eigenen kleinen Schaltjahrzähler, den die Firmware setzen muss.

Daraus folgt zweierlei:

- **Das Jahrhundert ist dem Gerät unbekannt.** Wüsste es das volle Jahr,
  könnte es das Schaltjahr selbst bestimmen. Die zweistellige Jahreszahl aus
  `[S11]` ist damit bestätigt, und die Frage nach dem Verhalten jenseits von
  `99` gewinnt an Gewicht.
- **Falsch gesetztes `LY` verschiebt das Datum ab dem 1. März** um einen Tag,
  weil der 29. Februar entweder zu viel oder zu wenig gezählt wird.

Für 2026 gilt: **kein Schaltjahr**, `LY` entsprechend setzen.

### Belegt: `LY` ist einstellig, alle anderen Felder zweistellig

Aufgenommen 2026-08-14: `Y`, `M`, `D`, `H` und `MI` nehmen jeweils
**zweistellige** Werte aus dem Nummernblock an, **`LY` nur eine Stelle.**

Das schließt eine Jahreszahl als `LY`-Inhalt aus und lässt zwei Bauformen
übrig — mit **unterschiedlichem einzutragenden Wert für 2026**:

| Bauform | Bedeutung | Wert für 2026 |
|---|---|---|
| **Merker `0`/`1`** | „laufendes Jahr ist ein Schaltjahr: ja/nein" | **`0`** |
| **Schaltjahrzähler `0`–`3`** | Jahre seit dem letzten Schaltjahr; so zählen viele Uhrenbausteine dieser Zeit | **`2`** (Schaltjahr war 2024) |

**Der Unterschied ist nicht kosmetisch:** Ein falsch gesetzter Wert verschiebt
das Datum ab dem 1. März um einen Tag, weil der 29. Februar zu viel oder zu
wenig gezählt wird.

**Entscheidender Test, ein Tastendruck:**

- [ ] **Im Feld `LY` eine `3` eingeben.**
      → **angenommen:** Zähler `0`–`3`. Für 2026 dann `2` eintragen.
      → **abgewiesen oder auf `1` begrenzt:** Merker `0`/`1`. Für 2026 dann `0`.

Ein Wertebereich `0`–`3` wäre zugleich ein **direkter Hinweis auf den verbauten
Uhrenbaustein** — mehrere verbreitete Typen jener Jahre führen genau so einen
Zweibit-Schaltjahrzähler. Das ließe sich beim späteren Öffnen gegen das
tatsächliche Bauteil halten.

- [ ] **Zweite Gegenprobe:** Lässt sich der `29.02.` nur bei passend gesetztem
      `LY` eingeben? Dann ist die Deutung hart belegt.

### Sprache

Auch die Feldkürzel sind **englisch** (`Y`, `M`, `D`, `H`, `MI`, `LY`) — im
deutschen Sprachmodus wären `J`, `M`, `T`, `S`, `MI` zu erwarten. Die
Eingabemaske ist damit **durchgehend unübersetzt**, nicht nur die Überschrift.

### `SET:` steht auf Englisch — im deutschen Sprachmodus

Ein kleiner, aber echter Befund: Das Gerät läuft auf Deutsch (`[S01]`), und
alle bisher aufgenommenen Beschriftungen waren deutsch — `Betriebsart`,
`Messroutine`, `Messdatenverwaltung`, `Uhr`, `Einstellen`, `Anzeigen`,
`Jahr`, `Datum`, `Systemselbsttest`, `Bitte warten !`. Hier steht **`SET:`**.

Die Übersetzung des Softwarestands `IVM429 D` ist also **nicht vollständig** —
Eingabemasken sind offenbar durchgerutscht. Zwei Möglichkeiten:

- Der Eingabeteil ist sprachneutral gehalten und wurde bewusst nicht übersetzt.
- Es ist schlicht eine Lücke in der Lokalisierung.

- [ ] **Gegenprobe:** Beim Kartieren darauf achten, ob weitere englische
      Reste auftauchen — besonders in Eingabemasken und Fehlermeldungen.
      Eine Häufung wäre ein Hinweis darauf, dass die deutsche Fassung eine
      nachträgliche Übersetzung der englischen ist, und nicht umgekehrt.

Das ist kein Mangel, sondern ein **Merkmal des Softwarestands** und gehört
dokumentiert.

### Noch aufzunehmen

- [ ] Wie wird eingegeben — Nummernblock direkt, Feldwechsel womit?
- [ ] Reihenfolge der Felder, Format, Bestätigung
- [ ] **Nimmt das Feld `Jahr` einen Wert wie `26` an — und was wird daraus?**
- [ ] Lässt sich der Vorgang abbrechen, ohne zu speichern?

---

## [S11] Uhr → Anzeigen

**Erreicht:** Softkey Zeile 4 von `[S09]` · **aufgenommen 2026-08-14**

```
  1  Jahr       : 3?
  2  Datum (M/T):1?/02
  3  <leer>
  4        00:56:19          (mittig)
  LED: noch nicht notiert
```

### Der Zustand bestätigt die tote Pufferung

**Jahr und Datum enthalten Unsinn**, und das Gerät sagt das auch: `3?` und
`1?`. Jahr und Monat stehen auf Werten, die sich nicht als gültige Ziffern
darstellen lassen — typisch für einen Uhrenbaustein, dessen Register nach
Spannungsverlust undefiniert sind. Nur der Tag (`02`) ist zufällig gültig.

**Die Uhrzeit läuft dagegen.** `00:56:19` entspricht der bisherigen
Einschaltdauer — die Uhr ist beim Einschalten bei `00:00:00` losgelaufen. Sie
funktioniert also einwandfrei, sie **behält nur nichts**. Genau das war zu
erwarten (`BATTERIE.md`).

Damit ist der Befund rund: Uhrenbaustein in Ordnung, Stützversorgung fehlt.

### `?` ist die geräteeigene Kennzeichnung für „undefiniert"

Dasselbe Zeichen steht in `[S06]` hinter `Betriebsart ?`. Das ist keine
Zufälligkeit, sondern eine **durchgehende Konvention der Bedienoberfläche**:
Wo ein Wert unbekannt oder nicht gesetzt ist, schreibt das Gerät ein `?`.

Das stützt rückwirkend die Deutung von `Betriebsart ?` als **„noch keine
Betriebsart gewählt"** — und ist beim weiteren Kartieren nützlich: ein `?` im
Text ist eine Aussage des Geräts, kein Lesefehler.

### Layout

Zeile 3 bleibt leer, Zeile 4 ist **mittig gesetzt**. Das Gerät kennt also
Zentrierung — ein weiterer Beleg dafür, dass das Zeilenlayout frei gestaltet
wird und nicht dem Softkey-Raster folgt.

Format der Datumsangabe: **`Datum (M/T)`** — Monat vor Tag, mit ausdrücklicher
Beschriftung. Das Jahr steht in einem eigenen Feld.

### Noch aufzunehmen

- [ ] LED-Zustand aller sieben Tasten
- [ ] Wie wird gestellt — Nummernblock direkt, oder Feldauswahl mit Softkeys?
- [ ] Trägt dieser Bildschirm rechts oben eine Zahl wie die `57` in `[S06]`?
      **Das ist die Gegenprobe zur Bildschirmnummer-Deutung.**
- [ ] Meldet das Gerät die leere Batterie ausdrücklich?

### Offene Frage: Zweistelliges Jahr

Das Feld heißt schlicht `Jahr` und zeigt zwei Zeichen. Ein Gerät von etwa 1990
rechnet mit hoher Wahrscheinlichkeit mit **zweistelligen Jahreszahlen**.

- [ ] Lässt sich überhaupt ein Jahr jenseits von `99` eingeben?
- [ ] Was druckt das Gerät dann — `26`, `126`, `1926`?
- [ ] Nimmt es die Eingabe an, oder weist es sie zurück?

Das ist kein Mangel, sondern ein Befund über den Softwarestand `IVM429 D` und
gehört dokumentiert. Praktische Folge: Eigene Messprotokolle tragen
möglicherweise eine unbrauchbare Jahresangabe — dann **das Datum der Messung
zusätzlich von Hand festhalten.**

### Gestellt (2026-08-14)

- [x] Falschen Ist-Wert wörtlich notieren — erledigt, siehe oben
- [x] Uhr über `[S10]` gestellt. Die Anzeige zeigt jetzt **`26`** als Jahr,
      den **richtigen Monat und Tag** und eine **laufende Uhr**.

**Damit ist die Zweistelligkeit des Jahresfelds belegt.** Das Gerät nimmt `26`
an und stellt es auch so dar; ein Jahrhundert kennt es nicht. Für eigene
Ausdrucke heißt das: **das volle Jahr von Hand dazuschreiben.**

Offen bleibt, wie das Jahr im **Ausdruck** erscheint:

- [x] **Erledigt (2026-08-14): Der Ausdruck stimmt.** Nach dem Stellen erscheinen
      Datum und Uhrzeit korrekt auf dem Protokoll.

Damit ist die Kette geschlossen: Uhrenbaustein in Ordnung, Stützversorgung
fehlt, Stellen funktioniert, Ausgabe stimmt. **Das Gerät erzeugt wieder
brauchbar datierte Protokolle** — erstmals seit dem Ausfall der Batterie.

Aufzubewahren sind damit **zwei Ausdrücke desselben Tages**: einer mit
stehender, einer mit gestellter Uhr. Sie belegen den Befund vollständig.

- [ ] Wörtlichen Wortlaut beider Ausdrücke notieren und beide fotografieren —
      Thermopapier verblasst

⚠️ **Ohne Batterie hält die Einstellung nur bis zum Ausschalten.** Vor jeder
Sitzung, in der gedruckt wird, neu stellen — oder bewusst darauf verzichten und
die Ausdrucke von Hand datieren.

---

## Noch nicht betretene Zweige

- **`[S04]` / `[S05]`** — die beiden Normzweige, der eigentliche Funktionsumfang
- Prüfabläufe und Einzelmessungen (Abgleich mit den sechs Piktogrammen)
- Prüflings- und Protokollverwaltung, gespeicherte Daten des Vorbesitzers
- Bearbeitung des **Betreibertextes** — dass er existiert, ist belegt
- Einstellungen: Datum/Uhrzeit, Grenzwerte, Drucker
- Ein etwaiges Service-/Kalibriermenü — **nur ansehen, nichts ändern**
