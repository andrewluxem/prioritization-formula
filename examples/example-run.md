# Example run

A full Mode A pass on a real-shaped request. This is what the skill produces when invoked.
Names and numbers are illustrative.

---

**Invocation:**

> Help me prioritize the next build for our coffee roasting business. Wholesale cafes keep
> emailing and calling in their reorders and half of them get keyed in wrong. We have some
> interest in a flavor quiz for the subscription signup. The retail storefront looks dated,
> nobody has scoped it. And our founder wants a single-origin premium tier, which would tie
> up the roasting team through the fall.

**No questions asked.** Mode A is decided by what arrived: an unscored list of initiatives
with context attached. Everything the input does not settle gets a labeled assumption in the
row where the value sits, which is faster for the reader than a round of questions. The one
thing that would stall the run is an empty list, and this is not that.

**1. Fix the scale, silently.** The defaults in `references/scoring-scales.md` apply: CN 0 to
3, BO negative 3 to 3, E 1 to 3 relative points, C as a percentage. No user scale was
supplied. This is working, not output. Only the one-line Scale statement lands in the
artifact.

**2. Score each row from evidence.** Two business objectives are in play, so the table
carries two BO columns and both are named, because an objective nobody named is an objective
nobody can check the score against. The reorder portal earns CN 3: cafes are not requesting
it, they are working around its absence today. The single-origin tier earns CN 0, because a
founder's preference is not a customer signal, and it earns a negative BO2, because tying up
the roasting team through the fall works directly against the subscriber-retention objective.
Every confidence value is an assumption here, since the input supplied none, so each one is
labeled with what was assumed and why. No label cites a descriptor the request did not
contain.

**3. Show the arithmetic.** Raw and Priority are derived columns, and one row's derivation is
written out in full so a reader can check the other three against it.

**4. Rank and flag.** Ordered by Priority, then the patterns in
`assets/sniff-test-checklist.md` run over the finished table. Two rows draw flags: the row
whose rank rests on an effort nobody scoped, and the row that scores negative.

**5. Deliver only the backlog.** The reply's first line is the backlog title line and its last
line is the sniff-test flags' final line. Nothing before it, nothing after it. No verdict is
written into a backlog build; the verdict belongs to Sniff Test mode's own artifact.

**The Scored Backlog:**

```
Scored backlog: Coffee roasting, next build
Date: August 6, 2026
Scored by: Scorer needed
Scale: CN 0-3, BO -3 to 3, E 1-3 relative points, C as a percentage
BO1 = Wholesale revenue growth. BO2 = Subscription retention.

| Initiative | CN | BO1 | BO2 | E | Raw | C | Priority | Notes |
|---|---|---|---|---|---|---|---|---|
| Wholesale reorder portal | 3 | 3 | 0 | 2 | 3.00 | 70% | 2.10 | CN 3, cafes are working around the gap today, and the keying errors are evidence of behavior, not a request. C assumed at 70 percent, the scale default for scoped work with proven demand; no delivery estimate supplied |
| Subscription flavor quiz | 1 | 0 | 2 | 1 | 3.00 | 60% | 1.80 | CN 1, interest was described but not quantified. C assumed at 60 percent, no conversion data on the current signup |
| Retail storefront redesign | 1 | 1 | 1 | 3 | 1.00 | 55% | 0.55 | E assumed at 3, nobody has scoped it, Effort estimate needed. C assumed at 55 percent, and it moves once the scope does |
| Single-origin premium tier | 0 | 1 | -2 | 3 | -0.33 | 35% | -0.12 | CN 0, founder preference with no customer signal. BO2 negative, the roasting team is tied up through the fall, which is time taken directly from subscription work. C assumed at 35 percent, no demand evidence |

Derivation, wholesale reorder portal:
Raw = (CN 3 + BO1 3 + BO2 0) / E 2 = 6 / 2 = 3.00
Priority = 3.00 x 0.70 = 2.10

Ranking: Wholesale reorder portal 2.10, Subscription flavor quiz 1.80, Retail storefront
redesign 0.55, Single-origin premium tier -0.12. No ties.

Sniff-test flags:
Subscription flavor quiz ranks second on an effort of 1 against the thinnest customer
signal in the table. E=1 is doing the work here, not demand. Ask who scoped the quiz at
one point and against which row, and what the current signup conversion rate is before
this is sequenced ahead of the storefront.
Retail storefront redesign carries an assumed effort with nothing behind it, so its score
rests on a number nobody produced. Even at E=1, the smallest this scale allows, it reaches
1.65 and still sits behind the flavor quiz, so a scope changes the margin rather than the
order. Ask for one before the effort is treated as known.
Single-origin premium tier is the only negative row, and the negative BO2 is the reason,
not the effort. Even at E=1 it scores below zero. Ask the founder whether the fall
roasting capacity is a trade they accept, because the score says the subscription
objective pays for this one.
```

---

## Why the awkward cases are in here

The example keeps three things a cleaner sample would have quietly dropped:

- **A row that scores negative.** A backlog where nothing trades off against any objective
  has usually scored objectives as sentiment. The single-origin tier costs the retention
  objective real time, and the score says so out loud rather than burying it in a note.
- **An assumption standing in for a score nobody supplied.** The storefront's effort is
  assumed, the label says so in the row, and the flag names what the rank rests on.
- **A flag on a row nobody would have questioned.** The flavor quiz looks fine at a glance.
  It ranks second because its effort is 1, not because anyone wants it, and that is exactly
  the pattern the sniff test exists to surface.
