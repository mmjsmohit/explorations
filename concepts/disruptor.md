---
title: Disruptor
created: 2026-06-26
updated: 2026-06-26
type: concept
tags: [concept, architecture, performance]
sources: [raw/articles/lmax-architecture-martin-fowler.md]
confidence: medium
---

# Disruptor

The Disruptor is the concurrency component used around the LMAX business core. Fowler describes it as something that can look like a graph of queues from the outside, but internally behaves more like a shared ring-buffer data structure designed to reduce contention and coordinate multiple processing stages efficiently.

## Role in the architecture

- The input disruptor handles unmarshalling, journaling, and replication before work reaches the core.
- Output disruptors handle publishing responses and events after the core has processed them.
- The structure helps separate IO concurrency from the single-threaded business logic processor.

## Why it matters

- It supports the low-latency goals of [[lmax]].
- It reflects the hardware-aware thinking captured by [[mechanical-sympathy]].
- It is part of the broader argument that concurrency design should minimize cache-hostile coordination.

## Related pages

[[lmax]] · [[the-lmax-architecture]] · [[event-sourcing]] · [[mechanical-sympathy]]
