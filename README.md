# Tuten-Gag
This repository will shake letters in a sentence in a humorful way, f.e. "Ich kacke meinen Poffer."


## Regeln für Tausch
- Es werden immer Wortbestandteile getauscht.
- Ein Wortbestandteil besteht aus mehreren Buchstaben der gleichen Art, z.B. Vokale ("A", "au") oder Konsonanten ("Kl", "Schn")
- Wortbestandteile, die mit Vokalen oder Umlauten beginnen, dürfen nur gegen solche Wortbestandteile getauscht werden.
- Wortbestandteile, die mit starken Konsonanten beginnen, dürfen nur gegen solche Wortbestandteile getauscht werden.
- Wortbestandteile, die mit schwachen Konsonanten beginnen, sind vom Tausch ausgeschlossen.
- Artikel - bestimmt oder unbestimmt - dürfen nicht für einen Tausch herangezoegen werden, z.B. "das", "einer"
- Satzzeichen dürfen nicht für einen Tausch herangezogen werden.
- Es darf maximal innerhalb von vier Woertern getauscht werden, Satzzeichen werden bei der Spanne nicht gezaehlt.




## Toolboxen
- AVLTree


## Config-Daten
- benötigte Dateipfade
- Zuordnung der Satzbestandteile, z.B. Woerter, Satzzeichen, Artikel
- Zuordnung der Wortbestandteile, z.B. Vokale, Konsonanten_stark
- Zuordnung, welche Satzbestandteile nicht getauscht werden dürfen
- Punkteskala fuer Rating


## Hauptprogramm
- Import Module
- Import verwendete Python-Bibliotheken
- Import Toolboxen
- Start
- Ende


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


### Modul Zerlegen

#### Funktionen
- überschuessige Leerzeichen entfernen
- Satz in Satzbestandteile aufsplitten
- Satzbestandteile in Baum haengen
- Woerter in Wortbestandteile aufsplitten
- Wortbestandteile in Baum haengen


### Modul Analysieren

#### Funktionen
- bestimmen, ob Wortaenderung moeglich ist
- Gross- und Kleinschreibung bestimmen
- bestimmen, mit welchem Wortbestandteil das Wort anfaengt


### Modul Kombinationen

#### Funktionen
- ueberpruefen, welche Woerter sich kombinieren lassen
- Wortbestandteile verschiedener Woerter miteinander kombinieren


### Modul KI

#### Funktionen
- Benutzer über die beste Kombination eines Satzes entscheiden lassen
- beste Kombination in eigene Datei schreiben
- Regeln für gelungene Kombinationen entwickeln und in Rating einfließen lassen


### Modul Rating

#### Funktionen
- Bewertung der Wortbestandteil-Kombinationen
- Vergabe von Punkten für Kombinationen
- Sortierung der Kombinationen nach Punkten

#### Zugriff auf Module
- Woerterbuch: Abgleich mit echten Woertern, falls vorhanden Punktzuschlag
- KI: Abgleich mit als gut bewerteten Wortbestandteil-Kombinationen, falls vorhanden Punktezuschlag


### Modul Ausgabe

#### Funktionen
- Ausgabegerät steuern
- Finalen Satz ausgeben

