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
- **Die Kopfzeile trägt nie ein `>`.** Sie nennt Thema und aktuellen Wert und
  ist rein beschreibend — belegt an `[S02]`, `[S04]`, `[S06]`, `[S07]`, `[S09]`
  und `[S13]`. Sie kann sich über **zwei Zeilen** erstrecken (`[S02]`, `[S07]`).
  Was handelt, steht darunter.
- **Wörtlich** abschreiben, samt Abkürzungspunkten, Doppelpunkten, Leerzeichen.
- **Groß- und Kleinschreibung einzelner Wörter gilt als unsicher**, solange sie
  nicht eigens nachgeprüft wurde — sie verrutscht beim Abschreiben zu leicht,
  um daraus etwas abzuleiten. Belegte Eigenarten des Softwarestands sind
  stattdessen `SET:` samt englischer Feldkürzel, die wechselnde Schreibung von
  `>>> Nur Messung <<<` und `Bitte warten !` gegenüber `drehen!`.
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

## [S30] Spannungstest — beim Einschalten, vor allem anderen

**Erreicht:** läuft selbsttätig nach dem Einschalten · **aufgenommen 2026-08-15**

```
  1  Spannungstest
  2  <leer>
  3  Bitte warten !
  4  <leer>
```

Das Gerät stellt hier fest, **welcher Stift seines eigenen Schuko-Steckers die
Phase führt.** Bei falscher Lage fordert es auf, auszuschalten und den Stecker
zu drehen. Begründung und Folgen: `FUNKTIONSAUFNAHME.md`, Abschnitt B.

**Der Name bestätigt die Vermutung:** Es ist ein **Spannungstest**, keine
Strommessung — also der Vergleich beider Netzleiter gegen den Schutzleiter.

### [S31] Meldung bei falscher Steckerlage

**Aufgenommen 2026-08-15, wörtlich:**

```
  1  Bitte ausschalten
  2  und Netzstecker des
  3  µP-Tester in der
  4  Steckdose drehen!
```

**Die Anzeige stellt das `µ` tatsächlich dar** (bestätigt 2026-08-15) — dort
steht `µP-Tester`, nicht `uP-Tester`.

Das ist ein kleiner Hardwarehinweis: Das Zeichen `µ` liegt im
Standard-Zeichensatz **HD44780 A00** auf Platz `0xE4`. Dass es verfügbar ist,
stützt die Annahme eines **HD44780-kompatiblen Zeichendisplays**
(`FUNKTIONSAUFNAHME.md`, Abschnitt A) — bislang nur aus der Bauform
geschlossen.

- [ ] Weitere Sonderzeichen im Betrieb sammeln — `Ω`, `°`, Umlaute. Sie
      grenzen den Zeichensatz weiter ein. `Ω` liegt im A00-Satz auf `0xF4`,
      Umlaute dagegen **nicht** — erscheinen sie trotzdem (`Prüfsteckdose`,
      `Gerätenr`), sind sie entweder selbstdefinierte Zeichen oder das Display
      trägt einen anderen Zeichensatz.

**Alle vier Zeilen sind Text** — kein `>`, keine Auswahl. **Aber `START`
leuchtet**, und ein Druck darauf **startet die Spannungserkennung neu**
(belegt 2026-08-15).

Die Meldung ist also kein Endzustand: Man dreht den Stecker und drückt
`START`, statt aus- und wieder einzuschalten. Der Text ist insofern strenger
formuliert als das Gerät sich verhält — verständlich, denn **das Ziehen des
Steckers ist ohnehin nötig**, um ihn zu drehen, und dabei geht das Gerät
sowieso aus.

Die Bauentscheidung aus `FUNKTIONSAUFNAHME.md`, Abschnitt B, bleibt davon
unberührt: Das Gerät gleicht die Steckerlage nicht selbst aus. Es prüft nur
auf Verlangen erneut.
- [ ] Steht dort wirklich **`up-Tester`**, oder zeigt die Anzeige ein
      **`µ`** (`µP-Tester`)? Das Zeichen `µ` ist im Standard-Zeichensatz
      solcher Displays vorhanden — schreibt Bender es trotzdem als `u` aus,
      wäre das ein Hinweis auf den verwendeten Zeichenvorrat.

### Nachtrag zur Typografie

Die Meldung endet mit **`drehen!`** — **ohne** Leerzeichen vor dem
Ausrufezeichen, anders als `Bitte warten !` in `[S30]` und `[S03]`.

Damit ist die frühere Notiz zu berichtigen: Es handelt sich **nicht** um eine
durchgehaltene Schreibkonvention, sondern schlicht um **Uneinheitlichkeit**
innerhalb desselben Softwarestands. Das reiht sich in `SET:`, `ja`/`Nein` und
die wechselnde Schreibung von `>>> Nur Messung <<<` ein.

### Der Startvorgang ist damit vollständig (2026-08-15)

```
Einschalten
   │
   └─► [S30] Spannungstest — „Bitte warten !"  ◄─────────┐
          │                                              │
          ├─ Phasenlage falsch ─► [S31] „Bitte ausschalten …"
          │                        START ● ── erneut prüfen ┘
          │
          └─ Phasenlage richtig ─► [S00] Startbildschirm
                                    Betreibername · IVM429 D
```

**Der Systemselbsttest `[S03]` gehört *nicht* zum Startvorgang.** Er wird
ausschließlich von Hand ausgelöst, mit `↓` vom Startbildschirm.

### Warum diese Aufteilung folgerichtig ist

Das Gerät unterscheidet zwei Arten von Prüfung an sich selbst — und behandelt
sie verschieden:

| | Spannungstest `[S30]` | Systemselbsttest `[S03]` |
|---|---|---|
| Auslösung | **zwingend**, bei jedem Einschalten | **freiwillig**, auf Tastendruck |
| Gegenstand | die **Umgebung** — Phasenlage der Steckdose | das **Gerät** — eigene Baugruppen |
| Bei Nichtbestehen | **Betrieb wird verweigert** | Ausdruck, sonst keine Sperre bekannt |
| Ausdruck | keiner beobachtet | ja, mit Datum, Zeit, Nennspannung, Gerätenummer |

**Erzwungen wird, was die Messungen verfälschen würde; freigestellt bleibt,
was nur der Diagnose dient.** Die Phasenlage ist Voraussetzung jeder
folgenden Messung — ohne sie wären „Netzleiter offen" und „Phase vertauscht"
bedeutungslos. Deshalb steht sie vor allem anderen und lässt sich nicht
übergehen.

Für die Praxis heißt das: **Das Gerät kann nicht falsch herum betrieben
werden.** Wer eine Messung von ihm bekommt, hat die richtige Phasenlage —
das ist keine Frage der Sorgfalt des Anwenders.

### Musterbildung: „Bitte warten !"-Bildschirme

Dieselbe Form wie beim Systemselbsttest `[S03]`:

```
  1  <was gerade läuft>
  2  <leer>
  3  Bitte warten !
  4  <leer>
```

Damit ist ein weiteres Bauprinzip der Oberfläche belegt: **Läuft ein Vorgang
ohne Zutun des Anwenders, steht in Zeile 1 sein Name und in Zeile 3
`Bitte warten !`** — keine Softkeys, kein `>`. Beim Kartieren sind solche
Bildschirme daran sofort zu erkennen.

Bemerkenswert die Schreibweise mit **Leerzeichen vor dem Ausrufezeichen**
(`Bitte warten !`) — französische Typografie im deutschen Text, an beiden
Stellen gleich. Eine weitere Eigenart des Softwarestands `IVM429 D`, neben
`SET:`, `ja`/`Nein` und `>>> Nur Messung <<<` / `>>> NUR MESSUNG <<<`.

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

### Nachtrag (2026-08-15): Deutung A gewinnt deutlich

Auf der Meldung `[S31]` — falsche Steckerlage — leuchtet `START`, und ein
Druck darauf **lässt den Spannungstest `[S30]` von vorn laufen.**

`START` stößt dort also **den Startvorgang neu an**, nicht bloß einen
Bildschirmwechsel. Das ist genau das Verhalten, das Deutung **A — Neustart der
Anwendung** vorhersagt, und es erklärt zugleich das kurze Erlöschen der LEDs
auf `[S00]`: Dort läuft dieselbe Routine, findet aber nichts vor, was sie
ändern müsste.

Damit ist die ursprüngliche Beobachtung des Bedieners — „sieht aus wie
Reset" — **bestätigt**. Offen bleibt nur noch der Umfang: Ob `START` auch
Einstellungen wie die Sprache auf Vorgabewerte zurücksetzt, klärt weiterhin
der Test oben (auf Englisch stellen, `START` drücken, nachsehen).

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

**Erreicht:** Softkey Zeile 3 von `[S02]` · **Aufnahme begonnen 2026-08-14**

```
  1  Betriebsart:   IEC
  2> Klassifikation          → [S15]
  3> Grenzwerteingabe        → [S16]
  4> Nur Messgerät           → [S17]
  LED: noch nicht notiert
```

### Drei Wege, und einer davon ist der wichtigste für dieses Projekt

| Zweig | Was dahintersteckt |
|---|---|
| **`Klassifikation`** | Einordnung des Prüflings — Schutzklasse, Anwendungsteil-Typ. Der Einstieg in den **vollständigen genormten Prüfablauf** mit Bewertung und Protokoll. |
| **`Grenzwerteingabe`** | Die Grenzwerte sind **einstellbar**, nicht fest verdrahtet. Bemerkenswert für ein Normprüfgerät — und ein Ort, an dem man **nichts verstellen sollte**, solange die Werkseinstellung unbekannt ist. |
| **`Nur Messgerät`** | **Betrieb als reines Messgerät**, ohne Prüfablauf, ohne Bewertung, ohne Datenbank. |

### `Nur Messgerät` — der gefahrlose Zugang zu den Messfunktionen

Das ist der praktisch wertvollste Fund dieses Bildschirms. Ein Modus, der
**einzelne Messungen ohne Prüflingsbezug** erlaubt, bedeutet:

- **Keine Datensätze werden angelegt oder verändert.** Der Bestand des
  Vorbesitzers bleibt unangetastet — das war die Sorge, die bisher jedes
  Ausprobieren am lebenden Gerät gebremst hat.
- **Kein Ausdruck am Ende**, vermutlich — also kein Verschleiß am Druckwerk.
- Die **einzelnen Messgrößen** sollten hier unmittelbar wählbar sein. Damit ist
  das voraussichtlich der Ort, an dem sich die **sechs Piktogramme der
  Frontplatte** wiederfinden (`FUNKTIONSAUFNAHME.md`, Abschnitt A).

**Für Abschnitt F der Funktionsaufnahme ist damit der Weg gefunden:** Messungen
werden über `Nur Messgerät` erprobt, nicht über den Prüfablauf.

### `Grenzwerteingabe` — ansehen, nicht ändern

Dass sich Grenzwerte eingeben lassen, ist für sich schon eine Aussage über das
Gerät: Es ist nicht auf eine Normfassung festgenagelt, sondern anpassbar.

⚠️ **Werte notieren, bevor irgendetwas verändert wird.** Ob es eine Funktion
„Werkseinstellung" gibt, ist unbekannt. Ein verstellter Grenzwert ist ohne
Kenntnis des Ausgangswerts nicht wiederherstellbar — und er würde jede spätere
Bewertung stillschweigend verfälschen.

- [ ] Alle Grenzwerte **vollständig abschreiben**, bevor dort etwas passiert.
      Das ist zugleich ein wertvolles Dokument: die Grenzwerttabelle der
      IEC 601-1:1988, wie dieses Gerät sie führt.
- [ ] Gilt die Eingabe je Betriebsart getrennt? Der VDE-Zweig `[S05]` hätte
      dann eigene Werte.

### Noch aufzunehmen

- [ ] LED-Zustand · Ziel von `↓` · Verhalten von `F`
- [ ] Trägt Zeile 1 rechts eine Zahl?

### Bestätigt: Die Kopfzeile zeigt den gültigen Wert

`Betriebsart:   IEC` — an derselben Stelle, an der in `[S06]` noch
`Betriebsart ?` stand. **Das Fragezeichen ist durch den gewählten Wert
ersetzt.** Damit ist das Bauprinzip der Oberfläche endgültig belegt:

> Zeile 1 nennt Thema und aktuellen Wert. `?` heißt „nicht gesetzt".

Die Gegenprobe, die für `[S06]` vorgemerkt war, ist damit erledigt.

### Bestätigt: `IEC` in `[S13]` ist das Prüfregime des Datensatzes

Das Gerät kürzt die Betriebsart hier mit **`IEC`** ab — **genau die
Zeichenfolge**, die in der Prüflingsdatenbank `[S13]` in Zeile 2 steht und sich
beim Blättern mit dem Datensatz ändert.

Damit ist die dortige Arbeitsvermutung so gut wie belegt: **Jeder Prüfling
trägt sein Prüfregime mit sich.** Die endgültige Gegenprobe bleibt, einen
Datensatz zu finden, bei dem stattdessen die VDE-Kennung steht.

### `Klassifikation` als erster Schritt

Nach der Norm kommt die **Einordnung des Prüflings** — Schutzklasse,
Anwendungsteil-Typ. Genau das erwartet der Erwartungsrahmen in
`FUNKTIONSAUFNAHME.md`: Ohne Klassifizierung gibt es keine Grenzwerte, und
ohne Grenzwerte kein Bestanden/Nicht bestanden.

Der Ablauf zeichnet sich damit ab:

```
Prüfling wählen  →  Norm  →  Klassifikation  →  Messung  →  Bewertung  →  Ausdruck
```

- [ ] Zeilen 3 und 4, LED-Zustand, Ziele der Softkeys
- [ ] Trägt `Klassifikation` ein `>`, oder ist es eine Überschrift zu den
      Zeilen darunter?

## [S15] IEC → Klassifikation

**Erreicht:** Softkey Zeile 2 von `[S04]` · **aufgenommen 2026-08-14**

```
  1  Schutzklasse:
  2> Klasse I               → [S18]
  3> Klasse II              → [S19]
  4> int. Stromquelle       → [S20]
  LED: noch nicht notiert
```

### Die Klassifikation beginnt mit der Schutzklasse

Drei Möglichkeiten, und sie decken den Geltungsbereich der IEC 601-1
vollständig ab:

| Auswahl | Prüfling |
|---|---|
| **Klasse I** | Schutz durch **Schutzleiter** — Gehäuse ist mit PE verbunden |
| **Klasse II** | **schutzisoliert**, kein Schutzleiter |
| **int. Stromquelle** | **Gerät mit interner Stromquelle** — batteriebetrieben, ohne Netzanschluss |

### `int. Stromquelle` ergänzt den Erwartungsrahmen

Der Erwartungsrahmen in `FUNKTIONSAUFNAHME.md` führte nur **Schutzklasse I und
II** auf. Die dritte Kategorie der Norm — **Geräte mit interner Stromquelle** —
fehlte dort. **Das Gerät ist vollständiger als der Rahmen, gegen den es
gehalten wurde.**

Das ist keine Kleinigkeit: Ein batteriebetriebenes Medizingerät hat keinen
Netzanschluss, also auch keinen Erdableitstrom und keine netzbezogenen
Fehlerbedingungen. Geprüft werden dort im Wesentlichen **Patientenableitstrom**
und **Patientenhilfsstrom** — und genau dafür sind die zehn Buchsen auf der
Front da.

Erwartung für diesen Zweig: **ein deutlich kürzerer Prüfumfang** als bei
Klasse I. Gute Gelegenheit, das Gerät beim Denken zu beobachten — was es
weglässt, sagt so viel wie das, was es prüft.

### Erwartung für den nächsten Schritt

Nach der Schutzklasse fehlt noch der **Anwendungsteil-Typ (B / BF / CF)**.
Er bestimmt die Grenzwerte für die Patientenableitströme und ist für ein
Medizinprüfgerät unverzichtbar.

- [ ] Kommt er als nächster Bildschirm — oder ist er anderswo untergebracht?
- [ ] Gibt es zusätzlich „**ohne Anwendungsteil**" für Geräte ohne
      Patientenkontakt?

---

## [S18] Klassifikation → Klasse I → fest angeschlossen?

**Erreicht:** Softkey Zeile 2 von `[S15]` · **aufgenommen 2026-08-14**

```
  1  Klassifikation
  2  fest angeschlossenes
  3> Gerät ?   ja           → [S21]
  4> Nein                   → [S22]
  LED: noch nicht notiert
```

### Layout: Die Frage läuft in eine Optionszeile hinein

Neue Beobachtung, die das bisherige Bild verfeinert: Die Frage
**„fest angeschlossenes Gerät ?"** erstreckt sich über die Zeilen 2 und 3 —
und **Zeile 3 trägt zugleich die Antwort `ja` und ein `>`.**

Damit ist zu präzisieren:

> **Zeile 1** trägt nie ein `>`. **Fortsetzungstext** einer Überschrift oder
> Frage kann sich dagegen eine Zeile mit einer Option **teilen**; die
> auswählbare Angabe steht dann **rechts** in der Zeile.

Beim Abschreiben deshalb immer die **ganze Zeile** aufnehmen, nicht nur das
Wort, das nach Option aussieht.

Auch das `?` fügt sich in die bekannte Konvention: ein noch nicht gesetzter
Wert. Hier zugleich als Frage gelesen.


### Warum diese Frage an dieser Stelle steht

Ein **fest angeschlossenes Gerät** ist ortsfest installiert und hat keinen
Netzstecker — es lässt sich also **nicht in die Prüfsteckdose stecken.**

Das ändert den ganzen Messaufbau:

| | Gerät mit Stecker | Fest angeschlossenes Gerät |
|---|---|---|
| Netzversorgung | über die **Prüfsteckdose** des µP601 | bleibt an der Hausinstallation |
| Fehlerbedingungen (Netzleiter offen, Phase vertauscht) | vom Gerät **schaltbar** | **nicht herstellbar** |
| Schutzleitermessung | über den Stecker | über **Prüfspitze** am Schutzleiteranschluss |
| Ableitstrommessung | direkt | nur als **Ersatzableitstrom** oder über Differenzstrom |

Die Frage entscheidet also, **welche Prüfschritte überhaupt möglich sind.**
Dass das Gerät sie so früh stellt — direkt nach der Schutzklasse und noch vor
allem anderen — ist folgerichtig.

Zu erwarten ist, dass der Zweig `ja` einen **deutlich kürzeren Prüfumfang**
ergibt als `Nein`.

---

## [S21] Klasse I → fest angeschlossen: ja → Anwendungsteil-Typ

**Erreicht:** Softkey Zeile 3 von `[S18]` · **aufgenommen 2026-08-14**

```
  1  Klassifikation:
  2> Typ B                  → [S23]
  3> Typ BF                 → [S24]
  4> Typ CF                 → [S25]
  LED: noch nicht notiert
```

### Der Anwendungsteil-Typ — die Grenzwertklasse

Damit ist die Klassifikationskette komplett:

```
Schutzklasse  →  fest angeschlossen?  →  Anwendungsteil-Typ
```

| Typ | Bedeutung |
|---|---|
| **B** | *Body* — Anwendungsteil mit Grundschutz, **erdbezogen**. Nicht für direkte Anwendung am Herzen. |
| **BF** | *Body Floating* — Anwendungsteil **galvanisch getrennt** vom übrigen Gerät. |
| **CF** | *Cardiac Floating* — getrennt und für die **direkte Anwendung am Herzen** zugelassen. Strengste Grenzwerte. |

Der Typ bestimmt die zulässigen **Patientenableitströme**, und die Unterschiede
sind erheblich — bei `CF` liegen sie um eine Größenordnung unter denen von
`B` und `BF`.

**Welche Werte dieses Gerät ansetzt, steht nicht in einem Lehrbuch, sondern im
Gerät selbst:** in `Grenzwerteingabe` (`[S16]`). Das ist der maßgebliche
Beleg — und ein Grund mehr, jene Tabelle vollständig abzuschreiben, bevor dort
irgendetwas verändert wird.

### Offen: Gibt es „ohne Anwendungsteil"?

Angezeigt werden genau drei Optionen, die die Zeilen 2 bis 4 füllen. Ein
Prüfling **ohne** Anwendungsteil — ein Medizingerät ohne Patientenkontakt —
hat hier keinen sichtbaren Platz.

- [ ] **Leuchten `↑` oder `↓`?** Wenn ja, ist die Liste länger als der
      Bildschirm und es rückt eine vierte Möglichkeit nach. Wenn beide dunkel
      sind, kennt das Gerät an dieser Stelle **nur** diese drei — und dann ist
      die Frage, wie es Geräte ohne Anwendungsteil behandelt.
- [ ] Falls es keine vierte gibt: Wird der Anwendungsteil-Prüfschritt später
      übersprungen, wenn nichts an den zehn Buchsen hängt?

---

## [S23] Typ B · [S24] Typ BF · [S25] Typ CF

**Erreicht:** Softkeys von `[S21]` · **noch nicht betreten**

Hier endet voraussichtlich die Klassifikation und der eigentliche
**Prüfablauf** beginnt — der Punkt, an dem die sechs Piktogramme der
Frontplatte auftauchen sollten.

⚠️ **Ab hier wird es ernst.** Am Ende eines Prüfablaufs legt das Gerät
Netzspannung auf die Prüfsteckdose. Solange nichts angeschlossen ist, ist das
Durchklicken ungefährlich — aber ab hier lohnt es, vor jedem Schritt auf die
Anzeige zu sehen, statt durchzutippen.

## [S22] Klasse I → fest angeschlossen: Nein

**Erreicht:** Softkey Zeile 4 von `[S18]` · **noch nicht betreten**

Der Regelfall — Prüfling mit Netzstecker. Hier ist der vollständige
Prüfumfang zu erwarten.

## [S19] Klassifikation → Klasse II

**Erreicht:** Softkey Zeile 3 von `[S15]` · **noch nicht betreten**

## [S20] Klassifikation → int. Stromquelle

**Erreicht:** Softkey Zeile 4 von `[S15]` · **noch nicht betreten**

## [S16] IEC → Grenzwerteingabe

**Erreicht:** Softkey Zeile 3 von `[S04]` · **noch nicht betreten**

⚠️ **Nur ansehen und abschreiben.** Siehe Warnung bei `[S04]`.

## [S17] IEC → Nur Messgerät

**Erreicht:** Softkey Zeile 4 von `[S04]` · **noch nicht betreten**

**Der Zweig, über den später gemessen wird.** Hier sollten die einzelnen
Messgrößen unmittelbar wählbar sein.

- [ ] Welche Messgrößen werden angeboten — Abgleich mit den **sechs
      Piktogrammen** der Frontplatte
- [ ] Wird beim Aufruf bereits etwas geschaltet? **Solange das offen ist,
      nichts an Prüfsteckdose und Buchsen angeschlossen lassen.**
- [ ] Erscheinen Messwerte fortlaufend, oder erst auf `START`?

---

## [S05] Betriebsart „DIN VDE 0751T1/90"

**Erreicht:** Softkey Zeile 4 von `[S02]` · **aufgenommen 2026-08-15**

```
  1  Betriebsart:    VDE
  2> Klassifikation          → …
  3> Grenzwertangabe         → …
  4> Nur Messgerät           → [S26]
  LED: noch nicht notiert
```

### Bestätigt: `VDE` ist die Kurzform

Die Betriebsart wird mit **`VDE`** abgekürzt, so wie die andere mit `IEC`
(`[S04]`). Damit steht das Gegenstück fest, nach dem in der
Prüflingsdatenbank `[S13]` zu suchen ist:

- [ ] **Beim Blättern durch die Datensätze nach einem Eintrag mit `VDE` in
      Zeile 2 suchen.** Findet sich einer, ist endgültig belegt, dass jeder
      Prüfling sein Prüfregime mit sich trägt.

### Beide Zweige heißen `Grenzwerteingabe`

Nachgelesen am 2026-08-15: In beiden Betriebsarten lautet der Menüpunkt
**`Grenzwerteingabe`**. Eine zwischenzeitlich vermutete Unterscheidung
(`-angabe` gegen `-eingabe`, also nur anzeigen gegen einstellen) beruhte auf
einem Abschreibfehler und ist gegenstandslos.

Die sachliche Frage dahinter bleibt aber offen und ist zu prüfen:

- [ ] **Sind die Grenzwerte in beiden Betriebsarten wirklich veränderbar?**
      DIN VDE 0751 gibt für die Wiederholungsprüfung feste Grenzwerte vor —
      dass das Gerät sie dort zur Eingabe anbietet, muss nicht heißen, dass es
      sie auch annimmt.
- [ ] **Führen beide Zweige eigene Werte?** Naheliegend, weil die Normen
      unterschiedliche Grenzen setzen — aber zu belegen.

⚠️ Zum Nachsehen genügt das Öffnen. **Nichts verändern**, in keinem der beiden
Zweige — die Werkseinstellung ist unbekannt und nicht wiederherstellbar.

---

## [S32] VDE → Grenzwerteingabe → Verfahrensfrage

**Erreicht:** Softkey Zeile 3 von `[S05]` · **aufgenommen 2026-08-15**

```
  1  Ableitstrommessung:
  2  Prüfling in Betrieb
  3> nehmen?     Ja        → …
  4>    Nein               → …
  LED: noch nicht notiert
```

### Nicht die Grenzwerttabelle, sondern zuerst das Verfahren

`Grenzwerteingabe` führt **nicht unmittelbar zu einer Werteliste**, sondern
stellt zuerst eine Verfahrensfrage. Das ist folgerichtig: **Ein Grenzwert für
den Ableitstrom ist ohne das Messverfahren nicht bestimmt.** DIN VDE 0751
setzt für die beiden Verfahren unterschiedliche Grenzen.

### 🔑 Die vorhergesagte Unterscheidung ist da

Der Erwartungsrahmen in `FUNKTIONSAUFNAHME.md` sagte für den VDE-Zweig
voraus, dass zwischen **Direktmessung** und **Ersatzableitstrommessung**
unterschieden wird. Genau das steckt hinter dieser Frage:

| Antwort | Verfahren |
|---|---|
| **`Ja`** | **Direktmessung** — der Prüfling läuft an der Prüfsteckdose, gemessen wird der tatsächlich fließende Ableitstrom. Realistisch, aber mit Netzspannung am Prüfling. |
| **`Nein`** | **Messung am stromlosen Prüfling** — Ersatzableitstrom- oder Differenzstromverfahren. Zwischen den gebrückten Netzkontakten und Gehäuse bzw. Anwendungsteil wird eine Prüfspannung angelegt. Sicherer, in der Wiederholungsprüfung üblich. |

- [ ] Bestätigen: Nennt das Gerät weiter unten die Verfahren beim Namen —
      `Ersatzableitstrom`, `Differenzstrom`, `Direktmessung`?
- [ ] Unterscheiden sich die Grenzwerte je nach Antwort? Das wäre der Beleg
      dafür, warum die Frage hier steht.

---

## [S33] VDE → Grenzwerteingabe → Schutzleiter

**Erreicht:** Antwort `Nein` auf `[S32]` · **aufgenommen 2026-08-15**

```
  1  Grenzwerteingabe:
  2  Schutzleiter
  3  <leer>
  4  R-PE :       Ω
  LED: noch nicht notiert
```

### Die Grenzwerte kommen einzeln, nicht als Liste

Nach der Verfahrensfrage folgt **ein Bildschirm je Grenzwert** — hier der
erste: der **Schutzleiterwiderstand**, bezeichnet als **`R-PE`**, Einheit
**`Ω`**.

Es ist also **keine blätterbare Tabelle**, sondern eine geführte Abfolge.
Damit erklärt sich auch, warum das Gerät ohne Blätterfunktion auskommt: Wo
andere Geräte eine Liste anbieten, führt der µP601 Schritt für Schritt.

- [ ] Womit geht es zum nächsten Grenzwert — `↑`, ein Softkey, oder erst nach
      einer Eingabe?
- [ ] **Wie viele Grenzwerte folgen insgesamt?** Die Abfolge ist die
      vollständige Liste der Prüfgrößen, die dieses Gerät kennt — und damit
      die genaueste Antwort auf die Ausgangsfrage „was kann das Gerät".

### Offen und wichtig: Wird der gespeicherte Wert angezeigt?

Auf der Zeile steht `R-PE :` und rechts die Einheit `Ω` — **ein Zahlenwert
wurde nicht mit notiert.**

### Geklärt: Der gespeicherte Wert wird *nicht* angezeigt

Zwischen `:` und `Ω` steht **keine Zahl** (bestätigt 2026-08-15). Das Feld ist
leer und erwartet eine Eingabe, **ohne den geltenden Grenzwert zu zeigen.**

**Damit ist die Grenzwerttabelle auf diesem Weg nicht lesbar.** Der Plan,
sie hier abzuschreiben, ist gescheitert.

### Das ist kein Einzelfall, sondern Bauart

Dasselbe Verhalten zeigt die Uhr-Eingabemaske `[S10]`: Auch dort sind alle
Felder leer, obwohl im Gerät Werte stehen. Daraus wird eine Regel:

> **Eingabemasken zeigen den Ist-Wert nicht.** Sie nehmen entgegen, sie
> berichten nicht.

Der Ist-Wert steht stattdessen an anderer Stelle — bei der Uhr auf einem
eigenen Bildschirm `Anzeigen` `[S11]`, sonst in der Kopfzeile
(`Betriebsart: IEC`, `Uhrzeit ?`).

- [ ] **Gibt es für die Grenzwerte ein Gegenstück zu `Anzeigen`?** Bei der Uhr
      hat Bender Ansehen und Ändern sauber getrennt. Falls es das hier auch
      gibt, ist die Tabelle doch lesbar — zu suchen im `F`-Zweig oder als
      weiterer Punkt neben `Grenzwerteingabe`.

⚠️ **Erst recht nichts eingeben.** Ein leeres Feld verrät nicht, was es
ersetzen würde. Diesen Bildschirm ausschließlich mit `START` verlassen.

### `↑` leuchtet — und es ist unklar, was es tut

Auf `[S33]` ist die **`↑`-LED an** (belegt 2026-08-15). Nach dem
Tastenmodell heißt das „übernehmen". Bei einem **leeren** Feld sind aber zwei
Wirkungen denkbar, und sie sind nicht zu unterscheiden, ohne es zu tun:

| Deutung | Folge bei leerem Feld |
|---|---|
| **`↑` = Wert übernehmen** | Der gespeicherte Grenzwert wird durch nichts oder durch `0` ersetzt — **Verlust** |
| **`↑` = weiter zum nächsten Grenzwert** | Leeres Feld heißt „unverändert lassen", die Abfolge läuft weiter — **harmlos** |

Für eine geführte Abfolge wäre die zweite Lesart naheliegend. Sie am
Grenzwertsatz auszuprobieren, wäre trotzdem leichtsinnig: Trifft die erste zu,
ist ein Wert unwiederbringlich weg, dessen Ausgangszustand niemand kennt.

### Geklärt (2026-08-15): `↑` blättert weiter

Mit leerem Feld gedrückt, **springt das Gerät zum nächsten Grenzwert** — der
ebenfalls leer ist. `↑` wirkt hier also als **Weiter**, nicht als
„übernehmen".

**Damit ist die Abfolge gefahrlos durchblätterbar** — und das ist mehr wert,
als es zunächst klingt:

> **Die Reihenfolge der Grenzwertbildschirme ist die vollständige Liste der
> Größen, die dieses Gerät bewertet.** Auch ohne die Zahlenwerte beantwortet
> sie die Ausgangsfrage „was kann das Gerät" genauer als alles andere bisher.

- [ ] **Die ganze Abfolge durchblättern und jede Bezeichnung mit Einheit
      notieren** — `R-PE : Ω`, und was danach kommt. Ergebnis unten eintragen.
- [ ] Läuft sie am Ende um, oder mündet sie irgendwo?
- [ ] Dieselbe Abfolge im **IEC-Zweig** aufnehmen und vergleichen. Der
      Unterschied zwischen beiden Listen ist der Unterschied zwischen den
      beiden Normwelten, wie dieses Gerät sie sieht.

**Restunsicherheit, ehrlich vermerkt:** Dass das erste Feld *unverändert*
blieb, ist damit **nicht** bewiesen — nachsehen lässt es sich nicht, weil das
Gerät gespeicherte Grenzwerte nirgends anzeigt. Die Wahrscheinlichkeit spricht
klar für „unverändert" (sonst wären fortgeschaltete Felder auch nicht leer,
sondern genullt sichtbar), aber die Gegenprobe bleibt das **Prüfprotokoll**:
Steht dort ein plausibler Grenzwert neben dem Messwert, ist alles in Ordnung.

### Der gefahrlose Ersatzversuch: an der Uhr

**Die Uhr ist das ideale Versuchsobjekt.** Ihre Eingabemaske `[S10]` ist
genauso gebaut — mehrere Felder, alle leer —, und ihr Inhalt ist **ohne Wert**:
Ohne Batterie geht er beim Ausschalten ohnehin verloren, und neu stellen
dauert eine halbe Minute.

- [ ] **Versuch:** Uhr stellen, damit ein bekannter Stand vorliegt. Dann
      `[S10]` erneut aufrufen, **ein einzelnes Feld leer lassen**, die übrigen
      ausfüllen, `↑` drücken — und in `[S11] Anzeigen` nachsehen.
      → **Alter Wert steht noch:** Leer bedeutet „unverändert". Dann ist `↑`
        auch bei den Grenzwerten ungefährlich.
      → **Feld ist genullt:** Leer überschreibt. Dann darf `↑` auf `[S33]`
        **nie** gedrückt werden.

Ein Versuch am wertlosen Objekt, der die Frage für das wertvolle beantwortet.

### Wie die Grenzwerte doch noch zu bekommen sind

**Über ein vollständiges Prüfprotokoll.** In einem echten Prüfablauf — nicht
in `Nur Messung` — bewertet das Gerät jeden Messwert und druckt ihn aus.
Prüfprotokolle solcher Geräte stellen üblicherweise **Messwert und Grenzwert
gegenüber**, samt Urteil.

Das ist der eine Ausdruck, der sich wirklich lohnt:

- [ ] Einen vollständigen Prüfablauf an einem **harmlosen Prüfling** fahren
      (`FUNKTIONSAUFNAHME.md`, Abschnitt F) und das Protokoll aufheben.
      Es liefert in einem Zug das **Protokollformat**, die **Prüfschritt-
      reihenfolge** und voraussichtlich die **Grenzwerte**.
- [ ] Ergibt sich daraus die Tabelle, in `research/` als eigenes Dokument
      festhalten — sie existiert sonst nirgends.

Alternativ später über die RS-232, wenn dort dasselbe ausgegeben wird.

### Zeichensatz: `Ω` ist bestätigt

Die Anzeige stellt **`Ω`** dar. Zusammen mit dem `µ` aus `[S31]` sind damit
zwei Zeichen belegt, die im **HD44780-A00-Zeichensatz** enthalten sind
(`µ` auf `0xE4`, `Ω` auf `0xF4`).

Die Annahme eines HD44780-kompatiblen Zeichendisplays ist damit gut gestützt.
Offen bleibt allein die Herkunft der **Umlaute** — sie fehlen im A00-Satz und
dürften als selbstdefinierte Zeichen im CGRAM liegen
(`FUNKTIONSAUFNAHME.md`, Abschnitt A).

⚠️ **Die Antwort `Ja` ist eine Ansage.** Sie bedeutet, dass das Gerät im
weiteren Verlauf **Netzspannung auf die Prüfsteckdose legt** und den Prüfling
in Betrieb nimmt. Solange nur kartiert wird und nichts angeschlossen ist, ist
das folgenlos — aber es ist der Punkt, ab dem das gilt.

### Layout und Schreibweise

Die Frage läuft über die Zeilen 2 und 3, und **Zeile 3 trägt zugleich die
Antwort `Ja`** — dasselbe Muster wie `[S18]` („fest angeschlossenes / Gerät ?
ja"). Die Regel von dort bestätigt sich.


---

### Aufbau identisch zum IEC-Zweig

Beide Betriebsarten bieten dieselben drei Wege. Der Unterschied liegt also
**nicht in der Gliederung**, sondern in dem, was hinter den Zweigen steckt —
Prüfschritte, Verfahren und Grenzwerte. Für die Aufnahme heißt das: Der
VDE-Zweig ist kein Sonderfall, sondern eine zweite vollständige Ausprägung
desselben Gerüsts.

---

## [S26] VDE → Nur Messgerät

**Erreicht:** `Nur Messgerät` von `[S05]` · **aufgenommen 2026-08-14**

```
  1  >>> Nur Messung <<<
  2> Schutzleiter           → [S27]
  3> Isolation              → …
  4> Ableitstrom            → …
  LED: noch nicht notiert
```

**Die drei Grundmessungen des Geräts, auf einem Bildschirm.** Damit ist die
oberste Gliederung des Messteils bekannt:

| Zweig | Deckt ab |
|---|---|
| **Schutzleiter** | Durchgang und Widerstand des Schutzleiters |
| **Isolation** | Isolationswiderstand, Piktogramm mit `MΩ` |
| **Ableitstrom** | die Strommessungen, Piktogramm mit `µA` |

Die Kopfzeile ist hier nicht beschreibend, sondern eine **Betriebsartwarnung**:
`>>> Nur Messung <<<`, in Pfeile gesetzt. Das Gerät weist darauf hin, dass
hier **ohne Bewertung und ohne Prüflingsbezug** gemessen wird.

**Schreibweise:** Die Zeile erscheint mal als `>>> Nur Messung <<<`, mal als
`>>> NUR MESSUNG <<<` (siehe `[S27]`). Weitere Uneinheitlichkeit im
Softwarestand `IVM429 D`, wie `ja`/`Nein` und `SET:`.

---

## [S27] Nur Messung → Schutzleiter → Netzleitung

**Erreicht:** Softkey Zeile 2 von `[S26]` · **aufgenommen 2026-08-14**

```
  1  >>> NUR MESSUNG <<<
  2  Netzleitung
  3> fest                   → …
  4> abnehmbar              → [S28]
  LED: noch nicht notiert
```

Dieselbe Unterscheidung wie in der Klassifikation des IEC-Zweigs (`[S18]`),
hier auf die Leitung bezogen: **fest angeschlossen** oder **abnehmbar**. Sie
entscheidet, ob überhaupt eine Kupplung zu prüfen ist.

---

## [S28] Nur Messung → Schutzleiter → abnehmbar

**Erreicht:** Softkey Zeile 4 von `[S27]` · **aufgenommen 2026-08-14**

```
  1  >>> Nur Messung <<<
  2  Schutzleiter
  3> Zuleitung              → [S29]
  4> Gehäuse                → …
  LED: noch nicht notiert
```

Zwei verschiedene Schutzleitermessungen:

- **`Zuleitung`** — die abnehmbare Leitung für sich allein, von Stecker zu
  Kupplung. **Das ist Piktogramm 3** (Hand mit zwei Kabelenden).
- **`Gehäuse`** — vom Netzstecker zum berührbaren Metall des Prüflings,
  angetastet mit der Prüfspitze. Vermutlich Piktogramm 2.

---

## [S29] Messung: Schutzleiter der Zuleitung

**Erreicht:** Softkey Zeile 3 von `[S28]` · **durchgeführt 2026-08-14**

Die Messung läuft und zeigt den Widerstand in Ohm.
Erster Messwert: **0,109 Ω**, Prüfstrom **16 A AC** (mit der Stromzange
gemessen, das Gerät selbst nennt ihn nicht — `FUNKTIONSAUFNAHME.md`,
Abschnitt F).

### 🔑 Die Piktogramme der Frontplatte sind beleuchtet

**Beim Start der Messung leuchtet das dritte Piktogramm auf** — das mit der
Hand und den beiden Kabelenden.

Das ist ein Befund von grundsätzlicher Bedeutung: **Die sechs Schaltbilder auf
der Frontplatte sind keine gedruckten Beschriftungen, sondern hinterleuchtete
Anzeigen.** Sie zeigen im Betrieb, **welcher Messaufbau gerade aktiv ist.**

Damit ist die Frontplatte ein **Schaltbild-Display**: Der Anwender sieht nicht
nur einen Zahlenwert auf vier Zeilen, sondern die zugehörige Beschaltung als
Bild — welche Buchsen beteiligt sind, wo der Schutzleiter aufgetrennt wird,
wogegen gemessen wird. Für ein Gerät mit einem so kleinen Textdisplay ist das
eine elegante Lösung.

**Und es macht die Piktogramme entschlüsselbar:** Jeder Messpunkt im Menü
lässt sich seinem Schaltbild zuordnen, indem man beobachtet, welche Fläche
aufleuchtet. Die Frage aus der Frontplattenaufnahme — was zeigen die sechs
Bilder? — ist damit **systematisch beantwortbar**, ohne Handbuch.

- [ ] **Zuordnungstabelle anlegen:** je Menüpfad notieren, welches Piktogramm
      leuchtet. Nach wenigen Messungen ist die Frontplatte vollständig
      entschlüsselt.
- [ ] Leuchtet immer **genau eines**, oder können mehrere gleichzeitig an sein?
- [ ] Leuchten sie auch im **Prüfablauf** (nicht nur in „Nur Messung")?
- [ ] Sind es LEDs hinter der Folie, oder Glühlampen? Bei Glühlampen wäre das
      ein künftiges Verschleißthema.

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

### Nachtrag (2026-08-14): Der Datenbestand umfasst rund 69 Einträge

Beim Blättern in `[S13]` gezählt: **etwa 69 verschiedene Gerätenummern.**

⚠️ **Die Zahl ist eine Schätzung, kein Messwert.** Der Zähler hat beim
Durchblättern möglicherweise Tastendrücke mitgezählt, auf die das Gerät nicht
reagiert hat. Die tatsächliche Zahl kann darunter liegen — und die
Rechnung unten steht und fällt mit ihr.

Damit ist die Lesart „**57 = Anzahl der gespeicherten Datensätze**"
**widerlegt** — es sind mehr.

**Aber die Zahlen passen zusammen, wenn 57 die *freien* Plätze meint:**

```
69 belegt  +  57 frei  =  126
```

126 ist eine plausible Speicherkapazität für ein Gerät dieser Bauart —
zwei Plätze unter 128. Das wäre die schlüssigste Deutung: **Zeile 1 von
`[S06]` zeigt an, wie viele Prüflinge noch angelegt werden können.**

Das ist vorerst Arithmetik, keine Beobachtung. Es steht und fällt mit der
genauen Zahl:

- [ ] **Verlässlich auszählen — aber nicht durch Zählen von Tastendrücken.**
      Stattdessen jede angezeigte `Gerätenr` mitschreiben. Dann fallen
      Wiederholungen und Auslassungen auf, und ein hängengebliebener
      Tastendruck verfälscht das Ergebnis nicht.
      **Noch besser: warten, bis die RS-232 läuft** — ein Auszug des ganzen
      Bestands liefert die Zahl nebenbei und fehlerfrei
      (`FUNKTIONSAUFNAHME.md`, Abschnitt E).
- [ ] Zeigt sich irgendwo im Menü eine **Kapazitätsangabe**?
- [ ] Ändert sich die `57`, wenn eine andere Betriebsart gewählt ist?
      (Getrennte Kontingente für IEC und VDE wären denkbar.)

**Nicht ausprobieren:** Einen Datensatz anlegen, um zu sehen, ob die Zahl auf
56 fällt, wäre der direkte Beweis — aber ein Schreibvorgang im Bestand des
Vorbesitzers. Erst, wenn der Bestand gesichert ist.

Die zuvor erwogene Lesart „Bildschirmnummer" bleibt offen; sie klärt sich
beiläufig, sobald auf einem anderen Bildschirm eine Zahl an derselben Stelle
auftaucht. Ihre ursprüngliche Bedeutung — als möglicher Weg zur Bedienung
langer Listen — ist dagegen hinfällig: **Listen werden mit `↑`/`↓` durch-
geblättert** (`[S13]`).

### Noch aufzunehmen

- [ ] LED-Zustand aller sieben Tasten
- [ ] Wohin führt `↓` von hier — nach `[S02]` zurück?
- [ ] Was tut `F` von hier aus? Gibt es eine dritte Nebenebene?
- [ ] Gegenprobe zu `Betriebsart ?`: erst Norm wählen, dann `F`
- [ ] Eine Zahl über den Nummernblock eintippen — reagiert das Gerät?

---

## [S07] Messroutine

**Erreicht:** Softkey Zeile 2 von `[S06]` · **aufgenommen 2026-08-14**

```
  1  Datenbank :
  2  Zugriff ?
  3> über Gerätenummer       → [S12]
  4> über Suchen             → [S13]
  LED: noch nicht notiert
```

### Der Messablauf beginnt nicht mit einer Messung, sondern mit dem Prüfling

Bemerkenswert: Wer „Messroutine" wählt, landet **nicht** bei den Messgrößen,
sondern bei einer **Datenbank**. Das Gerät ist prüflingsorientiert gebaut —
zuerst wird festgelegt, *woran* gemessen wird, dann erst *was*.

Das passt zum Einsatzzweck: Ein Sicherheitstester in der Medizintechnik prüft
denselben Gerätebestand in wiederkehrenden Abständen. Die Zuordnung
Messwert → Prüfling ist die eigentliche Leistung, nicht die Einzelmessung.

**Damit ist auch klar, wo die sechs Piktogramme der Frontplatte auftauchen:**
erst hinter der Prüflingsauswahl, nicht davor.

### Die bekannten Muster bestätigen sich

- **Zweizeilige Überschrift**: `Datenbank :` / `Zugriff ?` — dieselbe Form wie
  `Betriebsart:` / `Prüfungen nach:` in `[S02]`.
- **`?` für „nicht gesetzt"**: `Zugriff ?` — die Zugriffsart ist noch nicht
  gewählt. Dritter Beleg für die Konvention.

### Dieser Zweig beantwortet womöglich die Batteriefrage

`über Suchen` führt in den vorhandenen Datenbestand. **Zeigt sich dort etwas,
haben die Daten des Vorbesitzers die leere Pufferbatterie überlebt** — die
offene Frage aus `BATTERIE.md`, Folge 2, wäre dann hier beantwortet, ohne den
Umweg über `[S08]`.

⚠️ **Nur ansehen, nicht messen.** Die Prüflingsauswahl ist der Einstieg in
einen Prüfablauf, an dessen Ende Netzspannung auf der Prüfsteckdose liegt.
Solange nichts angeschlossen ist, ist das Blättern in der Datenbank
ungefährlich — aber `START` nicht aus Versehen drücken.

### Und hier zeigt sich, wie das Gerät Listen bedient

`über Suchen` setzt einen Bestand voraus, der größer ist als drei Einträge.
**Das ist die Stelle, an der sich die seit `[S02]` offene Frage klärt:** Wie
stellt ein Gerät mit drei Softkeys und ohne Blättertasten eine lange Liste dar?

Zu beobachten:

- [ ] Erscheinen mehrere Treffer gleichzeitig, oder einer nach dem anderen?
- [ ] Womit wird weitergeblättert — ein Softkey, `↑`, der Nummernblock?
- [ ] Trägt der Bildschirm rechts oben eine Zahl wie die `57` in `[S06]`?

### Offene Frage: Was heißt „Gerätenummer" hier?

Auf dem **Selbsttest-Ausdruck** (`[S03]`) steht ebenfalls eine
`Gerätenummer` — dort naheliegenderweise die des µP601 selbst. Hier bezeichnet
derselbe Begriff die Kennung eines **Prüflings**.

- [ ] Sind das zwei verschiedene Dinge, oder benutzt die Firmware einen
      einzigen Begriff für beides? Vergleich: Taucht die Nummer vom
      Selbsttest-Ausdruck im Datenbestand als Eintrag auf?

---

## [S12] Datenbank → über Gerätenummer

**Erreicht:** Softkey Zeile 3 von `[S07]` · **noch nicht betreten**

Direkte Eingabe einer Prüflingsnummer, vermutlich über den Nummernblock.
Erwartete Form: eine Eingabemaske wie `[S10]`, mit `↑` zum Übernehmen.

## [S13] Datenbank → über Suchen

**Erreicht:** Softkey Zeile 4 von `[S07]` · **aufgenommen 2026-08-14**

```
  1  Gerätenr:112
  2  IEC                     (linksbündig)
  3> Daten                   → [S14]
  ?> Ende                    → zurück
  LED: ↑ ● · ↓ ●  — blättern durch den Datenbestand
```

- [ ] **Klärungsbedarf zur Zeilenzuordnung:** Stehen `Daten` und `Ende` auf
      **einer** Zeile nebeneinander, oder auf Zeile 3 und Zeile 4? Ersteres
      wäre ein Bruch mit dem bisherigen Bild, dass jede belegte Zeile genau
      einem Softkey entspricht — und damit ein wichtiger Nachtrag zur Notation.

## Der Datenbestand des Vorbesitzers ist erhalten

**`Gerätenr:112`** — es sind Prüflinge gespeichert, und mit `↑`/`↓` lässt sich
durch sie blättern.

Damit ist die offene Frage aus `BATTERIE.md` beantwortet: **Der Messdaten-
speicher hing nicht an der leeren Pufferbatterie.** Er ist nichtflüchtig —
so wie Betreibertext und Gerätenummer, die den Spannungsverlust ebenfalls
überstanden haben.

**Der Bestand ist damit auch beim späteren Batteriewechsel nicht gefährdet.**

⚠️ Trotzdem gilt weiter: Es ist die einzige Kopie. Keine Lösch-, Rücksetz-
oder Neuanlagefunktion bestätigen, bevor der Bestand gesichert ist.

## `↑`/`↓` blättern hier durch Datensätze — Nachtrag zum Tastenmodell

Bisher galt: `↑` = eine Ebene hinein oder bestätigen, `↓` = eine Ebene heraus.
**In einer Liste bewegen sie sich stattdessen durch die Einträge.**

Die Lesart bleibt im Kern erhalten — `↑` vorwärts, `↓` rückwärts —, aber
**worin** vorwärts und rückwärts gegangen wird, hängt vom Bildschirm ab:

| Bildschirmart | `↑` | `↓` |
|---|---|---|
| Auswahlmenü | eine Ebene hinein | eine Ebene heraus |
| Eingabemaske `[S10]` | Wert übernehmen | ○ dunkel |
| **Liste `[S13]`** | **nächster Datensatz** | **vorheriger Datensatz** |

**Damit ist die seit `[S02]` offene Frage beantwortet:** Das Gerät braucht
keine gesonderte Blätterfunktion und keine Direktwahl über den Nummernblock —
in Listen sind `↑`/`↓` die Blättertasten. Der Menübaum ist deshalb schmal
gebaut, die Listen aber beliebig lang.

Der Verlass bleibt die LED: Sie sagt, dass die Taste etwas tut. Was sie tut,
sagt der Bildschirm.

## Zeile 2: `IEC` — vermutlich das Prüfregime des Datensatzes

Beim Blättern ändert sich **mit der Gerätenummer auch Zeile 2.** Sie gehört
also zum Datensatz, nicht zum Bildschirm.

Arbeitsvermutung: Dort steht, **nach welcher Norm dieser Prüfling geprüft
wird** — passend zur Betriebsartenwahl in `[S02]`, wo `IEC 601-1:1988` und
`DIN VDE 0751T1/90` zur Wahl stehen. Jeder Prüfling trüge damit sein
Prüfregime mit sich.

- [ ] **Gegenprobe:** Weiterblättern, bis ein Datensatz erscheint, in dem
      **nicht** `IEC` steht. Taucht dort `VDE`, `0751` oder Ähnliches auf, ist
      die Deutung belegt.
- [ ] Erscheint noch etwas anderes in Zeile 2 — Klassifizierung des Prüflings
      (Schutzklasse, Anwendungsteil-Typ), ein Name, ein Datum?

## Weiteres zum Mitschreiben beim Blättern

- [ ] **Wie viele Datensätze gibt es?** Bis ans Ende blättern und zählen.
      Passt die Zahl zur `57` aus `[S06]`? Dann wäre die `57` ein Zähler des
      Datenbestands — und keine Bildschirmnummer.
      Beachte: `Gerätenr:112` ist größer als 57, die Nummern müssen also nicht
      lückenlos sein.
- [ ] Niedrigste und höchste Gerätenummer
- [ ] Läuft die Liste am Ende um, oder stoppt sie?
- [ ] Trägt dieser Bildschirm rechts oben eine Zahl?
- [ ] Was tut `F` von hier aus?

---

## [S14] Datensatz → Daten

**Erreicht:** Softkey `Daten` von `[S13]` · **zurückgestellt 2026-08-14**

Hier liegen die Angaben zu einem Prüfling — das, was der Vorbesitzer über Jahre
erfasst hat.

### Die Messdaten sind nur über den Drucker zugänglich

**Befund:** Die Messdaten lassen sich **ausschließlich ausdrucken**, nicht auf
der Anzeige durchsehen. Bei vier Zeilen zu je etwa zwanzig Zeichen ist das
nachvollziehbar — ein vollständiger Prüfbericht mit Messgrößen, Bedingungen
und Grenzwerten passt dort nicht hinein. Der Drucker ist nicht Beiwerk,
sondern **die eigentliche Ausgabe des Geräts.**

### Entscheidung: zurückgestellt

**Der Bestand wird vorerst nicht ausgedruckt.** Jeder Ausdruck belastet den
**Nadeldrucker** — Farbband und Druckkopf sind Verschleißteile, für die es
nach über dreißig Jahren keinen selbstverständlichen Ersatz gibt. 69 Datensätze
einzeln auszudrucken, nur um sie zu lesen, wäre ein schlechtes Geschäft.

**Damit hängt die Auswertung des Datenbestands an der RS-232.** Sie ist nicht
mehr nur bequemer, sondern der **einzige verschleißfreie Weg** an diese Daten.
Das Vorhaben aus `STAND.md` — den Ausdruck elektronisch aufnehmen — bekommt
dadurch einen zweiten, unabhängigen Zweck: nicht nur künftige Protokolle
sichern, sondern den **vorhandenen Bestand überhaupt erst lesbar machen.**

Beruhigend dabei: Der Bestand ist nichtflüchtig und hat schon Jahre ohne
Batterie überstanden. **Es eilt nicht.**

### Wenn die Schnittstelle läuft

- [ ] Bestand vollständig auslesen und sichern
- [ ] Welche Felder hat ein Datensatz — Stammdaten, Messwerte, oder beides?
- [ ] Datumsangaben: wegen der stehengebliebenen Uhr unzuverlässig, die
      **Reihenfolge** bleibt aussagekräftig
- [ ] Exakte Zahl der Datensätze — Gegenprobe zur `57` in `[S06]`

### Vorher, ohne Verschleiß

- [ ] **Einen einzigen** Datensatz ausdrucken, um das Protokollformat zu
      kennen. Einer genügt und ist gut investiert: Er zeigt, welche Felder es
      gibt, und dient später als Vergleich für das, was über die RS-232
      ankommt.
- [ ] Zeigt `[S14]` auf der Anzeige wenigstens **einzelne Felder**, bevor
      gedruckt wird — oder führt der Weg unmittelbar zum Ausdruck?

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
