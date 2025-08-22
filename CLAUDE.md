# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This repository contains the BMad-Method framework (Breakthrough Method of Agile AI-driven Development) - a modular AI agent system for structured software development workflows. The project provides specialized AI agents that follow Agile methodologies to assist with everything from product planning to code implementation.

## Architecture

### Core Structure

- **`web-bundles/`** - Pre-built agent bundles for web AI interfaces
  - **`agents/`** - Individual specialized AI agent definitions
  - **`teams/`** - Team configurations combining multiple agents
  - **`expansion-packs/`** - Domain-specific agent extensions

### Key Components

**Agent System:**
- Each agent is defined in a text file with YAML configuration
- Agents have specialized roles: analyst, pm (Product Manager), architect, dev (Developer), qa, ux-expert, po (Product Owner), sm (Scrum Master)
- Meta-agents: bmad-orchestrator (coordination), bmad-master (universal capabilities)

**Agent Capabilities:**
- Template-driven document creation (PRDs, architecture specs, user stories)
- Interactive elicitation methods for content refinement
- Structured task execution with dependency management
- Built-in quality assurance checklists

## Development Workflow

### No Traditional Build System
This project has no package.json, Makefile, or traditional build commands. It's a framework of structured prompts and templates for AI-assisted development.

### Agent Usage Patterns

**For Planning (Web UI Recommended):**
```
/pm create-doc prd          # Create Product Requirements Document
/architect create-doc architecture    # Create technical architecture
/analyst perform-market-research      # Market analysis
```

**For Development (IDE):**
```
@sm *create                 # Create next user story
@dev develop-story         # Implement story
@qa review-story          # Quality assurance review
```

**Document Management:**
```
*shard-doc docs/prd.md prd           # Break large documents into manageable pieces
*shard-doc docs/architecture.md architecture
```

### Key Workflow Principles

1. **Clean Context Windows** - Start fresh chats when switching between agents
2. **Sequential Development** - Complete one story before starting the next
3. **Document-Driven** - All development follows structured PRD and architecture documents
4. **Agent Specialization** - Use specific agents for their expertise areas

## Common Commands

### Agent Commands (in context)
- `*help` - Show available commands for current agent
- `*status` - Show current context and progress
- `*exit` - Exit agent mode
- `*create` - Execute create-next-story task (SM agent)
- `*develop-story` - Implement user story (Dev agent)

### Document Commands
- `*shard-doc {file} {type}` - Split document into smaller sections
- `*doc-out` - Output current document to file
- `*yolo` - Toggle skip-confirmations mode

## Agent Roles

| Agent | Role | Use For |
|-------|------|---------|
| analyst | Business Analyst | Market research, competitive analysis, project briefs |
| pm | Product Manager | PRD creation, feature prioritization, product strategy |
| architect | Solution Architect | System design, technical architecture |
| dev | Developer | Code implementation, debugging, development tasks |
| qa | QA Specialist | Code review, testing strategies, quality assurance |
| ux-expert | UX Designer | UI/UX design, user experience, prototypes |
| po | Product Owner | Backlog management, story validation |
| sm | Scrum Master | Sprint planning, story creation from requirements |
| bmad-orchestrator | Team Coordinator | Multi-agent workflows, agent switching |
| bmad-master | Universal Expert | All capabilities without agent switching |

## Development Best Practices

### Document Structure
- Place final documents at `docs/prd.md` and `docs/architecture.md`
- Shard large documents into `docs/prd/` and `docs/architecture/` folders
- User stories go in `docs/stories/`

### Agent Workflow
1. Use planning agents (PM, Architect) for documentation
2. Always shard documents before starting development
3. Use SM agent for story creation from sharded documents
4. Use Dev agent for implementation
5. Use QA agent for code review and quality assurance

### Context Management
- Keep agent conversations focused on single tasks
- Start new chats when switching between SM → Dev → QA cycles
- Provide story content directly to Dev agent to save lookup time

## Important Notes

- This is a framework for AI-assisted development, not traditional software
- No code compilation or testing - the "code" is structured prompts and templates
- The system relies on AI agents following structured workflows
- All functionality is contained within the agent bundle files
- Designed for both web AI interfaces and IDE integration