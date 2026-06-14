# DEPT · v-toe — the R→S audit (Theory of Everything, condensed)

This document is DEPT-stratum, preserved and decoupled from CORE: it is not itself truth, and it is neither a gene 𝒢 nor an archive entry Λ. Source [FACT]: the R→S audit (origin recorded as provenance in archive/archive.md) plus the comment thread carrying the eval-gate fixes. The claims below carry the audit's own internal tags; this file re-tags, it does not re-prove.

`v-toe` = a single map of the co-system Σ: formal-methods **spec** + cross-disciplinary **graph** + science-determined **dev-vector**. Demotes the bug-list to an appendix; spine = spec → ideas → plans → sources. Method (binding, the R→S audit): every load-bearing claim is verified *outside* the document — non-LLM ground truth (a stats library), or a disjoint source, or executable repo code. Discipline: no single study makes a FACT; failed claims are discarded, not displayed.

## §1 — Central thesis (the diagnosis)
The repo claims far more formality than it holds — "more rigour than it holds" [FACT, the R→S audit §1]. Anchors: README.md:3 "invariants obey logic+math" / "Nash-equilibrium cooperation"; README.md:85 "pre-registered statistical proof"; README.md:100 "2026 SOTA".
```
gap-table [FACT, the R→S audit §1] :
  FormalMethods   claimed "logic+math"      actual ~2/31 invariants machine-checkable; 29 = NL deontic maxims
  FormalSpec      claimed "proof"            actual no spec; invariants.txt = NL deontic [O|P|F]; rule inverted (§3)
  SDL             claimed "co-system"        actual no formal model; graph (§2) informal, awaits SysML/Z
```
Diagnosis: the gap between claimed and actual formality; closing it is the dev-vector (§6: V6 + V7).

### §1.1 — Formality-maturity ladder (L0–L3; rubric replaces arbitrary scores)
```
L0  prose claim                              assertion, no executable artifact
L1  executable code, unchecked               runs; no test binds it to intent
L2  code + deterministic test                selftest binds impl→behaviour on examples
L3  code + formal spec, checked against it    property proved/verified, not illustrated
```
```
layer-levels [FACT, the R→S audit §1] :
  deterministic machinery (weighted sampler 3/2/1, cycle-detector, sha256 critic-bind, canaries)  = L2  (selftests 300/300, 28/28)
  inferential layer (McNemar/Wilcoxon/Cohen's d/Krippendorff α)                                   = L1  (only hard gate; inverted §3; test = hardcoded string ¬formula)
  game theory ("Nash-equilibrium","dominates")                                                    = L0  (zero strategy sets/payoffs/equilibria in repo)
  citation catalog                                                                                = ext-spot-verified (33/33 real; 44/47 pending-verification)
verdict-1-line : rigour concentrated L2 in plumbing, collapses to L0–L1 exactly where advertised loudest
                 (the "statistical proof" + the "game theory") ; vector lifts load-bearing layers L0/L1 → L3
```

## §2 — System graph (informal SDL model; SysML/Z candidate, vector V7)
```
nodes :
  G  goal       hallucinations↓ ∧ accuracy↑ ∧ tokens↓ ∧ sycophancy↓
  P  protocol   CLAUDE.md + 31 invariants + sampler
  H  runtime gates                          A  5 agents
  C  catalog    47 anchors                  E  eval loop
  S  mutation   sessions ↦ edits            R  reality  (tasks, ext benchmarks, compiler/tests)
  N1 developer
edges [FACT, the R→S audit §2; ✓=holds ⚠=weak ✗=broken] :
  C  ──grounds──▶ P        ✓ 33/33 real, 44/47 pending-verification
  P  ──serves──▶  G        ✓ by design
  H  ──enforces─▶ P        ⚠ machine-enforced for ~2/31
  S  ──mutates──▶ P,H,A,E  ✓ directed (sessions), ¬random
  R  ══arbiter══▶ G        ✓ stated (README:7 "reality is the only arbiter")
  E  ──measures─▶ P,H,A    ✗ SEVERED — McNemar inverted (§3) ∧ judge=generator
  R  ──feeds──▶   E        ✗ MISSING — no vanilla arm (run_suite.py:214-219); no ext benchmark
  E  ──selects──▶ S        ✗ consequence — selection signal never reaches the mutations
  R  ──felt──▶ N1 ──▶ S    ⚠ only live path; routes through a miscalibrated node (introspection; cf METR)
  README ─claims▶ all      ⚠ showcase > code (Nash / 2026-SOTA / pre-registered / 4≠5 agents)
```
Graph-property verdict [FACT, the R→S audit §2]: there is no working path from R to S — the intended loop R→E→S is cut at E (the severed R→S edge). So the generator (P, H, A, C, S) is built and works, but the feedback edge back to reality is open. "100 mutations from sessions" is therefore variation plus heredity *without* differential selection — the selection sieve is open. In Lewontin's terms: variation is present, heredity is present (invariants.txt + git), but selection-by-environment is absent — so this is drift, not adaptation. Formalizing the graph in SysML (an internal block diagram) or Z (a state-schema with edge-predicates) would make "R→S absent" mechanically checkable rather than rhetorical (V7).

## §3 — Central finding: the inversion (the one hard stat gate, inverted in the tail)
```
[FACT, reproduced vs non-LLM ground truth, the R→S audit §3] : the only hard statistical CI gate is inverted.
anchor eval/statistical_test.py:189 :
  p = sum(math.comb(n,k) for k in range(regressions+1)) / (2**n)
  range(regressions+1) ⇒ sums k∈[0,regressions] = LOWER tail P(X≤regressions), X~Binom(n,½)
  one-sided McNemar firing on regressions REQUIRES UPPER tail P(X≥regressions)
ground-truth table (vs scipy.stats.binomtest, statsmodels …mcnemar; NOT an encyclopedia link) :
  b=5  c=0 (worse)      repo p=1.00000  correct=0.03125  ⇒ repo PASSES, correct=BLOCK
  b=0  c=5 (better)     repo p=0.03125  correct=1.00000  ⇒ repo BLOCKS, correct=pass
  b=11 c=0 (mass reg)   repo p=1.00000  correct=0.00049  ⇒ repo PASSES, correct=BLOCK
  repo p ≡ binomtest(b,n,½,alternative='less') bit-for-bit  ⇒ gate passes regressions, blocks improvements
root-cause = absent spec predicate :
  had  gate_fires ⟺ P(X≥regressions | H₀) < α  existed, range(reg+1) would be checkable against it ⇒ inversion could not survive commit-1
archaeology [FACT] : present at commit-1; mcnemar_one_sided edited ×2 (count + threshold) but tail-direction never touched;
                     test eval/test_mock_e2e.py:283 hardcodes a correct upper-tail value the buggy code never produces ⇒ tests parser, ¬formula
```
This is **the binding constraint** (genome §D): `R→S` open in N ⇒ ΔN = drift until closed. The single hard gate of an anti-neuroslop harness, inverted since birth, survived two reviews.

## §4 — Cross-disciplinary layers (typed by evidence strength; importance does not exempt a claim from proof)
```
4a ESTABLISHED-FRAMING (load-bearing today) :
  principal-agent / information-asymmetry  [ESTABLISHED, the R→S audit §4a]
    "AI = hypothesis-generator w/ more local knowledge; developer-principal decides ∧ bears responsibility" IS a principal-agent structure (repo L6)
    anchors: Phelps&Ranson 2023 "Of Models and Tin Men" arXiv:2307.11137 (LLM agents show hidden-action w/o controlling harness);
             Hadfield-Menell 2021 (UC Berkeley, CIRL/off-switch); repo arXiv:2601.23211, arXiv:2504.03255
    caveat(corrected) : ONE alignment framing, ¬"the central schema" — coexists w/ RLHF/RLAIF, reward-modelling, scalable-oversight, debate
4b ANALOGY (ASSOC — a working lens, ¬mechanism) :
  dynamical-systems / attractors / edge-of-chaos  [ASSOC, the R→S audit §4b]  applied to the AGENTIC INFERENCE LOOP (¬weight-training)
    sticking-attractors ∧ help→saturate→collapse as vocabulary for loop-collapse + cycle-detection (repo L8)
    anchors: Hopfield 1982 / Nobel Physics 2024 (assoc. memory); Bertschinger&Natschläger 2004 (computation near order↔chaos in RNNs)
    discipline: NO transfer of any training-time mechanism
4c HYPOTHESIS (HYPO — falsifiable, untested; the home of "something new") :
  open-ended-evolution / config-search for the harness  [HYPO, the R→S audit §4c]
    R→S IS variation+selection; missing selection-signal (V1) = what makes harness-config-evolution real ¬drift
    anchors: PNAS "Evolvable AI" 10.1073/pnas.2527700123 (SINGLE framework paper, ¬proof); POET Wang+2019 arXiv:1901.01753; Stanley 2019 Artif.Life 25(3)
    HYPO: a digital-Petri-dish over harness-configs could auto-select robust invariants — untested; depends on a working fitness signal (V1)
  intrinsic-motivation / curiosity  [HYPO, scope-caveat, the R→S audit §4c]
    anchors: Oudeyer&Kaplan 2007 (Front.Neurorobotics); Pathak+2017 arXiv:1705.05363
    caveat: these are RL training-signal constructs; transfer to a FROZEN-model prompt harness = hypothesis ¬mechanism (today category-error; future config-search objective)
  predictive-coding / Free-Energy-Principle  [HYPO, CONTESTED, the R→S audit §4c]
    anchor Friston 2010 nrn2787 ; contested hard-to-falsify/overgeneral (Colombo&Wright 2021; Biehl+2021); "minimise FE"↔thermo = formal analogy ¬physical derivation
    kept ONLY as contested analogy, never as justification
  Viable-System-Model (Beer S1–S5)  [ASSOC, design-analogy, the R→S audit §4c]  for control-harness recursion; ¬"mathematics", ¬rigid-hierarchy
4d DISCARDED (failed independent verification — listed once for due-diligence, ¬carried as content) [the R→S audit §4d] :
  Jarzynski-equality → model-confidence       (zero papers under that task; re-confirmed; UQ/calibration lit exists, no fluctuation-theorem link)
  "deep nets train ONLY at criticality / MIT"  (false attribution — Pennington/Schoenholz/Ganguli @ Google-Brain/Stanford; correct = edge-of-chaos init SPEEDS/DEEPENS, ¬"only")
  information-bottleneck "compression phase" as fact  (contested, Saxe+2018 ICLR)
```

## §5 — Verified external anchors (FACT, the R→S audit §5)
```
citation-survival 33/33, 0 phantoms (spot-check 5/5). EviBound arXiv:2511.05524 (100%→25%→0%, 8 tasks ~8.3%) EXACT but SINGLE-study ¬law; SAVeR arXiv:2604.08401 (ACL 2026) real.
industry (multi-sourced) : CodeRabbit 470 PRs ~1.7× +75% logic-bugs ; Google ~75% AI-written (2026) ; Microsoft 20–30% (range ¬"~30%").
benchmarks : SWE-bench Verified contaminated+saturated (~95% frontier); OpenAI Feb-2026 "deprecation" is what that rests on; SWE-bench Pro harder (Opus 4.5 80.9%→45.9%); Aider Polyglot unit-test-graded (judge-independent); harness-disclosure itself a topic arXiv:2605.23950.
analogies (dev-supplied, verified) : Drosophila whole-brain emulation Eon 2026 arXiv:2602.17997 (connectome→behaviour w/o training, validated vs real fly); pygmy-seahorse/coral mutualism PNAS 10.1073/pnas.2423818122 (adaptation by gene-loss, CRISPR-confirmed). Both establish claims by outcome-measurement vs ground truth — the standard the harness lacks.
evolution-requires-heredity : Lewontin's 3 conditions (variation, differential-fitness, HERITABILITY) necessary+sufficient (Britannica; SEP). drift = evolution w/o adaptation ⇒ "directed mutation from sessions" needs a fitness signal to be adaptation ¬drift.
```

## §6 — Development vector (priority-ordered; V1 = binding constraint; each step carries variants per the cross-AI advisory exemplar)
```
V1  Close R→S   [binding-constraint; do first]
    (a) minimum     : fix McNemar sign (upper tail) + 1 ext UNSATURATED benchmark (SWE-bench Pro / Terminal-Bench 2.0 / hardest Aider slice / a game bench); 2 arms (vanilla / +harness); run manually → "does the bundle help?"
    (b) triangulation: + a game bench + human-in-loop sycophancy probe → goals the code-bench can't see
    (c) attribution : + ablation (hooks-only arm, leave-one-out) → which component earns its cost
    metric = VECTOR (resolved%, median-tokens, wall-clock) ¬scalar ; paired McNemar(upper!) + bootstrap-CI + k seeds ; PRODUCTION model ¬haiku ; kill-criterion written BEFORE the run
    note: a prompt layer over an already-strong scaffold has single-digit-pp marginal headroom ⇒ N must be large
V2  showcase ⊆ verified-artifact   (a) lower claims ("Nash"→"cooperation protocol"; drop 2026-SOTA ×3; 4→5 agents; N7→open; EviBound single-study caveat into README) (b) raise code to claims (build the formal game; real stack checks) (c) split README shipped vs research-vector
V3  instrument tokens   CLAUDE.md ≈8,960 chars ≈1.6–2.2k tokens + ~1 invariant/turn + Opus critic on push. (a) measure (b) budget gate (c) optimise. "tokens↓" must BEAT measured overhead
V4  channel independence   compiler/tests (extend verification-gate to real stacks = make N7 real — but N7 live-status is in CONFLICT: ROADMAP.md:25 status=shipped vs verification-gate.sh:72-94 still sh/py/json only; [ASSOC/conflict, unverifiable-here]) + human + cross-family judge + production metrics ; same-family LLM layers = ONE channel (correlated errors)
V5  dogfood gates onto docs   CI "status:shipped ⇒ anchor-diff" (verification-gate aimed at ROADMAP) ⇒ catches false accounting (N7) automatically
V6  formal-spec layer [core of formal-methods vector]   1-line spec predicate / gate (verify_gate ⟺ P(X≥r|H₀)<α ; cycle_blocks ⟺ last3≡current ; push_allowed ⟺ ∃verdict ∧ sha256(diff)=verdict.sha) checked vs impl (property-based / Z) ; machine-encode ~2/31 ; explicitly label other 29 heuristic ⇒ lifts L1→L3, closes §3's failure class
V7  SDL model   graph §2 → SysML-IBD (structure G/P/H/A/C/E/S/R) + Z schemas (edge behaviour) ⇒ "R→S open" inspectable ¬rhetorical
```

## §7 — Open questions (Q, the R→S audit §7)
```
Q1 does the always-on P layer earn its token cost net, given curse-of-instructions? → arm-C of V1
Q2 which of 31 invariants actually move outcomes? → leave-one-out ablation
Q3 can a prompt layer REDUCE sycophancy (training-level property) or only MASK it (arXiv:2603.16643)? → human-in-loop bench
Q4 which unsaturated benchmark closest to the developer's production use? → V1 primary anchor
```

## §8 — Verdict (the R→S audit §8)
Not neuroslop in README:29's sense ("plausible but architecturally meaningless"): the foundation is real (0 phantoms / 33 cites), the machinery is L2, the self-checking is genuine. The diagnosis is a working generator with an OPEN R→S feedback edge — rigour in the plumbing (L2), thin (L0–L1) exactly where advertised. The obligatory first move is V1 (fix the McNemar sign + an external unsaturated outcome anchor); the maturity vector is V6 + V7 (formal spec + SDL). Everything else (skills, agents, the §4 hypotheses) is a mutation that cannot be selected until R→S is closed.

## §9 — Eval fixes landed in the R→S audit comments (the R→S prerequisites; transient — discard on land)
```
[FACT, the R→S audit comments; each verified vs non-LLM ground truth, golden-tested to fail on the OLD behaviour]
the McNemar-tail fix          FIXED  inverted tail: lower P(X≤r) → upper P(X≥r). vs scipy binomtest(alt='greater') + statsmodels mcnemar; canon Wikipedia/CRAN exact2x2.  [DONE]
the Cohen's-d edge fix        FIXED  zero-variance: perfectly-consistent improvement scored d=0 (CI(0,0)) ⇒ gate blocked strongest signal. → sd=0,mean>0→+∞ (pass); mean<0→−∞ (fail); mean=0→0. vs CRAN effectsize, MRC-CBU.  [DONE]
the rater-aware-α fix         FIXED  Krippendorff α was rater-blind: one judge's k runs counted as raters (α=0.375 from 3 runs = run-noise). → group by `rater`, aggregate a rater's runs (majority) to 1 rating, α across raters; 1 rater→None (criteria.md:49); ≥2→genuine inter-rater.  [DONE]
the cross-family second judge WIRED  the missing real `rater`: GitHub Models (free, in Actions, no API key; permissions: models:read; actions/ai-inference@v1; NON-Claude family e.g. openai/gpt-4o-mini). different family ON PURPOSE — same-family share error modes (arXiv:2506.07962); triangulation (Munafò&Davey-Smith Nature 2018). deterministic parts tested locally; live call gated/non-blocking (workflow_dispatch).  [WIRED, live run deferred]
the vanilla baseline arm      LANDED  run_suite.py skipped empty calibration ⇒ could only compare 2 plugin versions. → `vanilla` sentinel = empty system-prompt, NOT skipped, flows as bare Claude = the structural R→S edge. minimal diff; 4/4 golden tests fail when reverted; regression clean (stat 19/19, judge2 3/3, mock-e2e ALL PASS); run_suite materialization calls no LLM ⇒ locally verifiable.  [LANDED, A/B run deferred to product maturity]
```
```
state-of-R→S [FACT, the R→S audit comments] :
  buildable prerequisites COMPLETE : gate correct (the McNemar-tail, Cohen's-d, and rater-aware-α fixes) and the cross-family judge wired and the vanilla arm landed — all deterministic, golden-tested, vs non-LLM ground truth.
  DEFERRED (owner-gated, "fix the instrument first, run it when the product is less raw") : the live A/B run for merge verdicts (first inter-rater α rater1 Claude + rater2 GitHub-Models; then A/B vanilla vs +harness vs an ext UNSATURATED benchmark — avoid saturated/contaminated, SWE-bench Verified deprecation OpenAI Feb-2026, use SWE-bench Pro).
  remaining CODE (no run) : N7 stack-coverage — ~/.neuro-matrix/ROADMAP.md:25 marks status=shipped (tsc --noEmit, dotnet build, swift build); but ~/.neuro-matrix/scripts/verification-gate.sh:72-94 case-block still covers only sh/py/json. ROADMAP vs snapshot-code DISAGREE; unverifiable-here which is live. [ASSOC/conflict, ¬FACT-open] ; eval power (N=17 probes underpowered for Wilcoxon/McNemar).  → see bugs.md
```
```
parking-lot consolidation [FACT, the R→S audit comments] :
  MIGRATED to this vector (theory-relevant) : the vanilla A/B step (the parking-lot consolidation §3, from the vanilla-baseline-arm idea) = the structural R→S step ; HMM latent-state for halt/drift/invariant-sampling (the parking-lot consolidation §1, from the halt/drift-detection idea) [HYPO ¬commitment] — forward-filtering over cycle-trail, target metric tokens-after-stuck-onset, gated on a labeled trail corpus + the now-correct eval; counter-variants (pointwise change-point, supervised classifier); weakest sub-state S3 "neuroslop-risk" (the parking-lot consolidation §2) has no trail observable ⇒ separate detector.
  NOT migrated (stay parked w/ triggers) : role-subset invariant inheritance (N8) ; two-way Telegram reader / prompt-injection OWASP-LLM01 ; emit-time body↔deontic check (the INV_LINES PR closed the known path: LINES→INV_LINES) ; MCP external-artifact verification (jupyter-mcp inspectable; sympy-mcp Docker-only parse_expr→eval ⇒ sandbox required).
```

## §I — Ledger (this entry)
```
FACT  : the R→S audit exists+OPEN; the McNemar inversion (statistical_test.py:189, reproduced vs scipy/statsmodels); the eval-gate fixes statuses (comments); L2 selftests 300/300,28/28; 33/33 citations; PNAS seahorse + Drosophila anchors.
ASSOC : §4b dynamical-systems lens; §4c VSM design-analogy; the graph as an INFORMAL SDL model (formalisation = V7, not yet done).
HYPO  : §4c open-ended-evolution/intrinsic-motivation/predictive-coding; V1(c) attribution outcome; "directed evolution → adaptation only once R→S closed".
Q     : the R→S audit §7 Q1–Q4; whether a prompt layer can reduce (¬mask) a training-level property.
transient : whole entry — once the eval-gate fixes are implemented, discard; the live A/B run, V2–V7, N7, eval-power are the open work. Discarding v-toe does not force a rebuild of GENOME.
```
