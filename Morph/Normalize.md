# Normalize

This API allows you to normalize words in Hebrew. 

Normalization allows you to take words with different permutations and normalize them into a single common word.

For example:
1. ילדים
2. ילדיהם
3. הילד
4. הילדה

will all turn into `ילד`

## Endpoint
https://hebrew-nlp.co.il/service/morphology/normalize

## Parameters
There are 4 parameter sets you can use

### To run sentencer and tokenizer on text and then normalize each word per sentence
Field | Type | Description
------|------|-------------
token | string | The token/password, sent in sms when you register
type | enum as string | The nomralization type
text | string | The text to normalize

```json
{
	"token":"...",
	"type": "SEARCH",
	"text": "שלום מה שלומך?\nהכל בסדר."
}
```

this will return array of sentences where each is an array of strings
```json
[
	[
		"שלומ",
		"מה",
		"שלומ",
		"?"
	],
	[
		"כל",
		"סדר",
		"."
	]
]
```

### To run tokenizer on each sentence and then normalize each word per sentence
Field | Type | Description
------|------|-------------
token | string | The token/password, sent in sms when you register
type | enum as string | The nomralization type
sentences | array of strings | The sentences to normalize

```json
{
	"token":"...",
	"type": "SEARCH",
	"sentences": [
		"שלום מה שלומך?",
		"הכל בסדר."
	]
}
```

this will return array of sentences where each is an array of strings
```json
[
	[
		"שלומ",
		"מה",
		"שלומ",
		"?"
	],
	[
		"כל",
		"סדר",
		"."
	]
]
```

### To run tokenizer on a sentence and then normalize each word
Field | Type | Description
------|------|-------------
token | string | The token/password, sent in sms when you register
type | enum as string | The nomralization type
sentences | string | The sentences to normalize

```json
{
	"token":"...",
	"type": "SEARCH",
	"sentence": "הילד שהלך לפרק ישב"
}
```

this will return array of strings:
```json
[
	"ילד",
	"הלכ",
	"פרק",
	"ישב"
]
```

### To run normalizer on each word
Field | Type | Description
------|------|-------------
token | string | The token/password, sent in sms when you register
type | enum as string | The nomralization type
word | array of strings | The words to normalize

```json
{
	"token":"...",
	"type": "SEARCH",
	"sentence": [
		"הילד",
		"שהלך",
		"לפרק",
		"ישב"
	]
}
```

this will return array of strings:
```json
[
	"ילד",
	"הלכ",
	"פרק",
	"ישב"
]
```

## Normalization Types
### INDEX
This is used when you want to index text in a database, it will return all the normalization options so the search will be as accurate as possible

For example:

```json
{
    "token": "tQzDuMV9h9b07ek",
    "type": "INDEX",
    "sentence": "מהנדסת"
}
```

will return:
```json
[
    "מהנדס",
    "הנדסה"
]
```

### SEARCH
This is the simplest normalization type, it will return only one option, but when searching against indexed text using the INDEX normalization type, it will most probably find the correct match.