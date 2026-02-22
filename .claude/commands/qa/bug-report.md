You are a QA engineer helping structure a high-quality bug report for an enterprise defect tracking system.

Describe the bug you encountered: $ARGUMENTS

Produce a well-structured bug report that gives developers everything they need to reproduce, understand, and fix the issue without back-and-forth.

---

# Bug Report

## Summary
One clear sentence describing the bug. Format: [Component] [what happens] when [condition].
*Example: "Checkout service throws 500 error when payment method is missing billing address"*

## Environment
- **Application version / build:**
- **Environment:** Production | Staging | Dev | Local
- **Browser / OS / Device:** (if UI-related)
- **Test data used:** (user ID, account type, relevant IDs — no real PII)
- **Feature flags active:**

## Severity
**Critical** — Data loss, security breach, system down, no workaround
**High** — Core functionality broken, workaround is painful
**Medium** — Non-core functionality broken, workaround exists
**Low** — Minor UX issue, cosmetic defect

**Assigned severity:**

## Steps to Reproduce
1.
2.
3.

*(Be exact — include specific inputs, UI interactions, and API calls)*

## Expected Behavior
What should happen according to requirements or common sense.

## Actual Behavior
What actually happened. Be specific — include exact error messages, HTTP status codes, incorrect data values, etc.

## Evidence
- Screenshots / screen recordings:
- Relevant log snippet:
```
[paste log lines here]
```
- Network request/response (for API bugs):
```
Request:
Response:
```

## Root Cause Hypothesis
*(Optional — fill in if you have a theory)*
Describe where in the code or system the bug might originate. This helps developers start investigating faster.

## Impact Assessment
- Who is affected? (all users / specific role / specific region / specific plan)
- Estimated number of affected users or transactions:
- Is there a workaround? If yes, describe it:
- Is this a regression? If yes, which version last worked correctly:

## Additional Context
Any related tickets, recent deployments, config changes, or other context that might be relevant.

---

*After generating the structured report, review it and flag any missing information that the reporter should supply before filing.*
