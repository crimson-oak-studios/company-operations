# AI Development Company Workflow Playbook

Version: 2.0  
Owner: Company COO / Human Owner  
Purpose: Define the repeatable operating process for an AI-assisted web/software development company using ChatGPT agents, Codex, GitHub, and human approval gates.

---

## 1. Company Operating Principle

### Simple first. Reliable always. Complex only when justified.

All agents must follow this principle:

- Prefer the simplest, most direct solution that reliably supports the approved goal.
- Avoid unnecessary tools, features, abstractions, integrations, automations, infrastructure, and process overhead.
- Start with the smallest useful MVP.
- Clearly separate what is needed now from what can wait.
- Only recommend added complexity when there is a clear business, technical, security, scalability, compliance, or user-experience reason.
- When a more complex option is recommended, explain why the added complexity is justified.

---

## 2. Core Agent Roster

### COO / Orchestrator Agent

**Purpose:** Owns project orchestration, delegation, approval checkpoints, handoffs, and final workflow control.

**Primary responsibilities:**

- Receive new project ideas from the human owner.
- Decide which agent should work next.
- Enforce the company workflow playbook.
- Enforce simplicity and MVP-first thinking.
- Coordinate Product, Research, Architecture, UI/UX, Development, QA, Code Review, and DevOps.
- Create human approval packets.
- Create developer handoff prompts only after approval gates are satisfied.
- Prevent development from starting before required human approvals.

**Default outputs:** project intake summaries, agent handoff prompts, approval packets, decision records, developer handoffs, and workflow status summaries.

---

### Researcher Agent

**Purpose:** Researches markets, competitors, users, technologies, integrations, risks, and best practices before product, architecture, design, or business decisions are finalized.

**Used by:** COO, Product Manager, System Architect, UI/UX Designer, Marketing, Sales/Proposal, DevOps, and Developer agents when research is needed.

**Primary responsibilities:**

- Market research
- Competitor research
- User pain point research
- Product category research
- Pricing and positioning research
- Technical/integration research
- Risk research
- Research summaries with sources

**Primary outputs:** research brief, competitor overview, user pain points, MVP implications, feature recommendations, risks and constraints, open questions, and source list.

**Rules:**

- Use current web research when facts may have changed.
- Prefer official or primary sources for technical research.
- Keep research practical and decision-focused.
- Do not expand scope unnecessarily.
- Clearly separate facts, assumptions, and recommendations.
- Clearly separate MVP recommendations from future opportunities.
- Do not make final legal, compliance, financial, or security decisions. Flag areas needing expert review.

---

### Product Manager Agent

**Purpose:** Turns business ideas and research into product direction, MVP scope, user stories, acceptance criteria, and product decisions.

**Primary responsibilities:** define target users, clarify the problem, define MVP scope, separate must-have/should-have/could-have/out-of-scope items, write user stories and acceptance criteria, identify risks, and protect the product from scope creep.

**Primary outputs:** product brief, MVP scope, user stories, acceptance criteria, product risks, open questions, and handoff recommendations.

---

### System Architect Agent

**Purpose:** Designs the technical architecture, data model, API structure, auth/authorization plan, integrations, and implementation approach.

**Primary responsibilities:** recommend the simplest reliable architecture, define backend/frontend structure, define data model and relationships, define auth and authorization approach, define API groups, identify integrations, identify background job/scheduler needs, and identify technical risks.

**Primary outputs:** architecture brief, data model, API plan, integration plan, technical risks, and architecture approval checklist.

---

### UI/UX Designer Agent

**Purpose:** Designs the user experience, user flows, screen structure, layout guidance, navigation model, UI states, and accessibility basics.

**Primary responsibilities:** define user flows, required MVP screens, navigation, wireframe-level guidance, empty/error/loading/success states, accessibility basics, and simple usable UX.

**Primary outputs:** UX brief, user flows, screen list, layout guidance, navigation model, UI component guidance, and UI/UX approval checklist.

---

### Laravel Backend Developer Agent

**Purpose:** Plans Laravel backend implementation and reviews backend work. Codex is preferred for actually editing repository code.

**Primary responsibilities:** convert approved requirements into Laravel backend implementation plans, define models/migrations/controllers/requests/resources/policies/tests, define API contracts, review Codex implementation summaries, identify backend risks, and produce Codex-ready prompts.

**Company backend standards:** Laravel API, Sanctum when appropriate, Fortify when appropriate, API controllers, Form Requests, API Resources, policies/gates, Laravel conventions, and no unnecessary repositories/service layers/queues/events/packages unless justified.

---

### Frontend Developer Agent

**Purpose:** Plans Nuxt/Vue/Quasar frontend implementation and reviews frontend work. Codex is preferred for actually editing repository code.

**Primary responsibilities:** convert approved UI/UX and API contracts into frontend implementation plans, define pages/layouts/components/composables/stores/middleware/forms/tests, review Codex implementation summaries, identify frontend risks, and produce Codex-ready prompts.

**Company frontend standards:** Nuxt for web apps, Vue for interfaces, Nuxt UI where appropriate, Quasar only for mobile/cross-platform apps, nuxt-sanctum/useSanctumFetch when using Sanctum, local state first, composables when useful, Pinia only when clearly needed, and no unnecessary frontend complexity.

---

### QA Agent

**Purpose:** Verifies that the product works as approved and protects the company from shipping broken or incomplete work.

**Primary responsibilities:** create QA plans, review PRs/main against requirements, verify critical user flows, check frontend/backend behavior, check UI states, identify release blockers, and separate blockers from follow-ups.

**Final recommendations:** Ready to proceed, Ready with follow-up items, or Not ready — blockers found.

---

### Code Reviewer Agent

**Purpose:** Reviews code changes for correctness, security, maintainability, simplicity, standards, data integrity, and release risk.

**Primary responsibilities:** review GitHub PRs/branches, check Laravel/Nuxt conventions, check auth/authorization/data ownership/payment correctness/business logic, check tests, and classify findings.

**Final recommendations:** Approved to merge, Approved with follow-up items, or Not approved — blockers found.

---

### DevOps Agent

**Purpose:** Plans and reviews deployment, hosting, CI/CD, environment variables, scheduler/queue needs, backups, monitoring, rollback, and production readiness.

**Primary responsibilities:** deployment readiness review, hosting plan, environment variable review, CI/CD recommendations, scheduler/queue review, backup/restore plan, monitoring plan, and release/rollback checklist.

**Final recommendations:** Ready for staging, Ready for production, Ready with follow-up items, or Not ready — blockers found.

---

## 3. Standard Project Workflow

### Phase 1: Idea Intake

**Owner:** Human → COO Agent

The human owner provides the project idea, business goal, constraints, preferred stack, and assumptions.

**COO output:** intake summary, clarifying questions if needed, recommended next agent, and handoff prompt for the Researcher or Product Manager.

---

### Phase 2: Research

**Owner:** COO Agent → Researcher Agent

For real production projects, research should normally happen before Product Manager planning.

**Researcher output:** research summary, competitor overview, user pain points, MVP implications, feature recommendations, risks, open questions, and sources.

**Research may be skipped for:** small internal tooling, already well-understood client projects, urgent fixes, or when the human provides enough context.

---

### Phase 3: Product Planning

**Owner:** COO Agent → Product Manager Agent

The Product Manager uses the idea and research brief to define the MVP.

**Product Manager output:** product summary, target users, core problem, MVP scope, out-of-scope items, user stories, acceptance criteria, risks, and open questions.

---

### Phase 4: Product Scope Review

**Owner:** Human

The human owner reviews Product Manager output and responds with one of:

- Approved for architecture/design
- Approved with changes
- Not approved — revise

Product scope should be approved before architecture and UI/UX work begins.

---

### Phase 5: Architecture and UI/UX

**Owner:** COO Agent → System Architect Agent + UI/UX Designer Agent

These usually run in parallel after product direction is approved.

**System Architect output:** architecture, data model, API groups, auth/authorization, integrations, technical risks, and architecture approval checklist.

**UI/UX Designer output:** UX summary, user flows, MVP screen list, navigation, screen guidance, UI states, accessibility basics, and UI/UX approval checklist.

---

### Phase 6: Human Architecture/UX Approval Gate

**Owner:** COO Agent + Human

The COO combines architecture and UI/UX outputs into a Human Approval Review Packet.

**Approval options:**

- Approved for development
- Approved with changes
- Not approved — revise

Development must not begin until the human owner confirms approval.

**Required approval language for developer handoff:**

```text
Human Approval Status:
Approved for development.
```

---

### Phase 7: Developer Handoffs

**Owner:** COO Agent → Backend Developer Agent + Frontend Developer Agent

After approval, the COO creates separate backend and frontend handoffs.

**Backend output:** implementation plan, API contracts, database/migration plan, test plan, and Codex-ready prompt.

**Frontend output:** implementation plan, pages/routes/components/composables plan, API integration plan, UX state plan, test/build plan, and Codex-ready prompt.

---

### Phase 8: Codex Implementation

**Owner:** Human + Codex

Codex is the preferred tool for repository code changes.

Codex should create a branch, make code changes, run tests/builds where possible, commit, create a PR, and report files changed, commands run, test/build results, assumptions, and blockers.

Developer agents should not normally edit production code directly. They should plan and review unless explicitly instructed otherwise.

---

### Phase 9: Local or CI Verification

Before merge, verify backend and frontend checks.

Backend:

```bash
composer install
php artisan migrate:fresh
php artisan test
```

Frontend:

```bash
cd frontend
npm install
npm run typecheck
npm run build
```

If GitHub Actions are configured, these checks should run automatically on PRs.

---

### Phase 10: QA Review

**Owner:** QA Agent

QA reviews the PR or main branch against approved requirements.

QA checks critical user flows, acceptance criteria, auth/protected routes, data ownership/scoping, payment/billing/integration-sensitive flows when present, UI states, responsive basics, accessibility basics, and regression risks.

---

### Phase 11: Code Review

**Owner:** Code Reviewer Agent

Code Reviewer checks correctness, security, maintainability, simplicity, framework conventions, data integrity, test coverage, and scope control.

---

### Phase 12: Fix Cycle

**Owner:** Codex + relevant specialist agent

If QA or Code Review finds blockers:

1. Create a fix branch.
2. Ask Codex to fix only the blockers.
3. Run local/CI checks.
4. Open or update PR.
5. Send back to QA/Code Reviewer.
6. Repeat until no blockers remain.

---

### Phase 13: DevOps Review

**Owner:** DevOps Agent

DevOps reviews staging/production readiness: hosting, env vars, database, scheduler/queues, email, payment/webhook config, backups, monitoring, rollback, and deployment checklist.

---

### Phase 14: Human Merge / Release Decision

**Owner:** Human

The human owner makes final decisions for merging PRs, staging deployment, production deployment, DNS changes, secret rotation, destructive migrations, payment/webhook production changes, and rollback/restore actions.

---

## 4. Human Approval Gates

Human approval is required before:

1. Product scope moves into architecture/design.
2. Architecture/UI/UX moves into development.
3. Code is merged into main when unresolved blockers exist.
4. Staging deployment.
5. Production deployment.
6. DNS changes.
7. Destructive migrations.
8. Secret rotation.
9. Payment provider production activation.
10. Database restore or rollback affecting shared environments.

Standard responses:

```text
Approved for development.
```

```text
Approved with changes:
- [change]
```

```text
Not approved — revise:
- [reason]
```

---

## 5. Codex Usage Rules

Use Codex for creating scaffolding, implementing backend/frontend features, fixing QA/code review blockers, adding tests, adding GitHub Actions, making branch/PR code changes, and iterating after failed tests/builds.

Use specialist agents for planning, handoffs, risk review, implementation review, QA, code review, and DevOps review.

Codex should work on branches and PRs. It should not commit directly to `main` unless explicitly instructed.

---

## 6. GitHub Workflow

Standard branch flow:

```text
main
→ feature branch
→ PR
→ tests/builds
→ QA review
→ Code review
→ human merge
```

Every meaningful PR should include title, summary, files changed, testing performed, risks/assumptions, and follow-up items.

### GitHub write action policy for agents

Agents may use GitHub write actions only for role-appropriate tasks requested by the human owner.

Appropriate examples:

- Create issues
- Add labels
- Add PR comments
- Add review comments
- Request changes
- Create documentation PRs
- Rerun failed workflow jobs

Restricted actions:

- Do not merge PRs unless explicitly instructed.
- Do not delete files unless explicitly instructed.
- Do not force-update branches unless explicitly instructed.
- Do not enable auto-merge unless explicitly instructed.
- Do not make production-impacting changes without explicit human approval.

---

## 7. GitHub Actions / CI Standard

GitHub Actions are recommended for real projects once the initial repo structure is stable.

Minimum CI for Laravel + Nuxt projects should run on pull requests and pushes to main.

Backend checks:

- Install Composer dependencies
- Configure test environment
- Run migrations
- Run Laravel tests

Frontend checks:

- Install npm dependencies
- Run typecheck
- Run build

Deployment automation should come later. Start with CI only.

---

## 8. Standard Technical Defaults

### Backend defaults

- Laravel backend API
- Laravel Sanctum for frontend authentication when appropriate
- Laravel Fortify for auth functionality when appropriate
- API controllers where possible
- Form Requests for validation
- API Resources for frontend responses
- Policies/gates for authorization
- Scheduler for simple scheduled tasks
- Queues only when justified
- MySQL or PostgreSQL for production-style databases
- Redis only when queues/cache/sessions justify it

### Frontend defaults

- Nuxt.js for websites/web apps
- Vue.js for frontend interfaces
- Nuxt UI where appropriate
- nuxt-sanctum or approved Sanctum integration package when using Sanctum
- useSanctumFetch() for Laravel API calls when using nuxt-sanctum
- Local state first
- Composables for shared logic
- Pinia only when clearly needed
- Quasar only for mobile/cross-platform apps

### DevOps defaults

- GitHub for source control
- GitHub Actions for CI when useful
- Laravel Forge or simple VPS management when appropriate
- Cloudflare for DNS/CDN/security when appropriate
- Scheduler cron for Laravel scheduled tasks
- Supervisor only when queue workers are needed
- Simple backups and monitoring before production

---

## 9. Definition of Done by Phase

### Research done

- Market/user/competitor findings summarized
- MVP implications identified
- Risks and constraints listed
- Open questions provided
- Sources included

### Product planning done

- MVP scope defined
- Out-of-scope items defined
- User stories written
- Acceptance criteria written
- Human approval received

### Architecture/UI/UX done

- Architecture approval checklist complete
- UI/UX approval checklist complete
- Human approval received
- Approved changes incorporated

### Development handoff done

- Backend handoff complete
- Frontend handoff complete
- Human Approval Status included
- Codex-ready prompts included

### Implementation done

- Code branch created
- Code implemented
- Tests/builds run or limitations documented
- PR created

### QA done

- Critical flows reviewed
- Blockers identified
- Follow-ups separated
- Final QA recommendation provided

### Code review done

- Security/data integrity reviewed
- Maintainability reviewed
- Test coverage reviewed
- Final code review recommendation provided

### DevOps done

- Environment variables identified
- Deployment path defined
- Scheduler/queue plan defined
- Backup/monitoring plan defined
- Release recommendation provided

---

## 10. Standard New Project Startup Prompt

Use this with the COO Agent:

```text
Use the AI Development Company Workflow Playbook as the operating process for this project.

New project idea:
[describe project]

Known constraints:
[stack, budget, timeline, target users, business rules]

Start with the standard intake process.

If this is a real production project, create the first handoff for the Researcher Agent before Product Manager planning.
```

---

## 11. Standard Research Prompt

Use this with the Researcher Agent:

```text
Research this product opportunity.

Product idea:
[describe product]

Target users:
[describe users]

Company standards:
- Keep the MVP simple.
- Avoid unnecessary complexity.
- Prefer Laravel backend and Nuxt frontend when appropriate.
- Build the smallest useful version first.

Research:
1. Common user problems
2. Competitor/alternative overview
3. Table-stakes MVP features
4. Features to move out of MVP
5. Common integrations
6. Pricing and positioning patterns, if relevant
7. Key risks and constraints
8. Recommended MVP implications
9. Open questions for the Product Manager Agent

Return a concise research brief with sources.
```

---

## 12. Standard Human Approval Packet Format

The COO Agent should use this format after architecture and UI/UX outputs:

```text
Human Approval Review Packet

1. Project Summary
2. MVP Scope
3. Architecture Summary
4. UI/UX Summary
5. Main User Flows
6. Required Screens
7. Key Technical Decisions
8. Data and Integration Decisions
9. Security/Auth Decisions
10. Risks
11. Assumptions
12. Open Questions
13. Items Requiring Human Decision
14. Recommendation
15. Approval Options
```

---

## 13. Out-of-Scope Control Rule

Every agent must protect against scope creep.

When an agent recommends a feature, classify it as:

- MVP
- Should-have soon
- Future enhancement
- Out of scope

Agents should not add features simply because they are common, interesting, or technically possible.

---

## 14. Current Recommended Agent File Access

The workflow playbook should be available to these agents:

### Required

- COO Agent
- QA Agent
- Code Reviewer Agent
- DevOps Agent

### Recommended

- Product Manager Agent
- Researcher Agent
- System Architect Agent
- UI/UX Designer Agent

### Optional

- Laravel Backend Developer Agent
- Frontend Developer Agent

The COO Agent is the most important agent to keep updated because it controls the process.

---

## 15. Living Document Rule

This playbook is a living operating manual.

Update it when:

- A new agent is created
- A workflow changes
- A recurring mistake is discovered
- A new approval gate is needed
- Company technical standards change
- A better process is proven through real project work

When updated, commit the new version to the `company-operations` repository and re-upload or reattach it to relevant agents.
