---
name: ux-body-test
description: Use when creating, reviewing, or iterating on any user interface — React components, HTML pages, mobile screens, wireframes, or Figma screenshots. Also use when generating UI code to self-evaluate before presenting to the user, or when asked anything about usability or UX quality. Runs a five-layer Body Test that simulates how a real human with a physical body, spatial memory, and limited cognitive budget experiences the interface — catching failures that pass every accessibility and design-system check but still feel wrong to real users.

---

# The Body Test: Human-Embodied UX Evaluation

## Why This Exists

There's no compiler error for bad UX. You can follow every Material Design guideline, pass every accessibility audit, use perfect contrast ratios and touch targets — and still produce an interface that confuses real humans. Design systems like Material, Bootstrap, and shadcn/ui created an invisible "eval" for design: if it fits the system's patterns, it's probably fine. But "fits the pattern" ≠ "works for humans."

The core problem: machines understand language as signifiers pointing to other signifiers. Humans understand the world through bodies — we know scissors because they look like they fit our hands. A machine doesn't have hands. This skill bridges that gap by forcing structured simulation of embodied human cognition before declaring any UI "done."

## When To Run This

Run the Body Test:
- **After generating any UI code** — before presenting it to the user
- **When reviewing a screenshot or wireframe** the user uploaded
- **When the user asks "is this good UX?"** or anything about usability
- **When iterating on a design** — run it each round to track improvement
- **When you notice yourself defaulting** to generic Material/Bootstrap patterns without thinking about whether they actually serve the use case

## The Five Layers

Work through these sequentially. Each layer produces a **pass/warning/fail** signal and concrete observations. At the end, synthesize into an overall assessment.

### Layer 1: First Contact (The 3-Second Test)

Simulate a person who has never seen this screen before. No context, no onboarding, no tooltip. They just landed here.

Ask yourself:
1. **Where does the eye land first?** Is that the most important element? If the eye lands on a decorative element or secondary action, that's a warning.
2. **What does each visible element appear to do?** Go element by element. If you can't articulate what something does from appearance alone, it fails.
3. **What's the obvious first action?** There should be exactly one clear thing to do. Zero obvious actions = confusion. Three equally weighted actions = paralysis.
4. **Can someone form a mental model in 3 seconds?** "This is a ___ where I can ___." If that sentence is hard to complete, the screen lacks a clear identity.

**Output format:**
```
FIRST CONTACT:
- Eye lands on: [element] → [appropriate/misplaced]
- Unclear elements: [list, or "none"]
- Primary action: [what it is] → [obvious/ambiguous/hidden]
- 3-second mental model: "[This is a ___ where I can ___]" → [clear/fuzzy/impossible]
- Verdict: [PASS / WARNING / FAIL]
```

### Layer 2: The Physical Metaphor Check

Every interaction carries an implicit physics. Humans expect digital interfaces to honor physical-world intuitions — not because interfaces are physical, but because our brains run on spatial reasoning that evolved for physical space.

Check each of these:
1. **Spatial persistence:** Things that were "above" stay above. If I scroll down and come back, what I saw before should still be there, not replaced by something else. Tabs I visited should retain state. Back buttons should take me back to where I was, not a reset version.
2. **Action-reaction:** Every user action should produce a visible, proportional response. Clicking a button with no feedback = broken physics. A tiny action causing a massive page restructure = disproportionate.
3. **Gravity and weight:** Heavier visual elements (larger, darker, more saturated) should be anchored — typically at the bottom or center. Lightweight elements (text, icons, subtle controls) float above. If the visual weight distribution feels "top-heavy" or unbalanced, note it.
4. **Containment:** Things that are grouped should look contained (card, section, shared background). Things that aren't related shouldn't be visually grouped. Physical proximity = conceptual proximity.
5. **Direction and flow:** The reading direction (LTR/RTL) creates an implicit "time arrow." Progress should move in the reading direction. Going backward should feel like going... backward.

**Output format:**
```
PHYSICAL METAPHOR:
- Spatial persistence: [respected/violated — describe where]
- Action-reaction: [proportional/missing/disproportionate]
- Visual weight: [balanced/top-heavy/unanchored]
- Containment logic: [consistent/leaking — where]
- Flow direction: [natural/reversed/unclear]
- Verdict: [PASS / WARNING / FAIL]
```

### Layer 3: The Affordance Test (The Scissors Test)

Don Norman's concept: an affordance is a property of an object that suggests how it can be used. Scissors have holes shaped like fingers. A door handle shaped to be pulled affords pulling. A flat plate affords pushing.

For every interactive element on the screen:
1. **Does it look like what it does?** A button should look pressable. A slider should look slideable. A link should look clickable. A drag handle should look grabbable.
2. **Category check for each element:**
   - **Physical affordance** (looks like a real-world object): Best case. Examples: toggle switch, slider, pressable button with depth/shadow.
   - **Learned convention** (doesn't look physical but users know it): Acceptable. Examples: hamburger menu, X to close, underlined text = link, three dots = more options.
   - **Neither physical nor conventional**: Danger zone. The element requires learning. This is only acceptable if (a) it's the core novel interaction of the product and (b) there's onboarding for it.
3. **False affordances:** Does anything look interactive but isn't? (Underlined text that isn't a link, card-like elements that don't click, elements with hover states that lead nowhere.) These are worse than missing affordances because they actively train users to distrust the interface.

**Output format:**
```
AFFORDANCE TEST:
For each interactive element:
- [Element]: [physical / convention / novel / false affordance]
Critical issues: [list elements that are novel without justification or are false affordances]
- Verdict: [PASS / WARNING / FAIL]
```

### Layer 4: Cognitive Budget

Humans have limited working memory (roughly 4±1 chunks at a time). Every decision, every new concept, every piece of unfamiliar UI drains the budget. Once it's spent, users either leave or make errors.

Evaluate:
1. **Decision count per screen:** How many choices does the user face simultaneously? Count buttons, links, tabs, form fields — anything that asks "what do you want?" More than 5-7 simultaneous decisions is a warning. More than 10 is a fail.
2. **Novel concepts:** How many things on this screen require learning? Every icon that isn't universally known, every non-standard interaction, every domain-specific term costs cognitive budget. More than 2 novel concepts per screen is risky.
3. **Steps to primary task:** Count the clicks/taps/actions from landing on this screen to completing the thing the user came here to do. Every step beyond the minimum is friction. What's the minimum possible? How far off is the current design?
4. **Escape routes:** Can the user always go back? Is it clear how to undo? Is there always a visible way to get to safety (home, back, close)? Missing escape routes cause panic-spending of cognitive budget.
5. **Status clarity:** At any given moment, does the user know: Where they are? What state the system is in? What just happened? What will happen next? Ambiguous status forces the user to spend budget figuring out context instead of doing their task.

**Output format:**
```
COGNITIVE BUDGET:
- Simultaneous decisions: [count] → [fine/heavy/overloaded]
- Novel concepts: [count and list] → [manageable/costly]
- Steps to primary task: [count] (minimum possible: [count])
- Escape routes: [always visible / sometimes missing / absent]
- Status clarity: [clear / partial / opaque]
- Verdict: [PASS / WARNING / FAIL]
```

### Layer 5: Expectation Consistency (The Surprise Test)

For every action a user can take, there's what they **expect** will happen and what **actually** happens. The gap between these is the single most important UX metric. Zero gap = invisible UX (the best kind). Large gap = confusion, frustration, distrust.

For each primary interaction:
1. **Write the expectation:** "When I [action], I expect [result]."
2. **Write the reality:** "When I [action], what actually happens is [result]."
3. **Measure the gap:** Are these the same? If not, how surprising is the difference?

Common expectation violations to watch for:
- Clicking "Save" but getting no confirmation
- Pressing "Back" but losing entered data
- Scrolling but content jumps or reloads
- Tapping a card but going somewhere unrelated to the card's content
- Submitting a form but staying on the same page with no feedback
- Opening a menu but finding options unrelated to the menu's label
- Expecting immediate action but getting a loading state with no progress indicator

**Output format:**
```
EXPECTATION CONSISTENCY:
For each primary interaction:
- Action: [user action] → Expected: [what they think] → Actual: [what happens] → Gap: [none/minor/major]
Critical gaps: [list any major gaps]
- Verdict: [PASS / WARNING / FAIL]
```

## Synthesis

After all five layers, produce a summary:

```
═══════════════════════════════════════
BODY TEST SUMMARY
═══════════════════════════════════════
First Contact:     [PASS/WARNING/FAIL]
Physical Metaphor: [PASS/WARNING/FAIL]
Affordance:        [PASS/WARNING/FAIL]
Cognitive Budget:  [PASS/WARNING/FAIL]
Expectation:       [PASS/WARNING/FAIL]
───────────────────────────────────────
Overall:           [PASS/WARNING/FAIL]
═══════════════════════════════════════

Top issues (prioritized by impact):
1. [Most critical finding]
2. [Second most critical]
3. [Third most critical]

Recommended fixes:
1. [Specific, actionable fix for issue 1]
2. [Specific, actionable fix for issue 2]
3. [Specific, actionable fix for issue 3]
```

## How to Apply When Generating UI

When you're creating UI code (not just reviewing), integrate the Body Test as a self-check loop:

1. **Before coding:** Think about the target user's mental model. What screen did they come from? What are they trying to do? Write it down for yourself.
2. **After first draft:** Run the full Body Test mentally against your own output. Don't present it to the user yet.
3. **Fix any FAILs** before showing the result. WARNINGs are acceptable but should be noted to the user as known tradeoffs.
4. **When presenting:** Include a brief Body Test summary — not the full output, just the overall verdict and any warnings. Example: "I ran this through the Body Test — it passes on all five layers, though the cognitive budget is tight with 6 simultaneous actions on the dashboard. I could simplify by collapsing the filters into a single dropdown if you'd prefer."

## Important Nuances

- **This is not a replacement for user testing.** It's a simulation that catches obvious problems. Real humans will always find things this framework misses.
- **Context matters enormously.** A complex dashboard for data analysts has a different cognitive budget than a checkout flow for consumers. Always calibrate expectations to the audience.
- **Convention is cultural.** Hamburger menus are "learned convention" in Western mobile apps but may not be in other contexts. Consider the target audience.
- **Breaking rules can be good design.** If a novel interaction is the core value proposition (like Tinder's swipe), it's not a failure — it's a deliberate investment that needs to be supported by onboarding and consistency.
- **Material/Bootstrap compliance means nothing on its own.** You can build a perfectly valid Material Design interface that is terrible to use. The system provides components, not usability.

## Reference

- `references/theory.md` — Theoretical framework behind each layer (Saussure, Norman, cognitive load, expectation research)
- `references/checklists.md` — Quick-reference checklists for rapid evaluation
- `examples/login-form-pass.md` — Full Body Test walkthrough: simple form that passes all five layers
- `examples/analytics-dashboard-fail.md` — Full Body Test walkthrough: complex dashboard with multiple failures
