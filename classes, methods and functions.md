# Structure of classes


    ConfigData  
        ├ Files  
        ├ Pathes  
        └ Stocks  
     
    Dictionaries
    
    Strings
        ├ TextInput
        │   └ TextEdit
        │       └ Sentences
        │           └ Words
        │               ├ Parts
        │               │   └ PartsAnalyze
        │               └ WordsAnalyze
        ├ TextOutput
        




# Klassen

## ConfigData

## Files (ConfigData)

## Pathes (ConfigData)
*Geeignet zu Erfassung von Dateipfaden, auf mit denen spaeter Dateien angesteuert werden, z.B. die Woerterbuch-Dateien.*

### Methoden
#### NewPathDictionary.init__ (self) 

NewPathDictionary: Dictionary, in der alle Dateipfade hinterlegt werden.

*Legt ein neue Variable vom Typ Dic an, in der die Dateipfade aus der Config-Datei erfasst werden.*
>Die Initialisierung erfolgt mit der Zuweisung von {}. Der erste Teil jedes neuen Eintrags umfasst immer den konkreten Pfad, der zweite Teil die Bezeichnung (nicht den Namen!) der Datei, zu der der Pfad fuehrt.

#### PathDictionary.add_to (self, ForFile, Path)  

PathDictionary: Dictionary, in das der neue Dateipfad aufgenommen werden soll.

##### Parameter:  
- **ForFile**: Bezeichnung der Datei, zu der der Pfad leitet.
- **Path**: Dateipfad, der neu ins Dictionary aufgenommen werden soll.

*Fuegt einen neuen Eintrag zum bisherigen Dictionary der Dateipfade zu.*
>Ans Ende der Dictionary wird neue zweiteiliger Eintrag angefuegt. Der erste Teil jedes neuen Eintrags umfasst immer den konkreten Pfad, der zweite Teil die Bezeichnung (nicht den Namen!) der Datei, zu der der Pfad fuehrt.

## Stocks (ConfigData)  
*Geeignet zur Erfassung von Buchstabengruppen, z.B. Vokale oder Konsonanten, oder Wortklassen, z.B. Artikel, in einer Menge.*  
Aufbau im Modul `M_Config`.

### Methoden
#### NewStock.init__ (self, StockType)  

NewStock: Neuer Bestand, der angelegt werden soll.

##### Parameter:
- **StockType**: Art des neu anzulegenden Bestandes, z.B. Set (Menge), String (Zeichenkette), Dictionary (Woerterbuch) oder List (Liste).

*Legt einen neue, leere Menge, String, Liste oder Dictionary an.*  
>Enthaelt NewStock den Wert 'String', wird ein leerer String "" angelegt; enthaelt NewStock den Wert 'Set', wird eine leere Menge () angelegt; enthaelt NewStock den Wert 'Dictionary', wird ein leeres Woerterbuch {} angelegt; enthaelt NewStock den Wert 'List', wird eine leere Liste [] angelegt. Fallback ist ein leerer String - die Ueberpruefung auf den Uebergabewert 'String' erfolgt also am Ende der If-Abfragen.

#### Stock.add_to (self, Component)  

Stock: Namentlicher Bestand, in den der Buchstabe eingefuegt werden soll.

##### Parameter:  
- **Component**: Jeweiliger Buchstaben oder die Wortklasse, die eingefuegt werden soll.  

*Durchsucht die Config-Datei und fuegt die passenden Buchstaben zur jeweiligen Menge zu.*
>Mit 'type' wird zunaechst ueberprueft, zu welcher Bestandsart der entsprechende Bestand gehoert. In Abhaengigkeit von der Bestandsart wird der neue Buchstabe zum Bestand hinzugefuegt.

#### CheckStock.search_in (self, CheckComponent)  

CheckStock: Name des Bestandes, der ueberprueft werden soll.

##### Parameter:  
- **CheckComponent**: Buchstabe, der in diesem Bestand gesucht werden soll.  

*Ueberprueft, ob der jeweilige Buchstabe in der jeweiligen Menge vorhanden ist. Liefert 'True' oder 'False' zurück.*   
>Mit 'type' wird zunaechst ueberprueft, zu welcher Bestandsart der entsprechende Bestand gehoert. Wird der Buchstabe innerhalb des Bestands gefunden, wird die der Rueckgabewert 'InStock' auf 'True' gesetzt. Grundeinstellung/Fallback fuer 'InStock' ist 'False'. 

-----------------------

## Dictionaries  
*Geeignet zur Erfassung der Woerterbuecher in einem AVL-Baum.*  
Aufbau im Modul `M_Dictionaries`.

### Methoden
#### Dictionary.init__ (self)

Dictionary: Woerterbuch (AVL-Baum), das neu angelegt werden soll.

*Legt ein neues Woerterbuch mit dem Namen von Dictionary an.*
>Die Methode greift auf die Toolbox 'AVLTree' zu und erzeugt einen Grundeintrag für ein neues Woerterbuch, in das später die einzelnen Woerter geladen werden.

#### InDictionary.load (self, FromDictionaryFile)  

InDictionary: Woerterbuch (AVL-Baum), in das die Woerterbuch-Datei geladen werden soll.

##### Parameter:
- **FromDictionaryFile**: Dateiname inkl. Pfad, aus dem die Woerter fuer das Woerterbuch geladen werden sollen.

*Laedt ein Woerterbuch aus einer Datei in den Woerterbuch-Baum.*  
>Die einzelnen Woerter werden aus der Woerterbuch-Datei ausgelesen und in das Woerterbuch eingefuegt, solange bis das Ende der Datei erreicht ist. Doppelte Woerter werden nicht eingefuegt. Dazu wird innerhalb der Tollbox 'AVLTree' die Methode 'insert_without_double' genutzt.

#### FromDictionary.save (self, InDictionaryFile)  

FromDictionary: Woerterbuch (AVL-Baum), das in die Woerterbuch-Datei gespeichert werden soll.

##### Parameter:
- **InDictionaryFile**: Dateiname inkl. Pfad, in den die Woerter fuer das Woerterbuch gespeichert werden sollen.

*Speichert einen Woerterbuch-Baum in einer Woerterbuch-Datei ab.*  
>Zunaechst wird ueberprueft, ob eine Woerterbuch-Datei mit gleichem Namen schon existiert, in diesem Fall wird daraus das Backup gemacht - mit dem Namen 'Dateiname_Entstehungsdatum'. Anschließend wird die Woerterbuch-Datei mit der aktuellen Fassung ueberschrieben. Dazu wird das Woerterbuch (AVL-Baum) ausgelesen und jedes Wort in eine einzelne Zeile geschrieben.

#### InDictionary.check_word (self, SearchWord)

InDictionary: Woerterbuch, in dem das Wort gesucht werden soll.

#### Parameter:  
- **SearchWord**: Wort, das in dem Woerterbuch gesucht werden soll.

*Ueberprüft, ob das eingegebene Wort im Woerterbuch vorhanden ist*  
>Mit der 'Search-Methode' der 'Toolbox AVLTree' wird das Wort im Woerterbuch-Baum gesucht. Ist es nicht enthalten, wird der Nutzer gefragt, ob das Wort richtig geschrieben ist und ist das Fremdwoerterbuch aufgenommen werden soll.

#### InDictionary.add_word (self, AddWord)

InDictionary: Woerterbuch, in das das Wort ergaenzt werden soll.

##### Parameter:
- **AddWord**: Wort, das in das Woerterbuch eingefuegt werden soll.

>Mithilfe der 'Insert-Methode' der Toolbox 'AVLTree' wird das Wort in das jewelige Woerterbuch an der richtigen Stelle eingefuegt. Anschließend wird die 'Save-Methode' aufgerufen, um das ergaenzte Woerterbuch abzuspeichern.

#### DictionaryFile.check_size (self)  

DictionaryFile: Name der Datei inkl. Pfad, dessen Groesse bestimmt werden soll.

*Ermittelt die Groesse (= Anzahl der Eintraege) einer Woerterbuch-Datei.*  
>Fuer die Ermittlung der Groesse wird die Anzahl der Zeilen in der Woerterbuch-Datei auslesen. Fuer jede Zeile wird der Wert '1' zur Gesamtzahl dazuaddiert. Leerzeilen werden nicht mitgezaehlt. Ist das Dateiende erreicht, wird die Gesamtzahl (DictionarySize) zurueckgegeben.

#### Dictionary.check_status (self, DictionarySize, NumberLine)  

Dictionary: Woerterbuch, dessen Ladestatus ermittelt werden soll.

##### Parameter:
- **DictionarySize**: Groesse (= Anzahl der Eintraege) einer Woerterbuch-Datei, die vorher ermittelt wurde.
- **NumberLine**: Nummer der aktuell einzulesenden Zeile.

*Ermittelt, wie viel Prozent der Woerterbuch-Datei bereits in den Woerterbuch-Baum übertragen wurden.*
>Zur Ermittlung des aktuellen Status wird die Nummer des aktuell einzulesenden Eintrags ins Verhaeltnis zur Gesamtzahl gesetzt. Zurueckgegeben wird dann das Verhaeltnis als Prozentzahl.

-----------------------

## Strings  
*Geeignet zur Erfassung von Texten, Saetzen, Satzbestandteilen und Wortstandteilen*  
Aufbau im Modul `M_Input`

#### Attribute
- String

## TextInput (Strings)
Aufbau im Modul `M_Input`


-----------------------

### Structure of TextTree (TextEdit)

    ┌───────┐           ┌───────┐
    │Content│     ┌────►│Content│     ┌──── =None
    │ =Text1│     │     │ =Text2│     │
    └───────┘     │     └───────┘     │
    │Node   └─────┘     │Node   └─────┘
    │Down   NodeRight   │Down   NodeRight
    │                   │=None
    │
    ▼
    ┌───────┐           ┌───────┐           ┌───────┐
    │Content│     ┌────►│Content│     ┌────►│Content│     ┌──── =None   
    │ =Satz1│     │     │ =Satz2│     │     │ =Satz3│     │
    └───────┘     │     └───────┘     │     └───────┘     │
    │Node   └─────┘     │Node   └─────┘     │Node   └─────┘
    │Down   NodeRight   │Down   NodeRight   │Down   NodeRight
    │                   │=None              │=None
    │
    ▼                   
    ┌───────┐           ┌───────┐           ┌───────┐           ┌───────┐
    │Content│     ┌────►│Content│     ┌────►│Content│     ┌────►│Content│     ┌──── =None
    │ =Wort1│     │     │ =Wort2│     │     │ =Wort3│     │     │ =Wort4│     │
    └───────┘     │     └───────┘     │     └───────┘     │     └───────┘     │
    │Node   └─────┘     │Node   └─────┘     │Node   └─────┘     │Node   └─────┘
    │Down   NodeRight   │Down   NodeRight   │Down   NodeRight   │Down   NodeRight
    │                   │=None              │=None              │=None
    │
    ▼                   
    ┌───────┐           ┌───────┐           ┌───────┐           ┌───────┐           ┌───────┐
    │Content│     ┌────►│Content│     ┌────►│Content│     ┌────►│Content│     ┌────►│Content│     ┌──── =None
    │ =Teil1│     │     │ =Teil2│     │     │ =Teil3│     │     │ =Teil4│     │     │ =Teil5│     │
    └───────┘     │     └───────┘     │     └───────┘     │     └───────┘     │     └───────┘     │
    │Node   └─────┘     │Node   └─────┘     │Node   └─────┘     │Node   └─────┘     │Node   └─────┘
    │Down   NodeRight   │Down   NodeRight   │Down   NodeRight   │Down   NodeRight   │Down   NodeRight
    │=None              │=None              │=None              │=None              │=None 

-----------------------

## TextEdit (TextInput)
Aufbau im Modul `M_Edit`

### Attribute
- **NodeContent**: Inhalt des Knotens
- **NodeDown**: Zeiger zu tiefer gelegenen Ebene
- **NodeRight**: Zeiger auf den naechten Inhalt in der gleichen Ebene
- **NumberText**: Nummer des Textes, der in den Baum gehangen wird.
- **WhoSaid**: Person, der der Text zugordnet wird. Wichtig z.B. bei Dialogen.

### Methoden
#### TextNode.init__ (self)

TextNode: Knoten fuer den Text, der erzeugt werden soll.

*Erzeugt einen Knoten fuer den Baum*
>Fuer den Inhalt des Knotens wird mit NodeContent = '' ein leerer String angelegt, die Zeiger werden auf 'None' gesetzt: NodeDown = None und NodeRight = None. NumberText wird auf '0' gesetzt, WhoSaid wird mit einem leeren String gefülltt. Die Attribute koennen spaeter mit dem jeweiligen Inhalt ueberschrieben werden. Die Attribute koennen spaeter mit dem jeweiligen Inhalt ueberschrieben werden.

#### InsertText.insert_string (self, InTree, NumberText, WhoSaid)

InsertText: Text, der als Wurzel in den Baum gehangen wird. (Typ: Str)

##### Parameter
- **InTree**: Baum, in den der Text gehangen wird.
- **NumberText**: Nummer des Textes, der in den Baum gehangen wird. (Typ: Int)
- **WhoSaid**: Person, der der Text zugordnet wird. Wichtig z.B. bei Dialogen. (Typ: Str)

*Fuegt den eingegebenen Text als Wurzel in den Baum ein.*
>Zunaechst wird ein neuer Baum generiert. Anschließend wird der Text als Wurzel eingefuegt: InTree.NodeContent = InsertText

#### TextToSplit.split_string (self)  

TextToSplit: Text, der aufgeteilt werden soll.

*Teilt den Gesamtext in mehrere Saetze auf.*  
>Es werden zwei Marker benötigt, einer für den Satzanfang und einer für das Satzende. Der Text wird Buchstabe für Buchstabe überprüft.  Wird eines der Satzzeichen '.', '!' oder '?' gefunden, wird der String bis zu dieser Stelle in einen neuen Satz kopiert. Dabei werden überflüssige Leerzeichen am Satzanfang und Satzende abgeschnitten. Der neue Satz wird als String in einen Baum gehangen. Der Marker für den Satzanfang wird auf die neue Textstelle (Satzzeichen + 1) verschoben. Anschließend geht die Überprüfung an der Stelle weiter.
Die Marker für Satzanfang (SentenceStart) und Satzende (SentenceEnd) sind Variablen, die nur in der Funktion benötigt werden. Es wird eine interne Variable NumberSentence (Typ: int) eingesetzt, die die laufende Nummer des Satzes abspeichert und mit in den Baum überträgt -> Methode: insert_string (self, InTree, InsertSentence, NumberSentence). Damit können später die einzelnen Sätze gezielt angesteuert werden.  

## Sentences (TextEdit)
Aufbau im Modul `M_Edit`

### Attribute
- **NodeContent**: Inhalt des Knotens
- **NodeDown**: Zeiger zu tiefer gelegenen Ebene
- **NodeRight**: Zeiger auf den naechten Inhalt in der gleichen Ebene
- **NumberSentence**: Nummer der Reihenfolge des Satzes im Text. (Typ: Int)
- **WhoSaid**: Person, der der Satz zugeordnet wird. (Typ: Str)


#### SentenceNode.init__ (self)

SentenceNode: Knoten fuer den Satz, der erzeugt werden soll.

*Erzeugt einen Knoten fuer den Baum*
>Fuer den Inhalt des Knotens wird mit NodeContent = '' ein leerer String angelegt, die Zeiger werden auf 'None' gesetzt: NodeDown = None und NodeRight = None. NumberSentence wird auf '0' gesetzt, WhoSaid wird mit einem leeren String gefülltt. Die Attribute koennen spaeter mit dem jeweiligen Inhalt ueberschrieben werden.
 

#### InsertSentence.insert_string (self, InTree, NumberSentence, WhoSaid)

InsertSentence: Satz, der eingefuegt werden soll.

##### Parameter
- **InTree**: Baum, in den der Satz gehangen wird.
- **NumberSentence**: Nummer des Satzes, der in den Baum gehangen wird.
- **WhoSaid**: Person, der der Satz zugordnet wird. Wichtig z.B. bei Dialogen.

*Fuegt einen einzelnen Satz mit einer laufenden Nummer in den Baum ein.*
>Der einzufuegende Satz wird mit den Attributen in den Baum auf der zweiten Ebene eingefuegt. Handelt es sich um den ersten Satz, wird NodeContent mit den einzufuegenden Satz, NumberSentence mit '1' und WhoSaid mit dem Namen der Person ueberschrieben, der der Satz zugeordnet wird. Ab den folgenden Saetzen muss zuerst ein neuer Knoten initiiert werden und anschließend der Zeiger des vorherigen Satzes auf den neuen Knoten gestellt werden: SentencePredecessor.NodeRight = NodeNeu.


#### SentenceToSplit.split_string (self)  

SentenceToSplit: Satz, der aufgeteilt werden soll.
 
*Teilt den jeweiligen Satz in Satzbestandteile (Woerter, Satzzeichen etc.) auf*  
>Vor jedes Satzzeichen wird ein Leerzeichen gesetzt. Dann wird der Saz überprüft: Sind mehr als zwei Leerzeichen nacheinander vorhanden, wird das erste davon geloescht. Anschließend wird der Satz bei jedem Leerzeichen getrennt und die einzelnen Satzbestandteile als String in einen Baum gehangen, versehen mit der Nummer der Position, an der es gestanden hat. Zudem wird als Attribut (SwitchPermit) mitgegeben, ob es sich um einen Satzbestandteil handelt, bei dem die Wortbestandteile getauscht werden duerfen ('True') oder nicht ('False'). Nicht getauscht werden duerfen zum Beispiel Artikel oder Satzzeichen.



## Words (Sentences)
Zu der in der Klasse 'Words' erfassten Zeichenketten zaehlen nicht nur Woerter, sondern auch beispielweise Satzzeichen.
Aufbau im Modul `M_Edit`.

### Attribute
- **NodeContent**: Inhalt des Knotens
- **NodeDown**: Zeiger zu tiefer gelegenen Ebene
- **NodeRight**: Zeiger auf den naechten Inhalt in der gleichen Ebene
- **NumberWord**:Nummer der Reihenfolge des Wortes im jeweiligen Satz. (Typ Int)
- **NumberOfParts**: Anzahl der einzelnen Teile, in der Regel Silben, des Wortes. (Typ Int)
- **SwapAllowed**: Gibt an, ob das Wort zum Tauschen freigegeben ist oder nicht, z.B. bei Artikeln / Grundeinstellung: 'False' (Typ Bool)
- **ConnectedWith**: Nummer des anderen Wortes, das mit dem aktuellene Wort ueber eine Kooplung verbunden ist (NumberWord). / Grundeinstellung: 'None' (Typ Int)
- **Capital**: Gibt an, ob das Wort mit einem Großbuchstaben anfängt / Grundeinstellung: 'False' (Typ Bool)
- **Equal**: Gibt an, ob innerhalb der Spanne ein geeigneter Tauschpartner vorliegt, der mit der gleichen Buchstabenart beginnt / Grundeinstellung: 'False' (Typ Bool)
- **SwitchPartOwn**: Gibt an, welcher Bestandteil des eigenen Wortes getauscht werden soll / Grundeinstellung: 'None' (Typ Int)
- **SwitchPartForeign**: Teil welches fremden Wortes, der getauscht werden soll. (NumberWord:NumberPart) / Grundeinstellung: 'None' : 'None' (Typ Dic)
- **Initial**: Typ der Wortbestandteile, zu dem der Anfang des Wortes gehört, z.B. Vokale oder Konsonanten_Stark / Grundeinstellung: 'None' (Typ Str)

### Methoden

#### WordNode.init__ (self)

WordNode: Knoten fuer das Wort, der erzeugt werden soll.

*Erzeugt einen Knoten fuer den Baum*
>Fuer den Inhalt des Knotens wird mit NodeContent = '' ein leerer String angelegt, die Zeiger werden auf 'None' gesetzt: NodeDown = None und NodeRight = None. Die Attribute werden wie folgt gesetzt: NumberWord = 0; NumberOfParts = 0; SwapAllowed = False; ConnectedWith = 0; Capital = False; Equal = False; SwitchPartOwn = None, SwitchPartForeign = None; Initial = None. Die Attribute koennen spaeter mit dem jeweiligen Inhalt ueberschrieben werden.

#### InsertWord.insert_string (self, InTree, NumberWord)

InsertWord: Wort, das in den Baum eingefuegt werden soll.

##### Parameter
- **InTree**: Baum, in den der Satz gehangen wird.
- **NumberWord**: Nummer des Worts im Satz, der in den Baum gehangen wird.

*Fuegt ein einzelnes Wort mit einer laufenden Nummer in den Baum ein.*
>Das einzufuegende Wort wird mit den Attributen in den Baum auf der dritten Ebene eingefuegt. Handelt es sich um das erste Wort, wird NodeContent mit dem einzufuegenden Wort und NumberWord mit '1' ueberschrieben. Ab den folgenden Worten muss zuerst ein neuer Knoten initiiert werden und anschließend der Zeiger des vorherigen Wortes auf den neuen Knoten gestellt werden: WortPredecessor.NodeRight = NodeNeu.

#### WordToSplit.split_string (self)**  

WordToSplit: Wort, das aufgeteilt werden soll.

*Teilt das jeweilige Wort in mehrere Wortbestandteile auf* | Methode wird ueberschrieben  
>Es werden zwei Marker benötigt, einer für den Wortbestandteilanfang und einer für das Wortbestandteilende. Wechselt der aktuelle Buchstabe von Vokal zu Konsonant oder Satzzeichen oder Sonstige - oder umgekehrt, wird der aktuelle Wortbestandteil abgeschnitten und als String in einen Baum gehangen. Der Marker für den Wortbestandteilanfang wird auf die neue Textstelle (Wortbestandteilende + 1) verschoben. Anschließend geht die Überprüfung an der Stelle weiter. Die Marker für Wortbestandteilanfang (WordElementStart) und Satzende (WordElementEnd) sind Variablen, die nur in der Funktion benötigt werden. Es wird eine interne Variable NumberElement (Typ: int) eingesetzt, die die laufende Nummer des Wortbestandteils abspeichert und mit in den Baum überträgt -> Methode: insert_wordelement (self, NumberElement). Damit können später die einzelnen Wortbestandteile gezielt angesteuert werden.


## Parts (Words)
Enthaelt die einzelnen Bestandteile des Wortes, z.B. St|e|f|a|n
Aufbau im Modul `M_Edit`.

### Attribute
- **NodeContent**: Inhalt des Knotens
- **NodeDown**: Zeiger zu tiefer gelegenen Ebene
- **NodeRight**: Zeiger auf den naechten Inhalt in der gleichen Ebene
- **InTree**: Baum, in den der Satz gehangen wird.
- **NumberPart**: Nummer des Worts im Satz, der in den Baum gehangen wird.

### Methoden

#### PartNode.init__ (self)

PartNode: Knoten fuer den Wortbestandteil, der erzeugt werden soll.

*Erzeugt einen Knoten fuer den Baum*
>Fuer den Inhalt des Knotens wird mit NodeContent = '' ein leerer String angelegt, die Zeiger werden auf 'None' gesetzt: NodeDown = None und NodeRight = None. Die Attribute koennen spaeter mit dem jeweiligen Inhalt ueberschrieben werden.

#### InsertPart.insert_string (self, InTree, NumberPart)

InsertPart: Wortbestandteil, der in den Baum gehangen werden soll.

##### Parameter
- **InTree**: Baum, in den der Satz gehangen wird.
- **NumberPart**: Nummer des Worts im Satz, der in den Baum gehangen wird.

*Fuegt einen einzelnes Wort mit einer laufenden Nummer in den Baum ein.*
>Der einzufuegende Teil wird mit den Attributen in den Baum auf der vierten Ebene eingefuegt. Handelt es sich um den ersten Teil, wird NodeContent mit dem einzufuegenden Teil und NumberPart mit '1' ueberschrieben. Ab den folgenden Teilen muss zuerst ein neuer Knoten initiiert werden und anschließend der Zeiger des vorherigen Wortes auf den neuen Knoten gestellt werden: WortPredecessor.NodeRight = NodeNeu.

-----------------------

## WordsAnalyze (Words)
*Bildet die Klasse ab, mit der die Analyseprozesse auf Satzbestandteilebene durchgeführt werden.*
Aufbau im Modul `M_Analyze`.

### Attribute
- xxx

### Methoden
#### check (self, WordToBeAnalyzed)  
##### Parameter
- **WordToBeAnalyzed**: Wort, fuer das die Checks durchgefuehrt werden sollen.

*Steuert die gesamten Überprüfungsprozess, z.B. Großschreibung am Wortanfang, beim jeweiligen Wort:*
>Die Methode ruft nach und nach die durchzufuehrenden Einzelchecks auf. Anschließend werden die Ergebnisse der Checks in die Attribute des jeweiligen Wortes geschrieben, z.B. Capital = True, falls das Wort mit einem Großbuchstaben beginnt. Ausserdem muss vor der Suche nach moeglichen Tauschpartnern in der Nachbarschaft zuerst die Buchstabenklasse ermittelt werden. Es werden auf jeden Fall alle moeglichen Checks fuer ein Wort durchgefuehrt, damit zukuenftige Erweiterungen einfacher umgesetzt werden koennen.

#### check_swap_allowed (self, WordToBeAnalyzed)
##### Parameter
- **WordToBeAnalyzed**: Wort, fuer das die Ueberpruefung, ob es zum Tausch herangezogen werden darf, durchgefuehrt werden soll.

*Ueberprueft, ob das jeweilige Wort ueberhaupt zum Tausch herangezogen werden darf.*
>Fuer das Wort erfolgt ein Abgleich, ob es in einer der Wort-Mengen, z.B. Artikel, ist, die nicht zum Tausch herangezogen werden duerfen. Falls getauscht werden darf, wird 'SwapAllowed' mit 'True' zurueckgeliefert, sonst mit 'False'.

#### check_capital (self, WordToBeAnalyzed)
##### Parameter
- **WordToBeAnalyzed**: Wort, fuer das die Ueberpruefung auf einen Grossbuchstaben durchgefuehrt werden soll.

*Ueberprueft, ob das jeweilige Wort mit einem Grossbhuchstaben anfaengt*
>Fuer das Wort erfolgt ein Abgleich, ob es mit einem Grossbuchstaben (Funktion 'capital') beginnt. Falls das der Fall ist, wird 'Capital' mit 'True' zurueckgeliefert, sonst mit 'False'.

#### check_equal (self, WordToBeAnalyzed, LetterClass, Range)
##### Parameter
- **WordToBeAnalyzed**: Wort, fuer das die Ueberpruefung, ob ein anderes passendes Wort innerhalb der Spanne vorliegt, durchgefuehrt werden soll.
- **LetterClass**: Buchstabengruppe, nach der Woerter in der Nachbarschaft ueberprueft werden sollen.
- **Range**: Spanne innerhalb der gesucht werden soll.

*Ueberprueft, ob fuer das jeweilige Wort ein Tauschpartner innerhalb der Spanne vorliegt.*
>Fuer das Wort erfolgt ein Abgleich, ob sich innerhalb der vorgegebenen Spanne er Wort, das mit der gleichen Buchstabenart beginnt vorliegt. Falls ja, wird 'Equal' mit 'True' zurueckgeliefert, sonst mit 'False'. Die Ueberpruefung findet ab dem direkten Wortnachbarn rechts statt. Das Nummer des ersten Wortes innerhalb der Spanne, das mit der gleichen Buchstabengruppe beginnt, im Attribut 'SwitchPartForeign' unter 'NumberWord' festgehalten, 'NumberPart' wird dann direkt auf '1' gesetzt, da es sich um den ersten Teil des Wortes handelt. Falls die Spanne '0' ist, wird innerhalb desselben Wortes gesucht. Oder: Falls innerhalb der vorgegebenen Spanne kein passender Tauschpartner gefunden wird, wird die Spanne auf '0' gesetzt (NOCH ZU KLAEREN)

## PartsAnalyze (Parts)
*Bildet die Klasse ab, mit der die Analyseprozesse auf Wortbestandteilebene durchgeführt werden.*
Aufbau im Modul `M_Analyze`.

### Attribute
- xxx

### Methoden
#### check_initial (self, WordToBeAnalyzed)
##### Parameter
- **WordToBeAnalyzed**: Wort, fuer das die Ueberpruefung, mit welcher Buchstabenklasse es beginnt, durchgefuehrt werden soll.

*Ueberprueft, mit mit welcher Buchstabenklasse das Wort beginnt, z.B. Vokale).*
>Zur Ueberpruefung wird der erste Wortbestandteil herangezogen und mit den entsprechenden Mengen, die ueber die Config-Datei eingelesen wurden, abgeglichen. Die Methode liefert dann als Ergebnis die Buchstabenklasse zurueck. Diese wird ueber die Methode 'check' in die Attribute des Worts ueberspielt.

-----------------------

### CombinationList
#### Methoden
- **insert**: Fuegt eine neue Wortkombination mit der Gesamtpunktzahl in die Liste ein.
- **delete**: Loescht eine Wortkombination aus der Liste.
- **sort**: Sortiert die Liste nach der Gesamtpunktzahl. Algorithmus: Bubble-Sort.
- **rank_list (Word1:Part1, Word2:Part2, Points)**: Sortiert die Liste aus Kombinationen in die richtige Reihenfolge, gemessen an der Gesamtpunktzahl pro Kombination. Anschließend gibt die Funktion die Daten der am höchsten bewerteten Kombination zurück: Word1:Part1, Word2:Part2 / Regeln: An die Funktion rank_list werden die entsprechenden Daten zu den Kombinationen uebergeben und in eine Liste geschrieben. Sollten keine weiteren Kombinationen zur Verfügung stehen, wird die Funktion noch einmal aufgerufen, aber mit den Argumenten 'None:None', 'None:None', '0'. Die Funktion uberprueft zuerst ob diese Werte uebergeben wurden. Falls nein, werden die Werte in eine Liste geschrieben. Falls ja, startet die Sortierung der Liste und die Daten der Kombination mit der hoechsten Punktezahl wird zurueckgegeben.


### Combination

#### Attribute
- SumPoints: Gesamtpunktzahl der Kombination für das Ranking.
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

-----------------------

### TextOutput (Strings)
Aufbau im Modul M_Output

#### Attribute

#### Methoden

-----------------------------

## Funktionen



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

## Variablen

### Global

Text = Trees
InputText = TextInput
OutputText = TextOutput

### kurzzeitig einsetzbar
- Counter: benoetigt für Zaehloperationen in Schleifen



 
 #### *Attributes*
 - SwapAllowed: True/False
 - ConnectedWith: Number
 - Capital: True/False
 - SwitchPartOwn: Number
 - SwitchPartForeign: Number
 - Initial: Stock
 
 
