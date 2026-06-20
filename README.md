# remix

A divergent ideation engine for agents. Feed it an idea you **already have** — remix explodes it into dozens of wild cross-domain reshapes, audits them without crushing the bold ones, and converges to a few concepts worth building.

It's the opposite of normal brainstorming: brainstorming *converges* one idea into a spec; remix *diverges* one idea into many.

## Install

```bash
npx skills add Onsraa/remix
```

Installs to `.claude/skills/remix/`. Then invoke `/remix` — or just ask to "remix", "reshape", or "reinvent" something you've built.

## Use

```
/remix <repo path | doc | one-paragraph brief>
```

Two knobs:
- **wildness** — `grounded` (stays shippable) · `bold` (default) · `unhinged` (feasibility ignored, every assumption fair game)
- **focus** — `anything` (default) · `features` · `monetization` · `growth` · `UX` · …

## How it works

Five phases, fanned out across parallel agents:

1. **Understand** — reads your idea and names its *sacred cows*, the assumptions nobody questions. You can't break a rule you haven't named.
2. **Scout** — assigns blind explorers across a near→absurd **distance dial**: adjacent industries, unrelated ones, far domains (slime molds, casinos, ER triage), and absurd ones (myth, dreams) — each paired with a transform technique.
3. **Explode** — each blind explorer steals one mechanic from its domain and uses it to break one assumption. Contract: name the steal, state what it *removes* — no bolt-on features.
4. **Audit** — dedupe, score (novelty × fit × feasibility × moat), sort into portfolio buckets (🔒 safe · 🎲 big swing · 😴 sleeper). Bold ideas are deliberately protected from feasibility bias.
5. **Converge** — finalists each get a skeptic (why it dies) and a champion (why it wins), then become full concept cards.

The output is a `creative-board-<date>.md`: the full bucketed board plus concept cards — each with the rule it breaks, what it steals, a skeptic/champion verdict, and a first move. It then offers to hand a chosen concept to brainstorming to become a real spec.

## Requirements

- An agent harness with parallel-agent orchestration (built for Claude Code's `Workflow`). Without one, it falls back to a single-context run — narrower, but it still works.
- A run fans out ~15–30 agents, and skills run with **full agent permissions**. Review before use.

## Files

| file | what |
|------|------|
| `SKILL.md` | the skill — triggers, inputs, run + output contract |
| `remix.workflow.js` | the 5-phase orchestration |
| `lenses.md` | the domain palette + technique deck |
