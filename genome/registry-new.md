# 𝒢|+ — new genes (owner-selected) + channel genes

Re-anchoring shows 3/4 new genes are **¬greenfield** — seeds already exist in M (membackup, obs) and N (skills). placement/extension decided by 𝕆 (law, §B). Schema: §B GENOME.

## New genes
```
G-know    knowledge / second-brain   τ=FACT (seed exists)
   α_M: membackup (sync ~/.claude memory ↔ host) + memory store ~/.claude/memory
   α_N: recall discipline (#31 grep-memory-by-symptom) + memory-write protocol
   E: →durable knowledge  ⊣G-membackup, ⊣Λ     δ:𝕆     φ: recall-hit / Δre-derivation
   ASSOC: cavemem (cross-agent memory)          Q: extension beyond sync (index / extract / semantic-search)

G-fleet   orchestration / fleet      τ=FACT (seed in N)
   α_N: skills agent-fleet-orchestration + adversarial-review + 5 agents
   α_M: Task/subagent substrate (native Claude Code)
   E: →parallel build, no collision  ⊣role-agents, ⊣#26     δ: ≥3 agents / disjoint scope     φ: Δwallclock @ quality
   ASSOC: cavecrew-*

G-obs+    observability / G5         τ=FACT (seed exists)
   α_M: obs (observable state-map + slog single sink) — G5 partial
   α_N: feedback interpretation (what worked) → eval/φ
   E: →single sink + feedback  ⊣G-obs     δ: always     φ: IS the φ-channel (selection signal into R→S)
   NB: candidate to close the open R→S loop (the R→S audit)

G-domain  domain-packs               τ=HYPO (greenfield)
   α_N: pack-as-skill (domain rules) + Λ department
   α_M: ?  (Q — provision domain tools?)
   E: →"any task" (meta-vision)  ⊣Λ.{interviews,design,psychology,…}     δ: 𝕆-select     φ: task-success / domain
   ASSOC: JuliusBrussee/skills (grill-me, interface-kit, junior-to-senior)

G-route   declarative routing / C3    τ=FACT (seed exists: the routing-policy + lane-map table below; config-driven, a unit's home is read, never inferred)
   α_Γ: the routing-policy + lane-map below — a declarative gene (config, ¬content-inference). darwin DEFINES it.
   α_M: mirabilis PRODUCES the changeset-manifest (C1) whose units this policy routes; the manifest is the routed object.
   α_N: neuro-matrix storozh skill READS this policy (C4 routing-check) — flags a misroute, advisory-only (¬gate).
   E: →deterministic unit→repo placement, no collision across parallel slices  ⊣G-route policy, ⊣C1 manifest     δ: per manifest-unit     φ: misroute-rate (storozh flags / units)
   home: routing-policy + lane-map tables (this file) [MAY ROT — the tables are the mechanical home]
   grounding: G4 config-driven (R4) + G1 no-churn (§A.3 a constant/inferred home is a frozen gene) + G13 (design-principles.md) + R7 pace-layering (knowledge-lane ≺ code-lane churn). Validity from HERE, not from the table's location (§B home vs grounding).
   ASSOC: storozh routing-check (C4)     Q: per-unit-type φ once storozh runs (misroute counts pre-eval)
```

## Routing-policy + lane-map (contract C3 — declarative; storozh READS, darwin DEFINES)
Declarative only: a unit's destination is decided by its **declared unit-type**, never inferred from its content (G13). Every pointer is HYPO-until-checked at use-time (§J PRE-1) — the table is the home (MAY ROT), validity is the grounding above.
```
routing-policy   unit-type → repo (allele)
  lesson | invariant            → SolitaryEquilibriumShield (α_S)   [knowledge units]
  skill  | agent | hook         → neuro-matrix (α_N)               [behaviour units]
  sandbox-mechanism | state     → mirabilis (α_M)                  [mechanism units]
  genome | meta                 → darwin (α_Γ)                     [heredity units]

lane-map         repo → lane
  mirabilis, neuro-matrix       = code-lane        (PR + CI ; CI green-gate BYPASSED this session)
  darwin, shield                = knowledge-lane   (push + storozh ; advisory storozh, ¬gate)
```
The lane-map is pace-layered (R7): the knowledge-lane (Γ, S) is the slow inner layer (push + advisory storozh), the code-lane (M, N) is the faster outer layer (PR + CI). A code-lane churn does NOT force a knowledge-lane change (R7 / G13).

## Channel genes (input R; feed Λ)
```
G-sci   science     α: arxiv-mcp (in env, FACT) + papers   → Λ.{research, evolution}   default ASSOC → FACT on reproduction
G-web   web-search  α: SearXNG (W8, organ M) / WebSearch    → Λ.*                        ASSOC (sourced)
G-code  code/tests  α: repos(M,N) + verification-gate(N) + LSP   → direct FACT channel (¬Λ)
```
Channels materialize access to 𝕌 (§A); their output deduplicates into Λ (except G-code — direct executable fact).

## Ledger
FACT: G-know seed=membackup, G-obs+ seed=obs, G-fleet seed=skills+agents, G-sci=arxiv-mcp (read / in-env); G-route = declarative routing-policy + lane-map (C3), grounded G4+G1+G13+R7 — config-driven, ¬content-inference. HYPO: G-domain (greenfield); G-know beyond sync; G-route φ (misroute-rate) unmeasured until storozh (C4) runs. Q: α_M of G-domain; per-gene φ pre-eval-run; α_S corpus contents (lesson|invariant home in shield, projections.md).
