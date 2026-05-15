# Submission Review Prompts

> [!info] Purpose
> Use these prompts before submitting a bootcamp lab/project or presenting it to a teacher/stakeholder.

---

## Submission Readiness Review

```text
Review this repository as a lab/project submission.

Context:
Assume engineering hygiene and documentation have already been reviewed separately.
Focus on whether a teacher or stakeholder can quickly understand and evaluate the project.

Check:
- Is the project goal clear within the first minute?
- Is it obvious what the app/lab does?
- Is the main flow easy to demo?
- Are the AI techniques used visible to a reviewer?
- Is the student's/team's contribution understandable?
- Are limitations or assumptions stated?
- Are there any final blockers that would prevent evaluation?

Return:
1. Submission readiness score from 0 to 10
2. What a reviewer will understand quickly
3. What a reviewer may find confusing
4. Final blockers before submission
5. Minimal changes to improve reviewability
6. Final presentation/readiness checklist

Rules:
- Do not edit files yet.
- Distinguish required fixes from nice polish.
- Do not duplicate the Documentation Audit or Repository Hygiene Audit unless an issue blocks submission.
```

---

## Final Demo Readiness Prompt

```text
Review this project for demo readiness.

Context:
This will be shown in a bootcamp setting. The goal is a clear, reliable demo, not production perfection.

Check:
- Can the app run from a clean setup?
- Is the main user flow obvious?
- Are sample inputs available?
- Are expected outputs clear?
- Are API keys/environment variables documented?
- Are long-running steps understandable to the user?
- Are errors understandable during a demo?
- Is there a fallback if the ideal demo input fails?
- Are generated outputs saved or visible?

Return:
1. Demo readiness diagnosis
2. Highest-risk demo failure points
3. Minimal fixes before presenting
4. Suggested demo script
5. Backup plan if API/file/input fails

Rules:
- Do not edit files yet.
- Focus on practical demo reliability.
```

---

## Teacher Review Simulation

```text
Review this project as a bootcamp instructor with limited time.

Assume you have 5-10 minutes to understand the repo.

Check:
- Is the goal clear?
- Is the code understandable?
- Is the project structure reasonable?
- Can I run it?
- Can I see what AI techniques were used?
- Can I see what the student/team contributed?
- Are limitations and future improvements clear?

Return:
1. First impression
2. What is strong
3. What is confusing
4. What might reduce the grade
5. Minimal changes to improve reviewability
6. Suggested README summary paragraph

Rules:
- Do not edit files yet.
- Focus on clarity for a human reviewer.
```

---

## Final Submission Checklist Prompt

```text
Create a final submission checklist for this project.

Include:
- expected demo flow
- known limitations
- reviewer-facing explanation
- visible AI techniques
- sample inputs or demo data
- backup plan if an API call or file input fails
- final run-through before presenting

Return:
1. Checklist grouped by priority
2. Items already satisfied
3. Items missing
4. Fastest path to submission readiness

Rules:
- Do not duplicate detailed documentation, repo hygiene, or security audits.
- Focus on final review/presentation readiness.
```
