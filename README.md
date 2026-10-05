# Mongolian Lexical Dataset Schema

This document describes the schema used by the Mongolian Lexical Dataset.

## Entry Structure

```json
{
  "id": "",
  "lemma": "",
  "normalized": "",
  "pos": "",
  "pronunciation": "",
  "transliteration": "",
  "senses": [
    {
      "sense_id": 1,
      "definitions": {
        "mn": [],
        "en": []
      },
      "translations": {
        "en": [],
        "ru": [],
        "zh": []
      },
      "examples": [],
      "synonyms": [],
      "antonyms": [],
      "domain": "",
      "frequency": null,
      "register": "neutral"
    }
  ],
  "morphology": {},
  "etymology": "",
  "tags": [],
  "source": "",
  "license": "",
  "created_at": "",
  "updated_at": ""
}
```

---

# Field Definitions

## id

Permanent unique identifier for the lexical entry.

### Example

```json
"id": "mng_000001"
```

### Rules

- Must be unique.
- Must never be reused.
- Must remain unchanged after creation.

---

## lemma

The canonical dictionary form (headword) of the word.

### Examples

```json
"морь"
"харах"
"сайн"
```

---

## normalized

Machine-readable normalized form of the lemma.

Used for:

- Search
- Indexing
- Deduplication
- NLP processing

### Example

```json
"морь"
```

---

## pos

Part of speech.

### Allowed Values

```text
noun
verb
adjective
adverb
pronoun
numeral
particle
postposition
conjunction
interjection
abbreviation
proper_noun
```

### Example

```json
"noun"
```

---

## pronunciation

Word pronunciation represented using IPA (International Phonetic Alphabet).

### Example

```json
"mɔrʲ"
```

---

## transliteration

Latin-script representation of the Mongolian word.

### Example

```json
"mor'"
```

---

# Senses

A single word may have multiple meanings.

Each meaning is stored as a separate sense object.

Example:

```text
гар
 ├─ hand
 ├─ handle
 └─ skill
```

---

## sense_id

Unique identifier of a meaning within the entry.

### Example

```json
1
```

---

## definitions.mn

Dictionary-style definition in Mongolian.

### Example

```json
[
  "Хүний мөрнөөс хурууны үзүүр хүртэлх дээд мөч."
]
```

### Notes

- Should explain meaning.
- Should not be a synonym.

---

## definitions.en

Dictionary-style definition in English.

### Example

```json
[
  "The upper limb of a human body extending from the shoulder to the fingers."
]
```

---

## translations

Closest equivalent words in another language.

Translations are not definitions.

---

### translations.en

English translations.

### Example

```json
["horse"]
```

---

### translations.ru

Russian translations.

### Example

```json
["лошадь"]
```

---

### translations.zh

Chinese translations.

### Example

```json
["马"]
```

---

## examples

Real-world usage examples associated with the specific sense.

### Example

```json
[
  {
    "mn": "Тэр хурдан морь унадаг.",
    "en": "He rides a fast horse."
  }
]
```

### Guidelines

- Examples must match the current sense.
- Prefer natural modern language.

---

## synonyms

Words with similar meaning within the same sense.

### Example

```json
[
  "ажнай"
]
```

---

## antonyms

Words expressing opposite meaning.

### Example

```json
[
  "муу"
]
```

---

## domain

Subject area where the sense is used.

### Examples

```text
general
technology
medicine
finance
law
education
politics
mathematics
military
religion
culture
sports
```

### Example

```json
"technology"
```

---

## frequency

Relative usage frequency of the sense.

### Suggested Scale

```text
100 = extremely common
80  = common
60  = frequent
40  = uncommon
20  = rare
5   = archaic
```

### Example

```json
95
```

---

## register

Speech or writing style associated with the sense.

### Allowed Values

```text
neutral
formal
informal
slang
literary
technical
archaic
honorific
vulgar
```

### Example

```json
"neutral"
```

---

# Linguistic Metadata

## morphology

Grammatical and inflectional information.

### Noun Example

```json
{
  "plural": "морьд",
  "genitive": "морийн",
  "dative": "моринд",
  "accusative": "морийг",
  "ablative": "мориноос",
  "instrumental": "мориор"
}
```

### Verb Example

```json
{
  "past": "харсан",
  "present": "харж байна",
  "future": "харна",
  "imperative": "хар",
  "participle": "харах"
}
```

---

## etymology (Not Required, Nice to have.)

Historical origin of the word.

### Examples

```json
"Proto-Mongolic origin"
```

```json
"Borrowed from Tibetan"
```

```json
"Borrowed from Russian"
```

```json
"Borrowed from English"
```

---

## tags

Flexible labels for searching, filtering, and categorization.

### Examples

```json
[
  "animal",
  "livestock",
  "culture"
]
```

```json
[
  "technology",
  "computer"
]
```

---

# Administrative Metadata

## source

Source from which the entry was obtained.

### Examples

```json
"Mongolian Explanatory Dictionary"
```

```json
"Wiktionary"
```

```json
"Community Contribution"
```

```json
"Manual Annotation"
```

---

## license

License governing the entry.

### Examples

```json
"CC-BY-4.0"
```

```json
"CC-BY-SA-4.0"
```

```json
"ODC-BY"
```

```json
"Public Domain"
```

---

## created_at

Date the entry was created.

### Format

```text
YYYY-MM-DD
```

### Example

```json
"2026-10-05"
```

---

## updated_at

Date the entry was last modified.

### Format

```text
YYYY-MM-DD
```

### Example

```json
"2026-10-05"
```

---

# Recommended Optional Fields

```json
{
  "status": "verified"
}
```

### Allowed Values

```text
draft
reviewed
verified
deprecated
```

---

# Design Principles

- One entry per lemma.
- One sense per meaning.
- Definitions explain meaning.
- Translations provide equivalent words.
- Examples should be natural and contextual.
- Morphology should be included whenever available.
- Entries should be UTF-8 encoded.
- Dates should use ISO-8601 format (`YYYY-MM-DD`).
