---
title: Event Sourcing
created: 2026-06-26
updated: 2026-06-26
type: concept
tags: [concept, architecture, database]
sources: [raw/articles/lmax-architecture-martin-fowler.md]
confidence: medium
---

# Event Sourcing

Event sourcing is the pattern of treating the input event stream as the durable system record, with current state reconstructed by replaying those events. In the LMAX architecture, this allows the business logic processor to keep all active state in memory without giving up recoverability.

## What the article emphasizes

- The system journals input events durably before they are fully relied on.
- The current state of the business core is derivable from the event history.
- Recovery is sped up with snapshots plus replay of newer events.
- The pattern simplifies the write path because the hot path does not need a traditional transactional database.

## Trade-offs

- Replay from zero can be too slow without snapshots.
- The event log becomes a central systems primitive, not just an audit trail.
- Consumers need clear event schemas and replay semantics.

## Related pages

[[lmax]] · [[the-lmax-architecture]] · [[disruptor]] · [[mechanical-sympathy]]
