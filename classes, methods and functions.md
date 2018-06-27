## Klassen

### Text (Datenstruktur Baum)

#### Methoden
- create_node: Erzeugt einen neuen Kindenknoten für einen Satz.

### Dictionary (Datenstruktur AVL-Baum)

#### Methoden
- load: Lädt ein Woerterbuch aus einer Datei in den Woerterbuch-Baum.
- save: Speichert einen Woerterbuch-Baum in einer Woertrebuch-Datei ab.
- check_size: Ermittelt die Groesse (= Anzahl der Eintraege) der Woerterbuch-Datei.
- check_status: Ermittelt, wie viel Prozent der Woerterbuch-Datei bereits in den Woerterbuch-Baum übertragen wurden.

### Sentence

#### Methoden
- create_node: Erzeugt einen neuen Knoten für einen Satzbestandteil.
- xxx

### Word
- xxx
- xxx


## Funktionen

### split_text
Teilt den Gesamttext in Sätze auf. Aufteilung nach '.', '!' oder '?'
#### Regeln
Der Text wird Buchstabe für Buchstabe überprüft.
Es werden zwei Marker benötigt, einer für den Satzanfang und einer für das Satzende.
Wird eines der genannten Satzzeichen gefunden, wird der String bis zu dieser Stelle in einen neuen Satz kopiert. Dabei werden überflüssige Leerzeichen am Satzanfang und Satzende abgeschnitten. Der neue Satz wird als String in einen Baum gehangen. Der Marker für den Satzanfang wird auf die neue Textstelle (Satzzeichen + 1) verschoben. Anschließend geht die Überprüfung an der Stelle weiter.
Die Marker für Satzanfang (SentenceStart) und Satzende (SentenceEnd) sind Variablen, die nur in der Funktion benötigt werden.
Es wird eine interne Variable number_sentence (Typ: int) eingesetzt, die die laufende Nummer des Satzes abspeichert und mit in den Baum überträgt -> Methode: insert_sentence (self, number_sentence). Damit können später die einzelnen Sätze gezielt angesteuert werden.

### split_sentence
Teilt den jeweiligen Satz in Satzbestandteile (Woerter, Satzzeichen etc.) auf
### split_word
Teil das jeweilige Wort in Wortbestandteile auf.
#### Regeln
Es werden zwei Marker benötigt, einer für den Wortbestandteilanfang und einer für das Wortbestandteilende.
Wechselt der aktuelle Buchstabe von Vokal zu Konsonant oder Satzzeichen oder Sonstige - oder umgekehrt, wird der aktuelle Wortbestandteil abgeschnitten und als String in einen Baum gehangen. (Der Marker für den Satzanfang wird auf die neue Textstelle (Satzzeichen + 1) verschoben. Anschließend geht die Überprüfung an der Stelle weiter.
Die Marker für Satzanfang (SentenceStart) und Satzende (SentenceEnd) sind Variablen, die nur in der Funktion benötigt werden.
Es wird eine interne Variable number_sentence (Typ: int) eingesetzt, die die laufende Nummer des Satzes abspeichert und mit in den Baum überträgt -> Methode: insert_sentence (self, number_sentence). Damit können später die einzelnen Sätze gezielt angesteuert werden.) NOCH ZU BEARBEITEN
### check_capital
Prueft, ob das Wort mit einem Großbuchstaben anfängt und setzt - falls ja - das Attribut auf 'True'

### AvlTree (aus Toolbox AVLTree)

#### Methoden
- insert: Fuegt einen neuen Knoten in den Baum ein.
- insert_without_double: Fuegt einen neuen Knoten in den Baum ein, aber nur wenn das keyword nicht bereits existiert.
- rebalance: Richtet den Baum neu aus.
- update_heights: Ermittelt die aktuelle Höhe des Baums.
- update_balances: Ermittelt, ob der Baum ausbalanciert ist.
- rotate_right: Fuehrt eine Rechtsrotation im Knoten durch.
- rotate_left: Fuehrt eine Linksrotation im Knoten durch.
- delete: Loescht einen Knoten aus dem Baum.
- search: Sucht ein keyword in dem Baum.
- inorder_traverse: Liest den Baum nach der Regel Links-Wurzel-Rechts aus.
- preorder_traverse: Liest den Baum nach der Regel Wurzel_Links-Rechts aus.
- postorder_traverse: Liest den Baum nach der Regel Links-Rechts-Wurzel aus.
- levelorder_traverse: Liest den Baum etagenweise aus.
