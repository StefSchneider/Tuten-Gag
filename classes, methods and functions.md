## Klassen

### Text (Datenstruktur Baum)

#### Methoden
- create_node: Erzeugt einen neuen Kindenknoten für einen Satz.

### Dictionary

#### Methoden
- load: Lädt ein Woerterbuch aus einer Datei in den Woerterbuch-Baum.
- save: Speichert einen Woerterbuch-Baum in einer Woertrebuch-Datei ab.
- check_size: Ermittelt die Groesse (= Anzahl der Eintraege) der Woerterbuch-Datei.
- check_status: Ermittelt, wie viel Prozent der Woerterbuch-Datei bereits in den Woerterbuch-Baum übertragen wurden.

### Sentence

#### Methoden
- create_node: Erzeugt einen neuen Kinderknoten für einen Satzbestandteil.
- xxx

### Word
- xxx
- xxx


## Funkionen

### split_text
Teilt den Gesamttext in Sätze auf. Aufteilung nach '.', '!' oder '?'
#### Regeln
Der Text wird Buchstabe für Buchstabe überprüft.
Es werden zwei Marker benötigt, einer für den Satzanfang und einer für das Satzende.
Wird eines der genannten Satzzeichen gefunden, wird der String bis zu dieser Stelle in einen neuen Satz kopiert. Dabei werden überflüssige Leerzeichen am Satzanfang und Satzende abgeschnitten. Der neue Satz wird als String in einen Baum gehangen. Der Marker für den Satzanfang wird auf die neue Textstelle (Satzzeichen + 1) verschoben. Anschließend geht die Überprüfung an der Stelle weiter.
Die Marker für Satzanfang (SentenceStart) und Satzende (SentenceEnd) sind Variablen, die nur in der Funktion benötigt werden.

### split_sentence
Teilt den jeweiligen Satz in Satzbestandteile (Woerter, Satzzeichen etc.) auf
### split_word
Teil das jeweilige Wort in Wortbestandteile auf.
### check_capital
Prueft, ob das Wort mit einem Großbuchstaben anfängt und setzt - falls ja - das Attribut auf 'True'
