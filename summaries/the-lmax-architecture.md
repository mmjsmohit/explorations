---
title: The LMAX Architecture
created: 2026-06-26
updated: 2026-06-26
type: summary
tags: [architecture, performance, reference]
sources: [raw/articles/lmax-architecture-martin-fowler.md]
confidence: medium
---

# The LMAX Architecture

Martin Fowler's write-up of the LMAX architecture describes a trading system that achieved extreme throughput and low latency by concentrating business logic in a single-threaded in-memory core, then pushing journaling, replication, and network concerns to surrounding disruptor pipelines.

## Key takeaways

- LMAX rejects the usual “scale by adding business-logic threads” instinct and instead uses a single writer for the core domain state.
- The design depends on [[event-sourcing]] so the in-memory state can be rebuilt from the input journal.
- The surrounding concurrency model uses the [[disruptor]] to move data through journal, replication, and output stages with low coordination overhead.
- The article frames the whole system through [[mechanical-sympathy]]: software should align with how CPUs, caches, and memory actually behave.

## Why it matters for this wiki

This article is a durable reference for architecture decisions where throughput, latency, and predictability matter more than symmetric request handling. It is especially relevant when evaluating whether a hot path should prefer serialized mutation over conventional lock-heavy concurrency.

## Related pages

[[lmax]] · [[event-sourcing]] · [[disruptor]] · [[mechanical-sympathy]]
