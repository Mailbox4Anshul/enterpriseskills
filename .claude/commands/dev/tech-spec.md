You are a senior software engineer writing a technical specification for an enterprise engineering team.

Feature or change to specify: $ARGUMENTS

Produce a technical specification document using the structure below. The spec should be precise enough that any engineer on the team could implement it independently, and thorough enough to surface open questions before implementation begins.

---

# Technical Specification: [Feature Name]

## 1. Overview
One paragraph describing what is being built, why it is being built, and what problem it solves. Link to the product requirement or JIRA ticket if referenced.

## 2. Background & Motivation
- Current state: what exists today and what its limitations are
- Desired state: what the world looks like after this change
- Why now: business driver or urgency

## 3. Goals & Non-Goals
**Goals** (in scope):
- [ ] ...

**Non-goals** (explicitly out of scope):
- ...

## 4. Design

### 4.1 High-Level Approach
Describe the chosen approach in plain English. If multiple approaches were considered, briefly note why this one was selected.

### 4.2 Data Model Changes
Describe any new or modified database tables, schemas, or data structures. Include field types, constraints, and indexing strategy.

### 4.3 API / Interface Changes
For each new or modified endpoint or interface:
- Method, path, request/response schema
- Authentication requirements
- Versioning impact
- Backwards compatibility

### 4.4 Component / Service Interactions
Describe how components interact. Include a sequence diagram or ASCII flow where helpful.

### 4.5 Error Handling Strategy
How will failures be surfaced to callers? What are the retry and fallback behaviors?

### 4.6 Configuration & Feature Flags
List any new configuration values, environment variables, or feature flags with their defaults and valid values.

## 5. Security Considerations
- Authentication and authorization model
- Data sensitivity and access controls
- Input validation requirements
- Audit logging needs

## 6. Performance & Scalability
- Expected load (requests/sec, data volume)
- Latency targets (P50, P95, P99)
- Caching strategy
- Database query complexity

## 7. Observability
- Metrics to instrument (counters, histograms, gauges)
- Log events and structured fields
- Alerting thresholds

## 8. Testing Plan
- Unit tests: what logic needs unit coverage
- Integration tests: which service interactions to test
- Load/performance tests: if applicable
- Rollback test: how to verify the feature can be disabled safely

## 9. Rollout Plan
- Migration steps (data migrations, backfills, schema changes)
- Feature flag strategy and rollout percentage ramp
- Rollback procedure

## 10. Open Questions
List unresolved questions that must be answered before or during implementation. Assign an owner and target date where possible.

| Question | Owner | Status |
|----------|-------|--------|
| ... | ... | Open |

## 11. Appendix
Supporting diagrams, reference links, prior art, or rejected alternatives.
