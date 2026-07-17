# PathReview Contribution Journal

## Week 7 — Issue selection

**Issue link:** https://github.com/ascherj/pathreview/issues/154

**Issue title:** Health check DB probe passes a raw SQL string, which fails under SQLAlchemy 2.x

**Tier:** [x] Tier 1  [ ] Tier 2  [ ] Tier 3

**Problem summary:**
The health-check endpoint tests the database connection by executing a raw SQL string in `api/routes/health.py`. SQLAlchemy 2.x does not allow this type of SQL statement unless it is wrapped with `sqlalchemy.text()`. Because of this, the health check can incorrectly report that the database is unavailable even when it is running. A successful fix will update the database probe and include a test showing that the health check works correctly.

**Selection notes:**
This issue is a reasonable size for me because it mainly affects one API file and its related tests. The issue provides clear reproduction information and identifies the likely cause. I can run the application and tests locally, and the expected result is specific and testable. The change should not require redesigning the application or modifying several unrelated systems.

**Branch name:** `fix/154-health-check-sql`

**Setup confirmation:** [x] App runs locally at localhost:5173

**Cohort ledger:** [x] Issue added to cohort ledger