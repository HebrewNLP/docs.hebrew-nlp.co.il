# Tokenizer

This API allows you to split text/sentences into words.

## Endpoint
https://hebrew-nlp.co.il/service/preprocess/tokenizer

## Parameters
There are three types of parameter sets you can give:

### To run sentencer and tokenizer per sentence

Field | Type | Description
------|------|-------------
token | string | The token/password, sent in sms when you register
text | string | The text to tokenize

```json
{
    "token": "...",
    "text": "שלום מה נשמע? הכל בסדר"
}
```

will return an array of array of tokens:
```json
[
    [
        "שלום",
        "מה",
        "נשמע",
        "?"
    ],
    [
        "הכל",
        "בסדר"
    ]
]
```

### To run on sentences tokenizer per sentence

Field | Type | Description
------|------|-------------
token | string | The token/password, sent in sms when you register
sentences | array of string | The sentences to tokenize

```json
{
    "token": "...",
    "sentences": [
        "שלום מה נשמע?",
        "הכל בסדר"
    ]
}
```

will return an array of array of tokens:
```json
[
    [
        "שלום",
        "מה",
        "נשמע",
        "?"
    ],
    [
        "הכל",
        "בסדר"
    ]
]
```

### To run tokenizer on a single sentence

Field | Type | Description
------|------|-------------
token | string | The token/password, sent in sms when you register
sentence | string | The sentence to tokenize


```json
{
    "token": "...",
    "sentence": "שלום מה נשמע?"
}
```

this will return array of tokens:
```json
[
    "שלום",
    "מה",
    "נשמע",
    "?"
]
```