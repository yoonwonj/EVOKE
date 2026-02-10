# Korean–English Mapping Dataset
This dataset contains many-to-many translation mappings between Korean and English emotion words.

## Variables / Columns
| Column Name      | Description                                                                           | Type    | Values / Notes                                                                |
| ---------------- | ------------------------------------------------------------------------------------- | ------- | ----------------------------------------------------------------------------- |
| `Korean_Word`    | Korean word                                              | String  | empty if no equivalent exists                           |
| `English_Word`   | English word                                             | String  | empty if no equivalent exists                           |
| `Translational_Equivalence`    | Indicates whether the word has a cross-lingual gap                                    | Integer | `0` = no gap (translational equivalents exist) <br> `1` = gap (no direct equivalent exists) |
| `POS` | Part of speech of the source word                                                     | String  | `noun`, `adjective`, and `verb`.                                                   |
| `Notes`          | Additional information on idiomatic expressions, dictionary glosses, or special cases | String  |                                             |
| `Korean_Source1`          | The source of Korean word | String  |  `Park_Min_2005`, `Rhee_Ko_2013`, `KOTE`                                           |
| `Korean_Source2`          | Additional source of Korean word if a word appears in more than two sources | String  | `Park_Min_2005`, `Rhee_Ko_2013`, `KOTE`                                            |
| `English_Source1`          | The source of English word | String  | `Baron-Cohen_2010`, `Morgan_Heise_1988`, `Storm_Storm_1987`                                            |
| `English_Source2`          | Additional source of English word if a word appears in more than two sources | String  | `Baron-Cohen_2010`, `Morgan_Heise_1988`, `Storm_Storm_1987`                                            |

## Notes on Word Selection
1. Korean (Jeon et al., 2022; Park and Min, 2005; Rhee and Ko, 2013) and English (Baron-Cohen et al., 2010; Morgan and Heise, 1988; Storm and Storm, 1987) words are extracted from previous work on emotion words.
2. Word entries that are not noun, verb, or adjectives were excluded (e.g. Rhee and Ko, 2013 included a lot of slangs and interjections).

## Notes on Translation Mappings
1. Each row indicates a pair of Korean-English words that are translationally equivalent.
2. Multiple were created for the source words if there are multiple corresponding target words, and likewise when a target word corresponds to multiple source words. 

## Notes on Lexical Gaps
1. Collocations and free-form expressions are not considered as single lexical entries:
    - Entries consisting of more than two words are identified as gap words by default (coded as 1). 
    - Hyphenated forms, however, are treated as single lexical items and are not considered gap words (coded as 0), e.g., *cliché-ridden*.
    - Korean words that are used both as single words and as multi-word with a space bar in between two words were left as a single entry: *'깜짝 놀란'*, *'신이 난'*, *'눈물 어린'*, *'겁에 질린'*, *'겁이 많은'*, *'사려 깊은'*, *'수배 중인'*, *'가슴 시린'*
2. Gaps identified in this dataset are restricted to semantic gaps. 
only the gaps exhibiting meaningful conceptual differences were coded as 0
    - Verb entries with *be-* constructions, noun entries with *being-* constructions, and noun entries with *sense of-* constructions are not coded as gaps (coded as 1)
    - Idioms and conventionalized collocations are identified as gaps; corresponding idiomatic expressions are recorded in the Note column.
    - Entries without established idiomatic expressions in the target language (i.e. free-form experessions), dictionary-definition-based glosses written in the target language are provided in the Note column.
3. Since gap words do not have direct target-language equivalents, multiple rows were created to represent different meanings of the same source word, based on dictionary entries.
