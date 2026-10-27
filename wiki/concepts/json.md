---
title: "JSON: JavaScript Object Notation"
type: concept
chapter: "03-architectures-and-web-systems"
tags: [json, serialization, data-interchange, http]
sources: ["raw/summaries/vs_3.pdf (p. 22, 35, 38)"]
status: solid
updated: 2026-10-12
---

# JSON: JavaScript Object Notation

> [!definition]
> **JSON** is a **simple text-based data interchange format**. MIME type:
> **`application/json`**.

It exists because, to **simplify the transfer of structured data**, data interchange formats
were developed — raw `application/x-www-form-urlencoded` strings (see [[concepts/http]]) are
flat and cannot express nesting.

## Example

```json
{
  "coord": { "lon": -0.13, "lat": 51.513 },
  "sys":   { "message": 0.5, "country": "GB", "sunrise": 123 },
  "alt": 123,
  "cod": 200
}
```

## Value types

```text
object  : { "key": value, ... }      # nesting is the point
array   : [ value, ... ]
string  : "text"
number  : 3000  |  39.80
boolean : true | false
null    : null
```

## Building a JSON object (Java, from the source)

```java
JSONObject book = new JSONObject();
book.put("Title",   "Bla");
book.put("Auflage", 3000);
book.put("Preis",   39.80);
book.put("Inhalt",  null);

JSONObject author = new JSONObject();
author.put("Vor",  "Volker");
author.put("Nach", "Turau");
book.put("Autor", author);
```

`book.toString()` yields:

```json
{
  "Title": "Bla",
  "Auflage": 3000,
  "Preis": 39.80,
  "Inhalt": null,
  "bestseller": true,
  "Autor": { "Vor": "Volker", "Nach": "Turau" }
}
```

Note that `put("Autor", author)` **nests one object inside another** — the whole reason for
preferring JSON over a flat parameter string.

## Automatic mapping with Gson

```java
import com.google.gson.Gson;

Gson gson = new Gson();
String jsonString = gson.toJson(myObject);
MyClass mc = gson.fromJson(jsonString, MyClass.class);
```

> [!inference]
> `toJson`/`fromJson` is the application-level answer to the problem first raised by
> [[concepts/byte-order]]: a sender and a receiver on different platforms need an
> unambiguous external representation. JSON solves it by being **text**, so there is no
> endianness and no word size — at the price of size and parsing cost.

## Related
- [[concepts/http]]
- [[concepts/byte-order]]
- [[concepts/application-protocol]]
- [[concepts/server-and-client]]
- [[exercises/ex03-architectures-and-http]]
- [[concepts/external-data-representation]]
- [[chapters/03-architectures-and-web-systems]]
