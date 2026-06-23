# Vec · v-bugs — Bugs / fixes (the eval-gate fixes + open)

Type: this is a Vec entry — transient, not truth, neither a gene 𝒢 nor an archive entry Λ (vectors.md §Type). Source [FACT]: the comments on the R→S audit (the eval-gate-correction thread; origin recorded as provenance in archive/archive.md). Each fix verified vs NON-LLM ground truth + golden-tested to FAIL on the OLD behaviour. Scope: these are the R→S prerequisites — the merge gate `eval/statistical_test.py` is N's "measurement organ"; until it read true, ΔN = drift (GENOME §D binding-constraint, the R→S audit §3). Cross-ref vectors/theory-of-everything.md §3,§9. Discipline: once a bug-fix is implemented, discard it — a landed fix stays here only until it's clearly stable; the OPEN items (§Open) are the live work.

## §Fixed — the three gate conditions (all corrected, golden-tested, MERGED to main #64/#65/#66 — verified 2026-06-23) [FACT, the R→S audit comments]
```
the McNemar-tail fix  McNemar tail inverted              [DONE]
     bug : statistical_test.py:189 summed the LOWER binomial tail P(X≤r) ⇒ gate PASSED regressions, BLOCKED improvements (inverted since commit-1; a hardcoded test string masked it — tested the parser ¬the formula).
     fix : → UPPER tail P(X≥r).  verified vs scipy.stats.binomtest(alt='greater') + statsmodels …mcnemar (library ground truth); canon Wikipedia/CRAN exact2x2.
the Cohen’s-d edge fix  Cohen's d zero-variance → 0        [DONE]
     bug : a perfectly-CONSISTENT improvement scored d=0, CI(0,0) ⇒ the gate blocked the STRONGEST possible signal.
     fix : correct limit — sd=0,mean>0 → +∞ (pass) ; mean<0 → −∞ (fail) ; mean=0 → 0.  verified vs CRAN effectsize, MRC-CBU ("everyone changes by the same amount ⇒ d=±infinity").
the rater-aware-α fix  Krippendorff α rater-blind          [DONE]
     bug : one judge's k runs counted AS raters ⇒ run-to-run noise reported as "inter-rater reliability" (e.g. α=0.375 from 3 runs).
     fix : rater-aware — group by the `rater` dim, aggregate a rater's runs (majority) → one rating, then α ACROSS raters. 1 rater → None (criteria.md:49) ; ≥2 → genuine inter-rater.  ref Wikipedia Krippendorff's-alpha.
```

## §Wired / Landed — the missing rater + the structural edge (MERGED to main #67/#68 — verified 2026-06-23) [FACT, the R→S audit comments]
```
the cross-family second judge  cross-family second judge          [WIRED — live run deferred]
     gap : the rater-aware-α fix makes α rater-aware, but with one judge there's no real `rater`. need a second judge of a DIFFERENT model family (same-family judges share error modes — arXiv:2506.07962; triangulation needs independent channels — Munafò&Davey-Smith Nature 2018).
     fix : `judge --judge-provider github-models --rater 2` → GitHub Models (FREE, in Actions, no API key; permissions: models:read; actions/ai-inference@v1; a NON-Claude family e.g. openai/gpt-4o-mini, pin the live catalog id). a `rater` column lets α (the rater-aware-α fix) compute genuine inter-rater across rater-1 (Claude) + rater-2.
     status : deterministic parts tested locally; the LIVE model call is gated + non-blocking (workflow_dispatch), validates on first CI run.
the vanilla baseline arm  vanilla / no-plugin baseline arm   [LANDED — A/B run deferred to product maturity]
     gap : run_suite.py skipped any empty calibration ⇒ the eval could only compare TWO PLUGIN VERSIONS, never "Claude" vs "Claude + harness".
     fix : a `vanilla` sentinel arm = an empty system-prompt that is NOT skipped, flows through generation as bare Claude = the structural R→S edge.
     status : verified independently — minimal diff (sentinel + `from __future__ import annotations`), no new comments, 4/4 golden tests FAIL when the sentinel is reverted (catch the old skip, ¬a parser), regression clean (statistical 19/19, second-judge 3/3, mock-e2e ALL PASS); run_suite materialization calls no LLM ⇒ fully locally verifiable.
```
```
state-of-R→S [FACT, the R→S audit comments] :
  buildable prerequisites COMPLETE — gate correct (the McNemar-tail, Cohen's-d, and rater-aware-α fixes) and the cross-family judge wired and the vanilla arm landed; all deterministic, golden-tested, vs non-LLM ground truth.
  DEFERRED (owner-gated; "fix the instrument first, run it when the product is less raw") — the live A/B run for merge verdicts: first inter-rater α (rater-1 Claude + rater-2 GitHub-Models), then A/B vanilla vs +harness vs an external UNSATURATED benchmark (avoid saturated/contaminated — SWE-bench Verified deprecation OpenAI Feb-2026; use SWE-bench Pro).
```

## §Open — remaining issues (CODE, no run) [FACT, the R→S audit comments]
```
N7   verification-gate stack-coverage               [OPEN — conflict now VERIFIED, 2026-06-23]
     problem : ROADMAP.md:25 marks N7 status=shipped (claims tsc --noEmit / dotnet build / swift build); but the live `scripts/verification-gate.sh` case-block (verified on origin/main) STILL covers only `*.sh` / `*.py` / `*.json` — NO tsc/dotnet/swift/go. The conflict is now RESOLVED-as-real (no longer "unverifiable here"): the code half NO-OPS on C#/.NET / TS / Swift (the approval-only / high-false-completion regime) ⇒ "verified" is empty for those stacks. ROADMAP's "shipped" is aspirational, not actual.
     fix (planned, still open) : make N7 REAL — a stack-aware verification-gate that runs the right build/test per stack. ⟵ this is V4 in theory-of-everything.md §6 (extend channel independence: compiler/tests as a real channel for every stack). NOTE for owner: ROADMAP.md:25 should be flipped shipped→open to match the code (organ-side doc fix, flagged in PR).
     status : VERIFIED open — verification-gate.sh = sh/py/json only on origin/main; ROADMAP.md:25 still says shipped (organ's own doc is internally inconsistent — see PR "needs owner decision").
eval-power   N too small                              [OPEN]
     problem : N=17 probes is UNDERPOWERED for the Wilcoxon/McNemar gate — even a now-correct test can't detect the single-digit-pp marginal headroom of a prompt layer over an already-strong scaffold at that N.
     fix (planned) : raise N (theory-of-everything.md §6 V1 note: "N must be large"); a larger probe set before trusting a live verdict.
     status : named as remaining work in the vanilla-baseline-arm comment; gated on the same "run when less raw" decision.
```

## §Parked — items with explicit triggers (transient/Vec; discard when landed)

```
WSL2-canary   docker-in-WSL2 E2E canary + failure notification   [PARKED → TRIGGER FIRED 2026-06-16; now actionable, owner to schedule]
     source   : mirabilis#121 L1
     trigger  : date ≥ 2026-06-16 (VS2026 runner-image migration settles) — NOW PAST (today 2026-06-23)
     current state [FACT, re-verified vs mirabilis origin/main on 2026-06-23 — state UNCHANGED]:
       - canary.yml on main STILL has no windows job and no `if: failure()` notification step (the work is not done)
       - ci.yml windows-wsl leg (windows-2025, Vampire/setup-wsl v7) smokes only install.sh;
         the actual docker-in-WSL2 container path is still unexercised by CI
     work when triggered:
       - add a best-effort `windows-2025` CI job in canary.yml, `continue-on-error: true`
       - add `if: failure()` step → create/update a tracking issue (failure notification)
       - Docker install via get.docker.com or `apt-get install docker-ce` + `sudo service docker start`
     sharp edges (pre-researched, carried from #85):
       - WSL keep-alive: `wsl -d Ubuntu --exec dbus-launch true`
       - use `127.0.0.1` not `localhost` inside WSL2
       - iptables-legacy fallback (microsoft/WSL#6655)
       - env bridging via WSLENV
       - `windows-11-arm` excluded (actions/runner-images#14076, Vampire/setup-wsl#74)
     note: #121 L2 (telegram extensions) and L3 (Common Code consumer-side) are already in the
           genome; this entry covers L1 only. Discard this parked entry once canary job is landed.
```

## §M-iter · sandbox iteration — OPEN residue [FACT unless tagged]

W1–W7 and W-arch-C expressed as genes (registry-M / graph-plan-sandbox); PR#135 MERGED to main (origin/main HEAD #148 as of 2026-06-23). Only the OPEN residue lives here (discard each when closed):
```
dependabot-blindspot  dependabot tracks only FROM digests + go.mod + action SHAs; CANNOT track go-install@v / curl / apt / npm pins. closed for the 4 light Go tools (→ go.mod tool directives); golangci-lint → official install.sh; go-arch-lint stays a Dockerfile pin. REMAINING manual-bump: golangci-lint · gitleaks · go-arch-lint · RTK · uv · go · gh · docker-ce-cli · claude-code · bats. [Q: a non-dependabot release-watch workflow worth its cost?]
pty/signal env-tests  TestTTYChildInheritsForegroundPgroup FAILS in a no-controlling-terminal container (this sandbox), PASS on main + CI ⇒ env-sensitivity, ¬regression; pre-existing.
sanitize-overstrip    [HYPO, low-prob] broadened regex could strip a literal `<word|>` in genuine model output; bounded by `|>` close; no evidence.
```

§ledger: FACT — dependabot-blindspot mirrors mirabilis AGENTS.md. ASSOC — Vec placement. HYPO — regex over-strip. transient — discard each when closed.

## §Mac — fresh-Mac install blockers [HYPO — reasoned from code + vendor docs; no real macOS run; source: 2026-06-23 audit vs mirabilis origin/main HEAD 5e9d33b]

Critical path: `install.sh darwin` → `make bootstrap/install` → `mirabilis` TUI Launch → container + Claude boot.
All blockers below are HYPO (not empirically run on macOS; anchored to code path + Docker/Homebrew docs; `empirically_verified` noted per item).

```
Mac-B1  Docker Desktop first-run GUI license [HIGH — empirically_verified: false]
         Daemon will not start until the Subscription Service Agreement is accepted (GUI modal or
         `--accept-license` to the install binary). `make bootstrap` only `brew bundle`-installs the cask;
         nothing runs `/Applications/Docker.app/Contents/MacOS/install --accept-license`.
         On a fresh Mac, preflight `open -a Docker` + 30x2s poll times out → Launch fails.
         fix: add `sudo /Applications/Docker.app/Contents/MacOS/install --accept-license` to bootstrap
              after `brew bundle`, then `open -a Docker`; at minimum name the dialog in preflight
              timeout message (κ:internal/engine/steps/preflight.go).
         evidence: Brewfile = `cask "docker-desktop"` only; repo grep accept-license = 0 hits.

Mac-B2  curl|bash sudo-prompt hang [HIGH — empirically_verified: false]
         README quick-start `curl -fsSL .../install.sh | bash` runs `brew bundle` of docker-desktop cask.
         The cask's privileged linking step prompts for sudo; in a non-TTY piped context (CI / curl-pipe)
         the prompt may hang until SIGINT. `sudo -v` pre-auth and `/dev/tty` handling are absent in repo.
         fix: instruct owner to run from a real terminal (`bash -c "$(curl -fsSL ...)"`, not pipe);
              add `sudo -v` keep-alive before `brew bundle`; split bootstrap into an interactive step.
         evidence: README.md quick-start = `| bash`; install.sh has no sudo -v / NONINTERACTIVE.

Mac-B3  host `claude setup-token` PATH gap [MED — empirically_verified: false]
         If `mirabilis` is run in the SAME shell as the installer, `~/.local/bin` is not yet on PATH
         (rc edits not sourced). claudeAuthStep execs `claude setup-token` via PTY using LookPath against
         inherited PATH; no ~/.local/bin augmentation in Go. install.sh only warns (no re-source/re-exec).
         fix: install.sh prepend ~/.local/bin to PATH before printing "run: mirabilis", or tell owner to
              open a new terminal.
         evidence: internal/tui/app/handlers_pipeline.go → exec LookPath on inherited PATH; install.sh
                   warn only, no re-source.

Mac-B4  settings-env pins :8787 when Optional headroom skips [MED — empirically_verified: false]
         headroom is Optional (stateSkipped on pip failure); failedDep blocks only on stateFailed — so
         settingsEnvStep (Deps:[headroom]) still runs and pins ANTHROPIC_BASE_URL=:8787 unconditionally.
         SessionStart ensureProxyForSession early-returns if upstream file absent (never written on skip) →
         no self-heal. Claude is wired to a dead :8787, cannot reach Anthropic until re-provision.
         fix: settings-env falls back to host authproxy URL when :8787 unreachable, OR promote headroom to
              non-optional, OR Check :8787 reachability before pinning.
         evidence: internal/engine/provision/headroom.go:Optional=true; pipeline.go cascade-skip; settingsenv.go
                   unconditional base-URL write; session.go early-return on missing upstream file.

Mac-B5  keychain entry name doc/invariant mismatch [LOW — empirically_verified: true]
         Code: tokenKey="claude-token" (source.go) → entryName="mirabilis-claude-token" (keychain.go).
         Docs (SECURITY.md + AGENTS.md) say "mirabilis-claude"; AGENTS.md invariant "no doubled suffix".
         Functionally harmless (set/get symmetric on the same name) but docs point at a nonexistent entry.
         fix: change tokenKey="claude" (+one-time migration) OR correct SECURITY.md/AGENTS.md to
              "mirabilis-claude-token".
         evidence: source.go tokenKey literal + keychain.go entryName construction — directly verified.
```

§Mac-verdict [HYPO]: the scripted path is architecturally complete and the in-container auth chain is sound (token never enters container, onboarding belt, SessionStart hook, raid-default harness). But "fresh Mac → just works, zero manual steps" is false on first launch for B1+B2 (Docker license + brew-sudo TTY) AND the first launch always requires two interactive sign-ins (Anthropic setup-token + GitHub device flow) — repeat launches ARE zero-question. B4 is a verified code-path break (not macOS-specific). B5 is cosmetic. None of B1–B3 could be run here (no macOS/Docker/brew).

## §I — Ledger (this entry)
```
FACT  : the eval-gate fixes are MERGED to main (#64/#65/#66/#67/#68, verified 2026-06-23 on origin/main); each fix verified vs the named non-LLM ground truth + golden-tested to fail on the old behaviour; eval-power N=17 stated in the vanilla-baseline-arm comment.
FACT/conflict : N7 stack-coverage — ROADMAP.md:25 status=shipped vs verification-gate.sh sh/py/json only — VERIFIED on origin/main: the code IS sh/py/json only, so the conflict is real and N7 is open (ROADMAP's "shipped" is aspirational). Upgraded from "unverifiable-here" to verified-open 2026-06-23.
FACT  : Mac-B5 keychain mismatch verified directly from source.go + keychain.go + docs (2026-06-23 audit).
ASSOC : the cited references (scipy/statsmodels, CRAN effectsize/exact2x2, arXiv:2506.07962, Munafò&Davey-Smith) — cited BY the thread; the mapping of N7→V4 and eval-power→V1 is to theory-of-everything.md §6 (same source, the R→S audit).
HYPO  : Mac-B1/B2/B3/B4 — reasoned from code path + Docker/Homebrew docs; no macOS/Docker/brew run possible (Linux container). Mac-B4 code path deterministic but trigger is environmental.
HYPO  : that the deferred live A/B run will show the harness helps — explicitly OPEN (the whole reason V1 is the binding constraint); whether N7-real + larger-N suffice to detect the effect.
Q     : the exact unsaturated benchmark to anchor the A/B (theory-of-everything.md §7 Q4). Live A/B RUN status (verified 2026-06-23): NOT done — no published results/CSV committed to neuro-matrix; a dev-time live run is referenced in statistical_test.py:187 ("live run 2026-06-11: 4 regressions...") but no merge-verdict A/B is published ⇒ "built + landed, not run" stands.
transient : entry — once the eval-gate fixes are implemented, discard; the live run + N7 + eval-power are the open work. §Mac blockers: discard each entry when the fix is verified on a real Mac and landed. Discarding v-bugs does not force a rebuild of GENOME.
```
