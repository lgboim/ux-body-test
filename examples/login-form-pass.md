# Body Test Example: Login Form (PASS)

**Subject:** Standard email/password login form with "Remember me" and "Forgot password" link.

```
┌─────────────────────────────────┐
│         Welcome back            │
│                                 │
│  Email                          │
│  [user@example.com          ]   │
│                                 │
│  Password                       │
│  [••••••••••••••••          ]   │
│                                 │
│  ☐ Remember me                  │
│                                 │
│  [        Sign in        ]      │
│                                 │
│  Forgot your password?          │
└─────────────────────────────────┘
```

---

## Layer 1: First Contact

```
FIRST CONTACT:
- Eye lands on: "Welcome back" heading → appropriate (confirms location/purpose)
- Unclear elements: none
- Primary action: "Sign in" button → obvious (single CTA, high contrast)
- 3-second mental model: "This is a login screen where I can sign into my account" → clear
- Verdict: PASS
```

## Layer 2: Physical Metaphor

```
PHYSICAL METAPHOR:
- Spatial persistence: n/a (single screen, no navigation state)
- Action-reaction: form submission → loading state → redirect (proportional)
- Visual weight: heading > fields > button > secondary link (balanced top-to-bottom flow)
- Containment logic: email and password visually grouped as "credentials", secondary actions separated below
- Flow direction: top-to-bottom, matches reading direction and natural task sequence
- Verdict: PASS
```

## Layer 3: Affordance Test

```
AFFORDANCE TEST:
- Email field: convention (rectangular input box → type here)
- Password field: convention + physical hint (bullet masking signals "sensitive input")
- Remember me checkbox: physical (square box → check/uncheck)
- Sign in button: convention (filled rectangle with label)
- Forgot password: convention (underlined/colored text → clickable link)
Critical issues: none
- Verdict: PASS
```

## Layer 4: Cognitive Budget

```
COGNITIVE BUDGET:
- Simultaneous decisions: 3 (fill in credentials, toggle remember-me, choose sign in or forgot password) → fine
- Novel concepts: 0 → manageable
- Steps to primary task: 3 (enter email, enter password, click sign in) (minimum possible: 3)
- Escape routes: browser back always available; no destructive action on this screen
- Status clarity: clear (form state is visible; error states should display inline)
- Verdict: PASS
```

## Layer 5: Expectation Consistency

```
EXPECTATION CONSISTENCY:
- Action: click Sign in → Expected: redirect to dashboard or error message → Actual: same → Gap: none
- Action: click Forgot password → Expected: navigate to password reset flow → Actual: same → Gap: none
- Action: toggle Remember me → Expected: session persists across browser restarts → Actual: same → Gap: none
Critical gaps: none
- Verdict: PASS
```

---

```
═══════════════════════════════════════
BODY TEST SUMMARY
═══════════════════════════════════════
First Contact:     PASS
Physical Metaphor: PASS
Affordance:        PASS
Cognitive Budget:  PASS
Expectation:       PASS
───────────────────────────────────────
Overall:           PASS
═══════════════════════════════════════

Top issues: none

Notes:
- Cognitive budget is naturally low because login is an intrinsically simple task
- The "Remember me" label is slightly ambiguous (does it mean "remember my email"
  or "keep me logged in"?) — consider "Keep me signed in" for clarity
```
