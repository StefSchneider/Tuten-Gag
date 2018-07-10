## Regeln für Tausch
- Es werden immer Wortbestandteile getauscht, diese können aus einzelnen oder mehreren Buchstaben bestehen.
- Ein Wortbestandteil besteht aus mehreren Buchstaben der gleichen Art, z.B. Vokale ("A", "au") oder Konsonanten ("Kl", "Schn")
- Wortbestandteile, die mit Vokalen oder Umlauten beginnen, dürfen nur gegen Wortbestandteile, die entweder Vokale oder Umlaute enthalten, getauscht werden.
- Wortbestandteile, die mit starken Konsonanten beginnen, dürfen nur gegen solche Wortbestandteile getauscht werden.
- Wortbestandteile, die mit schwachen Konsonanten beginnen, sind vom Tausch ausgeschlossen.
- Artikel - bestimmt oder unbestimmt - dürfen nicht für einen Tausch herangezoegen werden, z.B. "das", "einer"
- Satzzeichen dürfen nicht für einen Tausch herangezogen werden.
- Es darf maximal innerhalb von vier Woertern getauscht werden, Satzzeichen oder Artikel werden bei der Spanne nicht gezaehlt.
- Es dürfen auch Wortbestandteile - nach den oben aufgeführten Regeln - innerhalb des Wortes getauscht werden.
- Werden Wortbestandteile innerhalb eines Wortes getauscht, gilt dieser Tausch auch für dieselben Woerter im weiteren Text.
- Wird innerhalb eines Wortes ein Bindestrich verwendetn, werden die beiden Woerter getrennt behandelt und bevorzugt getauscht.
- Woerter, die vor dem Tausch der Wortbestandteile gross geschrieben werden, werden auch nach dem Tausch der Bestandteile gross geschrieben.
- Es dürfen auch Wortbestandteile, die mit einen Grossbuchstaben beginnen, mit Worbestandteilen, die mit einem Kleinbuchsaben beginnen, getauscht werden.
- Zwischen zwei Wörtern oder dem Satzzeichen "-" steht immer nur ein Leerzeichen. Überflüssige Leerzeichen werden gelöscht.
- Ein Wort, das bereits zu einem Tausch der Wortbestandteile herangezogen wurde, ist von weiteren Tauschopartionen ausgeschlossen.
- Es wird nur innerhalb eines Satzes getauscht.


## Regeln für Rating
- Für jede Kombination werden Grundpunkte und ein Zusatzfaktor vergeben.
- Es wird der Gesamttausch, d.h. die beiden betroffenen Woerter bewertet, Ausnahme: Es werden Buchtaben innerhalb eines Wortes getauscht.
- Neu kombinierte Woerter, die in einem Woerterbuch vorkommen, erhalten eine hoehere Punktzahl.
- Neu kombinierte Woerter, die von vorherigen Nutzern als gut gekennzeichnet wurden, erhalten eine hoehere Punktzahl.
- Je naeher die beiden neu kombinierten Woerter zusammenstehen, umso hoeher ist die Punktzahl, auch bei einem Tausch der Wortbestandteile innerhalb eines Wortes gibt es Punkte.
- Je mehr Buchstaben die beiden Wortbestandteile (Summe) bei einem Tausch haben, umso hoeher ist die Punktzahl.
- Tauschoperationen innerhalb eines gekoppelten Wortes erhalten sollen bevorzugt getauscht werden und erhalten eine hohe Punktzahl.


## Toolboxen
- AVLTree (TB_AVLTree.py)


## Config-Daten
- benötigte Dateipfade
- Zuordnung der Satzbestandteile, z.B. Woerter, Satzzeichen, Artikel
- Zuordnung der Wortbestandteile, z.B. Vokale, Konsonanten_stark
- Zuordnung, welche Satzbestandteile nicht getauscht werden dürfen
- Punkteskala und Faktoren fuer Rating


## Hauptprogramm (Program Tuten Gag)
- Import Module
- Import verwendete Python-Bibliotheken
- Import Toolboxen
- Start
- Ende


## Architektur Module


### Modul Config (M_Config.py)

#### Funktionen
- Config-Daten aus Datei einlesen
- Config-Daten verarbeiten


### Modul Woerterbuecher (M_Dictionaries.py)

#### Funktionen
- Woerterbuecher auslesen
- Woerter aus Woerterbuechern in AVL-Baum schreiben
- Wort in Woerterbuch einfügen
- Wort in Woerterbuch suchen


### Modul Menu/Steuerung (M_Menu.py)

#### Funktionen
- Menueaufbau
- Menueanzeige
- Steuerung der Programmteile nach Benutzerauswahl


### Modul Eingabe (M_Input.py)

#### Funktionen
- Eingabefeld auslesen
- ueberpruefen, ob Woerter in den Woerterbuechern vorhanden sind
- Satz auf Richtigkeit ueberpruefen


### Modul Zerlegen (M_Split.py)

#### Funktionen
- überschuessige Leerzeichen entfernen
- Satz in Satzbestandteile aufsplitten
- Satzbestandteile in Baum haengen
- Woerter in Wortbestandteile aufsplitten
- Wortbestandteile in Baum haengen
- Wortbestandteile in Kleinbuchstaben umwandeln


### Modul Analysieren (M_Analyze.py)

#### Funktionen
- bestimmen, ob Wortaenderung moeglich ist
- Gross- und Kleinschreibung bestimmen
- bestimmen, mit welchem Wortbestandteil das Wort anfaengt


### Modul Kombinationen (M_Combine.py)

#### Funktionen
- ueberpruefen, welche Woerter sich kombinieren lassen
- Wortbestandteile verschiedener Woerter miteinander kombinieren


### Modul Künstliche Intelligenz (M_AI.py)

#### Funktionen
- Benutzer über die beste Kombination eines Satzes entscheiden lassen
- beste Kombination in eigene Datei schreiben
- Regeln für gelungene Kombinationen entwickeln und in Rating einfließen lassen


### Modul Rating (M_Rating.py)

#### Funktionen
- Bewertung der Wortbestandteil-Kombinationen
- Vergabe von Punkten für Kombinationen
- Sortierung der Kombinationen nach Punkten

#### Zugriff auf Module
- Woerterbuch: Abgleich mit echten Woertern, falls vorhanden Punktzuschlag
- KI: Abgleich mit als gut bewerteten Wortbestandteil-Kombinationen, falls vorhanden Punktezuschlag


### Modul Zusammensetzen (M_Build.py)

#### Funktionen
- Einzelne Woerter mit der neuen Wortbestandteile-Kombination in finalen Satz aufnehmen
- Grossschreibung wieder aufnehmen

### Modul Ausgabe (M_Output.py)

#### Funktionen
- Ausgabegerät steuern
- Finalen Satz ausgeben
