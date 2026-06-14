# graph-plan-sandbox (improve/M) — what & how to improve the coral (mirabilis, mechanism)

Organ `M` = sandbox = mechanism phenotype (§A GENOME). Anchor: `/workspace/mirabilis` (live git, Go). This file answers, per gene, **WHAT** to improve and **HOW** — concrete, to the file. Encoding: English + FOL where a real formal object exists; honest dense prose elsewhere (§C). Per-claim tag `FACT·ASSOC·HYPO·Q`; FACT carries a `file:line` / repo / issue anchor. No invention: where a Δ is a plan not a landed fact, it is `HYPO`.

Scope law (G2; defined genome/design-principles.md): `M` provisions + exposes a tool/service (config-driven, replaceable, observable, bounded); behavioural use (when-to-search, judging, routing) belongs to `N`. A Δ that decides *when* or *whether* to use a mechanism is mis-placed in `M`.

Mission-frame (INV-A; do not justify a Δ by "saves tokens"): the ecosystem goal is ⟨truth, capability-across-domains, self-sufficiency, evolvability⟩ — grounded: truth/accuracy ↔ R4+R6 (a knowledge-system not tracking reality is selected against; density=truth=accuracy are one thing); evolvability ↔ R4 (variation+heredity+selection; without selection → drift). Every work-item's rationale must serve that goal; token/$ economy is a *consequence* of a work-item, never its rationale. The goals nest and are inherited downward — ecosystem (working with AI) ⊃ sandbox (provisioning) ⊃ each feature-module Wi.

---

## 0 — Ordering by leverage

Leverage of a work-item rises with mission-reach and organ-health gain, and falls with cost. Resulting order: G-cav ≻ W1 ≻ W2 ≻ W8 ≻ W7 ≻ W3 ≻ W6 ≻ W5 ≻ W4 ≻ W9 ≻ W10. Rationale:
- `G-cav` first: a **standing catalog entry already exists** (`config/skills.txt:2` = `juliusbrussee/caveman`) yet there is **no provision step + no session-flag wiring** (HYPO; §1) ⇒ adopting AS-IS is the cheapest mission-positive Δ (self-sufficiency of the dialogue channel; communication.md) and removes a genome↔repo contradiction (§7-C1).
- `W1` (localllm) next: highest *capability+self-sufficiency* reach (a host model becomes a first-class, replaceable, sanitized tool) and lands two invariant-genes `INV-D, INV-E` (registry-M:51-54).
- `W2` (telegram) lands `INV-F` (bound-IO) — remote presence is a mission organ (owner↔AI; communication.md), but below W1 because the watcher is *already* bounded (`watcher.go:25` ticker, `:38-44` panic→degraded); the open gap is narrower (detection breadth + delivery retry).
- `W8` (SearXNG) = a new channel gene `G-web` materializing access to `𝕌` (registry-new:35) → capability-across-domains; larger surface (new package + compose), so below the in-place Δs.
- `W7, W3, W6, W5, W4` = robustness/UX/build-hygiene with bounded mission-reach; `W4` last (pure deletion).

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

## 2 — W1 · localllm: config-driven model + /v1/models discovery + Sanitize  [lands INV-D, INV-E]

```
W1 : G-localllm, G-config            registry-M:40
κ : /workspace/mirabilis/internal/engine/localllm/{completer.go,mcp.go}
    /workspace/mirabilis/internal/engine/config/config.go:20-24
    /workspace/mirabilis/internal/engine/provision/localllm.go
INV-D config/discover ¬hardcode  (registry-M:52)
INV-E sanitize external-model out (registry-M:53)
```

WHAT: turn the host-LLM edge from a **hardcoded constant** into a **config-driven, self-describing, sanitized** mechanism — a first-class replaceable tool (`G4 config-separate`, `G8 replaceable`), with model output treated as untrusted input crossing the trust boundary into the agent.

State (verify, all FACT):
- `config.go:20-24` — `LocalLLMBaseURL = "http://host.docker.internal:1234/v1"`, `LocalLLMModel = "local-model"`, `LocalLLMTimeout = 60s`, `LocalLLMMaxTokens = 2048` are **compile-time `const`** — NOT read from `.env`, unlike `STACKS/SKILLS/SOCK/AUTH_PROXY_PORT` which use `envRead` (`config.go:55,76,153,141`). ⇒ to change the model you edit code, violating `G4`.
- `completer.go:24-30` — `HTTPAdapter{BaseURL,Model,…}` POSTs to `…/chat/completions` (`:80`); the **model name is sent verbatim** (`:38,68`). No `GET /v1/models` discovery anywhere in `localllm/`.
- `completer.go:112` — returns `cr.Choices[0].Message.Content` **raw**; no sanitization. `mcp.go:21-35` — the `offload` MCP tool returns that text straight to the agent as `TextContent`. ⇒ a host model's output reaches the agent unfiltered (prompt-injection / control-char / oversize surface).
- `AGENTS.md` (`mirabilis/CLAUDE.md`) **documents** the edge as *intentional and hardcoded* to `…:1234/v1`. ⇒ W1 is a **deliberate design change**, not a bug-fix; it must update that doc paragraph too (contradiction §7-C2; `HYPO` until owner-approved).

HOW (Δ):
1. `INV-D` — Move the four constants to config. Add `.env` keys (`LOCALLLM_BASE_URL`, `LOCALLLM_MODEL`, `LOCALLLM_TIMEOUT`, `LOCALLLM_MAX_TOKENS`) read via the existing `envRead` pattern (`config.go:170`), with the current constants as defaults. One adapter constructs `HTTPAdapter` from config (`G8`: swap = config edit, zero code edit).
2. `INV-D / discover` — Add `GET {BaseURL}/models` (OpenAI/LM-Studio `/v1/models`) discovery: if `LOCALLLM_MODEL` is unset/`"auto"`, pick the first served id; if set, verify it is in the served list, else degrade (`G6`) with a clear obs error (`completer.go:89` style). The bridge becomes self-describing rather than assuming `"local-model"`.
3. `INV-E` — Sanitize at the **adapter boundary** (`completer.go`, before returning, and/or in `mcp.go` before `TextContent`): strip/escape control chars, enforce a max-bytes cap, mark the payload as untrusted model output. The boundary is the right home (single chokepoint, `G3` SRP) — *not* the agent (that is `N`).
4. Tests: extend `completer_test.go` / `mcp_test.go` (existing) for discovery + sanitize; `go test -race`, golangci-lint, bats must stay green (`mirabilis` bar §"Engineering bar").

INV homes (where the invariant-gene actually lives, registry-M:50): `INV-D` → a contract test asserting no `localllm` constant is read in place of config + a discovery unit test; `INV-E` → a unit test feeding hostile bytes through the adapter and asserting they are neutralized. Until those tests exist, `INV-D/INV-E` are `HYPO` (registry-M:51 "HYPO until landed").

Mission frame: a config-driven, discoverable, sanitized local model = **self-sufficiency** (the ecosystem can run an offline/owned model) + **safety of the truth-channel** (untrusted output can't smuggle claims past `N`'s gates). Behaviour — *when* to offload, *which* prompts — stays in `N` (the `offload` tool is exposed; the policy is not in `M`; G2).

CONFLICT carried from the plan [FACT registry-M:58]: `mirabilis-impl-plan.md` W1 = "auto-offload hook" contradicts `[D5]` (no hook) and fuses caveman↔localLLM. Resolution: do **not** add an auto-offload hook in `M` (that is a behavioural *when*-decision = `N`). W1 here = config + discovery + sanitize only. (Genome already flags this as a gene-mutation for selection, not a code patch — and it is owner-approval-gated.)

---

## 3 — W2 · telegram: detection broadening + delivery retry  [lands INV-F]

```
W2 : G-notify, G-steps, G-secrets        registry-M:41
κ : /workspace/mirabilis/internal/engine/notify/{watcher.go,queue.go,chatid.go,telegram.go}
    /workspace/mirabilis/internal/hooks/{telegram.go,dispatch.go}
    /workspace/mirabilis/internal/engine/steps/telegram.go
INV-F bound IO ¬human-wait (registry-M:54)
```

WHAT: broaden chat detection and make delivery durable, while keeping every wait bounded (no IO blocks a human). Remote presence (owner↔AI off-keyboard) is a mission organ, not a convenience.

State (verify, all FACT):
- Detection is **narrow**: `chatid.go:47` sets `allowed_updates=["channel_post"]` and `:67-72` only reads `channel_post` chat ids ⇒ a **group/supergroup/private** chat is not detected (`ErrNoChannel`, `:18`). Event mapping `dispatch.go:42-50` (`messageFor`) fires only on `Notification` and `Stop` ⇒ no signal for other lifecycle events.
- Delivery has **no retry**: `watcher.go:73-97` (`deliver`) calls `n.Send` once; whether OK or error it writes a `.status` (`queue.go:64`); `PendingJobs` (`queue.go:87-111`) treats *any* job with a `.status` as done. ⇒ a transient `Send` failure is recorded terminal and **never retried**. `JobStatus` (`queue.go:27-32`) has no `Attempts`/`NextRetry` field.
- Already bounded (INV-F partly present): `watcher.go:25` 2s ticker; `:38-44` `recover()`→`StateDegraded` (a panic degrades the node, not the system, `G6/G12`); `telegram.go:38` 15s HTTP client timeout; queue writes atomic (`queue.go:141` temp+rename). ⇒ the watcher is non-blocking; the gap is breadth + retry, not unboundedness.

HOW (Δ):
1. Detection broadening — `chatid.go:47` extend `allowed_updates` to `["channel_post","message","my_chat_member"]`; `:54-72` also parse `message.chat.id` (group/private) and `my_chat_member` (bot-added-to-chat). Keep `ErrNoChannel` semantics for "nothing yet". (`G6`: still degrades cleanly when empty.)
2. Event broadening — `dispatch.go:42-50` add the lifecycle events the owner wants surfaced (e.g. long-tool-start, error) as new `messageFor` cases; text stays in one place (mirror `tui/strings` discipline; emoji exist there already `:45-47`).
3. Delivery retry (bounded) — add `Attempts int` + `NextRetryAt time.Time` to `JobStatus` (`queue.go:27`); on `Send` error write a *retryable* status (not terminal) with backoff; `PendingJobs` (`queue.go:101`) re-selects a job whose status is retryable and `NextRetryAt ≤ now`, until a **max-attempts cap** (config) → then terminal `degraded`. Each attempt still inside the 15s client timeout ⇒ **INV-F preserved** (bounded, no human-wait).
4. Tests: extend `watcher_test.go`, `queue_test.go`, `chatid_test.go`, `hooks/telegram_test.go` (all exist) for new event types + retry/backoff + cap.

INV-F home (registry-M:50): a contract/lint test asserting every notify wait has a deadline and retry is capped (no unbounded loop). `HYPO` until that test lands.

Mission frame: durable, broadly-detected notifications = the owner stays in the loop from anywhere (the `R→N1→S` human path, the R→S audit §2) without the agent ever blocking on delivery. (Telegram detail reprised in communication.md "remote presence".)

---

## 4 — W8 · SearXNG web-search  [new gene G-web; channel into 𝕌]

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

## 5 — W7 · bounded proxy wait + ctx sleep

```
W7 : G-hooksM, G-provision        registry-M:46
κ : /workspace/mirabilis/internal/hooks/{session.go,dispatch.go}
    /workspace/mirabilis/internal/engine/provision/{headroom.go,provision.go}
```

WHAT: ensure the headroom-proxy startup wait is bounded **and context-cancellable** (no goroutine sleeps past a cancel; `mirabilis` "No-hang/no-race" bar).

State (verify, FACT): the proxy poll is **already bounded** — `session.go:78-80` builds `for i in $(seq 1 60); do curl … && exit 0; sleep 1; done; exit 1` with `headroomPollLimit = 60` (`dispatch.go:16`, dup `provision.go:20`); same shape in `provision/headroom.go:123`. ⇒ max ~60s, then fail (not infinite). The wait is a **shell `sleep` inside `bash -lc`**, run via `exec.Run(ctx,…)`.

HOW (Δ, narrow):
1. The remaining gap is **ctx-awareness of the sleep**: a shell `sleep 1` loop does not observe Go `ctx` cancellation between iterations (the outer `exec.Run` ctx governs the *process*, but cancel mid-loop relies on process kill, not a cooperative ctx-sleep). Δ = either (a) move the poll into Go with a `select{ <-ctx.Done(); <-time.After(1s) }` loop (cooperative, `G6`), or (b) keep shell but ensure the ctx kill path is exercised. `HYPO`: exact intent is the plan's "ctx sleep" — (a) is the faithful reading (replace blind sleep with ctx-aware wait).
2. De-duplicate the two constant blocks (`dispatch.go:15-16` vs `provision.go:19-20`) into one home (`G1` no churn / single source). `HYPO` (cleanup, owner-discretion).

Mission frame: robustness of the API chain (`claude → headroom → authproxy → Anthropic`, `mirabilis/CLAUDE.md`) — a node failure degrades its function, not the system (`G6`). Low mission-reach ⇒ mid-order.

---

## 6 — W3 · ghauth host browser + copy

```
W3 : G-sandbox, G-steps, G-tui, G-bus        registry-M:42
κ : /workspace/mirabilis/internal/engine/steps/ghauth.go
```

WHAT: make GitHub sign-in open the device URL **on the host browser** and **copy the user code**, so the owner doesn't hand-shuttle the code (UX + bounded interactive wait).

State (verify, FACT): `ghauth.go:19-27` runs `gh auth login … --web` **inside the container** with `BROWSER=true` (a container has no host browser). `:14-17` parse the device code (`ABCD-1234`) and `…/login/device` URL via regex; `:79-82` emit `EvWaiting{code,url}` to the TUI. ⇒ the code+URL are captured; the host-side open + clipboard copy are the missing affordances.

HOW (Δ): on `EvWaiting`, host-side open the URL (`open`/`xdg-open`/`start`, mirror the VS-Code resolver pattern in `sandbox/vscode.go:32-51`) and copy the code to the host clipboard; surface in `tui` via `bus`. Keep the interactive wait bounded (`steps` already uses ctx-cancel, `ghauth.go:50-88`). `HYPO` (UX Δ, not yet coded).

Mission frame: lower owner friction at the one mandatory interactive step. Bounded reach.

---

## 7 — W6 · lint + arch-lint into the image

```
W6 : .devcontainer/Dockerfile        registry-M:45
κ : /workspace/mirabilis/.devcontainer/Dockerfile ; .golangci.yml ; .go-arch-lint.yml
```

WHAT: bake `golangci-lint` + `go-arch-lint` into the dev image so the agent can run the *same* gates the CI enforces, in-sandbox (reproducibility, `mirabilis` "Code-is-truth / not-green-not-done").

State (verify, FACT): the Dockerfile installs `rtk, uv, go, dotnet(opt), ripgrep, …` (`.devcontainer/Dockerfile`) but **not** `golangci-lint` or `go-arch-lint` (grep: `NO_LINT_IN_IMAGE`). The configs exist (`.golangci.yml` 3.4K, `.go-arch-lint.yml` 2.9K at repo root). ⇒ the agent inside the box can't run the gates without ad-hoc install.

HOW (Δ): add SHA-pinned installs of both tools to the second stage of `.devcontainer/Dockerfile` (mirror the rtk/uv/go pinning blocks already there, `--retry`, checksum-verify). `HYPO` (Dockerfile Δ).

Mission frame: in-sandbox parity with CI = the agent can self-verify (self-sufficiency + evolvability — a tighter `R→S` for `M` itself). Build-hygiene reach ⇒ lower-mid.

---

## 8 — W5 · vscode open "/"

```
W5 : G-sandbox        registry-M:44
κ : /workspace/mirabilis/internal/engine/sandbox/vscode.go:29
```

WHAT: open VS Code at the repo/workspace root the owner intends.

State (verify, FACT): `vscode.go:29` opens `vscode-remote://attached-container+<enc>/workspace` — i.e. `/workspace`, not `/`. The plan item says open "/". `Q`: is "/" actually wanted, or is "/workspace" (the owned named volume per `mirabilis/CLAUDE.md`) correct? This reads as a one-token path change; surface to owner before flipping (invariant #16 ambiguity → ask).

HOW (Δ): change the folder-uri suffix in `vscode.go:29` if the owner confirms "/" over "/workspace". `HYPO` + `Q`. Minimal reach.

---

## 9 — W4 · attach: remove standalone

```
W4 : G-steps, G-tui        registry-M:43
κ : /workspace/mirabilis/internal/engine/steps/attach.go
```

WHAT: remove the standalone attach step if it is redundant with the launch/attach path.

State (verify, FACT): `attach.go:13-43` is a `pipeline.Terminal` step (`Check`→`false` always, `:26-28`) emitting `EvWaiting{argv,env}`; `AttachExec` (`:45-54`) builds the attach argv with a gh token. A separate attach also exists in `sandbox/attach.go`. ⇒ candidate duplication. `HYPO`: "standalone" = the steps-level one; confirm it is dead before deleting (`I11` no dead code; PR-diff review is its mechanical home).

HOW (Δ): delete the standalone step + its wiring + tests once confirmed unused (`G1` no churn, pure subtraction). Lowest leverage (cleanup) ⇒ last.

---

## 10 — W9 · cross-cluster back navigation  [eng-choice; deferred from #131]

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

## 11 — W10 · adaptive overlay form sizing  [eng-choice; deferred from #131]

```
W10 : G-tui, G-bus, G-router        registry-M (work-item list)
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

## M invariant-genes (the homes that make a Δ "landed")

```
INV-D  config/discover ¬hardcode    lands W1   home: contract-test (no localllm const read in place of config) + discovery unit
INV-E  sanitize external-model out  lands W1   home: unit feeding hostile bytes through the adapter boundary
INV-F  bound IO ¬human-wait         lands W2   home: contract/lint — every notify wait has a deadline and retry is capped
status: each of {INV-D, INV-E, INV-F} stays HYPO until its home (lint / contract-test / CI) exists   [registry-M:51]
```
An invariant is *landed* exactly when it has a mechanical home (a lint rule, a contract test, or a CI check) and that home is green. Prose in this file identifies the home; the home is what enforces it (mirror `mirabilis/CLAUDE.md` Invariants table discipline). An invariant without a passing home is a wish, not a gene.

---

## §Ledger (epistemic, this file)

```
FACT (file:line / repo / issue):
  caveman ∈ catalog: config/skills.txt:2 ; test/token_opt.bats
  caveman mechanism: JuliusBrussee/caveman README+INSTALL (skill+hook+caveman-compress+opt-in MCP)
  localllm constants hardcoded: config/config.go:20-24 ; raw output: completer.go:112, mcp.go:33 ; no /v1/models in localllm/
  localllm edge documented intentional+hardcoded: mirabilis/CLAUDE.md (Boundaries)
  notify narrow detect: chatid.go:47,67-72 ; events Notification/Stop only: dispatch.go:42-50
  notify no retry: watcher.go:73-97 + queue.go:64,87-111 ; JobStatus has no Attempts: queue.go:27-32
  notify already bounded: watcher.go:25,38-44 ; telegram.go:38 (15s)
  proxy wait bounded: session.go:78-80, dispatch.go:16 (headroomPollLimit=60), provision/headroom.go:123
  ghauth in-container --web + device-code parse: steps/ghauth.go:14-27,79-82
  vscode opens /workspace not /: sandbox/vscode.go:29
  attach standalone Terminal step exists: steps/attach.go:13-54 (also sandbox/attach.go)
  lint NOT in image: .devcontainer/Dockerfile (grep NO_LINT_IN_IMAGE) ; configs exist .golangci.yml/.go-arch-lint.yml
ASSOC:
  leverage ordering (mission-reach × organ-Δ / cost) = owner-lens application of G0
HYPO:
  G-cav not-wired (catalog-only; no per-tool provision step / session-flag)
  W1 is a deliberate design change (must update mirabilis/CLAUDE.md hardcoded-edge paragraph) — owner-approval gated
  every Wi Δ below "state" is a plan, not landed code; INV-D/E/F HYPO until homes green
  W7 "ctx sleep" = replace shell sleep with Go ctx-aware wait (faithful reading)
Q:
  pin caveman by release/SHA? (no SHA-pin path for marketplace skills today)
  W5: open "/" vs "/workspace" — confirm with owner
  W4: which "attach" is the dead standalone (steps vs sandbox) — confirm before delete
```
