# efficient-semantic-thinking

[![skills.sh](https://skills.sh/b/CamjamPNG/efficient-semantic-thinking)](https://skills.sh/CamjamPNG/efficient-semantic-thinking)

A skill that helps AI agents think in **meaning before wording** — converting unnecessary natural-language structure into compact semantic representations, operating on that compressed state, and expanding back to natural language only when communicating with the user.

## Install

```
npx skills add CamjamPNG/efficient-semantic-thinking
```

## What it does

- Extracts goals, entities, requirements, preferences, conditions, and uncertainty from input
- Represents them with compact semantic primitives (`PRICE<=500`, `RAM>=16GB`, `BEST=B`)
- Reasons over the compressed state instead of restating prose
- Preserves specificity — never replaces a specific fact with a generic abstraction
- Expands back into natural language at the communication boundary

The goal is not fewer words for their own sake. The goal is **more meaning per unit of linguistic overhead** — a representation that is compact, precise, reversible, specific, and unambiguous.

## Structure

```
efficient-semantic-thinking/
└── SKILL.md
```
