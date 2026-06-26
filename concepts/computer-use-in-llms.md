---
title: Computer use in LLMs
created: 2026-06-26
updated: 2026-06-26
type: concept
tags: [concept, tooling, security]
sources: [raw/articles/x-2069819170477293863-gemini-3-5-flash-computer-use.md, raw/articles/philschmid-gemini-android-computer-use-2026-06-25.md, raw/transcripts/what-does-the-next-training-paradigm-look-like.md]
confidence: medium
---

# Computer use in LLMs

Computer use is a capability where an LLM receives a screen and goal, then decides which actions to take in order to complete the task. In the current wiki sources, it is described as available in [[gemini-3-5-flash|Gemini 3.5 Flash]] across browser, mobile, and desktop environments.

The Android walkthrough makes the execution loop concrete: a screenshot is sent to the model, the model returns structured actions such as `click`, `type`, `open_app`, or `drag_and_drop`, an external bridge executes them, and a fresh screenshot is fed back into the next turn. On mobile, those actions use a normalized 0-999 coordinate grid that must be converted into device-specific pixels before ADB can issue taps, swipes, and key events.

The later talk adds a research angle: computer use is verifiable, but it is not always grindable. The bottleneck is not whether a task can be checked, but whether it can be replayed from the same starting state across many deterministic rollouts. That makes UI automation harder to scale than coding-style environments and helps explain why model progress there has lagged.

The announcement-level source highlights safety mechanisms including user confirmation, auto-stop on [[prompt-injection]], and additional training against prompt injection. Taken together, the sources show computer use as both a promising automation interface and a security-sensitive control surface.

Related pages: [[gemini-3-5-flash|Gemini 3.5 Flash]], [[prompt-injection|prompt injection]], [[gemini-android-computer-use|Gemini Android Computer Use]], [[rlvr]], and [[continual-learning]].
