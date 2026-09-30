# Bender µP601 — Funktionsaufnahme eines intakten Sicherheitstesters

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
