# W4D2 Reflection Skills Lab

**Source folder**
- `W4D2_three_reflection_skills`

**Main files**
- `lab_source/Ironhack Student Portal.html`

**Lab type**
- open-ended skills lab
- Main value: use agent skills to create repeatable learning and review rituals inside a coding assistant

## What This Lab Teaches

This lab treats skills as small reusable cognitive workflows.

```text
session notes / stuck moment / code snippet
-> selected skill
-> structured reflection or review
-> next learning action
```

The important idea is progressive disclosure: a skill should be discoverable by description, then provide just enough instructions for the assistant to perform a useful ritual.

## Techniques Practiced

- agent skill authoring
- `SKILL.md` structure
- YAML frontmatter
- description-based routing
- progressive disclosure
- realistic skill testing
- reflection prompts
- obstacle analysis
- misconception scanning
- reviewer-role prompting

## Important Architecture

```text
learning-environment/
-> session-recap/SKILL.md
-> honest-check-in/SKILL.md
-> review-roles/SKILL.md
```

Each skill has a different trigger and output shape, but all are designed to make learning more explicit.

## Important Code Patterns

The core pattern is skill metadata:

```yaml
---
name: session-recap
description: Use after a learning or troubleshooting session to extract concepts and process reflection.
---
```

## What Was Provided

The lab source provides the three-skill design, recommended folder tree, and validation prompts. The workspace currently contains the HTML source but no created skill files.

## What I Practiced

- designing reusable assistant behavior
- writing descriptions that trigger the right skill
- testing whether a skill activates as expected
- using reflection as part of technical learning
- separating recap, obstacle review, and critique roles

## Links to Topic Notes

- [[../Agentic/Effective Context Engineering for AI Agents]]
- [[../Agentic/Agent Skills]]
- [[../Prompt Library/Learning Extraction Prompts]]
- [[../Prompt Library/Engineering Quality Prompts]]

## What To Reuse Later

- Use skill descriptions as routing logic.
- Keep skill instructions short until more detail is needed.
- Test skills with realistic prompts, not abstract examples.
- Separate supportive reflection from critical review.
- End review skills with useful questions, not only assertions.

## Improvement Ideas

- Add references for longer reflection frameworks.
- Create a shared output template for study notes.
- Add examples for implicit routing tests.
- Version skills as learning style changes.

## Key Takeaway

Skills are not only for automation. They can encode repeatable ways of learning, reflecting, and reviewing work with an assistant.
