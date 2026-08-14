# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Worum es geht

Analyse und Dokumentation eines gebraucht erworbenen **Bender Model 601**.
Das ist kein Software-, sondern ein **Hardware-Archäologie-Repository**: das
Ergebnis sind Markdown-Dokumente unter `research/`, nicht ein Programm.
Code entsteht nur dort, wo er Unterlagen erschließt (`tools/`).

**Projektsprache ist Deutsch.** Dokumente, Commit-Meldungen und Kommentare
werden auf Deutsch geschrieben.

### Das Gerät

**Bender µP601**, Gerätebeschriftung `Bender µP 601-1`, Typnummer `B928161`.
Einphasiger Sicherheitstester für Prüfungen nach **IEC 60601-1** (medizinische
elektrische Geräte), Hersteller Bender GmbH & Co. KG, Grünberg.

Belegt ist das bislang nur über das Datenblatt des Zubehörs DS601 — siehe
`research/STAND.md`. Ein Handbuch des µP601 ist öffentlich nicht auffindbar.
Der Ordner `docs/` enthält daher zunächst fast nichts; **das Gerät selbst ist
die Hauptquelle.**

Der µP601 gehört **nicht** zur UNIMET-Reihe, sondern steht daneben. Befunde aus
dem UNIMET-Umfeld nicht übertragen, ohne sie hier neu zu belegen.

Das Gerät wirkt äußerlich **intakt**. Das bestimmt die Vorgehensweise (siehe
unten) und unterscheidet dieses Projekt vom Vorgänger.

## Vorgängerprojekt

`C:\Users\LattePanda\Bender-Unimet-1000ST` (GitHub: `feiglein74/bender-unimet-1000st`)
— dasselbe Vorgehen an einem defekten Bender UNIMET 1000 ST, abgeschlossen
2026-07-31.

**Als technische Referenz nur mit Vorsicht.** Die dortigen Befunde gelten für
ein anderes Gerät, das zusätzlich vor dem Verkauf umgebaut worden war. Nichts
davon auf das 601 übertragen, ohne es hier neu zu belegen.

**Als Muster für Struktur und Arbeitsweise brauchbar** — daher stammen die
Konventionen unten. Lesenswert dort: `research/STAND.md` (Aufbau eines
chronologisch geschichteten Arbeitsstands) und `tools/parse_interface.py`
(PDF-Tabellen in eine Referenz überführen).

## Vorgehen bei einem intakten Gerät

Der Vorgänger scheiterte nicht am Fehler, sondern daran, dass Firmware und
Anwendungssoftware **nirgends mehr beschaffbar** waren. Daraus folgt hier die
oberste Regel:

> **Erst sichern und dokumentieren, dann eingreifen.**
> Jeder funktionierende Zustand ist ein Original, das es nur einmal gibt.

Konkret, in dieser Reihenfolge:

1. **Auslieferungszustand aufnehmen** — Typenschild, Aufkleber, Seriennummer,
   Zubehör, Kabel, alles fotografieren, bevor irgendetwas geöffnet wird.
2. **Betriebszustand aufnehmen** — Bootverlauf, Versionsanzeigen, Menübaum,
   gespeicherte Daten des Vorbesitzers.
3. **Datenträger sichern**, bevor am Gerät konfiguriert wird.
4. **Erst danach** öffnen, messen, verändern.

Keine schreibenden Eingriffe (Konfiguration zurücksetzen, formatieren,
Firmware-Update) ohne vorherige Sicherung und ohne Rückfrage.

## Sicherheit

Bender-Prüfgeräte für elektrische Sicherheit schalten **Netzspannung auf
Prüfkreise** und erzeugen für die Isolationsprüfung **Hochspannung**
(beim 1000 ST 500 V DC). Vor dem Öffnen Netzstecker ziehen, danach
Restspannungen prüfen. Diese Warnung bleibt gültig, bis am konkreten Gerät
belegt ist, dass sie nicht zutrifft.

## Ordnerlogik

| Ordner | Inhalt | im Repo? |
|---|---|---|
| `research/` | **eigene Analysen** — das eigentliche Ergebnis | ja |
| `research/text/` | Volltext aus PDFs (`pdftotext`) | nein |
| `docs/` | Herstellerunterlagen (PDF), nach Hersteller unterteilt | nein |
| `bilder/` | eigene Fotos; extrahierte Handbuchabbildungen in Unterordnern | eigene ja |
| `software/` | fremde Binärdateien, Treiber, Archivfunde | nein |
| `firmware/` | Dumps aus dem Gerät | nein |
| `tools/` | eigene Python-Skripte zur Auswertung | ja |

**Die Trennlinie ist das Urheberrecht.** Herstellerunterlagen und alles daraus
Abgeleitete (Volltext, extrahierte Abbildungen) sowie fremde Binärdateien
bleiben lokal und stehen in `.gitignore`. Ihre Bezugsquellen gehören nach
`QUELLEN.md`, damit die Analysen ohne die Dateien nachvollziehbar bleiben.
Eigene Fotos und eigene Analysen werden veröffentlicht.

Wird ein Dokument geladen, gehört im selben Zug ein Eintrag in `QUELLEN.md`
(Datei ist noch nicht angelegt — beim ersten Download erzeugen, Aufbau siehe
Vorgängerprojekt).

## Werkzeuge

Es gibt kein Build- oder Testsystem. Die wiederkehrenden Arbeitsschritte:

```bash
# PDF in durchsuchbaren Text (Spaltenlayout erhalten)
pdftotext -layout docs/<hersteller>/<datei>.pdf research/text/<name>.txt

# Tabellen: -raw statt -layout, sonst verschieben sich die Spalten
pdftotext -f <von> -l <bis> -raw -enc UTF-8 docs/.../<datei>.pdf -

# Abbildungen aus einem Handbuch extrahieren
pdfimages -list docs/.../<datei>.pdf              # erst sichten
pdfimages -all -p docs/.../<datei>.pdf bilder/<name>/<praefix>

# Auswerteskript ausführen (erzeugt sein Zieldokument neu)
python tools/<skript>.py
```

Skripte in `tools/` sind eigenständig, ohne Argumente aufrufbar und
idempotent: sie lesen aus `docs/`, schreiben genau ein Dokument nach
`research/` und leiten Pfade aus `Path(__file__).parent.parent` ab. Der
Docstring nennt Quelle, Aufruf und Ergebnisdatei.

Poppler (`pdftotext`, `pdfimages`) kam im Vorgängerprojekt über `scoop`.

## Wie Dokumente geschrieben werden

- **`research/STAND.md` ist der Einstiegspunkt.** Chronologisch geschichtet:
  neue Befunde hinten anfügen, die abschließende Deutung als Kasten oben.
- **Widerlegte Annahmen nicht löschen**, sondern als Nachtrag markieren. Die
  Irrwege sind Teil des Ergebnisses und verhindern, dass sie jemand wiederholt.
- **Beobachtung und Deutung trennen.** Was am Gerät abgelesen wurde, steht
  getrennt von dem, was daraus geschlossen wird. Wo mehrere Deutungen
  plausibel sind, alle nennen und den Test angeben, der entscheidet.
- **Bauteile mit vollem Aufdruck** notieren (Typ, Datumscode, Revision) — die
  Recherche hängt oft an einer einzelnen Zeichenfolge.
- Datumsangaben absolut (`2026-08-14`), keine relativen.
- Tabellen für Bauteillisten, Anschlüsse, Quellen; Fließtext für Befunde.

## Git

Commit-Meldungen auf Deutsch, ohne Umlaute (Konvention des Vorgängerprojekts:
`Bender UNIMET 1000 ST — Analyse eines unvollstaendigen Geraets`).
Vor dem ersten Push prüfen, dass `.gitignore` greift — `docs/`, `software/`,
`firmware/` und die extrahierten Texte dürfen nicht mitgehen.
