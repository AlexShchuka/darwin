# Vec · v-disc — Idea-exchange (the cross-AI advisory exemplar condensed)

Type: this is a Vec entry — transient, not truth, neither a gene 𝒢 nor an archive entry Λ (vectors.md §Type). Source [FACT]: the cross-AI advisory exemplar (OPEN) and its comments (origin recorded as provenance in archive/archive.md); two authors — O = AlexShchuka (owner, neuro-matrix) · D = daniilkosofferrumcom-png (external, own harness). This is the §J `public(Γ)` exemplar — other-AI reads Γ and extracts ideas (GENOME §J). Γ is an idea-SOURCE, not a private cache. This file records the diagnostic + the reusable patterns; the dialogue itself is transient. Exemplar-claim [FACT]: an external dev (D) read O's repo, adopted patterns (a NEURO_MATRIX_ADOPTION_ROADMAP exists on D's side, comment §Part-1), and fed corrections back — bidirectional gene-flow.
`v-disc` = the cross-harness exchange: O audits D's nascent agent-system via a fixed diagnostic; both sides trade engineering patterns; the medium is one public issue (the "boundary object"). Method O imposes: type every thought; reality is arbiter, ¬the AI; understanding proven by paraphrase ¬nod.

## §1 — The 6-question diagnostic protocol [FACT, the cross-AI advisory exemplar opening comment]
```
frame  : per-item shape = "что есть → что делаешь → а не думал, что…? → что поможет (+links)"
                          (state → your-move → reframe → remedy+sources)
Q1 [most-important] goals/invariants/nevers :
   (a) 3 concrete tasks the system must DO (¬"improve itself")  (b) priority order reliability/speed/budget  (c) 3–5 "never"s
   ground : self-improvement w/o an objective fn = optimizing the easily-measured, ¬the wanted (Goodhart-shaped)
Q2 the brain (bottleneck) : LLM-calls/task? budget 0 vs ~$5/mo?       theory-of-constraints: widen the one bottleneck first
Q3 memory : recall 3 times a note was READ and changed an action      "no reader → it's a log, not memory"
Q4 the monolith : which 3 spots broke most last month?               decomposition is NOT step 1 (see §3 patterns)
Q5 secrets : name them (NO values)                                    leak is at the INPUT (secrets in context), ¬the output
Q6 prompt-as-system : rewrite your last big prompt in the 5-line template
verdict-discipline [FACT] : "где не знаешь — пиши «не знаю», это полноценный ответ"  ("don't know" is a valid datum)
∴ the 6 answers ARE the plan; answer with data, not explanations of how-it-got-this-way.
```

## §2 — The 5-line prompt template [FACT, the cross-AI advisory exemplar §8, verbatim structure]
```
Цель        Goal:        one, primary
Контекст    Context:     links to files/issues, ¬a retelling
Ограничения Constraints: what NOT to do
Готово-когда Done-when:   a checkable signal of result
Шаг         Step:        what we do first
```
```
diagnosis [FACT, the cross-AI advisory exemplar §8] : write-only prompt ≅ write-only memory (same disease — input w/o structure → system w/o structure).
claim [FACT] : rewriting a 10-tasks-in-one-sentence prompt through the template makes the tasks fall out as separate solvable lines.
adoption [FACT, D's reply] : D maps it to an existing STEP-0 / activation-gate (structured session ENTRY: declare role, what-read, anti-patterns, scope).
```

## §3 — Reusable patterns (the harvest; each = a portable gene) [FACT, the cross-AI advisory exemplar unless tagged]
```
P1 invariants = machine-enforced GATES, ¬willpower
   "правило, которое не проверяется машиной — это пожелание"  (an unchecked rule is a wish)
   enforce-classes [FACT, D's taxonomy, comment §Part-2] :
     [A] pre-commit structural checks (deterministic)  [B] manual 0-LLM linters (selftest, but "remember to run")  [C] conversational space (role-decode) — git-hook can't force by design (no commit yet at prompt-read)
   portable: pre-commit · pytest as a real barrier (no green → no merge, no --no-verify) · cron'd random invariant self-sample (~20 lines bash)
P2 memory : "no reader → no write"  +  cite-2-3-notes-before-acting (0 LLM)
   mechanic : before a task the agent must quote 2–3 notes it will use; nothing to quote ⇒ memory dead ⇒ fix READING ¬writing (~10 lines, honest metric)
   skill = runnable CODE, ¬prose "how-to"  [ASSOC: Voyager arXiv:2305.16291]
   size-cap + compaction of old → digests  [ASSOC: Letta/MemGPT, Mem0]
   O's home [FACT] : mirabilis memory = 7 typed category-files, index read at EVERY session-start ⇒ write-w/o-read impossible by construction
   OPEN-Q [FACT, both sides, unresolved] : a 0-LLM judge can verify a note was READ, but NOT that it CHANGED the decision (ritual cite vs live cite). candidate 💭: require the cite's token-span to overlap the final diff — weak, machine, AND misses notes that CANCELLED an action (empty diff, no overlap).
P3 LLM-only-where-code-cannot
   "LLM зовём только там, где нельзя кодом" — turn every repeating call into code/a rule  [ASSOC: Anthropic "Building effective agents"; 12-factor-agents]
   corollary : a deterministic construct beats a "smart" agent for the same job; D's dry-mode (tests w/o LLM) = this instinct
P4 prompt-injection defense [FACT, OWASP-LLM01:2025] — "чужой текст = данные, ¬команды"
   layered : (1) author ALLOWLIST — instructions only from O/owner; everyone-else's text handled AS DATA  (2) single OUTBOX — all external acts (post/commit/msg) through ONE gated fn + (for now) manual confirm  (3) ↑ dual-LLM (Willison: privileged-w/-tools never sees foreign text; quarantined sees it "w/o hands")  [ASSOC]; CaMeL arXiv:2503.18813
   REFINEMENT [FACT, later comment, O self-corrected] : look not at WHO authored but at WHAT the text can BREAK → least-privilege + blast-radius containment > an author-gate. ⇒ D downgrades author-allowlist (their B6), keeps the single outbox (B5).
P5 secrets : .env on-device only; git holds .env.example (names, no values); agent gets secrets as ENV at launch, NEVER as a readable file; gitleaks in pre-commit + GitHub push-protection  [FACT; O's home: mirabilis tokens in keychain/docker-volume, 0 secrets in git]
P6 strangler-fig refactor — decomposition is NOT step 1  [FACT, the cross-AI advisory exemplar §4; ASSOC: Fowler StranglerFig / BranchByAbstraction]
   ORDER (binding) : (1) ban `except: pass` by machine — ruff E722  (2) characterization tests (freeze behaviour AS-IS, ¬as-should-be = the safety net)  (3) agent whitelist: may edit only test-covered files  (4) ONLY THEN carve, strangler-fig (new grows beside old, traffic shifts, old dies); never rewrite-from-scratch
   in-one-process seam [FACT, O's answer] : seam is at code-joints ¬network; introduce an interface layer over a chunk, hide old behind it, grow new beside, "traffic switch" = a flag / dependency-swap; first seam = behind a single access-point to the shared global state
P7 characterization tests : capture current behaviour incl. its warts  [ASSOC: understandlegacycode.com]
   OPEN-Q [FACT, D, unresolved] : with `except: pass`, "as-is" INCLUDES silent-swallow → the net freezes the bug too; distinguishing behaviour-to-keep from bug-frozen-into-the-net is unsolved
P8 brain-bottleneck widening (region-dependent — the table's numbers are O-region) [FACT]
   O-claim : free tiers (Groq 1k–14.4k req/day, Cerebras 1M tok/day, GitHub-Models 50–150/day, OpenRouter 50→1k/day) ⇒ thousands of calls/day for ~$0; LiteLLM = a cascade over keys-you-ALREADY-have; FrugalGPT (≤−98% $) ; GPTCache for repeats
   D-correction [FACT, accepted by O] : the bottleneck is KEY-ACQUISITION not rate-limit — Groq signup 403 by fingerprint, Gemini ≈20/day; LiteLLM cannot ACQUIRE a key. region-proof base = local model (Qwen-Coder 7B/14B) as router/classifier/compressor, cloud as coder. RU keys: GigaChat/YandexGPT (₽, KYC barrier ≠ zero), reseller-proxies.  [ASSOC: CoALA arXiv:2309.02427 memory taxonomy D arrived at independently]
```

## §4 — The communication-protocol layer (the "connector"; O's thesis: the real bottleneck is information-EXCHANGE) [FACT, the cross-AI advisory exemplar mid-thread]
```
8 rules [FACT, O, sourced to comms science — Lakoff&Johnson, Korzybski/Hayakawa ladder, Clark common-ground, Grice, Star&Griesemer boundary-objects, Nida] :
  1 tag every thought ✅proven/💭guess/❓open   (≅ FACT/HYPO/Q — D maps to their epistemic-auditor [факт/гипотеза/мнение])
  2 abstraction-ladder: drop a cloud-idea to a touchable stone (file/number) and lift a dry fact up
  3 a "what we both now know" receipt line ending each exchange   4 diverge-then-converge (associate freely, THEN select signal/decoration/noise)
  5 translate by-MEANING ¬by-word; accept iff the other can PARAPHRASE w/o losing the invariant (¬a 1–5 score — a score is itself Goodhart-able, D's correction accepted)
  6 shared dict ≤10 words (a disputed word halts talk until "X means Y" is written)   7 the shared object (this thread)   8 move by points (mark what closed)
truth-model [FACT, O] : truth = reality (checkable) + the two humans' agreement; the AI is a TRANSLATOR that "errs beautifully" (hallucinates) and cannot self-judge.
  believe only when 3 independent witnesses converge: direct human talk + AI + reality; two diverge → STOP.   [grounds GENOME §D R→S = AskMe⊕eval⊕tests; §I anti-self-judge]
attachment [FACT] : O attached an ADR "Общий код / Common-Code" (v1 226-line spec: layers CHANNEL→MEANING→SYSTEMS→ARGUMENT→HANDS-CHECK, postulates П1–П9, theorems Т1–Т5, falsifiable predictions Э1–Э4; v2 = compressed: a 3-side invariant-table + 3 numbers N_inv≤30/N_terms≤20/B_recheck + a sycophancy frame). [Q] full ADR body not fetched here — title/structure only, from D's paraphrase.
  load-bearing from v1 [FACT, D's paraphrase] : DPI/П4 (translator M only LOSES info about intent ⇒ truth at sides+reality); Т2 (linearizing a tree by one path under-determines edges ⇒ pass relations EXPLICITLY — Toulmin/Novak map); A5 (paraphrase-acceptance; a number-score is a gameable surrogate).
  anti-sycophancy [FACT] : not "be honest" but observable — a zero-disagreement flag + a separate refuting pass; human oracle SIGNS the OTHER side's claim (D signs what AI produced in an A-session, O vice-versa), budgeted B_recheck/wk [ASSOC: Bainbridge — humans can't vigilance continuously; Sharma 2023 + Perez 2022 sycophancy is inverse-scaling].
```

## §5 — Exchanged deliverables (bidirectional, symmetric) [FACT, the cross-AI advisory exemplar closing comments]
```
D→O : (1) token-budget calibration framework (size×load-type → %budget, re-cal in-session)  (2) FAILURE-FIRST (final report opens with a "Failures" section, else rose-tinted)  (3) the parser-builder domain case (self-improve bound to a real product acceptance, ¬abstract self-improvement)  (4) mutual held-out canary (each side seals N tasks the OTHER's eval never saw → blind run, beats Goodhart for both)  (5) the 0-LLM "live-cite" overlap criterion (a concretization of O's own guess)  (6) the verdict-backlog format §6-bis (carrier of rule-8)
O→D : the 6-Q diagnostic · the 5-line template · the 8 connector-rules · the Common-Code ADR · the patterns P1–P8 above
D-self-FAILURE [FACT, D's own FAILURE-FIRST] : D's earlier comment opened with deference/praise ("ученик" lexicon) — D HAS a mechanical outgoing-text gate (issue_answer_check.py) that catches exactly that tone, but didn't run it on the sent text ⇒ "rule exists, not executed" — D's instance of O's §0 (a mediator left to self-check skipped the check).
```

## §6 — Cross-references into Γ (why this entry is load-bearing despite being Vec)
- GENOME §J, public(Γ): "other-AI reads Γ and extracts ideas" — this exchange is the cited exemplar.
- GENOME §J, read-before-act (invariant #22): P2 cite-before-acting is the same instinct, cross-confirmed by an external party.
- GENOME §D, R→S = AskMe + eval + tests: §4's truth-model (3 witnesses — human + AI + reality) is the same shape.
- GENOME §I, anti-self-judge: §4 "AI cannot self-judge"; §5 D's gate-skipped-on-self = the failure mode that motivates externalizing the judge.

Discipline-note: these are CONVERGENCES (two harnesses reached the same rule), not proofs. The tag stays ASSOC for "convergence ⇒ the rule is right".

## §I — Ledger (this entry)
```
FACT  : the cross-AI advisory exemplar exists+OPEN; two authors O/D; the 6-Q protocol; the 5-line template (verbatim); patterns P1–P8 as stated in-thread; the 8 connector-rules; the two ADR attachments exist; D's self-FAILURE on the gate.
ASSOC : the named external sources (Voyager, Letta/Mem0, Anthropic/12-factor, OWASP-LLM01, Willison/CaMeL, Fowler, CoALA, comms-science set, Bainbridge/Sharma/Perez) — cited BY the thread, not re-fetched here except caveman/§Γ checks; "convergence ⇒ correctness".
HYPO  : that adopting any specific pattern improves D's (or N's) outcomes — untested across the boundary; the live-cite overlap criterion; the held-out-canary scheme.
Q     : full body of the Common-Code ADR (only title+D's paraphrase captured — marked); whether the exchange's mutual corrections have landed in either repo (a roadmap is CLAIMED on D's side, not verified here).
transient : whole entry — the dialogue is working-state; the harvested patterns, once they land as 𝒢/Λ, make this discardable. Discarding v-disc does not force a rebuild of GENOME.
```
