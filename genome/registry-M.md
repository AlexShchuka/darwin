# 𝒢|M — genes of the coral (mirabilis, mechanism phenotype)

Anchor: `/workspace/mirabilis` (live git, ≈9.6k LoC Go). `package ≡ gene`. existence = FACT (listing + package-doc read); role = FACT where read, ASSOC where name-only. `α_N = ⊥` by default (mechanism ≠ behaviour). Schema: §B GENOME.
home vs grounding (§B discipline): `κ` points are `home` — WHERE a gene lives (code path). They are mechanical and may rot. `grounding` = WHY the gene holds: the scientific source in Λ or a §0 root. Validity comes from grounding, never from κ. Engineering-convention genes without a Λ/§0 root carry [eng-choice], not FACT-grounded.

## Anatomy (package = gene)
```
G-authproxy  FACT  α_M: HTTP proxy injects Anthropic headers host-side; real token never enters container;
                        per-session key; constant-time compare   →security ⊣G-obs  κ:engine/authproxy/authproxy.go   [SECURITY]
G-harness    FACT  α_M: install-actions + probe-scripts; installs harness N INTO M (InstallActions, StartMarkerHash)
                        →M↔N coupling: expresses N into env(M)  κ:engine/harness/harness.go   [wiring gene: mechanical install, ¬asymmetric life-dependence (§A.6/§F)]
G-membackup  FACT  α_M: syncs ~/.claude memory container→host-repo (Save)  →knowledge persistence  κ:engine/membackup/membackup.go   [allele of G-know]
G-obs        FACT  α_M: thread-safe observable state-map of subsystem health + slog single sink  →observability(G5)  κ:internal/obs/obs.go   [allele of G-obs+]
G-config     FACT  α_M: G4 tunables (LocalLLM*, Sock…)  κ:engine/config/config.go
G-exec       FACT  α_M: Runner port — sole os/exec home (forbidigo)  κ:engine/exec
G-localllm   FACT  α_M: bridge + local-offload MCP (155 LoC)  κ:engine/localllm   [= quartet G-loc]
G-notify     FACT  α_M: telegram delivery (watcher, status)  κ:engine/notify
G-pipeline   FACT  α_M: provision DAG (failedDep, stateSkipped, emit)  κ:engine/pipeline
G-provision  FACT  α_M: provision steps (rtk, headroom, settingsenv, localllm, carry)  κ:engine/provision
G-sandbox    FACT  α_M: docker / vscode / attach / host-IO (OpenVSCode)  κ:engine/sandbox
G-secrets    FACT  α_M: FileStore(Linux)/keychain(macOS); .mirabilis-* tokens  κ:engine/secrets
G-claudeauth FACT  α_M: claude auth chain  κ:engine/claudeauth   [role ASSOC]
G-status     FACT  α_M: provision status  κ:engine/status   [role ASSOC]
G-steps      FACT  α_M: pipeline steps (telegram, ghauth, launch, attach)  κ:engine/steps
G-hooksM     FACT  α_M: session hooks — RTK/headroom/session-start  κ:internal/hooks
G-bus        FACT  α_M: event bus (tui msgs)  κ:internal/bus
G-tui        FACT  α_M: TUI (app/screens/router/strings/styles/components/frame/a11y)  κ:internal/tui
```

## Compression-quartet alleles in M
```
G-rtk  α_M: provision rtk-config + PreToolUse hook install   κ:~/.claude/settings.json
G-hed  α_M: provision headroom (ANTHROPIC_BASE_URL→:8787)     κ:engine/provision/headroom.go
G-cav  α_M: catalog-present — config/skills.txt + test/token_opt.bats [FACT]; gap = per-tool provision-step / session-flag wiring [HYPO]   (earlier "∉ M, grep ∅" was FALSE — grep excluded .txt)
G-loc  = G-localllm
channel-disjoint(tool-out, API-window, agent-out, ∅) ⇒ ¬duplication   [FACT]
```

## Work-item mutations (Δ on these genes, ¬new organs)
```
W1–W7 LANDED — mirabilis PR#134 (expressed in the genes; the plan-Δ is applied):
  W1 localllm config + /v1/models discovery + Sanitize (wired into offload MCP)  → G-localllm,G-config   [INV-D,INV-E]
  W2 telegram detect-broaden + progress + 4xx-permanent capped-retry             → G-notify,G-steps,G-secrets   [INV-F]
  W3 ghauth host browser-open + device-code copy (OSC52 + shell-out)             → G-sandbox,G-steps,G-tui,G-bus
  W4 attach standalone removed                                                   → G-steps,G-tui
  W5 vscode open "/"                                                             → G-sandbox
  W6 full toolchain into image + dependabot integrity (4 light tools→go.mod tool directives; golangci-lint→install.sh)  → .devcontainer/Dockerfile,G-config
  W7 bounded proxy wait + ctx-aware sleep                                        → G-hooksM,G-provision
  off-plan (same PR): onboarding/trust/theme suppression (~/.claude.json seed)   → G-provision ; copy-feedback honesty → G-tui
OPEN plan:
  W8 SearXNG websearch (new gene)        → G-websearch,G-config,compose
  W9 cross-cluster back-nav (rewindable FSM / front-load)  → G-pipeline,G-steps,G-tui   [eng-choice/HYPO; deferred mirabilis#132-L1]
  W10 adaptive overlay form sizing on push  → G-tui,G-bus   [eng-choice/HYPO; deferred mirabilis#132-L2]
```

## M invariant-genes (LANDED mirabilis PR#134 — homes green)
```
INV-D  config/discover ¬hardcode   home: localllm env-overridable config + /v1/models discovery + completer/config tests   [owner approved the design-reversal via the W1–W7 iteration; CONFLICT-2 resolved]
INV-E  sanitize external-model out  home: SanitizeOutput + table test + mcp_test (offload tool sanitizes at the boundary)
INV-F  bound IO ¬human-wait         home: notify 4xx-permanent + capped-retry tests; Configure bounded (¬the human-input wait)
```

## Ledger
FACT: all packages exist (listing) + package-doc read for authproxy/harness/membackup/obs/localllm. caveman ∈ M (config/skills.txt + test/token_opt.bats) — earlier "grep ∅" was a FALSE FACT (grep excluded .txt); CORRECTED. ASSOC: role of claudeauth/status (name-only).
CONFLICT-1 RESOLVED (PR#134): W1 landed integration-only — NO auto-offload hook (D5/D6 honored); caveman↔localLLM stay distinct alleles (§H quartet, channel-disjoint).
CONFLICT-2 RESOLVED (PR#134) [#30]: the owner approved the W1–W7 iteration ⇒ the config-driven design-reversal is accepted; the localllm constants are now env-overridable with the prior hardcoded values as defaults, and SanitizeOutput crosses the model-output trust boundary. FOLLOW-UP (mirabilis doc, ¬genome): AGENTS.md "intentional and hardcoded" wording is now stale (config-driven default) — fix in a mirabilis doc pass.
ROT-HYGIENE (iter-2): volatile `:line` suffixes stripped from κ package-homes in THIS registry (the package is the home; the line rots — §B). NOT cleaned here (deferred): PR-status provenance — e.g. the `PR#134` landing-refs above belong in archive Provenance — and the ~85 file:line refs across DEPT plans. NB `[#30]` etc. are stable invariant-ids, not issue numbers (archive Provenance). Plans are file-actionable *by design*, so whether plan-homes count as rot is an owner call, not assumed here.
