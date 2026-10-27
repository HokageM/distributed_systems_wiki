---
title: Iterative and Concurrent Servers
type: concept
chapter: "03-architectures-and-web-systems"
tags: [servers, threads, sockets, concurrency]
sources: ["raw/summaries/vs_3.pdf (p. 11–12)"]
status: solid
updated: 2026-10-12
---

# Iterative and Concurrent Servers

How a single server process handles more than one request.

## Iterative server

- **Requests are processed sequentially** — a **single-threaded server**.
- Requests arriving **during processing are rejected, buffered or ignored**.
- **Only sensible for simple services with short processing times.**

```text
socket()
bind()
listen()
loop forever:
    conn ← accept()
    read(conn) / write(conn)      # the whole request, start to finish
    close(conn)
```

```mermaid
sequenceDiagram
    participant C1 as Client 1
    participant C2 as Client 2
    participant S as Server
    C1->>S: request
    Note over S: processing
    C2->>S: request (rejected / buffered)
    S-->>C1: answer
    S-->>C2: answer
```

## Concurrent server

- **Several requests are processed simultaneously.**
- **Sensible for long requests.**
- **Realization: one thread or process per request.**
- Advantages: the **mean response time per request improves**, and there is **better
  utilization of the hardware**.

```text
socket()
bind()
listen()
loop forever:
    conn ← accept()
    fork()                        # or: start a new thread
    in the child:
        read(conn) / write(conn)
        close(conn)
```

```mermaid
sequenceDiagram
    participant C1 as Client 1
    participant C2 as Client 2
    participant D as Dispatcher
    participant W1 as Worker 1
    participant W2 as Worker 2
    C1->>D: request
    D->>W1: hand over socket
    C2->>D: request
    D->>W2: hand over socket
    W1-->>C1: answer
    W2-->>C2: answer
```

### Concurrent TCP echo server (Java sketch, from the source)

```java
public class Dispatcher {
    ServerSocket sock = new ServerSocket(PORT);
    while (true) {
        Socket cSocket = sock.accept();
        WorkerThread at = new WorkerThread(cSocket);
        at.start();
    }
}
```

The dispatcher loop does nothing but `accept()` and hand the connection to a worker — it
must never block on application work, or the server degenerates to an iterative one.

## Comparison

| | Iterative | Concurrent |
|---|---|---|
| Threads | one | one per request |
| Suitable for | short, simple services | long requests |
| Behaviour under concurrent load | reject / buffer / ignore | serve in parallel |
| Mean response time | degrades quickly | improves |
| Hardware utilization | poor | good |

**Assumptions:** TCP sockets; the OS supports `fork()` or threads.
**Message complexity:** unchanged — one request/response pair per client.
**Time complexity:** iterative serializes, so the *k*-th waiting client sees a delay of
roughly *k* · processing time; concurrent sees ≈ one processing time while threads are
available.
**Failure behaviour:** in a concurrent server a crashing worker kills only its own request;
in an iterative server a hanging request blocks every other client.

## Related
- [[models/client-server-architecture]]
- [[concepts/sockets]]
- [[concepts/performance-criteria]]
- [[concepts/server-and-client]]
- [[concepts/tcp]]
- [[chapters/03-architectures-and-web-systems]]
