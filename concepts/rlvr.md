---
title: RLVR
created: 2026-06-26
updated: 2026-06-26
type: concept
tags: [concept, reference]
sources: [raw/transcripts/what-does-the-next-training-paradigm-look-like.md]
confidence: medium
---

# RLVR

In the talk, RLVR is the training regime built around verifiable tasks and replayable environments. The point is that if an agent can be trained on enough containerized, deterministic problems, it may develop broader planning and problem-solving ability than the task distribution would suggest.

The essay is skeptical that this alone solves everything. RLVR can be powerful in domains with clean reset and evaluation loops, but many real-world problems are non-stationary, sparse, or too expensive to replay thousands of times from the same initial state.

## Core points

- RLVR benefits from deterministic rollouts and identical starting conditions.
- It appears well-suited to coding-like environments where tasks can be cloned and replayed.
- Its generalization to long-horizon, messy deployment settings is an open question.
- The talk treats RLVR as a necessary step toward deployable agents, not the end state.

## Related pages

[[continual-learning]] · [[computer-use-in-llms]] · [[on-policy-self-distillation]]
