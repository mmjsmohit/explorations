---
source_url: https://martinfowler.com/articles/lmax.html
ingested: 2026-06-26
sha256: 19e90b53670d803af5927e60fbf253c5f41022c1f3b63ecc70578381ac50ee98
---

# The LMAX Architecture — Comprehensive Summary

**Source:** Martin Fowler, 12 July 2011  
**Topic:** High-performance trading architecture on the JVM using a **single-threaded in-memory business core**, **event sourcing**, and the **Disruptor** concurrency component.

---

## Executive Summary

LMAX built a retail financial trading platform that handles **very high throughput with very low latency** by doing something counterintuitive for the multi-core era:

> **All business logic for all trades, customers, and markets runs on a single thread.**

Key claims and characteristics:

- **~6 million orders per second** on a **single thread**
- Runs on **commodity hardware**
- Business core is:
  - **single-threaded**
  - **entirely in-memory**
  - **event-sourced**
- Surrounding IO/concurrency concerns are handled by **Disruptors**
- The architecture is based on **mechanical sympathy**: designing software to match modern CPU/cache behavior
- Core insight: **traditional queue-heavy concurrency can fight modern hardware**, especially cache behavior and single-writer principles

---

## Key Excerpts

### Core positioning

> “the free lunch is over”

> “all the business logic for their platform: all trades, from all customers, in all markets - on a single thread.”

> “A thread that will process 6 million orders per second using commodity hardware.”

### Core architectural idea

> “The Business Logic Processor takes input messages sequentially (in the form of a method invocation), runs business logic on it, and emits output events.”

> “It operates entirely in-memory, there is no database or other persistent store.”

### Event sourcing

> “the current state of the Business Logic Processor is entirely derivable by processing the input events.”

### Disruptor concept

> “At a crude level you can think of a Disruptor as a multicast graph of queues...”

> “When you look inside you see that this network of queues is really a single data structure - a ring buffer.”

### Mechanical sympathy

> “The phrase Martin Thompson likes to use is ‘mechanical sympathy’.”

> “The conclusion they came to was that to get the best caching behavior, you need a design that has only one core writing to any memory location”

### Memorable storage quote

> “disk is the new tape”

---

## Architecture Overview

LMAX has **three main parts**:

- **Business Logic Processor**
- **Input Disruptor**
- **Output Disruptors**

### Responsibilities

#### 1) Business Logic Processor
Handles all domain/business logic:

- single-threaded Java program
- responds to method calls
- emits output events
- no framework dependency beyond JVM
- easy to run in test environments

#### 2) Input Disruptor
Handles inbound processing before the core logic:

- receives network messages
- unmarshals messages
- journals input events durably
- replicates events to other nodes

#### 3) Output Disruptors
Handles outbound processing after the core logic:

- marshals output events for network transmission
- organizes outputs by topic
- each topic has its own disruptor

---

## Why This Architecture Exists

LMAX needed:

- **very low latency**
- **high throughput**
- support for a **retail-scale** trading platform
- predictable behavior during **bursts and micro-bursts**

Important operational context:

- Traditional professional trading systems may have **hundreds of users**
- Retail trading can mean **far more users**
- Real activity is dominated by **market makers**
- During volatility:
  - an instrument can get **hundreds of updates per second**
  - with **micro-bursts of hundreds of transactions within a single microsecond**

### Benchmark hardware

The famous **6 million TPS** number was measured on:

- **3Ghz dual-socket quad-core Nehalem Dell server**
- **32GB RAM**

---

## Business Logic Processor

### Keep Everything In Memory

The processor:

- consumes input events sequentially
- executes business logic
- emits output events
- has **no database**
- uses **no persistent store in the request path**

### Benefits

#### Performance
- avoids database IO
- avoids transactional DB overhead
- sequential processing eliminates inter-thread coordination inside the core

#### Simplicity
- no ORM impedance mismatch
- pure Java object model
- easier domain modeling

---

## Event Sourcing and Recovery

LMAX addresses the “what if memory is lost?” question with **Event Sourcing**.

### Principle

- Current state is fully reconstructible from input events
- Input event stream is durably stored by the input disruptor
- State can be rebuilt by replaying events

### Analogy used
Like a **version control system**:

- commits = events
- current working copy = reconstructed state
- the stream is linear, not branching

### Snapshots

Replay-from-zero is too slow in practice, so LMAX also uses:

- **nightly snapshots**
- restore from snapshot + replay recent journal

---

## Mechanical Sympathy

A major architectural theme is that software structure should respect hardware realities:

- CPU caches matter
- memory contention matters
- one-writer designs are often friendlier to hardware than many lock-heavy writers
- queues and contention can become the true bottleneck

---

## Why the article matters

The article is influential because it treats architecture as a performance model, not just a decomposition exercise. It links domain design, concurrency control, storage strategy, and hardware behavior into one coherent system.
