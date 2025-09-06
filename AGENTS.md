# Agent Guidelines for BMaD x opencode Integration

## Language Rules
- Use Vietnamese when interacting with users or writing documentation
- Use English for code, searches, and agent-to-agent communication

## Project Structure
- This is a BMaD methodology integration with opencode agents system
- Core files in `.bmad-core/` contain templates, workflows, and agent definitions
- Active agents in `agents/` and commands in `commands/` directories
- Stories located in `docs/stories/` (when created)

## Build/Test Commands
- No package.json found - this is a documentation/configuration project
- Tests referenced via `*run-tests` command in dev agent (executes linting and tests)
- Validation through BMaD checklist execution: `execute-checklist` command

## Code Style Guidelines
- Follow existing markdown formatting patterns in agent files
- YAML frontmatter required for agent definitions with model, tools, description
- File naming: kebab-case for commands, lowercase for agents
- Reference dependencies as `.bmad-core/{type}/{name}` format

## Agent Behavior
- Always use numbered lists when presenting choices to users
- Load dependency files only when user requests specific command execution
- Follow sequential task execution: implement → test → validate → update checkboxes
- HALT on missing config, ambiguous requirements, or failing regressions
- Update only authorized story sections (Dev Agent Record, File List, Change Log)