# Vec · v-bugs — Bugs / fixes (the eval-gate fixes + open)

Type: this is a Vec entry — transient, not truth, neither a gene 𝒢 nor an archive entry Λ (vectors.md §Type). Source [FACT]: the comments on the R→S audit (the eval-gate-correction thread; origin recorded as provenance in archive/archive.md). Each fix verified vs NON-LLM ground truth + golden-tested to FAIL on the OLD behaviour. Scope: these are the R→S prerequisites — the merge gate `eval/statistical_test.py` is N's "measurement organ"; until it read true, ΔN = drift (GENOME §D binding-constraint, the R→S audit §3). Cross-ref vectors/theory-of-everything.md §3,§9. Discipline: once a bug-fix is implemented, discard it — a landed fix stays here only until it's clearly stable; the OPEN items (§Open) are the live work.

## §Fixed — the three gate conditions (all corrected, golden-tested) [FACT, the R→S audit comments]
```
the McNemar-tail fix  McNemar tail inverted              [DONE]
     bug : statistical_test.py:189 summed the LOWER binomial tail P(X≤r) ⇒ gate PASSED regressions, BLOCKED improvements (inverted since commit-1; a hardcoded test string masked it — tested the parser ¬the formula).
     fix : → UPPER tail P(X≥r).  verified vs scipy.stats.binomtest(alt='greater') + statsmodels …mcnemar (library ground truth); canon Wikipedia/CRAN exact2x2.
the Cohen’s-d edge fix  Cohen's d zero-variance → 0        [DONE]
     bug : a perfectly-CONSISTENT improvement scored d=0, CI(0,0) ⇒ the gate blocked the STRONGEST possible signal.
     fix : correct limit — sd=0,mean>0 → +∞ (pass) ; mean<0 → −∞ (fail) ; mean=0 → 0.  verified vs CRAN effectsize, MRC-CBU ("everyone changes by the same amount ⇒ d=±infinity").
the rater-aware-α fix  Krippendorff α rater-blind          [DONE]
     bug : one judge's k runs counted AS raters ⇒ run-to-run noise reported as "inter-rater reliability" (e.g. α=0.375 from 3 runs).
     fix : rater-aware — group by the `rater` dim, aggregate a rater's runs (majority) → one rating, then α ACROSS raters. 1 rater → None (criteria.md:49) ; ≥2 → genuine inter-rater.  ref Wikipedia Krippendorff's-alpha.
```

## §Wired / Landed — the missing rater + the structural edge [FACT, the R→S audit comments]
```
the cross-family second judge  cross-family second judge          [WIRED — live run deferred]
     gap : the rater-aware-α fix makes α rater-aware, but with one judge there's no real `rater`. need a second judge of a DIFFERENT model family (same-family judges share error modes — arXiv:2506.07962; triangulation needs independent channels — Munafò&Davey-Smith Nature 2018).
     fix : `judge --judge-provider github-models --rater 2` → GitHub Models (FREE, in Actions, no API key; permissions: models:read; actions/ai-inference@v1; a NON-Claude family e.g. openai/gpt-4o-mini, pin the live catalog id). a `rater` column lets α (the rater-aware-α fix) compute genuine inter-rater across rater-1 (Claude) + rater-2.
     status : deterministic parts tested locally; the LIVE model call is gated + non-blocking (workflow_dispatch), validates on first CI run.
the vanilla baseline arm  vanilla / no-plugin baseline arm   [LANDED — A/B run deferred to product maturity]
     gap : run_suite.py skipped any empty calibration ⇒ the eval could only compare TWO PLUGIN VERSIONS, never "Claude" vs "Claude + harness".
     fix : a `vanilla` sentinel arm = an empty system-prompt that is NOT skipped, flows through generation as bare Claude = the structural R→S edge.
     status : verified independently — minimal diff (sentinel + `from __future__ import annotations`), no new comments, 4/4 golden tests FAIL when the sentinel is reverted (catch the old skip, ¬a parser), regression clean (statistical 19/19, second-judge 3/3, mock-e2e ALL PASS); run_suite materialization calls no LLM ⇒ fully locally verifiable.
```
```
state-of-R→S [FACT, the R→S audit comments] :
  buildable prerequisites COMPLETE — gate correct (the McNemar-tail, Cohen's-d, and rater-aware-α fixes) and the cross-family judge wired and the vanilla arm landed; all deterministic, golden-tested, vs non-LLM ground truth.
  DEFERRED (owner-gated; "fix the instrument first, run it when the product is less raw") — the live A/B run for merge verdicts: first inter-rater α (rater-1 Claude + rater-2 GitHub-Models), then A/B vanilla vs +harness vs an external UNSATURATED benchmark (avoid saturated/contaminated — SWE-bench Verified deprecation OpenAI Feb-2026; use SWE-bench Pro).
```

## §Open — remaining issues (CODE, no run) [FACT, the R→S audit comments]
```
N7   verification-gate stack-coverage               [ASSOC/conflict, ¬FACT-open]
     problem : ROADMAP.md:25 marks N7 status=shipped (tsc --noEmit, dotnet build, swift build); but ~/.neuro-matrix/scripts/verification-gate.sh:72-94 case-block still covers only sh/py/json. ROADMAP vs snapshot-code DISAGREE; unverifiable-here which is live. If snapshot is live, `verification-gate.sh` NO-OPS on C#/.NET / TS / Swift (the approval-only / high-false-completion regime) ⇒ "verified" empty for those stacks; if ROADMAP is live, already shipped.
     fix (planned, IF still open) : make N7 REAL — a stack-aware verification-gate that runs the right build/test per stack. ⟵ this is V4 in theory-of-everything.md §6 (extend channel independence: compiler/tests as a real channel for every stack).
     status : the vanilla baseline arm comment names it as remaining code-work; ROADMAP.md:25 contradicts (status=shipped) — conflict unresolved here.
eval-power   N too small                              [OPEN]
     problem : N=17 probes is UNDERPOWERED for the Wilcoxon/McNemar gate — even a now-correct test can't detect the single-digit-pp marginal headroom of a prompt layer over an already-strong scaffold at that N.
     fix (planned) : raise N (theory-of-everything.md §6 V1 note: "N must be large"); a larger probe set before trusting a live verdict.
     status : named as remaining work in the vanilla-baseline-arm comment; gated on the same "run when less raw" decision.
```

## §I — Ledger (this entry)
```
FACT  : the eval-gate fixes exist as the R→S audit comments with the statuses above; each fix verified vs the named non-LLM ground truth + golden-tested to fail on the old behaviour; eval-power N=17 stated in the vanilla-baseline-arm comment.
ASSOC/conflict : N7 stack-coverage — ROADMAP.md:25 status=shipped vs verification-gate.sh:72-94 sh/py/json only; the vanilla baseline arm comment says still open. Sources DISAGREE; ¬FACT-open, unverifiable-here.
ASSOC : the cited references (scipy/statsmodels, CRAN effectsize/exact2x2, arXiv:2506.07962, Munafò&Davey-Smith) — cited BY the thread; the mapping of N7→V4 and eval-power→V1 is to theory-of-everything.md §6 (same source, the R→S audit).
HYPO  : that the deferred live A/B run will show the harness helps — explicitly OPEN (the whole reason V1 is the binding constraint); whether N7-real + larger-N suffice to detect the effect.
Q     : the exact unsaturated benchmark to anchor the A/B (theory-of-everything.md §7 Q4); whether the live run has occurred since the vanilla-baseline-arm fix landed (not verified — owner-gated, deferred).
transient : entry — once the eval-gate fixes are implemented, discard; the live run + N7 + eval-power are the open work. Discarding v-bugs does not force a rebuild of GENOME.
```
