---
title: Dreaming for LLM continual learning
created: 2026-06-26
updated: 2026-06-26
type: concept
tags: [concept, reference]
sources: [raw/transcripts/what-does-the-next-training-paradigm-look-like.md]
confidence: low
---

# Dreaming for LLM continual learning

"Dreaming" is the essay's speculative idea that a model could build or refine its own simulated environments, then rehearse new skills against those environments to manufacture more training signal. If it works, this would create a fourth axis of scaling alongside pretraining, RL, and inference-time compute.

The appeal is sample efficiency: the model could practice repeatedly on synthetic rollouts that resemble the real world closely enough to matter. The obvious limitation is that the world is much harder to simulate faithfully than a game like Go or Atari.

## Core points

- The model would spend compute creating and training against its own simulations.
- The idea is meant to help with sparse, expensive, real-world learning.
- It is more speculative than RLVR or OPSD.
- It depends on building simulations that are faithful enough to transfer.

## Related pages

[[continual-learning]] · [[rlvr]] · [[agent-sandbox]] · [[sandbox-crd]]
