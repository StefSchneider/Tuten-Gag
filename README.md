# Tuten-Gag
This repository will shake letters in a sentence in a humorful way, f.e. "Ich kacke meinen Poffer."


## Toolboxen
- AVLTree


## Config-Daten
- benötigte Dateipfade
- Zuordnung der Satzbestandteile, z.B. Woerter, Satzzeichen, Artikel
- Zuordnung der Wortbestandteile, z.B. Vokale, Konsonanten_stark
- Zuordnung, welche Satzbestandteile nicht getauscht werden dürfen


## Architektur Module


### Modul Config

#### Funktionen
- Config-Daten aus Datei einlesen
- Config-Daten verarbeiten


### Modul Woerterbuecher

#### Funktionen
- Woerterbuecher auslesen
- Woerter aus Woerterbuechern in AVL-Baum schreiben
- Wort in Woerterbuch einfügen
- Wort in Woerterbuch suchen


### Modul Menu/Steuerung

#### Funktionen
- Menueaufbau
- Menueanzeige
- Steuerung der Programmteile nach Benutzerauswahl


### Modul Eingabe

#### Funktionen
- Eingabefeld auslesen
- ueberpruefen, ob Woerter in den Woerterbuechern vorhanden sind
- Satz auf Richtigkeit ueberpruefen



### Modul Kuenstliche Intelligenz

#### Funktionen
- Benutzer über die beste Kombination eines Satzes entscheiden lassen
- beste Kombination in eigene Datei schreiben
- Regeln für gelungene Kombinationen entwickeln und in Rating einfließen lassen
