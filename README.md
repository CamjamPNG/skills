# efficient-semantic-thinking

[![skills.sh](https://skills.sh/b/CamjamPNG/skills)](https://skills.sh/camjampng/skills/efficient-semantic-thinking)

An agent skill that stops AI models from drowning complex tasks in words — it thinks in compact meaning, not prose, and only talks normally when it needs to.

**Who it's for:** anyone building or running agents that handle multi-step planning, comparing options, or juggling lots of constraints.

**Why it exists:** natural language is verbose. When an agent restates requirements as prose over and over, it burns tokens, repeats itself, and drifts. This skill gives the model a compressed "mental workspace" — the same information, less overhead.

**AKA:** why use many word, few word do trick 

## Install

```
npx skills add CamjamPNG/skills
```

## What the skill does

When active, the model:

1. Extracts the real goal, entities, hard requirements, preferences, conditions, and uncertainty from the task
2. Represents them compactly — e.g. `PRICE<=500`, `RAM>=16GB`, `BEST=B`
3. Reasons over that compressed state instead of restating prose
4. Preserves specificity — never swaps a specific fact for a generic label
5. Expands back into natural language when it talks to you

**The point is not fewer words.** The point is more meaning per word — a representation that stays compact, precise, and reversible, and that never loses information to sound shorter.

## Example

A user asks to compare three laptops. The model internally works with:

```
REQ:  PRICE<=700USD, OS=WINDOWS, RAM>=16GB, STORAGE>=512GB
PREF: PERFORMANCE > BATTERY
VALID: A, B      REJECT: C (RAM<16)
BEST: B
```

...then answers in plain English: *"I'd pick B — it meets every requirement and has 32GB RAM and 1TB storage."*

## Repository structure

```
efficient-semantic-thinking/
└── SKILL.md
```
