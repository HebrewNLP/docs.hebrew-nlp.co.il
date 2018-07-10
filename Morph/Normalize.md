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
Field | Type | Description
------|------|-------------
token | string | The token/password, sent in sms when you register
words | array of strings | The words to normalize

### Example
```json
{
	"token":"...",
	"words": ["הילד", "שהלך", "לפרק", "ישב"]
}
```

## Returns
JSON array of strings

### Example
```json
["ילד", "הלכ", "פרק", "ישב"]
```