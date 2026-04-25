---
description: 'Generate comprehensive unit tests for a function, class, or module'
mode: 'agent'
tools: ['codebase', 'search', 'usages', 'editFiles', 'runTests']
---

# Generate Unit Tests

Your goal is to generate a complete, runnable unit test file for ${input:target:the selected code}.

If nothing is selected, ask which file or symbol to test before proceeding. Do not guess.

## Step 1 — Detect the Test Stack

Before writing any tests, inspect the workspace to determine the existing test framework and conventions:

- Check `package.json`, `*.csproj`, `pom.xml`, `requirements.txt`, or `pyproject.toml` for the test framework already in use (Jest, Vitest, xUnit, NUnit, JUnit, pytest, etc.).
- Look for an existing test file near the target (e.g., `Foo.test.ts` next to `Foo.ts`, or `test_foo.py` next to `foo.py`) and match its style exactly — imports, naming, folder location, assertion library.
- If no convention exists, default to: **Jest** for TS/JS, **xUnit** for C#, **pytest** for Python, **JUnit 5** for Java.

State the detected framework in one line before generating tests.

## Step 2 — Identify What to Test

Use the `usages` tool to see how the target is called elsewhere in the codebase. This reveals the real contract, not just the signature.

Enumerate the test cases you plan to write **before** writing them. Cover:

1. **Happy path** — typical valid input, expected output.
2. **Boundary values** — empty inputs, zero, negative numbers, max/min values, single-element collections.
3. **Invalid input** — wrong type, null/undefined, malformed data. Assert the correct error is thrown.
4. **Edge cases specific to the logic** — e.g., for a date function, leap years and DST transitions; for a parser, unicode and whitespace.
5. **Side effects** — if the function writes to disk, calls an API, or mutates state, verify the interaction (using mocks/spies).

Skip cases that don't apply. Do not pad the test file with redundant assertions.

## Step 3 — Write the Tests

Follow these rules:

- **One assertion per concept.** Multiple `expect` calls are fine if they describe the same behavior; split into separate tests when they describe different behaviors.
- **Arrange–Act–Assert.** Use blank lines or comments to separate the three phases.
- **Descriptive names.** Test names should read like a sentence: `returns empty array when input is null`, not `test1`.
- **No shared mutable state** between tests. Use `beforeEach` for setup, not module-level variables.
- **Mock external dependencies** (HTTP, filesystem, database, time). Never let a unit test hit the network.
- **Deterministic.** No `Math.random()`, no real timestamps, no flaky waits.

## Step 4 — Place the File

Create the test file in the location matching the existing convention. If creating a new test directory, mirror the source structure (e.g., `src/utils/format.ts` → `tests/utils/format.test.ts`).

After writing the file, run the test suite using the `runTests` tool and report the result. If any test fails, fix the test (not the source code) unless the failure reveals a genuine bug — in which case, flag it clearly and stop.

## Output

End with a short summary in this format:

```
Framework: <detected>
File created: <path>
Tests written: <count>
Status: <passing | failing — see above>
```

Do not modify the source file under test unless the user explicitly asks for it.
