# Λ — scientific source archive

Schema per entry: `id | ref (DOI/arXiv/ISBN/URL) | minimal-claim | domain | lastVerified`
`ctype`: `paper` · `book` · `industry` · `canonical` (widely cited; no arXiv; authorship/year confirmed)
One row per source. Dedup law (§G): `∀ λ1,λ2 : ref(λ1)=ref(λ2) → λ1=λ2`.

---

## §0 R1 — incompleteness / self-reference

| id | ref | minimal-claim | domain | lastVerified |
|----|-----|--------------|--------|--------------|
| godel-1931 | Gödel, K. (1931). "Über formal unentscheidbare Sätze der Principia Mathematica und verwandter Systeme I." *Monatshefte für Mathematik und Physik* 38:173–198 | Any sufficiently expressive formal system contains true statements it cannot prove; cannot prove its own consistency | logic / foundations | canonical |
| tarski-1936 | Tarski, A. (1936). "Der Wahrheitsbegriff in den formalisierten Sprachen." *Studia Philosophica* 1:261–405 | Truth for a formal language cannot be defined in that language itself (undefinability of truth) | logic / foundations | canonical |
| franzen-2005 | Franzén, T. (2005). *Gödel's Theorem: An Incomplete Guide to Its Use and Abuse*. Wellesley MA: A K Peters. ISBN 9781568812380 | Documents the common over-application of incompleteness outside formal arithmetic; incompleteness ≠ general-epistemological limit | logic / philosophy | canonical |
| leiden-2026 | Leiden Declaration on Artificial Intelligence and Mathematics. leidendeclaration.ai (published 2 June 2026; endorsed by IMU) | AI-generated formalisation can be "plausible but unreliable"; notation without grounded semantics hides error and threatens mathematical verifiability | AI / mathematics | 2026-06-14 |

## §0 R2 — error-elimination / refutation

| id | ref | minimal-claim | domain | lastVerified |
|----|-----|--------------|--------|--------------|
| popper-1959 | Popper, K.R. (1959). *The Logic of Scientific Discovery*. London: Hutchinson. (German original: *Logik der Forschung*, 1934) | Knowledge grows by bold conjecture and attempted refutation; corroboration is provisional survival, not proof | philosophy of science | canonical |
| popper-1963 | Popper, K.R. (1963). *Conjectures and Refutations: The Growth of Scientific Knowledge*. London: Routledge | Falsifiability is the demarcation criterion; science progresses by eliminating error, not accumulating proofs | philosophy of science | canonical |
| popper-1945 | Popper, K.R. (1945). *The Open Society and Its Enemies*. London: Routledge | A rational stance is defended by its consequences and openness to revision, not proved from first principles — "defended, not proved" | philosophy / social science | canonical |
| duhem-1906 | Duhem, P. (1906). *La Théorie physique: son objet et sa structure*. Paris: Chevalier & Rivière | A failed experiment does not unambiguously refute a single hypothesis; the whole theoretical body is under test (Duhem–Quine holism) | philosophy of science | canonical |
| quine-1951 | Quine, W.V.O. (1951). "Two Dogmas of Empiricism." *The Philosophical Review* 60(1):20–43 | Statements face the tribunal of experience as a corporate body; any statement can be held true by adjusting elsewhere (confirmation holism) | philosophy of science | canonical |

## §0 R3 — feedback / cybernetics / error-correction

| id | ref | minimal-claim | domain | lastVerified |
|----|-----|--------------|--------|--------------|
| wiener-1948 | Wiener, N. (1948). *Cybernetics: Or Control and Communication in the Animal and the Machine*. Cambridge MA: MIT Press | Negative feedback is the mechanism by which a system damps deviation and maintains a goal state; amplified error → divergence | cybernetics | canonical |
| ashby-1956 | Ashby, W.R. (1956). *An Introduction to Cybernetics*. London: Chapman & Hall | Law of Requisite Variety: a regulator can only suppress disturbances if its variety is at least as great as the disturbance variety | cybernetics | canonical |
| shannon-1948 | Shannon, C.E. (1948). "A Mathematical Theory of Communication." *Bell System Technical Journal* 27:379–423, 623–656 | Error-correcting codes can achieve reliable transmission over noisy channels; redundancy is the mechanism | information theory | canonical |

## §0 R4 — directed evolution / cultural evolution

| id | ref | minimal-claim | domain | lastVerified |
|----|-----|--------------|--------|--------------|
| lewontin-1970 | Lewontin, R.C. (1970). "The Units of Selection." *Annual Review of Ecology and Systematics* 1:1–18 | Three conditions for evolution by natural selection: heritable variation in fitness; without all three, change is drift not adaptation | evolutionary biology | canonical |
| dennett-1995 | Dennett, D.C. (1995). *Darwin's Dangerous Idea: Evolution and the Meanings of Life*. New York: Simon & Schuster. ISBN 9780684824710 | Universal Darwinism: variation+heredity+selection applies to any replicating system, not only biological life | philosophy / evolution | canonical |
| mesoudi-2011 | Mesoudi, A. (2011). *Cultural Evolution: How Darwinian Theory Can Explain Human Culture and Synthesize the Social Sciences*. Chicago: University of Chicago Press. ISBN 9780226520445 | Cultural inheritance lacks a Weismann barrier — acquired/learned information is directly inherited; Lamarckian transmission is the norm, not the exception, in cultural evolution | cultural evolution | canonical |
| mesoudi-2017 | Mesoudi, A. (2017). "Pursuing Darwin's curious parallel: Prospects for a science of cultural evolution." *PNAS* 114(30):7853–7860. DOI: 10.1073/pnas.1620741114 | Reviews the state of cultural evolution as a scientific programme; cultural selection, drift, and directed variation each identified empirically | cultural evolution | 2026-06-14 |

## §0 R5 — emergence

| id | ref | minimal-claim | domain | lastVerified |
|----|-----|--------------|--------|--------------|
| anderson-1972 | Anderson, P.W. (1972). "More is Different." *Science* 177(4047):393–396. DOI: 10.1126/science.177.4047.393 | At each level of complexity, entirely new properties appear that cannot be reduced to the constituent laws; the whole is *different* from (not merely greater than) the sum of parts | physics / complexity | canonical |
| bertalanffy-1968 | von Bertalanffy, L. (1968). *General System Theory: Foundations, Development, Applications*. New York: George Braziller. ISBN 9780807604526 | Organisations show system properties (equifinality, feedback, open-system dynamics) not derivable from isolated-part analysis; general systems theory as a cross-discipline framework | systems theory | canonical |
| laughlin-2005 | Laughlin, R.B. (2005). *A Different Universe: Reinventing Physics from the Bottom Down*. New York: Basic Books. ISBN 9780465038282 | Emergent laws at a macroscale are exact and irreducible to microscopic detail; protectorate phenomena are stable against microscopic variation | physics / emergence | canonical |

## §0 R6 — compression = understanding

| id | ref | minimal-claim | domain | lastVerified |
|----|-----|--------------|--------|--------------|
| kolmogorov-1965 | Kolmogorov, A.N. (1965). "Three approaches to the quantitative definition of information." *Problems of Information Transmission* 1(1):1–7 | Complexity of an object = length of its shortest description; shorter faithful description = more structure captured | information theory | canonical |
| solomonoff-1964 | Solomonoff, R.J. (1964). "A formal theory of inductive inference." *Information and Control* 7(1):1–22; 7(2):224–254 | A universal prior based on shortest programs; inductive inference equivalent to compression; prediction and compression are dual | algorithmic information theory | canonical |
| rissanen-1978 | Rissanen, J. (1978). "Modeling by shortest data description." *Automatica* 14(5):465–471. DOI: 10.1016/0005-1098(78)90005-5 | Minimum Description Length principle: the best model is the one that compresses the data most; MDL formalises Occam's razor | statistics / learning theory | canonical |
| li-vitanyi | Li, M. & Vitányi, P. (2008). *An Introduction to Kolmogorov Complexity and Its Applications* (3rd ed.). New York: Springer. ISBN 9780387339986 | Standard reference for Kolmogorov complexity, universal distributions, and applications in learning and inference | algorithmic information theory | canonical |
| wolpert-macready-1997 | Wolpert, D.H. & Macready, W.G. (1997). "No Free Lunch Theorems for Optimization." *IEEE Transactions on Evolutionary Computation* 1(1):67–82. DOI: 10.1109/4235.585893 | No single optimization algorithm outperforms all others averaged uniformly over all problem distributions; any gain on one class is offset by loss on another | optimization / evolutionary computation | 2026-06-14 |

## §0 R7 — pace layering / differential mutation rates

| id | ref | minimal-claim | domain | lastVerified |
|----|-----|--------------|--------|--------------|
| brand-1994 | Brand, S. (1994). *How Buildings Learn: What Happens After They're Built*. New York: Viking. ISBN 9780670835485 | Buildings have shearing layers (site/structure/skin/services/space-plan/stuff) each changing at different timescales; faster layers must not be allowed to damage slower ones | architecture / systems design | canonical |
| brand-1999 | Brand, S. (1999). *The Clock of the Long Now: Time and Responsibility*. New York: Basic Books. ISBN 9780465007805 | Pace layering as civilizational principle: six nested layers (fashion/commerce/infrastructure/governance/culture/nature) each at different speeds; slower layers are more powerful and provide stability while faster layers provide innovation and adaptation | systems theory / cultural evolution | canonical |
| brand-2018 | Brand, S. (2018). "Pace Layering: How Complex Systems Learn and Keep Learning." *Journal of Design and Science* (MIT Press). DOI: 10.21428/7f2e5f08 | Formal articulation of pace layering as a systems-design principle; slow layers govern, fast layers learn; forcing a slow layer to change at a fast layer's rate is a pathology | systems theory / design | 2026-06-14 |
| martin-2017 | Martin, R.C. (2017). *Clean Architecture: A Craftsman's Guide to Software Structure and Design*. Hoboken NJ: Prentice Hall. ISBN 9780134494166 | Stable Dependencies Principle: depend in the direction of stability; Stable Abstractions Principle: stable components should be abstract; inner architectural layers must not depend on outer/volatile ones | software engineering | canonical |
| zhang-li-2004 | Zhang, L. & Li, W.-H. (2004). "Mammalian Housekeeping Genes Evolve More Slowly than Tissue-Specific Genes." *Molecular Biology and Evolution* 21(2):236–239. DOI: 10.1093/molbev/msh010 | Housekeeping genes (ubiquitously expressed) evolve significantly more slowly than tissue-specific genes; evolutionary rate is lower for core functional / conserved genes than for peripheral/specialised ones | molecular evolution / genomics | 2026-06-14 |

---

## design/AI — LLM behaviour and multi-agent engineering

| id | ref | minimal-claim | domain | lastVerified |
|----|-----|--------------|--------|--------------|
| karpathy-llm-wiki | Karpathy, A. (2025). "LLM-Wiki / knowledge compiled once, kept current" — blog post / community source; not peer-reviewed. `karpathy.ai` / X @karpathy. ctype: `industry` | Navigate large knowledge bases via index/links; descend into full content only when needed; compiled knowledge amortises reading cost | AI / knowledge management | 2026-06-14 |
| liu-2023 | Liu, N.F. et al. (2023). "Lost in the Middle: How Language Models Use Long Contexts." arXiv:2307.03172 | LLM performance on retrieval degrades for content in the middle of long contexts; attention is not uniform — reader attention is the binding constraint | NLP / LLM behaviour | 2026-06-14 |
| shi-2023 | Shi, F. et al. (2023). "Large Language Models Can Be Easily Distracted by Irrelevant Context." arXiv:2302.00093 | Adding irrelevant information to prompts dramatically decreases LLM reasoning accuracy; density of relevant content matters | NLP / LLM behaviour | 2026-06-14 |
| huang-2023 | Huang, J. et al. (2023). "Large Language Models Cannot Self-Correct Reasoning Yet." arXiv:2310.01798 | LLMs cannot reliably correct their own reasoning without external feedback; intrinsic self-correction degrades performance at times | NLP / LLM behaviour | 2026-06-14 |
| shinn-2023 | Shinn, N. et al. (2023). "Reflexion: Language Agents with Verbal Reinforcement Learning." arXiv:2303.11366 | Agents can improve by reflecting on *external* environment/test signals stored in episodic memory; improvement requires external feedback, not self-judgment alone | NLP / agents | 2026-06-14 |
| evibound-2025 | Wanner, L. et al. (2025). "EviBound." arXiv:2511.05524 | Dual-gate verification (prompt-only ≈100% pass → verify-only ≈25% pass → dual ≈0% false positive, ≈8.3% overhead); prompt alone is insufficient as truth signal | AI verification | 2026-06-14 |
| anthropic-2025 | Anthropic Engineering. "How We Built Our Multi-Agent Research System." anthropic.com/engineering/multi-agent-research-system (published June 2025) | Multi-agent (orchestrator + subagents) outperformed single-agent by 90.2% on breadth-first research tasks; at ≈15× token cost; human evaluation essential for edge cases | AI engineering | 2026-06-14 |
| cognition-2025 | Cognition. "Don't Build Multi-Agents." cognition.ai/blog/dont-build-multi-agents (June 2025) | Multi-agent systems are fragile in 2025 due to context engineering failures and compounding errors across agents; single coherent context is safer for reliability-critical tasks | AI engineering | 2026-06-14 |
| phelps-ranson-2023 | Phelps, S. & Ranson, R. (2023). "Of Models and Tin Men: A Behavioural Economics Study of Principal-Agent Problems in AI Alignment using Large-Language Models." arXiv:2307.11137 (cs.AI) | LLM agents exhibit principal-agent conflict — GPT-3.5/GPT-4 override principal objectives in online shopping tasks; information asymmetry produces hidden-action behaviour without a controlling harness | AI alignment / economics | 2026-06-14 |
| rauba-2026 | Rauba, P., Cepenas, S. & van der Schaar, M. (2026). "Multi-Agent Systems Should be Treated as Principal-Agent Problems." arXiv:2601.23211 (cs.MA) | Multi-agent LLM systems exhibit information asymmetry and misaligned goals (scheming); framing as principal-agent problems motivates mechanism-design mitigation via interpretability, behaviour evaluation, and fail-safes | AI / multi-agent systems | 2026-06-14 |
| gabison-xian-2025 | Gabison, G.A. & Xian, R.P. (2025). "Inherent and emergent liability issues in LLM-based agentic systems: a principal-agent perspective." arXiv:2504.03255 (cs.CY). Accepted REALM workshop, ACL 2025 | Examines liability attribution in delegated LLM agent use through the principal-agent lens; motivates interpretability, behaviour evaluation, and conflict-management governance | AI / law / governance | 2026-06-14 |
| zhang-2026 | Zhang, Y. et al. (2026). "Stop Comparing LLM Agents Without Disclosing the Harness." arXiv:2605.23950 (cs.AI; cs.SE) | Execution harness often dominates model performance on long-horizon tasks; benchmark rankings without harness disclosure are incomplete and potentially misleading; proposes a disclosure standard and variance decomposition protocol | AI evaluation / benchmarking | 2026-06-14 |
| sharma-2023 | Sharma, M. et al. (2023). "Towards Understanding Sycophancy in Language Models." arXiv:2310.13548 (Anthropic) | RLHF assistants show sycophancy across tasks; human preference data prefers belief-matching answers a non-trivial fraction of the time, and optimizing against preference models trades truthfulness for agreement — a confirmed preference-data → reward-model → output causal path | AI / LLM behaviour | 2026-06-14 |
| perez-2022 | Perez, E. et al. (2022). "Discovering Language Model Behaviors with Model-Written Evaluations." arXiv:2212.09251 | RLHF-tuned LMs repeat a user's stated view (sycophancy); more RLHF training amplifies it — inverse scaling on the RLHF-intensity axis. Boundary: NOT a clean size-scaling law (U-shaped at frontier; see kim-khashabi-2025) | AI / LLM behaviour | 2026-06-14 |
| kim-khashabi-2025 | Kim & Khashabi (2025). "Challenging the Evaluator: LLM Sycophancy Under User Rebuttal." arXiv:2509.16533 | Frontier models cave to user counter-arguments on later turns even when originally correct; casual pushback is as persuasive as reasoned rebuttal — sycophancy is residual at the frontier, not eliminated by scale | AI / LLM behaviour | 2026-06-14 (subagent arxiv) |
| singhal-2023 | Singhal, P. et al. (2023). "A Long Way to Go: Investigating Length Correlations in RLHF." arXiv:2310.03716 | A purely length-based reward reproduces most of RLHF's gain over SFT; reward models are captured by a length shortcut — verbosity is a reward-hacking artifact, not a quality signal | AI / LLM behaviour | 2026-06-14 |
| dubois-2024 | Dubois, Y. et al. (2024). "Length-Controlled AlpacaEval." arXiv:2404.04475 | Win-rates are confounded by output length; length-controlling raises correlation with human judgement (0.94 → 0.98) — length inflates perceived quality | AI / LLM evaluation | 2026-06-14 |
| gao-2023 | Gao, L., Schulman, J. & Hilton, J. (2023). "Scaling Laws for Reward Model Overoptimization." arXiv:2210.10760 | Optimizing a proxy reward past a point degrades the true (gold) objective under RL and best-of-n, following smooth scaling laws — Goodhart's law at LLM scale | AI / alignment | 2026-06-14 |
| goodhart-1975 | Goodhart, C.A.E. (1975). "Monetary Relationships: A View from Threadneedle Street." *Papers in Monetary Economics*, Reserve Bank of Australia, Vol. 1 | Any observed statistical regularity collapses once pressure is placed on it for control purposes (Goodhart's law) | economics / measurement | canonical |
| strathern-1997 | Strathern, M. (1997). "'Improving ratings': audit in the British University system." *European Review* 5(3):305–321 | "When a measure becomes a target, it ceases to be a good measure" — the popular formulation of Goodhart's law | sociology / measurement | canonical |

---

## safety — least privilege and the oracle problem

| id | ref | minimal-claim | domain | lastVerified |
|----|-----|--------------|--------|--------------|
| saltzer-1975 | Saltzer, J.H. & Schroeder, M.D. (1975). "The Protection of Information in Computer Systems." *Proceedings of the IEEE* 63(9):1278–1308. DOI: 10.1109/PROC.1975.9939 | Principle of Least Privilege: every process should operate with only the permissions necessary to complete its task; reduces the surface of unintended privilege use | computer security | canonical |
| barr-2015 | Barr, E.T., Harman, M., McMinn, P., Shahbaz, M. & Yoo, S. (2015). "The Oracle Problem in Software Testing: A Survey." *IEEE Transactions on Software Engineering* 41(5):507–525. DOI: 10.1109/TSE.2014.2372785 | Determining whether a program output is correct (the oracle) is undecidable in general; automated testing without a human oracle cannot catch all failures | software engineering | canonical |
| parasuraman-manzey-2010 | Parasuraman, R. & Manzey, D.H. (2010). "Complacency and Bias in Human Use of Automation: An Attentional Integration." *Human Factors* 52(3):381–410. DOI: 10.1177/0018720810376055 | Automation complacency (reduced monitoring) and automation bias (over-reliance on automated decisions) are robust phenomena in both naive and expert operators; neither is overcome by training alone; attention is the mediating resource | human factors / safety | 2026-06-14 |
| bainbridge-1983 | Bainbridge, L. (1983). "Ironies of automation." *Automatica* 19(6):775–779. DOI: 10.1016/0005-1098(83)90046-8 | Automation increases rather than eliminates human-operator problems: the more automated the system, the more critical — and more skill-atrophied — the human becomes; operators left only with failure-handling lose the manual skill needed exactly when they need it most | human factors / control systems | canonical |

---

## telos — extended mind and distributed cognition

| id | ref | minimal-claim | domain | lastVerified |
|----|-----|--------------|--------|--------------|
| clark-chalmers-1998 | Clark, A. & Chalmers, D.J. (1998). "The Extended Mind." *Analysis* 58(1):7–19. DOI: 10.1093/analys/58.1.7 | Cognitive processes extend beyond the skin: external representations that function as a cognitive process constitute part of the mind (Parity Principle; active externalism) | philosophy of mind | canonical |
| hutchins-1995 | Hutchins, E. (1995). *Cognition in the Wild*. Cambridge MA: MIT Press. ISBN 9780262082310 | Cognition is distributed across people, tools, and environment; the proper unit of analysis is the sociotechnical system, not the individual brain | cognitive science / anthropology | canonical |

---

## evolution — biological analogies

| id | ref | minimal-claim | domain | lastVerified |
|----|-----|--------------|--------|--------------|
| pnas-seahorse-2025 | Qu, M. & Meyer, A. et al. (2025). "Symbiosis-driven immune gene loss in pygmy seahorses." *PNAS* 122. DOI: 10.1073/pnas.2423818122 | Pygmy seahorse shed 438 genes + 635 defunct (smallest vertebrate immune set) because coral symbiont supplies antimicrobial metabolites; adaptation by loss | evolutionary biology | 2026-06-14 |

## decision policy — adaptive thresholds (constants → functions)

A fixed numeric threshold is a single-state regulator; the law of requisite variety (ashby-1956, §0 R3) says it cannot absorb a variable disturbance. These anchor replacing hardcoded counts with functions of the real variable (blast-radius, progress signal, work-independence). Boundary (ashby): the law shows a fixed regulator is *insufficient* — it does NOT prescribe the controller; "every constant is wrong" is an over-application.

| id | ref | minimal-claim | domain | lastVerified |
|----|-----|--------------|--------|--------------|
| elkan-2001 | Elkan, C. (2001). "The Foundations of Cost-Sensitive Learning." *IJCAI 2001* | The optimal decision threshold is τ = C_fp/(C_fp+C_fn) — it falls out of the cost asymmetry, not a fixed count; a high cost of failing to act (e.g. an irreversible mutation) shifts τ to trigger earlier | decision theory / ML | canonical |
| page-1954 | Page, E.S. (1954). "Continuous Inspection Schemes." *Biometrika* 41(1/2):100–115 | CUSUM: accumulate a running score, signal when it crosses a threshold calibrated to a target false-alarm rate; the trigger is a function of observed history, not a fixed count (optimality: Moustakides 1986) | statistics / change detection | canonical |
| schmitt-1938 | Schmitt, O.H. (1938). "A Thermionic Trigger." *Journal of Scientific Instruments* 15:24–26 | Hysteresis / dual-threshold: two trip points create a dead band so noise near the boundary cannot cause repeated switching ("chattering") | control engineering | canonical |

---

## open systems / dissipation — LENS, bounded (NOT a §0 root)

These ground a LENS, not a root (§A.5 formalism honesty). The open-system / free-energy core is FACT (a *necessary condition* on life); but "the most efficient dissipator is *selected*" is CONTESTED and directly rebutted, and applying the frame to an AI improving itself in a software ecosystem is an ANALOGY, not a mechanism — the actual improvement mechanism here is directed selection (R4) + the measurement loop (R→S). The root bar (could-not-refute + ≥3 independent) is NOT met by the selection claim; this is why it lives as a lens under R4/R5, not as an R8. Supersedes the parked "negentropy" owner-disclaimed-metaphor (mined-invariants) — same idea, now anchored with its boundary.

| id | ref | minimal-claim | domain | lastVerified |
|----|-----|--------------|--------|--------------|
| schrodinger-1944 | Schrödinger, E. (1944). *What is Life?* Cambridge University Press | A living system maintains local order by importing free energy and exporting entropy (open system; no second-law violation). A necessary condition, NOT a selection criterion | physics / biology | canonical |
| prigogine-1977 | Nicolis, G. & Prigogine, I. (1977). *Self-Organization in Nonequilibrium Systems*. Wiley. (Nobel Chemistry 1977) | Far-from-equilibrium open systems can spontaneously self-organize past instability thresholds (dissipative structures). Boundary: shows self-organization is *possible*, NOT that maximal dissipators are selected or that biology is thereby explained | physics / chemistry | canonical |
| england-2013 | England, J.L. (2013). "Statistical physics of self-replication." *J. Chem. Phys.* 139:121923. arXiv:1209.1179 | Fluctuation-theorem lower bound on heat dissipated in self-replication; driven matter may restructure to dissipate more ("dissipative adaptation"). CONTESTED in strong form — England (2016) concedes that for replicators the thermodynamic and Darwinian accounts "become one and the same" (not a distinct mechanism) | physics / origin-of-life | 2026-06-14 (subagent arxiv) |
| kolchinsky-2024 | Kolchinsky, A. (2024). arXiv:2404.01130 [exact title pending independent verify] | Argues a universal thermodynamic bound linking dissipation to replicator growth/decay rates "cannot exist in principle" — a direct theoretical rebuttal of the strong dissipation-adaptation claim | physics / statistical mechanics | 2026-06-14 (subagent-reported; id pending re-verify) |
| england-2016 | Perunov, N., Marsland, R.A. & England, J.L. (2016). "Statistical Physics of Adaptation." *Phys. Rev. X* 6:021036 | Driven self-assembly adapts toward higher work-absorption; states that for self-replicators the thermodynamic and Darwinian accounts "become one and the same" — so it is NOT a distinct mechanism (the concession that bounds the lens) | physics / adaptation | 2026-06-14 (subagent arxiv) |
| dewar-2009 | Dewar, R.C. (2009). "Maximum Entropy Production as an Inference Algorithm..." *Entropy* 11(4):931–944 | Dewar recants MEPP-as-physical-law, recasting it as a MaxEnt inference algorithm — MEPP failures falsify the input assumptions, not an established law of nature | physics / inference | 2026-06-14 (subagent-reported; pending re-verify) |

---

## Provenance (non-Λ: owner-artifacts, not scientific anchors)

The following are owner artifacts, issue/PR references, and engineering notes. They are recorded here for provenance but are NOT Λ anchors and must not be cited as scientific sources. Structural ids for invariants (#1…#34) come from `neuro-matrix/invariants.txt` — they are not issue numbers.

```
neuro-matrix#27   the cross-AI advisory exemplar ("Поехали")
neuro-matrix#28   the harness-is-a-communication-system
neuro-matrix#43   the INV_LINES PR
neuro-matrix#56   the parking-lot consolidation
neuro-matrix#59   the protocol-path human-gate PR
neuro-matrix#63   the R→S audit
neuro-matrix#64–68 the eval-gate fixes (McNemar-tail, Cohen's-d, rater-aware-α, cross-family judge, vanilla baseline)
neuro-matrix commit #133  "caveman" commit title
mirabilis#114     paired sandbox-side issue

interview-coach-skill   noamseg/interview-coach-skill ∈ mirabilis config/skills.txt:1 (catalog seed, not a scientific source)
owner-memory / per-session logs → SCRATCH; do not store in Λ

mirabilis-TUI-followups   → mirabilis#132 (W9 cross-cluster back-nav + W10 adaptive overlay form sizing; dept/graph-plan-sandbox.md §10-11; genome/registry-M.md work-item list; agreed deferrals from PR #131)
WSL2-canary (parked)      → mirabilis#121-L1 (docker-in-WSL2 E2E canary; vectors/bugs.md §Parked; trigger: date ≥ 2026-06-16)
```
