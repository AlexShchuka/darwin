# Projections — two graphs from one genome

The two "graphs" (owner requirement) are **not two disjoint plans but two projections of one genome `𝒢` by organ**. Explicit hard responsibility-split is rejected (contradicts genetics): a gene may be expressed in both organs.

## Projection operator
```
proj_o(𝒢) = ⟨V_o, E_o⟩,   o∈{M,N,S}
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

## Ecosystem-graph (5 nodes) [FACT where checked; HYPO where open]
The guild ecosystem has five identified nodes. Γ models the CODE organs (M, N) plus the
knowledge organ Shield (S) as its carriers; only the environment ℛ is external. The shield is
an organ of the genome (allele `α_S`), **not** a mere external witness — owner decision (locked):
```
darwin (Γ)               github.com/AlexShchuka/darwin
                         role: genome — holds the heredity (design+theorems); this repo. self-allele α_Γ.
mirabilis (M)            github.com/AlexShchuka/mirabilis
                         role: sandbox / mechanism / coral — the expressed organ (code); allele α_M; FACT
neuro-matrix (N)         github.com/AlexShchuka/neuro-matrix
                         role: harness / behaviour / seahorse — the expressed organ (code); allele α_N; FACT
SolitaryEquilibriumShield (S)  github.com/AlexShchuka/SolitaryEquilibriumShield
                         role: knowledge organ — the owner's math+learning repo + lesson/invariant
                         corpus; allele α_S. consumes neuro-matrix invariants (PROVENANCE.md: verbatim
                         import). PROMOTED from external R1-witness to a Γ-organ — owner ontology
                         decision (locked): shield IS a genome organ (α_S). The R1-witness reading is
                         superseded; the asymmetry note is kept honest in the edges below.
```
The §B projection operator now ranges over `o∈{M,N,S}` (CORE-backed: GENOME.md §A ontology + §B
expr operator admit S as the 3rd Γ-organ, owner decision locked). S is the knowledge organ whose
allele `α_S` carries lesson/invariant units (it does not run code into M, so it is not a peer of the
M/N expression coupling — §A.6/§F asymmetry). proj_S is therefore a well-formed projection of `𝒢`;
S's allele α_S is already used by G-route (registry-new.md) so its edges are not dangling (G1 density).
Cross-edges:
  shield → neuro-matrix   FACT (invariants import, PROVENANCE.md)
  darwin ↔ M              FACT (Γ determines organ M; §A ontology)
  darwin ↔ N              FACT (Γ determines organ N; §A ontology)
  darwin ↔ shield (S)     PRESENT [owner decision, locked: shield IS a Γ-organ (α_S); Γ now describes S
                          as the home of lesson|invariant units — see G-route, registry-new.md].
                          Direction note (honest, §F): the git-level reference shield→darwin is still
                          ABSENT in shield's tracked files (was [FACT: zero darwin references, 2026-06-23]);
                          the edge holds at the ONTOLOGY level (Γ names S as organ), not yet as a code link.
Edge-should-exist: RESOLVED — owner decided the edge exists (shield IS an organ, α_S).

## Ledger
FACT: projection is a pure operation on 𝒢; biallelic genes confirmed in code (harness/membackup/obs/rtk-hook); ecosystem 5-node listing FACT where repo-URLs confirmed; cross-edges (shield→neuro-matrix) FACT from PROVENANCE.md (verified 2026-06-23 audit); darwin↔shield edge PRESENT by owner decision (locked: shield IS a Γ-organ, allele α_S); the §B operator now ranges over {M,N,S} (CORE-backed, GENOME.md §A/§B). ASSOC: "independent clocks" of the repos = target model (§E), not measured current state. HYPO: proj_S (a shield projection) well-formed but not yet populated — α_S so far carried only by G-route (registry-new.md). Q: exact iface(o) (public contracts) — extract when encoding contracts; the git-level shield→darwin reference is still absent (edge holds at ontology, not yet code).
