---
title: Performance Criteria, QoS and SLAs
type: concept
chapter: "03-architectures-and-web-systems"
tags: [performance, latency, throughput, qos]
sources: ["raw/summaries/vs_3.pdf (p. 10)"]
status: solid
updated: 2026-10-12
---

# Performance Criteria, QoS and SLAs

Performance criteria for client–server architectures.

## The criteria

> [!definition]
> **Response time** (*Antwortzeit*) — the **time span between sending the request and
> completely receiving the answer.** It comprises the data transfer in the transmission
> media, waiting time, and processing time.

> [!definition]
> **Throughput** (*Durchsatz*) — a **measure of the amount of data per time unit that can be
> transferred over the network and processed**; work per unit time.

> [!definition]
> **Latency** (*Verzögerung*) — the **duration of the data transfer from client to server.**
> It is **independent of the size of the answer and of the server's processing time.**

> [!theorem]
> **response time ≥ latency**

> [!definition]
> **Jitter** — the **deviation of the latency or response time from the mean.**

> [!definition]
> **Load** (*Last*) — the **utilization of the system.**

> [!definition]
> **Load sensitivity** (*Lastabhängigkeit*) — the **dependence of the response time on the
> load.**

```mermaid
flowchart LR
    A[Request sent] -->|latency| B[Request arrives]
    B -->|processing time| C[Answer produced]
    C -->|transfer| D[Answer fully received]
    A -.->|response time| D
```
*Latency is one leg; response time is the whole round trip including processing.*

```text
response_time = latency_request + waiting_time + processing_time + transfer_of_answer
jitter        = deviation of (latency | response_time) from its mean
load_sensitivity = d(response_time) / d(load)
```

## Quality of Service

> [!definition]
> **Quality of Service (QoS)** is the **ability of a system to guarantee compliance with
> specified performance criteria.** It is realized by **prioritization of data traffic** and
> **guaranteed provision of computing and communication resources.**

> [!warning]
> **TCP/IP is best-effort** — it gives no QoS guarantees at all. Any guarantee must be built
> above it or provided by the network operator.

> [!definition]
> A **Service Level Agreement (SLA)** is an **agreement between the client and the service
> provider regarding the quality of service.**

## Why these matter together

> [!inference]
> The criteria are not independent. Raising throughput by batching raises response time;
> adding servers (see [[concepts/distribution-server]]) lowers load sensitivity but adds a
> hop of latency. An SLA forces you to pick which one you are promising.

Latency is examined quantitatively in [[exercises/ex03-architectures-and-http]] (task 3.2b),
where an average alarm delay of 1 s is translated into a 2 s polling interval.

## Related
- [[concepts/scalability]]
- [[concepts/iterative-and-concurrent-servers]]
- [[concepts/distribution-server]]
- [[concepts/tcp]]
- [[exercises/ex03-architectures-and-http]]
- [[chapters/03-architectures-and-web-systems]]
