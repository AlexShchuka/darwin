# Projections — two graphs from one genome

The two "graphs" (owner requirement) are **not two disjoint plans but two projections of one genome `𝒢` by organ**. Explicit hard responsibility-split is rejected (contradicts genetics): a gene may be expressed in both organs.

## Projection operator
```
proj_o(𝒢) = ⟨V_o, E_o⟩,   o∈{M,N}
  V_o = { g∈𝒢 : α_o(g) ≠ ⊥ }                vertices = genes expressed in organ o
  E_o = { (g,h,r)∈E : g,h ∈ V_o }            induced edges
```

## Graph-M = proj_M (mechanism / coral)
Vertices: M anatomy (`registry-M`: authproxy, harness, membackup, obs, config, exec, localllm, loadout, notify, pipeline, provision, sandbox, secrets, claudeauth, status, steps, hooksM, bus, tui, serve) ⊕ work-item mutations (W1–W7 landed; W-arch-C landed PR#135; W-post-arch landed PRs #150/#151/#152; W8/W9/W10 open) ⊕ M-invariants (INV-D/E/F/I3) ⊕ M-alleles of the quartet.
Deliverable projection: **landed code** — W1–W7 + W-arch-C + W-post-arch expressed as genes (PRs #135/#150/#151/#152 merged to main, HEAD 5e9d33b); open: W8/W9/W10. [FACT for all landed items as of 2026-06-23]

## Graph-N = proj_N (behaviour / seahorse)
Vertices: `registry-N` (31 invariants, 5 agents, 5 skills, hooks, eval/R→S, scripts, references) ⊕ candidates INV-A/B/C ⊕ N-alleles of the quartet.
Deliverable projection: **plan** (the R→S audit's dev-vector: close `R→S`, formalize V6/V7).

## Organ coupling (biallelic genes ∈ V_M ∩ V_N)
```
G-harness   install N→M mechanism (M) ⊕ installed behaviour (N)     [primary coupling = wiring: N is installed INTO M (asymmetric at expression; §A.6/§F); evolution-clocks are independent (§E), not expression]
G-rtk       provision (M) ⊕ filter-hook (N)
G-hed       provision (M) ⊕ mode (N)
G-cav       install+flag (M) ⊕ terse skill (N)
G-loc       bridge (M) ⊕ routing-deferred (N)
G-know      membackup (M) ⊕ recall-discipline (N)
G-obs+      obs sink (M) ⊕ feedback-interpretation (N)
G-hook      plugin install (M) ⊕ runtime gate (N)
```
∴ `Σ = M ⊕ N` are coupled not by document links but by **shared genes** (one gene, two alleles) and the **shared environment** `ℛ` / genome `Γ`.

## Independent evolution in the shared environment ℛ / genome Γ (§E)
M, N, Γ evolve on their own clocks, with no shared mutable state. Each one's environment is reality ℛ plus the public interfaces of the others — and nothing more: M sees N's public interface (via G-harness) and Γ; N sees M's interface and Γ; Γ sees both M's and N's interfaces (and so describes both, within the self-description limit of §F). Each must read its own environment or it maladapts.

## Ecosystem-graph (4 repos) [FACT where checked; HYPO where open]
The guild ecosystem currently has four identified nodes; Γ models the two CODE organs (M, N) as its carriers; the other two are external but named here per G1 density (¬dangling nodes in the shared environment):
```
darwin (Γ)               github.com/AlexShchuka/darwin
                         role: genome — holds the heredity (design+theorems); this repo
mirabilis (M)            github.com/AlexShchuka/mirabilis
                         role: sandbox / mechanism / coral — the expressed organ (code); FACT
neuro-matrix (N)         github.com/AlexShchuka/neuro-matrix
                         role: harness / behaviour / seahorse — the expressed organ (code); FACT
SolitaryEquilibriumShield  github.com/AlexShchuka/SolitaryEquilibriumShield
                         role: owner / RL self-model — the owner's private math+learning repo;
                         consumes neuro-matrix invariants (PROVENANCE.md: verbatim import);
                         does NOT reference darwin or M; sits OUTSIDE Γ's organ-set {M,N};
                         whether it belongs as a Γ-organ or as the R1 owner-witness layer
                         is an owner ontology decision — recorded here as OPEN [HYPO]
```
Cross-edges confirmed:
  shield → neuro-matrix   FACT (invariants import, PROVENANCE.md)
  darwin ↔ M              FACT (Γ determines organ M; §A ontology)
  darwin ↔ N              FACT (Γ determines organ N; §A ontology)
  shield → darwin         ABSENT [FACT: zero darwin references in shield tracked files, 2026-06-23]
  darwin → shield         ABSENT [FACT: shield not named as organ in GENOME.md §A carriers]
Edge-should-exist: OPEN [HYPO] — owner to decide

## Ledger
FACT: projection is a pure operation on 𝒢; biallelic genes confirmed in code (harness/membackup/obs/rtk-hook); ecosystem 4-node listing FACT where repo-URLs confirmed; cross-edges (shield→neuro-matrix) FACT from PROVENANCE.md (verified 2026-06-23 audit). ASSOC: "independent clocks" of the repos = target model (§E), not measured current state. HYPO: SolitaryEquilibriumShield ontological placement (organ vs R1-witness), shield↔darwin edge. Q: exact iface(o) (public contracts) — extract when encoding contracts.
