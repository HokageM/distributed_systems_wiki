---
title: Log
type: overview
tags: [log, timeline]
sources: ["raw/summaries/vs_1_2.pdf", "raw/summaries/vs_3.pdf", "raw/summaries/vs_4.pdf", "raw/summaries/vs_5.pdf"]
status: solid
updated: 2026-10-12
---

# Log

Append-only, newest at the bottom. Every entry starts with `## [YYYY-MM-DD] <type> | <title>`
so it stays greppable: `grep "^## \[" wiki/log.md | tail -5`.

Types: `ingest`, `query`, `lint`, `refactor`.

---

## [2026-10-12] refactor | Wiki initialized
- Created `CLAUDE.md` schema, `raw/` and `wiki/` directory structure.
- Created [[index]], [[log]], [[overview]], [[glossary]].
- Notes: no sources ingested yet.

## [2026-10-12] ingest | Chapters 1–2 and Exercises 1–2
- Source: `raw/summaries/vs_1_2.pdf` (32 pages, handwritten German, no extractable text —
  rendered to images and read page by page).
- Created chapters: [[chapters/01-networking-and-sockets]],
  [[chapters/02-foundations-of-distributed-systems]]
- Created concepts: [[concepts/distributed-system]], [[concepts/osi-model]],
  [[concepts/ip-addressing-and-ports]], [[concepts/udp]], [[concepts/tcp]],
  [[concepts/sockets]], [[concepts/application-protocol]],
  [[concepts/persistent-data-storage]], [[concepts/communication-paradigms]],
  [[concepts/blocking-function]], [[concepts/synchronous-communication]],
  [[concepts/asynchronous-communication]], [[concepts/transparency]],
  [[concepts/scalability]], [[concepts/speedup]], [[concepts/elasticity]],
  [[concepts/cloud-computing]], [[concepts/byte-order]]
- Created algorithms: [[algorithms/two-phase-commit]]
- Created models: [[models/client-server-architecture]]
- Created exercises: [[exercises/ex01-tcp-udp-and-sockets]],
  [[exercises/ex02-foundations-and-2pc]]
- Updated: [[index]], [[overview]], [[glossary]]
- Chapter numbering: confirmed with the user as Ch1 = Networking & Sockets,
  Ch2 = DS Foundations, following the exercise-sheet numbering in the source.
- Notes:
  - Flagged a `[!contradiction]` in [[exercises/ex01-tcp-udp-and-sockets]]: the UDP/TCP
    selection heuristics (short duration + many connections ⇒ UDP) contradict the answer
    "TCP" for HTTP. Resolved as: the performance-criterion column dominates.
  - The source's first attempt at `f(n)` (`90n + 10`) is struck out and corrected to
    `10n(11 − n)`; only the corrected version was filed, with the wrong one kept as an
    `[!exam]` trap.
  - [[concepts/persistent-data-storage]] left as `draft` — the source covers it in 3 lines.
  - Exercise 1 in the source jumps from task 1.4 to 1.8; tasks 1.5–1.7 are absent.

## [2026-10-12] ingest | vs_3.pdf — Chapter 3: Architectures and Web-Based Systems

**Source:** `raw/summaries/vs_3.pdf` (38 pages, scanned handwritten German notes, no
extractable text). Pages 1–27 lecture content, pages 28–37 exercise sheet 3, page 38
practical 3. Rendered to JPEG at 110 dpi and read page by page.

**Pages created (20):**
- `chapters/03-architectures-and-web-systems.md`
- Concepts: `software-architecture`, `pull-and-push-style`, `service-oriented-architecture`,
  `middleware`, `server-and-client`, `persistent-and-transient-communication`,
  `interaction-types`, `performance-criteria`, `iterative-and-concurrent-servers`,
  `distribution-server`, `replication`, `proxy`, `fat-and-thin-clients`,
  `libraries-frameworks-and-containers`, `http`, `http-scalability`,
  `sessions-and-statelessness`, `json`
- Models: `architectural-styles`, `centralized-and-decentralized-architectures`
- Exercises: `ex03-architectures-and-http`

**Pages updated:** `index`, `overview` (chapter table, topic map extended, recurring threads
and gaps rewritten), `glossary` (+128 rows), `models/client-server-architecture`,
`concepts/transparency`, `concepts/scalability`, `concepts/application-protocol`,
`concepts/persistent-data-storage`, `algorithms/two-phase-commit`,
`chapters/02-foundations-of-distributed-systems`.

**Notes and judgement calls:**
- `[!contradiction]` filed in [[concepts/distribution-server]]: the p. 13 table labels
  distributed data "transparent" and replicated data "not transparent", but p. 14 presents
  both transparent and non-transparent variants of distributed data and says replication
  works with or without a distribution server. Resolved as: transparency is an orthogonal
  choice (is there a distribution server?), not a property of distribute-vs-replicate. The
  p. 14 statement is treated as authoritative.
- Exercise 3.7 result generalized on [[concepts/replication]] as `r > k·w` — the document
  size `s` cancels and is irrelevant.
- Exercise 3.2b generalized as `T = 2d`: an average detection delay of `d` needs a polling
  interval of `2d`.
- Exercise 3.2a pull loads assume two messages per poll (request + response), which is what
  makes the source's 7200 vs. 3600 figures come out.
- Layered and multi-tier architectures already existed in
  [[models/client-server-architecture]] from Chapter 1; the Chapter 3 treatment was filed in
  the new [[models/architectural-styles]] and the two pages cross-linked rather than
  duplicating content.
- `[!warning]` on the middleware page: "Middleware provides NO application functionality" is
  triple-underlined in the source.

## [2026-10-12] ingest | vs_4.pdf — Chapter 4: Remote Invocation

**Source:** `raw/summaries/vs_4.pdf` — 29 scanned pages of handwritten German notes
(no extractable text; rendered to JPEG and read page by page).
Pages 1–17 are lecture content, pages 18–29 are exercise sheet 4 plus the practical task.

**Created (13 pages):**

- [[chapters/04-remote-invocation]] — chapter hub
- [[concepts/remote-invocation]], [[concepts/external-data-representation]],
  [[concepts/basic-encoding-rules]], [[concepts/interface-definition-language]],
  [[concepts/stubs-and-skeletons]], [[concepts/remote-call-failures]],
  [[concepts/call-semantics]], [[concepts/distributed-object-model]],
  [[concepts/rmi-registry]]
- [[algorithms/at-most-once-rpc]]
- [[models/java-rmi]]
- [[exercises/ex04-rpc-rmi-and-ber]]

**Updated:** [[index]], [[overview]] (chapter table, topic map, recurring threads, open
questions), [[glossary]] (+81 rows), and back-links from
[[chapters/03-architectures-and-web-systems]], [[concepts/middleware]], [[concepts/proxy]],
[[concepts/json]], [[concepts/byte-order]], [[concepts/http]], [[concepts/transparency]],
[[algorithms/two-phase-commit]].

**Notes and source defects:**

- Page 23 is a blank/garbage scan and page 24 duplicates page 22 — no content lost.
- Exercise numbering jumps **4.4 → 4.6**; task 4.5 is absent from the summary.
- The BER encoding in task (i) is partly illegible in the scan. It was reconstructed as
  `30h 0Ah 02h 01h 20h 01h 01h FFh 04h 02h 61h 0Ah` and flagged with a `[!warning]` on
  [[exercises/ex04-rpc-rmi-and-ber]].
- The exercise 4.6 print-job semantics table was **independently re-derived** and matches
  the source exactly. Its conclusion — no column yields exactly one execution under every
  interleaving — is recorded as the exactly-once impossibility argument on
  [[concepts/call-semantics]].
- BER decode example (d) was verified by arithmetic: `3 + 6 + 3 = 12` bytes of content,
  matching the declared long-form length.

## [2026-10-12] ingest | vs_5.pdf — Chapter 5: Distributed Resources and Synchronization

**Source:** `raw/summaries/vs_5.pdf` — 36 scanned pages of handwritten German notes
(headed *VS-KVB*; no extractable text, rendered to JPEG and read page by page).
Pages 1–18 cover storage, pages 19–30 cover time, pages 31–36 are exercise sheet 5.

Chapter title chosen in conversation with the user: **Distributed Resources and
Synchronization**, since exercise sheet 5 spans both halves (5.1 storage, 5.2–5.3 clocks)
and they therefore form one chapter.

**Created (22 pages):**

- [[chapters/05-distributed-resources-and-synchronization]] — chapter hub
- Storage: [[concepts/file-system]], [[concepts/distributed-file-system]],
  [[concepts/file-access-semantics]], [[concepts/stateless-and-stateful-servers]],
  [[concepts/file-caching-and-replication]], [[concepts/storage-architectures]],
  [[concepts/virtualization]], [[concepts/containers]],
  [[concepts/cloud-service-models]], [[models/nfs]]
- Time: [[concepts/synchronization]], [[concepts/clock-correctness]],
  [[concepts/clock-synchronization]], [[concepts/network-time-protocol]],
  [[concepts/causality]], [[concepts/logical-clock]], [[concepts/causal-ordering]]
- Algorithms: [[algorithms/cristians-algorithm]], [[algorithms/berkeley-algorithm]],
  [[algorithms/lamport-timestamps]], [[algorithms/totally-ordered-multicast]],
  [[algorithms/vector-clocks]]
- [[exercises/ex05-storage-and-clock-synchronization]]

**Updated:** [[index]], [[overview]] (chapter table completed, topic map extended with both
chapter-5 clusters, three new recurring threads, open questions revised), [[glossary]]
(+205 rows), and back-links from earlier chapters.

**Notes and source defects:**

- Exercise numbering jumps **5.1 a) → 5.1 c)**; task **5.1 b) is absent**.
- The second principle of clock correction is missing — the source numbers them **1) and
  3)**. Flagged on [[concepts/clock-correctness]].
- **Exercise 5.1 d) contains an arithmetic error in the source.** It writes `56 940 000`
  ticks/min and a difference of `3 060 000`, but concludes `60 ms/min`. Independently
  re-derived: `999 × 60 000 = 59 940 000`, difference `60 000` ticks `= 60 ms/min`, drift
  rate `ρ = 10⁻³`. **The source's final answer is correct; its intermediate figures are
  not.** Corrected in the wiki with a `[!warning]`.
- **Exercise 5.3: `C_2(T)` is illegible** (final digit reads as 4 or 9). Reconstructed as
  **1:01:09**, because the source's own answer `A_2 = +2` requires it. The whole Berkeley
  round was then independently re-derived and **matches every published value**
  (`A = [0, −4, +2, −3, 0]`, `D = −1`, `D = [−1, +3, −3, +2, −1]`, all clocks converging on
  1:01:06).
- **Exercise 5.3 (2) is cut off mid-line in the source** (`D_2 = 3 − 6 = …`) and its visible
  working is inconsistent with part (1). Reconstructed from the part-(1) results: the one
  correct clock is moved 3 s away from true time, giving the counterexample to the converse
  of the `2D` theorem.
- [[models/nfs]] lists **failure** and **concurrency transparency** as empty headings in
  the source; recorded as a gap rather than as a claim.
- The comparison of [[algorithms/totally-ordered-multicast]] with
  [[concepts/causal-ordering]] (neither implies the other) is **my synthesis**, not in the
  source, and is marked as an `[!inference]`.

**All five summary PDFs are now ingested.**

## [2026-10-12] lint | Full health check across all 87 pages

First whole-wiki health pass, run after the fifth and last source PDF was ingested.

**Mechanical checks — all clean.** 87 pages: no broken wikilinks, no orphans, no page with
fewer than two inbound links, every page listed in [[index]], every page carrying a
`## Related` section, no page under 1 200 characters, no `TODO`/`TBD` markers. Callout
census: 100 `[!inference]`, 84 `[!definition]`, 57 `[!exam]`, 32 `[!warning]`, 11
`[!theorem]`, 5 `[!contradiction]`, 1 `[!proof]`.

**Content errors found and fixed (4):**

- [[models/java-rmi]] — the source claims "the interface `Remote` is an extension of
  `Serializable`". **This is false** and it contradicted the class table on the same page.
  `java.rmi.Remote` is an empty marker interface. The two interfaces mark opposites:
  `Remote` = reached by reference through a stub, `Serializable` = copied by value.
  Corrected, with the source's claim preserved in a `[!warning]`.
- [[concepts/sockets]] — the lecture's TCP server snippet (`String data = in.read();`)
  **does not compile**; `DataInputStream.read()` returns an `int`, not a `String`. Replaced
  with `readUTF()` / `writeUTF()` and flagged.
- [[concepts/http]] — "non-ASCII characters become `%XX`" was imprecise. Percent-encoding
  operates on **bytes**. Noted that the source's own example `M%FCller` is Latin-1, and that
  the same `ü` in UTF-8 would be `%C3%BC`.
- [[algorithms/berkeley-algorithm]] — the outlier-discard line in the pseudocode left it
  ambiguous whether discarded machines still get corrected. Made explicit: `D` is averaged
  over the retained set, but **every** clock is corrected.

**Rejected finding.** An audit flagged the [[algorithms/vector-clocks]] receive rule
(increment own component, then merge) as able to overwrite the increment. It cannot:
`V(m)[i] ≤ V_i[i]` always holds, because the sender's knowledge of `p_i` can only have come
from `p_i` itself. Added an `[!inference]` proving the two orderings equivalent rather than
"fixing" a non-bug.

**Consistency sweep:**

- **Spelling normalized to `-ize`/`-ization`** (was mixed: 206 American vs 96 British forms).
  151 lines across 47 pages. German originals left untouched. Rule added to `CLAUDE.md`.
- **[[glossary]] deduplicated and sorted.** It had grown to 514 append-ordered rows with 24
  German terms duplicated across ingests. Now **488 rows, one per term, alphabetical**, with
  the `Page` column merged. Where a term has genuinely distinct senses they are kept in one
  cell (`Anforderung | Request / Requirement`, `Verzögerung | Delay / Latency`). Rule added
  to `CLAUDE.md`.
- Frontmatter completed on [[index]] and [[log]]; [[overview]] promoted `draft` → `solid`
  now that all five chapters are in.

**Remaining known gaps** (unchanged, all deliberate and flagged in place): the empty NFS
failure/concurrency transparency headings, the missing second principle of clock correction,
absent exercise task 5.1 b), and the thin [[concepts/persistent-data-storage]] page — all
awaiting the lecture slides.
