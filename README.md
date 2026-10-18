# MuhammadEhteshamAli.github.io

## Backend Security Testing Runbook (Authorized Scope Only)

Use this runbook only for systems you own or have explicit written authorization to test.

### 1) Scope Lock (Backend Only)

**In scope**
- API endpoints
- Authentication/authorization services
- Database layer and access controls
- Admin/backend panels
- Server/cloud configuration used by backend workloads

**Out of scope**
- Frontend/UI behavior
- CDN/static asset delivery paths

**Before starting**
- Confirm maintenance window
- Confirm rollback owner and rollback procedure
- Confirm incident contact channel

### 2) Pre-Test Baseline

- Create/update architecture map:
  - Services and owners
  - Exposed ports and protocols
  - Auth flows (login, token refresh, role checks)
  - Database connections and permission model
- Ensure logging/monitoring is active:
  - WAF events
  - Application logs
  - Database audit logs
  - Cloud audit trails
- Prepare testing identities:
  - Separate test accounts per role
  - Least-privilege credentials only
  - Time-bound secrets/tokens

### 3) Backend-Focused Assessment Checklist

- Auth/AuthZ:
  - Broken access control checks
  - Privilege escalation checks
  - IDOR checks
- Injection and input handling:
  - SQL/NoSQL injection checks
  - Command injection checks
  - Unsafe deserialization checks
- API security:
  - OWASP API Top 10 coverage
  - Rate-limiting enforcement checks
  - Mass-assignment checks
- Session/token controls:
  - JWT validation checks
  - Expiry and refresh flow checks
  - Token revocation checks
- Infrastructure/configuration:
  - Exposed service/management ports
  - TLS and cert configuration
  - Default/weak credential review
  - Secret exposure and storage policy review
- Supply chain:
  - Dependency vulnerability scanning
  - Container/runtime image review
- Business logic:
  - Workflow bypass checks
  - Credit/payment abuse scenarios
  - Race-condition-sensitive flows

### 4) Safety Controls During Testing

- Start with read-only and non-destructive validation
- Run risky payload validation in staging/parity environment first
- Keep real-time alerting and on-call responders active
- Define immediate stop conditions (service impact, data risk, latency spike)

### 5) Reporting and Prioritization

Track each finding with:
- Severity (Critical/High/Medium/Low)
- Affected service/endpoint
- Business impact
- Reproducibility steps
- Evidence/log references
- Recommended fix
- Owner and due date

Remediation order:
1. Critical
2. High
3. Medium

Each fix must include:
- Regression verification
- Security retest evidence

### 6) Retest and Hardening

- Verify patches by re-running the original test cases
- Confirm exploit path no longer works
- Apply durable controls:
  - WAF hardening rules
  - Rate-limit policies
  - Strict RBAC enforcement
  - Secret rotation cadence
  - Dependency update routine
- Establish recurring cadence:
  - Monthly vulnerability scanning
  - Quarterly pentest

---

## Security Finding Template

Use this template for each discovered issue:

| Field | Value |
|---|---|
| Finding ID | |
| Date | |
| Tester | |
| Severity | |
| Affected service/endpoint | |
| Impact summary | |
| Reproducibility steps | |
| Evidence (logs/screenshots/trace IDs) | |
| Recommended remediation | |
| Owner | |
| Target fix date | |
| Retest status | |