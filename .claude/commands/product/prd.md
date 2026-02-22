You are a senior product manager writing a Product Requirements Document (PRD) for an enterprise software product.

Product feature or initiative to document: $ARGUMENTS

Produce a complete, enterprise-grade PRD. The document should give engineering, design, QA, legal, and business stakeholders a single source of truth for what is being built, why, and how success will be measured.

---

# Product Requirements Document

**Product / Feature Name:**
**Author:**
**Status:** Draft | In Review | Approved | Superseded
**Version:** 1.0
**Last Updated:**
**Stakeholders:**

---

## 1. Executive Summary
2–3 paragraph overview: the problem being solved, the proposed solution, and the expected business impact. Write for a VP-level audience — no jargon, clear business value.

## 2. Problem Statement

### 2.1 Background
Describe the current state of the world and why it is inadequate. Include data where available (e.g., support ticket volume, conversion rates, user research findings).

### 2.2 Problem Definition
What specific problem are we solving? Who experiences it? How often? What is the cost of not solving it?

### 2.3 Opportunity Size
Quantify the opportunity: affected users, revenue at risk, efficiency gains, regulatory requirement, or strategic differentiation.

## 3. Goals & Success Metrics

### 3.1 Goals
| Goal | Type | Metric | Baseline | Target | Measurement Method |
|------|------|--------|----------|--------|--------------------|
| Reduce support tickets for X | Efficiency | Ticket volume/week | 150 | <50 | Zendesk dashboard |
| Improve onboarding completion | Growth | % users who complete flow | 42% | 65% | Product analytics |

### 3.2 Non-Goals
What this product/feature will explicitly NOT do:
- ...
- ...

## 4. User Personas & Use Cases

### 4.1 Primary Persona
**Name:** [Give the persona a name]
**Role:** [Job title]
**Goal:** [What they are trying to accomplish]
**Pain points:** [Current frustrations]
**Success looks like:** [What a great experience means for them]

### 4.2 Secondary Personas
*(Repeat above for each additional persona)*

### 4.3 Key Use Cases
Describe 3–5 concrete scenarios showing how personas interact with the feature end-to-end.

**Use Case 1: [Title]**
Actor: [Persona]
Trigger: [What initiates the flow]
Flow: Step-by-step description
Outcome: What the user achieves

## 5. Requirements

### 5.1 Functional Requirements

| ID | Priority | Requirement | Notes |
|----|----------|-------------|-------|
| FR-001 | Must Have | The system shall... | |
| FR-002 | Should Have | The system shall... | |

*Priority: Must Have / Should Have / Could Have / Won't Have (MoSCoW)*

### 5.2 Non-Functional Requirements

| ID | Category | Requirement |
|----|----------|-------------|
| NFR-001 | Performance | Page load time < 2s at P95 under 1,000 concurrent users |
| NFR-002 | Availability | 99.9% uptime SLA |
| NFR-003 | Security | All PII encrypted at rest and in transit |
| NFR-004 | Accessibility | WCAG 2.1 AA compliance |
| NFR-005 | Compliance | SOC2 Type II audit trail for all data access |

### 5.3 Out of Scope
Explicitly list requirements that were considered and deferred:
- ...

## 6. UX & Design

### 6.1 Design Principles
List 2–4 principles guiding the design decisions for this feature.

### 6.2 User Flows
Reference or embed key user flow diagrams. Describe the critical paths in text if diagrams are not available.

### 6.3 Wireframes / Mockups
Link to Figma, attach images, or describe key screens/states.

### 6.4 Accessibility Considerations
Specific requirements beyond the baseline NFR (e.g., screen reader support, keyboard navigation, color contrast).

## 7. Technical Considerations

*This section is informational, not prescriptive — engineering owns the technical design.*

- Known constraints or platform limitations
- Integration requirements (systems this must connect to)
- Data requirements (what data is needed and where it comes from)
- Security or compliance constraints
- Scalability expectations

## 8. Dependencies & Risks

### 8.1 Dependencies

| Dependency | Type | Team / System | Status |
|------------|------|--------------|--------|
| Payment API v3 | Technical | Payments team | In progress |
| Legal review of data retention | Compliance | Legal | Pending |

### 8.2 Risks & Mitigations

| Risk | Likelihood | Impact | Mitigation |
|------|-----------|--------|------------|
| Third-party API rate limits | Medium | High | Implement caching and retry logic |
| Scope creep from stakeholder feedback | High | Medium | Weekly alignment meetings, frozen requirements by [date] |

## 9. Go-to-Market Considerations
- Rollout strategy (feature flag, beta, gradual rollout)
- Customer communication plan
- Training or documentation needs
- Support team enablement

## 10. Timeline & Milestones

| Milestone | Target Date | Owner |
|-----------|-------------|-------|
| PRD approved | | PM |
| Design complete | | Design |
| Engineering kickoff | | Engineering |
| Beta available | | PM |
| GA launch | | PM |

## 11. Open Questions

| Question | Owner | Due Date | Status |
|----------|-------|----------|--------|
| | | | Open |

## 12. Appendix
Supporting research, data, competitive analysis, or prior art.
