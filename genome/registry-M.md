# 𝒢|M — genes of the coral (mirabilis, mechanism phenotype)

Anchor: `/workspace/mirabilis` (live git, ≈9.6k LoC Go). `package ≡ gene`. existence = FACT (listing + package-doc read); role = FACT where read, ASSOC where name-only. `α_N = ⊥` by default (mechanism ≠ behaviour). Schema: §B GENOME.
home vs grounding (§B discipline): `κ` points are `home` — WHERE a gene lives (code path). They are mechanical and may rot. `grounding` = WHY the gene holds: the scientific source in Λ or a §0 root. Validity comes from grounding, never from κ. Engineering-convention genes without a Λ/§0 root carry [eng-choice], not FACT-grounded.

## Anatomy (package = gene)
```
G-authproxy  FACT  α_M: HTTP proxy injects Anthropic headers host-side; real token never enters container;
                        per-session key; constant-time compare   →security ⊣G-obs  κ:engine/authproxy/authproxy.go:1   [SECURITY]
G-harness    FACT  α_M: install-actions + probe-scripts; installs harness N INTO M (InstallActions, StartMarkerHash)
                        →M↔N coupling: expresses N into env(M)  κ:engine/harness/harness.go:1   [wiring gene: mechanical install, ¬asymmetric life-dependence (§A.6/§F)]
G-membackup  FACT  α_M: syncs ~/.claude memory container→host-repo (Save)  →knowledge persistence  κ:engine/membackup/membackup.go:1   [allele of G-know]
G-obs        FACT  α_M: thread-safe observable state-map of subsystem health + slog single sink  →observability(G5)  κ:internal/obs/obs.go:1   [allele of G-obs+]
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
G-rtk  α_M: provision rtk-config + PreToolUse hook install   κ:~/.claude/settings.json:39
G-hed  α_M: provision headroom (ANTHROPIC_BASE_URL→:8787)     κ:engine/provision/headroom.go:62
G-cav  α_M: catalog-present — config/skills.txt:2 + test/token_opt.bats:31 [FACT]; gap = per-tool provision-step / session-flag wiring [HYPO]   (earlier "∉ M, grep ∅" was FALSE — grep excluded .txt)
G-loc  = G-localllm
channel-disjoint(tool-out, API-window, agent-out, ∅) ⇒ ¬duplication   [FACT]
```

## Work-item mutations (plan = Δ on these genes, ¬new organs)
```
W1 localllm config+discovery+Sanitize → G-localllm,G-config   [INV-D,INV-E]
W2 telegram detect+feedback+retry      → G-notify,G-steps,G-secrets   [INV-F]
W3 ghauth host browser+copy            → G-sandbox,G-steps,G-tui,G-bus
W4 attach remove standalone            → G-steps,G-tui
W5 vscode open "/"                      → G-sandbox
W6 lint+arch-lint into image           → .devcontainer/Dockerfile
W7 bounded proxy wait + ctx sleep      → G-hooksM,G-provision
W8 SearXNG websearch (new gene)        → G-websearch,G-config,compose
W9 cross-cluster back-nav (rewindable FSM / front-load)  → G-pipeline,G-steps,G-tui   [eng-choice/HYPO; deferred mirabilis#132-L1]
W10 adaptive overlay form sizing on push  → G-tui,G-bus   [eng-choice/HYPO; deferred mirabilis#132-L2]
```

## M invariant-genes (plan node 50; HYPO until landed; home = lint/contract-test/CI)
```
INV-D  config/discover ¬hardcode   lands W1   [#30: overrides intentional-hardcode mirabilis/CLAUDE.md:23-26 → owner-gated; real lever = model-id discovery, F4]
INV-E  sanitize external-model out  lands W1
INV-F  bound IO ¬human-wait         lands W2
```

## Ledger
FACT: all packages exist (listing) + package-doc read for authproxy/harness/membackup/obs/localllm. caveman ∈ M (config/skills.txt:2 + test/token_opt.bats:31) — earlier "grep ∅" was a FALSE FACT (grep excluded .txt); CORRECTED. ASSOC: role of claudeauth/status (name-only).
CONFLICT-1: `mirabilis-impl-plan.md` W1="auto-offload hook" contradicts `[D5]` (no hook) + fused genes caveman↔localLLM → gene-mutation for selection.
CONFLICT-2 [#30]: INV-D/W1 "config-driven, ¬hardcode" contradicts a RECORDED decision — mirabilis/CLAUDE.md:23-26 "This edge is intentional and hardcoded to http://host.docker.internal:1234/v1"; config.go:20-23 are compile-time const ⇒ W1 = design-reversal, owner-approval-gated; reopening needs new evidence (model-id "local-model" ≠ loaded-model, plan F4). Do not patch code under this conflict — it is owner-gated.
