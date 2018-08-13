# Cities Named Entity Recognition

This API allows you to tag words in a text as cities.

The service can also distinguish between real city names and city names that are a part of a phrase, for example `מעגלים` is a name of a city, but it can also be part of the phrase `מעגלים חשמליים`. The service knows that and will not return it as a city name if it is part of another phrase.

## Endpoint
https://hebrew-nlp.co.il/service/ner/cities

## Token  

Field | Type | Description
------|------|-------------
Type | enum as string | The type of the token
Token | string | The token itself
Entity | string | A normalized Entity of the Token (Like a name), only appears on `CITY` tokens 

## TokenType

- CITY
- WORD


## Parameters
There are 4 parameter sets you can use

### To run sentencer and tokenizer on text and then run the ner for each sentence
Field | Type | Description
------|------|-------------
token | string | The token/password, sent in sms when you register
text | string | The text to ner

```json
{
    "token": "...",
    "text": "אני לומד בתל אביב. אבל אני גר במודיעין."
}
```

this will return array of sentences where each is an array of tokens
```json
[
    [
        {
            "Token": "אני",
            "Type": "WORD"
        },
        {
            "Token": "לומד",
            "Type": "WORD"
        },
        {
            "Token": "בתל אביב",
            "Entity": "תל אביב יפו",
            "Type": "CITY"
        },
        {
            "Token": ".",
            "Type": "WORD"
        }
    ],
    [
        {
            "Token": "אבל",
            "Type": "WORD"
        },
        {
            "Token": "אני",
            "Type": "WORD"
        },
        {
            "Token": "גר",
            "Type": "WORD"
        },
        {
            "Token": "במודיעין",
            "Entity": "מודיעין מכבים רעות",
            "Type": "CITY"
        },
        {
            "Token": ".",
            "Type": "WORD"
        }
    ]
]
```

### To run tokenizer on each sentence and then run the ner for each sentence
Field | Type | Description
------|------|-------------
token | string | The token/password, sent in sms when you register
sentences | array of strings | The sentences to ner

```json
{
    "token": "...",
    "sentences": [
        "אני לומד בתל אביב",
        "אבל אני גר במודיעין"
    ]
}
```

this will return array of sentences where each is an array of tokens
```json
[
    [
        {
            "Token": "אני",
            "Type": "WORD"
        },
        {
            "Token": "לומד",
            "Type": "WORD"
        },
        {
            "Token": "בתל אביב",
            "Entity": "תל אביב יפו",
            "Type": "CITY"
        }
    ],
    [
        {
            "Token": "אבל",
            "Type": "WORD"
        },
        {
            "Token": "אני",
            "Type": "WORD"
        },
        {
            "Token": "גר",
            "Type": "WORD"
        },
        {
            "Token": "במודיעין",
            "Entity": "מודיעין מכבים רעות",
            "Type": "CITY"
        }
    ]
]
```

### To run tokenizer on a sentence and then run the ner
Field | Type | Description
------|------|-------------
token | string | The token/password, sent in sms when you register
sentences | string | The sentences to ner

```json
{
    "token": "...",
    "sentence": "יש מסיבה בתל אביב ומודיעין"
}
```

this will return array of tokens:
```json
[
    {
        "Token": "יש",
        "Type": "WORD"
    },
    {
        "Token": "מסיבה",
        "Type": "WORD"
    },
    {
        "Token": "בתל אביב",
        "Entity": "תל אביב יפו",
        "Type": "CITY"
    },
    {
        "Token": "ומודיעין",
        "Entity": "מודיעין מכבים רעות",
        "Type": "CITY"
    }
]
```

### To run ner on a sentence pre-tokenized
Field | Type | Description
------|------|-------------
token | string | The token/password, sent in sms when you register
word | array of strings | The words to ner

```json
{
    "token": "...",
    "words": [
        "יש",
        "מסיבה",
        "בתל",
        "אביב",
        "ומודיעין"
    ]
}
```

this will return array of tokens:
```json
[
    {
        "Token": "יש",
        "Type": "WORD"
    },
    {
        "Token": "מסיבה",
        "Type": "WORD"
    },
    {
        "Token": "בתל אביב",
        "Entity": "תל אביב יפו",
        "Type": "CITY"
    },
    {
        "Token": "ומודיעין",
        "Entity": "מודיעין מכבים רעות",
        "Type": "CITY"
    }
]
```