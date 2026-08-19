# GitHub Showcase + OSS Design

**Date:** 2026-08-19
**Horizon:** 4 weeks
**Primary objective:** Improve recruitment impact while strengthening a focused open-source presence.

## 1. Success definition

At the end of the four-week cycle:

- A recruiter can understand the profile positioning and reach the strongest work in under 60 seconds.
- No pinned repository looks abandoned or contradicts the quality claims made on the profile.
- `memos` can be discovered, installed, exercised, and understood by a newcomer without private environment knowledge.
- `ai-battle-simulator` offers a reproducible no-key demonstration through its scripted mode and clearly exposes its engineering decisions and measured results.
- Important claims about tests, compatibility, performance, releases, and supported workflows are verifiable.
- GitHub profile, portfolio, and CV tell the same professional story.
- Work remains focused on existing projects; new features enter scope only when they remove an adoption blocker or materially strengthen professional evidence.

## 2. Positioning

The primary positioning is:

> Full-stack developer who builds usable products and real software systems, with a strong specialization in AI-agent infrastructure and reliability.

The profile must remain understandable to general full-stack recruiters. AI-agent infrastructure is the differentiator, not a replacement for the broader engineering profile.

## 3. Repository hierarchy

### Tier 1 — Flagships

1. `memos` — flagship open-source product and AI-agent infrastructure project.
2. `ai-battle-simulator` — flagship engineering, experimentation, deterministic systems, and LLM orchestration project.

These receive the deepest work during the month.

### Tier 2 — Complementary evidence

3. `full-stack-portfolio` — frontend/full-stack quality and product presentation.
4. `mcp-audit` — developer tooling, security, CI, and MCP ecosystem knowledge.
5. `trajectory-monitor` — AI-agent reliability and observability.
6. `jobflow-assistant` — substantial end-to-end product/application work.

These complete the six-project public showcase. Work is limited to issues that materially affect credibility or presentation.

### Tier 3 — Supporting laboratory

Repositories such as `heartbeat`, `pulse`, `repoready`, `agent-cost-tracker`, and `near-earth-visualizer` remain accessible but do not compete with the six showcase repositories. Private workspaces remain operational/internal artifacts rather than portfolio products.

## 4. Four-week structure

### Week 1 — Showcase baseline

Goal: make the GitHub account immediately credible before deeper OSS work begins.

Scope:

- Audit and refine the `Mars375` profile README.
- Verify profile facts, contact information, project links, descriptions, topics, and pinned-repository selection.
- Present the two flagships first and the four complementary projects second.
- Replace the default `create-next-app` README in `near-earth-visualizer` with project-specific documentation.
- Fix RepoReady's visible repository-readiness contradictions: committed `.env.example`, test command, and appropriate validation/CI where supported by the current codebase.
- Replace the screenshot TODO in `agent-cost-tracker` with useful product evidence if a reproducible UI is available; otherwise remove the empty promise until evidence exists.
- Avoid feature development unless required to make an existing documented flow truthful and reproducible.

### Week 2 — MemOS OSS product hardening

Goal: make MemOS usable and understandable as an independent open-source product.

Audit the complete newcomer path:

1. Discover the repository.
2. Understand the problem and intended users.
3. Choose an installation path.
4. Install from the documented source/package.
5. Complete the smallest useful learn/recall flow.
6. Understand MCP/REST/Docker options without reading implementation code.
7. Find troubleshooting, contribution, security, release, and compatibility information.

Changes prioritize adoption blockers, documentation correctness, CI/test truthfulness, packaging/release hygiene, contribution flow, security guidance, and reproducibility. New MemOS capabilities are out of scope unless required to repair one of these flows.

### Week 3 — AI Battle Simulator flagship hardening

Goal: turn the existing technically deep repository into a highly legible engineering case study.

The golden path is the no-key scripted battle. A newcomer must be able to clone the repository, install dependencies, run a scripted battle, and view/understand the resulting replay without configuring an LLM provider.

Documentation must clearly expose:

- the model-decides / engine-resolves boundary;
- deterministic/replayable behavior;
- ruleset/versioning strategy;
- provider routing and rate-limit lessons;
- measured experimental findings;
- test/replay verification;
- what can be reproduced offline versus what requires provider credentials.

Visual evidence is added only when it improves comprehension of the battle/replay experience. Claims are validated against current commands and tests rather than copied from stale documentation.

### Week 4 — Cross-surface consistency and validation

Goal: validate the entire public story from an outsider's perspective.

Scope:

- Review GitHub profile -> flagship -> install -> demo -> portfolio -> GitHub loop.
- Check public links and remove or correct broken/stale destinations.
- Compare GitHub positioning with portfolio and CV language.
- Perform clean-environment installation/reproduction checks for both flagships.
- Review screenshots/media on relevant viewport sizes when applicable.
- Perform a recruiter-style 60-second review and a newcomer-style OSS review.
- Fix only issues discovered by those validations; defer unrelated ideas.
- Prepare a small, evidence-based OSS visibility pass only after newcomer flows are sound.

## 5. Common repository release gate

Every repository touched during this initiative is evaluated using the same gate.

### Discovery

The README and repository metadata explain the problem, intended audience, current status, and why the project exists.

### Reproducibility

Documented setup commands are tested from a clean checkout where practical. Required environment variables and optional integrations are distinguished clearly.

### Quality

Applicable lint, typecheck, tests, build, packaging, or smoke checks are executed. README claims are updated when reality differs.

### OSS readiness

Required deeply for `memos` and `ai-battle-simulator`: licensing, contribution path, security guidance, releases/changelog where relevant, issue/discussion guidance where useful, and newcomer documentation.

### Evidence

Screenshots, GIFs, diagrams, benchmarks, test counts, or measurements are included only when they demonstrate something useful and current.

### Recruiter review

For each showcase repository, the answer to “what does this prove about the developer?” must be obvious without requiring a full source-code review.

## 6. Change discipline

- No new repository is created during this four-week initiative.
- No unrelated feature work is included.
- Feature ideas discovered during cleanup are deferred unless they block adoption or invalidate an important professional claim.
- Changes are split into reviewable commits with focused purposes such as `docs:`, `test:`, `ci:`, and `fix:`.
- Existing repository architecture and conventions are followed unless they directly prevent the required outcome.
- Validation happens after each meaningful change rather than only at the end of the month.

## 7. Review criteria by audience

### Recruiter

Within 60 seconds, the reviewer should understand:

- the developer is full-stack;
- the work includes real backend/infrastructure concerns, not only UI demos;
- AI-agent infrastructure/reliability is a distinctive specialization;
- the two strongest projects are obvious;
- there are concrete quality signals rather than unsupported technology lists.

### Open-source newcomer

For each flagship, the reviewer should be able to answer:

- What problem does this solve?
- Is it for me?
- What is the fastest way to try it?
- What requires credentials or external infrastructure?
- What is stable versus experimental?
- Where do I report a problem or contribute?

## 8. Explicit non-goals

This initiative does not attempt to:

- make every repository production-ready;
- give every repository identical README structure or branding;
- maximize repository count, commit count, or badge count;
- invent usage numbers, benchmarks, compatibility, or maturity claims;
- convert private agent workspaces into public products;
- add major features to Pulse, Heartbeat, RepoReady, JobFlow, or other supporting projects;
- reposition the profile so narrowly around AI that ordinary full-stack work becomes invisible.
