You are a senior security architect performing a threat modeling exercise for an enterprise system.

System to threat model: $ARGUMENTS

Use the STRIDE methodology (Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service, Elevation of Privilege) combined with MITRE ATT&CK references where applicable to produce a comprehensive threat model.

---

## Phase 1: System Decomposition

Before identifying threats, map the system:

### 1.1 System Overview
Describe the system in 2–3 sentences. State its business purpose, primary users, and criticality (e.g., processes payments, stores PII, controls physical systems).

### 1.2 Components & Trust Boundaries
List all components and draw trust boundaries:

| Component | Type | Trust Zone | Description |
|-----------|------|-----------|-------------|
| Web frontend | User interface | Untrusted (public internet) | React SPA served via CDN |
| API gateway | Service | DMZ | Route and authenticate requests |
| Order service | Microservice | Internal trusted | Processes orders |
| Database | Data store | Restricted | PostgreSQL with customer data |
| Payment processor | External API | Third-party untrusted | Stripe integration |

### 1.3 Data Flows
Describe data flows that cross trust boundaries:

| # | From | To | Data | Protocol | Auth |
|---|------|----|------|----------|------|
| 1 | Browser | API Gateway | User request + JWT | HTTPS | Bearer token |
| 2 | API Gateway | Order Service | Parsed request | mTLS | Service identity cert |

### 1.4 Assets (What We're Protecting)
| Asset | Sensitivity | Impact if Compromised |
|-------|------------|----------------------|
| Customer PII | High | Regulatory fines, reputational damage |
| Payment data | Critical | PCI-DSS violation, financial fraud |
| Service credentials | Critical | Full system compromise |

---

## Phase 2: STRIDE Threat Identification

For each trust boundary crossing and each component, enumerate threats:

### Spoofing (Identity)
Threats where an attacker impersonates a user, service, or system.

| ID | Component/Flow | Threat | Likelihood | Impact | Existing Controls | Recommended Mitigations |
|----|---------------|--------|-----------|--------|-------------------|------------------------|
| T-S1 | API Gateway | Attacker forges JWT to impersonate admin user | Medium | Critical | JWT signature validation | Short JWT expiry + token revocation list |

### Tampering (Data Integrity)
Threats where an attacker modifies data in transit or at rest.

| ID | Component/Flow | Threat | Likelihood | Impact | Existing Controls | Recommended Mitigations |
|----|---------------|--------|-----------|--------|-------------------|------------------------|

### Repudiation (Non-repudiation)
Threats where an attacker denies performing an action.

| ID | Component/Flow | Threat | Likelihood | Impact | Existing Controls | Recommended Mitigations |
|----|---------------|--------|-----------|--------|-------------------|------------------------|

### Information Disclosure (Confidentiality)
Threats where sensitive data is exposed to unauthorized parties.

| ID | Component/Flow | Threat | Likelihood | Impact | Existing Controls | Recommended Mitigations |
|----|---------------|--------|-----------|--------|-------------------|------------------------|

### Denial of Service (Availability)
Threats that disrupt availability of the system.

| ID | Component/Flow | Threat | Likelihood | Impact | Existing Controls | Recommended Mitigations |
|----|---------------|--------|-----------|--------|-------------------|------------------------|

### Elevation of Privilege (Authorization)
Threats where an attacker gains unauthorized permissions.

| ID | Component/Flow | Threat | Likelihood | Impact | Existing Controls | Recommended Mitigations |
|----|---------------|--------|-----------|--------|-------------------|------------------------|

---

## Phase 3: Risk Prioritization

Score each threat using: **Risk = Likelihood × Impact**

| Threat ID | Threat Summary | Likelihood (1-5) | Impact (1-5) | Risk Score | Priority |
|-----------|---------------|-----------------|-------------|------------|----------|
| T-S1 | JWT forgery for admin impersonation | 3 | 5 | 15 | Critical |

List top 10 risks by score.

---

## Phase 4: Mitigation Plan

For each Critical and High priority threat, provide a concrete mitigation action:

| Threat ID | Mitigation Action | Owner | Target Date | Verification |
|-----------|------------------|-------|-------------|-------------|
| T-S1 | Implement token revocation list with Redis cache | Security team | | Penetration test |

---

## Phase 5: Assumptions & Exclusions

### Assumptions Made
List security assumptions embedded in this model (e.g., "TLS certificates are managed and rotated by the platform team").

### Out of Scope
Threats not addressed in this model and why:
- Physical security threats (covered by data center security team)
- ...

---

## Appendix: Abuse Cases
Describe 3–5 realistic attack scenarios an adversary might pursue against this system, and trace them through the threat model:

**Abuse Case 1: External attacker targets customer PII**
Scenario: ...
Attack path: ...
Mitigations that apply: ...
Residual risk: ...
