# Klassen

## ConfigData

## Stocks (ConfigData)  
*Geeignet zur Erfassung von Buchstabengruppen, z.B. Vokale oder Konsonanten, oder Wortklassen, z.B. Artikel, in einer Menge*  
Aufbau im Modul `M_Config`

### Attribute

### Methoden
#### initiate (self, NewStock)  
##### Parameter:
- **NewStock**: Enthaelt die Art des neu anzulegenden Bestandes, z.B. Set (Menge), String (Zeichenkette), Dictionary (Woerterbuch) oder List (Liste)

*Legt einen neue, leere Menge, String, Liste oder Dictionary an*  
>Enthaelt NewStock den Wert 'String', wird ein leerer String "" angelegt; enthaelt NewStock den Wert 'Set', wird eine leere Menge ()   angelegt; enthaelt NewStock den Wert 'Dictionary', wird ein leeres Woerterbuch {} angelegt; enthaelt NewStock den Wert 'List', wird eine leere Liste [] angelegt. Fallback ist ein leerer String - die Ueberpruefung auf den Uebergabewert 'String' erfolgt also am Ende    der If-Abfragen.

#### add_to (self, Stock, Component)  
##### Parameter:  
- **Stock**: Enthaelt den namentlichen Bestand, in den der Buchstabe eingefuegt werden soll.
- **Component**: Enthaelt den jeweiligen Buchstaben oder die Wortklasse, die eingefuegt werden soll.  

*Durchsucht die Config-Datei und fuegt die passenden Buchstaben zur jeweiligen Menge zu.*
>Mit 'type' wird zunaechst ueberprueft, zu welcher Bestandsart der entsprechende Bestand gehoert. In Abhaengigkeit von der Bestandsart wird der neue Buchstabe zum Bestands hinzugefuegt.

#### search_in (self, CheckStock, CheckComponent)  
##### Parameter:  
- **CheckStock**: Enthaelt den Namen des Bestandes, der ueberprueft werden soll.
- **CheckComponent**: Enthaelt den Buchstaben, der in diesem Bestand gesucht werden soll.  

*Ueberprueft, ob der jeweilige Buchstabe in der jeweiligen Menge vorhanden ist. Liefert 'True' oder 'False' zurück.*   
>Mit 'type' wird zunaechst ueberprueft, zu welcher Bestandsart der entsprechende Bestand gehoert. Wird der Buchstabe innerhalb des Bestands gefunden, wird die der Rueckgabewert 'InStock' auf 'True' gesetzt. Grundeinstellung/Fallback fuer 'InStock' ist 'False'. 


### Trees (Datenstruktur Baum)

Text = Tree

#### Methoden
- **create_node**: Erzeugt einen neuen Kinderknoten für einen Satz.  

## Dictionaries  
*Geeignet zur Erfassung der Woerterbuecher in einem AVL-Baum*  
Aufbau im Modul `M_Dictionaries`

### Attribute

### Methoden
#### load (self, InDictionary, FromDictionaryFile)  
##### Parameter:
- **InDictionary**: Enthaelt das Woerterbuch (AVL-Baum), in das die Woerterbuch-Datei geladen werden soll.
- **FromDictionaryFile**: Enthaelt den Dateinamen inkl. Pfad, aus dem die Woerter fuer das Woerterbuch geladen werden sollen.

*Lädt ein Woerterbuch aus einer Datei in den Woerterbuch-Baum.*  
>Die einzelnen Woerter werden aus der Woerterbuch-Datei ausgelesen und in das Woerterbuch eingefuegt, solange bis das Ende der Datei erreicht ist. Doppelte Woerter werden nicht eingefuegt.

#### save (self, InDictionaryFile, FromDictionary)  
##### Parameter:
- **InDictionaryFile**: Enthaelt den Dateinamen inkl. Pfad, in den die Woerter fuer das Woerterbuch gespeichert werden sollen.
- **FromDictionary**: Enthaelt das Woerterbuch (AVL-Baum), das in die Woerterbuch-Datei gespeichert werden soll.

*Speichert einen Woerterbuch-Baum in einer Woerterbuch-Datei ab.*  
>Zunaechst wird ueberprueft, ob eine Woerterbuch-Datei mit gleichem Namen schon existiert, in diesem Fall wird daraus das Backup gemacht - mit dem Namen 'Dateiname_Entstehungsdatum'. Anschließend wird die Woerterbuch-Datei mit der aktuellen Fassung ueberschrieben. Dazu wird das Woerterbuch (AVL-Baum) ausgelesen und jedes Wort in eine einzelne Zeile geschrieben.

#### check_size (self, DictionaryFile)  
##### Parameter:
- **DictionaryFile**: Enthaelt den Namen der Datei inkl. Pfad, dessen Groesse bestimmt werden soll.

*Ermittelt die Groesse (= Anzahl der Eintraege) einer Woerterbuch-Datei.*  
>Fuer die Ermittlung der Groesse wird die Anzahl der Zeilen in der Woerterbuch-Datei auslesen. Fuer jede Zeile wird der Wert '1' zur Gesamtzahl dazuaddiert. Leerzeilen werden nicht mitgezaehlt. Ist das Dateiende erreicht, wird die Gesamtzahl (DictionarySize) zurueckgegeben.

#### check_status (self, DictionarySize, NumberLine)  
##### Parameter:
- **DictionarySize**: Enthaelt die Groesse (= Anzahl der Eintraege) einer Woerterbuch-Datei, die vorher ermittelt wurde.
- **NumberLine**: Enthaelt die Nummer der aktuell einzulesenden Zeile.

*Ermittelt, wie viel Prozent der Woerterbuch-Datei bereits in den Woerterbuch-Baum übertragen wurden.*
>Zur Ermittlung des aktuellen Status wird die Nummer des aktuell einzulesenden Eintrags ins Verhaeltnis zur Gesamtzahl gesetzt. Zurueckgegeben wird dann das Verhaeltnis als Prozentzahl.


## Strings  
*Geeignet zur Erfassung von Texten, Saetzen, Satzbestandteilen und Wortstandteilen*  
Aufbau im Modul M_Input

#### Attribute
- String

#### Methoden


### TextInput (Vererbung Strings)
Aufbau im Modul M_Input

#### Attribute

#### Methoden
**split_string**  
*Teilt den Gesamtext in mehrere Saetze auf.*  
>Es werden zwei Marker benötigt, einer für den Satzanfang und einer für das Satzende. Der Text wird Buchstabe für Buchstabe überprüft.  Wird eines der Satzzeichen '.', '!' oder '?' gefunden, wird der String bis zu dieser Stelle in einen neuen Satz kopiert. Dabei werden überflüssige Leerzeichen am Satzanfang und Satzende abgeschnitten. Der neue Satz wird als String in einen Baum gehangen. Der Marker für den Satzanfang wird auf die neue Textstelle (Satzzeichen + 1) verschoben. Anschließend geht die Überprüfung an der Stelle weiter.
Die Marker für Satzanfang (SentenceStart) und Satzende (SentenceEnd) sind Variablen, die nur in der Funktion benötigt werden. Es wird eine interne Variable NumberSentence (Typ: int) eingesetzt, die die laufende Nummer des Satzes abspeichert und mit in den Baum überträgt -> Methode: insert_sentence (self, number_sentence). Damit können später die einzelnen Sätze gezielt angesteuert werden.   


### TextOutput (Vererbung Strings)
Aufbau im Modul M_Input

#### Attribute

#### Methoden


### Sentences (Vererbung Strings)
Aufbau im Modul M_Input

#### Attribute
- **Number (Typ Int)**: Erfasst die Nummer der Reihenfolge des Satzes im Text.

#### Methoden
**create_node**: Erzeugt einen neuen Kinderknoten für einen Satzbestandteil 

**split_string** 
*Teilt den jeweiligen Satz in Satzbestandteile (Woerter, Satzzeichen etc.) auf* | Methode wird uerberschrieben
>Vor jedes Satzzeichen wird ein Leerzeichen gesetzt. Dann wird der Saz überprüft: Sind mehr als zwei Leerzeichen nacheinander vorhanden, wird das erste davon geloescht. Anschließend wird der Satz bei jedem Leerzeichen getrennt und die einzelnen Satzbestandteile als String in einen Baum gehangen, versehen mit der Nummer der Position, an der es gestanden hat. Zudem wird als Attribut (SwitchPermit) mitgegeben, ob es sich um einen Satzbestandteil handelt, bei dem die Wortbestandteile getauscht werden duerfen ('True') oder nicht ('False'). Nicht getauscht werden duerfen zum Beispiel Artikel oder Satzzeichen.


### Words (Vererbung Sentences)

#### Attribute
- **Number (Typ Int)**: Erfasst die Nummer der Reihenfolge des Wortes im jeweiligen Satz.
- **SwapAllowed (Typ Bol)**: Gibt an, ob das Wort zum Tauschen freigegeben ist oder nicht, z.B. bei Artikeln / Grundeinstellung: 'False'
- **ConnectedWith (NumberWord, Typ Int)**: Gibt an, mit welchem anderen Wort das jeweilige Wort ueber eine Kooplung verbunden ist. / Grundeinstellung: 'None'
- **Capital (Typ Bol)**: Gibt an, ob das Wort mit einem Großbuchstaben anfängt / Grundeinstellung: 'False'
- **SwitchPartOwn (Typ Int)**: Gibt an, welcher Bestandteil des eigenen Wortes getauscht werden soll / Grundeinstellung: 'None'
- **SwitchPartForeign (NumberWord : NumberPart, Typ Dic)**: Gibt an, welcher Teil welches fremden Wortes getauscht werden soll. / Grundeinstellung: 'None' : 'None'
- **Initial**: Gibt an, zu welchem Typ der Wortbestandteile der Anfang des Wortes gehört, z.B. Vokale oder Konsonanten_Stark / Grundeinstellung: 'None'

#### Methoden
- **split_string**:   
*Teilt das jeweilige Wort in mehrere Wortbestandteile auf* | Methode wird ueberschrieben  
>Es werden zwei Marker benötigt, einer für den Wortbestandteilanfang und einer für das Wortbestandteilende. Wechselt der aktuelle Buchstabe von Vokal zu Konsonant oder Satzzeichen oder Sonstige - oder umgekehrt, wird der aktuelle Wortbestandteil abgeschnitten und als String in einen Baum gehangen. Der Marker für den Wortbestandteilanfang wird auf die neue Textstelle (Wortbestandteilende + 1) verschoben. Anschließend geht die Überprüfung an der Stelle weiter. Die Marker für Wortbestandteilanfang (WordElementStart) und Satzende (WordElementEnd) sind Variablen, die nur in der Funktion benötigt werden. Es wird eine interne Variable NumberElement (Typ: int) eingesetzt, die die laufende Nummer des Wortbestandteils abspeichert und mit in den Baum überträgt -> Methode: insert_wordelement (self, NumberElement). Damit können später die einzelnen Wortbestandteile gezielt angesteuert werden.
- **create_node**: Erzeugt einen neuen Kinderknoten für einen Wort und setzt die Attribute auf die Grundeisntellungen 
- **check**: Steuert die Ueberpruefungen der einzelnen Woerter, zum Beispiel auf Grossbuchstaben / ruft alle anderen Pruef-Methoden in der richtigen Reihenfolge auf.
- **check_swap_allowed**: Ueberprueft, ob das Wort ueberhaupt zum Tausch der Bestandteile freigegeben ist.
- **check_capital**: Ueberprüft, ob das Wort mit einem Grossbuchstaben beginnt. Rueckgabewert 'True' oder 'False'

### Part
Enthaelt die einzelnen Bestandteile des Wortes, z.B. St|e|f|a|n
- **create_node**: Erzeugt einen neuen Kinderknoten für einen Wortbestandteil



### CombinationList
#### Methoden
- **insert**: Fuegt eine neue Wortkombination mit der Gesamtpunktzahl in die Liste ein.
- **delete**: Loescht eine Wortkombination aus der Liste.
- **sort**: Sortiert die Liste nach der Gesamtpunktzahl. Algorithmus: Bubble-Sort.
- **rank_list (Word1:Part1, Word2:Part2, Points)**: Sortiert die Liste aus Kombinationen in die richtige Reihenfolge, gemessen an der Gesamtpunktzahl pro Kombination. Anschließend gibt die Funktion die Daten der am höchsten bewerteten Kombination zurück: Word1:Part1, Word2:Part2 / Regeln: An die Funktion rank_list werden die entsprechenden Daten zu den Kombinationen uebergeben und in eine Liste geschrieben. Sollten keine weiteren Kombinationen zur Verfügung stehen, wird die Funktion noch einmal aufgerufen, aber mit den Argumenten 'None:None', 'None:None', '0'. Die Funktion uberprueft zuerst ob diese Werte uebergeben wurden. Falls nein, werden die Werte in eine Liste geschrieben. Falls ja, startet die Sortierung der Liste und die Daten der Kombination mit der hoechsten Punktezahl wird zurueckgegeben.


### Combination

#### Attribute
- SumPoints: Gibt die Gesamtpunktzahl der Kombination für das Ranking an.
- Part1: Liste aus Nummer Wort 1, Position in Wort 1
- Part2: Liste aus Nummer Wort 2, Position in Wort 2

#### Methoden
- **combine**: Steuert das Kombinieren von Wortbestandteilen
- **combine_inner**: Tauscht die beiden Anfangswortbestandteile eines gekoppelten Wortes

- **rate**: Steuert, welche Ratings der Wortkombinationen durchgefuehrt werden sollen.
- **rate_in_dictionary**: Ueberprueft, ob eines oder die beiden Woerter in einem der Woerterbuecher auftauchen. Falls ja, werden die Punkte von RateInDictionary mit dem jweiligen Faktor zur Gesamtpunktzahl (SumPoints) dazuaddiert.
- **rate_in_user**: Ueberprueft, ob eines oder die beiden Woerter im Woerterbuch der User als beliebtes Wort auftauchen. Falls ja, werden die Punkte von RateInUser mit dem jeweiligen Faktor zur Gesamtpunktzahl (SumPoints) dazuaddiert.
- **rate_number_letters**: Ueberprueft, wie viele Buchstaben insgesamt in der Kombination der beiden Worte getauscht wurden und addiert pro Buchstaben die Punkte fuer RateNumberLetters mit dem jeweiligen Faktor zur Gesamtpunktzahl.
- **rate_words_linked**: Ueberprueft, ob die Kombination aus zwei miteinander gekoppelten Worten besteht und addiert fuer diesen Fall die Punkte von RateWordsLinked mit dem Faktor zur Gesamtpunktzahl hinzu.

-----------------------------

## Funktionen



### search_equal (Buchstabenart, Spanne)
Sucht in der vorgegebenen Spanne nach passenden Tauschpartnern mit der gleichen Buchstabenart.
#### Regeln
Falls die Spanne '0' ist, wird innerhalb desselben Wortes gesucht. Oder: Falls innerhalb der vorgegebenen Spanne kein passender Tauschpartner gefunden wird, wird die Spanne auf '0' gesetzt (NOCH ZU KLAEREN)

### check_word
Ueberprüft, ob das eingegebene Wort im Woerterbuch vorhanden ist, meldet zurück, wenn eines fehlt und fragt in diesem Fall, ob das Wort neu aufgenommmen werden soll (in Woerterbuch 'Fremd')

### rank_list (Word1:Part1, Word2:Part2, Points)
Sortiert die Liste aus Kombinationen in die richtige Reihenfolge, gemessen an der Gesamtpunktzahl pro Kombination. Anschließend gibt die Funktion die Daten der am höchsten bewerteten Kombination zurück: Word1:Part1, Word2:Part2 
#### Regeln
An die Funktion rank_list werden die entsprechenden Daten zu den Kombinationen uebergeben und in eine Liste geschrieben. Sollten keine weiteren Kombinationen zur Verfügung stehen, wird die Funktion noch einmal aufgerufen, aber mit den Argumenten 'None:None', 'None:None', '0'. Die Funktion uberprueft zuerst ob diese Werte uebergeben wurden. Falls nein, werden die Werte in eine Liste geschrieben. Falls ja, startet die Sortierung der Liste und die Daten der Kombination mit der hoechsten Punktezahl wird zurueckgegeben.


------------------------

### AvlTree (aus Toolbox AVLTree)

#### Methoden
- **insert**: Fuegt einen neuen Knoten für ein neues Wort in den Baum ein.
- **insert_without_double**: Fuegt einen neuen Knoten in den Baum ein, aber nur wenn das keyword nicht bereits existiert.
- **rebalance**: Richtet den Baum neu aus.
- **update_heights**: Ermittelt die aktuelle Höhe des Baums.
- **update_balances**: Ermittelt, ob der Baum ausbalanciert ist.
- **rotate_right**: Fuehrt eine Rechtsrotation im Knoten durch.
- **rotate_left**: Fuehrt eine Linksrotation im Knoten durch.
- **delete**: Loescht einen Knoten aus dem Baum.
- **search**: Sucht ein keyword in dem Baum.
- **inorder_traverse**: Liest den Baum nach der Regel Links-Wurzel-Rechts aus.
- **preorder_traverse**: Liest den Baum nach der Regel Wurzel_Links-Rechts aus.
- **postorder_traverse**: Liest den Baum nach der Regel Links-Rechts-Wurzel aus.
- **levelorder_traverse**: Liest den Baum etagenweise aus.

----------------------

### Variablen

#### kurzzeitig einsetzbar
- Counter: benoetigt für Zaehloperationen in Schleifen

-----------------------
### Baumstruktur
                                              Text
                       |                                         |
                   Sentence(1)                              Sentence(2)
         |          |         |         |           
       Word(1)    Word(2)   Word(3)   Word(4)
      |       |
    Part(1) Part(2)
 

 
 #### *Attributes*
 - SwapAllowed: True/False
 - ConnectedWith: Number
 - Capital: True/False
 - SwitchPartOwn: Number
 - SwitchPartForeign: Number
 - Initial: Stock
 
 
