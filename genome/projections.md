# Projections — two graphs from one genome

The two "graphs" (owner requirement) are **not two disjoint plans but two projections of one genome `𝒢` by organ**. Explicit hard responsibility-split is rejected (contradicts genetics): a gene may be expressed in both organs.

## Projection operator
```
proj_o(𝒢) = ⟨V_o, E_o⟩,   o∈{M,N}
  V_o = { g∈𝒢 : α_o(g) ≠ ⊥ }                vertices = genes expressed in organ o
  E_o = { (g,h,r)∈E : g,h ∈ V_o }            induced edges
```

## Graph-M = proj_M (mechanism / coral)
Vertices: M anatomy (`registry-M`: authproxy, harness, membackup, obs, config, exec, localllm, notify, pipeline, provision, sandbox, secrets, claudeauth, status, steps, hooksM, bus, tui) ⊕ work-item mutations (W1–W8) ⊕ M-invariants (INV-D/E/F) ⊕ M-alleles of the quartet.
Deliverable projection: **plan-code** (`mirabilis-impl-plan.md`, needs repair — CONFLICT W1/[D5], in Vec/`vectors.md`).

## Graph-N = proj_N (behaviour / seahorse)
Vertices: `registry-N` (31 invariants, 5 agents, 5 skills, hooks, eval/R→S, scripts, references) ⊕ candidates INV-A/B/C ⊕ N-alleles of the quartet.
Deliverable projection: **plan** (the R→S audit's dev-vector: close `R→S`, formalize V6/V7).

## Organ coupling (biallelic genes ∈ V_M ∩ V_N)
```
G-harness   install N→M mechanism (M) ⊕ installed behaviour (N)     [primary coupling = wiring: M expresses N into env(M); symmetric peers, ¬life-dependence (§A.6/§F)]
G-rtk       provision (M) ⊕ filter-hook (N)
G-hed       provision (M) ⊕ mode (N)
G-cav       install+flag (M) ⊕ terse skill (N)
G-loc       bridge (M) ⊕ routing-deferred (N)
G-know      membackup (M) ⊕ recall-discipline (N)
G-obs+      obs sink (M) ⊕ feedback-interpretation (N)
G-hook      plugin install (M) ⊕ runtime gate (N)
```
∴ `Σ = M ⊕ N` are coupled not by document links but by **shared genes** (one gene, two alleles) and the **shared ocean** `Γ`/env.

## Independent evolution in the shared ocean (§E)
M, N, Γ evolve on their own clocks, with no shared mutable state. Each one's environment is reality ℛ plus the public interfaces of the others — and nothing more: M sees N's public interface (via G-harness) and Γ; N sees M's interface and Γ; Γ sees both M's and N's interfaces (and so describes both, within the self-description limit of §F). Each must read its own environment or it maladapts.

## Ledger
FACT: projection is a pure operation on 𝒢; biallelic genes confirmed in code (harness/membackup/obs/rtk-hook). ASSOC: "independent clocks" of the repos = target model (§E), not measured current state. Q: exact iface(o) (public contracts) — extract when encoding contracts.
