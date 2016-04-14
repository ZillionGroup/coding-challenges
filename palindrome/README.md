Palindrome Coding Challenge
===========================

Write an API that searches [NASA patents](https://api.nasa.gov/api.html#patents) and determines the number of [palindromic](https://en.wikipedia.org/wiki/Palindrome) strings that can be created from inventor's name.

Details
-------
The implementation should expose a service at the following entry point:
```
GET /palindromes
```
The service accepts the following parameters:

Name | Required | Default | Description
---- | -------- | ------- | -----------
`search` | yes | - | patent search text
`limit`  | no  | 1 | number of patents considered (min:1, max:5)

Request example:
```
GET /palindromes?search=electricity&limit=3
```

The service should search the NASA patents for given text and retrieve up to given number of patents. For each extracted inventor, first and last name should be concatenated into a single string (e.g. `"Graham"` and `"Bell"` becomes `"Graham Bell"`). For each such name the service should calculate the number of palindromic strings that can be created using the name letters. Name should be treated as case-insensitive (i.e. `b` and `B` is the same letter) and all white-spaces should be ignored. A valid palindromic string is one that uses only the letters in the given name, and is the same length as the given name. Each letter can be used more than once, and not every letter must be used. For example, given the name `"Graham Bell"`, `"aaahhhhaaa"` and `"bellmmlleb"` are valid, but `"aaa"` and `"hhhsagtbbb"` are not. Results should be returned in JSON format sorted by the count, highest to lowest.

Response example:
```
[
    { "name": "Thomas Edison", count: 1000000 },
    { "name": "Nicola Tesla", count: 531441 },
    { "name": "Graham Bell", count: 32768 }
]
```

Constraints
-----------

* Choice of languages and frameworks is open. Utilization of JVM-based technology is a plus.
