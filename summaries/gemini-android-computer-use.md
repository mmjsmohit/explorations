---
title: Gemini Android Computer Use
created: 2026-06-26
updated: 2026-06-26
type: summary
tags: [reference, tooling, backend]
sources: [raw/articles/philschmid-gemini-android-computer-use-2026-06-25.md]
confidence: medium
---

# Gemini Android Computer Use

Phil Schmid's walkthrough turns [[computer-use-in-llms|computer use]] for [[gemini-3-5-flash|Gemini 3.5 Flash]] into a concrete Android control loop: capture a screenshot, let the model emit a structured action, execute it via ADB, and send back the refreshed screen until the task is done.

## Key takeaways

- The article uses Gemini's `mobile` computer-use environment, showing that the same capability announced for browser, mobile, and desktop can be driven against an Android emulator.
- The runtime bridge is thin but important: it maps model tool calls like `click`, `open_app`, `type`, and `drag_and_drop` onto ADB commands, then captures a fresh screenshot for the next model turn.
- Mobile actions use a normalized 0-999 coordinate grid, so the bridge must convert model coordinates into real device pixels before issuing taps and swipes.
- The quickstart script also handles practical setup work such as locating the Android SDK, starting an emulator if needed, waiting for boot completion, and then entering the model-action loop.

## Why it matters for this wiki

This source complements the earlier announcement-level notes on [[computer-use-in-llms|computer use in LLMs]] with implementation detail. It shows that the feature is not only a product surface on [[gemini-3-5-flash|Gemini 3.5 Flash]], but also an integration pattern that depends on a reliable execution bridge and state-refresh loop. It also reinforces why safeguards around [[prompt-injection]] matter once a model can drive real UI actions.

## Related pages

[[gemini-3-5-flash]] · [[computer-use-in-llms]] · [[prompt-injection]]
