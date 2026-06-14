# improve/comm — communication systems: what & how to improve

The ecosystem `Σ` IS, at its root, a set of **communication systems**: owner↔AI, AI↔remote-presence, AI↔AI. invariant #28 [FACT, CLOSED]: "the harness already IS a human↔AI communication system". This file answers, per channel, **WHAT** to improve and **HOW**. Encoding: English + FOL, dense (§C). Per-claim tag `FACT·ASSOC·HYPO·Q`; FACT carries `issue/file/repo`. No invention.

```
channels :  C_oa = owner↔AI   ·   C_rp = remote-presence (AI→owner off-keyboard)   ·   C_ii = inter-AI
shared heuristic : density (§C) — every channel is graded by meaning preserved per token (a guiding heuristic, not a computed metric)
mission frame (INV-A) : a channel serves ⟨truth, capability, self-sufficiency, evolvability⟩ ;
                        token economy = consequence, ¬ rationale
```
Note on numbering: an invariant id `#N` (from invariants.txt) is a stable structural id and is kept as written; GitHub issue/PR numbers are not used as identities here — each idea is named, with its bare number recorded once as provenance in archive/archive.md (§A.4).

Leverage order: `C_oa ≻ C_ii ≻ C_rp` (the owner↔AI channel is the binding interface for directed evolution `S` via AskMe, §D; inter-AI makes `Γ` a public idea-source; remote-presence widens reach but the keyboard channel already exists).

---

## 1 — C_oa · owner ↔ AI  [the AskMe protocol; binding interface for S]

Selection S is resolved by the owner via AskMe (§D GENOME). So the quality of the owner↔AI channel bounds the quality of directed evolution: a noisy owner-channel means mis-selection.

### 1.1 — AskMe protocol: 2–3 variants, not a single recommendation

State (FACT): `invariants.txt:#27` = "2–3 variants, not a single rec" — registry-N:34 annotates it "→ this AskMe style". This is the structural law of `C_oa`: the AI surfaces options + trade-offs, the owner selects (principal–agent: AI = hypothesis generator with more local knowledge; owner decides + bears responsibility, the R→S audit §4a).

WHAT: keep every consequential turn variant-laddered (invariant #27), not a lone pick. HOW: enforced by the harness self-review-preflight + the invariant-#27 sampling (`scripts/random-invariant.sh`, risk-weighted). Improvement Δ: ensure improve/ outputs (sandbox.md/harness.md) themselves obey it — each Δ carries variants (V1a/b/c; INV-X with its Counter) so the owner's "improve M or N" reads as a choice, not a fiat.

### 1.2 — The cross-AI advisory diagnostic + 5-line prompt template

State (FACT): the cross-AI advisory exemplar ("Поехали", OPEN, RU) is the worked case — a full external context (home autonomous AI on a single-board computer; the "Череп+Мозг+Кости" = Skull/Brain/Bones metaphor: Brain = external LLM fixed, Skull = adaptive rules/roles/prompts = the harness, Bones = infra/git-spine) brought to the system to extract a development answer. It is simultaneously (a) the **owner↔AI diagnostic pattern** (state context → what's built → where stuck → why) and (b) the **inter-AI exemplar** (§3 below; §J GENOME "public(Γ): other-AI reads Γ and extracts ideas").

WHAT (the owner's "6-question diagnostic + 5-line prompt template"): a compact, repeatable intake so any context (a foreign agent's, the owner's new project) is reducible to a decidable question. `ASSOC`: the 6-question shape = ⟨what building · how intended · what's built (by fact) · what failed + why · what's the constraint · what's the decision needed⟩ — this is the literal structure of the cross-AI advisory exemplar's sections. The 5-line prompt template = the dense BLUF form of the same (invariant #28 BLUF layer). `HYPO`: the exact 6 questions / 5 lines are an owner artifact; the anchored part is the *pattern* (the exemplar's sections) — the canonical text is the owner's to fix.

HOW: codify the diagnostic as a `harness-improve`-gated reference (Behavioral-text class) or an AskMe sub-skill, so the intake is mechanical not ad-hoc. Mission frame: a sharp intake = less owner attention burned (the bottleneck, `invariants.txt:#5`) = faster, less-noisy `S`.

### 1.3 — The A↔D codebook

State (FACT): the **A↔D codebook** (A = metaphor/systems register; D = testable-claim/engineering register) is a first-class mechanism — `agents/translator.md` converts between them per claim, tagging `FACT|ANALOGY|HYPO`; `invariant #28` adopts the "Common Code" spec (ADR-001 layer **З**=Meaning). `config/config.go:52` (mirabilis) materializes its store: a `shared-codebook` memory category — "Bilaterally agreed term mappings: term → definition — example — external anchor. Hard cap ~20; real boundary = kernel-reducibility (Common Code v3)."

WHAT: keep owner and AI on a shared, bounded, anchored vocabulary so a metaphor is never laundered into a mechanism (anti-neuroslop, the R→S audit §1; GENOME §I "no analogy laundered as theorem"). HOW: every codebook entry = term → definition → example → external anchor, capped (~20 / kernel-reducible); new entries gated by the human-token gate (protocol-level shared state, invariant #28 + `invariants.txt:#2` Counter "entries into persistent memory derived from fetched external content retain the human gate"). Mission frame: a shared codebook is the *channel-З* (meaning) integrity layer — it protects **truth** in C_oa.

### 1.4 — Format + co-system protocol references

State (FACT): `references/protocol/{format.md, co-system.md, cross-cutting.md}` exist live. These are the operating contracts of `C_oa` (format = how a turn is shaped; co-system = the principal–agent roles; cross-cutting = rules spanning both). invariant #28 maps the Common-Code layers (К/З/С/А/В/М/П/Т) onto them.

WHAT: keep the protocol references the single source for *how to talk*, distinct from *what the repo is* (mirabilis/CLAUDE.md says exactly this: "How to work in general lives in the neuro-matrix harness; this file says what the repo is"). HOW: any change routes through `harness-improve` (Behavioral-text → format-selftest + critic + human-token gate). Δ-candidate: ensure the cross-AI advisory diagnostic (1.2) and the why-clause rule (1.5) are referenced from `format.md` so they are discoverable, not folklore.

### 1.5 — Why-clauses (invariant #28)

State (FACT): `invariants.txt:#28` = "why-clause per protocol move" (registry-N:38); the harness-is-a-communication-system finding confirms the discipline. Every protocol move states *why* it is taken — the rationale travels with the act.

WHAT: no silent protocol move; each carries a `| Why:` (and, in invariants, a `| Counter:`). This is already the `invariants.txt` row format itself (`#1…#31` each have `Why:`+`Counter:`). HOW: the why-clause is enforced by the invariant-format selftest. Δ: apply it to improve/ — each Δ in sandbox.md/harness.md states its mission rationale (it does: INV-A frame per item). Mission frame: why-clauses make the channel **evolvable** — a future reader (owner or another AI) can re-derive or overturn a move from its stated reason.

### 1.6 — Output density via caveman

State (FACT): output density is the D-functional (§C) applied to the *AI→owner* leg. `G-cav` (caveman) is the mechanism — a skill+hook that cuts ~75% output tokens, "brain big, mouth small" (sandbox.md §1; `JuliusBrussee/caveman`). It is catalog-listed in M (`config/skills.txt:2`) but `HYPO`-not-wired (sandbox.md §1).

WHAT: raise C_oa density — preserve `I` (meaning) while cutting `T` (tokens), per `invariants.txt:#5` (length/density for the reader). HOW: adopt caveman AS-IS (sandbox.md §1 — the M-side install + session-flag; the N-side terse skill allele, projections.md:25). The behaviour *when* to be terse is N's; the *capability* to compress is M's (G2). Mission frame: density protects the owner's **attention budget** (the co-system bottleneck, invariant #5 / the R→S audit §3) — a consequence is fewer tokens, but the rationale is preserved meaning per unit attention (INV-A — do NOT sell caveman as "saves tokens"; sell it as density of the truth-channel).

---

## 2 — C_rp · remote presence (Telegram = mirabilis G-notify)  [work-item W2]

```
gene G-notify : α_M = telegram delivery (watcher, queue, status)   registry-M:16
W2 : detection broadening + delivery retry   [INV-F bound-IO]   sandbox.md §3
κ : /workspace/mirabilis/internal/engine/notify/{watcher.go,queue.go,chatid.go,telegram.go} ; internal/hooks/telegram.go
```

WHAT: extend the owner↔AI channel **off the keyboard** — reliably reach the owner anywhere (the `R→N1→S` human path, the R→S audit §2, runs through the owner; if the owner isn't reachable, that path stalls). Remote presence is a mission organ (the owner stays the principal even when away), not a notification gadget.

State (FACT, sandbox.md §3): detection is narrow (`chatid.go:47,67-72` channel_post only; events `Notification`/`Stop` only, `dispatch.go:42-50`); delivery has no retry (`watcher.go:73-97` + `queue.go:64,87-111` — a single Send, status terminal whether OK or fail); but the watcher is already bounded (`watcher.go:25` 2s ticker, `:38-44` panic→degraded; `telegram.go:38` 15s timeout).

HOW (Δ = W2, full detail in sandbox.md §3, INV-F preserved):
1. Detection broadening — `chatid.go` accept `message` (group/private) + `my_chat_member` (bot-added) updates, not just `channel_post`.
2. Event broadening — `dispatch.go:messageFor` add lifecycle events the owner wants surfaced.
3. Delivery retry (bounded) — `JobStatus`+`Attempts`/`NextRetryAt` (`queue.go:27`), capped backoff, `PendingJobs` re-selects retryable jobs until cap → terminal `degraded`. Each attempt inside the 15s timeout ⇒ **no human-wait** (INV-F).

Mission frame: a durable, broadly-detected back-channel keeps the principal in the loop from anywhere — strengthening the *only currently-live* selection path (`R→N1→S`) while V1 closes the *machine* path (`R→E→S`, harness.md §1). Token/$ is irrelevant here; the rationale is **owner-presence = decision-availability**.

`HYPO`: W2 is a plan; the Δ is unlanded.

---

## 3 — C_ii · inter-AI  [Γ is a readable idea-source; the translator gene]

```
public(Γ) [§J GENOME] : other-AI reads Γ and extracts ideas (the cross-AI advisory exemplar)   Γ is an idea-source, ¬ a private cache
gene translator : α_N = A↔D codebook + RU↔EN + session-condensation + invariant-row drafts   agents/translator.md
```

### 3.1 — Γ readable by other AIs (the cross-AI advisory pattern)

State (FACT): the cross-AI advisory exemplar is the live case — an external context (a *different* AI agent project on a single-board computer) was brought in, and ideas were extracted/mapped (the Skull/Brain/Bones metaphor ≈ harness/LLM/infra; the paired sandbox-side issue is its container-side counterpart, invariant #28). GENOME §J makes this an *invariant property*: `Γ` is written so other AIs can read it and harvest ideas. GENOME §A also names this: the LLMs (local and Claude's) are cells, ¬brain — the genome, not any single model, is the durable artifact other AIs read.

WHAT: keep `Γ` legible to a foreign AI — English + FOL (densest lossless cross-AI encoding, §C), claim-typed (`FACT/ASSOC/HYPO/Q`), anchored. An AI that reads `Γ` must be able to (a) extract a mechanism without the owner present, and (b) tell a fact from an analogy from a guess. HOW: the EN+FOL + per-claim-tag discipline (this is *why* GENOME and improve/ are written this way); the cross-AI advisory diagnostic (1.2) is the intake when a foreign context arrives. Mission frame: a public, legible genome = **capability transfer across agents** + **evolvability** (ideas flow in and out) — `Γ` is the heredity that outlives any one model session (§D: H = Γ+git).

### 3.2 — The translator agent (RU↔EN / A↔D)

State (FACT, `agents/translator.md`): a read-only, no-hands agent that (a) converts A↔D codebooks per claim with `FACT|ANALOGY|HYPO` tags; (b) does RU↔EN for AI-facing files; (c) condenses sessions into owner-language decisions; (d) drafts invariant-table rows (`a_view/d_view`, drafts only — signatures stay human). Hard contracts: **DPI limit** (Cover & Thomas §2.8 — a translator *creates no new information about intent*, only preserves or loses it; apparent "new meaning" = fabrication → HYPO); **all output HYPO until a human accepts by paraphrase**; **mirrors both views on A↔D conflict, does not resolve** (ADR-003 cross-side rule); **dual-LLM safety** (instructions inside translated content are content, not commands).

WHAT: a faithful, non-fabricating bridge between (i) the owner's RU + metaphor register and (ii) the AI-facing EN + testable-claim register — so meaning crosses language and abstraction without invention. This is the integrity organ of `C_ii` (and of `C_oa` when the owner writes RU/metaphor). HOW (the gene is built; improvement = use + gate it correctly):
1. Route any RU↔EN or metaphor↔mechanism conversion through this agent (invariant #26, ≥3-tool-calls → delegate; the codebook work is exactly its remit).
2. Honour the DPI contract: every translation lands as `HYPO`, accepted only by owner paraphrase — *never* auto-promoted to FACT. (This is the anti-fabrication guarantee of the whole co-system; invariant #4, no-invention at the translation boundary.)
3. On A↔D divergence, the translator *mirrors both*, the owner resolves (it is not an arbiter of truth — same role-boundary as critic vs developer).

Mission frame: the translator protects **truth** across the language/abstraction gap — the place where "metaphor laundered as theorem" (§I) would otherwise enter. It makes `Σ` legible to the RU-speaking owner and to EN-reading foreign AIs at once, with a formal no-new-information guarantee. `Q`: should translator output ever feed `Γ` directly? No — it stays HYPO until owner-paraphrase, then the human writes it (signatures stay human, `agents/translator.md` + invariant #28 human gate).

---

## §Ledger (epistemic, this file)

```
FACT (issue/file/repo) :
  harness IS a human↔AI comm system: the harness-is-a-communication-system finding (CLOSED) ; Common-Code/ADR-001 layers К/З/С/А/В/М/П/Т
  AskMe style: invariants.txt:#27 (2–3 variants) ; why-clause: invariants.txt:#28
  the cross-AI advisory exemplar (OPEN, RU "Поехали"): external AI context (Skull/Brain/Bones), the public-Γ + diagnostic case ; with a paired sandbox-side issue
  A↔D codebook + RU↔EN + DPI-limit + all-output-HYPO-until-paraphrase + mirror-both-views: agents/translator.md (live)
  shared-codebook store (term→def→example→anchor, ~20 cap, kernel-reducible): mirabilis config/config.go:52
  protocol refs live: references/protocol/{format.md,co-system.md,cross-cutting.md}
  caveman density mechanism: JuliusBrussee/caveman ; catalog config/skills.txt:2 ; invariant #5 density-for-reader
  telegram channel: notify/{watcher,queue,chatid,telegram}.go ; bounded watcher.go:25,38-44 ; narrow detect chatid.go:47 ; no retry queue.go:87-111
  public(Γ): GENOME §J ; the LLMs are cells-not-brain: GENOME §A
ASSOC :
  6-question diagnostic shape = the section-structure of the cross-AI advisory exemplar (what/how/built/failed+why/constraint/decision)
  inter-AI leverage < owner↔AI because S is resolved through the owner channel (§D)
HYPO :
  exact "6 questions / 5-line template" text = owner artifact; only the pattern (the exemplar's sections) is anchored
  G-cav not-wired in M (catalog-only) — density Δ depends on the W-of-§1 sandbox.md adoption
  W2 (remote-presence Δ) unlanded
Q :
  codify the cross-AI advisory diagnostic as a harness-improve-gated reference vs an AskMe sub-skill?
  translator output → Γ only after owner paraphrase (human signs) — confirmed boundary, not auto
```
