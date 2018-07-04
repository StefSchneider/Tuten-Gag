## Klassen

### Text (Datenstruktur Baum)

#### Methoden
- create_node: Erzeugt einen neuen Kinderknoten für einen Satz.

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

#### Attribute
- ConnectedWith (NumberWord, Typ Int): Gibt an, mit welchem anderen Wort das jeweilige Wort ueber eine Kooplung verbunden ist.
- Capital (Boolean): Gibt an, ob das Wort mit einem Großbuchstaben anfängt

#### Methoden
- check: Steuert die Ueberpruefungen der einzelnen Woerter, zum Beispiel auf Grossbuchstaben
- xxx

### Combination

#### Attribute
- Points: Gibt die Gesamtpunktzahl der Komibination für das Ranking an.
- Part1: Liste aus Nummer Wort 1, Position in Wort 1
- Part2: Liste aus Nummer Wort 2, Position in Wort 2

#### Methoden
- rate_in_dictionary: Ueberprueft, 

## Funktionen

### split_text
Teilt den Gesamttext in Sätze auf. Aufteilung nach '.', '!' oder '?'
#### Regeln
Der Text wird Buchstabe für Buchstabe überprüft.
Es werden zwei Marker benötigt, einer für den Satzanfang und einer für das Satzende.
Wird eines der genannten Satzzeichen gefunden, wird der String bis zu dieser Stelle in einen neuen Satz kopiert. Dabei werden überflüssige Leerzeichen am Satzanfang und Satzende abgeschnitten. Der neue Satz wird als String in einen Baum gehangen. Der Marker für den Satzanfang wird auf die neue Textstelle (Satzzeichen + 1) verschoben. Anschließend geht die Überprüfung an der Stelle weiter.
Die Marker für Satzanfang (SentenceStart) und Satzende (SentenceEnd) sind Variablen, die nur in der Funktion benötigt werden.
Es wird eine interne Variable NumberSentence (Typ: int) eingesetzt, die die laufende Nummer des Satzes abspeichert und mit in den Baum überträgt -> Methode: insert_sentence (self, number_sentence). Damit können später die einzelnen Sätze gezielt angesteuert werden.

### split_sentence
Teilt den jeweiligen Satz in Satzbestandteile (Woerter, Satzzeichen etc.) auf
#### Regeln
Vor jedes Satzzeichen wird ein Leerzeichen gesetzt. Dann wird der Saz überprüft: Sind mehr als zwei Leerzeichen nacheinander vorhanden, wird das erste davon geloescht. Anschließend wird der Satz bei jedem Leerzeichen getrennt und die einzelnen Satzbestandteile als String in einen Baum gehangen, versehen mit der Nummer der Position, an der es gestanden hat. Zudem wird als Attribut (SwitchPermit) mitgegeben, ob es sich um einen Satzbestandteil handelt, bei dem die Wortbestandteile getauscht werden duerfen ('True') oder nicht ('False'). Nicht getauscht werden duerfen zum Beispiel Artikel oder Satzzeichen.

### split_word
Teil das jeweilige Wort in Wortbestandteile auf.
#### Regeln
Es werden zwei Marker benötigt, einer für den Wortbestandteilanfang und einer für das Wortbestandteilende.
Wechselt der aktuelle Buchstabe von Vokal zu Konsonant oder Satzzeichen oder Sonstige - oder umgekehrt, wird der aktuelle Wortbestandteil abgeschnitten und als String in einen Baum gehangen. Der Marker für den Wortbestandteilanfang wird auf die neue Textstelle (Wortbestandteilende + 1) verschoben. Anschließend geht die Überprüfung an der Stelle weiter.
Die Marker für Wortbestandteilanfang (WordElementStart) und Satzende (WordElementEnd) sind Variablen, die nur in der Funktion benötigt werden. Es wird eine interne Variable NumberElement (Typ: int) eingesetzt, die die laufende Nummer des Wortbestandteils abspeichert und mit in den Baum überträgt -> Methode: insert_wordelement (self, NumberElement). Damit können später die einzelnen Wortbestandteile gezielt angesteuert werden.


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


### Variablen

#### kurzzeitig einsetzbar
- Counter: benoetigt für Zaehloperationen in Schleifen
