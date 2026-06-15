# Design principles G0–G12 (sandbox/engineering)

These principles govern engineering decisions in M (sandbox) and, where noted, N.
They are **engineering choices** [eng-choice], not grounded scientific laws — each is tagged accordingly.
Where a §0 root applies it is noted; otherwise the tag is [eng-choice/HYPO].

Source of these definitions: distilled from `/workspace/plan/00-system.md` (superseded) + usage patterns in `dept/graph-plan-sandbox.md`.
The superseded plan is the origin; Darwin (Γ) is the canonical home from this point.

```
G13 map+doctrine¬prose  system-prompt injected into a session = map (pointers to sources, read-on-demand) +
                         doctrine (dense FOL invariants); prose narratives → 0. Single canonical source for
                         any injected taxonomy (config.go); derived text (markdown files, frontmatter) = rot hazard.
                         Grounding: R6 (density = truth; shortest faithful = best model); liu-2023 (irrelevant
                         content in context actively lowers accuracy).
                         [eng-choice; grounded R6 + Λ:liu-2023]

G0  system-over-nodes    reason at the ecosystem goal level (⟨truth, capability, self-sufficiency, evolvability⟩),
                         not at a local metric (tokens, cost, speed); every Δ is justified by mission-reach.
                         grounding: R5 emergence (the whole is different from the nodes; optimising a node ≠ optimising the system).
                         [eng-choice; grounded R5]

G1  no-churn / YAGNI    minimal diff — add only what is needed; duplicate routes to one destination = churn.
                         single source of truth for any value (one home, not two constant blocks).
                         [eng-choice/HYPO — a YAGNI heuristic, not a proven law]

G2  sandbox≠harness     M provisions + exposes a tool/service; behavioural use (when-to, judging, routing) belongs to N.
                         a Δ that decides *when* or *whether* to use a mechanism is mis-placed in M.
                         grounding: the M/N part split (§A GENOME); N is installed into M, not the reverse.
                         [eng-choice; grounded §A ontology]

G3  SRP per package     one package, one responsibility; a new capability = a new package, not a bloated existing one.
                         [eng-choice/HYPO]

G4  config-driven       tunables (URLs, model ids, timeouts, caps) live in config/env, not compile-time constants;
                         swap = a config edit, zero code edit. A hardcoded value is a frozen gene (R4 boundary).
                         grounding: R4 directed evolution (a constant blocks adaptation at that point).
                         [eng-choice; grounded R4]

G5  observability       every subsystem exposes a health signal to a single thread-safe observable state-map;
                         a subsystem whose health is invisible cannot be corrected (R3 boundary).
                         grounding: R3 feedback/correction.
                         [eng-choice; grounded R3]

G6  degrade-not-crash   a node failure degrades that node's function, not the system; panic → StateDegraded,
                         never system halt; every external IO call has a deadline.
                         grounding: R3 feedback/correction (a viable system absorbs disturbance, ¬amplifies it).
                         [eng-choice; grounded R3]

G7  bounded-IO          every IO wait (network, process, user) has a timeout/cancel path; no goroutine sleeps
                         past a context cancellation; no human-input wait blocks automated flow.
                         grounding: G6 + R3.
                         [eng-choice; grounded R3 via G6]

G8  replaceable         a module is a replaceable unit: its concrete impl is hidden behind a single interface;
                         swap = inject a different impl, zero call-site edits.
                         [eng-choice/HYPO — DI/interface discipline, a convention]

G9  least-privilege     each process/module runs with only the permissions necessary for its task;
                         secret material never enters the container or a readable file.
                         grounding: Λ saltzer-1975 (Principle of Least Privilege).
                         [eng-choice; grounded saltzer-1975]

G10 no-dead-code        remove unused paths before they create maintenance surface; a dead route is a liability
                         (two routes to one destination = G1 churn; dead branches confuse future editors).
                         [eng-choice/HYPO]

G11 test-before-delete  characterise behaviour (including warts) before deleting a path; deletion without a
                         characterisation test may delete load-bearing behaviour silently.
                         [eng-choice/HYPO]

G12 panic-degrade       a panic in a subsystem is caught, logged, and the subsystem is demoted to StateDegraded;
                         the outer system continues. Specialisation of G6 for Go panic-recover paths.
                         grounding: R3 feedback/correction.
                         [eng-choice; grounded R3 via G6]
```

## Cross-references

| principle | using files | root / Λ |
|-----------|-------------|----------|
| G0 | dept/graph-plan-harness.md; dept/graph-plan-sandbox.md | R5 |
| G1 | dept/graph-plan-sandbox.md | [eng-choice] |
| G2 | dept/graph-plan-harness.md; dept/graph-plan-sandbox.md; dept/graph-plan-communication.md | §A ontology |
| G3 | dept/graph-plan-sandbox.md | [eng-choice] |
| G4 | dept/graph-plan-sandbox.md; genome/registry-M.md (G-config, G-hed) | R4 |
| G5 | genome/registry-M.md (G-obs); genome/registry-new.md | R3 |
| G6 | dept/graph-plan-sandbox.md | R3 |
| G8 | dept/graph-plan-sandbox.md | [eng-choice] |
| G12 | dept/graph-plan-sandbox.md | R3 via G6 |
| G13 | genome/registry-M.md (G-sandbox sandbox_context V2) | R6 + Λ:liu-2023 |

## Ledger
```
FACT   : G0/G2/G4/G5/G6/G12 grounded in §0 roots or Λ (noted above); G9 grounded Λ:saltzer-1975; G13 grounded R6+Λ:liu-2023.
HYPO   : G1/G3/G8/G10/G11/G13 are conventions without full scientific grounding — engineering choices that have survived use.
Q      : G7/G9/G10/G11 not observed in current file set (defined here for completeness).
source : distilled from /workspace/plan (superseded); Darwin Γ is the canonical home.
```
