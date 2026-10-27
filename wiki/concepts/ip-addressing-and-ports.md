---
title: IP Addressing and Ports
type: concept
chapter: "01-networking-and-sockets"
tags: [networking, addressing, dns, ports]
sources: ["raw/summaries/vs_1_2.pdf (p. 2)"]
status: solid
updated: 2026-10-12
---

# IP Addressing and Ports

An IP address identifies a *host* on the network; a port number identifies an *application*
on that host. Together they form the endpoint that a [[concepts/sockets|socket]] is bound to.

## IPv4 addressing

- **32 bit** wide, giving 2³² ≈ 4.3 billion addresses.
- Three equivalent forms of the same host:
  - decimal integer: `1062734774`
  - dotted quad: `192.168.0.2`
  - host name: `www.foo.com`
- **DNS** (Domain Name System) translates host names into IP addresses.
- An address splits into a **network ID** and a **host ID** (*Netz-ID / Rechner-ID*).

```mermaid
flowchart LR
    N["www.foo.com"] -->|DNS lookup| A["192.168.0.2"]
    A --> S["Network ID | Host ID"]
```
*Name resolution and the two-part structure of an IPv4 address.*

> [!inference]
> IPv6 exists and carries both UDP and TCP; the summary only confirms that UDP packets can be
> transmitted over IPv6 (exercise 1, statement 8 — *true*). The module does not develop IPv6
> further at this point.

## Ports

A single IP address must potentially serve **several internet applications** at once.
Therefore **each application is assigned exactly one port number**.

```text
endpoint ≔ ⟨IP address, port⟩
```

- The IP address routes a packet to the right *machine*.
- The port number demultiplexes it to the right *process* on that machine.
- UDP ports and TCP ports are separate namespaces.

> [!exam]
> A client using UDP **cannot** communicate with a server that only has TCP ports open —
> the transport protocols are disjoint. (Exercise 1, statement 5 — *false*.)

## Related
- [[concepts/osi-model]]
- [[concepts/sockets]]
- [[concepts/udp]]
- [[concepts/tcp]]
- [[chapters/01-networking-and-sockets]]
