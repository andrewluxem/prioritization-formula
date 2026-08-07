# Scoring scales

The formula compares value against effort, so the scales only need to be consistent within one backlog. These defaults match the worked example in `assets/backlog-template.md`. A user who brings their own scale keeps it; state theirs in the Scale line instead.

## Customer Needs, CN, 0 to 3

Scores what customers have communicated or what their behavior implies. Not what the team hopes customers want.

- 0: no customer signal
- 1: implied by behavior, not stated
- 2: stated by customers, or strongly implied by repeated behavior
- 3: stated repeatedly by many customers, or blocking their use today

Use two CN components when two distinct customer needs are in play and score each on its own evidence.

## Business Objectives, BO, negative 3 to 3

Scores alignment with a named objective: financial goals, market size, technology position, competitive advantage. Each BO column maps to one named objective, written down, so the objective's owner could check the score.

- Negative values are real and required when an initiative works against an objective. A backlog with no negative BO anywhere has usually scored objectives as sentiment.
- 0 means the initiative neither serves nor harms that objective.

## Effort, E, 1 to 3 relative points

Resources required, scored relative to the other rows in this backlog.

- 1: small against this backlog's rows
- 2: typical
- 3: large

Effort is relative points, not raw hours. Dividing value points by man-hours makes the score's magnitude depend on the unit somebody chose, and two teams using different units stop being comparable, which defeats the formula's cross-team purpose. If the team has hour estimates, bucket them into 1 to 3 against each other.

## Confidence, C, a percentage

The stakeholder's confidence that the initiative delivers the intended customer and business outcome. Applied last, as a multiplier.

- Anchor high confidence to evidence: prior comparable wins, tested demand, scoped delivery.
- Cut confidence for cross-team dependencies; a result depending on more than two teams rarely deserves more than 50 percent.

## Reading the result

The priority score is an indicator for comparison, not a prediction. It makes assumptions about needs, objectives, effort, and confidence, so it should start the discussion about sequence, not end it. The score also says something about the scorer: inputs that always favor the submitter are what the sniff test in `assets/sniff-test-checklist.md` exists to catch.
