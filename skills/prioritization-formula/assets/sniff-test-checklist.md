# Sniff-test checklist

The leader's challenge pass, named for checking fruit you cannot judge by sight. The formula is a comparison tool, and its inputs are estimates from people with stakes in the ranking. This pass questions the inputs before the ranking gets used. The readout format below is the Sniff Test mode's own artifact and ends at the verdict; when this checklist is applied inline during a backlog build, only the flag lines land in the backlog, and no verdict is written there.

## Patterns worth questioning

- **High value, low effort, high confidence, same row.** The everything-is-easy row. Ask who scoped the effort and what specifically the customers said.
- **One team's rows dominate every column.** A submitter whose initiatives all score near the top is describing their conviction, not the backlog.
- **No negative BO anywhere.** A portfolio where nothing trades off against any objective usually means objectives were scored as vibes, not checked one by one.
- **Confidence above 80 percent on anything cross-team.** Dependencies eat confidence. Ask what the number was before the dependency was known.
- **Uniform effort.** Every row at the same E means effort was not really estimated.
- **A score that moved since last review without a stated reason.** Inputs drift toward whatever ranking the room wants.

## The questions

For each flagged row, ask in order:

1. What did customers actually say or do that sets CN? Name the source.
2. Which objective does each BO score serve, and would the objective's owner agree with the number?
3. Who scoped E, and against what comparison row?
4. What single event would cut C in half?

## Readout format

```
Sniff test: [Backlog name], [Date]

| Initiative | Flag | Question for the owner | Score stands? |
|---|---|---|---|
| [Name] | [Pattern observed] | [The specific question] | [Stands, Revise, or Rescore pending answer] |

Verdict: [One sentence on whether the ranking is safe to act on, and which rows
hold it up]
```
