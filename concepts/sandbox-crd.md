---
title: Sandbox CRD
created: 2026-06-26
updated: 2026-06-26
type: concept
tags: [concept, architecture, devops]
sources: [raw/articles/agent-sandbox-overview.md]
confidence: medium
---

# Sandbox CRD

The Sandbox CRD is the central abstraction in Agent Sandbox. It gives Kubernetes users a declarative way to request a single isolated runtime with stable identity and persistent state, without assembling the behavior manually from lower-level primitives.

## What it bundles

- Stable hostname and network identity.
- Persistent storage that survives restarts.
- Controller-managed lifecycle operations such as pause, resume, and scheduled deletion.
- A path for extensions like warm pools and claims to sit on top of the core abstraction.

## Why it matters

This concept sits between familiar Kubernetes patterns: it is more specialized than a Deployment and more focused than a generic StatefulSet. For agent infrastructure, that makes it a useful building block for [[context-isolation]] and for workloads driven by [[computer-use-in-llms]].

## Related pages

[[agent-sandbox]] · [[agent-sandbox-overview]] · [[context-isolation]] · [[computer-use-in-llms]]
