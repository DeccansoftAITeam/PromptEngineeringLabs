---
description: 'Perform a thorough code review with structured, actionable feedback'
mode: 'agent'
model: 'GPT-5'
tools: ['codebase', 'search', 'usages', 'problems']
---

# Code Review

Your goal is to perform a comprehensive code review of ${input:target:the currently open file} and produce structured, actionable feedback.

If no specific file or selection is provided, review the active editor's selection. If nothing is selected, review the entire active file.

## Review Scope

Focus the review on the following areas, in this order of priority:

1. **Correctness** — logic errors, off-by-one mistakes, incorrect null/undefined handling, race conditions, unhandled exceptions.
2. **Security** — input validation, injection risks (SQL, XSS, command), secrets in code, insecure dependencies, improper authentication or authorization checks.
3. **Performance** — N+1 queries, unnecessary loops, blocking I/O on hot paths, memory leaks, missing pagination or caching where appropriate.
4. **Readability & Maintainability** — naming, function length, single-responsibility violations, dead code, missing or misleading comments.
5. **Testing** — missing test coverage for new logic, edge cases not asserted, brittle test design.
6. **Style** — adherence to the conventions described in `.github/copilot-instructions.md` (if present in the workspace).

## Output Format

Produce the review as Markdown with the following exact structure:

### Summary
A 2–3 sentence overview of the overall code quality and the most important issue to address.

### Critical Issues
List each issue as a bullet. Format: `- **[file:line]** Description — *Suggested fix*`. Only include issues that block merge (bugs, security holes, broken tests).

### Recommendations
List non-blocking improvements in the same format. These are nice-to-haves: refactoring suggestions, naming improvements, minor performance tweaks.

### Positives
Briefly call out 1–3 things the author did well. This is not optional — finding something to acknowledge keeps reviews collaborative.

## Rules

- Reference exact file paths and line numbers. If you cannot locate the line, say so explicitly rather than guessing.
- Quote the problematic code in fenced code blocks before suggesting a fix.
- For every "Suggested fix," provide a concrete code snippet, not a vague description.
- Do **not** rewrite the entire file. Suggest the smallest change that resolves the issue.
- If the code looks fine, say so. Do not invent issues to pad the review.
- If you need more context (e.g., how a function is used elsewhere), use the `usages` tool before flagging an issue.

## Severity Tags

Prefix each Critical Issue with one of: `[BUG]`, `[SECURITY]`, `[PERF]`, `[BREAKING]`.
Prefix each Recommendation with one of: `[REFACTOR]`, `[NAMING]`, `[STYLE]`, `[TEST]`, `[DOCS]`.
