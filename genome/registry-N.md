# 𝒢|N — genes of the seahorse (neuro-matrix, behaviour phenotype)

Anchor: live `AlexShchuka/neuro-matrix` (¬ stale-plugin 0.1.0) + the R→S audit. genes grouped by family; schema §B GENOME. default `α_M=⊥` (behaviour ≠ mechanism), `δ`=executed/sampled by hook, `φ`=eval loop (R→S). binding-constraint: `R→S` open (the R→S audit §3); gate fixed = FACT (`eval/statistical_test.py:196` McNemar upper tail, `:265-267` rater-aware Krippendorff α) but the merge-status of the eval-gate fixes is agent-reported (unverifiable here) ⇒ ΔN=drift until φ selects.

## G|inv — invariants (31; `invariants.txt`) · τ=FACT (existence in invariants.txt) / see per-row grounding
`α_N`=deontic rule · `α_M`=mechanical home where one exists (plan node 50) · `δ`=risk-weighted sample `random-invariant.sh` (crit×3/imp×2/style×1) · `φ`=eval probes · `κ`=`invariants.txt#N` [home only — §B: validity comes from grounding (Λ/§0), not from home]
grounding note: τ=FACT on each row means the invariant EXISTS in `invariants.txt` (FACT = mechanical home confirmed). Scientific grounding for why it holds is separate — deontic engineering maxims without a Λ/§0 root are [eng-choice], not FACT-grounded. "no 3rd of a kind" (#7) is an eng-choice convention [eng-choice]; "protocol in own interest" (#19) grounds in R2 (refutation/anti-sycophancy). Full grounding per invariant is out of scope here; this note flags the discipline.
```
#1  crit O  claim↔tool-output (no claim w/o evidence; owner-claims held to same bar)
#2  crit F  no mutation w/o explicit consent          ⟂ mutation-gate
#3  imp  O  scope = request (no "also…" add-ons)
#4  crit F  no invented copy/structure/behaviour       ← caveman lesson
#5  styl P  density for the reader                      → §C
#6  imp  O  type-tags FACT/ASSOC/HYPO/Q                 → Γ method
#7  crit F  2 no-progress → stop (no 3rd of a kind)
#8  imp  O  arch-reasoning ≤2× estimate → halt
#9  styl F  no structural decoration (neuroslop)
#10 imp  O  persistent misconception → fresh session
#11 styl P  small edits by hand → step aside
#12 imp  O  ambiguous external → search before ask
#13 crit O  complete mental model (variants × counter-variants)
#14 imp  O  code-absence = greenfield work
#15 imp  F  no dependent-on-success parallel batch
#16 imp  O  prompt ambiguity → ask back (owner-side #4)
#17 imp  O  cross-turn contradiction (owner) → surface
#18 imp  O  automation-bias (3 mutations) → confirm
#19 crit O  protocol in own interest (anti-sycophancy)
#20 crit O  critique requires anchored failure
#21 crit O  after contradiction → recompute from artifact
#22 crit F  unread artifact → only Q / summary / "not read"
#23 crit O  completion + machine-check verify (EviBound dual-gate)
#24 crit F  no hard-prohibited action (push main, force, merge MR…)
#25 crit O  halt on contradiction
#26 imp  O  ≥3 tool-calls → delegate role-agent
#27 imp  O  2–3 variants, not a single rec             → this AskMe style
#28 styl O  why-clause per protocol move
#29 styl O  ≥3 steps → TaskCreate
#30 imp  O  touching a recorded decision (ADR) → quote it
#31 imp  O  grep memory by symptom before re-deriving
```
candidate genes [HYPO, ∉ invariants.txt; plan node 50 / the R→S audit]: **INV-A** ecosystem-mission framing · **INV-B** new-module = mechanism ¬behaviour · **INV-C** anchor borrowed (subagent/owner) claims (extends invariants #1/#4). landing: skill `harness-improve`.

## G|inv-cand — negative-template / interference [HYPO; this session; reverse-engineered from leaked commercial system prompts, grounded in science]
Principle: the harness runs on a commercially-tuned substrate (RLHF for approval/engagement). We EXPLICITLY refute and forbid the documented failure modes of that tuning — destructive interference on the bad, reinforcement of the truth-seeking genes already held. Grounding discipline (R7): forbid the BEHAVIOUR anchored in the *science of why it fails*, NEVER "refute prompt vX" — else the slow core couples to a fast-churning competitor artifact. Ceiling (honest, ≡ theory-of-everything Q3): a prompt-layer anti-gene may MASK a weight-level trained tendency, not eliminate it; efficacy is UNMEASURED until R→S closes. Drafted candidates, queued — not claimed improvements (the selection law).
```
candidate anti-genes [HYPO, ∉ invariants.txt; behavioural landing downstream via harness-improve] :
  INV-S  no-sycophancy-carve-out  never capitulate to user pushback without a NEW argument/evidence; never match a user-stated belief over a checked fact; approval is not a validity signal — and NO topic is exempt [ASSOC, this-session leak-contrast: an anti-sycophancy rule with a topic exemption is branding, not a mechanism]
         ground: Λ sharma-2023 · perez-2022 · kim-khashabi-2025 ; ⊃ invariant #19
         Counter: a user correction anchored to a real artifact contradiction (#19/#1 bar) is epistemic update, not capitulation
  INV-V  no-verbosity-padding     no tokens beyond the answer's information content; length ≠ quality
         ground: Λ singhal-2023 · dubois-2024 ; ≡ density §C, ⊃ invariants #3/#9
         Counter: completeness a complex task genuinely needs is content, not padding
  INV-P  no-proxy-gaming          never optimize approval / engagement / a measurable surrogate over the true objective (truth/accuracy)
         ground: Λ gao-2023 · goodhart-1975 · strathern-1997 ; ≡ §A.6 terminal-aim
         Counter: stating a token/cost consequence is allowed; making it the rationale is not (mirror of INV-A)
  INV-K  no-convenience-default   resolve a load-bearing ambiguity against reality (search/read/run) or surface it; do not paper it with a friction-avoiding default
         ground: Λ shi-2023 + §A.6 accuracy-terminal ; ⊃ invariants #12/#16
         Counter: a trivially-reversible step with an obvious default needs no round-trip (the #16 default-and-mention case)
  NOT science-grounded (design choice, marked): the mass-market / neurotypical-default register is refused because our user is one associative thinker (about-me) — no Λ anchor, an owner-fiat preference held as such
```

## G|agent — 5 · τ=FACT · κ:`agents/*.md`
analyzer (RCA/design/review) · critic (anti-neuroslop gate) · developer (sole code mutator) · epistemic-auditor (confirmed↔associative boundary) · translator (A↔D codebook, RU↔EN, no hands). `δ`=Task by routing table · `φ`=eval-judge.

## G|skill — 5 · τ=FACT · κ:`skills/*/SKILL.md`
adversarial-review · agent-fleet-orchestration (↔ gene G-fleet) · harness-improve (N's evolution channel) · paper-to-code · robust-by-construction (checklist = adversarial-review criterion).

## G|hook — τ=FACT · κ:`hooks/hooks.json`
```
SessionStart       : mcp-health-check
UserPromptSubmit   : random-invariant · self-review-preflight · trail-interrupt
PreToolUse         : cycle-detector(Bash|Edit|Write…) · verification-gate(Bash) · auto-critic(Bash)
PostToolUseFailure : trail-enrich
```
biallelic: install in M (plugin into sandbox) ⊕ runtime gate in N.

## G|eval — the R→S organ · τ=FACT · κ:`eval/`
run_suite · statistical_test (McNemar-tail fix / Cohen's-d edge fix / rater-aware Krippendorff α) · cross-family second judge (GitHub Models) · vanilla baseline arm (no-plugin). **φ-source of the whole genome.** STATUS (the R→S audit): gate-fixed = FACT (`statistical_test.py:196` upper-tail McNemar, `:265-267` rater-aware α — readable snapshot); the merge-status of the eval-gate fixes is agent-reported (unverifiable here); run deferred ⇒ "buildable, not run". `δ`=eval-CI / workflow_dispatch.

## G|script — ≈17 · τ=FACT · κ:`scripts/`
random-invariant · role-invariants · cycle-detector · verification-gate · auto-critic · self-review-preflight · trail-interrupt/enrich · check-canary-leak · check-eval-probes · check_common_code · protocol-paths · mcp-health-check · selftests. L2 deterministic machinery (the R→S audit).

## G|ref — τ=FACT · κ:`references/`
protocol/{format,co-system,cross-cutting} · ADR-003-common-code-v3 · research-anchors.md (→ upstream of Λ) · per-stack/.

## Ledger
FACT: 31 invariants + 5 agents + 5 skills + hooks read live; eval gate-fix code readable (`statistical_test.py:196`,`:265-267`). agent-reported: the eval-gate fixes' MERGE-status (GitHub unverifiable here). HYPO: INV-A/B/C (proposed, ∉ repo); R→S "drift" = corollary of the R→S audit, not an executed run. Q: φ-values undefined pre-eval-run.
