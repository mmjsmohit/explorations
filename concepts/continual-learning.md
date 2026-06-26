---
title: Continual learning in LLMs
created: 2026-06-26
updated: 2026-06-26
type: concept
tags: [concept, reference]
sources: [raw/transcripts/what-does-the-next-training-paradigm-look-like.md]
confidence: medium
---

# Continual learning in LLMs

Continual learning means improving the model from deployment experience, not just from pretraining or static RL runs. In the talk, the key claim is that important information often only appears during real use, so a model that never updates its weights is leaving valuable signal on the table.

In-context learning is sample-efficient, but it is a poor long-term storage mechanism. The essay argues that if a model keeps learning only through the context window, it may retain session details without consolidating the durable intuitions that matter across jobs, companies, and users.

## Core points

- Real deployments expose organization-specific and user-specific tacit knowledge that training runs miss.
- Session memory in context is useful, but it does not scale as a substitute for learned weights.
- The hard part is finding an update rule that is sparse enough to avoid overwriting useful knowledge.
- Continued improvement depends on turning messy interaction traces into compact weight updates.

## Related pages

[[rlvr]] · [[on-policy-self-distillation]] · [[dreaming]] · [[computer-use-in-llms]]
