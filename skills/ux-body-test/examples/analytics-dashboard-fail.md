# Body Test Example: Analytics Dashboard (FAIL)

**Subject:** SaaS analytics dashboard — first screen after login, intended for non-technical marketing users.

```
┌──────────────────────────────────────────────────────────────┐
│  ≡  DataPulse   Overview  Reports  Segments  API  Settings   │
│─────────────────────────────────────────────────────────────│
│  ▼ Workspace: Acme Corp  [+ New]    ● Live   ⚙  Export  🔔  │
│─────────────────────────────────────────────────────────────│
│                                                              │
│  [Sessions] [Users] [Revenue] [Funnel] [Cohort] [Custom]    │
│                                                              │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐       │
│  │  12,430  │ │  $48.2K  │ │   3.2%   │ │  00:04:12│       │
│  │ sessions │ │ revenue  │ │conv. rate│ │avg session│      │
│  └──────────┘ └──────────┘ └──────────┘ └──────────┘       │
│                                                              │
│  [Line chart — unlabeled axes, 6 colored lines, no legend]  │
│                                                              │
│  Recent Events          Top Pages          Alerts (3)       │
│  [dense table]          [dense table]      [dense table]    │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

## Layer 1: First Contact

```
FIRST CONTACT:
- Eye lands on: top navigation bar → misplaced (decorative/structural, not actionable first)
- Unclear elements:
    "▼ Workspace: Acme Corp" — unclear if this is a filter, a label, or a nav item
    "● Live" — is this a status indicator? A toggle? A streaming mode?
    The 6 metric tabs (Sessions/Users/Revenue/...) — unclear if these filter the chart below
    The line chart has no legend and unlabeled axes
- Primary action: none obvious — everything has equal visual weight
- 3-second mental model: "This is a ___ where I can ___" → impossible to complete without studying the screen
- Verdict: FAIL
```

## Layer 2: Physical Metaphor

```
PHYSICAL METAPHOR:
- Spatial persistence: unknown — do the tab selections persist across page reloads? No indication.
- Action-reaction: clicking a metric tab presumably updates the chart, but there's no visual connection
  between the tabs and the chart (no proximity, no shared container)
- Visual weight: top nav and icon toolbar are visually heavy (dark bar, many elements) but are
  secondary to the data — weight is inverted from importance
- Containment logic: "Recent Events," "Top Pages," and "Alerts" are siblings with no visual grouping —
  they appear to be the same type of thing but serve different purposes
- Flow direction: user's eye is pulled left-to-right across the nav before they can focus on data
- Verdict: FAIL
```

## Layer 3: Affordance Test

```
AFFORDANCE TEST:
- "≡" hamburger: convention (known on mobile, ambiguous on desktop with full nav visible)
- "+ New" button: convention (but "new what?" is unclear without tooltip)
- "● Live" indicator: false affordance — looks like a button (circular element, colored) but
  behavior is unknown; if it's status-only, it should not look interactive
- Metric tabs (Sessions/Users/...): convention, but their relationship to the chart below is
  non-obvious; users may not realize clicking them updates the chart
- Line chart: novel — 6 lines with no legend requires learning which line is which
- Export icon: convention (arrow-out-of-box) — acceptable
- "⚙" settings icon: convention — acceptable
Critical issues:
  - "● Live" false affordance
  - Unlabeled chart lines — novel interaction with no onboarding
- Verdict: FAIL
```

## Layer 4: Cognitive Budget

```
COGNITIVE BUDGET:
- Simultaneous decisions: 14+ (5 nav items, 6 metric tabs, 4 stat cards, 3 table sections,
  plus workspace selector, new button, export, settings, alerts) → overloaded
- Novel concepts: 3+ (Live mode, Cohort tab, unlabeled chart) → costly for non-technical users
- Steps to primary task: unclear — what IS the primary task? The screen doesn't suggest one.
  If "check today's revenue," steps = find the Revenue tab (1) + read the stat card (2) +
  interpret chart (3+) — minimum possible would be 1 if it were surfaced prominently
- Escape routes: present (nav always visible) but noisy — the escape routes are lost in the
  visual weight of everything else
- Status clarity: "● Live" suggests real-time data but this is not explained; users don't know
  if the numbers are current, delayed, or cached
- Verdict: FAIL
```

## Layer 5: Expectation Consistency

```
EXPECTATION CONSISTENCY:
- Action: click "Sessions" tab → Expected: chart shows session data → Actual: probably true,
  but not visually confirmed (no axis labels to verify) → Gap: minor
- Action: click "+ New" → Expected: create something → Actual: unknown — new workspace?
  new report? new segment? → Gap: major
- Action: click "● Live" → Expected: unknown — toggle live mode? open live view? → Actual: unknown
  → Gap: major (false affordance = unmet expectation)
- Action: hover over chart line → Expected: tooltip with data → Actual: probably true (standard
  charting behavior) but not signified → Gap: minor
Critical gaps:
  - "+ New" has no clear object — violates "action + object" expectation pattern
  - "● Live" creates expectation of interactivity with no defined outcome
- Verdict: WARNING
```

---

```
═══════════════════════════════════════
BODY TEST SUMMARY
═══════════════════════════════════════
First Contact:     FAIL
Physical Metaphor: FAIL
Affordance:        FAIL
Cognitive Budget:  FAIL
Expectation:       WARNING
───────────────────────────────────────
Overall:           FAIL
═══════════════════════════════════════

Top issues (prioritized by impact):
1. No primary action / visual hierarchy — everything competes equally for attention
2. Cognitive overload — 14+ simultaneous decisions for a non-technical audience
3. False affordance on "● Live" and unlabeled chart lines erode trust

Recommended fixes:
1. Establish a single hero metric or "today at a glance" section above the fold with
   clear visual hierarchy — one number, one chart, one action
2. Hide advanced tabs (Funnel, Cohort, API) behind a "More" control; surface only the
   2-3 most common actions for this audience
3. Label chart axes and add a legend; replace "● Live" with a static badge ("Updated 2 min ago")
   unless it's genuinely interactive, in which case label it "Pause live updates"
```
