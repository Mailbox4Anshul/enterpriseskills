# Enterprise Claude Skills

A curated library of Claude Code skills for enterprise IT teams, covering the full Software Development Lifecycle. Each skill is a custom slash command that brings role-specific expertise directly into your development workflow.

## What Are Skills?

Skills are custom slash commands for [Claude Code](https://claude.ai/code). They are stored as Markdown files under `.claude/commands/` and invoked with `/skill-name [arguments]`. When invoked, the skill's prompt is sent to Claude along with your arguments, giving Claude the context and structure to act as a domain expert.

**Example:**
```
/dev:code-review src/api/orders.py
/qa:bug-report "Login button unresponsive on Safari mobile after session timeout"
/security:threat-model "Payment processing microservice with Stripe integration"
```

---

## Skill Catalog

### Developer (`/dev:*`)

| Skill | Command | Description |
|-------|---------|-------------|
| Code Review | `/dev:code-review [file or PR description]` | Structured review covering correctness, security, performance, maintainability, and test coverage |
| Debug | `/dev:debug [issue description]` | Systematic debugging methodology from symptom to root cause to fix |
| Refactor | `/dev:refactor [file or function]` | Safe, incremental refactoring plan with risk assessment and validation guidance |
| Tech Spec | `/dev:tech-spec [feature description]` | Full technical specification document including API design, data model, rollout plan, and open questions |

---

### QA / Testing (`/qa:*`)

| Skill | Command | Description |
|-------|---------|-------------|
| Test Plan | `/qa:test-plan [feature or release]` | Enterprise test plan with scope, approach, environment needs, entry/exit criteria, and sign-off matrix |
| Test Cases | `/qa:test-cases [feature, user story, or requirement]` | Comprehensive test case suite covering happy paths, edge cases, error conditions, and boundaries |
| Bug Report | `/qa:bug-report [bug description]` | Structured defect report with reproduction steps, evidence, impact assessment, and root cause hypothesis |

---

### DevOps / Platform Engineering (`/devops:*`)

| Skill | Command | Description |
|-------|---------|-------------|
| Pipeline Review | `/devops:pipeline-review [pipeline config or description]` | CI/CD pipeline review covering security, reliability, efficiency, compliance, and observability |
| Incident Response | `/devops:incident-response [incident or system description]` | Active incident triage checklist or preparatory incident response plan with PIR template |
| Deployment Checklist | `/devops:deployment-checklist [service and release details]` | Role-specific deployment checklist with pre-deploy, deploy, post-deploy, and rollback procedures |

---

### Product Management / Business Analysis (`/product:*`)

| Skill | Command | Description |
|-------|---------|-------------|
| User Story | `/product:user-story [feature or capability]` | INVEST-compliant user stories with Given-When-Then acceptance criteria and story map |
| PRD | `/product:prd [product feature or initiative]` | Full Product Requirements Document with personas, functional/non-functional requirements, metrics, and go-to-market plan |
| Requirements Analysis | `/product:requirements-analysis [raw requirements or stakeholder input]` | Classify, gap-analyze, and prioritize requirements; generate targeted stakeholder questions |

---

### Software Architecture (`/architect:*`)

| Skill | Command | Description |
|-------|---------|-------------|
| Architecture Review | `/architect:arch-review [system or design description]` | Rigorous review of scalability, resilience, security, coupling, operability, and technology choices |
| ADR | `/architect:adr [decision to document]` | Architecture Decision Record with context, options comparison, rationale, consequences, and review criteria |

---

### Security Engineering (`/security:*`)

| Skill | Command | Description |
|-------|---------|-------------|
| Security Review | `/security:security-review [code or system]` | OWASP Top 10 and CWE-based security review with severity-ranked findings and remediation guidance |
| Threat Model | `/security:threat-model [system description]` | STRIDE-based threat model with asset inventory, data flow analysis, threat enumeration, and risk prioritization |

---

### Technical Writing (`/techwriter:*`)

| Skill | Command | Description |
|-------|---------|-------------|
| API Documentation | `/techwriter:api-docs [API, endpoint, or code]` | Developer-grade API docs with authentication, endpoint references, request/response schemas, error catalog, and code examples |
| Runbook | `/techwriter:runbook [service or procedure]` | Production operational runbook with alert responses, common procedures, rollback steps, and escalation paths |

---

### Project Management / Scrum (`/pm:*`)

| Skill | Command | Description |
|-------|---------|-------------|
| Sprint Planning | `/pm:sprint-planning [sprint context and team info]` | End-to-end sprint planning facilitation with capacity planning, backlog selection, task breakdown, and risk identification |
| Retrospective | `/pm:retro [sprint number and context]` | Blameless retrospective facilitation with multiple format options, root cause analysis, and action item tracking |

---

## Getting Started

### Installation

These skills are project-scoped — any team member working in a repository that contains this `.claude/commands/` structure can use the skills immediately with Claude Code.

To add these skills to an existing project, copy the `.claude/` directory into your project root:

```bash
cp -r .claude/ /path/to/your/project/
```

### Usage Tips

1. **Provide context**: The more specific your argument, the better the output. Paste code snippets, user stories, or system descriptions directly into the command.

2. **Iterate**: Use skills as a starting point. Edit the output, ask Claude to refine specific sections, or re-run with additional context.

3. **Combine skills**: For example, use `/product:user-story` to write stories, then `/dev:tech-spec` to design the implementation, then `/qa:test-cases` to generate the test suite.

4. **Reference files**: You can reference files in your workspace — e.g., `/dev:code-review src/api/orders.py` will include the file contents.

---

## Skill Directory Structure

```
.claude/
└── commands/
    ├── dev/
    │   ├── code-review.md
    │   ├── debug.md
    │   ├── refactor.md
    │   └── tech-spec.md
    ├── qa/
    │   ├── test-plan.md
    │   ├── test-cases.md
    │   └── bug-report.md
    ├── devops/
    │   ├── pipeline-review.md
    │   ├── incident-response.md
    │   └── deployment-checklist.md
    ├── product/
    │   ├── user-story.md
    │   ├── prd.md
    │   └── requirements-analysis.md
    ├── architect/
    │   ├── arch-review.md
    │   └── adr.md
    ├── security/
    │   ├── security-review.md
    │   └── threat-model.md
    ├── techwriter/
    │   ├── api-docs.md
    │   └── runbook.md
    └── pm/
        ├── sprint-planning.md
        └── retro.md
```

---

## Contributing

To add a new skill:

1. Identify the team and role the skill serves
2. Create a `.md` file in the appropriate team subdirectory
3. Structure the prompt to: set the expert persona, define what input to expect (use `$ARGUMENTS`), specify the analytical framework, and define the output format
4. Test the skill with realistic enterprise scenarios
5. Add an entry to this README

---

## Roadmap

Future skill areas planned for enterprise teams beyond SDLC:
- **IT Operations**: capacity planning, change management, SLA reporting
- **Data Engineering**: pipeline design review, data quality assessment, data contract authoring
- **Cloud/FinOps**: cost optimization review, infrastructure right-sizing
- **Governance & Compliance**: control gap analysis, audit evidence preparation
- **HR / People**: job description writing, interview guide creation, performance review structuring
