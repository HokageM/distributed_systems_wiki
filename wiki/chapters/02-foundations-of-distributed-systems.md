---
title: "Chapter 2 — Foundations of Distributed Systems"
type: chapter
chapter: "02-foundations-of-distributed-systems"
tags: [foundations, transparency, scalability, communication]
sources: ["raw/summaries/vs_1_2.pdf (p. 14–21)"]
status: solid
updated: 2026-10-12
---

# Chapter 2 — Foundations of Distributed Systems

Why distributed systems are built, what makes them hard, and the two quality properties the
module keeps returning to: **transparency** and **scalability**.

## Scope

```mermaid
flowchart TB
    A[Why distribute?<br/>motivation & drawbacks] --> B{Communication paradigm}
    B -->|shared address space| C[Memory-based<br/>communication]
    B -->|network| D[Message-based<br/>communication]
    D --> E[Blocking functions]
    E --> F[Synchronous]
    E --> G[Asynchronous]
    A --> H[Problems of DS<br/>no global clock, deadlocks, ...]
    H --> I[Transparency]
    H --> J[Scalability]
    J --> K[Vertical scaling]
    J --> L[Horizontal scaling]
    L --> M[Elasticity] --> N[Cloud computing]
```
*Chapter 2 roadmap.*

## Contents

1. [[concepts/distributed-system]] — definition, motivation, and drawbacks.
2. [[concepts/communication-paradigms]] — memory-based vs. message-based communication.
3. [[concepts/blocking-function]] — the primitive that distinguishes the next two pages.
4. [[concepts/synchronous-communication]] — sender and receiver synchronized; both block.
5. [[concepts/asynchronous-communication]] — buffered; `send` does not block.
6. [[concepts/transparency]] — the six transparency dimensions.
7. [[concepts/scalability]] — definition, vertical vs. horizontal scaling, techniques.
8. [[concepts/speedup]] — the scaling factor; super-/linear/sub-linear.
9. [[concepts/elasticity]] — adaptation at *runtime*.
10. [[concepts/cloud-computing]] — unlimited horizontal scaling as a service.

## Key takeaways

**Motivation for distributing:** resource sharing (physical: disks, CPUs; logical: data),
information exchange, geographically distributed access, virtualization of IT systems,
economy, reliability — and the plain fact that the real world *is* distributed.

**Drawbacks:** new security risks, increased complexity, performance losses.

**Inherent problems** (these recur in every later chapter):

| Problem | Why it hurts |
|---|---|
| No global clock | Events cannot be totally ordered by timestamp |
| Heterogeneous participants | Different hardware, OS, byte order ([[concepts/byte-order]]) |
| Security | The network is an attack surface |
| Concurrency | Interleavings must be controlled |
| Deadlocks | Synchronization across nodes can cycle |
| Independent failures | Parts fail while others keep running |

> [!exam]
> The distinction *distributed system vs. multiprocessor system* is a standard exam question.
> Multiprocessor: shared memory, tight coupling, homogeneous, one global clock.
> Distributed: no shared memory, message passing with an explicit protocol, heterogeneous
> (needs middleware), no global clock. Worked out in [[exercises/ex02-foundations-and-2pc]].

## Exercises

- [[exercises/ex02-foundations-and-2pc]] — includes [[algorithms/two-phase-commit]] and
  [[concepts/byte-order]].

## Related
- [[chapters/01-networking-and-sockets]]
- [[chapters/03-architectures-and-web-systems]]
- [[overview]]
- [[glossary]]
