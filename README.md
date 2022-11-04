# english-dictionary
A dictionary database containing definitions and examples for over 50,000 English words. This data was dumped from the [Free Dictionary API](https://dictionaryapi.dev/) using [this word list](http://www.mieliestronk.com/wordlist.html).

### [Download from Releases](https://github.com/CyberGen49/english-dictionary/releases)

## Database structure
### Table `word_list`
Contains a single entry for every word in the database.
* Column `word`: The word

### Table `phonetics`
Contains phonetic pronounciations. Not all words have pronounciations. Some words may have multiple entries.
* Column `word`: The word
* Column `phonetic`: The word's pronetic pronounciation

### Table `meanings`
Contains definitions and examples for words. Most words will have multiple entries.
* Column `word`: The word
* Column `part_of_speech`: The word's part of speech
  * Possible values: `noun`, `adverb`, `preposition`, `verb`, `adjective`, `interjection`, `conjunction`, `pronoun`, `numeral`, `proper noun`
* Column `definition`: The word's definition
* Column `example`: An example using this word in a sentence, or `null`

### Table `related`
Contains synonyms and antonyms for words. Words may have no entries, a single entry, or many entries.
* Column `word`: The word
* Column `relation`: Either `synonym` or `antonym`
* Column `target`: The related word or phraise

### Table `audio`
Contains URLs to audio pronounciations of words. Not all words have audio files. Some words may have multiple entries.
* Column `word`: The word
* Column `url`: The audio file URL

## Download formats
### SQLite
The **sqlite3_dump.sql** file can be imported into an existing database using the `.read` command.

### CSV
Each of the available CSV files corresponds to one of the tables listed above, using the same column names.

### JSON
The **dump_by_table.json** file contains an array for each table, where each array element corresponds to an entry and contains properties matching that entry's columns.

The **dump_by_words.json** file contains an object for each word:
```json
"word": {
  "phonetics": "Array",
  "meanings": [
    {
      "part_of_speech": "String",
      "definition": "String",
      "example": "String|null"
    }
  ],
  "related": {
    "synonyms": "Array",
    "antonyms": "Array"
  },
  "audio": "Array"
}
```

The **_pretty** versions of these JSON files are formatted and intended for human readability.
