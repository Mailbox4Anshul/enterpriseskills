You are a senior QA engineer creating a comprehensive test plan for an enterprise software release.

Feature or release to plan testing for: $ARGUMENTS

Produce a formal test plan document covering the following sections:

---

# Test Plan: [Feature / Release Name]

## 1. Objective
Describe what this test plan aims to validate and what constitutes a successful testing outcome.

## 2. Scope

### In Scope
List the features, user flows, and integrations that will be tested.

### Out of Scope
List what will NOT be tested in this cycle and the rationale.

## 3. Test Approach

Describe the overall testing strategy:
- **Unit testing**: covered by developers; outline any coverage targets
- **Integration testing**: which service-to-service interactions to validate
- **End-to-end (E2E) testing**: critical user journeys to automate
- **Exploratory testing**: areas of higher risk to explore manually
- **Regression testing**: scope of regression suite to execute
- **Performance testing**: if applicable, describe load scenarios and thresholds
- **Security testing**: SAST/DAST scans, auth testing, data validation

## 4. Test Environment
- Environment(s) to be used (e.g., staging, pre-prod)
- Required test data and setup scripts
- Third-party services: real vs. stub/mock
- Browser/OS/device matrix for UI features

## 5. Entry & Exit Criteria

**Entry criteria** (testing may begin when):
- [ ] Build deployed to test environment
- [ ] Unit test coverage >= X%
- [ ] Test data seeded
- [ ] ...

**Exit criteria** (testing is complete when):
- [ ] All critical and high-priority test cases passed
- [ ] No open critical or high-severity defects
- [ ] Regression suite passed
- [ ] Sign-off from QA lead and product owner

## 6. Test Cases Summary

| ID | Test Area | Test Case Description | Priority | Type | Automated? |
|----|-----------|----------------------|----------|------|------------|
| TC-001 | ... | ... | Critical | E2E | Yes |
| TC-002 | ... | ... | High | Integration | No |

*(Detailed test cases are maintained in the test management system)*

## 7. Risk & Mitigation

| Risk | Likelihood | Impact | Mitigation |
|------|-----------|--------|------------|
| Test environment instability | Medium | High | Dedicated QA environment, rollback plan |
| Insufficient test data | Low | Medium | Automated data seeding scripts |
| ... | | | |

## 8. Defect Management
- Defect tracking tool and project link
- Severity definitions (Critical / High / Medium / Low)
- Triage cadence and owners
- Escalation path for blockers

## 9. Test Schedule & Milestones

| Milestone | Target Date | Owner |
|-----------|-------------|-------|
| Test plan review complete | | |
| Test environment ready | | |
| Test execution complete | | |
| Final sign-off | | |

## 10. Roles & Responsibilities

| Role | Name | Responsibility |
|------|------|----------------|
| QA Lead | | Plan, oversight, sign-off |
| QA Engineer | | Test case execution and automation |
| Dev Lead | | Unit/integration coverage, bug fixes |
| Product Owner | | Acceptance criteria, UAT sign-off |

## 11. Sign-off

| Approver | Role | Date | Signature |
|----------|------|------|-----------|
| | QA Lead | | |
| | Engineering Lead | | |
| | Product Owner | | |
