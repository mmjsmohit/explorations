---
source_url: https://agent-sandbox.sigs.k8s.io/docs/getting_started/overview/
ingested: 2026-06-26
sha256: 31ac8033c7d4f51d0dedf1921d2acc400c18e0b31c6c670f08d702dcecc9cc83
---

# Agent Sandbox — Overview Summary

## What it is

> **“agent-sandbox enables easy management of isolated, stateful, singleton workloads, ideal for use cases like AI agent runtimes.”**

Agent Sandbox is a Kubernetes project under **SIG Apps** that provides a **`Sandbox` Custom Resource Definition (CRD)** and controller for managing:

- **isolated**
- **stateful**
- **singleton**
- **long-running**
- **stable-identity**

workloads.

It aims to offer a **declarative, standardized API** for workloads that need something closer to a **lightweight, single-container VM experience**, using Kubernetes primitives.

**Links:**
- Website: https://agent-sandbox.sigs.k8s.io/
- Docs: https://agent-sandbox.sigs.k8s.io/docs/
- DeepWiki: https://deepwiki.com/kubernetes-sigs/agent-sandbox
- Getting Started: https://agent-sandbox.sigs.k8s.io/docs/getting_started/
- Examples: https://agent-sandbox.sigs.k8s.io/docs/use-cases/examples/
- Roadmap: https://github.com/kubernetes-sigs/agent-sandbox/blob/main/roadmap.md

---

## Core concept: `Sandbox`

The **`Sandbox` CRD** is the main abstraction.

### What it provides
- **Stable Identity:** stable hostname and network identity
- **Persistent Storage:** survives restarts
- **Lifecycle Management:** controller handles:
  - creation
  - scheduled deletion
  - pausing
  - resuming

### Why it exists
It fills a gap between:
- **Deployments**: good for stateless, replicated apps
- **StatefulSets**: good for stable, numbered stateful sets

But some workloads need a **single persistent pod with stable identity** without the overhead or awkwardness of approximating it via:
- StatefulSet of size 1
- Service
- PersistentVolumeClaim

---

## Extensions

The `extensions` module adds higher-level CRDs/controllers built on top of `Sandbox`.

### Extension resources
- **`SandboxTemplate`**
  - reusable templates for creating Sandboxes
  - useful when managing many similar Sandboxes

- **`SandboxClaim`**
  - lets users create Sandboxes from a `SandboxWarmPool`
  - hides underlying Sandbox configuration details

- **`SandboxWarmPool`**
  - maintains pre-warmed Sandboxes
  - reduces startup time for new allocations

---

## Architecture

Agent Sandbox follows the **Kubernetes controller pattern**:
1. A user creates a `Sandbox` custom resource.
2. The controller reconciles it.
3. The controller creates and manages the underlying runtime resources.

**Implied relationships:**
- Extensions create/reference/adopt Sandboxes
- `Sandbox` creates a Pod
- `SandboxWarmPool` pre-warms Sandboxes
- `SandboxClaim` can draw from the warm pool

---

## Installation

## Core controller and CRDs

```sh
# Replace "vX.Y.Z" with a specific version tag (e.g., "v0.1.0") from
# https://github.com/kubernetes-sigs/agent-sandbox/releases
export VERSION="vX.Y.Z"

# To install only the core components:
kubectl apply -f https://github.com/kubernetes-sigs/agent-sandbox/releases/download/${VERSION}/manifest.yaml

# To install the extensions components:
kubectl apply -f https://github.com/kubernetes-sigs/agent-sandbox/releases/download/${VERSION}/extensions.yaml
```

### Notes
- Use a **specific release tag** from GitHub Releases.
- `manifest.yaml` installs **core components**
- `extensions.yaml` installs **extensions**

---

## Python SDK

A **Python SDK** is available for programmatic interaction.

### Purpose
- high-level interface for creating and managing sandboxes

### Docs
- Python SDK README: https://github.com/kubernetes-sigs/agent-sandbox/blob/main/clients/python/agentic-sandbox-client/README.md

---

## Configuration

For **advanced scale and concurrency tuning**, see the configuration guide:

- API QPS
- worker counts

Guide:
- https://github.com/kubernetes-sigs/agent-sandbox/blob/main/docs/configuration.md

---

## Quick start

Apply this `Sandbox` resource:

```yaml
apiVersion: agents.x-k8s.io/v1beta1
kind: Sandbox
metadata:
  name: my-sandbox
spec:
  podTemplate:
    spec:
      containers:
      - name: my-container
        image: <IMAGE>
```

### Result
- Creates a Sandbox named **`my-sandbox`**
- Runs the specified container image
- Accessible using its stable hostname: **`my-sandbox`**

### More examples
- Examples: https://agent-sandbox.sigs.k8s.io/docs/use-cases/examples/
- Extension examples: https://github.com/kubernetes-sigs/agent-sandbox/blob/main/extensions/examples

---

## Motivation and target use cases

Agent Sandbox is intended for workloads that Kubernetes does not model cleanly with standard primitives alone.

### Example use cases
- **Development Environments**
  - isolated, persistent, network-accessible cloud environments

- **AI Agent Runtimes**
  - isolated environments for executing **untrusted, LLM-generated code**

- **Notebooks and Research Tools**
  - persistent, resumable, user-specific runtime environments
