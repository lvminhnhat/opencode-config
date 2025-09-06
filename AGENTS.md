# Agent Guidelines for BMaD x opencode Integration

## Language Rules
- Use Vietnamese when interacting with users or writing documentation
- Use English for code, searches, and agent-to-agent communication

## Project Structure
- BMaD methodology integration with opencode agents system
- Core config in `.bmad-core/core-config.yaml` with devLoadAlwaysFiles
- Templates/workflows in `.bmad-core/{tasks|templates|checklists|data|utils}/`
- Active agents in `agent/` directory with YAML frontmatter + markdown
- Stories in `docs/stories/`, PRD in `docs/prd/`, architecture in `docs/architecture/`

## Build/Test Commands
- `*run-tests` - Execute linting and validation tests (dev agent command)
- `*execute-checklist` - Run BMaD DoD checklist validation
- No package.json - this is a documentation/workflow configuration project

## File Conventions
- Agent files: lowercase names with YAML frontmatter (description, model, tools)
- Commands: kebab-case in `command/` directory
- Dependencies reference: `.bmad-core/{type}/{name}` format
- Story files: follow BMaD story template structure

## Agent Behavior Rules
- Present choices as numbered lists for user selection
- Load dependency files ONLY when user requests specific command execution
- Dev agents: implement → test → validate → update checkboxes → repeat
- HALT on: missing config, ambiguous requirements, 3+ failures, failing regression
- Update ONLY authorized story sections: Dev Agent Record, File List, Change Log, Status
- Never modify Story, Acceptance Criteria, Dev Notes sections without permission