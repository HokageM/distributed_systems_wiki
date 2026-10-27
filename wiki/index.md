---
title: Index
type: overview
tags: [index, catalog]
sources: ["raw/summaries/vs_1_2.pdf", "raw/summaries/vs_3.pdf", "raw/summaries/vs_4.pdf", "raw/summaries/vs_5.pdf"]
status: solid
updated: 2026-10-12
---

# Index

Catalog of every page in this wiki. Updated on every ingest. See [[log]] for the timeline
and `CLAUDE.md` for the schema.

**Sources ingested:** 4 — `raw/summaries/vs_1_2.pdf` (Chapters 1–2 + Exercises 1–2),
`raw/summaries/vs_3.pdf` (Chapter 3 + Exercise 3), `raw/summaries/vs_4.pdf` (Chapter 4 +
Exercise 4), `raw/summaries/vs_5.pdf` (Chapter 5 + Exercise 5).

## Overview
- [[overview]] — course map: chapters and how they connect. *(solid)*
- [[glossary]] — German → English term table. *(solid)*
- [[log]] — chronological record of ingests, queries and lint passes.

## Chapters
- [[chapters/01-networking-and-sockets]] — the protocol stack, UDP/TCP, sockets and application protocols. *(ch1, solid)*
- [[chapters/02-foundations-of-distributed-systems]] — motivation, communication models, transparency and scalability. *(ch2, solid)*
- [[chapters/03-architectures-and-web-systems]] — architectural styles, middleware, multi-server realizations and HTTP. *(ch3, solid)*
- [[chapters/04-remote-invocation]] — RPC and RMI, marshalling, failure handling and call semantics. *(ch4, solid)*
- [[chapters/05-distributed-resources-and-synchronization]] — distributed file systems, storage, virtualization, cloud, and time. *(ch5, solid)*

## Concepts
- [[concepts/distributed-system]] — the three-part definition, motivation, drawbacks, and the six inherent problems. *(ch1/ch2, solid)*
- [[concepts/osi-model]] — seven layers, header encapsulation, and the internet protocol hourglass. *(ch1, solid)*
- [[concepts/ip-addressing-and-ports]] — IPv4 addresses, DNS resolution, and ports as application demultiplexers. *(ch1, solid)*
- [[concepts/udp]] — connectionless datagram transport with no delivery guarantees. *(ch1, solid)*
- [[concepts/tcp]] — reliable, ordered, full-duplex byte stream with a connection lifecycle. *(ch1, solid)*
- [[concepts/sockets]] — OS communication endpoints; Java and C/C++ APIs. *(ch1, solid)*
- [[concepts/application-protocol]] — request/reply messages and the 4-byte packet header. *(ch1, solid)*
- [[concepts/persistent-data-storage]] — `PersistentObject` over a generic `FlatDB` class. *(ch1, draft)*
- [[concepts/communication-paradigms]] — memory-based vs. message-based communication. *(ch2, solid)*
- [[concepts/blocking-function]] — the primitive underlying synchronous/asynchronous communication. *(ch2, solid)*
- [[concepts/synchronous-communication]] — rendezvous semantics; both partners block. *(ch2, solid)*
- [[concepts/asynchronous-communication]] — buffered, non-blocking send; temporal decoupling. *(ch2, solid)*
- [[concepts/transparency]] — the six dimensions of hiding distribution from the user. *(ch2, solid)*
- [[concepts/scalability]] — vertical vs. horizontal scaling; partitioning, clustering, sharding. *(ch2, solid)*
- [[concepts/speedup]] — the scaling factor; super-/linear/sub-linear regimes. *(ch2, solid)*
- [[concepts/elasticity]] — runtime adaptation to growing *and* shrinking demand. *(ch2, solid)*
- [[concepts/cloud-computing]] — IT resources as a service; unlimited horizontal scaling. *(ch2, solid)*
- [[concepts/byte-order]] — big- vs. little-endian and `htonl()` network byte order. *(ch2, solid)*
- [[concepts/software-architecture]] — component and architecture definitions; separation of concerns. *(ch3, solid)*
- [[concepts/pull-and-push-style]] — who controls the information flow; why push is hard. *(ch3, solid)*
- [[concepts/service-oriented-architecture]] — decomposition by function; orchestration; loose coupling. *(ch3, solid)*
- [[concepts/middleware]] — the application-neutral layer that hides platform differences. *(ch3, solid)*
- [[concepts/server-and-client]] — the role definitions and the request/response protocol. *(ch3, solid)*
- [[concepts/persistent-and-transient-communication]] — how long the system stores a message. *(ch3, solid)*
- [[concepts/interaction-types]] — synchronous, asynchronous, deferred synchronous, one-way. *(ch3, solid)*
- [[concepts/performance-criteria]] — response time, throughput, latency, jitter, load; QoS and SLAs. *(ch3, solid)*
- [[concepts/iterative-and-concurrent-servers]] — sequential vs. one-thread-per-request servers. *(ch3, solid)*
- [[concepts/distribution-server]] — one address in front of many servers; load-balancing strategies. *(ch3, solid)*
- [[concepts/replication]] — synchronous vs. asynchronous; when replication pays off. *(ch3, solid)*
- [[concepts/proxy]] — a representative controlling access; remote, protection, cache, smart. *(ch3, solid)*
- [[concepts/fat-and-thin-clients]] — where the application logic lives. *(ch3, solid)*
- [[concepts/libraries-frameworks-and-containers]] — the Hollywood principle, IoC, containers. *(ch3, solid)*
- [[concepts/http]] — URLs, head/body message format, methods, status codes, MIME types. *(ch3, solid)*
- [[concepts/http-scalability]] — persistent connections, pipelining, head-of-line blocking, HTTP/2. *(ch3, solid)*
- [[concepts/sessions-and-statelessness]] — sessions over a stateless protocol; cookies, session IDs, privacy. *(ch3, solid)*
- [[concepts/json]] — text-based data interchange format; Gson mapping. *(ch3, solid)*
- [[concepts/remote-invocation]] — calling functions in other address spaces; RPC vs. RMI. *(ch4, solid)*
- [[concepts/external-data-representation]] — marshalling, unmarshalling, CDR; CDR vs. JSON. *(ch4, solid)*
- [[concepts/basic-encoding-rules]] — type–length–value encoding with worked examples. *(ch4, solid)*
- [[concepts/interface-definition-language]] — language-neutral interface description; stub generation. *(ch4, solid)*
- [[concepts/stubs-and-skeletons]] — the generated proxy code; call-by-copy/restore. *(ch4, solid)*
- [[concepts/remote-call-failures]] — the six failure situations; lost calls and lost replies. *(ch4, solid)*
- [[concepts/call-semantics]] — at-least-once, at-most-once, and why exactly-once is impossible. *(ch4, solid)*
- [[concepts/distributed-object-model]] — what OO adds; value vs. remote-reference parameters. *(ch4, solid)*
- [[concepts/rmi-registry]] — binding objects to names; the bootstrap reference. *(ch4, solid)*
- [[concepts/file-system]] — namespace, directories, metadata; persistence and consistency. *(ch5, solid)*
- [[concepts/distributed-file-system]] — the emulation goal and the requirement catalogue. *(ch5, solid)*
- [[concepts/file-access-semantics]] — one-copy, upload/download, read-only, transaction. *(ch5, solid)*
- [[concepts/stateless-and-stateful-servers]] — who holds the open-file state, and what it costs. *(ch5, solid)*
- [[concepts/file-caching-and-replication]] — server cache, client cache, replication control. *(ch5, solid)*
- [[concepts/storage-architectures]] — DAS, NAS, SAN, cloud storage; block vs. file access. *(ch5, solid)*
- [[concepts/virtualization]] — hardware-level virtualization, VMs, server consolidation. *(ch5, solid)*
- [[concepts/containers]] — managed applications, images and Docker. *(ch5, solid)*
- [[concepts/cloud-service-models]] — IaaS, PaaS, SaaS along one responsibility axis. *(ch5, solid)*
- [[concepts/synchronization]] — the two meanings: temporal alignment vs. replica alignment. *(ch5, solid)*
- [[concepts/clock-correctness]] — `C(t)`, skew, offset, drift rate, monotonicity. *(ch5, solid)*
- [[concepts/clock-synchronization]] — internal vs. external, accuracy `D`, the `2D` theorem. *(ch5, solid)*
- [[concepts/network-time-protocol]] — strata, UTC-anchored hierarchy, UDP port 123. *(ch5, solid)*
- [[concepts/causality]] — cause and effect, happened-before, concurrency. *(ch5, solid)*
- [[concepts/logical-clock]] — timestamps that never contradict causality. *(ch5, solid)*
- [[concepts/causal-ordering]] — delivering messages in an order that respects `→`. *(ch5, solid)*

## Algorithms
- [[algorithms/two-phase-commit]] — atomic distributed commit in two rounds; 4n messages; blocking on failure. *(ch2, solid)*
- [[algorithms/at-most-once-rpc]] — duplicate suppression with a per-client reply history. *(ch4, solid)*
- [[algorithms/cristians-algorithm]] — external clock synchronization; `C_UTC + δ/2`. *(ch5, solid)*
- [[algorithms/berkeley-algorithm]] — internal synchronization by averaging; `D_i = D − A_i`. *(ch5, solid)*
- [[algorithms/lamport-timestamps]] — scalar logical clock; `max(C_j, C(m)) + 1`. *(ch5, solid)*
- [[algorithms/totally-ordered-multicast]] — same delivery order everywhere, via a timestamp queue. *(ch5, solid)*
- [[algorithms/vector-clocks]] — `a → b ⟺ C(a) ≤ C(b)`; concurrency as incomparability. *(ch5, solid)*

## Models
- [[models/client-server-architecture]] — client–server interaction, server threading models, layered/multi-tier architectures. *(ch1, solid)*
- [[models/architectural-styles]] — layered, two/three-tier, object-based, data-centric, event-based. *(ch3, solid)*
- [[models/centralized-and-decentralized-architectures]] — client–server vs. peer-to-peer. *(ch3, solid)*
- [[models/java-rmi]] — stub/skeleton/reference layer, exporting objects, server and client code. *(ch4, solid)*
- [[models/nfs]] — VFS, mounting, file groups, the two-timestamp cache validity check. *(ch5, solid)*

## Exercises
- [[exercises/ex01-tcp-udp-and-sockets]] — TCP/UDP true-false, protocol selection table, Java socket API, server threading, layered architectures. *(ch1, solid)*
- [[exercises/ex02-foundations-and-2pc]] — definitions, the `f(n) = 10n(11 − n)` scalability derivation, endianness, and the full 2PC analysis. *(ch2, solid)*
- [[exercises/ex03-architectures-and-http]] — push/pull network-load table, the 2 s polling interval, HTTP forms, JSON, session-ID pools, the `r > k·w` replication bound. *(ch3, solid)*
- [[exercises/ex04-rpc-rmi-and-ber]] — RPC/RMI definitions, BER encode/decode, the at-most-once protocol, and the print-job table proving exactly-once impossible. *(ch4, solid)*
- [[exercises/ex05-storage-and-clock-synchronization]] — DAS/NAS/SAN, the 60 ms/min drift, Cristian vs. Berkeley, and the worked Berkeley round that breaks the one correct clock. *(ch5, solid)*

## Queries
_none yet_
