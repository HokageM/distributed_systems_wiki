---
title: Persistent and Transient Communication
type: concept
chapter: "03-architectures-and-web-systems"
tags: [communication, messaging, middleware]
sources: ["raw/summaries/vs_3.pdf (p. 8)"]
status: solid
updated: 2026-10-12
---

# Persistent and Transient Communication

How long does the **communication system** hold on to a message?

> [!definition]
> With **persistent communication** a sent message is **stored by the communication system
> until it can be delivered** to the receiver. The storage happens **at the sender or at an
> independent location**.

> [!definition]
> With **transient communication** a message is **only stored as long as the sending and the
> receiving application are running.**

```mermaid
flowchart LR
    subgraph P["Persistent"]
        S1[Sender] --> B[(Message store)] --> R1[Receiver<br/>may start later]
    end
    subgraph T["Transient"]
        S2[Sender] --> R2[Receiver<br/>must be running now]
    end
```

| | Persistent | Transient |
|---|---|---|
| Receiver must run at send time | no | **yes** |
| Message storage | sender or independent broker | only in transit |
| Example | e-mail, message queues | TCP connection, HTTP request |

> [!inference]
> Persistence decouples the *lifetimes* of the two parties, while
> [[concepts/interaction-types|synchronicity]] decouples their *waiting*. The two axes are
> independent: you can have transient asynchronous communication (a callback over a live
> connection) and persistent synchronous communication (blocking on a queued request).

> [!exam]
> Do not confuse this with [[concepts/persistent-data-storage]]. There, "persistent" means
> data survives the program; here it means a *message* survives until deliverable. Same word,
> different subject.

## Related
- [[concepts/interaction-types]]
- [[concepts/communication-paradigms]]
- [[concepts/persistent-data-storage]]
- [[concepts/service-oriented-architecture]]
- [[chapters/03-architectures-and-web-systems]]
