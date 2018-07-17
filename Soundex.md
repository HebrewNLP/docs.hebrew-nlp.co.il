# Soundex

The Soundex returns a possible phonetic codes for both Hebrew and English words, it is intended to work with names but will also work on any other english/hebrew word.

You might get multiple phonetic codes since some words could be pronounced in different ways.

## Endpoint
https://hebrew-nlp.co.il/service/soundex

## Parameters
Field | Type | Description
------|------|-------------
token | string | The token/password, sent in sms when you register
words | array of strings | The words to soundex

```json
{
    "token": "...",
    "words": [
        "ג'ורג'",
        "George"
    ]
}
```

## Returns 
JSON array of string arrays, each element represents phonetic code.

```json
[
    [
        "4607852",
        "1487623169"
    ],
    [
        "1487623169"
    ]
]
```

As you can see the two words are probably similar because both have the phonetic code of `1487623169`