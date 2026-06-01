# AI Development Company Workflow Playbook

## 1. Purpose

This playbook defines the standard operating workflow for our AI-driven web and software development company.

It explains how ideas move from intake to product planning, architecture, design, development, QA, code review, DevOps review, and release planning.

The goal is to make every project repeatable, simple, controlled, and reviewable.

## 2. Company Operating Principle

**Simple first. Reliable always. Complex only when justified.**

All agents and humans should follow these rules:

- Prefer the simplest solution that reliably solves the approved problem.
- Build the MVP before adding future-phase features.
- Avoid unnecessary tools, services, packages, infrastructure, automations, abstractions, and processes.
- Use framework conventions before custom architecture.
- Clearly separate what is needed now from what can wait.
- Add complexity only when there is a clear business, technical, security, scalability, or user-experience reason.
- Do not expand scope without approval.

## 3. Core Agent Roster

### COO / Orchestrator Agent

Primary owner of workflow coordination.

Responsibilities:

- Receive raw ideas, client requests, and project concepts.
- Decide which specialist agent should work next.
- Maintain scope discipline.
- Enforce human approval gates.
- Create handoff prompts between agents.
- Confirm when work is ready for development, QA, code review, or DevOps review.
- Keep projects aligned with the company simplicity principle.

### Product Manager Agent

Defines what should be built.

Responsibilities:

- Create product briefs.
- Define target users and problems.
- Recommend MVP scope.
- Prioritize features.
- Write user stories and acceptance criteria.
- Identify assumptions, risks, and open questions.
- Prepare handoffs to architecture and design.

### System Architect Agent

Defines how the system should be built technically.

Responsibilities:

- Recommend application architecture.
- Define modules, roles, permissions, data models, API groups, integrations, jobs, schedulers, and technical risks.
- Keep architecture simple and MVP-focused.
- Prepare backend, frontend, QA, and DevOps handoff notes.

### UI/UX Designer Agent

Defines how users experience the product.

Responsibilities:

- Create user flows.
- Define screens, layouts, navigation, empty states, error states, and success states.
- Provide accessibility and responsive design guidance.
- Keep the interface simple and usable.
- Prepare frontend and QA handoff notes.

### Laravel Backend Developer Agent

Plans and reviews Laravel backend implementation.

Responsibilities:

- Convert approved requirements and architecture into backend tasks.
- Define models, migrations, controllers, Form Requests, API Resources, policies, jobs, commands, integrations, and tests.
- Follow Laravel conventions.
- Avoid unnecessary packages and abstractions.
- Produce Codex-ready implementation prompts when code needs to be written.

### Frontend Developer Agent

Plans and reviews Nuxt, Vue, and Quasar frontend implementation.

Responsibilities:

- Convert approved UI/UX and API contracts into frontend tasks.
- Define pages, layouts, components, composables, API integration, auth flow, validation, and UI states.
- Follow Nuxt, Vue, Nuxt UI, and Quasar conventions as appropriate.
- Avoid unnecessary state management and packages.
- Produce Codex-ready implementation prompts when code needs to be written.

### QA Agent

Verifies that the product works as approved.

Responsibilities:

- Create QA plans.
- Review PRs or current branches against approved scope and acceptance criteria.
- Identify release blockers, should-fix items, follow-ups, and nice-to-have issues.
- Focus on authentication, authorization, data integrity, payment/billing, core user flows, and approved MVP behavior.
- Produce manual smoke test and regression checklists.

### Code Reviewer Agent

Reviews code quality, maintainability, security, and merge risk.

Responsibilities:

- Review GitHub pull requests or branches.
- Check framework conventions, simplicity, maintainability, tests, security, data integrity, and scope control.
- Classify issues as merge blockers, should-fix items, follow-ups, or nice-to-have items.
- Do not write code unless explicitly asked.

### DevOps Agent

Plans and reviews deployment and operations readiness.

Responsibilities:

- Create staging and production deployment plans.
- Review environment variables, hosting, CI/CD, scheduler, queues, backups, monitoring, rollback, SSL, DNS, and secrets.
- Keep deployment simple and reliable.
- Flag production-readiness risks.

## 4. Standard Project Workflow

### Phase 1: Idea Intake

Input:

- Raw business idea
- Client request
- Product concept
- Internal opportunity

Agent:

- COO / Orchestrator Agent

Output:

- Clarified idea summary
- Initial business goal
- Recommended next agent
- Product Manager handoff prompt

### Phase 2: Product Planning

Agent:

- Product Manager Agent

Output:

- Product summary
- Target users
- Problem statement
- Proposed solution
- MVP scope
- Features by priority
- User stories
- Acceptance criteria
- Risks and assumptions
- Open questions
- Recommended handoff to System Architect and UI/UX Designer

Human approval:

- Required if scope, budget, business model, payment behavior, compliance, or major assumptions are unclear.

### Phase 3: Architecture and UX Planning

Agents:

- System Architect Agent
- UI/UX Designer Agent

These agents work in parallel after Product Manager output is reviewed by the COO.

System Architect output:

- Architecture summary
- Application structure
- Modules
- User roles and permissions
- High-level data model
- Backend architecture
- Frontend architecture
- API groups
- Integrations
- Jobs, queues, and scheduled tasks
- Security considerations
- Technical risks
- Implementation phases
- Architecture Approval Checklist

UI/UX Designer output:

- UX summary
- Target users and goals
- Primary user flows
- Required MVP screens
- Future screens and enhancements
- Screen-by-screen layout guidance
- Navigation model
- Key UI components
- Responsive/mobile considerations
- Accessibility requirements
- Empty, error, and success states
- UI/UX Approval Checklist

### Phase 4: Human Architecture and UX Approval Gate

Development must not begin until a human owner approves both architecture and UI/UX direction.

Acceptable approval responses:

- `Approved for development.`
- `Approved with changes: [list changes]`
- `Not approved — revise: [reason]`

If approved with changes:

- COO summarizes the approved changes.
- COO creates a final decision record.
- Developer handoffs must include all approved changes.

If not approved:

- COO routes the work back to the appropriate agent for revision.

### Phase 5: Developer Handoffs

Agents:

- COO / Orchestrator Agent
- Laravel Backend Developer Agent
- Frontend Developer Agent

COO creates separate handoff prompts for backend and frontend.

Every developer handoff must include:

- Project summary
- Human Approval Status
- Approved MVP scope
- Approved owner changes
- Technical standards
- Architecture notes
- UI/UX notes
- Out-of-scope items
- Expected output
- Verification requirements

Required handoff status:

```text
Human Approval Status:
Approved for development.
```

Developer agents should block implementation if this approval status is missing.

### Phase 6: Codex Implementation

Codex is used for actual code changes.

Planning agents do not replace Codex. They prepare clear implementation prompts and review results.

Use Codex for:

- Creating or editing code
- Running commands
- Creating branches
- Opening pull requests
- Fixing test failures
- Applying QA/code review fixes

Use specialist agents for:

- Planning
- Review
- Risk analysis
- Handoff creation
- Acceptance criteria
- QA plans
- Code review
- DevOps planning

Standard Codex process:

1. Create a feature branch from `main`.
2. Give Codex an approved implementation prompt.
3. Codex writes code.
4. Codex runs available checks.
5. Human/operator runs trusted local verification.
6. Push branch.
7. Create GitHub pull request.
8. Send PR to Code Reviewer and QA Agent.
9. Fix blockers.
10. Merge only after human approval.

### Phase 7: Local Verification

The human/operator should run local checks before merge whenever possible.

Laravel backend checks:

```bash
composer install
php artisan migrate:fresh
php artisan test
```

Nuxt frontend checks:

```bash
cd frontend
npm install
npm run typecheck
npm run build
```

If the app has both backend and frontend, run both sets of checks.

### Phase 8: Code Review

Agent:

- Code Reviewer Agent

Code review should happen before merge whenever possible.

Review focuses on:

- Correctness
- Security
- Data integrity
- Authentication and authorization
- Framework conventions
- Simplicity
- Maintainability
- Test coverage
- Scope control
- Payment/billing safety when relevant
- Public endpoint safety when relevant

Final recommendation must be one of:

- Approved to merge
- Approved with follow-up items
- Not approved — blockers found

### Phase 9: QA Review

Agent:

- QA Agent

QA review may happen before merge, after merge to staging, or both.

QA focuses on:

- Approved MVP behavior
- User flows
- Acceptance criteria
- Auth and permissions
- Data ownership/scoping
- Payment/billing flow when relevant
- Validation and error handling
- Empty/loading/success states
- Responsive basics
- Accessibility basics
- Regression risk

Final recommendation must be one of:

- Ready to proceed
- Ready with follow-up items
- Not ready — blockers found

### Phase 10: Fix Cycle

If QA or Code Review finds blockers:

1. COO summarizes blockers.
2. Codex receives a blocker-fix prompt.
3. Codex fixes only the listed issues.
4. Human/operator reruns checks.
5. QA and/or Code Reviewer re-review.
6. Merge only after blockers are resolved.

Do not expand scope during blocker fixes.

### Phase 11: DevOps Review

Agent:

- DevOps Agent

DevOps review should happen before staging or production deployment.

Review focuses on:

- Hosting architecture
- Environment variables
- Secrets
- DNS and SSL
- Laravel deployment steps
- Nuxt deployment steps
- Scheduler/cron
- Queue workers if needed
- Mail provider
- Payment/webhook configuration
- Database backups
- Restore process
- Monitoring and alerts
- Rollback plan
- Production readiness risks

Final recommendation must be one of:

- Ready for staging
- Ready for production
- Ready with follow-up items
- Not ready — blockers found

## 5. Human Approval Gates

Human approval is required before:

- Development starts after architecture/UX planning
- Merging major PRs if blockers were found earlier
- Production deployment
- DNS changes
- Payment provider production configuration
- Destructive migrations
- Database restores
- Secret rotation
- Cost-increasing infrastructure changes
- Public launch

Standard approval language:

```text
Approved for development.
```

```text
Approved with changes:
- [change]
- [change]
```

```text
Not approved — revise:
- [reason]
```

## 6. Standard Technical Defaults

These are defaults, not permanent rules. A project may override them with explicit approval.

Backend defaults:

- Laravel backend API
- Laravel Sanctum for frontend authentication when appropriate
- Laravel Fortify for authentication functionality when appropriate
- API controllers where possible
- Form Requests for validation
- API Resources for frontend responses
- Policies/gates for authorization
- MySQL or PostgreSQL for production-style relational data
- Redis only when queues/cache/sessions/background jobs clearly need it
- Queues/jobs/events only when justified

Frontend defaults:

- Nuxt.js for web apps
- Vue.js for frontend interfaces
- Nuxt UI where appropriate
- nuxt-sanctum or approved Sanctum integration package when using Laravel Sanctum
- `useSanctumFetch()` for Laravel API calls when using nuxt-sanctum
- Pinia only when shared app-level state is clearly needed
- Quasar only when mobile/cross-platform app is required

DevOps defaults:

- GitHub for source control
- GitHub pull requests for review
- GitHub Actions when useful for CI/CD
- Laravel Forge when using compatible VPS hosting
- Cloudflare for DNS/CDN/security when appropriate
- Simple VPS or managed app hosting for MVPs
- Avoid Kubernetes and complex cloud architecture unless clearly justified

## 7. Standard GitHub Workflow

Use this branch naming pattern:

```text
feature/[short-description]
fix/[short-description]
qa/[short-description]
devops/[short-description]
```

Standard PR process:

1. Create branch from `main`.
2. Implement changes with Codex or human developer.
3. Run local checks.
4. Push branch.
5. Create PR into `main`.
6. Code Reviewer Agent reviews PR.
7. QA Agent reviews PR or staging behavior.
8. Codex fixes blockers if needed.
9. Human approves merge.
10. Merge PR.
11. Pull latest `main` locally and rerun checks.

## 8. Definition of Done by Phase

### Product Planning Done

- MVP scope defined
- User stories written
- Acceptance criteria written
- Risks and assumptions identified
- Open questions listed
- Handoff ready for architecture/design

### Architecture Done

- Application structure defined
- Data model outlined
- API groups defined
- Roles and permissions defined
- Integrations identified
- Risks and tradeoffs documented
- Architecture approval checklist complete

### UI/UX Done

- Main user flows defined
- MVP screens listed
- Navigation model defined
- Layout guidance complete
- Empty/error/success states noted
- Accessibility basics noted
- UI/UX approval checklist complete

### Development Done

- Approved scope implemented
- Tests/checks pass locally
- PR created
- No known merge blockers
- Implementation summary complete

### QA Done

- Critical flows reviewed
- Blockers classified
- Manual checklist created or executed
- Final QA recommendation provided

### Code Review Done

- Code reviewed against project rules and company standards
- Blockers/follow-ups classified
- Final code review recommendation provided

### DevOps Review Done

- Deployment path recommended
- Environment variables identified
- Scheduler/queue/mail/payment needs identified
- Backup/monitoring/rollback plan documented
- Final DevOps recommendation provided

## 9. Project-Specific Rules

Every project may have its own business rules.

Do not assume all projects use the same:

- Data ownership model
- Tenant model
- Payment provider
- Booking logic
- Staff roles
- Deployment provider
- Database
- Frontend framework mode
- Auth flow

For each new project, the COO should collect and pass project-specific rules to every relevant agent.

Project-specific rules should include:

- Approved MVP scope
- Out-of-scope items
- User roles
- Payment/billing rules
- Data ownership/scoping rules
- Auth requirements
- Integrations
- Compliance concerns
- Deployment constraints
- Human approval decisions

## 10. Standard Handoff Template

Use this template when one agent hands work to another.

```text
Project:
[project name]

Human Approval Status:
[approved / not approved / approved with changes]

Context:
[short project summary]

Approved Scope:
- [item]
- [item]

Out of Scope:
- [item]
- [item]

Relevant Decisions:
- [decision]
- [decision]

Technical Standards:
- [standard]
- [standard]

Inputs:
[paste previous agent output or summary]

Requested Output:
[what this agent should produce]

Constraints:
- Keep it simple
- Do not expand scope
- Clearly label assumptions and open questions
```

## 11. Standard Codex Prompt Template

```text
You are working in the GitHub repository:
[repo]

Current branch:
[branch]

Goal:
[implementation goal]

Human Approval Status:
Approved for development.

Approved Scope:
- [item]
- [item]

Do not add features outside this scope.
Do not overcomplicate the implementation.
Follow company technical standards.
Use framework conventions.

Required changes:
1. [change]
2. [change]
3. [change]

Testing required:
- [command]
- [command]

When finished, report:
1. Files changed
2. Exact changes made
3. Tests added or updated
4. Commands run
5. Test/build results
6. Remaining risks
```

## 12. Standard QA Review Prompt Template

```text
Review this PR or branch as a QA workflow test.

Repository:
[repo]

PR or Branch:
[link / number / branch]

Project:
[project name]

Approved MVP Scope:
- [item]
- [item]

Project-Specific Rules:
- [rule]
- [rule]

Current Verification:
- [test/build status]

Do not write code.

Return:
1. QA Summary
2. Release blockers
3. Should-fix before release items
4. Follow-up items
5. Manual smoke test checklist
6. Final QA recommendation
```

## 13. Standard Code Review Prompt Template

```text
Review this PR or branch for code quality and merge readiness.

Repository:
[repo]

PR or Branch:
[link / number / branch]

Project:
[project name]

Approved Scope:
- [item]
- [item]

Project-Specific Rules:
- [rule]
- [rule]

Current Verification:
- [test/build status]

Do not write code.

Return:
1. Code Review Summary
2. Merge/release blockers
3. Should-fix before release
4. Follow-up items
5. Maintainability notes
6. Security/data-integrity notes
7. Test coverage notes
8. Final recommendation
```

## 14. Standard DevOps Review Prompt Template

```text
Run a DevOps readiness review.

Repository:
[repo]

Branch:
[branch]

Project:
[project name]

Current Status:
- [status]

Approved Stack:
- [stack item]
- [stack item]

Hosting Context:
- [hosting details]

Known Risks:
- [risk]
- [risk]

Do not write code.

Return:
1. DevOps Summary
2. Required environment variables
3. Environment recommendations
4. Deployment architecture recommendation
5. Backend deployment checklist
6. Frontend deployment checklist
7. Scheduler/queue requirements
8. Email/payment/webhook configuration notes
9. Backup and restore plan
10. Monitoring and alerts
11. Release blockers
12. Should-fix before production
13. Final DevOps recommendation
```

## 15. Current Agent Creation Roadmap

Core agents already created:

- COO / Orchestrator Agent
- Product Manager Agent
- System Architect Agent
- UI/UX Designer Agent
- Laravel Backend Developer Agent
- Frontend Developer Agent
- QA Agent
- Code Reviewer Agent
- DevOps Agent

Recommended next agents:

1. Researcher Agent
2. Sales / Proposal Agent
3. Marketing Agent
4. Documentation Agent

Do not create unnecessary agents until the core workflow is stable across at least two different mock projects.

## 16. Current Workflow Maturity Status

The workflow has successfully completed one full mock project cycle:

- Product planning
- Architecture planning
- UI/UX planning
- Human approval gate
- Backend implementation through Codex
- Frontend implementation through Codex
- Local verification
- QA review
- QA blocker fixes
- Code review
- DevOps readiness review

Next maturity step:

Run a second mock project in a different domain to prove the workflow is generic and not overfit to the appointment SaaS example.
