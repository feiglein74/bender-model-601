# Batteriefach und Pufferung

## Befund (2026-08-14)

Ein **von außen zugängliches Batteriefach** ist vorhanden. **Zwei Kontakte sind
vollständig oxidiert**, grün-blau — also ausgelaufene Zelle und angegriffenes
Kupfer bzw. Messing.

Zusammenhang: Der Selbsttest druckt **Zeit und Datum** aus
(`MENUEBAUM.md`, `[S03]`). Das Gerät hat also eine Uhr, die im ausgeschalteten
Zustand weiterlaufen soll — und das Batteriefach ist mit hoher
Wahrscheinlichkeit genau deren Versorgung.

**Geklärt (2026-08-14): Die gedruckte Zeit stimmt nicht.**
Die Pufferung ist **tot** — was zur Korrosion passt und bei diesem Gerätealter
zu erwarten war.

- [ ] Den **gedruckten Falschwert wörtlich notieren.** Ein Vorgabedatum verrät
      oft die Epoche der Firmware (`01.01.1990`, `01.01.80`, `00:00`) und ist
      damit ein Datierungshinweis auf den Softwarestand `IVM429 D`.

### Folge 1 — alle gespeicherten Datumsangaben sind unzuverlässig

Zeitstempel im Gerätespeicher können aus Zeiträumen stammen, in denen die Uhr
bereits falsch lief. Der zeitliche Rahmen des Vorbesitzers
(`FUNKTIONSAUFNAHME.md`, Abschnitt D) lässt sich daraus **nicht mehr sicher
ableiten** — allenfalls die Reihenfolge der Einträge.

### Folge 2 — die wichtigere: Lebt der Datenspeicher noch?

Wenn dieselbe Zelle **auch den Datenspeicher** puffert, sind die Prüflinge und
Protokolle des Vorbesitzers **bereits verloren**, und zwar lange bevor dieses
Projekt begann.

### Beantwortet (2026-08-14): Der Datenbestand ist erhalten

Über `Messroutine → Datenbank → über Suchen` (`MENUEBAUM.md`, `[S13]`) zeigt
sich ein **gefüllter Prüflingsbestand** — `Gerätenr:112`, mit `↑`/`↓`
durchblätterbar.

**Der Messdatenspeicher hing also nicht an dieser Batterie.** Er ist
nichtflüchtig, so wie Betreibertext und Gerätenummer, die den Spannungsverlust
ebenfalls überstanden haben. Verloren ist allein die **Uhr**.

**Folgen:**

- Der Bestand ist beim späteren Batteriewechsel **nicht gefährdet.**
- Die Daten des Vorbesitzers sind auswertbar — mit dem Vorbehalt, dass
  **Datumsangaben unzuverlässig** sind, weil die Uhr über einen unbekannten
  Zeitraum falsch lief. Aussagekräftig bleibt die **Reihenfolge**.
- Damit entfällt der Grund, vor dem Batteriewechsel den Speicher zu retten.

⚠️ Unverändert gilt: Es ist die einzige Kopie. Keine Lösch- oder
Rücksetzfunktion bestätigen.

<details><summary>Ursprüngliche Fragestellung, vor der Klärung</summary>

- [x] Im Menü die **Prüflings- und Protokollverwaltung** aufrufen
      (`MENUEBAUM.md`, `[S02]`)

| Ergebnis | Schluss |
|---|---|
| **Daten sind vorhanden** | Der Speicher hängt **nicht** an dieser Batterie — er ist nichtflüchtig (EEPROM, NVRAM mit eigener Zelle, batteriegepuffertes RAM mit zweiter Quelle). Gute Nachricht: die Daten sind sicher, und der Zellenwechsel gefährdet sie nicht. |
| **Speicher ist leer** | Entweder mit der Batterie verloren, oder vom Vorbesitzer gelöscht. Beides nicht mehr zu unterscheiden — und nichts mehr zu retten. |

Auch der **Betreibertext** und die **Gerätenummer** überstehen offenbar den
Spannungsverlust: beide erscheinen weiterhin (Startbildschirm bzw.
Selbsttest-Ausdruck), obwohl die Uhr längst steht. **Das ist bereits ein
Beleg**, dass zumindest die Geräteeinstellungen nichtflüchtig abgelegt sind —
also nicht in demselben gepufferten RAM wie die Uhr.

Damit ist Folge 2 schon halb beantwortet und die Aussicht gut, dass auch die
Prüfdaten liegen geblieben sind.

</details>

## Entscheidung (2026-08-14): zurückgestellt

**Die Reinigung erfolgt später, zusammen mit dem Öffnen des Geräts.**

Begründung: Die Korrosion besteht **seit Jahren** — das Gerät hat sie
offensichtlich lange überlebt und funktioniert vollständig, einschließlich
Selbsttest und Drucker. Ein akuter, frischer Schaden liegt also nicht vor,
sondern ein alter, weitgehend zum Stillstand gekommener. Damit entfällt der
Grund, dafür die zerstörungsfreie Außenaufnahme zu unterbrechen.

Die Argumente dagegen bleiben hier stehen, weil sie beim späteren Öffnen
wieder gelten:

> Ausgelaufener Elektrolyt **arbeitet weiter.** Er kriecht an Kontaktfedern,
> Litzen und Leiterbahnen entlang, zieht Feuchtigkeit aus der Luft und frisst
> sich in Zuleitungen hinein. Was im Fach sichtbar ist, ist oft der kleinere
> Teil des Schadens.

**Das Fach ist leer** (2026-08-14) — es liegt keine Zelle mehr darin. Damit
gibt es keine aktive Quelle mehr, der Zustand ist statisch. Die Zurückstellung
ist dadurch zusätzlich abgesichert.

Nebenbefund zur Herkunft: Jemand hat die ausgelaufenen Zellen **entfernt, aber
nicht gereinigt.** Der Schaden wurde also bemerkt und nur halb behandelt — das
Gerät lief danach weiter, ohne Uhr.

## Bestückung: 2 × AA, 1,5 V (2026-08-14)

Das Fach nimmt **zwei handelsübliche AA-Rundzellen zu je 1,5 V** auf,
zusammen **3 V**.

Damit ist die Frage „Akku oder Batterie?" praktisch beantwortet:

- **1,5 V ist die Nennspannung einer Primärzelle.** Ein NiCd-Akku hätte 1,2 V,
  und ein gepufferter Akkuverbund wäre bei diesem Gerätealter fast immer
  **verlötet** statt in ein Fach mit Federkontakten gelegt.
- **3 V ist genau der Wert, den eine CMOS-Echtzeituhr mit ihrem
  Stützspeicher braucht.** Die Bestückung passt zum Zweck.
- Ein von außen zugängliches Fach für Standardzellen ist eine
  **Verbrauchsmaterial-Lösung** — vom Hersteller zum regelmäßigen Wechseln
  vorgesehen, nicht zum Laden.

**Bauform und Beschriftung des Fachs stimmen damit überein** (2026-08-14) —
das Fach ist als das ausgewiesen, was es ist.

**Endgültig geklärt wird die Frage beim Öffnen** (Entscheidung 2026-08-14):
Ob hinter den Kontakten doch eine Ladeschaltung sitzt, ist an der Leiterplatte
in einem Blick zu sehen — Diode und Vorwiderstand zur Versorgung, oder eben
nichts dergleichen. Bis dahin gilt die Bestückung als **2 × AA Primärzelle,
3 V, Stützversorgung der Echtzeituhr**, und es wird keine Zelle eingelegt.

### Und damit ist auch der Schaden erklärt

**Ausgelaufene Alkali-AA-Zellen** sind der mit Abstand häufigste Grund für
grün-blaue Korrosion in genau solchen Fächern. Nach Jahrzehnten im Gerät ist
das kein Defekt, sondern der Normalfall. Der Befund fügt sich damit
vollständig: Alkalizellen ausgelaufen → jemand hat sie entfernt → Kontakte
blieben ungereinigt → Uhr steht seitdem.

### Empfehlung für den Ersatz

**Lithium-AA-Zellen (Li-FeS₂, 1,5 V)** statt Alkali. Sie sind in genau diesem
Anwendungsfall überlegen:

- Sie **laufen praktisch nicht aus** — das ist der eigentliche Punkt, denn
  genau daran hat dieses Gerät schon einmal Schaden genommen.
- Haltbarkeit von 15–20 Jahren, bei der geringen Stromaufnahme einer
  gepufferten Uhr die realistische Standzeit.
- Gleiche Bauform, gleiche 1,5 V — kein Eingriff nötig.

Wenn es doch Alkali sein soll: nur frische Markenzellen, und **einen Termin
zum Wechseln notieren**. Bei einem Gerät, das jahrelang unbenutzt im Regal
steht, ist die nächste Sauerei sonst vorprogrammiert.

Unabhängig vom Zelltyp: **bei längerer Lagerung die Zellen herausnehmen.**
Das Gerät verliert dabei nur Uhrzeit und Datum.

Alles Weitere — Reinigen, Neutralisieren, Kontakte prüfen, Ersatz — beim
Öffnen.

## Reihenfolge: erst feststellen, dann reinigen, dann ersetzen

### 1. Aufnehmen, bevor etwas angefasst wird

- [ ] Fach **fotografieren**, so wie es ist → `../bilder/`
- [ ] **Ist noch eine Zelle drin?** Wenn ja: Aufdruck vollständig notieren —
      Hersteller, Typ, Bauform, Spannung, Datumscode
- [ ] **Bauform und Anzahl**: Rundzelle (AA/AAA/Mignon), 9-V-Block,
      Knopfzelle, gelöteter Zellenverbund?
- [ ] **Beschriftung am Fach**: Bender gibt dort oft Typ und Polarität an
- [ ] Gehen von den Kontakten **Litzen ins Geräteinnere**, oder sitzt das Fach
      direkt auf einer Leiterplatte? Litzen sind die bessere Nachricht — dann
      ist der Schaden räumlich begrenzt
- [ ] **Kriechspuren** verfolgen, so weit von außen einsehbar: Verfärbungen an
      den Litzen, Salzausblühungen, brüchige Isolation

### 2. Die Frage, die vor dem Ersetzen zu klären ist

**Wiederaufladbar oder nicht?** Geräte dieser Bauart und Zeit puffern die Uhr
oft mit einem **NiCd-Zellenverbund, den das Gerät im Betrieb nachlädt.**
NiCd-Pufferzellen sind berüchtigt dafür, nach Jahrzehnten auszulaufen — was
zum Befund passt.

⚠️ **Steckt eine Ladeschaltung dahinter und man legt eine normale
Alkali-Batterie ein, wird diese geladen.** Das führt zu Gasbildung, Auslaufen
und im schlechtesten Fall zum Bersten. Umgekehrt ist ein Akku dort, wo eine
Lithium-Primärzelle vorgesehen war, nur nutzlos.

Anhaltspunkte:

| Hinweis | Deutung |
|---|---|
| Aufdruck des Fachs nennt „Akku", „NiCd", „rechargeable" | Ladeschaltung vorhanden |
| Zellen **fest verbunden/verlötet** statt einzeln entnehmbar | spricht für Akku |
| Reste einer **Lithium-Knopfzelle** (CR20xx) | Primärzelle, keine Ladung |
| Fach für handelsübliche Rundzellen mit Federkontakten | eher Primärzelle |

- [ ] Bevor eine neue Zelle eingelegt wird: **Spannung an den Kontakten messen,
      Gerät eingeschaltet.** Liegt dort eine Ladespannung an, ist die Frage
      beantwortet.
- [ ] Im Zweifel **leer lassen.** Ohne Pufferung verliert das Gerät nur Uhrzeit
      und möglicherweise den Speicher — es geht nichts kaputt. Eine falsch
      gewählte Zelle richtet Schaden an.

### 3. Reinigen

Ausgelaufener Elektrolyt aus Alkali- wie aus NiCd-Zellen ist **Kalilauge —
stark ätzend.** Handschuhe und Augenschutz, und die abgekratzten Rückstände
gehören in den Abfall, nicht in die Umwelt.

Vorgehen:

1. **Netzstecker ziehen.** Gerät stromlos, nicht nur ausgeschaltet.
2. Groben Belag **trocken** entfernen — Glasfaserstift, Messingbürste,
   Holzstäbchen. Nicht in Richtung Geräteinneres arbeiten.
3. Rest **neutralisieren**: Kalilauge ist basisch, also mit einer milden Säure
   angehen — Haushaltsessig oder Zitronensäurelösung, **sparsam** mit
   Wattestäbchen aufgetragen, nicht gegossen. Es darf nichts ins Gerät laufen.
4. Mit wenig **destilliertem Wasser** nachwischen, dann mit **Isopropanol**,
   dann **vollständig trocknen lassen**.
5. Kontakte auf **Substanz** prüfen: Ist die Vernickelung durch und das
   Grundmaterial angefressen, hilft Putzen nur optisch — dann muss die
   Kontaktfeder ersetzt oder überbrückt werden.
6. Nach dem Trocknen **Durchgang der Kontakte zum Gerät messen.**

**Nicht** mit Schleifpapier grob abtragen (nimmt die Beschichtung mit) und
**nicht** großzügig fluten.

### 4. Danach

- [ ] Zustand nach der Reinigung fotografieren
- [ ] Passende Zelle beschaffen — erst nach Klärung von Punkt 2
- [ ] Uhrzeit und Datum neu stellen, sofern das Menü es zulässt
- [ ] Selbsttest wiederholen und den neuen Ausdruck mit dem alten vergleichen

## Offene Fragen

- Versorgt diese Batterie nur die Uhr, oder auch den **Datenspeicher**? Wenn
  auch den Speicher, ist jeder Zellenwechsel heikel — dann können die Daten
  des Vorbesitzers dabei verlorengehen (`FUNKTIONSAUFNAHME.md`, Abschnitt D).
  **Im Zweifel den Speicher vorher auslesen und ausdrucken.**
- Gibt es im Gerät eine **zweite**, interne Pufferzelle? Ein von außen
  zugängliches Fach schließt das nicht aus.
- Meldet das Gerät eine leere Batterie von sich aus — beim Einschalten oder im
  Selbsttest?
