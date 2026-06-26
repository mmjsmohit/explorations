---
title: Agent Sandbox Overview
created: 2026-06-26
updated: 2026-06-26
type: summary
tags: [reference, tooling, architecture]
sources: [raw/articles/agent-sandbox-overview.md]
confidence: medium
---

# Agent Sandbox Overview

Agent Sandbox is presented as a Kubernetes-native way to run isolated, stateful, singleton workloads with stable identity, especially for AI agent runtimes. The core move is to introduce a `Sandbox` CRD so operators do not need to approximate this pattern with a size-1 StatefulSet plus extra services and persistent storage plumbing.

## Key takeaways

- The project is aimed at long-running workloads that need stable hostnames, persistent storage, and lifecycle controls such as pause and resume.
- The `Sandbox` CRD acts as the main abstraction and follows the normal Kubernetes controller pattern.
- The extensions layer adds templates, warm pools, and claims so teams can allocate sandboxes faster and with less repeated configuration.
- The examples make the project especially relevant to AI agent runtimes, development environments, and notebook-style tools.

## Why it matters for this wiki

Agent Sandbox is a concrete infrastructure pattern for [[context-isolation]] when agent workloads need process and filesystem boundaries, not just prompt-level separation. It also connects to [[computer-use-in-llms]] because those agents often need disposable but resumable execution environments.

## Related pages

[[agent-sandbox]] · [[sandbox-crd]] · [[context-isolation]] · [[computer-use-in-llms]]
