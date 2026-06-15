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
G-config     FACT  α_M: G4 tunables (LocalLLM*, Sock…, HEADROOM_MODE config-gated)  κ:engine/config/config.go
G-exec       FACT  α_M: Runner port — sole os/exec home (forbidigo)  κ:engine/exec
G-localllm   FACT  α_M: bridge + local-offload MCP  κ:engine/localllm   [= quartet G-loc]
G-notify     FACT  α_M: telegram delivery (watcher, status)  κ:engine/notify
G-pipeline   FACT  α_M: provision DAG (failedDep, stateSkipped, emit)  κ:engine/pipeline
G-provision  FACT  α_M: provision steps (rtk, headroom, settingsenv, localllm, carry)  κ:engine/provision
G-sandbox    FACT  α_M: docker / vscode / attach / host-IO (OpenVSCode); SystemPromptFile FOL-rendered from config.go single-source  κ:engine/sandbox
G-secrets    FACT  α_M: FileStore(Linux)/keychain(macOS); .mirabilis-* tokens  κ:engine/secrets
G-claudeauth FACT  α_M: claude auth chain  κ:engine/claudeauth   [role ASSOC]
G-status     FACT  α_M: provision status  κ:engine/status   [role ASSOC]
G-steps      FACT  α_M: pipeline steps (telegram, ghauth, launch, attach)  κ:engine/steps
G-hooksM     FACT  α_M: session hooks — RTK/headroom/session-start/credential-authority  κ:internal/hooks
              sub-gene: credential-authority — gh auth setup-git in SessionStart (idempotent, best-effort; sandbox owns git-credential independent of side VS Code attach) [HYPO landed-pending PR#135]
G-bus        FACT  α_M: event bus (tui msgs)  κ:internal/bus
G-tui        FACT  α_M: TUI (app/screens/router/strings/styles/components/frame/a11y)  κ:internal/tui
G-serve      HYPO  α_M: sub-gene of G-sandbox/G-authproxy; single-instance proxy+notify daemon
              serve lifecycle: `mirabilis serve` runs proxy+notify detached, flock-guarded (single-instance);
              TUI writes pidfile to .mirabilis/clients/<pid>.pid on startup, removes on exit;
              reap loop polls every 5s; self-exits 30s after last live client (ref-count I5);
              crash-exited TUI: dead PID detected via kill -0, stale pidfile removed;
              token-active worst-case window after crash: 5s poll + 30s grace = 35s.
              all TUI instances are equal clients (owner/secondary/flock-role/promote removed).
              [HYPO landed-pending PR#135; old multi-instance model removed]
```

## Compression-quartet alleles in M
```
G-rtk  α_M: provision rtk-config + PreToolUse hook install   κ:~/.claude/settings.json
G-hed  α_M: provision headroom (ANTHROPIC_BASE_URL→:8787); HEADROOM_MODE config-gated (G4) — allowlist {cache,token}, default cache; cache=lossless prefix-align, token=lossy CCR (trade-off: breaks prefix-cache)   κ:engine/provision/headroom.go  [HYPO landed-pending PR#135 — config knob new]
G-cav  α_M: wired via plugin catalog (marketplace+install) — caveman@caveman in plugins.txt + JuliusBrussee/caveman in marketplaces.txt; dead skills.txt git-clone removed; pluginsStep installs it each provision   [HYPO landed-pending PR#135; old "catalog-only, not wired" RESOLVED]
G-loc  = G-localllm
channel-disjoint(tool-out, API-window, agent-out, ∅) ⇒ ¬duplication   [FACT]
```

## Work-item mutations (Δ on these genes, ¬new organs)
```
W1–W7 LANDED — expressed in genes (the iteration that produced PR#134):
  W1 localllm config + /v1/models discovery + Sanitize (wired into offload MCP)  → G-localllm,G-config   [INV-D,INV-E]
  W2 telegram detect-broaden + progress + 4xx-permanent capped-retry             → G-notify,G-steps,G-secrets   [INV-F]
  W3 ghauth host browser-open + device-code copy (OSC52 + shell-out)             → G-sandbox,G-steps,G-tui,G-bus
  W4 attach standalone removed                                                   → G-steps,G-tui
  W5 vscode open "/"                                                             → G-sandbox
  W6 full toolchain into image + dependabot integrity (4 light tools→go.mod tool directives; golangci-lint→install.sh)  → .devcontainer/Dockerfile,G-config
  W7 bounded proxy wait + ctx-aware sleep                                        → G-hooksM,G-provision
  off-plan (same iteration): onboarding/trust/theme suppression (~/.claude.json seed)   → G-provision ; copy-feedback honesty → G-tui

W-arch-C LANDED-PENDING — mirabilis PR#135 (CI in-flight; NOT merged to main):
  proxy/notify decoupled into `mirabilis serve` (single-instance, detached, ref-count reap, I5)  → G-serve,G-authproxy,G-bus
  TUI = equal client (owner/secondary/flock-role/promote/applySecondary removed)               → G-tui,G-sandbox,G-steps
  attachStep.Check idempotent (I3)                                                              → G-steps
  UX: telegram three-state (skip non-terminal), provision statusbar, header+animated logo, spinner → G-tui,G-steps
  caveman activated (marketplace+install, dead git-clone removed)                               → G-cav
  headroom HEADROOM_MODE config-gated G4                                                        → G-hed,G-config
  sandbox_context V2: FOL-rendered from config.go single-source, sandbox-context.md deleted    → G-sandbox,G-hooksM
  credential-authority: gh auth setup-git in SessionStart (idempotent, best-effort)            → G-hooksM

OPEN plan:
  W8 SearXNG websearch (new gene)        → G-websearch,G-config,compose
  W9 cross-cluster back-nav (rewindable FSM / front-load)  → G-pipeline,G-steps,G-tui   [eng-choice/HYPO; deferred]
  W10 adaptive overlay form sizing on push  → G-tui,G-bus   [eng-choice/HYPO; deferred]
```

## M invariant-genes
```
INV-D  config/discover ¬hardcode   home: localllm env-overridable config + /v1/models discovery + completer/config tests
INV-E  sanitize external-model out  home: SanitizeOutput + table test + mcp_test (offload tool sanitizes at the boundary)
INV-F  bound IO ¬human-wait         home: notify 4xx-permanent + capped-retry tests; Configure bounded (¬the human-input wait)
INV-I3 attachStep.Check idempotent  home: Run⇒Check=true (PR#135 fix; was hardcoded false, violating I3)  [HYPO landed-pending PR#135]
```

## Ledger
FACT: all packages exist (listing) + package-doc read for authproxy/harness/membackup/obs/localllm. caveman ∈ M wired via plugin catalog (PR#135 in-flight — NOT merged to main; was catalog-only skill before). ASSOC: role of claudeauth/status (name-only).
CONFLICT-1 RESOLVED: W1 landed integration-only — NO auto-offload hook (D5/D6 honored); caveman↔localLLM stay distinct alleles (§H quartet, channel-disjoint).
CONFLICT-2 RESOLVED [#30]: the owner approved the config-driven design-reversal; the localllm constants are now env-overridable with the prior hardcoded values as defaults, and SanitizeOutput crosses the model-output trust boundary.
HYPO: W-arch-C block (G-serve, credential-authority, caveman wiring, headroom G4 knob, sandbox_context V2) — all in PR#135, CI in-flight; status = landed-pending-merge, NOT FACT yet. Will resolve to FACT when owner merges.
ROT-HYGIENE (this iter): volatile `:line` suffixes stripped from κ package-homes (the package is the home; the line rots — §B). PR-status provenance stripped from work-item descriptions (history in git, not genome — §A.4). plan-homes in DEPT plans are file-actionable by design; plan-line-homes left as-is (owner call).
