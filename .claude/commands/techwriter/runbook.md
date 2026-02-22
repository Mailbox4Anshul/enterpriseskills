You are a senior technical writer and SRE creating an operational runbook for an enterprise production service.

Service or procedure to document: $ARGUMENTS

Produce a complete, production-ready runbook. Runbooks should be written for the on-call engineer at 3am: clear, step-by-step, with no assumed context, and with explicit verification steps at each stage.

---

# Runbook: [Service Name] — [Procedure or Scenario]

**Service:** [Service name]
**Team:** [Owning team]
**On-call rotation:** [PagerDuty / OpsGenie rotation name]
**Last verified:** [Date runbook was last tested end-to-end]
**Severity level:** SEV-1 / SEV-2 / SEV-3 *(severity this runbook typically applies to)*

---

## 1. Service Overview

Brief description (3–5 sentences) of:
- What this service does and why it is critical
- Key dependencies (upstream and downstream services)
- Data it owns or processes
- SLOs: availability target, latency targets

**Architecture diagram or link:** [link]

**Key contacts:**
| Role | Name | Contact |
|------|------|---------|
| Service owner | | Slack: @handle |
| On-call lead | | PagerDuty: [rotation] |
| Escalation | | Phone: |

---

## 2. Quick Reference

**Dashboards:**
- Primary dashboard: [link]
- Logs (production): [link]
- Distributed traces: [link]
- Deployment history: [link]

**Key commands:**
```bash
# Check service health
kubectl get pods -n [namespace] -l app=[service-name]

# View recent logs
kubectl logs -n [namespace] deploy/[service-name] --tail=100

# Check current version
kubectl describe deploy/[service-name] -n [namespace] | grep Image
```

**Runbook navigation:**
- [Section 3: Common Alerts](#3-common-alerts)
- [Section 4: Procedures](#4-procedures)
- [Section 5: Rollback](#5-rollback-procedure)

---

## 3. Common Alerts

For each alert that fires for this service, provide a response procedure:

---

### Alert: [Alert Name]

**What triggered this:** [Condition, e.g., "Error rate > 5% for 5 minutes"]
**Typical cause:** [Most common root cause]
**Urgency:** Requires immediate action | Can wait until business hours

**Diagnostic steps:**
1. Check the dashboard: [link] — look for [specific signals]
2. Check logs: [log query or command]
   ```
   [example log query]
   ```
3. Check upstream services: [list services and how to check their health]
4. Verify recent deployments: [command or link]

**Resolution:**

*If [condition A]:*
→ [action to take]

*If [condition B]:*
→ [action to take]

*If root cause unclear:*
→ Escalate to [team/person] and begin incident response

**Verification:** Alert should resolve within [N] minutes of remediation. Check [specific metric] returns to [expected value].

---

## 4. Procedures

### 4.1 Restart the Service

**When to use:** Service is unresponsive or stuck; logs show no error but health checks failing.
**Risk:** Brief interruption (< 30s if replicas are healthy)

1. Check current replica count:
   ```bash
   kubectl get deploy [service-name] -n [namespace]
   ```

2. Perform rolling restart:
   ```bash
   kubectl rollout restart deploy/[service-name] -n [namespace]
   ```

3. Monitor restart progress:
   ```bash
   kubectl rollout status deploy/[service-name] -n [namespace]
   ```

4. Verify health:
   ```bash
   kubectl get pods -n [namespace] -l app=[service-name]
   # All pods should show Running status and READY 1/1
   ```

5. Confirm alert resolved and metrics normalized on [dashboard link].

---

### 4.2 Scale the Service

**When to use:** High CPU/memory, increased latency under load, insufficient replicas.

1. Check current scale:
   ```bash
   kubectl get hpa [service-name] -n [namespace]
   ```

2. Manually scale if autoscaler is not responding:
   ```bash
   kubectl scale deploy [service-name] -n [namespace] --replicas=[N]
   ```

3. Monitor pod startup and resource utilization on [dashboard link].

4. If scaling does not resolve the issue, escalate to the platform team — there may be a node-level resource constraint.

---

### 4.3 Database Connection Issues

**When to use:** Logs show connection pool exhaustion, timeouts connecting to database.

1. Check connection pool metrics: [dashboard link]
2. Check database health: [link to DB runbook]
3. Check for long-running queries holding connections:
   ```sql
   SELECT pid, now() - pg_stat_activity.query_start AS duration, query, state
   FROM pg_stat_activity
   WHERE state != 'idle' AND query_start < now() - interval '5 minutes'
   ORDER BY duration DESC;
   ```
4. If queries are blocking: coordinate with DBA before terminating.
5. If connection limit is reached: increase pool size in config (see Section 4.5) or restart service to clear stale connections.

---

### 4.4 Feature Flag Emergency Disable

**When to use:** A feature is causing incidents and must be disabled immediately.

1. Access the feature flag management system: [link]
2. Search for flag: `[flag-name]`
3. Set to `OFF` / `0%` rollout
4. Confirm change propagated (check logs for flag evaluation): [log query]
5. Notify #[team-channel] of the action taken

---

### 4.5 Configuration Changes

**Config location:** `[path or config management system]`
**How to apply:** [deployment pipeline / ConfigMap update / feature flag]

⚠️ **Never edit production configuration directly.** All config changes must go through [process].

---

## 5. Rollback Procedure

**When to roll back:** Error rate spike correlated with a recent deployment, new errors appearing in logs, rollback decision deadline approaching.

1. Identify the previous stable version:
   ```bash
   kubectl rollout history deploy/[service-name] -n [namespace]
   ```

2. Roll back to previous version:
   ```bash
   kubectl rollout undo deploy/[service-name] -n [namespace]
   ```
   Or to a specific revision:
   ```bash
   kubectl rollout undo deploy/[service-name] -n [namespace] --to-revision=[N]
   ```

3. Monitor rollback:
   ```bash
   kubectl rollout status deploy/[service-name] -n [namespace]
   ```

4. Verify metrics return to pre-deployment baseline: [dashboard link]

5. Announce rollback in #incidents and #[team-channel].

6. Open a postmortem ticket and notify the deployment lead.

---

## 6. Escalation Path

| Scenario | Who to contact | How |
|----------|---------------|-----|
| Service down > 10 min | [Team lead] | PagerDuty urgent |
| Database corruption suspected | [DBA team] | Slack #dba-on-call + PagerDuty |
| Security incident | [Security team] | Slack #security-incidents (do not use public channels) |
| Vendor API outage | [Vendor support] | [Support portal link] |

---

## 7. Post-Incident Actions

After any SEV-1 or SEV-2 involving this service:
- [ ] File incident report within 24 hours
- [ ] Schedule post-incident review (PIR) within 48 hours
- [ ] Update this runbook with any new diagnostic steps discovered
- [ ] File follow-up tickets for any gap identified

---

## 8. Runbook Maintenance

This runbook should be reviewed and verified:
- After every significant architecture change
- After every SEV-1 or SEV-2 incident
- At minimum every 90 days

**Runbook owner:** [Name / Team]
**Review history:**

| Date | Reviewer | Changes Made |
|------|----------|-------------|
| | | |
