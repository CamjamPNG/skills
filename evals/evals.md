# Efficient Semantic Thinking — Evaluation Suite

5 test prompts covering the skill's strongest use cases: constraint-based
decision, state maintenance, requirements extraction, candidate filtering,
and anti-AI rewriting.

Each prompt was run twice in fresh agent contexts: **baseline** (no skill)
and **with-skill** (skill instructions injected). Full comparison in
`results.md`.

## Prompts

### 1. Laptop comparison
"Pick between three laptops for college. Budget $700 max, Windows required,
at least 16GB RAM and 512GB storage. I'd prefer better performance, but
battery life matters too. A: $649, 16GB, 512GB, mid perf, high battery.
B: $679, 32GB, 1TB, high perf, low battery. C: $599, 8GB, 512GB, high
perf, high battery."

### 3. State maintenance across operations
"Process this list: start with score 0. For each item add 3 if it's green,
subtract 2 if red, skip if blue, and double the running total if the item
is gold. Items: green, red, blue, green, gold, red, green. What is the
final score? Track each step."

### 4. Requirements extraction
"Here's what my boss said: 'I need a new dashboard. It should probably show
revenue, definitely by region, and maybe by product too. Not sure about
dates — let's default to this month. Make it fast, it's gonna be big. Also
my PM wants a CSV export but I told him that's next quarter.' List every
requirement and mark each as must-have or nice-to-have."

### 5. Filtering candidates
"From this list of job candidates, find everyone who has a CS degree OR 5+
years experience, knows either Python or TypeScript, and is OK with hybrid
work. Alice: CS, 2y, Python, hybrid. Bob: no degree, 6y, Java, remote-only.
Carol: CS, 4y, TypeScript, hybrid. Dave: Physics, 7y, Python+TypeScript,
hybrid. Eve: CS, 1y, Python, hybrid."

### 6. Humanize an AI-slop paragraph
"Rewrite this to sound human: 'In today's ever-evolving digital landscape,
the company stands as a testament to innovation, underscoring the
importance of embracing change while navigating the challenges ahead.
This pivotal moment marks a significant shift, reflecting broader trends
that will ultimately shape the future of the industry.'"
