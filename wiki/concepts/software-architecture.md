---
title: Software Architecture and Components
type: concept
chapter: "03-architectures-and-web-systems"
tags: [architecture, components, design]
sources: ["raw/summaries/vs_3.pdf (p. 1)"]
status: solid
updated: 2026-10-12
---

# Software Architecture and Components

The vocabulary for everything else in [[chapters/03-architectures-and-web-systems]].

> [!definition]
> A **component** (*Komponente*) is a **modular unit with clearly defined required and
> provided interfaces** (*erforderliche und bereitgestellte Schnittstellen*).

> [!definition]
> The **architecture** of a system describes its **decomposition into separate components**
> and defines
> - the **functional roles** of the components,
> - their **relationships to one another**,
> - **how the components communicate** with each other, and
> - **how they are mapped onto a network of computers**.

```mermaid
flowchart LR
    A["Component A"] -->|provided interface| B["Component B"]
    B -->|required interface| C["Component C"]
```
*A component is defined by its interfaces, not by its implementation.*

> [!inference]
> The fourth clause — mapping onto a network — is what makes this a *distributed systems*
> definition rather than a general software-engineering one. The same logical decomposition
> can be deployed in many ways, and the deployment choice is part of the architecture.

## Two kinds of architecture

The module implicitly separates two questions, and it is worth keeping them apart:

| Question | Answer |
|---|---|
| How is the software organized logically? | **Architectural style** — see [[models/architectural-styles]] |
| How is it placed on machines? | **System architecture** — see [[models/centralized-and-decentralized-architectures]] |

## Separation of concerns

> **Separation of Concerns** is a design principle for separating a program into distinct
> sections such that each section addresses a separate concern.

This is the principle behind layering, components, and
[[concepts/libraries-frameworks-and-containers|containers]] alike.

## Related
- [[models/architectural-styles]]
- [[models/centralized-and-decentralized-architectures]]
- [[concepts/middleware]]
- [[exercises/ex03-architectures-and-http]]
- [[chapters/03-architectures-and-web-systems]]
