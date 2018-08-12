# Hebrew Name Analyzer

This service allows you to enter a name and hebrew and will return statistical info about that name to determine if the name is a first name, last name or if it belongs to a male or female

## Endpoint 
https://hebrew-nlp.co.il/service/names/analyze

## Parameters
Field | Type | Description
------|------|-------------
token | string | The token/password, sent in sms when you register
names | array of `NameInfo` | The names to analyze

```json
{
    "token": "...",
    "names": [
        "איתי",
        "חיים"
    ]
}
```

## Returns
JSON array of `NameInfo`

All the chances are measured from 0 to 10, with 0 being lowest chance and 10 being highest chance

Field | Type | Description
------|------|-------------
FirstName | int | The chance the name is a first name
LastName | int | The chance the name is a first name
Male | int | The chance the name is a first name
Female | int | The chance the name is a first name

```json
[
    {
        "FirstName": 10,
        "LastName": 0,
        "Male": 9,
        "Female": 1
    },
    {
        "FirstName": 9,
        "LastName": 1,
        "Male": 10,
        "Female": 0
    }
]
```
