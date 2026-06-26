---
title: Context Engineering
created: 2026-06-26
updated: 2026-06-26
type: concept
tags: [concept, workflow, tooling]
sources: [raw/articles/manus-context-engineering-langchain-webinar.md]
confidence: medium
---

# Context Engineering

Context engineering is the clearest boundary between the application and the model in agentic systems. Instead of treating context as an unlimited scratchpad, it treats the context window as a managed resource: what enters it, when it is reduced, how agents are isolated, and which work is offloaded elsewhere.

In the Manus webinar, this framing is presented as the practical way to ship agents without overfitting the model.

## Why it matters

- Model iteration limits product iteration.
- Do not rebuild capabilities the base-model provider already has.
- The right abstraction is often context management, not model customization.

## Related pages

[[manus-ai]] · [[context-reduction]] · [[context-isolation]] · [[context-offloading]] · [[manus-context-engineering-webinar]]
