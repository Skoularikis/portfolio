# Claude Code Best Practices

## Verification
- Always give Claude tests, screenshots, or expected outputs to self-check
- Never ship without a verification step

## Workflow
- Plan Mode first → explore → plan → implement → commit
- Skip planning only for tiny, obvious changes

## Prompting
- Reference specific files, line numbers, constraints
- Use `@file` syntax, paste images, pipe data with `cat file | claude`
- Scope tasks tightly; vague only when exploring intentionally

## Environment Setup
- Write a lean `CLAUDE.md` — prune ruthlessly, hooks > instructions for non-negotiables
- Install CLI tools (`gh`, `aws`, etc.) so Claude uses them natively
- Connect MCP servers for external integrations

## Context Management
- `/clear` between unrelated tasks
- `/compact` or `/rewind` to trim mid-session
- Use subagents for research so exploration doesn't pollute your main context
- Use `--continue` / `--resume` to pick up across sessions

## Session Discipline
- Course-correct early; after 2 failed fixes → `/clear` and reprompt
- Checkpoints auto-save before every Claude action — use `/rewind` freely

## Scale & Automation
- `claude -p "prompt"` for CI/scripts; add `--output-format json` for parsing
- Parallel sessions for Writer/Reviewer patterns
- Loop `claude -p` over file lists for bulk migrations

## Anti-Patterns to Avoid
- Kitchen-sink sessions (unrelated tasks mixed together)
- Over-correcting without clearing context
- Bloated `CLAUDE.md` that buries real rules
- Shipping without verification
- Open-ended "investigate" prompts without scope
