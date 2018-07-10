# Analyze

This API allows you to morpholoicaly analyze words in Hebrew. 

Analyzation gives you:
1. Part Of Speech (חלק דיבור)
2. Vav (ו' החיבור)
3. Shiabud (שיעבוד)
4. Prepositions (אותיות יחוס) 
5. Definitive article (ה' הידיעה)
6. Gender (מין)
7. Plural (מספר)
8. Person (גוף)
9. Smikut (סמיכות)
10. Tense (זמן)
11. Suffix (ownership) gender, plural and person (שיכות)

## Endpoint
https://hebrew-nlp.co.il/service/morphology/normalize

## Parameters
Field | Type | Description
------|------|-------------
token | string | The token/password, sent in sms when you register
words | array of strings | The words to analyze

### Example
```json
{
	"token":"...",
	"words": ["מילה"]
}
```

## Returns
JSON array of objects:

Field | Type | Description
------|------|-------------
BaseWord | string | The normalized word
Vav | boolean | Has vav?
Shaibud | enum as string |
PrepositionChars | enum as string | 
DefiniteArticle | boolean | has difinitive article
PartOfSpeech | enum as string | 
Gender | enum as string | 
Plural | boolean | Is Plural (true) or Single (false)
Person | enum as string | 
Smikut | enum as string | 
Tense | enum as string | 
SuffixGender | enum as string | 
SuffixPlural | enum as string | 
SuffixPerson |  enum as string | 

### Shaibud
1. NONE (אף אחד)
2. SHE (ש...)
3. KSHE (כש...)
4. LEKSHE (לכש...)
5. SHEKSHE (שכש...)
6. HA (ה...)
7. SHEHA (שה...)

### PrepositionChars
1. NONE (אף אחד)
2. BET (ב)
3. MEM (מ)
4. LAMED (ל)
5. KAF (כ)

### PartOfSpeech
1. NONE (אין)
2. VERB (פועל)
3. NOUN (עצם)
4. ADJECTIVE (תואר)
5. NUMBER (מיספר)
6. PREPOSITION (מילת יחס)
7. PRONOUN (מילת גוף)
8. QUESTION_WORD (מילת שאלה)
9. CONJUNCTION (מילת חיבור)
10. PARTICLE (מילית)
11. ADVERB (תואר הפועל)
12. MODAL (פועל עזר)
13. PROPER_NOUN (שם פרטי)

### PartOfSpeech
1. NONE (אף אחד)
2. MALE (זכר)
3. FEMALE (נקבה)

### Person
1. FIRST_PERSON (גוף ראשון)
2. SECOND_PERSON (גוף שני)
3. THIRD_PERSON (גוף שלישי)

### Smikut
1. NONE (אין)
2. NIFRAD (נפרד)
3. NISMAK (נסמך)

### Tense
1. NONE (אין)
2. PAST  (עבר)
3. PRESENT (הווה)
4. FUTURE (עתיד)
5. PRESENT_PASSIVE (הווה סביל (פעול))
6. IMPERATIVE (ציווי)
7. INFINITIVE (מקור)