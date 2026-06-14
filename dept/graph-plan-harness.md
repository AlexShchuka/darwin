# graph-plan-harness (improve/N) — what & how to improve the seahorse (neuro-matrix, behaviour)

Organ `N` = harness = behaviour phenotype (§A GENOME). Anchor: live `AlexShchuka/neuro-matrix` + the R→S audit (the development-vector source). This file answers **WHAT** to improve and **HOW**, strictly ordered by leverage. Encoding: English + FOL where a real formal object exists; honest dense prose elsewhere (§C). Per-claim tag `FACT·ASSOC·HYPO·Q`; FACT carries a file/issue/PR anchor. No invention: a proposed invariant or run is `HYPO` until landed/executed.

```
binding-constraint(N) [FACT, the R→S audit §2/§6, §D GENOME] :
  R --measures--> E   was severed ;   R --feeds--> E   was missing ;   E --selects--> S  open
  ⇒ ΔN = variation without differential selection = DRIFT, until R→S is closed
```
Law of order: while R→S is open, every other ΔN is drift — close R→S FIRST, or all else is taste.

The order below is **not negotiable by preference**: until `R→S` is closed, INV-A/B/C, V6, V7 are mutations that cannot be selected (the R→S audit §8 verdict). They are listed after V1 because they are *real and queued*, not because they are co-equal.

---

## 0 — Ordering by leverage (strict)

Priority order: V1 (close R→S) ≻ {INV-A, INV-B, INV-C via harness-improve} ≻ V6 (formal-spec) ≻ V7 (SDL). Nothing in {INV-*, V6, V7} is selectable until R→S is closed [the R→S audit §8].

---

## 1 — V1 FIRST · close the R→S loop  [binding; do first]

```
V1 : the RUN — vanilla arm vs external UNSATURATED benchmark, cross-family second judge
κ : eval/ (live) :  run_suite.py · statistical_test.py · test_vanilla_arm.py · test_second_judge.py · criteria.md · questions/ · adversarial/
issues : the eval-gate fixes  gate-fix = FACT (`statistical_test.py:196` upper-tail McNemar, `:265-267` rater-aware α — readable snapshot) ; issue MERGE-status = agent-reported (gh unverifiable here)
```

### 1.1 — State: the GATE is fixed (FACT, snapshot code); the missing step is the RUN  [pivotal]

Gate-fix is FACT — anchored to readable snapshot code, NOT to an issue tracker: `statistical_test.py:196` (McNemar upper tail `range(regressions, n+1)`) + `:265-267` (rater-aware Krippendorff α, a rater's k runs aggregated→one rating). The per-issue MERGE-status below is **agent-reported** (GitHub unverifiable here):
- `the McNemar-tail fix [agent-reported MERGED]` — inverted McNemar tail corrected (gate-fix = FACT `statistical_test.py:196`; the central finding of the R→S audit §3).
- `the Cohen’s-d edge fix [agent-reported MERGED]` — zero-variance paired diffs = infinite effect size, not zero (Cohen's d edge).
- `the rater-aware-α fix [agent-reported MERGED]` — Krippendorff α made rater-aware (gate-fix = FACT `statistical_test.py:265-267`; runs were masquerading as raters).
- `the cross-family second judge [agent-reported MERGED]` — cross-family second judge via GitHub Models (`models:read`, free) — the disjoint second channel.
- `the vanilla baseline arm [agent-reported MERGED]` — vanilla / no-plugin baseline arm.
- `eval/` now contains `test_vanilla_arm.py` + `test_second_judge.py` + `run_suite.py` + `statistical_test.py` [FACT, contents listed] ⇒ the gate is **built** (code readable here).

∴ the genome statements "the eval gate is already fixed" and registry-N:3 are **TRUE against the readable snapshot code** [FACT: `statistical_test.py:196`,`:265-267`]; the *merge* into main is agent-reported. The `R→S` machinery (`E`) is correct and present in the snapshot.

The remaining binding step is therefore **not the gate logic** — it is the **RUN**: execute the suite as a real measurement (`R` actually feeds `E`, `E` actually selects `S`). Per `eval/README.md` [FACT]: "minimum threshold for merge is no question regresses"; the suite is small (17 = 11 adversarial + 6 questions), 18 binary criteria; validity caveat names same-model convergence → the cross-family judge (the cross-family second judge) is what lifts it. Status (the R→S audit §1 ladder): the inferential layer was L1; the eval-gate fixes lift its *correctness*; the RUN lifts it to a *used* signal. Until a run is executed against an **external unsaturated** anchor, `N` is, in the R→S audit's words, "buildable, not run" (registry-N:57) ⇒ still drift.

### 1.2 — WHAT (the run, the R→S audit §6, variant-laddered per invariant #27)

```
V1a minimum   : vanilla-arm(the vanilla baseline arm) vs +harness, on ONE external UNSATURATED benchmark, run manually
V1b triangulate: + a game benchmark + a human-in-the-loop sycophancy probe
V1c attribute  : + ablation (hooks-only arm, leave-one-out) → which component earns its cost
metric = VECTOR (resolved%, median tokens, wall-clock), ¬ scalar
test = paired McNemar (UPPER tail, the McNemar-tail fix) + bootstrap CI + k seeds ; PRODUCTION model, ¬haiku
discipline : kill-criterion WRITTEN BEFORE the run ; report null results as-is (eval/README, harness-improve Stage 4)
```

Why "external unsaturated" [FACT, the R→S audit §5]: SWE-bench Verified is contaminated + saturated (~95% frontier) ⇒ no headroom to detect a prompt layer. Candidates: SWE-bench Pro (Opus 4.5: 80.9%→45.9%), Terminal-Bench 2.0, hardest Aider slice (unit-test-graded ⇒ judge-independent), or a game bench. Caveat [the R→S audit §6]: a prompt layer over an already-strong scaffold has single-digit-pp marginal headroom ⇒ `N` must be large; "Stop Comparing LLM Agents Without Disclosing the Harness" (`arXiv:2605.23950`) — the harness *is* measurable, leaderboards rank model+scaffold pairs.

### 1.3 — HOW (concrete)

1. Pick the V1a primary anchor (the R→S audit Q4 — closest to the owner's production use; owner decides via AskMe). Wire it into `run_suite.py` alongside the existing internal suite as the **external** arm.
2. Choose `vanilla` vs `+harness` arms — `test_vanilla_arm.py`/the vanilla baseline arm already encode the no-plugin baseline; ensure the harness arm loads the live plugin.
3. Write the **kill-criterion first** (e.g. "if resolved% Δ ≤ 0 at upper-tail McNemar p ≥ 0.05 with k≥… seeds on a production model, the bundle does not earn its cost"). This is `harness-improve` Stage 4 made real + the R→S audit's "kill-criterion before the run".
4. Run on a **production** model (not haiku), k seeds; aggregate with `statistical_test.py` (the now-correct upper-tail McNemar from the McNemar-tail fix + bootstrap CI on Cohen's d from the Cohen's-d edge fix + Krippendorff α from the rater-aware-α fix); add the cross-family judge as the disjoint second channel.
5. Publish the vector `(resolved%, median tokens, wall-clock)` **including nulls** (precedent: a candidate sentence measured null at judge-noise α 0.34–0.46 and was reported, not hidden — harness-improve Stage 4 / the R→S audit appendix B).

### 1.4 — Mission frame

N's goal is ⟨hallucinations↓, accuracy↑, tokens↓, sycophancy↓⟩ [the R→S audit §2 node G]. R→S is *closed* exactly when E measures (P, H, A), R feeds E, and E selects S [the R→S audit §2 graph]. N adapts only when R→S is closed; while it is open, N drifts [Lewontin, the R→S audit §5]. So V1 is not "an improvement among many" — it is the precondition for any ΔN being an improvement at all.

`HYPO` (the R→S audit §6, honest): even a correctly-run V1 may show the prompt layer's marginal effect is within noise on a strong scaffold — that is *information* (kill-criterion fires), not failure. The point of V1 is to *learn the sign*, not to confirm a prior.

---

## 2 — INV-A, INV-B, INV-C  [land via harness-improve; selectable only after V1]

```
candidates [HYPO, registry-N:40 ∉ invariants.txt ; the R→S audit / plan node 50] :
  INV-A  ecosystem-mission framing      frame a Δ at Σ-goal level, not a local metric
  INV-B  new-module = mechanism ¬behaviour    (a new module provisions; behaviour stays in N's gates)
  INV-C  anchor borrowed (subagent/owner) claims   extends invariants #1/#4 to claims that arrive via an agent or the owner
landing channel : skill harness-improve  [FACT, skills/harness-improve/SKILL.md viewed]
```

### 2.1 — State (verify)

- `FACT` `invariants.txt` currently holds **31** invariants (`#1…#31`), stable-id format (`grep "^#N "`), `[risk][deontic]` + `Why:` + `Counter:` clauses [live read]. INV-A/B/C are **not** among them.
- `FACT` `skills/harness-improve/SKILL.md` exists and is the documented evolution channel for `N`: Stage 0 anchor-or-stop; Stage 1 verify-against-main; Stage 2 classify→gate; Stage 3 minimal diff; Stage 4 measure + deletion-path; output contract BLUF.
- `ASSOC/owner-memory` INV-A is exactly the correction the owner repeatedly issues ("don't justify a module by saves-tokens; inherit the parent system's goals — truth, capability, self-sufficiency, evolvability"). INV-B is the `G2` split (mechanism vs behaviour). These are *real recurring incidents*, which is precisely the admissible anchor type (harness-improve Stage 0, invariants #1/#3).

### 2.2 — WHAT + HOW (route each through harness-improve)

Class = **Behavioral text** (`invariants.txt`) [harness-improve Stage 2 table] ⇒ gate = single-line invariant-format selftest (`scripts/selftest_random_invariant.sh` / `random-invariant`) + the push-time critic gate (`auto-critic.sh`) + the human-token gate on protocol paths (the protocol-path human-gate PR). One concern per branch/PR.

```
HOW(INV-X) :
  1. anchor   : cite the reproduced incident (INV-A: owner's repeated mission-frame correction, from owner memory;
                INV-B: G2 leak incidents; INV-C: a subagent/owner claim accepted without an anchor)   [Stage 0]
  2. verify   : pull main, confirm absent from invariants.txt (it is, 31 today) ∧ not already a ROADMAP row  [Stage 1]
  3. write    : one stable id each (#32,#33,#34 — ids assigned once, never renumbered, invariants.txt header),
                format [risk][deontic] rule | Why: … | Counter: …                                     [Stage 2/3]
                INV-C as an EXTENSION of invariants #1/#4 (claim↔evidence; no invented behaviour) to agent/owner-sourced claims
  4. gate     : selftest_random_invariant.sh green ∧ auto-critic ∧ human-token (protocol path)         [Stage 2]
  5. measure  : if any reads as a calibration change, eval-reference before/after (label run-eval), null reported  [Stage 4]
  6. delete-path: each new invariant states the Counter under which it does not apply (deletion path open) [Stage 3/4]
```

Caveats (honest):
- `HYPO` INV-A/B/C are proposals, not landed (registry-N:66). They become genes only after passing the gates above.
- `Counter` for INV-A must exist (harness is not append-only): mission-framing is an *obligation on rationale*, not a ban on stating consequences — a Δ may *also* note token economy as a consequence; what is forbidden is token economy *as the rationale*. (This Counter mirrors the existing invariant #5 Counter style.)
- Order vs V1: `selectable(INV-X) ↔ closed(R→S)`. Adding invariants while `R→S` is open is exactly the "variation without selection" failure — they can be *drafted/landed by gate* but their *value* is unmeasured until V1 runs (the R→S audit §8). The honest move: queue them, land the format-safe + critic-safe ones, but do not *claim* they improve `N` until eval says so.

### 2.3 — Mission frame

INV-A is the *self-application* of `G0` (system-over-nodes; defined genome/design-principles.md) to `N`'s own outputs: it makes the harness reason at the ecosystem level by rule, not by reminder. INV-B keeps `G2` (sandbox≠harness; defined genome/design-principles.md) from eroding as modules are added (it is the behavioural mirror of sandbox.md's scope law). INV-C closes a hole in invariants #1/#4: claims that arrive *through* an agent or *from* the owner are still external-state claims and need an anchor (the owner explicitly is held to invariant #1's bar — "user-asserted external-state claims are held to the same bar", `invariants.txt:#1`).

---

## 3 — V6 · formal-specification layer  [maturity; after V1]

```
V6 : one-line spec predicate per gate, checked against impl (property-based test / Z schema)   [the R→S audit §6]
goal : lift load-bearing layers L1→L3 (the R→S audit §1 ladder) ; close the failure CLASS of §3 (not just the instance)
```

WHAT: write a spec predicate for each gate and bind the implementation to it, so an inversion like the McNemar-tail fix cannot survive a commit.

State (verify): `the McNemar-tail fix` fixed the McNemar *instance*; the R→S audit §3 argues the *root cause* was the **absence of a spec predicate** — "had a spec predicate existed (`gate_fires ⟺ P(X≥r|H₀)<α`), the implementation `range(reg+1)` would be mechanically checkable against it." The test `test_statistical_test.py` exists [FACT, eval/ listing] but the R→S audit notes the original test hard-coded a value the buggy code never produced (tested the parser, not the formula). ⇒ V6 = make the *formula* checkable, not just the parser.

HOW (Δ, the R→S audit §6):
```
spec predicates (examples, the R→S audit §6) :
  verify_gate   ⟺ P(X ≥ regressions | H₀) < α            (upper tail — the McNemar-tail-fix invariant, now as a checked spec)
  cycle_blocks  ⟺ last3 ≡ current                         (cycle-detector)
  push_allowed  ⟺ ∃ verdict ∧ sha256(diff) = verdict.sha  (critic-binding)
```
1. Encode each as a one-line predicate; bind via property-based tests (Hypothesis-style) or Z schemas — assert the *formula*, fuzzed across inputs, not a golden string.
2. Machine-encode the ~2/31 genuinely formal invariants (the R→S audit §1: only ~2 are machine-checkable) and **explicitly label the other 29 as heuristic deontic maxims, not formal** (matches `invariants.txt` header self-description: "Deontic tags and Counter clauses are associative draft").
3. Home: lives under `eval/` + `scripts/selftest_*`; gate class = Mechanical/Calibration (harness-improve Stage 2).

Mission frame: evolvability — a spec layer makes `N` *self-checking at the formula level*, so regressions are caught by machine, not by a reviewer's eye (the R→S audit §3 root-cause closure). `HYPO`: V6 is a plan; no spec predicates exist in the repo yet beyond the now-correct code.

---

## 4 — V7 · SDL model  [makes "R→S open" inspectable; last]

```
V7 : graph §4 (the R→S audit) → SysML internal block diagram (G/P/H/A/C/E/S/R) + Z schemas for edge behaviour
```

WHAT: formalize the R→S audit's §2 system graph as an SDL model so a property like "`R→S` is open/closed" is **mechanically inspectable**, not rhetorical.

State (verify): `references/` holds `protocol/{format,co-system,cross-cutting}` + `ADR-003` + `research-anchors.md` + `per-stack/` [FACT registry-N:62, repo listing]. There is **no** SysML/Z model today (the R→S audit §2: "an informal model awaiting formalisation"). ⇒ V7 is greenfield modelling.

HOW (Δ, the R→S audit §7): nodes `G,P,H,A,C,E,S,R,N1` as SysML blocks; edges as Z state-schemas with predicates (e.g. `E_measures(P,H,A)`, `R_feeds(E)`, `E_selects(S)`); a checker that evaluates edge predicates against repo state. Store under `references/` (the protocol-model home).

Mission frame: the deepest evolvability lever — the system can *answer questions about its own structure* formally. Last because it depends on V1 (you model a *closed* loop once it exists) and V6 (predicates are the Z edge-conditions). `HYPO`: entirely a plan.

---

## 5 — What is NOT a Δ here (anti-scope, invariant #3)

- Re-fixing the gate: the gate-fix is present in the snapshot code (`statistical_test.py:196`,`:265-267` = FACT; the eval-gate fixes merge-status = agent-reported). Do **not** re-open the inversion as if unfixed (harness-improve Stage 1: a recorded decision must be quoted, re-open needs *new* evidence). The drift diagnosis now rests on *not-yet-run*, not *broken-gate*.
- README claim-lowering (V2), token instrumentation (V3), channel-independence (V4), dogfood-gates-on-docs (V5) are real vectors from the R→S audit but **out of this file's mandated scope** (owner named V1 / INV-A·B·C / V6 / V7). They sit below V1 and are selectable only after R→S closes; record as ROADMAP candidates (harness-improve Stage 0 fallback).

---

## §Ledger (epistemic, this file)

```
FACT (issue/PR/file) :
  eval gate fixed = FACT, anchored to readable snapshot code: `statistical_test.py:196` (McNemar upper tail) + `:265-267` (rater-aware Krippendorff α)
  the eval-gate fixes' issue MERGE-status = agent-reported (GitHub unverifiable here, not gh-verified)
  eval/ contains run_suite.py, statistical_test.py, test_vanilla_arm.py, test_second_judge.py, criteria.md, questions/, adversarial/
  invariants.txt = 31 invariants, stable-id format (live read) ; INV-A/B/C ∉ it
  skills/harness-improve/SKILL.md = the landing channel (Stage 0–4, class→gate table, critic + human-token gates) [live read]
  eval/README: 17 probes (11 adversarial + 6 questions), 18 binary criteria, same-model convergence caveat, "no question regresses" merge bar
  the R→S audit: R→S binding constraint; external-unsaturated benchmark rationale (SWE-bench Verified saturated ~95%); metric=vector; kill-criterion-first; V6 root-cause = missing spec predicate; V7 = SysML/Z
ASSOC :
  INV-A = owner's recurring mission-frame correction (owner memory) = admissible incident anchor
  INV-B = G2 (sandbox≠harness) as a behavioural invariant
HYPO :
  V1 even run-correctly may show within-noise marginal effect on a strong scaffold (= information, kill-criterion, not failure)
  INV-A/B/C are proposals; become genes only after format-selftest + critic + human-token gates
  V6, V7 are plans; no spec predicates / SDL model in the repo yet
  "selectable(x) ↔ closed(R→S)" — corollary of the R→S audit §8, not an executed result
Q :
  V1 primary anchor (the R→S audit Q4) — which unsaturated benchmark is closest to owner production use (owner decides via AskMe)
  φ-values of every N gene undefined pre-run (registry-N:66)
```
