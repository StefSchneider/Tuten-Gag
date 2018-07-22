# Documentation of modules and toolboxes

## Modules

### Module M_Config.py

#### Description
This module is reponsible for loading and including all data of the config file, f.e. pathes, groups or data for implementing the rules.

#### Classes
- **ConfigData**: Includes all data that is part of the cofig file.
- **Stocks (ConfigData)**: Includes groups of letters or groups, f.e. vowels or articles.

#### Methods
- **Stocks.initiate**: Generates a new stock, f.e. a set, a list, a dictionary or a string.
- **Stocks.add_to**: Adds a component from the config file to the stock.
- **Stocks.serach_in**: Checks, wether is component is part of a stock.

[more...](https://github.com/stefschneider1970/Tuten-Gag/blob/master/classes%2C%20methods%20and%20functions.md#configdata "See more about this classes and methods")  


### Module M_Dictionaries.py

#### Description
The module M_Dictionaries is reponsible for loading or saving all dictionaries from or into an avl tree.

#### Classes
- **Dictionaries**: All kind of dictionaries that is used in the program, f.e. German, Austrian, Foreign.

#### Methods
- **Dictionaries.load**: Adds all component from a dictionary file in a dictionary avl tree.
- **Dictionaries.save**: Saves all components from a dictionary avl tree in a dilctionary file.
- **Dictionaries.check_size**: Checks the size of a dictionary file.
- **Dictionaries.check_status**: Calculates the status of loading the dictionary file into the dictionary avl tree.

[more...](https://github.com/stefschneider1970/Tuten-Gag/blob/master/classes%2C%20methods%20and%20functions.md#dictionaries "See more about this classes and methods")

### Module M_Menu.py

#### Description

#### Classes

#### Methods


### Module M_Input.py

#### Description
This module is responsible for recording the text filled in by the user in all different ways, f.e. via keyboard or voice assistant.

#### Classes
- **Strings**: Includes all kind of strings filled in by the users and splitted, f.e. texts or sentences.
- **TextInput (Strings)**: Includes the text, that is filled in by the user in all diferent ways.

#### Methods
- **TextInput.--init--**: Generates a new data structure tree to collect all parts of the text, f.e. sentences or words. 
- **TextInput.insert_string**: Inserts the complete text into the root of the tree.

[more...](https://github.com/stefschneider1970/Tuten-Gag/blob/master/classes%2C%20methods%20and%20functions.md#strings "See more about this classes and methods")

### Module M_Edit.py

#### Description
This module is responsible for splitting the text into all parts od check the attributes, f.e. whether all words are containing in the language.

#### Classes
- **TextEdit (TextInput)**: Includes the text to be edited by the program.
- **Sentences (TextEdit)**: Includes all sentence contained in a text.
- **Words (Sentences)**: Includes all words containdes in a sentence.
- **Parts (Words)**: Includes all parts of a word contained in a word.

#### Methods
- **TextEdit.--init--**: Generates a new child node for the data structure tree.
- **TextEdit.generate_node**: Generates a new pointer to the new child node for a sentence.
- **TextEdit.split_string**: Splits the text into sentences.
- **Sentences.--init-**: Generates a new child node for the data structure tree.
- **Sentences.generate_node**: Generates a new pointer to the new child node for a word.
- **Sentences.split_string**: Splits the curremt sentence into words.
- **Sentences.check_word**: Checks wether all words are containing in the dictionaries
- **Words.--init-**: Generates a new child node for the data structure tree.
- **Words.generate_node**: Generates a new pointer to the new child node for a part of the word.
- **Words.split_string**: Splits the current word into all parts.
- **Words.check**: Steers all checks of the current word.
- **Words.check_swap_allowed**: Checks whether a swap is possibe or not.
- **Words.check_capital**: Checks whether the current word starts with a capital.
- **Parts.--init-**: Generates a new child node for the data structure tree.
- **Parts.generate_node**: Generates a new pointer to the new child node for a part of a word.

[more...](https://github.com/stefschneider1970/Tuten-Gag/blob/master/classes,%20methods%20and%20functions.md#textedit-textinput "See more about this classes and methods")


### Module M_Analyze.py

#### Description

#### Functions


### Module M_Combine.py

#### Description

#### Functions


### Module M_AI.py

#### Description

#### Functions


### Module M_Rating.py

#### Description

#### Functions


### Module M_Build.py

#### Description

#### Functions


### Module M_Output.py

#### Description

#### Functions



## Tollboxes

### AVLTree

#### Description

#### Functions


