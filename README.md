<div align="center">

# 🧠 UX Body Test

**A UX evaluation skill for AI agents that simulates how a real human experiences your interface.**

[![Install](https://img.shields.io/badge/npx%20skills%20add-lgboim%2Fux--body--test-4A90E2?style=for-the-badge&logo=npm)](https://skills.sh/lgboim/ux-body-test)
[![License: MIT](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](LICENSE)
[![Works with Claude](https://img.shields.io/badge/Works%20with-Claude-blueviolet?style=for-the-badge)](https://claude.ai)

Works with **Claude · Cursor · Copilot · Gemini CLI · Cline · Codex · Amp** and more.

</div>

---

## The Problem

AI can generate interfaces that follow every design system rule and still feel wrong to real humans. Why? Because machines understand UI as tokens — signifiers pointing to other signifiers. Humans understand UI through bodies — we know scissors work because the holes look like our fingers.

Design systems like Material Design created an invisible eval: *if it fits the pattern, it's probably fine.* But pattern compliance ≠ usability. There's no compiler error for bad UX.

---

## What This Skill Does

The Body Test forces AI to simulate how a person with a **physical body, spatial memory, and limited cognitive budget** actually experiences an interface — before declaring any UI "done."

It runs five structured layers and produces **PASS / WARNING / FAIL** verdicts with specific findings and fixes.

---

## Install

```bash
npx skills add lgboim/ux-body-test
```

That's it. The skill activates automatically whenever your agent builds or reviews any UI.

---

## Quick Demo

After installing, the agent runs the Body Test before presenting any UI:

```
[Agent builds a dashboard component, then self-evaluates before showing you]

BODY TEST — Analytics Dashboard

FIRST CONTACT:
- Eye lands on: top nav logo → misplaced (logo is not the action)
- Unclear elements: 3 icon-only buttons with no labels or tooltips
- Primary action: none obvious → paralysis (3 equally weighted CTAs)
- 3-second model: "This is a ___ where I can ___" → impossible to complete
- Verdict: ⚠️ WARNING

PHYSICAL METAPHOR:
- Spatial persistence: tabs retain state ✓
- Action-reaction: chart filter has no loading state — silent after click → broken physics
- Gravity: heaviest visual element (large chart) is top-left, nothing anchors the bottom
- Verdict: ❌ FAIL — fix loading state and visual weight distribution

AFFORDANCE:
- "Export" link looks like a label, not a button — no border, no hover state
- Date range picker has no visual affordance it's interactive
- Verdict: ⚠️ WARNING

COGNITIVE BUDGET:
- Counted 11 decisions on first screen: 3 nav items + 4 filters + 3 chart types + 1 date range
- Exceeds working memory limit (7 ± 2)
- Verdict: ❌ FAIL — collapse filters behind a single "Filter" button

EXPECTATION CONSISTENCY:
- "Save" button saves but doesn't confirm → leaves user uncertain
- Clicking a chart bar drills down — expected, consistent ✓
- Verdict: ⚠️ WARNING

OVERALL: ❌ FAIL (2 fails, 3 warnings) — revising before showing you...
```

---

## The Five Layers

| Layer | What It Checks | The Question |
|-------|----------------|--------------|
| **First Contact** | Can someone understand this in 3 seconds with zero context? | "Where do I look? What do I do?" |
| **Physical Metaphor** | Does it respect intuitive physics? | "If I scroll down and come back, is everything still where I left it?" |
| **Affordance** | Does every element look like what it does? | "Is this a button or a decoration?" |
| **Cognitive Budget** | How many decisions does one screen demand? | "Am I thinking about my task or about the interface?" |
| **Expectation Consistency** | Does what happens match what I expected? | "I clicked Save — did anything happen?" |

---

## When It Triggers

- **After generating any UI code** — runs before presenting it to you
- **When reviewing a screenshot or wireframe** you share
- **When you ask "is this good UX?"** or anything about usability
- **When iterating on a design** — runs each round to track improvement

Like a linter, but for human experience.

---

## What's Inside

```
skills/
  ux-body-test/
    SKILL.md                        ← Agent instructions (the five layers)
    references/
      theory.md                     ← Theoretical framework (Saussure, Norman, cognitive load)
      checklists.md                 ← Quick-reference checklists for rapid evaluation
    examples/
      login-form-pass.md            ← Full walkthrough: simple form (all PASS)
      analytics-dashboard-fail.md   ← Full walkthrough: complex dashboard (multiple FAIL)
```

---

## Theoretical Background

The framework draws on:
- **Saussure's signifier/signified distinction** — why machines miss embodied meaning
- **Don Norman's affordance theory** — the scissors test
- **Cognitive load theory** — working memory budgets for UI (Miller's Law: 7 ± 2)
- **Expectation violation research** — the gap between what users expect and what happens

See `skills/ux-body-test/references/theory.md` for the full deep-dive.

---

## Compatible Agents

Installs as a universal skill. Works with:

**Claude** · **Cursor** · **GitHub Copilot** · **Gemini CLI** · **Cline** · **OpenAI Codex** · **Amp** · **Zed AI** · **Continue**

---

## Also See

If you want empirical UX principles with quantified data (Baymard Institute, WCAG thresholds, A/B test findings), check out the companion skill:

```bash
npx skills add lgboim/ux-builder
```

The two skills are complementary — Body Test catches what *feels* wrong, UX Builder enforces what the research *proves*.

---

## License

MIT © [lgboim](https://github.com/lgboim)
