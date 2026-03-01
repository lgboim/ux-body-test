# 🧠 The Body Test

**A UX evaluation skill for AI agents that simulates human embodied cognition.**

AI can generate interfaces that follow every design system rule and still feel wrong to real humans. Why? Because machines understand UI as tokens — signifiers pointing to other signifiers. Humans understand UI through bodies — we know scissors work because the holes look like our fingers.

The Body Test bridges this gap. It's a structured protocol that forces AI to simulate how a person with a physical body, spatial memory, and limited cognitive budget actually experiences an interface.

## The Five Layers

| Layer | What It Checks | The Question |
|-------|---------------|--------------|
| **First Contact** | Can someone understand this screen in 3 seconds with zero context? | "Where do I look? What do I do?" |
| **Physical Metaphor** | Does the interface respect intuitive physics? | "If I scroll down and come back, is stuff still where I left it?" |
| **Affordance** | Does every element look like what it does? | "Is this a button or a decoration?" |
| **Cognitive Budget** | How many decisions does one screen demand? | "Am I thinking about my task or about the interface?" |
| **Expectation Consistency** | Does what happens match what I expected? | "I clicked Save — did anything happen?" |

Each layer produces a **PASS / WARNING / FAIL** verdict with specific findings and actionable fixes.

## Install

```bash
npx skills add YOUR_USERNAME/ux-body-test
```

Works with Claude Code, Cursor, Codex, Gemini CLI, and [40+ other agents](https://skills.sh).

## When It Triggers

The skill activates automatically when an AI agent:
- Generates any UI code (React, HTML, etc.)
- Reviews a screenshot or wireframe
- Gets asked about usability or UX quality
- Iterates on a design

It runs as a self-check before presenting UI to the user — like a linter, but for human experience.

## Background

Inspired by a [conversation](https://www.linkedin.com/feed/) about AI maturity levels in software development and the observation that there's no "compiler error" for bad design. Design systems like Material Design created an invisible eval — if it fits the pattern, it's probably fine — but pattern compliance ≠ usability.

The theoretical framework draws on:
- **Saussure's signifier/signified distinction** — why machines miss embodied meaning
- **Don Norman's affordance theory** — the scissors test
- **Cognitive load theory** — working memory budgets for UI
- **Expectation violation research** — the gap between what users expect and what happens

Full theoretical reference included in `references/theory.md`.

## Repo Structure

```
skills/
  ux-body-test/
    SKILL.md              ← Main skill instructions (the five layers)
    references/
      theory.md           ← Theoretical framework deep-dive
      checklists.md       ← Quick-reference checklists for rapid evaluation
    examples/
      login-form-pass.md          ← Full walkthrough: simple form (all PASS)
      analytics-dashboard-fail.md ← Full walkthrough: complex dashboard (multiple FAIL)
```

## License

MIT
