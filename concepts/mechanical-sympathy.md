---
title: Mechanical Sympathy
created: 2026-06-26
updated: 2026-06-26
type: concept
tags: [concept, performance, architecture]
sources: [raw/articles/lmax-architecture-martin-fowler.md]
confidence: medium
---

# Mechanical Sympathy

Mechanical sympathy is the idea that software should be shaped around the actual behavior of the hardware it runs on. In Fowler's LMAX article, that means paying close attention to cache behavior, memory contention, and the performance consequences of multiple threads writing to shared locations.

## What the article emphasizes

- Queue-heavy designs can hide expensive coordination costs.
- Single-writer designs can behave better with modern caches.
- Architecture should treat CPU and memory behavior as first-class design constraints.

## Why it matters

This concept helps explain why the LMAX team preferred serialized mutation in the core over more conventional parallel request handling. It is a useful lens for evaluating hot paths, concurrency strategies, and whether a system's bottlenecks are actually computational or coordination-based.

## Related pages

[[lmax]] · [[the-lmax-architecture]] · [[event-sourcing]] · [[disruptor]]
