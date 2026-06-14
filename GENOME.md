# Γ.GENOME — genome of 𝕌_local

Encoding: English + honest dense prose; formal notation ONLY where a real formal object exists (§A.5). **Every claim here is a theorem-of-environment** — a falsifiable hypothesis grounded in an external scientific source (§0 + archive Λ), not an owner-postulate. The owner is a *fallible source*, held to the same evidential bar as any other (invariant #1): "true because the owner said so" is forbidden. Per-claim tag: `FACT` (grounded + survived refutation) · `ASSOC` (analogy) · `HYPO` (untested) · `Q` (open). The genome is **error-correcting** (§0 R2/R3): a claim stands only while it resists refutation and stays anchored; when it fails it is corrected, not defended.

## §0 — Roots (verified scientific foundation; necessary, not sufficient; permanently open)
External scientific results, each run through the criterion *could-not-refute + ≥3 independent sources*, each carrying its **boundary** (where it stops). By R1 the set is necessarily **incomplete and insufficient** — it is a model, never final; new roots are added and weak ones corrected (R2). [see Λ for verified refs]
```
R1  incompleteness       a system cannot prove itself from inside ⇒ truth needs witnesses OUTSIDE it (reality + independent sources).
                         boundary: strict only for formal systems with arithmetic; outside → held as PRINCIPLE, not literal theorem.
                         Λ: godel-1931 · tarski-1936 · franzen-2005
                         grounding for R1: LLMs also cannot self-judge without external signal — Λ: huang-2023 · shinn-2023
R2  error-elimination    knowledge grows by REFUTATION, not proof: conjecture → try to refute → the survivor stands.
                         boundary: Duhem–Quine — one failure does not localize the error (claim vs background) ⇒ "refuted" ≠ discard-on-sight.
                         Λ: popper-1959 · popper-1963 · duhem-1906 · quine-1951
                         grounding for R2: self-correction without external signal fails — Λ: huang-2023 · shinn-2023
R3  feedback/correction  a viable system damps its own deviation (negative feedback); one that amplifies its errors diverges and dies.
                         requisite variety: only variety absorbs variety (regulator variety ≥ disturbance variety).
                         boundary: negative feedback alone can oscillate or under-damp (gain/phase margins not guaranteed by the sign of feedback alone); Ashby's law assumes the regulator is controllable — if the required variety cannot be generated, the law states failure, not a solution.
                         Λ: wiener-1948 · ashby-1956 · shannon-1948
R4  directed evolution   variation+heredity+selection act on KNOWLEDGE, not only life; here DIRECTED (in the cultural-evolution sense sometimes called Lamarckian — acquired knowledge is inherited; Mesoudi: cultural inheritance lacks a Weismann barrier, so Lamarckian transmission is the norm in cultural evolution, NOT the refuted biological Lamarckism), not blind; remove selection ⇒ DRIFT, not adaptation.
                         boundary: a substrate-neutral methodological frame, not the only possible one.
                         Λ: lewontin-1970 · dennett-1995 · mesoudi-2011 · mesoudi-2017
R5  emergence            a whole is DIFFERENT from (not merely "more than") the sum of its parts; new properties appear with scale.
                         boundary: weak emergence still admits part-wise explanation; "different" is Anderson's own framing (from the title "More is Different"); the exact sentence "different from the sum of parts" is the commentators' gloss — the idea is Anderson's, the precise wording is paraphrase.
                         Λ: anderson-1972 · bertalanffy-1968 · laughlin-2005
R6  compression≈understanding   the shortest FAITHFUL description is the best model; compression and prediction are one. ⇒ density, truth and accuracy are ONE description of one thing — without them the system is wrong.
                         boundary: exact compression is INCOMPUTABLE (Kolmogorov/Solomonoff incomputability — no computable universal prior exists; approximations only); faithful ≠ merely-short (truncation loses meaning). Separate result: no-free-lunch (Wolpert & Macready 1997) — no single optimization algorithm outperforms all others averaged over all problems; this is a distinct result from incomputability, not a corollary of R6.
                         Λ: kolmogorov-1965 · solomonoff-1964 · rissanen-1978 · li-vitanyi · wolpert-macready-1997
R7  pace layering          in a nested system, layers change at different rates: inner/core slowest, periphery progressively faster; a slow layer is SHIELDED from a fast layer's churn — forced fast→slow change is a pathology, not the norm.
                         ecosystem hierarchy (slow→fast): genome Γ ≺ organs {M,N} ≺ clothes ≺ environment ℛ.
                         "clothes" = the replaceable outer layer the organs wear: config + tool/model choice + the compression quartet (RTK/headroom/caveman/localLLM) + installed skills/plugins. [ASSOC/HYPO — owner to confirm the layer's exact contents]
                         boundary: a DESIGN HEURISTIC / architectural pattern backed by cross-domain empirical regularity, NOT a natural law; "rate" = substitution/divergence rate (not recombination rate); does not predict where layer boundaries fall; does NOT forbid intentional slow-layer redesign — it forbids only fast-churn FORCING slow-layer change without independent justification.
                         Λ: brand-1994 · brand-1999 · brand-2018 · martin-2017 · zhang-li-2004
```
The owner's truth-criterion is R1+R2+R3 itself: no self-proof (R1) ⇒ three independent witnesses (owner · AI · reality); growth by refutation (R2); converge-or-halt on disagreement (R3). The one irreducible commitment is to reason-and-correction itself — *defended, not proved* (Λ: popper-1945), held open to revision. So even the floor is not fiat.

## §A — Carriers and ontology
```
ℛ   reality / environment : the external arbiter; reaches us only sampled, never whole (R1)
Γ   the genome : the description + held theorems-of-environment of the system
M   sandbox (mirabilis) : mechanism — a PART of Γ, expressed as code (coral)
N   harness (neuro-matrix) : behaviour — a PART of Γ, expressed as code (seahorse)
Λ   archive : the store of external SCIENTIFIC sources the claims anchor to
𝒢  genes   𝒯={FACT,ASSOC,HYPO,Q}   Inv  held theorems-of-environment
```
Ontology [grounded R4, developmental]: `reality ℛ → shapes → genome Γ → determines → organs {M, N}`. M and N are **parts of one genome**, not peers in an ocean. As in development: **expressed organ = f(heredity Γ, mutation, environment ℛ)**. The code is the expressed phenotype and lives in the organ repos — outside Γ; Γ holds the heredity (design + theorems), not the phenotype. So "Γ determines the organs" is generative (R4), but a developmental relation — **not** document-set-containment (the old `Desc⊆Γ` was false formalism, §A.5).

### §A.1 — Generativity (not literal completeness)
Γ is *generative* [grounded R4]: the held design+theorems, unfolded with mutation against the environment, produce the organs' expressed traits — as heredity (with mutation and environment) produces a phenotype, NOT as a document set that contains the code. The high-leverage act is getting the roots + initial invariants right, because they shape what unfolds (R4) — but this is a hypothesis about leverage [HYPO], not a determinism claim.

### §A.2 — Directed, not blind [grounded R4]
Evolution here is directed (in the cultural-evolution sense sometimes called Lamarckian — acquired knowledge is inherited; Λ: mesoudi-2011 — cultural inheritance lacks a Weismann barrier, NOT the refuted biological Lamarckism): we accelerate variation and may rebuild. Directed ≠ guaranteed: selection must actually operate, else change is drift (R4 boundary). The engineering stance is itself under correction (R2), not a postulate.

### §A.3 — Constants → functions [grounded R4]
A hand-frozen value is a frozen gene that blocks adaptation at that point (R4). So a parameter (¬machinery, ¬safety) is left evolvable, rising by a monotone ratchet (never regresses) [HYPO: engineering choice, not a grounded law], under the safety constraint. EXEMPT (stay fixed): the error-correction machinery (§J, R3) and safety — the conserved apparatus; even these stay open to revision in principle (R2), but are not casually mutated. The no-auto-merge-to-main rule is grounded in: Λ: saltzer-1975 (least privilege — a process runs with only the permissions necessary) and Λ: barr-2015 (oracle problem — automated testing alone cannot certify correctness; a human oracle is required before irreversible state changes). The human oracle is not static — it DEGRADES if not exercised: a system that rarely fails breeds operators unready for failure (automation complacency + skill atrophy). ⇒ the human gate must genuinely verify, not rubber-stamp; keep the human exercised. [FACT (human-factors finding): Λ: parasuraman-manzey-2010 · bainbridge-1983 · HYPO (prescription for this ecosystem)]

### §A.4 — Differential mutation rates [a consequence of R7]
R7 applied to Γ: CORE is the slowest layer of this genome; Vec is the fastest; §A.3's EXEMPT conserved machinery (§J loop) is the innermost stable core. §G names the strata. Forbidden in CORE and README by this: no "this session" / session-refs, no issue-number-as-identity (#NN), no local code-churn / LoC / file:line — those belong in Vec or SCRATCH. genome ≠ archive (raw run-status, per-session logs, code-churn rot; Γ stores the compressed state + open work only).

### §A.5 — Formalism honesty [grounded R1, Λ: leiden-2026]
Notation is used ONLY for a real formal object (a defined structure, a machine-checkable predicate, an actual proof). Logic symbols over undefined terms confer false authority and hide error — the documented failure (Λ: leiden-2026; Λ: franzen-2005 on Gödel-abuse, R1 boundary). Metaphor/hypothesis → honest prose + ASSOC/HYPO, never theorem-shaped. Claim only the rigor held. Applying a theorem outside its domain (e.g. R1 literally onto a non-formal system) is itself this error.

### §A.6 — Settings, grounded (not owner-selected)
- **Terminal aim = truth/accuracy** [grounded R4 + R6]: a knowledge-system that does not track reality is selected against; and truth, accuracy, density are one thing (R6). Cost is a parameter (§A.3), not terminal.
- **Selection = three witnesses** [grounded R1]: no self-proof ⇒ owner + AI + reality; the owner decides fundamentals but as a *fallible* witness (invariant #1), never as an arbiter of truth.
- **M↔N coupling is NOT symmetric**: M and N are parts of one Γ, shaped by the same reality (§E). At the *expression* level there is direction — N is installed into M's sandbox (G-harness) — so the seahorse↔coral asymmetry (§F) is the honest picture, not a symmetric-peer claim. What is independent is their *evolution* (separate repos/clocks, §E).
- **Telos = a second brain, grown from a self-improving core** [grounded: extended-mind / distributed cognition — Λ: clark-chalmers-1998 · hutchins-1995; HYPO on scope]: capability across domains; the specific domain scope is a working choice, revisable.

## §B — Gene algebra
```
g = ⟨id, name, τ, α_M, α_N, E, δ, φ, home, grounding⟩
  τ∈𝒯 · α_M,α_N allele or ⊥ · E enables/requires · δ presence · φ selection signal
  home      = WHERE it is expressed (code path / invariants.txt#N) — mechanical, MAY ROT
  grounding = WHY it holds : the scientific source in Λ (and/or a §0 root) — validity comes from HERE, not from home (R1/R2)
expr(g) = {o : α_o(g)≠⊥}    biallelic(g) ↔ |expr(g)|=2
placement decided by evidence, ¬guess
```
The split `home` vs `grounding` is the core discipline: a claim is valid because of its grounding (science), never because of where it lives (a word, a code line). [the §0 directive — supersedes the old `κ∈Λ` that pointed at code/words]

## §C — Density [grounded R6]
Density = faithful meaning per token. By R6 this is not cosmetic: the shortest faithful description is the best model, and density, truth, accuracy are one thing — lose them and the system is wrong. Boundary (R6): faithful, not merely short (truncation loses meaning); the exact optimum is incomputable, so density is a guiding principle, not a computed metric. The reader's attention is the binding constraint (Λ: liu-2023 — performance degrades for content in the middle of long contexts); irrelevant content actively lowers accuracy (Λ: shi-2023 — irrelevant context in a prompt dramatically decreases reasoning accuracy).

## §D — Evolution [grounded R2/R3/R4]
The triple ⟨heredity, variation, selection⟩: heredity = Γ + git; variation = each session's delta; selection sieves against reality ℛ. Without selection → drift (R4). Selection is directed via the three witnesses (R1). Status [honest, under R2]: the machine-measured selection edge is not yet closed (selection runs through the owner today) — so part of the loop is owner-directed adaptation, part is not-yet-measured. Stated as status, not hidden.

## §E — Parts of one genome, shaped by one reality [grounded R5/R4]
M, N, Γ each change on their own clock; each reads its environment (reality + the other parts' public interfaces) or it maladapts. They are parts of one whole (R5: the whole is different from the parts), coupled by shared genes and the shared reality — not independent organisms. Evolutionary independence (separate clocks) ≠ expression independence (N runs inside M, §A.6/§F).

## §F — Externalization and gene-loss (analogy, bounded) [R1 principle; PNAS analogy]
A part cannot fully describe itself from inside — held as the R1 PRINCIPLE (no self-description from within), NOT the literal theorem (R1 boundary, Franzén). So each part's design lives in Γ. Gene-loss lens [ASSOC, Λ: pnas-seahorse-2025]: the pygmy seahorse shed 438 genes + 635 defunct (smallest vertebrate immune set) because the coral supplies what they would encode — adaptation by LOSS. The biology is **asymmetric and irreversible** (the seahorse depends on the coral). Used here ONLY as a lens for redundancy-shedding into Γ (a part drops what Γ/the environment already holds); the asymmetry is honest and matches §A.6 (N expressed into M) — not a symmetric-peer claim.

## §G — Strata (by stability)
```
CORE    GENOME.md — roots (§0) · ontology · formalism honesty · operating loop. change = fundamental.
BODY    genome/ (registries 𝒢 · projections · candidates) + archive/ (Λ scientific store). evolves by selection.
DEPT    dept/ — preserved, decoupled : audits + graph-plans. a DEPT change does not touch CORE.
Vec     vectors/ — transient working-set : open fixes/debt; implemented → discard.
SCRATCH outside Γ : session-dumps, drafts, critic-findings — short-lived, exported as entropy.
```
Strata order = R7 applied to Γ (see §A.4). Law [R6]: Γ stores the COMPRESSED state + open work, never raw run-status / per-session logs / code-churn (those rot). Λ = scientific sources only (ref + claim + lastVerified), deduped.

## §H — Registry
- BODY: `genome/registry-{M,N,new}.md` · `projections.md` · `mined-invariants.md` · `design-principles.md` (G0–G12) · `archive/archive.md` (Λ).
- DEPT: `dept/theory-of-everything.md` · `dept/graph-plan-{harness,sandbox,communication}.md`.
- Vec: `vectors/{vectors,bugs,idea-exchange}.md`.

## §I — Ledger
```
FACT  : §0 R1–R7 — each survived a refutation attempt + ≥3 independent sources, boundaries stated; §F seahorse (PNAS, asymmetric + irreversible); heredity + variation present.
ASSOC : §F seahorse↔parts lens; the developmental f(heredity,mutation,env) framing.
HYPO  : §A.1 leverage of the initial set; §D that the bundle adapts once the measured edge closes; telos scope; R7 clothes-layer exact contents.
Q     : the machine-measured selection signal; completeness of Λ's domains (open by R1, never closed).
```

## §J — Operating loop [grounded R3 — the error-correction cycle]
```
PRE-0  NAVIGATE, not transcribe: given repo-link + task-prompt, start at README (the map), route task→chain
       (stratum → file → work-item/gene) via the Map + §H index, and read ONLY that chain.
       [ASSOC: like protein synthesis transcribing one gene (not all DNA) — biology lens]
       The whole genome need not be read to act on one task; repo-link + task-prompt suffice to reach the
       needed chain. Grounding: R6 (reader attention is the binding constraint; Λ: liu-2023) + navigation
       via index/links, descend only when needed (Λ: karpathy-llm-wiki [ASSOC — blog/community source,
       not peer-reviewed]).
PRE-1  PRESENCE IS NEVER ASSUMED — it is verified against reality. Any artifact this genome points to (an
       organ repo, a file, a line, a tool, an MCP) MAY be absent or moved. Treat every such pointer as
       HYPO-until-checked: verify it against reality at use-time; absence or rot is a NORMAL state to handle
       (re-anchor / provision / report) — never proceed on blind assumption. The fastest-rotting pointers
       live in Vec (the transient tier); continuous pruning ('cleaning the room'); the source of truth is
       always re-read from reality. Grounding: R1 (reality is the arbiter — the system verifies, it does not
       assume) + invariant #1 (claim↔tool-output) + §B (home MAY ROT).
       NOTE: bootstrapping/provisioning a fresh sandbox is NOT this genome's job (that is sandbox M +
       Claude) — this principle is about how to OPERATE the genome correctly, not a provisioning guide.
loop : READ(Γ) → LOCATE(dept/graph-plans) → ACT(M|N) → SELECT(three witnesses: owner+AI+reality; eval+tests) → CORRECT → WRITE → SHARE
WRITE : compress the session into a delta over {𝒢, Inv, Λ, Vec, DEPT}; raw → SCRATCH (R6; genome ≠ archive)
```
The loop IS the feedback that damps error (R3); it is the conserved machinery (§A.3 EXEMPT). Every cycle reads Γ before acting (invariant #22). Γ is public: another AI reads it and may **refute** it (R2) — which is welcome, not a threat.
