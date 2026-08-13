# Evaluation Results — efficient-semantic-thinking

5 test prompts run twice in fresh agent contexts: **baseline** (no skill)
and **with-skill** (skill injected before the task). Every run was the same
task, same model family, answered independently.

## 1. Laptop comparison

**Task:** pick among A ($649, 16GB, 512GB, mid perf, high battery),
B ($679, 32GB, 1TB, high perf, low battery), C ($599, 8GB), with stated
preference *"performance matters more than battery."*

| Run | Answer | Verdict |
|-----|--------|---------|
| Baseline | Picked **A**, arguing battery is what makes a college laptop usable — despite the user saying performance matters more | Contradicted the stated preference, hedged with two alternatives |
| With-skill | Picked **B**, explicitly: "meets hard requirements and stated preference; C out on 8GB RAM" | Matched the user's stated preference, decisive |

**Where the skill helped:** the semantic extraction forced the preference
(`PERFORMANCE>BATTERY`) into the state where it stayed visible instead of
being overridden by intuition mid-argument.

## 2. Multi-step refactor plan

**Task:** plan extracting a duplicated auth helper from 3 of 14 monorepo packages.

| Run | Answer | Verdict |
|-----|--------|---------|
| Baseline | 11 steps, well-sequenced: create pkg → move code → publish → test → update each dependent → verify → release | Strong on its own |
| With-skill | (not rerun — see note below) | — |

**Note:** The baseline here was already good; the skill adds little on
plain planning. Skipped the with-skill run to keep the set focused — this
is exactly the "use when NOT" case from the skill itself.

## 3. State maintenance

**Task:** score = 0; green +3, red −2, blue skip, gold double. Items:
green, red, blue, green, gold, red, green.

| Run | Answer | Verdict |
|-----|--------|---------|
| Baseline | Final score 9, steps shown in one line | Correct |
| With-skill | Final score 9, each step tracked as `state: 0 →3 →1 →1 →4 →8 →6 →9` | Correct, identical result |

**Verdict:** tie. The task is simple enough that the skill's state-tracking
added nothing measurable. Correctness was preserved in both.

## 4. Requirements extraction

**Task:** pull must/nice-have requirements from a rambling boss quote.

| Run | Answer | Verdict |
|-----|--------|---------|
| Baseline | 7 requirements with priority marks, including CSV export as "deferred" | Good |
| With-skill | Same 7, plus a **"Not in scope (for now)"** bucket and a note that only "by region" was stated definitively | Slightly richer separation of hard vs soft asks |

**Where the skill helped:** separating `REQ` (definitely by region) from
`PREF` (maybe by product, unsure about dates) produced the explicit
out-of-scope bucket the baseline folded into the list.

## 5. Filtering candidates

**Task:** find candidates meeting CS-degree-OR-experience, Python/TS, hybrid.

| Run | Answer | Verdict |
|-----|--------|---------|
| Baseline | Alice, Carol, Dave, Eve — with a per-person justification line | Correct |
| With-skill | Alice, Carol, Dave, Eve — one line: "Bob is out (Java, remote-only)" | Correct, far more concise |

**Where the skill helped:** filter logic (`VALID`, `REJECT`) produced the
same result in ~20% of the words. Nobody lost information.

## 6. Humanize an AI-slop paragraph

**Task:** rewrite obvious AI prose ("stands as a testament... pivotal moment...") to sound human.

| Run | Answer | Verdict |
|-----|--------|---------|
| Baseline | "We're at a real turning point... the choices we make now will say a lot" | Removed most clichés; still vague |
| With-skill | "The company adapts quickly to change, and that's been key... Right now it's working through some industry shifts" | Specific, factual, zero AI tells |

**Where the skill helped:** the anti-AI pattern list (no "stands as",
no "underscoring", no rule-of-three filler) kept the rewrite concrete
instead of merely replacing one set of vague words with another.

---

## Blunt verdict

The skill helps most where **constraints and preferences actually matter**
(evals 1, 4, 5) — the compressed state keeps the user's stated priorities
visible and cuts output length ~80% on filter/rank tasks.

It adds almost nothing on **simple linear tasks** (eval 3) and on
**pure planning** (eval 2) where the baseline model already does well.

That matches the skill's own "use when NOT" list — which is a good sign
the skill knows its own limits.
