# Agent Skills

**Source**
- `lessons/W4D2_AI_agent_skills/lab_source/Ironhack Student Portal.html`

**Related labs**
- `W4D2_three_reflection_skills`
- `W3D5_MCP_in_codex_and_claude_code`

## Main Techniques
- Agent skills
- `SKILL.md`
- YAML frontmatter
- Skill descriptions for implicit activation
- Progressive disclosure
- Skill folder structure
- `scripts/`
- `references/`
- `assets/`
- Skill scope control
- Skills vs MCP

## Core Idea
An agent skill packages repeatable agent behavior into a reusable folder.

It is not a one-off prompt. It is a durable instruction package that can include:
- a `SKILL.md` file with required metadata and instructions
- optional scripts for deterministic steps
- optional references for longer documentation
- optional assets such as templates or examples

The value is consistency. A skill helps an assistant handle the same class of task in the same way across future sessions.

## Standard Skill Shape

```text
skill-folder/
-> SKILL.md
-> scripts/
-> references/
-> assets/
```

`SKILL.md` normally contains YAML frontmatter with at least:

```yaml
name: skill-name
description: Use this skill when...
```

The description is important because it acts as the routing signal for implicit activation.

## Progressive Disclosure
Progressive disclosure means the agent does not load the full skill immediately.

The usual flow is:

```text
user request
-> agent sees skill metadata
-> description matches task intent
-> agent opens SKILL.md
-> agent opens references/scripts/assets only when needed
```

This keeps context smaller and avoids loading long instructions that are irrelevant to the current task.

## Description Field
The description should explain when to use the skill from the user's point of view.

Good description pattern:

```text
Use this skill when the user wants to review SQL migrations for safety, rollback risk, schema compatibility, or production deployment readiness.
```

Weak description pattern:

```text
This skill reviews SQL.
```

Useful description habits:
- describe the user's goal
- include likely wording the user might use
- set boundaries for near-miss cases
- keep the description concise
- prefer "Use this skill when..." phrasing

## Creating Skills Well

Strong skills come from real repeated work:
- a task you completed with an agent
- a runbook
- an API specification
- a style guide
- repeated corrections you had to make
- domain-specific review criteria

Bad skills are usually too broad.

```text
Weak scope:
all data tasks

Better scope:
review dbt model changes for naming, lineage, tests, and warehouse cost risk
```

Use one coherent workflow per skill. Scope it like a well-named function.

## When To Add Files

Use `references/` when the agent needs long documentation only sometimes:
- API error tables
- policy manuals
- long style guides
- schema conventions

Use `scripts/` when the same deterministic step happens repeatedly:
- validation commands
- data extraction
- lint checks
- report generation

Use `assets/` when the skill needs static material:
- templates
- example outputs
- sample configs

## Skills vs MCP

| Mechanism | Main Role |
|---|---|
| Skills | Encode procedure, expertise, review behavior, and task-specific judgment |
| MCP | Expose tools, services, files, APIs, databases, or external capabilities |

Short version:

```text
Skills tell the agent how to work.
MCP gives the agent things it can use.
```

They combine well. A skill can instruct the agent when and how to use an MCP tool.

## How This Connects To The Course

Week 3 introduced agents, tools, and MCP:
- [[../Frameworks/LangChain]]
- [[../Frameworks/MCP]]

Week 4 adds controlled execution and automation:
- [[../Frameworks/LangGraph]]
- [[../n8n/n8n Workflows]]

Agent skills sit above those tools. They are not another execution framework. They are reusable operational knowledge for agents.

## Practical Heuristics
- Create a skill only when the task repeats.
- Keep one skill focused on one workflow.
- Put only high-signal instructions in `SKILL.md`.
- Move long details into `references/`.
- Use scripts for repeatable deterministic checks.
- Write the description for task intent, not implementation details.
- Improve skills from real traces and mistakes.

## Key Idea
Agent skills turn repeated prompting and review behavior into maintainable agent procedure.

They are useful when a task needs consistent judgment, domain rules, or a repeatable workflow that should not be reconstructed from scratch every time.
