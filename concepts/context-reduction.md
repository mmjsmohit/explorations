---
title: Context Reduction
created: 2026-06-26
updated: 2026-06-26
type: concept
tags: [concept, workflow]
sources: [raw/articles/manus-context-engineering-langchain-webinar.md]
confidence: medium
---

# Context Reduction

Context reduction is the practice of shrinking working context before it becomes noisy or stale. The webinar contrasts compaction with summarization and frames reduction as a response to pre-rot thresholds and long-running sessions.

## Compaction vs. summarization

- **Compaction** preserves recent state by collapsing history into a denser form.
- **Summarization** compresses older content into a smaller representation.
- In practice, the right choice depends on how much fidelity the task still needs.

## Why it matters

- Long sessions accumulate noise.
- Reduction keeps the model focused on what still matters.
- Better reduction can lower the need for heavy agent memory.

## Related pages

[[context-engineering]] · [[context-offloading]] · [[manus-context-engineering-webinar]]
