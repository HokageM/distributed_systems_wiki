---
title: External Data Representation and Marshalling
type: concept
chapter: "04-remote-invocation"
tags: [marshalling, serialization, cdr, heterogeneity]
sources: ["raw/summaries/vs_4.pdf (p. 2–3, 18)"]
status: solid
updated: 2026-10-12
---

# External Data Representation and Marshalling

## Why it is needed

- **TCP only provides the transmission of byte streams** — see [[concepts/tcp]].
- **All data must be converted into a byte sequence before transmission.**

> [!definition]
> An **external data representation** (*externe Datenrepräsentation*) is a **data format
> which is used in the transmission of data in a communication network.**

> [!definition]
> The **conversion of data in the local data format into the external format is called
> marshalling**, the **reverse process unmarshalling**. Frequently the terms **serialize**
> and **deserialize** are also used.

```mermaid
flowchart LR
    L1[Local format<br/>machine A] -->|marshalling| EX[External format<br/>byte sequence]
    EX -->|unmarshalling| L2[Local format<br/>machine B]
```

```text
on client_stub.call(args):
    buf ← marshal(args)          # local types -> byte sequence
    send buf
    reply ← receive()
    return unmarshal(reply)      # byte sequence -> local types
```

## CDR — Common Data Representation

- **Data types: 15 elementary types, 6 composite types.**
- **Representation: a byte sequence.**
  - **Elementary types:** if **n is the number of bytes**, the value is **stored at an index
    position which is a multiple of n** (natural alignment).
- **Every value has an unambiguous type and the receiver must know this type.**

```text
# alignment rule, with offset measured from the start of the message
offset(value of size n)  ≡  0  (mod n)
```

| Size n | Legal offsets |
|---|---|
| 1 | 0, 1, 2, 3, … |
| 2 | 0, 2, 4, 6, … |
| 4 | 0, 4, 8, 12, … |
| 8 | 0, 8, 16, 24, … |

## CDR vs. JSON

| | CDR | [[concepts/json]] |
|---|---|---|
| Encoding | binary byte sequence | text |
| Type information in the message | **no** — the receiver must know the type | yes, implied by the syntax |
| Compactness | **more compact** | more verbose |

> **CDR needs the data type for unmarshalling. CDR marshalling is more compact than JSON.**

> [!inference]
> The two facts are the same fact. CDR is compact *because* it omits type tags, which is
> exactly why the receiver must already know the types — i.e. why CDR requires an
> [[concepts/interface-definition-language|IDL]] and JSON does not.
> [[concepts/basic-encoding-rules|BER]] sits in between: it carries an explicit type tag, so
> it is self-describing but larger than CDR.

This is the Chapter-4 answer to the problem first raised by [[concepts/byte-order]].

## Related
- [[concepts/basic-encoding-rules]]
- [[concepts/interface-definition-language]]
- [[concepts/stubs-and-skeletons]]
- [[concepts/byte-order]]
- [[concepts/json]]
- [[concepts/tcp]]
- [[chapters/04-remote-invocation]]
