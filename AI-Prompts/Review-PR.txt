Review the current GitHub PR as a senior software engineer.

First:
1. Read CLAUDE.md if it exists.
2. Read relevant files in .claude/ if they exist.
3. Understand the project's architecture, coding standards, business logic, and testing approach.
4. Identify the PR branch and compare it against its target/base branch.
5. Review the complete git diff, not just individual files.

Review the PR for:

- Functional bugs
- Business logic errors
- Security vulnerabilities
- Authentication and authorization issues
- Input validation
- Error handling
- Database/query issues
- Transaction and rollback problems
- Race conditions
- Async/await and promise issues
- Performance problems
- API breaking changes
- Backward compatibility
- TypeScript/JavaScript issues
- Missing edge-case handling
- Environment/configuration issues
- Logging/observability problems
- Test coverage and missing tests
- Dependency risks
- Maintainability problems

Do not limit the review to changed lines. Inspect surrounding code and call sites when needed to determine whether the implementation is correct.

Only report actionable findings.

Do NOT report:
- Formatting issues
- Linter/prettier issues
- Purely subjective style preferences
- Minor refactoring suggestions without meaningful benefit
- Hypothetical issues without a realistic failure scenario
- Unrelated problems that already existed before this PR

For every finding, provide:

Severity: CRITICAL / HIGH / MEDIUM / LOW
File: <path>
Line: <line>
Issue: <clear explanation>
Impact: <why this can cause a real problem>
Recommendation: <specific fix>

Pay special attention to:
- Authorization bypass / IDOR
- Missing validation
- Null/undefined handling
- Incorrect database queries
- N+1 queries
- Duplicate operations
- Transaction consistency
- Incorrect status codes
- Sensitive data exposure
- Injection vulnerabilities
- Broken error handling
- Race conditions
- Retry/idempotency problems
- Date/time/timezone issues
- Incorrect assumptions about existing data
- Breaking changes to existing APIs
- Missing tests for important business logic

After completing the review, provide:

PR Review Result:
- APPROVE
- APPROVE WITH MINOR CHANGES
- REQUEST CHANGES

Risk:
- LOW
- MEDIUM
- HIGH
- CRITICAL

Summary:
<brief overall assessment>

Must Fix Before Merge:
<list only blocking issues>

Non-Blocking Recommendations:
<optional improvements>

Required Tests:
<specific tests that should be added or run>

Do not modify any files.
Do not commit anything.
Do not fix the issues automatically.
This is a review-only task.