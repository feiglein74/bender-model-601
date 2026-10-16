# Bender µP601 — documenting a working medical safety tester

![License: CC BY-SA 4.0](https://img.shields.io/badge/license-CC%20BY--SA%204.0-lightgrey)
![Device](https://img.shields.io/badge/device-Bender%20%C2%B5P601-005B96)
![Interface](https://img.shields.io/badge/interface-RS--232%20%404800%20baud-555)

Field notes on a **Bender µP601 safety tester** (front panel: *BENDER Medical
Division — µP SAFETY TESTER Model 601*, rating plate `µP 601-1`, part number
`B928161`, variant `IVM 429 D`): a single-phase electrical safety tester for
medical devices according to **IEC 601-1:1988** and **DIN VDE 0751-1:1990**,
built 1993 or later. Portable case, keyboard in the lid, built-in 24-column
dot-matrix printer, RS-232 on the back. Not part of the UNIMET range.

No manual, datasheet or service documentation for this device could be found
online — everything here was worked out **from the outside, on a running unit**.

<img src="bilder/selbsttest_ausdruck_20260815.jpg" alt="Self-test printout of the Bender µP601: IVM429 D, operator text, Selbsttest bestanden, Ger.Nr. 600521" width="320">

What the built-in printer produces after the power-on self-test (verbatim,
24 columns; the operator text is a field programmed by the previous owner):

```
             IVM429 D
MACK
Medizin-Technik GmbH
90482 Nürnberg
- - - - - - - - - - - -
Selbsttest bestanden
- - - - - - - - - - - -
Zeit   :    00:37:27
Datum  :    02/10/3?
Nennspannung:   230 V
Ger.Nr.:      600521
Prüfer:
```

> Detailed documentation is in German. Manufacturer documents and the photos
> from the sales listing are **not** included (copyright) — see
> [`QUELLEN.md`](QUELLEN.md).

## Summary (English)

**Status: work in progress. The unit works and has not been opened.**

- **Identification:** the only public trace of the µP601 is the datasheet of
  Bender's three-phase adapter **DS601** (BP 609002 / 09.2006), which names it
  next to the UNIMET 1000/1100 ST. "601" refers to the standard IEC 601-1.
  The postal code on the rating plate dates the unit to **July 1993 or later**.
- **Power-on:** the tester detects which pin of its own (reversible) Schuko
  plug carries the phase and asks you to switch off and turn the plug if it
  is the wrong way round.
- **Menu tree:** two operating modes, **IEC 601-1:1988** and
  **DIN VDE 0751T1/90**, mapped screen by screen down to the protection class
  selection; language switch German/English.
- **Stored data:** about **69 test records** of the previous owner, a
  medical equipment dealer in Nuremberg, survived in non-volatile memory.
  Only the real-time clock was lost (leaked 2 × AA cells, corroded contacts).
- **Printer:** Datamega **DPN-240-24-S105** panel printer, ribbon
  **DPN-290-SW** (equivalent to Epson **ERC-21**). It is a bare mechanism
  driven directly by the main board. The disintegrated ribbon drive roller
  was repaired.
- **RS-232:** DB-25 on the rear, labelled `V.24/RS-232C`, `BAUD 4800`.
  Whether it sends the printout on its own is the next thing to find out
  (plan in [`research/AUSLESEN.md`](research/AUSLESEN.md)).

**Do you have a manual, interface description or service documents for the
Bender µP601 / µP 601-1?** Please open an issue — it would help a lot.

| Document (German) | Content |
|---|---|
| [`research/STAND.md`](research/STAND.md) | **start here** — status, identification, history |
| [`research/FUNKTIONSAUFNAHME.md`](research/FUNKTIONSAUFNAHME.md) | front panel, rear panel, rating plate, power-on, printer |
| [`research/MENUEBAUM.md`](research/MENUEBAUM.md) | menu tree screen by screen, self-test printout |
| [`research/BATTERIE.md`](research/BATTERIE.md) | battery compartment corrosion, clock without backup |
| [`research/AUSLESEN.md`](research/AUSLESEN.md) | draft: capturing test reports via RS-232 |

Related: [Bender UNIMET 1000 ST — teardown & reverse engineering](https://github.com/feiglein74/bender-unimet-1000st)
(a different, PC-based Bender tester — findings do not carry over).

---

## Deutsch — Funktionsaufnahme eines intakten Sicherheitstesters

Dokumentation eines gebraucht erworbenen **Bender µP601** (Frontplatte:
`BENDER Medical Division — µP SAFETY TESTER Model 601`, Typenschild
`µP 601-1`, Typnummer `B928161`). Einphasiges Prüfgerät für die elektrische
Sicherheit medizinischer Geräte nach **IEC 601-1**, Baujahr frühestens 1993,
tragbarer Koffer mit Tastatur im Deckel und eingebautem Protokolldrucker.

Ein Handbuch ist öffentlich nicht auffindbar. **Das Gerät selbst ist die
Hauptquelle** — alles hier ist von außen am laufenden Gerät erschlossen.

## Status: in Arbeit

Das Gerät **läuft einwandfrei**. Ziel ist daher keine Reparatur, sondern den
Funktionsumfang vollständig zu erfassen, bevor irgendetwas geöffnet wird:

> **Erst sichern und dokumentieren, dann eingreifen.**

Bisher erledigt: Identifikation und Datierung, Herkunft (Betreiber MACK
Medizin-Technik GmbH, Nürnberg), Startvorgang mit Phasenerkennung, Menübaum
der IEC- und VDE-Zweige, Instandsetzung des Farbbandtransports am Druckwerk.
Geplant: Protokolle über die RS-232 der Rückwand digital mitlesen.

Vorgängerprojekt mit demselben Vorgehen an einem defekten Gerät:
<https://github.com/feiglein74/bender-unimet-1000st>

## Wo was steht

| Datei | Inhalt |
|---|---|
| **`research/STAND.md`** | **Arbeitsstand, Identifikation, Herkunft. Hier einsteigen.** |
| `research/FUNKTIONSAUFNAHME.md` | Frontplatte, Rückwand, Typenschild, Messfunktionen, Druckwerk |
| `research/MENUEBAUM.md` | Menüstruktur, Bildschirm für Bildschirm, Selbsttest-Ausdruck |
| `research/BATTERIE.md` | Korrosion im Batteriefach, Uhr ohne Pufferung |
| `research/AUSLESEN.md` | Entwurf: Protokolle per RS-232 digital erfassen |
| `QUELLEN.md` | Bezugsquellen der Herstellerunterlagen |
| `bilder/` | eigene Fotos |

Herstellerunterlagen, daraus extrahierte Texte und die Fotos der
Verkaufsanzeige sind aus Urheberrechtsgründen nicht enthalten
(`.gitignore`, `LICENSE.md`).

## Sicherheit

Das Gerät schaltet Netzspannung auf Prüfkreise und erzeugt für die
Isolationsprüfung Gleichspannung im Bereich mehrerer hundert Volt. Vor dem
Öffnen Netzstecker ziehen und Restspannungen prüfen.
