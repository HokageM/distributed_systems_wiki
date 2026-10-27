---
title: "Chapter 5 — Distributed Resources and Synchronization"
type: chapter
chapter: "05-distributed-resources-and-synchronization"
tags: [chapter, file-systems, storage, virtualization, cloud, time, synchronization]
sources: ["raw/summaries/vs_5.pdf (p. 1–36)"]
status: solid
updated: 2026-10-12
---

# Chapter 5 — Distributed Resources and Synchronization

The chapter has two halves that the exercise sheet treats as one unit.

The **first half** asks how a distributed system shares a *resource* — concretely, storage.
It starts from the file system, generalizes it to the
[[concepts/distributed-file-system|distributed file system]], works through the design
choices that distribution forces (access semantics, server state, caching, replication),
grounds them in [[models/nfs|NFS]], and then zooms out to the hardware
([[concepts/storage-architectures|DAS, NAS, SAN]]) and to the abstraction layers built on
top of it ([[concepts/virtualization]], [[concepts/containers]],
[[concepts/cloud-service-models]]).

The **second half** confronts the one inherent problem that chapters 1–4 named but never
solved: **there is no global clock.** It builds up from physical clocks and their
imperfections ([[concepts/clock-correctness]]) through
[[concepts/clock-synchronization|synchronization of real time]]
([[algorithms/cristians-algorithm|Cristian]], [[algorithms/berkeley-algorithm|Berkeley]],
[[concepts/network-time-protocol|NTP]]) to the realization that *real time is not what
distributed algorithms actually need*. What they need is
[[concepts/causality|causal order]], and that can be captured exactly with
[[algorithms/lamport-timestamps|logical]] and [[algorithms/vector-clocks|vector]] clocks.

> [!inference]
> The two halves are less unrelated than they look. The whole first half is about **keeping
> replicas of data consistent**, and every consistency rule is secretly a statement about
> **order** — "the client sees changes immediately", "modifications become visible at
> `close`", "the invalidate must reach every copy". The second half supplies the only
> machinery that can state such ordering claims without a global clock. Read
> [[concepts/file-access-semantics]] and [[concepts/causal-ordering]] back to back.

## The storage half

- [[concepts/file-system]] — the non-distributed starting point: namespace, directories, metadata
- [[concepts/distributed-file-system]] — definition and the requirement catalogue
- [[concepts/file-access-semantics]] — one-copy, upload/download, read-only, transaction
- [[concepts/stateless-and-stateful-servers]] — who remembers the open files
- [[concepts/file-caching-and-replication]] — server cache, client cache, replication control
- [[models/nfs]] — the worked example: VFS, mounting, the two-timestamp validity check
- [[concepts/storage-architectures]] — DAS, NAS, SAN and cloud storage
- [[concepts/virtualization]] — hardware-level virtualization and server consolidation
- [[concepts/containers]] — managed applications and Docker
- [[concepts/cloud-service-models]] — IaaS, PaaS, SaaS

## The time half

- [[concepts/synchronization]] — the two meanings of the word
- [[concepts/clock-correctness]] — `C(t)`, skew, offset, drift rate, monotonicity
- [[concepts/clock-synchronization]] — internal vs. external, accuracy `D`, the `2D` bound
- [[algorithms/cristians-algorithm]] — external synchronization against a UTC server
- [[algorithms/berkeley-algorithm]] — internal synchronization by averaging
- [[concepts/network-time-protocol]] — the internet-scale hierarchy of strata
- [[concepts/causality]] — cause and effect, the happened-before relation, concurrency
- [[concepts/logical-clock]] — what a logical clock is required to do
- [[algorithms/lamport-timestamps]] — the scalar clock and its total-order extension
- [[algorithms/totally-ordered-multicast]] — the application that needs the total order
- [[algorithms/vector-clocks]] — the clock that characterizes causality exactly
- [[concepts/causal-ordering]] — ordering message *delivery*, not just timestamps

## Exercise

- [[exercises/ex05-storage-and-clock-synchronization]]

## Related
- [[chapters/04-remote-invocation]]
- [[overview]]
- [[glossary]]
