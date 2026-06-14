# Vec · v-plan — Fix-graph (sandbox plan-graph condensed)

Type: this is a Vec entry — transient, not truth, neither a gene 𝒢 nor an archive entry Λ (vectors.md §Type). Source [FACT]: /workspace/plan/*.md — a 17-node graph-structured implementation plan for the mirabilis SANDBOX (¬the harness); an INDEX plus nodes 00–90. State: SUPERSEDED BY THE GENOME — this is an OLDER sandbox-only plan; the four-strata Γ-genome (GENOME.md) is the current model. It is kept for traceability of the work-items and as the carrier of two flagged defects (§D below): the caveman MISIDENTIFICATION and the W1↔D5 CONFLICT. Scope: plan-only by owner directive [FACT, plan/02-decisions.md:8 P1] — the plan itself states "Development is cancelled; deliverable is the plan", and no code was written. Boundary [FACT, plan/00-system.md:8-11 G2]: sandbox (mirabilis) = MECHANISM (provisioning, autonomy plumbing); harness (neuro-matrix) = BEHAVIOUR. Every node builds mechanism; "use X to judge/decide" = harness, out-of-scope.
`v-plan` = the pre-genome sandbox roadmap. Graph (¬one file): 00–02 frame · 10 module · 20–27 work-item leaves W1–W8 · 30 verification · 40 research · 50 invariants · 90 open. Each leaf: problem→anchor · design · files · arch/lint/test impact · verification · risk · links.

## §W — Work-items W1–W8 (problem → fix, one line each) [FACT, plan/2x-*.md]
```
W1 local-LLM integration [20]   PROBLEM model id hardcoded "local-model" (F4), output verbatim leaks <turn|> + loops (F5), tunables not config (F1)
                                FIX W1a config-driven + GET /v1/models discovery · W1b a separate Sanitize() (keep Complete verbatim contract) · W1c LocalLLM* → config. MECHANISM only; uses deferred. ⚠ see §D-2 (W1↔D5).
W2 telegram [21]                PROBLEM "waiting" hang (Configure unbounded, no progress, no Meta.Timeout — F7b) · detection too narrow (allowed_updates=["channel_post"],limit=1 — F8) · no delivery retry (F9)
                                FIX broaden detection (my_chat_member+channel_post+message, limit 100, take first type=="channel") · emit progress + bound ONLY the Configure call (¬Meta.Timeout, which would kill the human-input wait) · transient-vs-permanent retry
W3 github-login UX [22]         PROBLEM device-flow runs in-container w/ browser-open neutralized; no auto-open, no copy affordance (F10); host-IO must sit in engine behind facade (F11)
                                FIX engine OpenURL (per-GOOS open/xdg-open/wslview via Runner, honour $BROWSER) · OSC-52 copy primary + shell-out fallback (pbcopy/clip.exe/xclip/xsel) · wire facade→tui/app as tea.Cmd; G6 degrade to manual display
W4 attach removal [23]          PROBLEM standalone `attach` menu action duplicates launch's destination — both → identical `docker exec -it mirabilis claude …` (F12); two routes to one dest violate G1
                                FIX delete the standalone TUI path + its strings/handlers/facade entry; keep the terminal attachStep (single funnel). Pure TUI deletion; engine untouched
W5 vscode root [24]             PROBLEM "Open in VS Code" opens /workspace only (vscode.go:29) (F13); owner wants container root /
                                FIX change folder-uri suffix /workspace → / (optional G4 config tunable, default /)
W6 tooling-in-image [25]        PROBLEM CI runs golangci-lint v2.12.2 + go-arch-lint v1.15.0 but neither is in the Dockerfile → in-container agent can't run the gates locally (F14,F17)
                                FIX extend the `go install …@version` block with both, pinned, before `go clean -modcache`; comment-free (no-config-comments)
W7 safe core-fixes [26]         PROBLEM unbounded session-start proxy wait (session.go:19) · non-ctx-aware time.Sleep (headroom.go:54)
                                FIX W7a context.WithTimeout(≥75s, above the 60s poll budget) · W7b select{<-time.After:<-ctx.Done()}. W7c (failedDep ignores stateSkipped) DEFERRED→90. Two subagent "criticals" EXCLUDED as FALSE (F16).
W8 web-search SearXNG [27]      PROBLEM no sovereign grounding/web-search subsystem; metered WebSearch only
                                FIX optional `searxng` compose service (mirror SOCK toggle) + a `search` MCP (V-A in-repo Go recommended vs V-B external uvx). settings.yml needs formats:[html,json]+limiter:false (else 403, F21a). MECHANISM only; triage=harness.
```

## §F — Key facts F-* (pointers, ¬full text; full at plan/01-facts.md) [FACT]
```
F1  trio = 3 independent layers live in-container : RTK PreToolUse hook + headroom proxy :8787 (ANTHROPIC_BASE_URL) + local-offload MCP → host.docker.internal:1234/v1.  "caveman" string appears NOWHERE in code/docs/config — only in the caveman commit-title.  ⟵ load-bearing for §D-1.
F2  real Anthropic token never enters the container : per-session 64-hex key; authproxy injects the real Bearer host-side (I1 holds).
F3  headroom started `--mode cache` hardcoded; live stats: compression $0, only prefix caching; no mode knob (G4 gap).
F4  local-LLM model id hardcoded "local-model" ≠ real LM Studio id; works only by LM Studio's loaded-model fallback.  ⟵ W1a.
F5  local-LLM returns model text verbatim, no sanitization; live leaked <turn|> artifacts + looped.  ⟵ W1b.
F6  hooks (official docs) : PostToolUse CAN replace tool OUTPUT (updatedToolOutput); PreToolUse rewrites INPUT; NO hook can offload/replace the MAIN MODEL'S REASONING.  ⟵ load-bearing for §D-1 (a hook can compress output, not "be a brain").
F7/F7b/F8/F8-verified/F9  telegram host-side; hang = Configure blocks after awaitResume w/ no event/timeout; detection narrow; admin-add emits my_chat_member carrying the channel id; getUpdates retains ~24h; webhook→409.  ⟵ W2.
F10/F11  gh device-flow in-container w/ browser neutralized; host-IO via engine behind facade (forbidigo bans os/exec outside engine/exec; tui/app exempt fs+http only, NOT exec). precedent OpenVSCode.  ⟵ W3.
F12  attach redundant — standalone menu item + terminal step both → identical docker exec; all removal-target symbols enumerated.  ⟵ W4.
F13/F14  VS Code opens /workspace; Dockerfile bakes Go tools, comment-free.  ⟵ W5/W6.
F15  arch-lint allowed edges enumerated; any new cross-pkg edge must be declared in .go-arch-lint.yml.
F16  two subagent "critical" bugs FALSE on read-back (no race on pipeline.p.done; startSession once/process) ⇒ anchor every borrowed claim.  ⟵ INV-C / W7 exclusions.
F17  CI bar : go test -race -tags integration; coverage floor 87 (excl cmd/mirabilis); golangci-lint v2.12.2; go-arch-lint v1.15.0; actionlint/gitleaks/no-config-comments/image-build/bats. AGENTS.md "floor 86" is STALE; CI=87 authoritative.
F19  CAVEMAN-labelled item works end-to-end LIVE : container reached host.docker.internal:1234/v1/models (200) + offload round-tripped once LM Studio was up.  ⚠ NB the thing tested is the local-LLM offload bridge, NOT a tool named caveman — see §D-1.
F20  RTK seed config IS applied (live config.toml == seed); `rtk init` writes a different file filters.toml; no step-ordering bug.
F21a/b/c  SearXNG JSON API needs formats:[html,json]+limiter:false (else 403); public instances disable JSON → self-host; token-conscious MCP wrappers already exist; reachable as compose sidecar at http://searxng:8080.  ⟵ W8.
```

## §D — Decisions D-* (pointers; full at plan/02-decisions.md) [FACT]
```
P1 session=plan ¬code · P2 plan is a graph · P3 pipeline research→AskMe→deep-research→critic→plan · P4 source-of-truth = reality, anchor every claim, verify subagents (F16).
A1 sandbox≠harness strictly — build MECHANISM only · A2 Caveman NOT dropped (see §D-1 — this is the MISIDENTIFIED decision) · A3 modules replaceable+config-driven ("modules as genes") · A4 info-density is an acceptance criterion.
D1 VS Code opens / · D2 add golangci-lint+go-arch-lint to image · D3 apply all minor stabilizers · D4 coverage floor 87 · D5 NO offload-compression PostToolUse hook in this PR (see §D-2 — the CONFLICT) · D6 W1 = integrate the module, ¬build its uses · D7 attach V1 removal.
D8 telegram: bound only the Configure call, ¬Meta.Timeout · D9 broaden chat-id detection · D10 browser/clipboard on the host in engine behind facade · D11 adopt SearXNG as an optional mechanism module (token-saving conditional on token-conscious output; ¬a duplicate of RTK/headroom).
```

## §50 — Invariants the plan surfaced (formalize → mechanical home) [FACT, plan/50-invariants.md]
```
INV-A harness  ecosystem-mission framing, ¬local metric (token/$)        home invariants.txt+self-check hook   — ⟵ the framing whose ABSENCE produced §D-1 (Caveman reduced to a local token-metric)
INV-B harness+sandbox  new module = MECHANISM, ¬behaviour                home invariants.txt + robust-by-construction
INV-C harness  anchor borrowed (subagent/owner) claims before they land   home extend invariant #4 + critic gate          — ⟵ F16; same instinct as GENOME §J read-before-act
INV-D sandbox  integration params config-driven/discovered, ¬hardcoded    home contract test + lint             — lands w/ W1a
INV-E sandbox  external-model output sanitized at the boundary            home Sanitize() + table test         — lands w/ W1b
INV-F sandbox  bound IO, ¬the human-input wait                           home pipeline contract test          — lands w/ W2
note : these are the plan's genuine evolutionary output; several converge with the genome's own laws (INV-C ≅ GENOME §J read-before-act; INV-A ≅ GENOME §A.2 getting the initial invariant set right). [ASSOC]
```

## §D-1 — FLAGGED: the caveman MISIDENTIFICATION [FACT — defect in this plan]
```
plan-claim [FACT, plan/10-module-token-economy.md:11-22, plan/02-decisions.md:15 A2, plan/40-research.md:10-13 R2] :
   the plan casts "Caveman / local-LLM" as ONE node = the SEMANTIC · model-powered tier of the token-economy trio —
   "role-specialized lossy semantic work the mechanical tiers cannot do … CODEMAP-style skeleton, small-model localization/triage" (10:15);
   A2 "Caveman integrates as the SEMANTIC tier that does what the mechanical tiers cannot" ;
   R2 grounds it on arXiv:2604.07502 (program-skeleton) + arXiv:2604.03515 (multi-model routing).
   ⇒ the plan CONFLATES the caveman tool with the local-LLM offload module and builds a theory of a "semantic local-LLM tier" around the name.
reality [FACT, github.com/juliusbrussee/caveman, fetched 2026-06-14] :
   caveman = an OUTPUT-STYLE COMPRESSOR — a Claude-Code (and 30+ agents) skill/plugin that instructs the agent to REPLY in terse "caveman" prose,
   dropping filler while keeping technical accuracy, cutting ~65–75% of OUTPUT tokens. Self-description: "Caveman no make brain smaller. Caveman make MOUTH smaller."
   It touches OUTPUT tokens only; reasoning/thinking untouched. It is NOT a local LLM, NOT a semantic model-tier, NOT CODEMAP/routing.
internal corroboration [FACT] : the plan's OWN F1 (01-facts.md:8) records "'caveman' string appears NOWHERE in code/docs/config — only in the caveman commit-title" ;
   F6 (01-facts.md:17) records "NO hook can offload/replace the main model's reasoning" (a PostToolUse hook can only rewrite OUTPUT) — exactly caveman's real lane ;
   F19's live test exercised the local-LLM OFFLOAD bridge (host.docker.internal:1234/v1), NOT any tool called caveman.
∴ misidentification = caveman (an output-style compressor, a 4th mechanical-output lane) was mistaken for the local-LLM SEMANTIC tier.
   correct placement [ASSOC, derived] : caveman ∈ output-token compression (alongside RTK's bash-boundary filtering / headroom's window caching), NOT the local-offload semantic node.
   the genome already separates these correctly : GENOME §H "compression quartet (RTK·headroom·caveman·localLLM)" — caveman ≠ localLLM, listed as DISTINCT, channels disjoint. ⇐ the genome FIXED this; the plan carries the old error.
status : DEFECT IN v-plan, superseded. recorded, not propagated. Do NOT carry the "semantic local-LLM = Caveman" framing into 𝒢.
```

## §D-2 — FLAGGED: the W1 ↔ D5 CONFLICT [FACT — internal tension in this plan]
```
W1 [FACT, plan/20-w-localllm.md] : integrate the local-LLM OFFLOAD module — config-driven model + /v1/models discovery + Sanitize(); the `local-offload` MCP stays the exposed surface. "auto-offload" capability of work to the local model.
D5 [FACT, plan/02-decisions.md:24] : "NO offload-compression PostToolUse hook in this PR. It would duplicate RTK (output filtering) + headroom (caching) at the mechanical level."
the tension [the flagged CONFLICT] :
   W1 builds/keeps the offload SURFACE (the local-offload MCP, an auto-offload path to the local model) ;
   D5 forbids the offload-compression HOOK (an auto-PostToolUse that would route tool-output to the local model to compress it).
   ⇒ surface description, when read loosely, reads as "auto-offload exists" (W1) AND "no auto-offload hook" (D5) — an apparent contradiction on whether offload is in or out.
plan's own reconciliation [FACT, A2 + D6] : the plan TRIES to resolve it — W1/D6 = "integrate the module (mechanism), ¬build its USES"; D5 = the specific USE "a mechanical re-filter hook" is the duplicate that's barred; A2 = caveman's value is "semantic, ¬re-filtering."
   BUT that reconciliation RESTS ON §D-1's misidentification : it assumes a clean split "local-LLM = semantic (keep) vs caveman-as-mechanical-hook (drop)". Once caveman is correctly an output-style compressor (§D-1), the "semantic vs mechanical" line that D5 leans on is mis-drawn ⇒ the W1/D5 boundary is not as crisp as the plan asserts.
residue [HYPO] : whether an auto-offload hook should exist at all is left "a future harness/usage decision, deferred" (D5) — i.e. the conflict is PARKED, not closed. In genome terms this is a §D R→S question (does the offload earn its cost?) answerable only by measurement, which the plan defers.
status : recorded as an unresolved tension of v-plan. Superseded — the genome routes offload uses to the harness (GENOME §J) and the quartet placement to §H, dissolving the framing rather than adjudicating the hook.
```

## §I — Ledger (this entry)
```
FACT  : plan/* exists (17 nodes); W1–W8, F-*, D-*, INV-* as anchored above; F1 "caveman string nowhere but the caveman commit-title"; caveman=output-style compressor (github.com/juliusbrussee/caveman, fetched); the genome lists caveman≠localLLM (§H).
ASSOC : the plan's research anchors (arXiv:2604.07502, 2604.03515 — the plan ITSELF flags these as deep-research-reported, not re-fetched, single-author preprint for 07502); the "correct placement of caveman in the compression quartet" is derived, not separately sourced.
HYPO  : that any plan work-item, if implemented, yields the claimed capability gain (untested — plan-only); whether an auto-offload hook should exist (D5-parked, an R→S question).
Q     : did any W1–W8 land after this plan? not verified here — the plan is explicitly plan-only and is now superseded; current state lives in the genome + repo, not this stratum.
transient + superseded : the whole entry — superseded by GENOME.md (four strata). Once v-plan is implemented, discard it; discarding it does not force a rebuild of GENOME. It carries §D-1 + §D-2 as recorded defects, NOT to be propagated into 𝒢.
```
