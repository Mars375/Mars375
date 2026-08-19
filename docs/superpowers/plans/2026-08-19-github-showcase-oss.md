# GitHub Showcase + OSS Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Turn Mars375's GitHub into a recruiter-friendly showcase while hardening MemOS and AI Battle Simulator as the two flagship open-source projects over four weeks.

**Architecture:** Treat the account as a three-tier portfolio rather than normalizing every repository. Week 1 fixes navigation and obvious credibility gaps, Weeks 2–3 independently harden one flagship each through evidence-driven newcomer flows, and Week 4 validates consistency across GitHub, demos, portfolio, and CV. Repository changes remain independent and reviewable; feature work is excluded unless required for reproducibility or truthful documentation.

**Tech Stack:** GitHub profile/metadata, Markdown, GitHub Actions, Python packaging/pytest for MemOS and Python tools, Node.js/npm/Vitest/TypeScript for relevant TypeScript repositories, Docker where already supported.

**Spec:** `docs/superpowers/specs/2026-08-19-github-showcase-oss-design.md`

## Global Constraints

- Duration: 4 weeks.
- Primary objective: recruitment impact plus focused open-source maturity.
- Flagships: `Mars375/memos` and `Mars375/ai-battle-simulator`.
- Complementary showcase: `full-stack-portfolio`, `mcp-audit`, `trajectory-monitor`, `jobflow-assistant`.
- Do not create new repositories during this initiative.
- Do not add unrelated product features.
- Do not invent benchmarks, compatibility, maturity, test counts, or adoption claims.
- Validate documented commands against the repository state before strengthening any claim.
- Keep private operational workspaces private and outside the public showcase.

---

## Week 1 — Make the showcase credible immediately

### Task 1: Rebuild the profile hierarchy around two flagships

**Files:**
- Modify: `Mars375/Mars375:README.md`
- Reference: `Mars375/Mars375:docs/superpowers/specs/2026-08-19-github-showcase-oss-design.md`

**Interfaces:**
- Consumes: current public repository names and verified public links.
- Produces: profile navigation with `memos` and `ai-battle-simulator` first, then four complementary projects.

- [ ] **Step 1: Capture the current profile baseline**

Record the current headline, location, contact links, selected-project ordering, and project descriptions. Flag any factual field that cannot be verified rather than silently rewriting it.

- [ ] **Step 2: Verify all six showcase repository destinations**

Check that these public repository links resolve: `memos`, `ai-battle-simulator`, `full-stack-portfolio`, `mcp-audit`, `trajectory-monitor`, `jobflow-assistant`.

Expected: six valid destinations. Any failure becomes a blocking fix before profile publication.

- [ ] **Step 3: Rewrite the profile information architecture**

Use this order:

```markdown
# Loïc Rossi

**Full-stack developer building usable products and software systems, with a strong focus on AI-agent infrastructure and reliability.**

## Flagship projects
### MemOS
[problem + concrete engineering proof + repository link]

### AI Battle Simulator
[problem + concrete engineering proof + repository link]

## More selected work
- full-stack-portfolio — [proof]
- mcp-audit — [proof]
- trajectory-monitor — [proof]
- jobflow-assistant — [proof]

## Stack
[concise grouped stack]

## Contact
[verified contact/location/portfolio]
```

Do not add unsupported usage numbers, star counts, performance claims, or labels such as “production-ready”.

- [ ] **Step 4: Review the profile with the 60-second test**

Without opening source code, answer in writing:

```text
What does this developer build?
What are the two strongest projects?
What proves full-stack ability?
What is the differentiating specialization?
```

Expected: all four answers are obvious from the README alone.

- [ ] **Step 5: Commit**

```bash
git add README.md
git commit -m "docs: sharpen GitHub profile showcase"
```

### Task 2: Replace the Near Earth Visualizer starter README

**Files:**
- Modify: `Mars375/near-earth-visualizer:README.md`
- Inspect: `Mars375/near-earth-visualizer:package.json`
- Inspect: application entry points and data-source/configuration files discovered from the repository tree

**Interfaces:**
- Consumes: actual application behavior, scripts, data sources, and environment requirements.
- Produces: project-specific setup and explanation with no create-next-app boilerplate.

- [ ] **Step 1: Inspect the repository before writing claims**

Identify the actual purpose, data source, rendering/visualization approach, required environment variables, npm scripts, and whether a deployed URL exists.

- [ ] **Step 2: Run the existing validation commands**

Run only scripts actually declared by `package.json`, beginning with install and then applicable lint/test/build commands.

Expected: record exact pass/fail state. Do not conceal failures in documentation.

- [ ] **Step 3: Write the replacement README**

Required sections:

```markdown
# Near Earth Visualizer
[one-paragraph purpose]

## What it shows
[actual user-visible behavior]

## How it works
[data -> processing -> visualization]

## Local setup
[verified commands]

## Configuration
[only real environment variables]

## Validation
[commands that actually exist]

## Project status
[truthful maturity statement]
```

- [ ] **Step 4: Verify every README command from a clean shell**

Expected: each documented command either succeeds or is explicitly documented with its real prerequisite.

- [ ] **Step 5: Commit**

```bash
git add README.md
git commit -m "docs: replace starter README with project guide"
```

### Task 3: Make RepoReady pass its own readiness expectations

**Files:**
- Inspect/Modify: `Mars375/repoready:package.json`
- Create if justified by code references: `Mars375/repoready:.env.example`
- Inspect/Modify: `Mars375/repoready:.github/workflows/*`
- Modify if needed after verification: `Mars375/repoready:README.md`
- Test: existing `*.test.*` / `*.spec.*` files discovered in repository

**Interfaces:**
- Consumes: current Vitest tests and actual environment-variable references.
- Produces: one documented test command, a non-secret environment template, and CI that invokes the repository's real quality gate if CI is already appropriate for the project.

- [ ] **Step 1: Enumerate environment variables from source**

Search for `process.env` and framework-specific environment access. Classify each variable as required, optional, public, or secret. Never copy values from deployed environments.

- [ ] **Step 2: Create `.env.example` with names only**

Example form:

```dotenv
DATABASE_URL=
GITHUB_TOKEN=
# Add Clerk/AI variables only when current source actually reads them.
```

Expected: no credential values or realistic secret placeholders.

- [ ] **Step 3: Run Vitest directly before adding a script**

```bash
npx vitest run
```

Expected: tests execute. If they fail, fix only failures required to restore the already-present suite before proceeding.

- [ ] **Step 4: Add the package script**

Add to the existing `scripts` object without deleting existing commands:

```json
"test": "vitest run"
```

- [ ] **Step 5: Run the repository gate**

```bash
npm run test
npm run lint
npm run build
```

Expected: PASS. If an external-service prerequisite prevents a build, document and isolate it rather than claiming success.

- [ ] **Step 6: Align README and CI with the verified gate**

Remove the statement that no test script exists. If a workflow exists, make it call the verified install/lint/test/build commands using the repository's package manager and supported Node version.

- [ ] **Step 7: Commit in reviewable units**

```bash
git add .env.example package.json package-lock.json
git commit -m "chore: add reproducible RepoReady setup"

git add .github README.md
git commit -m "ci: verify RepoReady quality gate"
```

### Task 4: Resolve Agent Cost Tracker's empty screenshot promise

**Files:**
- Modify: `Mars375/agent-cost-tracker:README.md`
- Create only if generated from the current app: repository media under the project's existing documentation/media convention

**Interfaces:**
- Consumes: reproducible local dashboard state.
- Produces: either current visual evidence or a README with no unfulfilled screenshot TODO.

- [ ] **Step 1: Start the documented local application path**

Use the current documented Docker or development command. Confirm the dashboard renders with a reproducible state.

- [ ] **Step 2: Choose based on evidence availability**

If the dashboard can be rendered deterministically, capture one useful overview image and one detail view at most. If not, remove the `<!-- TODO: Add screenshots after deployment -->` section entirely.

- [ ] **Step 3: Verify README media references**

Expected: every referenced image exists in the repository and renders from GitHub.

- [ ] **Step 4: Commit**

```bash
git add README.md docs public assets 2>/dev/null || true
git commit -m "docs: add current agent cost tracker evidence"
```

Use the actual media paths instead of blindly staging nonexistent directories.

---

## Week 2 — Harden MemOS as the primary OSS product

### Task 5: Audit MemOS's newcomer golden path

**Files:**
- Inspect: `Mars375/memos:README.md`
- Inspect: `Mars375/memos:pyproject.toml`
- Inspect: CLI entry-point modules discovered from `pyproject.toml`
- Inspect: `.github/workflows/*`
- Inspect: existing tests and package/release configuration
- Create: `docs/oss/newcomer-audit.md` only if the repository has no equivalent audit document

**Interfaces:**
- Consumes: published package/install claims and current CLI behavior.
- Produces: an evidence list of blockers for install -> learn -> recall -> serve/MCP.

- [ ] **Step 1: Create a clean Python environment**

Use a supported Python version declared by the project. Do not reuse a developer environment containing undeclared dependencies.

- [ ] **Step 2: Test the minimal package path**

Execute the README's simplest supported install, then:

```bash
memos learn "GitHub showcase audit memory" --tags audit
memos recall "showcase audit"
```

Expected: installation and both commands succeed without requiring optional vector infrastructure when the README claims they do.

- [ ] **Step 3: Test one documented server path**

Run the documented server command and verify the documented health endpoint and one relevant docs/dashboard/MCP discovery endpoint.

Expected: HTTP success matching current documentation.

- [ ] **Step 4: Record every mismatch**

For each mismatch record:

```markdown
- Claim:
- Observed behavior:
- Reproduction command:
- Classification: docs | packaging | bug | external prerequisite
- Smallest acceptable fix:
```

- [ ] **Step 5: Commit the audit only if it has durable value**

```bash
git add docs/oss/newcomer-audit.md
git commit -m "docs: record MemOS newcomer audit"
```

If an equivalent durable document already exists, update that instead of creating duplication.

### Task 6: Repair MemOS newcomer blockers using TDD

**Files:**
- Modify: exact source files identified by Task 5
- Test: nearest existing test module for each broken behavior
- Modify: README only after behavior is verified

**Interfaces:**
- Consumes: Task 5 blocker list.
- Produces: passing minimal install/learn/recall/server path.

For **each actual behavioral blocker**, repeat Steps 1–5 independently rather than combining unrelated fixes.

- [ ] **Step 1: Write a failing regression test**

Add the smallest test reproducing the observed blocker using the project's existing pytest patterns.

- [ ] **Step 2: Verify the regression test fails for the expected reason**

```bash
pytest path/to/test_module.py::test_specific_regression -v
```

Expected: FAIL because of the audited behavior, not because the test is malformed.

- [ ] **Step 3: Implement the minimum fix**

Change only the code needed for that regression. Do not add adjacent features.

- [ ] **Step 4: Run focused then full validation**

```bash
pytest path/to/test_module.py::test_specific_regression -v
pytest
```

Then run the repository's configured lint/type/package checks from CI.

Expected: PASS.

- [ ] **Step 5: Commit that blocker independently**

```bash
git add <test-files> <source-files>
git commit -m "fix: unblock MemOS <specific newcomer flow>"
```

### Task 7: Make MemOS OSS governance discoverable

**Files:**
- Inspect/Create/Modify as needed: `CONTRIBUTING.md`
- Inspect/Create/Modify as needed: `SECURITY.md`
- Inspect/Modify: `CHANGELOG.md`
- Inspect/Modify: issue templates under `.github/ISSUE_TEMPLATE/`
- Modify: `README.md`

**Interfaces:**
- Consumes: actual test commands, supported Python versions, release process, and security contact mechanism.
- Produces: newcomer paths for contribution, vulnerability reporting, and release history.

- [ ] **Step 1: Inventory existing governance files before creating anything**

Expected: reuse existing files and conventions; no duplicate contribution/security documents.

- [ ] **Step 2: Verify contributor setup commands**

Run the exact editable/dev install and test/lint commands that will be documented.

- [ ] **Step 3: Add or repair contribution guidance**

At minimum document: supported Python version(s), dev install, focused/full tests, lint/format commands actually configured, PR expectations, and where architectural changes should be discussed.

- [ ] **Step 4: Add or repair security guidance**

Document a private vulnerability-reporting route supported by the repository/account. Do not instruct reporters to publish exploitable vulnerabilities in a public issue.

- [ ] **Step 5: Validate release/changelog claims**

Ensure README badges/version language and changelog/release references agree with the current package/repository state.

- [ ] **Step 6: Run the full MemOS gate**

Execute the same checks used by CI, including all supported test environments that are practical locally and Docker/package smoke checks where already configured.

Expected: PASS or an explicitly documented external limitation.

- [ ] **Step 7: Commit**

```bash
git add README.md CONTRIBUTING.md SECURITY.md CHANGELOG.md .github
git commit -m "docs: strengthen MemOS contributor and security paths"
```

Stage only files that exist or were intentionally created.

---

## Week 3 — Make AI Battle Simulator the engineering flagship

### Task 8: Verify the zero-key scripted golden path

**Files:**
- Inspect: `Mars375/ai-battle-simulator:README.md`
- Inspect: root `package.json` and workspace manifests
- Inspect: CLI/player entry points
- Test: existing engine/replay/CLI tests
- Create/update: an existing QA/audit document if one exists rather than duplicating it

**Interfaces:**
- Consumes: scripted battle command and replay player.
- Produces: verified clone -> install -> scripted battle -> replay-view flow with no provider credentials.

- [ ] **Step 1: Use a clean checkout with provider keys unset**

Confirm `OPENROUTER_API_KEY`, `GROQ_API_KEY`, `NVIDIA_API_KEY`, and `MISTRAL_API_KEY` are absent from the test environment.

- [ ] **Step 2: Install exactly as documented**

```bash
npm install
```

Expected: successful workspace installation using the repository's supported Node/npm versions.

- [ ] **Step 3: Run the offline battle**

```bash
npm run battle -- --scripted
```

Expected: successful battle and replay output without network/provider credentials.

- [ ] **Step 4: Run the player path**

```bash
npm run player:dev
```

Open the generated replay through the documented player workflow.

Expected: replay is viewable and understandable without running a remote model.

- [ ] **Step 5: Run the full advertised gate**

```bash
npm test
npm run typecheck
```

Also run lint/build commands if they exist in the current package scripts.

Expected: PASS. Compare actual test count/output with README claims and correct stale numbers.

- [ ] **Step 6: Record and classify mismatches**

Use the same Claim / Observed / Reproduction / Classification / Smallest fix format as MemOS.

### Task 9: Repair AI Battle Simulator golden-path regressions

**Files:**
- Modify: exact package(s) implicated by Task 8
- Test: nearest package test file
- Modify: README only after implementation truth is restored

**Interfaces:**
- Consumes: Task 8 mismatch list.
- Produces: reproducible scripted battle and replay flow.

For each behavioral mismatch:

- [ ] **Step 1: Add the smallest failing regression test**

Use the package's current Vitest/test conventions and test the public behavior rather than implementation details.

- [ ] **Step 2: Run focused test and confirm expected failure**

```bash
npm test -- <relevant-test-filter>
```

Use the repository's actual test filtering syntax discovered from package scripts.

- [ ] **Step 3: Implement the minimal repair**

Preserve the documented architectural invariant: model decisions remain separate from deterministic engine resolution.

- [ ] **Step 4: Run focused and complete checks**

```bash
npm test
npm run typecheck
```

Expected: PASS.

- [ ] **Step 5: Commit independently**

```bash
git add <source-files> <test-files>
git commit -m "fix: restore scripted battle <specific behavior>"
```

### Task 10: Restructure ABS documentation for progressive disclosure

**Files:**
- Modify: `README.md`
- Reuse/Modify: existing `docs/spec/*`, `docs/architecture/*`, `docs/research/*`, `docs/reports/*`
- Add media only under the repository's existing documentation/media convention

**Interfaces:**
- Consumes: verified Task 8/9 behavior and existing deep documentation.
- Produces: README optimized for a first-time visitor while preserving deep technical evidence in linked docs.

- [ ] **Step 1: Move the fastest proof near the top**

The first screen/sections must establish:

```text
What is this?
Why is it technically interesting?
How do I run the no-key demo?
Where can I see the replay?
```

- [ ] **Step 2: Preserve the key engineering narrative**

Keep concise explanations of:

```text
model decides -> engine resolves
deterministic replay verification
provider/rate-limit measurements
ruleset versioning
fidelity/accuracy measurements
```

Move detailed experimental evidence to the existing research/report docs rather than deleting it.

- [ ] **Step 3: Add current visual evidence if reproducible**

Prefer one replay overview and, if useful, one fog-of-war/faction-view example. Do not add decorative images unrelated to understanding the simulator.

- [ ] **Step 4: Verify every command and internal doc link**

Expected: no broken relative links and no stale command/test-count claims.

- [ ] **Step 5: Commit**

```bash
git add README.md docs <actual-media-paths>
git commit -m "docs: sharpen AI Battle Simulator flagship story"
```

---

## Week 4 — Validate the public story end-to-end

### Task 11: Audit all six showcase repositories from the profile

**Files:**
- Modify only repositories with issues discovered during the audit
- Modify: `Mars375/Mars375:README.md` if project descriptions no longer match verified reality

**Interfaces:**
- Consumes: Week 1–3 final repository states.
- Produces: consistent public navigation and truthful project summaries.

- [ ] **Step 1: Start from the GitHub profile without using private context**

For each showcased project record:

```markdown
- Purpose understood in <= 15 seconds: yes/no
- Setup path obvious: yes/no/not applicable
- Quality evidence visible: yes/no
- Current status clear: yes/no
- Broken links: [list]
- What this proves professionally: [one sentence]
```

- [ ] **Step 2: Fix only failed audit items**

Do not introduce redesigns or features that are unrelated to an observed failure.

- [ ] **Step 3: Re-run affected repository gates**

Expected: validation remains green after documentation/presentation corrections.

- [ ] **Step 4: Commit fixes per repository**

Use a focused `docs:`, `fix:`, or `ci:` commit for each repository rather than one cross-repo catch-all commit.

### Task 12: Perform clean-environment flagship verification

**Files:**
- No source changes unless verification discovers a defect
- Update README/tests only for verified defects

**Interfaces:**
- Consumes: final MemOS and ABS documentation.
- Produces: evidence that both golden paths work without developer-machine assumptions.

- [ ] **Step 1: Verify MemOS in a fresh environment**

Repeat install -> learn -> recall -> server/health using only public documentation.

Expected: PASS.

- [ ] **Step 2: Verify ABS in a fresh environment**

Repeat install -> scripted battle -> replay/player with provider keys unset.

Expected: PASS.

- [ ] **Step 3: If a failure appears, add regression coverage before fixing it**

Follow Task 6 for MemOS or Task 9 for ABS. Do not patch undocumented environment assumptions manually.

- [ ] **Step 4: Re-run full repository gates after any repair**

Expected: PASS.

### Task 13: Align GitHub, portfolio, and CV claims

**Files:**
- Inspect/Modify: `Mars375/full-stack-portfolio` content files that define profile/project copy
- Modify: `Mars375/Mars375:README.md`
- CV: update only in its actual source repository/file if available; otherwise produce a discrepancy list rather than inventing a file location

**Interfaces:**
- Consumes: verified flagship descriptions and current professional positioning.
- Produces: one consistent narrative across public surfaces.

- [ ] **Step 1: Build a claim matrix**

Use these rows:

```text
Headline/role
Primary specialization
MemOS description
AI Battle Simulator description
Full-stack evidence
Location
Portfolio URL
Contact email
```

Columns: GitHub profile / portfolio / CV.

- [ ] **Step 2: Resolve contradictions using verified facts**

Do not copy one surface blindly to the others. Keep copy appropriate to each surface while preserving factual consistency.

- [ ] **Step 3: Run the portfolio's existing release gate after copy changes**

Use its documented `npm run verify` gate if still present in the current repository.

Expected: lint, TypeScript, Vitest, and production build all succeed as configured by the project.

- [ ] **Step 4: Commit per surface**

```bash
git commit -m "docs: align portfolio project positioning"
git commit -m "docs: align GitHub profile positioning"
```

Create only commits corresponding to files actually changed.

### Task 14: Final recruiter and OSS acceptance review

**Files:**
- No mandatory file changes
- Update the design/plan only with completion notes if the repository convention supports tracked execution status

**Interfaces:**
- Consumes: all completed tasks.
- Produces: go/no-go decision for the four-week initiative.

- [ ] **Step 1: Run the recruiter acceptance test**

From the profile alone, verify within 60 seconds:

```text
Full-stack positioning is clear.
MemOS and AI Battle Simulator are obviously the flagships.
AI-agent infrastructure/reliability is visible as a specialization.
At least one project proves substantial application/full-stack work.
No pinned/showcase repository looks abandoned.
```

- [ ] **Step 2: Run the OSS acceptance test for MemOS**

A newcomer can answer what it solves, install it, execute a useful memory flow, find server/MCP options, understand optional infrastructure, and locate contribution/security guidance.

- [ ] **Step 3: Run the OSS/engineering acceptance test for ABS**

A newcomer can execute the offline scripted path, view a replay, understand model-vs-engine responsibility, and find the deeper evidence for deterministic behavior and provider experiments.

- [ ] **Step 4: Run final link and claim checks**

Check public repository links, portfolio links, internal README links, badges, version references, and documented validation commands.

Expected: no known broken public path or knowingly stale factual claim.

- [ ] **Step 5: Close the initiative**

Create a short completion note containing only:

```markdown
## Completed
[verified outcomes]

## Deferred
[feature ideas deliberately excluded by scope]

## Next OSS opportunities
[maximum three evidence-based follow-ups]
```

Do not turn the completion review into another feature roadmap.
