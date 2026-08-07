# Scored backlog template

The formula and its arithmetic stay visible in the artifact. A score whose derivation cannot be checked by the reader is an assertion, not a score. The document ends at the sniff-test flags line; nothing follows it.

## The formula

```
((CN1 + CN2 + BO1 + BO2) / (E1 + E2)) x C = P

Value = sum of Customer Need scores plus Business Objective scores
Effort = sum of Effort scores
Raw = Value / Effort
Priority = Raw x Confidence
```

Use as many CN, BO, and E components as the backlog needs, and the same set for every row. One CN, two BO, and one E is the common shape. Scales live in `references/scoring-scales.md`; every row in one backlog uses the same scale.

## Worked derivation, one row

```
Initiative A: CN 2, BO1 1, BO2 1, E 2, C 75%
Raw = (2 + 1 + 1) / 2 = 2.0
Priority = 2.0 x 0.75 = 1.5
```

## The table

```
Scored backlog: [Team or product name]
Date: [Date]
Scored by: [Names, or Scorer needed; scores are owned, not anonymous]
Scale: [The scale in use, from references/scoring-scales.md, stated in one line]

| Initiative | CN | BO1 | BO2 | E | Raw | C | Priority | Notes |
|---|---|---|---|---|---|---|---|---|
| [Name] | [0-3] | [-3 to 3] | [-3 to 3] | [1-3] | [derived] | [%] | [derived] | [assumptions and flags, in place] |

Ranking: [Initiatives in Priority order, ties broken by the stated tiebreak]
Sniff-test flags: [Rows flagged by assets/sniff-test-checklist.md, with the question to ask]
```

## Filled example

The example preserves the awkward cases on purpose: a negative business-objective score, a labeled assumption standing in for a score nobody supplied, and a sniff-test flag on the top-ranked row.

```
Scored backlog: Paddle accessories line
Date: November 3, 2026
Scored by: Katy, Andrew
Scale: CN 0-3, BO -3 to 3, E 1-3 relative points, C as a percentage

| Initiative | CN | BO1 | BO2 | E | Raw | C | Priority | Notes |
|---|---|---|---|---|---|---|---|---|
| A. Paddle covers | 2 | 1 | 1 | 2 | 2.0 | 75% | 1.5 | |
| B. Grip tape refresh | 1 | 1 | 0 | 2 | 1.0 | 90% | 0.9 | |
| C. Logo ball line | 1 | 2 | -1 | 1 | 2.0 | 40% | 0.8 | BO2 negative, works against the premium-brand objective |
| D. Court bag | 2 | 1 | 1 | 1 | 4.0 | 85% | 3.4 | E assumed at 1, no scoping supplied, Effort estimate needed |

Ranking: D 3.4, A 1.5, B 0.9, C 0.8
Sniff-test flags: D scores highest on an assumed effort with high confidence.
Ask who scoped it before acting on the rank.
```
