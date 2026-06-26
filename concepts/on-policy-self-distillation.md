---
title: On-policy self-distillation
created: 2026-06-26
updated: 2026-06-26
type: concept
tags: [concept, reference]
sources: [raw/transcripts/what-does-the-next-training-paradigm-look-like.md]
confidence: medium
---

# On-policy self-distillation

On-policy self-distillation is the proposal to distill what a model learned during a session back into the base weights by matching the predictions of the session-augmented teacher model. In the talk, it is framed as a practical route to continual learning when outer-loop verifiable rewards are unavailable.

The argument is that this is better than naïve supervised fine-tuning for the problem. Rather than replaying the full transcript, the goal is to capture only the information that actually changed the agent's decisions on real tasks.

## Core points

- It does not require a clean external reward signal.
- It provides denser supervision than a sparse RL reward on the whole trajectory.
- It aims to keep only the knowledge relevant to task success.
- It is meant to complement continual learning without overwriting the base model wholesale.

## Related pages

[[continual-learning]] · [[rlvr]] · [[dreaming]]
