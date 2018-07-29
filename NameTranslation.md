# English-Hebrew Name Translation

The service allows you to enter a name in english and get it's translation in Hebrew.


## Endpoint
https://hebrew-nlp.co.il/service/translation/names

## Parameters
Field | Type | Description
------|------|-------------
token | string | The token/password, sent in sms when you register
threshold | int | The "range" for searching the correct name, 1 or 0 will return the best translation 
type | enum as strong | The language 
words | array of strings | The words to translate

```json
{
    "token": "...",
    "threshold": 1,
    "type": "HEBREW",
    "words": [
        "haim",
        "haym"
    ]
}
```

## Returns 
JSON array of string arrays, each element represents a possible translation.

```json
[
    [
        "חיים"
    ],
    [
        "חיים"
    ]
]
```