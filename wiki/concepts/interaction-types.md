---
title: Interaction Types
type: concept
chapter: "03-architectures-and-web-systems"
tags: [communication, synchronous, asynchronous, callbacks]
sources: ["raw/summaries/vs_3.pdf (p. 9, 28)"]
status: solid
updated: 2026-10-12
---

# Interaction Types

The four **transient** interaction types — what the client does while the server works.

## 1. Synchronous communication

The **client sends a request and waits for the reply.**

```mermaid
sequenceDiagram
    participant C as Client
    participant S as Server
    C->>S: request
    Note over C: blocked
    S-->>C: reply
    Note over C: continues
```

## 2. Asynchronous communication

The **client registers a callback and continues working.** On completion the **server calls
the registered function (callback).**

```mermaid
sequenceDiagram
    participant C as Client
    participant S as Server
    C->>S: request + callback
    Note over C: continues working
    S-->>C: callback invocation
```

## 3. Deferred synchronous communication

The **client continues working** and **periodically checks whether the reply has arrived.**

```mermaid
sequenceDiagram
    participant C as Client
    participant S as Server
    C->>S: request
    Note over C: continues working
    C->>S: poll
    C->>S: poll
    S-->>C: reply
```

## 4. One-way communication

The **client sends the request and continues working**; **no return value is needed.**

```mermaid
sequenceDiagram
    participant C as Client
    participant S as Server
    C->>S: request
    Note over C: continues working,<br/>return value not needed
```

## Summary

| Type | Client blocks? | Reply? | Who initiates delivery of the reply |
|---|---|---|---|
| Synchronous | yes | yes | server, client already waiting |
| Asynchronous | no | yes | **server (push)** |
| Deferred synchronous | no | yes | **client (pull)** |
| One-way | no | **no** | — |

```text
# the distinguishing test
if no reply is expected        -> one-way
else if client waits           -> synchronous
else if server calls back      -> asynchronous
else (client polls)            -> deferred synchronous
```

> [!inference]
> Asynchronous vs. deferred synchronous is precisely the
> [[concepts/pull-and-push-style|push vs. pull]] distinction applied to the *reply* leg of a
> request/response exchange. Asynchronous needs the server to be able to reach the client —
> the registration problem again.

## Related
- [[concepts/synchronous-communication]]
- [[concepts/asynchronous-communication]]
- [[concepts/blocking-function]]
- [[concepts/pull-and-push-style]]
- [[concepts/persistent-and-transient-communication]]
- [[concepts/server-and-client]]
- [[chapters/03-architectures-and-web-systems]]
