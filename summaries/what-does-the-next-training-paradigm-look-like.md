---
title: What Does the Next Training Paradigm Look Like?
created: 2026-06-26
updated: 2026-06-26
type: summary
tags: [concept, reference]
sources: [raw/transcripts/what-does-the-next-training-paradigm-look-like.md]
confidence: medium
---

# What Does the Next Training Paradigm Look Like?

This talk argues that the next frontier after plain RL on verifiable tasks is better ways to turn scarce real-world experience into durable model improvements. The central tension is between scaling on replayable environments and learning from messy, non-repeatable settings such as real computer use, business operations, and deployment feedback.

## Key takeaways

- RLVR can improve agents on verifiable tasks, but the talk argues that many valuable domains are not grindable enough for brute-force simulation.
- Computer use is verifiable, yet progress is slower because the tasks are hard to replay at scale and harder to clone into deterministic environments.
- Continual learning likely requires updating weights, not just stretching the context window.
- On-policy self-distillation is presented as a denser, more targeted alternative to naïve supervised fine-tuning for distilling session learning.
- "Dreaming" is the speculative idea of building simulated environments to rehearse skills and amplify sample efficiency.
- Broad deployment could become a training signal if future systems can consolidate real-world experience back into the model.

## Related pages

[[continual-learning]] · [[rlvr]] · [[on-policy-self-distillation]] · [[dreaming]] · [[computer-use-in-llms]]
