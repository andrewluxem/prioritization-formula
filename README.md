# prioritization-formula

A small, static agent skill that scores and ranks competing work and shows its arithmetic. Ask it which thing to build first and it hands back a table you can argue with, not a preference it asserts.

Two artifacts:

- **Scored Backlog**: every initiative scored on customer needs, named business objectives, effort, and confidence, with Raw and Priority derived in the table and one row's derivation written out so a reader can check the rest. Scores nobody supplied carry a labeled assumption in the row where the value sits, never a quiet middle value.
- **Sniff Test**: the challenge pass over a ranking somebody else submitted. It questions the inputs before the ranking gets used, verifies the arithmetic on the submitted numbers, and returns a specific question per flagged row with a call of Stands, Revise, or Rescore pending answer. It never rewrites the owner's scores.

It executes the [Prioritization Formula playbook](https://www.andrewluxem.com/playbooks/prioritization-formula) from andrewluxem.com. The playbook page teaches the framework. This skill runs it.

**Static by construction: no network calls, no remote fetch, no auto-update, nothing scheduled, no background behavior. Model-invocable by design: an agent may pick it up when you ask for ranking or prioritization work, and naming the skill is the reliable path.** It reads nothing outside its own folder, never edits your global agent config, and never updates itself in place. The whole thing is one `SKILL.md` you can read in five minutes, plus two templates and one reference file it loads only when a step needs them.

## The loop

Pick the mode from what you bring. An unscored list means Score. A ranking you doubt means Sniff Test.

| Mode | You bring | You get |
|---|---|---|
| **A. Score** | A list of initiatives with whatever context exists | Scored Backlog |
| **B. Sniff Test** | An already-scored backlog or ranking | Sniff Test readout |

The formula is deliberately small:

```
((CN + BO) / E) x C = Priority

CN   Customer Needs, 0 to 3, what customers said or did
BO   Business Objectives, negative 3 to 3, against a named objective
E    Effort, 1 to 3 relative points against the other rows
C    Confidence, a percentage, applied last as a multiplier
```

Because the inputs are the same everywhere, it compares initiatives across teams that share no roadmap. Effort is relative points rather than hours on purpose: dividing value by man-hours makes the score's magnitude depend on whichever unit somebody picked, and two teams using different units stop being comparable, which defeats the point.

Negative business-objective scores are real and required. A backlog where nothing trades off against any objective has usually scored objectives as sentiment rather than checking them one at a time.

What it refuses to shortcut:

- **Never invent a score.** Every number traces to something you supplied or to a labeled assumption sitting in the row. A middle-of-scale default entered silently is the failure the table exists to prevent.
- **A label never cites what you did not say.** It states what was assumed and the default it came from. A number that reads as sourced when the source does not exist is worse than a blank.
- **The score is an indicator, not a prediction.** Rankings are presented as comparison. A reply that promises an outcome because the score is high has left the formula's warranty.
- **An assumption that is not visible is an invention.** Where an input is absent, the assumption appears in the artifact where the value sits.

A roadmap is not this skill's artifact. Ask it to rank and then sequence, and it produces the Scored Backlog and names the destination by slug: `how-to-plan-new-product-and-services` for the phased plan, `business-goals` when the objectives being scored against are not written down yet.

See [`examples/example-run.md`](examples/example-run.md) for a full Mode A pass, from four competing initiatives to a ranked table with its flags.

## Install

**Manual (recommended, clone and copy):**

```bash
git clone https://github.com/andrewluxem/prioritization-formula.git
cp -r prioritization-formula/skills/prioritization-formula ~/.claude/skills/
```

Then invoke it: `use the prioritization-formula skill to stack rank this backlog`.

**As a Claude Code plugin (version-pinned, no auto-update):**

```
/plugin marketplace add andrewluxem/prioritization-formula
/plugin install prioritization-formula@prioritization-formula
```

`plugin.json` carries an explicit `version`. Installing pins that version. It does not silently pull new commits. Taking an update means bumping the version and reinstalling, so the update is a decision rather than a background event.

**As a zip:** the packaged skill is on the playbook page at [andrewluxem.com/playbooks/prioritization-formula](https://www.andrewluxem.com/playbooks/prioritization-formula), for platforms that want a folder upload instead of a clone. Same files, apart from a `metadata:` block in the site copy's frontmatter that the site registry and packager read.

Portable by design: it is plain Markdown with no runtime, so it works anywhere a folder of skill files works.

## Usage

```
Stack rank these six backlog items, here is the customer feedback behind them
Which should we do first, the loyalty relaunch or the referral program?
Marketing sent over their priorities and everything is somehow high value and low effort, check it
```

Naming the skill is the reliable path: `use the prioritization-formula skill`. It has no background behavior and nothing scheduled, so nothing happens until a request goes to it.

## Iterating

The skill is the folder [`skills/prioritization-formula/`](skills/prioritization-formula/):

- `SKILL.md` is the procedure, and it is the only file loaded every time.
- `references/scoring-scales.md` is the depth: what each point on each scale means, why negative business-objective scores are required, and why effort is relative points rather than hours. It is read at the step that needs it.
- `assets/` holds the two documents the artifacts are built from. The backlog template carries a filled example under the blank one, and that example deliberately includes a row whose effort nobody supplied, so it ranks first on an assumption and draws a flag for it.
- `meta.yaml` carries the version, the invocation examples, the three test prompts with their pass bars, and the changelog.

Edit it, invoke it on a backlog you are actually arguing about, and see whether the artifact earns its place. The bar is that the output would have taken you an afternoon to build by hand.

When you change behavior meaningfully, bump `version` in both `.claude-plugin/plugin.json` and `meta.yaml` so plugin installs pick it up deliberately, and add the changelog line.

## Testing

`meta.yaml` ships the three prompts this skill is scored against, each with its own `passes_when` bar: a happy path, a messy input, and a near miss that bundles ranking with sequencing, which it should half-answer and half-hand-off. The bars live with the skill on purpose. A prompt that exists only in a chat transcript is gone by the next run, and a bar rewritten after seeing the output grades itself easier every round.

Version 1.0.0 was tested on Claude Code. It has not been exercised on other hosts.

## License

MIT, see [`LICENSE`](LICENSE). The skill folder carries the same MIT text in [`skills/prioritization-formula/LICENSE.md`](skills/prioritization-formula/LICENSE.md), so the whole repo is one license.

---

## More playbooks

This skill packages one playbook from the free library at [github.com/andrewluxem/playbooks](https://github.com/andrewluxem/playbooks). Every playbook is free to read, with no email required.
