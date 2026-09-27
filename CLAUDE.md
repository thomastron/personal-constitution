# CLAUDE.md — Socratic Debater Project

Project instructions for Claude Code. The instructions shared by every coding agent live in `AGENTS.md`, which this file imports so there is a single source of truth. Edit `AGENTS.md`, not this file, unless a rule is Claude-specific.

@AGENTS.md

## Claude Code notes

- **Slash commands.** The `/socratic` and `/dog-walk` workflows are defined in `commands/socratic.md` and `commands/dog-walk.md`. Claude Code only registers project slash commands from `.claude/commands/`, so to invoke them as `/socratic` and `/dog-walk`, copy them there. Otherwise ask directly: *"Follow `commands/socratic.md` for this claim: …"*.
