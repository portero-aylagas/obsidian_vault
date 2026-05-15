# Engineering Quality Prompts

> [!info] Purpose
> Use these prompts to raise the engineering quality bar of Python projects.
> They are designed for diagnosis first and small, controlled patches second.

## Main Rule

Do not ask:

```text
Improve everything.
```

Use this workflow instead:

```text
Diagnose first.
Patch second.
Patch only one controlled step at a time.
```

## Recommended Workflow

1. Run the general project quality audit.
2. Run the architecture and file structure audit.
3. Run the error handling audit.
4. Run the LLM/API integration audit if relevant.
5. Ask for a refactoring plan only.
6. Apply only the first safe patch.
7. Re-audit after each patch.

---

## General Project Quality Audit

```text
Review this Python project as a senior software engineer.

Context:
This is a bootcamp project. Keep recommendations beginner/intermediate-friendly.
Prefer clarity, maintainability, and small safe improvements over advanced abstractions.

Goal:
Improve code quality, maintainability, modularity, robustness, and debuggability.

Check specifically:
- Monolithic functions/classes
- Mixed responsibilities
- Repeated logic
- Bad naming
- Hardcoded values
- Hidden assumptions
- Silent failures
- Weak error handling
- Poor API boundaries between modules
- Dead code or unused imports
- Over-engineering
- Under-engineering
- Files that should be split
- Functions that should be merged
- Missing input validation
- Missing tests
- Bad project structure
- Security risks such as exposed API keys or unsafe file handling

Return:
1. High-level diagnosis
2. Concrete issues by file/function
3. Priority ranking: critical / important / nice-to-have
4. Exact recommended changes
5. What NOT to change
6. A minimal refactoring plan

Rules:
- Do not edit files yet.
- Do not rewrite the whole project.
- For every issue, explain why it matters.
```

---

## Architecture and File Structure Audit

```text
Analyze the architecture and file structure of this project.

Context:
This is a bootcamp project. Recommend structure improvements only when they reduce real confusion or duplication.

Check:
- Whether each file has a clear purpose
- Whether responsibilities are separated correctly
- Whether main.py only orchestrates
- Whether business logic is outside the UI layer
- Whether API/LLM calls are isolated
- Whether config, prompts, models, and utilities are in the right place
- Whether imports suggest circular dependencies or bad coupling
- Whether the current structure will scale if the project grows

Return:
1. Current architecture summary
2. Problems in the structure
3. Recommended file structure
4. What code should move where
5. Minimal changes needed now
6. Changes that would be overkill at this stage

Rules:
- Do not edit files yet.
- Do not propose a new structure unless it clearly improves the current project.
```

---

## Function Responsibility Audit

```text
Review every function in this project.

For each function, check:
- Does it do one thing?
- Is the name accurate?
- Are inputs and outputs clear?
- Does it mutate global state?
- Does it mix UI, file I/O, API calls, and business logic?
- Is it too long?
- Is it too small/useless?
- Should it be split, renamed, or merged?
- Does it need better error handling?

Return a table with:
- File
- Function
- Current responsibility
- Problem
- Recommended action
- Priority

Rules:
- Do not rewrite code unless the fix is very small.
- Prefer high-signal findings over listing harmless details.
```

---

## Error Handling Audit

```text
Audit error handling in this project.

Check:
- Where the code can fail
- Whether failures are visible or silent
- Whether exceptions are too broad
- Whether exceptions are swallowed
- Whether error messages explain WHERE and WHY
- Whether API errors are handled
- Whether file errors are handled
- Whether JSON/parsing errors are handled
- Whether user input errors are handled
- Whether environment variable errors are handled
- Whether the program exits cleanly or crashes badly

For each issue, return:
1. File/function
2. Failure scenario
3. Current behavior
4. Why it is bad
5. Minimal fix
6. Example error message format

Rules:
- Do not add complex logging unless it is justified.
- Do not edit files yet.
```

---

## UI Separation Audit

```text
Review the UI code in this project.

Check:
- Whether UI code is separated from business logic
- Whether callbacks are too large
- Whether callbacks call clean backend functions
- Whether UI state is handled cleanly
- Whether user inputs are validated before processing
- Whether errors are shown clearly to the user
- Whether long-running operations are structured sensibly
- Whether output components match backend return values
- Whether the UI imports too much internal logic

Return:
1. UI structure diagnosis
2. Callback problems
3. Input/output mismatch risks
4. Recommended backend function boundaries
5. Minimal refactor plan

Rules:
- Do not edit files yet.
- Keep the recommendations appropriate for a local bootcamp app.
```

---

## Testability Audit

```text
Review this project for testability.

Check:
- Which functions are easy to unit test
- Which functions are hard to test and why
- Whether logic is coupled to the UI framework, OpenAI, files, or environment variables
- Where mocks/fakes would be needed
- Which functions should be pure
- Which functions need integration tests
- Missing edge cases

Return:
1. Testability diagnosis
2. Functions that need refactoring before testing
3. Suggested unit tests
4. Suggested integration tests
5. Minimal test plan for this project

Rules:
- Do not edit files yet.
- Prioritize tests that give high confidence with low setup cost.
```

---

## Data and JSON Validation Audit

```text
Review data validation and JSON handling in this project.

Context:
This prompt is for general Python/data validation, not only LLM structured outputs. It is inspired by the W2D4 Python-for-low-code validation work.

Check:
- Where JSON, CSV, API responses, or user-provided structured data enter the project
- Whether required fields are checked before use
- Whether types are validated or converted safely
- Whether missing, null, malformed, or unexpected fields are handled
- Whether Pydantic, dataclasses, schemas, or plain validation functions are used appropriately
- Whether validation errors are readable and actionable
- Whether batch validation separates valid and invalid records
- Whether exported JSON can be reloaded and verified
- Whether validation logic is mixed into UI, file I/O, or API calls
- Whether invalid data can silently continue through the pipeline

Return:
1. Data/JSON entry points
2. Current validation approach
3. Failure scenarios
4. Minimal validation improvements
5. Suggested test cases
6. What is acceptable for a local bootcamp project

Rules:
- Do not edit files yet.
- Do not introduce Pydantic if simple validation functions are enough.
- Focus on preventing broken data from reaching later steps.
```

---

## Repository Hygiene Audit

```text
Review this repository for general engineering hygiene.

Context:
This is a bootcamp project, but I want it to follow normal professional repository practices where reasonable.

Check:
- Whether generated files are committed unnecessarily
- Whether cache folders are present
- Whether virtual environments are present
- Whether large temporary files are present
- Whether `.gitignore` covers common local/generated files
- Whether dependencies are listed clearly
- Whether there are duplicate or obsolete files
- Whether outputs should be kept as examples or removed
- Whether the repository layout is understandable

Return:
1. Repository hygiene diagnosis
2. Files/folders that should stay
3. Files/folders that should probably be removed
4. Files/folders that are acceptable but optional
5. Suggested `.gitignore` additions
6. Minimal cleanup plan

Rules:
- Do not delete anything yet.
- Be conservative. If unsure, mark it as "check before removing."
- Distinguish local bootcamp convenience from bad repository hygiene.
- For secrets and security-sensitive files, flag them but leave detailed analysis to the Security and Secrets Audit.
```

---

## Documentation Audit

```text
Review the documentation for this project as an engineering artifact.

Context:
The goal is not marketing polish. The goal is that another developer or future me can understand, run, and maintain the project.

Check:
- Whether the README explains the project goal
- Whether setup instructions are complete
- Whether dependencies are documented
- Whether environment variables are documented
- Whether there is a clear run command
- Whether there is a clear test command if tests exist
- Whether the project structure is explained
- Whether important modules are described
- Whether example inputs/outputs are provided
- Whether known limitations are documented
- Whether troubleshooting notes are needed

Return:
1. Documentation diagnosis
2. Missing documentation sections
3. Confusing or outdated sections
4. Minimal README improvements
5. Suggested project structure section
6. Suggested quick-start section

Rules:
- Do not edit files yet.
- Keep documentation practical and concise.
- Focus on what helps someone run and understand the project.
```

---

## Security and Secrets Audit

```text
Audit this project only for security and secret-handling issues.

Check:
- Hardcoded API keys
- .env or config files that should not be committed
- Unsafe file paths
- User-controlled paths
- Unvalidated uploads
- Prompt injection risks if documents/URLs are processed
- Overly verbose logging of sensitive data
- API responses or user inputs being stored unsafely

Return:
1. Security issues found
2. Severity
3. Exact file/location
4. Minimal fix
5. What is acceptable for a local student project
6. What would matter in production

Rules:
- Do not edit files yet.
- Distinguish local bootcamp risk from production risk.
- Do not duplicate general repository cleanup or README feedback.
```

---

## Refactor Plan Only

```text
Create a refactoring plan for this project.

Constraints:
- Do not rewrite code yet
- Do not introduce unnecessary frameworks
- Prefer small safe steps
- Preserve current behavior
- Keep it beginner/intermediate-friendly
- Avoid abstract architecture that does not solve a current problem

Return:
1. Step-by-step refactoring plan
2. Files affected in each step
3. Risk level per step
4. How to test after each step
5. Expected benefit
6. Stop point where further refactoring becomes unnecessary
```

---

## Apply First Safe Refactoring Patch

```text
Apply only the first safe refactoring step.

Rules:
- Before changing code, identify the files you will modify.
- Preserve behavior.
- Do not change unrelated files.
- Do not introduce new dependencies.
- Do not rewrite the whole project.
- Keep changes minimal.
- Add clear error handling where needed.
- Update imports if necessary.
- After editing, explain exactly what changed and why.
```

---

## Verify Last Code Patch

```text
Verify the last code patch.

Context:
A small refactoring or bug-fix patch was just applied. Review only the patch and its direct effects.

Check:
- Did behavior change unintentionally?
- Are imports still valid?
- Does the app still run?
- Did the patch introduce new coupling?
- Are errors clearer or more actionable?
- Did it modify unrelated files?
- Are README/setup instructions still accurate if touched?
- Are tests still valid?
- Are new tests needed?
- Is the patch smaller or larger than intended?

Return:
1. Patch summary
2. Behavior preserved: yes/no/uncertain
3. New issues introduced
4. Files that should be manually checked
5. Commands to run for verification
6. Whether another patch is justified
7. If another patch is justified, describe only the next smallest safe patch

Rules:
- Do not edit files yet.
- Be strict.
- Focus on the diff, not a full project re-audit.
```

---

## Best General Engineering Review Prompt

```text
Review this project as a senior Python/AI engineer.

Context:
This is a bootcamp project with LLM/API integration. I want to improve it before submission while keeping it beginner/intermediate-friendly.

Focus on:
- clear modular structure
- separation of UI, business logic, prompts, API calls, config, and file handling
- readable functions with single responsibilities
- safe environment variable handling
- clear error messages
- testability
- avoiding unnecessary abstractions

Rules:
- Do not edit files yet.
- Do not rewrite the project.
- Preserve current behavior.
- Prefer small, safe improvements.
- For each issue, cite the file/function and explain why it matters.

Return:
1. High-level diagnosis
2. Top 10 concrete issues
3. 5 highest-impact fixes
4. Suggested target structure, only if needed
5. Safe refactoring sequence
6. What should not be changed
7. First patch you would apply, but do not apply it yet
```
