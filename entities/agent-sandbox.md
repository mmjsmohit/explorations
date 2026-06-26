---
title: Agent Sandbox
created: 2026-06-26
updated: 2026-06-26
type: entity
tags: [entity, tooling, devops]
sources: [raw/articles/agent-sandbox-overview.md]
confidence: medium
---

# Agent Sandbox

Agent Sandbox is a Kubernetes SIG Apps project for running isolated, stateful, singleton workloads with stable identity. The overview positions it as a good fit for AI agent runtimes, development environments, and other cases where a single long-lived execution environment is easier to reason about than a replicated application deployment.

## Notable characteristics

- Defines a `Sandbox` CRD as the top-level interface.
- Preserves stable network identity and persistent storage across restarts.
- Supports lifecycle operations such as creation, scheduled deletion, pause, and resume.
- Adds higher-level allocation patterns through `SandboxTemplate`, `SandboxClaim`, and `SandboxWarmPool`.

## Relevance

The project is interesting here because it turns [[context-isolation]] into an infrastructure primitive and gives [[computer-use-in-llms]]-style agents a safer place to run tools or untrusted generated code.

## Related pages

[[agent-sandbox-overview]] · [[sandbox-crd]] · [[context-isolation]] · [[computer-use-in-llms]]
