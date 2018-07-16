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
text | string | The text to normalize

```json
{
	"token":"...",
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
sentences | array of strings | The sentences to normalize

```json
{
	"token":"...",
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
sentences | string | The sentences to normalize

```json
{
	"token":"...",
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
word | array of strings | The words to normalize

```json
{
	"token":"...",
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
