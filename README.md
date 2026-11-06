<p align="center">
  <a href="https://egm.dev"><img src="docs/assets/readme-header.svg" width="480" height="116" alt="Elephant-Goldfish Model"></a>
</p>

<p align="center">Design with an elephant. Review with a goldfish.</p>

<p align="center">
  <a href="#install">Install</a> &ensp;·&ensp;
  <a href="#try-your-first-design">Quickstart</a> &ensp;·&ensp;
  <a href="docs/getting_started.md">Documentation</a> &ensp;·&ensp;
  <a href="https://egm.dev">Website</a>
</p>

<br>

Develop ideas with context and review documents with fresh eyes. EGM is an open-source plugin for AI assistants.

**Elephant** holds your project context and drafts the specification. **Goldfish** reviewers examine the draft and referenced source material without the earlier conversation, helping expose unstated assumptions and blind spots. **You** make the architectural trade-offs and approve the specification before implementing.

The built-in draft and design-review workflow targets software specifications. For other documents, choose reviewers and standards with `/egm-review-loop`. Bootstrap and drift reporting apply to software codebases.

## Install

Choose your coding agent. Install the complete plugin so its skills can read the reviewer prompts and document standards.

### ChatGPT and Codex desktop

Open the [published EGM plugin](https://chatgpt.com/plugins/plugins_6aeb90f47ec88191a3c107e01d3eb357) in the desktop app and install it. This listing is desktop-only. For Codex CLI, use the commands below.

### Antigravity CLI

```sh
agy plugin install https://github.com/google/elephant-goldfish-model
```

For the **Antigravity App** and **Antigravity for IDEs** (Visual Studio Code extension), run `/plugin` or see the [installation instructions](docs/harnesses.md#antigravity-app-and-antigravity-for-ides).

### Claude Code

```sh
claude plugin marketplace add google/elephant-goldfish-model
claude plugin install egm@egm
```

### Codex CLI

```sh
codex plugin marketplace add google/elephant-goldfish-model
codex plugin add egm@egm
```

Start a new session after installation. For **Claude Cowork** and **ChatGPT Work**, see the [setup guide](docs/harnesses.md).

## Try your first design

Open your project in your coding agent and choose a feature that needs design decisions. This example adds webhook delivery: what should happen when a delivery fails, or the same event arrives twice?

The commands below are shown without a prefix. In Antigravity (agy CLI) and Claude Code, add the `/egm:` prefix, for example `/egm:egm-brainstorm`. On agy CLI 1.4.10 an unprefixed name is completed to the prefixed command ([#220](https://github.com/google/elephant-goldfish-model/issues/220)), but 1.4.8 does not ([#196](https://github.com/google/elephant-goldfish-model/issues/196)), so keep the prefix. In Codex, select the corresponding EGM skill from the skill picker. Brainstorming and review require a session that can create fresh subagents.

<img src="skills/egm-brainstorm/assets/icon.svg" width="20" height="20" align="top" alt=""> **Explore the idea**

```text
/egm-brainstorm Add webhook delivery to this project.
```

Discuss requirements and trade-offs with the agent. Fresh reviewers challenge the proposal, and the agent saves the agreed direction in `concepts_brief.md`.

<img src="skills/egm-draft/assets/icon.svg" width="20" height="20" align="top" alt=""> **Draft the specification**

```text
/egm-draft
```

The agent turns the brief into `design_draft.md`, pausing after each section for your feedback in chat.

<img src="skills/egm-review/assets/icon.svg" width="20" height="20" align="top" alt=""> **Review the draft**

```text
/egm-review design_draft.md
```

Use the draft path returned by the agent.

Fresh reviewers check the design, its clarity, its fit with the code, and its implementation plan. Choose which findings to address. When you approve the design, ask your coding agent to implement it.

See the [workflow guide](docs/getting_started.md) for the full process, including saving approved specifications under `docs/designs/`.

## How it works

<table>
  <thead><tr><th align="left">Role</th><th align="left">Context</th><th align="left">Responsibility</th></tr></thead>
  <tbody>
    <tr valign="top"><td><strong>Elephant</strong></td><td>Your project, requirements, and earlier decisions</td><td>Explore the problem and draft the specification.</td></tr>
    <tr valign="top"><td><strong>Goldfish</strong></td><td>The document and its referenced source material, without the earlier conversation</td><td>Find missing assumptions, unclear requirements, and implementation risks.</td></tr>
    <tr valign="top"><td><strong>You</strong></td><td>The goals and constraints that matter</td><td>Resolve trade-offs, approve the design, and decide what to build.</td></tr>
  </tbody>
</table>

Goldfish reviews require fresh subagent contexts. If your agent cannot create them, EGM stops the review. A review does not replace tests or human judgment. See [supported environments and verification limits](docs/harnesses.md#support-status--contributing-other-harnesses).

## Choose a skill

You can use each skill when you need it. You do not have to follow the full sequence.

<table>
  <thead><tr><th align="left">Skill</th><th align="left">Use it to…</th></tr></thead>
  <tbody>
    <tr valign="top"><td width="160" valign="top"><img src="skills/egm-brainstorm/assets/icon.svg" width="20" height="20" alt="" align="top">&nbsp;<a href="skills/egm-brainstorm/SKILL.md">Brainstorm</a></td><td>Test an idea and write a concept brief.</td></tr>
    <tr valign="top"><td width="160" valign="top"><img src="skills/egm-draft/assets/icon.svg" width="20" height="20" alt="" align="top">&nbsp;<a href="skills/egm-draft/SKILL.md">Draft</a></td><td>Turn a brief or existing notes into a design document.</td></tr>
    <tr valign="top"><td width="160" valign="top"><img src="skills/egm-resolve/assets/icon.svg" width="20" height="20" alt="" align="top">&nbsp;<a href="skills/egm-resolve/SKILL.md">Resolve</a></td><td>Work through review findings and agree on changes.</td></tr>
    <tr valign="top"><td width="160" valign="top"><img src="skills/egm-bootstrap/assets/icon.svg" width="20" height="20" alt="" align="top">&nbsp;<a href="skills/egm-bootstrap/SKILL.md">Bootstrap</a></td><td>Create or update documentation for an existing codebase.</td></tr>
    <tr valign="top"><td width="160" valign="top"><img src="skills/egm-review/assets/icon.svg" width="20" height="20" alt="" align="top">&nbsp;<a href="skills/egm-review/SKILL.md">Review</a></td><td>Review a design with fresh agents across five stages.</td></tr>
    <tr valign="top"><td width="160" valign="top"><img src="skills/egm-review-loop/assets/icon.svg" width="20" height="20" alt="" align="top">&nbsp;<a href="skills/egm-review-loop/SKILL.md">Review&nbsp;loop</a></td><td>Run a configured group of reviewers for a specific review task.</td></tr>
    <tr valign="top"><td width="160" valign="top"><img src="skills/egm-drift-report/assets/icon.svg" width="20" height="20" alt="" align="top">&nbsp;<a href="skills/egm-drift-report/SKILL.md">Drift&nbsp;report</a></td><td>Compare checked-in documents with the current source code.</td></tr>
  </tbody>
</table>

## Learn more

- [Getting started](docs/getting_started.md): the workflow and project layout.
- [Setup](docs/harnesses.md): installation, agent capabilities, and known limits.
- [Architecture](https://github.com/google/elephant-goldfish-model/blob/main/docs/designs/architecture.md): how skills and reviewers fit together.
- [Testing](https://github.com/google/elephant-goldfish-model/blob/main/TESTING.md): checks, execution records, and verification limits.
- [Dave Rensin’s original essay](https://medium.com/@drensin/elephants-goldfish-and-the-new-golden-age-of-software-engineering-c33641a48874): the ideas behind EGM.

## System Overview

This repository is the source of the EGM plugin. The product is prose, not a
service: Markdown skills, reviewer personas, and review standards that a coding
agent reads at run time, plus one thin manifest per host that maps those files
onto the host's native plugin, skill, and subagent features. The Python and Node
in this tree only validate, package, install, and publish that Markdown.

- **Workflows** live in `skills/` (seven `SKILL.md` files). A skill runs the
  Elephant side in the parent session and dispatches Goldfish reviewers as
  fresh subagents.
- **Reviewer personas** live in `agents/` (ten canonical prompts). Every host
  adapter in `.claude-plugin/agents/`, `.cursor-plugin/agents/`,
  `com.github.copilot/agents/`, and the generated OpenCode configuration is a
  thin wrapper that pins host tool restrictions and defers to the canonical
  persona file [`.claude-plugin/agents/design_critic.md`].
- **Shared rubrics** live in `resources/`: the execution instructions and five
  document standards that skills and reviewers load as the authoritative rules
  [`resources/README.md`].
- **Host manifests** declare one identity. `plugin.json` is the portable
  manifest (`name: egm`, `version: 0.1.0`, an `extensions.com.openai` listing
  block with `requires_local_executor: true`) [`plugin.json`]; `.claude-plugin/`,
  `.codex-plugin/`, `.cursor-plugin/`, `.plugin/`, `.agents/`, and
  `com.github.copilot/` hold the host-specific views of the same package.
- **Packaging and release**: `scripts/pack_plugin.py` builds the `claude` and
  `openai` runtime folders and ZIPs from an explicit allowlist,
  `scripts/prepare_release.py` wraps it for tagged releases, the generated
  Claude runtime is checked in at `distributions/claude/`, and an experimental
  OpenCode installer lives in `adapters/opencode/` [`scripts/pack_plugin.py:build`].
- **Validation**: `tests/unit/` is an offline pytest suite that enforces the
  manifest, frontmatter, link, packaging, and isolation contracts listed under
  [Global Invariants](#global-invariants); `tests/integration/` holds opt-in
  live host probes. `pyproject.toml` declares the `test` dependency group
  (`pytest==8.3.5`, `pyyaml==6.0.2`) and pins `testpaths = ["tests/unit"]` with
  `--import-mode=importlib` [`pyproject.toml:tool.pytest.ini_options`].
- **Website and governance**: `site/` is the egm.dev landing page and
  `.github/` holds CI, release, Pages deployment, and PR-scope automation. The
  root-level governance documents are `AGENTS.md`, `AI_POLICY.md`,
  `CONTRIBUTING.md`, `ACCESSIBILITY.md`, `TESTING.md`, and `LICENSE`
  (Apache-2.0). `.gitattributes` forces LF line endings on `*.sh`, and
  `.gitignore` excludes `__pycache__/`, `.venv/`, `.pytest_cache/`, and
  `eval_results/`. The root contains no source files of its own.

## Subdirectories & System Boundaries

Runtime packages ship only the paths allowlisted in
[`scripts/pack_plugin.py:SHARED`] plus one host directory; every other
directory is repository-only tooling. "Runtime" below marks a directory that
ships to users.

- `.agents/`: Antigravity marketplace catalog `plugins/marketplace.json`: name
  `egm`, one plugin entry with `source: "./"`, policy
  `installation: AVAILABLE` and `authentication: ON_INSTALL`, category
  `Productivity` [`.agents/plugins/marketplace.json`]. Repository-only.
- `.claude-plugin/` (runtime, `claude` target only): Claude Code host manifest
  `plugin.json` (ten `agents` adapter paths, `icon: ./.claude-plugin/icon.png`),
  `marketplace.json`, `icon.png`, and `agents/` with ten adapters. Reviewer
  adapters pin `tools: [Read, Grep, Glob]`, `model: inherit`, and
  `omitClaudeMd: true` and read `${CLAUDE_PLUGIN_ROOT}/agents/<persona>.md`;
  `synthesizer.md` adds `Agent` and `Write` and may write only the requested
  report; `bootstrap_orchestrator.md` adds `Agent`, `Bash`, `Write`, and `Edit`
  and routes to `skills/egm-bootstrap/SKILL.md`
  [`.claude-plugin/agents/synthesizer.md`, `.claude-plugin/agents/bootstrap_orchestrator.md`].
- `.codex-plugin/` (runtime, `openai` target only): Codex host manifest with
  `skills: ./skills/`, `requires_local_executor: true`, and an `interface`
  block that must equal `plugin.json` `extensions.com.openai.interface`
  [`.codex-plugin/plugin.json`].
- `.cursor-plugin/`: Cursor package. `plugin.json` points `skills`, `agents`,
  and `rules` at `./skills/`, `./.cursor-plugin/agents/`, and
  `./.cursor-plugin/rules/`; eight reviewer adapters set `readonly: true`,
  `permissionMode: readonly`, and `is_background: false` and require an
  absolute `EGM_ROOT` task value; `rules/egm.mdc` (`alwaysApply: true`)
  resolves `EGM_ROOT` by ascending three directories from the selected
  `SKILL.md` and forbids dispatching the synthesizer or bootstrap orchestrator
  as generic children [`.cursor-plugin/rules/egm.mdc`]. Repository-only.
- `.github/`: `CODEOWNERS` (six global owners), `dependabot.yml` (weekly
  grouped updates for `/site` npm packages and GitHub Actions with a 7-day
  cooldown), three issue templates, `PULL_REQUEST_TEMPLATE.md`, and seven
  workflows: `tests.yml` (unit matrix on `ubuntu-24.04` and `windows-2025`
  plus `site-validation`, gated by a `CI` job), `release.yml` (draft release
  from an existing tag), `deploy-site.yml` (GitHub Pages),
  `pr-scope-advisory.yml` (`pull_request_target` scope and template check),
  and the native probes `copilot-native.yml`, `cursor-native.yml`, and
  `opencode-native.yml` [`.github/workflows/tests.yml`]. Repository-only.
- `.plugin/`: generic agent-plugins manifest that declares
  `$schema: https://agent-plugins.org/schemas/1.0.0/plugin.schema.json` and
  identity fields only. The root `plugin.json` deliberately omits `$schema`
  because omp routes schema-declaring manifests to a strict validator that
  rejects `disable-model-invocation`
  [`tests/unit/test_harnesses.py:test_portable_manifest_schema`]. Repository-only.
- `adapters/`: `opencode/install.py`, the experimental OpenCode V1 installer
  (`HOST_VERSION = "1.18.29"`). `install(destination)` refuses an existing
  path, a path inside the source tree, and any path containing glob,
  template, or `.env.` characters; it copies `skills/`, `agents/`,
  `resources/`, `docs/`, `plugin.json`, `LICENSE`, `README.md`, and
  `TESTING.md` into `bundle/`, symlinks each skill, and writes `opencode.json`
  (eight `subagent` reviewers with `"*": "deny"`, `grep: deny`, and `.env`
  reads denied; one `primary` `egm` agent whose `skill` and `task` permissions
  allow only `egm-*` and the registered reviewers; seven commands) plus
  `installation.json` with a SHA-256 per bundled file
  [`adapters/opencode/install.py:install`]. Repository-only.
- `agents/` (runtime): ten canonical personas, each with `name`,
  `description`, and `license` frontmatter and no host tool keys:
  `egm-bootstrap-orchestrator`, `egm-codebase-details`, `egm-comprehension`,
  `egm-design` ([design_critic.md](agents/design_critic.md)),
  `egm-implementation-readiness`, `egm-inventive-catalyst`, `egm-structural`,
  `egm-style`, `egm-synthesizer` ([synthesizer.md](agents/synthesizer.md)),
  and `egm-zoom-out`. `style.md` must define the `DROP`, `CALIBRATE`,
  `RELOCATE`, and `KEEP` calibration actions
  [`tests/unit/test_style_and_boundaries.py`].
- `assets/` (runtime): `icon.svg`, the 64 by 64 plugin logo referenced as
  `composerIcon` and `logo` by the OpenAI listing; it must stay under
  `assets/`, be square and at least 48 px, and be at most 5 MiB
  [`tests/unit/test_harnesses.py:test_openai_submission_metadata_and_assets`].
- `com.github.copilot/`: nine Copilot CLI agent profiles. Eight reviewers
  `egm-<persona>.agent.md` use `tools: [read, search]`,
  `include-custom-instructions: false`, and `user-invocable: false`, read
  `<EGM_ROOT>/agents/<persona>.md`, and contain no `${` expansion;
  `egm.agent.md` (`tools: [read, search, edit, agent]`) reads
  `<EGM_ROOT>/docs/copilot.md` and keeps synthesis in the main session
  [`com.github.copilot/agents/egm.agent.md`]. Repository-only.
- `distributions/`: `claude/`, the checked-in output of
  `python3 scripts/pack_plugin.py --target claude` (66 files) that the
  Anthropic directory portal scans. It must stay byte-identical to a fresh
  build [`tests/unit/test_packaging.py:test_published_claude_runtime_is_current`].
  The packaging runbook is
  [docs/directory.md](https://github.com/google/elephant-goldfish-model/blob/main/docs/directory.md),
  and a draft design proposes a generated `release/claude` branch instead.
  Do not edit it by hand and do not commit ZIPs.
- `docs/`: user and contributor documentation. The runtime guides
  [index.md](docs/index.md), [getting_started.md](docs/getting_started.md),
  [harnesses.md](docs/harnesses.md), [claude.md](docs/claude.md),
  [codex.md](docs/codex.md), [faq.md](docs/faq.md),
  [privacy.md](docs/privacy.md), [releases.md](docs/releases.md), and
  `assets/readme-header.svg` ship in packages; `copilot.md`, `cursor.md`,
  `opencode.md`, `muse.md`, `directory.md`, and the fifteen design
  specifications indexed by
  [designs/README.md](https://github.com/google/elephant-goldfish-model/blob/main/docs/designs/README.md)
  are repository-only. Each host guide must document the
  `EGM artifact directory:` override and its working-directory fallback
  [`tests/unit/test_harnesses.py:test_artifact_directory_override_is_documented_for_each_harness`].
- `resources/` (runtime): the authoritative rules, indexed by
  [resources/README.md](resources/README.md): `execution_instructions.md`
  (design-only scope, private scratch directories, one question at a time,
  explicit consensus gates, no summaries, contradiction auditing) and
  `document_standards/` with the `feature-spec`, `heilmeier`,
  `implementation-readiness`, `re-implementation`, and `zoom-out` standards.
  The implementation-readiness standard must define "Target Scope & File
  Boundary" and a "Phase 5 write allowlist"
  [`tests/unit/test_style_and_boundaries.py`].
- `scripts/`: standard-library packaging tools. `pack_plugin.py` exposes
  `build(root, target, output) -> (folder, archive)` and the `SHARED`, `HOST`,
  `SKILLS`, and `REQUIRED_SHARED` allowlists (CLI:
  `--target {claude,openai} --output DIR`); `prepare_release.py` exposes
  `version_for_tag(root, tag)` and `prepare(root, tag, output, commit)` (CLI:
  `--tag vX.Y.Z --commit <40-hex SHA> --output DIR`)
  [`scripts/prepare_release.py:prepare`]. Repository-only.
- `site/`: the egm.dev landing page
  ([site/README.md](https://github.com/google/elephant-goldfish-model/blob/main/site/README.md)):
  Astro 7 static output, `@material/web` 2.5.0 gBreeze styles, self-hosted
  Google Sans fonts, `node >=22.23.4`; `src/components/SkillIcon.astro`
  imports the canonical `skills/*/assets/icon.svg` files; Google Analytics
  loads only on `egm.dev` after affirmative cookie consent
  [`site/astro.config.mjs`, `site/package.json`]. Repository-only.
- `skills/` (runtime): the seven workflows
  [egm-bootstrap](skills/egm-bootstrap/SKILL.md),
  [egm-brainstorm](skills/egm-brainstorm/SKILL.md),
  [egm-draft](skills/egm-draft/SKILL.md),
  [egm-drift-report](skills/egm-drift-report/SKILL.md),
  [egm-resolve](skills/egm-resolve/SKILL.md),
  [egm-review](skills/egm-review/SKILL.md), and
  [egm-review-loop](skills/egm-review-loop/SKILL.md). Every skill directory
  holds `SKILL.md` (frontmatter `disable-model-invocation: true`),
  `agents/openai.yaml`, `assets/icon.svg`, `test_scenarios.yaml`, and
  `TEST.md`; `egm-bootstrap/references/` (`templates.md`,
  `worker-return.schema.json`) and `egm-draft/references/design_doc.md` ship
  with the package while the test files do not
  [`scripts/pack_plugin.py:REQUIRED_SHARED`].
- `tests/`: `conftest.py` (`repo_root` and `discovered_skills` fixtures),
  eighteen offline modules under `unit/`, opt-in live probes under
  `integration/` (`test_claude.py`, `test_codex.py`, the Copilot, Cursor, and
  OpenCode probe scripts, and the `opencode-ci/` npm fixture), and
  `scope_advisory.cjs`, a Node `--test` harness that executes the PR-scope
  workflow script against a fake GitHub API
  [`tests/unit/test_scope_advisory.py`]. Repository-only.

## Global Invariants

- **One identity.** `name`, `version`, and `description` in
  `.claude-plugin/plugin.json` and `.codex-plugin/plugin.json` must equal
  `plugin.json`; both marketplace catalogs resolve to this directory with
  `source: "./"`; a release tag `vMAJOR.MINOR.PATCH` must match all three
  manifest versions
  [`tests/unit/test_harnesses.py:test_compatibility_metadata_matches_root`, `scripts/prepare_release.py:version_for_tag`].
- **Exactly seven skills.** Skill names are `egm-bootstrap`,
  `egm-brainstorm`, `egm-draft`, `egm-drift-report`, `egm-resolve`,
  `egm-review`, and `egm-review-loop`, unique across `skills/*/SKILL.md`. Each
  `SKILL.md` body is at most 24,000 bytes (the Antigravity load limit); each
  `test_scenarios.yaml` names its directory in `skill` and lists scenarios with
  `scenario_id`, `eval_type`, and non-empty `turns`; each `agents/openai.yaml`
  `short_description` is 25 to 64 characters and its icons are SVG files
  inside the skill
  [`tests/unit/test_harnesses.py:EXPECTED_SKILLS`, `tests/unit/test_skill_load_limits.py`, `tests/unit/test_scenario_coverage.py`, `tests/unit/test_packaging.py`].
- **Canonical personas, thin adapters.** Persona names in `agents/` are unique
  and carry no `tools` or `omitClaudeMd` keys; every host adapter re-declares
  the same `name` and points back to the canonical file. Claude reviewers are
  limited to `Read`, `Grep`, and `Glob` with `omitClaudeMd: true` and no
  `memory`; Copilot reviewers to `read` and `search`; Cursor reviewers to
  `readonly`; OpenCode reviewers deny everything except bundle reads. The
  synthesizer and bootstrap orchestrator have native adapters for Claude only
  [`tests/unit/test_harnesses.py:test_claude_reviewers_are_read_only_with_fresh_context`, `tests/unit/test_copilot_adapter.py`, `adapters/opencode/install.py:REVIEWERS`].
- **Goldfish isolation.** A reviewer receives only its task, the target, the
  named standards, and an explicit reading list; it never receives parent
  history, memory, or earlier findings unless the canonical stage requires
  them; a reviewer that cannot read a required file returns an incomplete
  review, never a verdict; the parent writes every report and preserves every
  human approval gate
  [`.cursor-plugin/rules/egm.mdc`, `com.github.copilot/agents/egm-design.agent.md`].
- **Design-only execution.** Skills must not write production source files;
  scratch code goes to the harness scratch directory or a fresh `mktemp -d`
  path, never a fixed shared path; one question per turn; explicit consent at
  every step transition; no status summaries; a detected contradiction halts
  all file writes in that turn
  [`resources/execution_instructions.md`, `tests/unit/test_harnesses.py:test_scratch_files_use_private_directories`].
- **No hooks, MCP, or apps.** No shipped manifest may declare `hooks`,
  `mcpServers`, `mcp`, or `apps`; `.claude-plugin/hooks/` and
  `hooks/hooks.json` must not exist; permissions stay under user control
  [`scripts/pack_plugin.py:build`, `tests/unit/test_harnesses.py:test_claude_permissions_remain_under_user_control`].
- **Allowlisted, reproducible packages.** Only `SHARED` plus the target's
  `HOST` globs ship; `CONTRIBUTING.md`, `AI_POLICY.md`, `TESTING.md`,
  `.github/`, `.agents/`, `site/`, `tests/`, `docs/designs/`,
  `docs/directory.md`, marketplace catalogs, hooks, `test_scenarios.yaml`, and
  `TEST.md` never ship; ZIP entries use fixed 1980-01-01 timestamps and mode
  `0644`; symlinked runtime paths, escaping manifest references, and existing
  outputs are rejected
  [`scripts/pack_plugin.py:SHARED`, `tests/unit/test_packaging.py:test_runtime_bundle_is_complete_and_reproducible`].
- **Published runtime freshness.** `distributions/claude/` must equal a fresh
  `claude` build byte for byte, so any change to `README.md`, `skills/`,
  `agents/`, `resources/`, `assets/`, the bundled `docs/` guides, or a
  manifest must regenerate that folder in the same change
  [`tests/unit/test_packaging.py:test_published_claude_runtime_is_current`].
- **Links and tables.** Every relative Markdown link outside dot-directories
  and `node_modules` must resolve on disk, both in this tree and inside the
  built runtime folder, and every README `<img src>` must be a bundled path;
  files that do not ship are therefore referenced by absolute GitHub URL.
  Intra-document anchors must match GitHub heading slugs, and tables must not
  use g3doc `:` continuation rows
  [`tests/unit/test_link_integrity.py`, `tests/unit/test_markdown_tables.py`, `tests/unit/test_packaging.py`].
- **Shared skill artwork.** Each skill icon is a `0 0 24 24` viewBox SVG with
  a `<title>` whose fills and strokes are exactly two colours per family:
  `#1b6ef3` and `#7cacf8` for bootstrap, brainstorm, draft, and resolve;
  `#e86e00` and `#ff8d41` for drift-report, review, and review-loop; the site
  imports the same files
  [`tests/unit/test_packaging.py:test_skill_icon_and_host_palette_match`].
- **Contribution scope.** A change over 100 non-test lines or touching three
  or more core files in `skills/` or `agents/` needs a merged design document
  in `docs/designs/` first; `docs/**`, `README.md`, `TEST.md`, lockfiles, and
  tests are excluded from the count; every PR description must be the filled
  template with a checked human accountability affirmation; no autonomous PRs
  and no artificial PR splitting
  [`.github/workflows/pr-scope-advisory.yml`, `AI_POLICY.md`, `AGENTS.md`].
- **CI gate.** The `CI` job must wait for every validation job and fails on
  any non-success result; the unit matrix runs on Ubuntu and Windows with
  `fail-fast: false`; the release workflow installs the test group before
  checking out the tag [`tests/unit/test_ci_workflow.py`].

## Global Side Effects

- **Plugin runtime.** The package operates no hosted service, database,
  analytics client, or telemetry endpoint and needs no EGM account. Skills
  read the project files and documents the user supplies and write briefs,
  design documents, README files, and review reports into the working
  directory or the folder named by an `EGM artifact directory:` line; the
  host processes prompts under the user's own account. Bootstrap may run
  local discovery commands and a project-configured formatter, which can
  contact a package registry, under the host's permission controls
  [`docs/privacy.md`].
- **`scripts/pack_plugin.py:build`** creates `egm-<target>/` and
  `egm-<target>.zip` under `--output`, refuses existing paths, and stages the
  archive through a temporary `.egm-*` directory that is removed afterwards.
- **`scripts/prepare_release.py:prepare`** creates the output directory,
  writes `egm-claude-<version>.zip`, `egm-openai-<version>.zip`,
  `SHA256SUMS`, and `RELEASE_NOTES.md`, and deletes the whole directory if any
  step fails.
- **`adapters/opencode/install.py:install`** creates a new installation
  directory outside the source tree containing `bundle/`, `skills/` symlinks,
  `opencode.json`, and `installation.json`; it never modifies the user's
  OpenCode configuration.
- **Site tooling.** `npm run build` writes `site/dist/`; `npm run capture`
  rebuilds and regenerates `site/public/og.png` and `site/screenshots/*.png`
  with a local Chrome; `.github/workflows/deploy-site.yml` publishes
  `site/dist/` to GitHub Pages at `egm.dev` on pushes to `main` that touch
  `site/**`, `skills/*/assets/*.svg`, or the workflow itself
  [`.github/workflows/deploy-site.yml`].
- **Release automation.** `.github/workflows/release.yml` runs only by manual
  dispatch from `main`, checks out an existing tag contained in `main`, runs
  the unit suite, builds and attests the archives, uploads a 7-day artifact,
  and creates a draft GitHub release; publication stays manual
  [`.github/workflows/release.yml`].
- **PR automation.** `.github/workflows/pr-scope-advisory.yml` runs on
  `pull_request_target`, creates, updates, or deletes one signed advisory
  comment, adds or removes the `design-needed` label, removes the legacy
  `advisory: design-doc-suggested` label, and fails the check when the PR body
  does not match the template; it never checks out PR code. Dependabot opens
  weekly grouped update PRs for `site/` npm packages and GitHub Actions
  [`.github/workflows/pr-scope-advisory.yml`, `.github/dependabot.yml`].
- **Opt-in live tests.** `EGM_CLAUDE_LIVE=1` and `EGM_CODEX_LIVE=1` invoke
  authenticated host CLIs, consume the account's model quota, and inspect the
  transcripts of their own sessions; the Codex suite creates and removes a
  temporary local marketplace. The native probe workflows for Copilot,
  Cursor, and OpenCode run offline on pull requests [`TESTING.md`].

## System Verification

- Run: `pytest tests/unit`
- Setup (Python 3.10 or newer, pip 25.1 or newer, and Node.js 22 or newer for
  the scope-advisory test): `python3 -m venv .venv && source .venv/bin/activate && python -m pip install --upgrade "pip>=25.1" && python -m pip install --group test`
- Site: `cd site && npm ci && npm test && npm run check && npm run build`
- Runtime packages: `python3 scripts/pack_plugin.py --target claude --output /tmp/egm-release` and the same with `--target openai`; after any source change, replace `distributions/claude` with the generated `egm-claude/` folder and rerun `pytest tests/unit`.
- Opt-in live probes (these consume model quota): `EGM_CLAUDE_LIVE=1 pytest tests/integration/test_claude.py` and `EGM_CODEX_LIVE=1 pytest tests/integration/test_codex.py -v`; see [Testing](https://github.com/google/elephant-goldfish-model/blob/main/TESTING.md).

## Contribute

See the [accessibility statement](https://github.com/google/elephant-goldfish-model/blob/main/ACCESSIBILITY.md)
for accessibility goals, known limits, and how to report barriers.

Read [contributing](https://github.com/google/elephant-goldfish-model/blob/main/CONTRIBUTING.md) for PRs, [issues](https://github.com/google/elephant-goldfish-model/issues) for bugs, and [discussions](https://github.com/google/elephant-goldfish-model/discussions) for questions.

## License

[Apache 2.0](LICENSE). This is not an officially supported Google product.
