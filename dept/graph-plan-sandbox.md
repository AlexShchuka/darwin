# graph-plan-sandbox (improve/M) — what & how to improve the coral (mirabilis, mechanism)

Organ `M` = sandbox = mechanism phenotype (§A GENOME). Anchor: `/workspace/mirabilis` (live git, Go). This file answers, per gene, **WHAT** to improve and **HOW** — concrete, to the file. Encoding: English + FOL where a real formal object exists; honest dense prose elsewhere (§C). Per-claim tag `FACT·ASSOC·HYPO·Q`; FACT carries a `file:line` / repo / issue anchor. No invention: where a Δ is a plan not a landed fact, it is `HYPO`.

Scope law (G2; defined genome/design-principles.md): `M` provisions + exposes a tool/service (config-driven, replaceable, observable, bounded); behavioural use (when-to-search, judging, routing) belongs to `N`. A Δ that decides *when* or *whether* to use a mechanism is mis-placed in `M`.

Mission-frame (INV-A; do not justify a Δ by "saves tokens"): the ecosystem goal is ⟨truth, capability-across-domains, self-sufficiency, evolvability⟩ — grounded: truth/accuracy ↔ R4+R6 (a knowledge-system not tracking reality is selected against; density=truth=accuracy are one thing); evolvability ↔ R4 (variation+heredity+selection; without selection → drift). Every work-item's rationale must serve that goal; token/$ economy is a *consequence* of a work-item, never its rationale. The goals nest and are inherited downward — ecosystem (working with AI) ⊃ sandbox (provisioning) ⊃ each feature-module Wi.

**LANDED — mirabilis PR#134 (pruned here, §G self-prune; expressed in registry-M):** W1 localllm config+discovery+Sanitize · W2 telegram detect+progress+4xx-retry · W3 ghauth host-open+copy · W4 attach removal · W5 vscode "/" · W6 toolchain+dependabot-integrity in image · W7 bounded proxy+ctx-sleep · (off-plan, same PR) onboarding/trust/theme suppression + copy-feedback honesty. INV-D/E/F landed (homes green). The plan below = the OPEN work only.

---

## 0 — Ordering by leverage

Order: G-cav ≻ W8 ≻ W9 ≻ W10. Rationale:
- `G-cav` first: a **standing catalog entry already exists** yet there is **no provision step + no session-flag wiring** (HYPO; §1) ⇒ adopting AS-IS is the cheapest mission-positive Δ (self-sufficiency of the dialogue channel).
- `W8` (SearXNG) = a new channel gene `G-web` materializing access to `𝕌` → capability-across-domains; larger surface (new package + compose), so below the in-place Δ.
- `W9`/`W10`: deferred UX architecture (mirabilis#132), eng-choice/HYPO; below W8.

---

## 1 — G-cav (caveman) — adopt AS-IS  [detail gene; highest leverage]

```
gene G-cav : α_M = install + session-flag ; α_N = terse skill (projections.md:25)
κ_external : github.com/JuliusBrussee/caveman   [FACT, repo viewed: public]
mechanism(caveman) [FACT, README + INSTALL.md viewed] :
  skill "caveman" (terse output)  ⊕  Claude-Code hook + statusline badge  ⊕  skill "caveman-compress" (compress memory files)
  ⊕ opt-in MCP "caveman-shrink" (--with-mcp-shrink)        cuts ~75% output tokens, "brain big, mouth small"
```

WHAT: express `G-cav` into `M` AS-IS — adopt the upstream artifact unchanged; do **not** reimplement (invariant #4 anti-invention; INV-B new-module=mechanism).

State of the gene in `M` (verify):
- `FACT` caveman **IS** in the catalog: `/workspace/mirabilis/config/skills.txt:2` = `juliusbrussee/caveman`; covered by smoke test `/workspace/mirabilis/test/token_opt.bats` ("caveman skill is in the skills catalog").
- `HYPO` caveman is **catalog-only**: no dedicated provision step nor a SessionStart flag wires it on. The generic skills path (`internal/engine/provision/skills.go`) installs entries from `skills.txt`; there is no `caveman`-specific step (cf. `provision/rtk.go`, `provision/headroom.go`, `provision/localllm.go` which are per-tool). ⇒ the genome's `registry-M:33` claim `caveman ∉ M, grep ∅` is **FALSE against the repo** (contradiction §7-C1).

HOW (Δ, AS-IS, minimal-diff G1/YAGNI):
1. `FACT-of-state` Keep the catalog line; it is the AS-IS install vector (Claude-Code marketplace skill). No code reimplements caveman.
2. `HYPO` If "always-on" is desired: add the caveman session-flag the way other quartet members are wired — a SessionStart concern (`internal/hooks/session.go`) or a one-line provision concern, **config-gated** (`G4`: a `config/` flag, not a code constant). Per the projections allele `α_M = install+flag`.
3. `HYPO` Memory-file compression: caveman ships `skills/caveman-compress` [FACT, contents listed]. The `M` memory channel is `G-know` (`internal/engine/membackup` + `internal/engine/provision/memory.go`, categories at `config/config.go:44-53`). Δ = make `caveman-compress` available to the memory writer; **mechanism only** — *when* to compress is `N`'s recall/write discipline (invariant #31), do not encode a compaction policy in `M`.
4. Channel-disjointness holds [FACT registry-M:35]: caveman = **agent-out** window; RTK = tool-out; headroom = API-window; localLLM = offload. ⇒ ¬duplication; adopting caveman does not collide with the other three quartet alleles.

Mission frame: caveman raises **density** of the owner↔AI channel (D-functional §C) and shrinks memory footprint → self-sufficiency of the second brain. Token economy is the *consequence*, not the rationale (INV-A).

Caveat: caveman is third-party (invariant #7 human-readable-without-AI applies to what it emits, but the *artifact itself* is an external dependency, not generated copy). `Q`: pin a release/SHA? (mirabilis pins rtk/uv/go by SHA in `.devcontainer/Dockerfile`; a marketplace skill has no SHA-pin path today — open question, not a blocker).

---

## 2 — W8 · SearXNG web-search  [new gene G-web; channel into 𝕌]

```
W8 : G-websearch (new), G-config, compose      registry-M:47
gene G-web : α = SearXNG service (organ M) → Λ.*    registry-new:35
κ : new package internal/engine/websearch (∄ today) ; config/mcp.json ; docker-compose.yml
```

WHAT: provision a SearXNG service + expose a websearch **tool/MCP** to the agent — a metasearch channel that materializes access to reality (`G-web`, registry-new:32-38). Mechanism only.

State (verify): `FACT` no `websearch` package exists (`internal/engine/` listing has no such dir). `FACT` `WebSearch`/`WebFetch` already work via the Anthropic API (`mirabilis/CLAUDE.md` boundaries). ⇒ W8 adds an **owned, self-hosted** search channel (self-sufficiency), distinct from the API one.

HOW (Δ, INV-B new-module=mechanism):
1. New SRP package `internal/engine/websearch` (`G3`) — port + adapter to a SearXNG instance (`G8`).
2. `docker-compose.yml` — add a SearXNG service (the override pattern already exists: `compose.sock.yml`, `compose.sock.yml` referenced in `mirabilis/CLAUDE.md`). Egress note: `mirabilis/CLAUDE.md` says if an allowlist is added it must include the new edge — same discipline applies.
3. `config/` — tunables (`G4`): instance URL, timeout, result cap; register the tool in `config/mcp.json` (the MCP catalog, `config.go:121`).
4. Expose as a tool/MCP; **do not** encode *when to search* — that is `N` (the harness decides; G2, owner memory explicitly names web-search as a module not to justify by tokens or to let behaviour leak in).

Mission frame: an owned search channel feeds `Λ` (the external-source stratum) → capability-across-domains + self-sufficiency. `φ` (selection signal) of `G-web` is task-success per domain (registry-new:28), measured by `N`'s eval, not by `M`.

`HYPO`: entire W8 is greenfield (no code yet); leverage is real but cost (new service + package + compose + egress) places it below the in-place Δs.

---

## 3 — W9 · cross-cluster back navigation  [eng-choice; deferred from #131]

```
W9 : G-pipeline, G-steps, G-tui        registry-M (work-item list)
κ   : /workspace/mirabilis/internal/engine/pipeline/pipeline.go   [home]
      /workspace/mirabilis/internal/tui/router/router.go           [home]
source: mirabilis#132 L1 (agreed deferral from PR #131)
```

WHAT: the config wizard (`stacks`/`plugins`/`skills`) supports `shift+tab` back within its three groups (intra-cluster), but there is no way to step back **across pipeline steps** — e.g. from `gh-auth`/`telegram`/`attach` back into the config wizard. `esc` cancels the whole launch instead of rewinding one step. `HYPO` (deferred, not yet coded).

State [home, tagged — not grounding]:
- `pipeline.go` — `Pipeline.Run` iterates `p.steps` forward-only with a forward-only `states` map; `Resume(step, r)` delivers only to the *currently-waiting* step and returns an error otherwise; once a step's `Run` goroutine returns and the loop advances, there is no rewind/replay primitive. `[home: pipeline/pipeline.go, mirabilis#132-L1]`
- `HYPO` — no rewindable-step primitive exists today; the pipeline FSM is forward-only by construction.

HOW (Δ, eng-choice/HYPO — plan not landed):
Two candidate approaches from the issue, both non-trivial:
1. **Rewindable FSM** — a step stack with backward `Resume`; must be side-effect-aware (image build / provision cannot be trivially undone); weigh against G7 idempotency.
2. **Front-load all interactive choices** before any side-effecting step — redesign so the pipeline collects all user config upfront, then executes. Avoids rewind semantics entirely.

Mission frame: owner navigability across the full launch flow = lower owner friction; bounded interactive wait preserved. Deliberately deferred from PR #131 as an architecture change beyond a UX wave; not a launch blocker.

`[eng-choice]` — the choice between rewindable-step vs front-load is owner-gated architecture decision. `HYPO` until a design is chosen and landed.

---

## 4 — W10 · adaptive overlay form sizing  [eng-choice; deferred from #131]

```
W10 : G-tui, G-bus        registry-M (work-item list)
κ   : /workspace/mirabilis/internal/tui/router/router.go    [home]
      /workspace/mirabilis/internal/tui/app/screens.go       [home]
      /workspace/mirabilis/docs/tui-principles.md (P1)       [home]
source: mirabilis#132 L2 (agreed deferral from PR #131)
```

WHAT: a form pushed mid-launch (config wizard, telegram, gh-auth) renders at huh's natural size until a `WindowSizeMsg` arrives; at very small viewports the overlay box clips content (a description line can push options off-screen). Normal/realistic sizes (>=50×20) render fully — verified. This is an edge, not a launch blocker, and is pre-existing behaviour shared by all overlay forms (not introduced by PR #131). `HYPO` (deferred, not yet coded).

State [home, tagged — not grounding]:
- `router.go` — `router.Model.Update` on `bus.ScreenPush` calls `s.Init()` but does **not** forward the current window size to the freshly-pushed screen. `[home: tui/router/router.go, mirabilis#132-L2]`
- `screens.go` — `formScreen.Update` calls `form.SetSize` only on `tea.WindowSizeMsg`; a pushed form is therefore unsized until the next terminal resize event. `[home: tui/app/screens.go, mirabilis#132-L2]`

HOW (Δ, eng-choice/HYPO — plan not landed):
On `ScreenPush`, deliver the current `winW/winH` to the new screen — either (a) the app re-emits a `WindowSizeMsg` after a push, or (b) the push carries dimensions explicitly. The form sizes itself to the overlay's inner area. Satisfies the Adaptive Layout principle (`docs/tui-principles.md P1`). Small and contained.

Mission frame: owner sees full form content at all tested viewports = fidelity of the interactive channel. Low enough blast-radius to be self-contained once prioritized. Explicitly deferred from PR #131.

`[eng-choice]` — exact delivery mechanism (re-emit vs carry) is owner/reviewer preference. `HYPO` until landed.

---

## M invariant-genes — LANDED (mirabilis PR#134, homes green)

INV-D config/discover ¬hardcode — home: localllm env-config + /v1/models discovery + completer/config tests
INV-E sanitize external-model out — home: SanitizeOutput + table test + mcp_test (offload boundary)
INV-F bound IO ¬human-wait — home: notify 4xx-permanent + capped-retry tests; bounded Configure

---

## §Ledger (epistemic, this file)

```
FACT (file:line / repo / issue):
  caveman ∈ catalog: config/skills.txt:2 ; test/token_opt.bats
  caveman mechanism: JuliusBrussee/caveman README+INSTALL (skill+hook+caveman-compress+opt-in MCP)
  W1–W7 + off-plan onboarding/copy-honesty LANDED mirabilis PR#134 (CI 9/9); pruned from this plan, expressed in registry-M.
ASSOC:
  leverage ordering (mission-reach × organ-Δ / cost) = owner-lens application of G0
HYPO:
  G-cav not-wired (catalog-only; no per-tool provision step / session-flag)
Q:
  pin caveman by release/SHA? (no SHA-pin path for marketplace skills today)
```
