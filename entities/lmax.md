---
title: LMAX
created: 2026-06-26
updated: 2026-06-26
type: entity
tags: [entity, architecture, performance]
sources: [raw/articles/lmax-architecture-martin-fowler.md]
confidence: medium
---

# LMAX

LMAX is the trading platform described in Martin Fowler's article as an example of a high-throughput, low-latency architecture built around a single-threaded business core. In this source, LMAX matters less as a company profile and more as a concrete proof point that architecture can trade parallel business logic for sequential mutation and still win on performance.

## What stands out

- All business logic runs on one thread in the core processor.
- The core keeps working state in memory instead of reading and writing a database on every request.
- Durability and recovery come from [[event-sourcing]].
- Coordination around the core uses the [[disruptor]] rather than conventional queue-heavy designs.

## Related pages

[[the-lmax-architecture]] · [[event-sourcing]] · [[disruptor]] · [[mechanical-sympathy]]
