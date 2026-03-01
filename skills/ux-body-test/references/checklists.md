# Body Test Quick-Reference Checklists

Use these when you need fast evaluation without the full protocol. Each checklist maps to one layer. Any "No" answer is a finding worth noting.

---

## Layer 1: First Contact

- [ ] Does the eye land on the most important element first?
- [ ] Can every visible element's purpose be identified from appearance alone?
- [ ] Is there exactly one obvious primary action?
- [ ] Can someone complete the sentence "This is a ___ where I can ___" in 3 seconds?

**Fail threshold:** Any "No" → investigate further.

---

## Layer 2: Physical Metaphor

- [ ] Do navigated-away-from screens retain their state when revisited?
- [ ] Does every user action produce a visible, proportional response?
- [ ] Is visual weight distributed so heavier elements anchor the layout (not float)?
- [ ] Are related things visually contained together?
- [ ] Does forward progress move in the reading direction (left-to-right for LTR)?

**Fail threshold:** "No" on action-reaction or spatial persistence → FAIL.

---

## Layer 3: Affordance

- [ ] Does every interactive element look interactive?
- [ ] Does every non-interactive element look non-interactive?
- [ ] Can every element be classified as: physical / learned-convention / novel?
- [ ] Are there zero false affordances (looks clickable but isn't, or does something unexpected)?
- [ ] If any element is "novel," is it the core value prop with explicit onboarding?

**Fail threshold:** Any false affordance → FAIL. Any unjustified novel interaction → WARNING.

---

## Layer 4: Cognitive Budget

- [ ] Fewer than 7 simultaneous choices? (4 or fewer = comfortable)
- [ ] Fewer than 3 novel concepts requiring active learning?
- [ ] Can the primary task be completed in the minimum possible number of steps?
- [ ] Is there always a visible way to go back / undo / escape?
- [ ] Does the user always know: where they are, what state the system is in, what just happened?

**Fail threshold:** 8+ simultaneous choices → FAIL. Missing escape routes → FAIL.

---

## Layer 5: Expectation Consistency

For each primary interaction, check: "When I [action], I expect [X]. Does X happen?"

- [ ] Submit / Save → confirmation or clear next state?
- [ ] Back / Cancel → returns to previous state without data loss?
- [ ] Scroll down and back → content in same position?
- [ ] Tap a card / list item → goes somewhere related to that item?
- [ ] Any loading state → progress indicator visible?
- [ ] Any destructive action → confirmation requested before executing?

**Fail threshold:** Any gap that causes data loss or navigation confusion → FAIL.

---

## Scoring Reference

| Result  | Meaning |
|---------|---------|
| PASS    | No significant issues on this layer |
| WARNING | Friction exists but recoverable; note as known tradeoff |
| FAIL    | Will cause confusion, errors, or abandonment for real users |

**Overall verdict:** Any single FAIL = overall FAIL. Three or more WARNINGs = overall WARNING.
