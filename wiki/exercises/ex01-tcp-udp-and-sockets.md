---
title: "Exercise 1 — TCP, UDP and Sockets"
type: exercise
chapter: "01-networking-and-sockets"
tags: [exercise, tcp, udp, sockets, threading]
sources: ["raw/summaries/vs_1_2.pdf (p. 8–13)"]
status: solid
updated: 2026-10-12
---

# Exercise 1 — TCP, UDP and Sockets

Exercise sheet accompanying [[chapters/01-networking-and-sockets]].

---

## Task 1.1 — True or false?

| # | Statement | Verdict |
|---|---|---|
| 1 | With TCP connections all packets are transmitted over the same route; with UDP the different packets may be transmitted over different routes. | **false** |
| 2 | TCP packets are always larger than UDP packets. | **false** |
| 3 | In the TCP/IP reference model, HTTP and TCP both belong to the transport layer. | **false** |
| 4 | In the OSI model the transport layer hides the unreliability of the session layer. | **false** |
| 5 | A client can communicate via UDP with a server that only has TCP ports open. | **false** |
| 6 | Unless specified otherwise, TCP is used. | **false** |
| 7 | UDP packets reach their destination faster than TCP packets. | **false** |
| 8 | UDP packets can be transmitted over IPv6. | **true** |
| 9 | According to the TCP protocol, incoming IP packets are passed to the application in the order in which they were received at the IP layer. | **false** |
| 10 | When using TCP it is guaranteed that no packet is lost, but the application must still check for duplicates. | **false** |

**Technique.** Each false statement attacks one specific guarantee. Work through them by
asking *which layer owns this property*:

- **1** — routing is an **IP-layer** decision, independent of the transport protocol. Even a
  single TCP connection's packets may take different routes.
- **3** — HTTP is application layer, TCP is transport layer ([[concepts/osi-model]]).
- **4** — the transport layer masks the unreliability of the layers **below** it (network
  layer), not of the session layer **above** it.
- **5** — TCP and UDP ports are **disjoint namespaces** ([[concepts/ip-addressing-and-ports]]).
- **7** — UDP has less overhead, but propagation speed is set by IP; both travel equally fast.
- **9** — TCP restores the **sender's** order, not the arrival order at IP.
- **10** — **duplicate detection is a TCP guarantee** ([[concepts/tcp]]); the application does
  not do it.

> [!exam]
> Statement 6 ("unless specified otherwise, TCP is used") is false because there is no such
> default — the protocol is always an explicit design decision, as task 1.2 shows.

---

## Task 1.2 — UDP vs. TCP per scenario

| Scenario | Duration | Connections | Performance criterion | Protocol |
|---|---|---|---|---|
| Virtual terminal access (e.g. Telnet) | long | few | reliability | **TCP** |
| FTP | long | many | reliability | **TCP** |
| IP telephony | long | few | latency | **UDP** |
| HTTP | short | many | reliability | **TCP** (UDP) |
| Remote procedure call | short | few | latency | **UDP** |
| DNS | short | many | latency | **UDP** |
| Media streaming | long | many | latency | **UDP** |

**The decision rules extracted from the table:**

```text
choose_protocol(duration, n_connections, delay_sensitivity, loss_tolerance):
    if duration = short:            prefer UDP
    if duration = long:             prefer TCP
    if n_connections = many:        prefer UDP
    if n_connections = few:         prefer TCP
    if delay matters:               prefer UDP
    if delay is irrelevant:         prefer TCP
    if lost packets are negligible: prefer UDP
    if lost packets must be detected and caught: prefer TCP
```

Stated as in the summary:
- **Duration of communication:** short → UDP, long → TCP.
- **Number of connections:** many → UDP, few → TCP.
- **Delay:** when short delay matters → UDP; when unimportant → TCP.
- **Lost packets:** negligible → UDP; must be detected and handled → TCP.

> [!contradiction]
> The rules conflict for HTTP (short duration and many connections ⇒ UDP) yet the answer is
> TCP, with UDP noted in parentheses. Reliability of the delivered document outweighs both
> criteria. Treat the rules as weighted heuristics, not as a decision procedure — the
> **performance criterion column dominates**.

---

## Task 1.3 — Java sockets

**1) What is the method `setSoTimeout(int timeout)` needed for?**
It enables `SO_TIMEOUT`: it **sets a timeout on blocking socket operations**, so that a
blocking call cannot wait indefinitely ([[concepts/blocking-function]]).

**2) What are `setSendBufferSize(int size)` and `setReceiveBufferSize(int size)` for?**
They **set the size of the I/O buffers**.

**3) The API offers `isBound()`. Is `isConnected()` still needed afterwards?**
Yes — they report different things:
- `isBound()` returns the **binding** state of the socket. It **remains true even after the
  socket is closed**.
- `isConnected()` returns the **connection** state of the socket.

**4) With TCP connections, must ACKs be sent?**
**No — this happens automatically.**

**5) Which ports are open on a given server for communication with TCP?**
Via `Socket(InetAddress address, int port)`; an **`IOException`** is raised **if an I/O error
occurs when creating the socket**, which is how an unavailable port is detected.

> [!exam]
> Question 3 is the subtle one: a closed socket is still *bound*. The two predicates are not
> redundant because binding and connecting are separate lifecycle steps.

---

## Task 1.4 — Server implementation

**1) Is it sensible to limit the number of threads in a server process?**
**Yes, so that the server does not become overloaded.**

**2) Servers can be implemented as multi-threaded or single-threaded. Are there situations in
which a single-threaded server would be better suited?**
Yes: a **simple application with few users** and **short** processing times.

See [[models/client-server-architecture]] for the pseudocode.

---

## Task 1.8 — Layered architectures

**Setting.** A multi-tier client–server architecture: `Pᵢ` is a client of `Pᵢ₊₁`, and `Pᵢ`
only returns an answer to `Pᵢ₋₁` after receiving an answer from `Pᵢ₊₁`.

**Which problems arise when the request from `P₁` has a short processing time?**

- **Each layer runs on its own machine** — every hop is a network round trip.
- From `P₁` to `Pₙ`, **n − 2 requests/replies** are required.
- The **latency is determined by the weakest machine** in the chain.
- **Problems when transferring larger files** through every tier.

Full discussion and diagram in [[models/client-server-architecture]].

---

## Practical 1 — Java threads

```java
new Thread(new Player()).start();   // starts the run() method of the called class
```

---

## Related
- [[chapters/01-networking-and-sockets]]
- [[concepts/tcp]]
- [[concepts/udp]]
- [[concepts/sockets]]
- [[concepts/osi-model]]
- [[models/client-server-architecture]]
