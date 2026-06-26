---
title: Context Offloading
created: 2026-06-26
updated: 2026-06-26
type: concept
tags: [concept, tooling, architecture]
sources: [raw/articles/manus-context-engineering-langchain-webinar.md]
confidence: medium
---

# Context Offloading

Context offloading pushes work out of the context window and into files, sandboxes, and APIs. In the webinar, offloading also applies to tools: instead of stuffing every capability into the prompt, expose coarse-grained operations and let the agent invoke them as needed.

## Levels of offloading

- **Function calling** — schema-safe, but easy to overfit into prompt complexity.
- **Sandbox utilities** — shell tools in a VM; useful for large outputs and file-based work.
- **Packages & APIs** — scripted calls to pre-authorized services for chained or data-heavy tasks.

## Why it matters

- Tools themselves can clutter context.
- Offloading keeps the model context cleaner.
- Retrieval plus offloading makes reduction cheaper and more reliable.

## Related pages

[[context-engineering]] · [[context-reduction]] · [[context-isolation]] · [[manus-context-engineering-webinar]]
