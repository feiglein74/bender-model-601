# Ausdruck digital aufnehmen — Entwurf

Ziel: Die Protokolle des µP601 **elektronisch mitlesen, darstellen und
speichern**, statt sie nur auf Papier zu haben. Zwei Ausbaustufen:

1. **Auslesen** — Protokolle auf einem Rechner erfassen und ablegen
2. **Anzeige** — ein eigenständiges Gerät, das den Ausdruck lesbar darstellt

Stufe 2 setzt Stufe 1 voraus. Alles hängt an einer Frage, die noch offen ist.

---

## Ausgangslage

| Befund | Woher |
|---|---|
| **RS-232 vorhanden**, 25-polig, `V.24/RS-232C`, `BAUD 4800` | Rückwand |
| Druckwerk **ohne eigene Steuerung**, Hauptplatine treibt den Kopf direkt | ausgebautes Modul |
| Protokolle sind **24 Spalten breit**, feste Zeichenpositionen | Selbsttest-Ausdruck |
| Aufbau: Kopf, Trennlinie, Ergebnis, Einzelangaben | Selbsttest-Ausdruck |
| Messdaten sind **nur über den Drucker** abrufbar | `MENUEBAUM.md`, `[S14]` |

**Am Druckerstecker liegt kein Zeichenstrom**, sondern Ansteuermuster für
Nadelmagnete. Die RS-232 ist damit der einzig sinnvolle Weg — vorbehaltlich
dessen, was sie tatsächlich ausgibt.

---

## Die eine Frage, die alles entscheidet

> **Sendet die Schnittstelle von sich aus, was gedruckt wird?**

Drei mögliche Antworten, drei völlig verschiedene Projekte:

| Fall | Was die Schnittstelle tut | Aufwand |
|---|---|---|
| **A — Protokollausgabe** | Sie gibt denselben Text aus, der gedruckt wird | **gering.** Mitschneiden, fertig |
| **B — Befehlsschnittstelle** | Sie antwortet nur auf Befehle | **hoch.** Befehlssatz ist unbekannt und müsste erraten werden |
| **C — stumm** | Sie tut nichts ohne Konfiguration | **mittel.** Erst die Einstellung im Menü finden |

**Bevor das nicht geklärt ist, lohnt kein Hardwareentwurf.** Der Versuch dazu
kostet einen Nachmittag und einen Adapter.

---

## Schritt 1 — Kabel und Anschluss klären

- [ ] **Stecker oder Buchse** am Gerät? 25-polig, aber die Bauart entscheidet
      das Gegenstück
- [ ] **USB-RS-232-Adapter** mit echtem Pegelwandler beschaffen, dazu einen
      Übergang 25-polig ↔ 9-polig

⚠️ **Echtes V.24 mit ±12 V.** Ein Mikrocontroller-UART direkt angeschlossen
wird zerstört. Pegelwandler ist Pflicht — `MAX3232` oder ein fertiger Adapter.

### Welche Ader sendet? — der Zwei-Minuten-Test

Statt Belegungen zu raten: **Spannung messen.** Eine RS-232-Sendeleitung liegt
im Ruhezustand auf etwa **−12 V** gegen Signalmasse; eine Empfangsleitung wird
vom Gerät nicht getrieben und liegt nahe 0 V.

- [ ] Gerät einschalten, Voltmeter an **Pin 7** (Signalmasse) und der Reihe
      nach an **Pin 2** und **Pin 3**
- [ ] Die Ader mit etwa **−12 V ist der Ausgang des µP601.** Sie gehört an den
      Empfangseingang des Adapters

Damit erübrigt sich die Frage, ob das Gerät als DTE oder DCE verdrahtet ist —
und ob ein Nullmodemkabel nötig wäre.

**Erwartete Normbelegung** (25-polig, DTE), falls sie zutrifft:

| Pin | Signal |
|---|---|
| 2 | TxD — Sendedaten |
| 3 | RxD — Empfangsdaten |
| 4 / 5 | RTS / CTS |
| 6 / 20 | DSR / DTR |
| 7 | **Signalmasse** |

---

## Schritt 2 — Passiv mithören

Nur empfangen, nichts senden. Der risikoloseste Versuch überhaupt.

- [ ] Terminalprogramm auf **4800 Baud**, zunächst **8N1**, Mitschnitt in eine
      Datei
- [ ] **Selbsttest auslösen** (`↓` vom Startbildschirm) und beobachten, ob
      etwas ankommt
- [ ] Kommt Unlesbares, **7E1** probieren — die zweite übliche Einstellung
      dieser Zeit. Ergibt sich dann Klartext, war es das
- [ ] Kommt gar nichts: **Menü nach Schnittstelleneinstellungen absuchen**,
      besonders im `F`-Zweig (`MENUEBAUM.md`, `[S06]`), wo Uhr und
      Messdatenverwaltung liegen

**Rohbytes mitschneiden, nicht nur Text.** Steuerzeichen wie Zeilenvorschub,
Seitenvorschub oder Papierschnitt sind für das spätere Zerlegen wichtig und
gehen in einer reinen Textanzeige verloren.

### Was der Mitschnitt beantwortet

- Gibt es überhaupt Ausgabe, und wann — beim Drucken, oder unaufgefordert?
- Ist es **derselbe Text wie auf Papier**, oder ein eigenes Datenformat?
- Welche Steuerzeichen trennen Zeilen und Protokolle?

---

## Schritt 3 — je nach Ergebnis

### Fall A — die Schnittstelle gibt das Protokoll aus

Dann ist das Wesentliche geschafft, und es bleibt Fleißarbeit:

- **Erfassen**: Mitschnitt in eine Datei, ein Protokoll je Trennmarke
- **Zerlegen**: Das Format ist **feste 24-Spalten-Zeilen** — Feldnamen links,
  Werte rechts, wie im Selbsttest-Ausdruck. Ein kurzes Skript in `tools/`
  genügt, das die Zeilen in Felder überführt
- **Ablegen**: eine Textdatei je Protokoll, dazu eine Übersichtstabelle

**Damit wäre nebenbei auch der Datenbestand des Vorbesitzers zu retten:** die
rund 69 gespeicherten Prüflinge (`MENUEBAUM.md`, `[S13]`), an die sonst nur
über 69 Ausdrucke heranzukommen wäre.

### Fall B — reine Befehlsschnittstelle

Ungünstig, aber nicht aussichtslos. Beim Vorgängerprojekt war die
Schnittstelle des UNIMET vollständig dokumentiert — mit Prüfschritten und
Befehlen als Zahlencodes. Für den µP601 gibt es das nicht.

- Anfrage bei **Bender** und bei **MACK Medizintechnik** (`STAND.md`) —
  gerade eine Schnittstellenbeschreibung ist etwas, das ein Fachhändler
  gehabt haben könnte
- Behutsames Ausprobieren gängiger Muster: Wagenrücklauf, `?`, `ENQ`, kurze
  Buchstabenbefehle. **Nichts senden, was nach Schreibbefehl aussieht**

### Fall C — stumm

Erst die Einstellung finden. Bleibt es dabei, greift die Rückfallebene.

---

## Rückfallebene: den Druckkopf mitlesen

Falls die RS-232 nichts hergibt. Aufwendig, aber machbar — und es zerstört
nichts, weil nur mitgehört wird.

Am 13-poligen Steckverbinder liegen die Ansteuersignale des Druckkopfs. Daraus
lässt sich der Text zurückgewinnen:

1. **Nadelleitungen und Taktsignal mitschneiden** — Logikanalysator, wenige
   Kanäle genügen; nach dem Flexkabel sind es sechs bis sieben Nadeln
2. **Punktmuster rekonstruieren** — jedes Zeichen ist ein Raster aus wenigen
   Spalten zu je sieben Punkten
3. **Muster den Zeichen zuordnen** — der Vorrat ist klein, gut hundert
   Zeichen. Eine einmal erstellte Tabelle gilt für immer

⚠️ **Pegel prüfen, bevor etwas angeschlossen wird.** Magnettreiber arbeiten
oft mit deutlich mehr als 5 V; ein Logikanalysator braucht dann einen
Spannungsteiler.

**Als Nebenprodukt entstünde dabei der komplette Zeichensatz des Geräts** —
eine hübsche Sache, aber kein Grund, diesen Weg zu wählen, solange die RS-232
nicht ausgeschöpft ist.

---

## Erst danach: die Anzeige

Welche Hardware die Darstellung übernimmt, ist die **letzte** Entscheidung,
nicht die erste. Sie hängt davon ab, was ankommt.

| Aufbau | Wofür |
|---|---|
| **Rechner mit Terminalprogramm** | der Anfang. Kostet nichts, beweist alles |
| **Kleinrechner mit Bildschirm** | ein eigenständiger Kasten neben dem Gerät, der Protokolle anzeigt und ablegt |
| **Mikrocontroller mit Pegelwandler** | die kleinste Lösung; kann Protokolle ins Netz stellen. Zwingend mit `MAX3232` oder gleichwertig |

**Empfehlung: mit dem Rechner anfangen.** Solange nicht feststeht, ob und was
die Schnittstelle liefert, ist jede gebaute Hardware eine Wette.

---

## Was das Gerät dabei nicht merken darf

Das Vorhaben ist ausdrücklich **nicht invasiv**:

- Am Gerät wird nichts verändert, nichts umgelötet, nichts umkonfiguriert
- Nur **empfangen**, solange nicht feststeht, was Senden auslöst
- Der Ausdruck bleibt die maßgebliche Ausgabe; die digitale Fassung ist eine
  Zweitschrift, kein Ersatz

Damit bleibt der Auslieferungszustand erhalten — die oberste Regel dieses
Projekts (`../CLAUDE.md`).
