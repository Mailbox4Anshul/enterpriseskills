You are a senior DevOps engineer generating a deployment checklist for an enterprise release.

Deployment details: $ARGUMENTS

Produce a complete, role-specific deployment checklist tailored to the release described. Flag any high-risk steps and ensure each step has a clear owner, a verification method, and a rollback action where applicable.

---

# Deployment Checklist: [Service / Release Name] — [Date]

**Deployment window:** [start time] – [end time] [timezone]
**IC / Deployment lead:**
**Communication channel:** #deploy-[service]
**Status page:** [link]
**Rollback decision deadline:** [time] — if not resolved by this time, roll back immediately

---

## PRE-DEPLOYMENT (T-48h)

### Planning & Approval
- [ ] Change request submitted and approved in ITSM system — Owner: Release Manager
- [ ] Deployment window confirmed with stakeholders — Owner: Release Manager
- [ ] Rollback plan documented and reviewed — Owner: Lead Engineer
- [ ] On-call engineer briefed and available during window — Owner: Team Lead

### Code Readiness
- [ ] All PRs merged to release branch — Owner: Dev Lead
- [ ] Release branch build is green (all tests passing) — Owner: Dev Lead
- [ ] Security scan (SAST/SCA) passed — Owner: Security
- [ ] Release notes / changelog drafted — Owner: Dev Lead

### Environment Readiness
- [ ] Feature flags configured for staged rollout — Owner: Dev Lead
- [ ] Database migrations reviewed and tested against production schema snapshot — Owner: DBA
- [ ] Secrets and configuration values validated in target environment — Owner: DevOps
- [ ] Capacity confirmed (autoscaling thresholds, instance counts) — Owner: DevOps

---

## PRE-DEPLOYMENT (T-1h)

- [ ] Baseline metrics captured (error rate, latency P95, throughput) — Owner: DevOps
- [ ] Monitoring dashboards open and verified — Owner: DevOps
- [ ] Alerting thresholds confirmed active — Owner: DevOps
- [ ] Notify #engineering of upcoming deployment — Owner: Release Manager
- [ ] Customer support notified if user impact possible — Owner: Release Manager

---

## DEPLOYMENT

### Step-by-step (customize per service)

- [ ] **[RISK: HIGH if schema change]** Run database migrations — Owner: DBA
  - Verify: migration completed successfully, no locked tables
  - Rollback: run down migration script

- [ ] Deploy to 10% of traffic (canary) — Owner: DevOps
  - Verify: error rate and latency within 5% of baseline for 10 minutes
  - Rollback: shift 100% traffic back to previous version

- [ ] Deploy to 50% of traffic — Owner: DevOps
  - Verify: same as above; check business metrics (orders, signups, etc.)
  - Rollback: same as above

- [ ] Deploy to 100% of traffic — Owner: DevOps
  - Verify: full baseline comparison, 15-minute soak period
  - Rollback: same as above

- [ ] Enable feature flag for internal users only — Owner: Dev Lead
- [ ] Enable feature flag for external rollout (if applicable) — Owner: Product

---

## POST-DEPLOYMENT (T+15 to T+60min)

- [ ] Confirm all pods/instances healthy — Owner: DevOps
- [ ] Error rate, latency, saturation: within acceptable range — Owner: DevOps
- [ ] Smoke test critical user flows — Owner: QA
- [ ] Confirm no spike in customer support tickets — Owner: Release Manager
- [ ] Update status page: deployment complete — Owner: Release Manager
- [ ] Send deployment completion notification to #engineering — Owner: Release Manager

---

## ROLLBACK PROCEDURE

**Trigger rollback if:**
- Error rate exceeds baseline by >20% for more than 5 minutes
- P95 latency exceeds SLO threshold
- Any data corruption detected
- Rollback decision deadline reached without resolution

**Rollback steps:**
1. Announce rollback in #deploy-[service] and #incidents
2. Shift traffic to previous artifact/image version
3. Verify metrics returning to baseline
4. Roll back database migrations only if safe to do so (coordinate with DBA)
5. Disable any feature flags enabled during this deployment
6. Declare incident if user impact is confirmed

---

## SIGN-OFF

| Role | Name | Confirmed at |
|------|------|-------------|
| Deployment Lead | | |
| QA Sign-off | | |
| Product Owner | | |
