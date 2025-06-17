<!-- place into .cursor/rules/pm.md -->
# AI Coding Agent Policy

## 1. Introduction

**Actors:**
- **User**: Defines requirements, prioritizes, approves, accountable for code
- **AI_Agent**: Executes User instructions per epics and tasks

## 2. Fundamental Principles

1. **Task-Driven Development**: All code changes require an agreed-upon authorizing task
2. **Epic Association**: Tasks MUST be associated with an agreed-upon epic
3. **User Authority**: User is sole decider for scope and design
4. **User Responsibility**: User is responsible for all code changes
5. **No Unapproved Changes**: Changes outside explicit task scope are PROHIBITED
6. **Task Focus**: AI_Agent works on ONE specific task at a time as instructed by User
7. **Status Management**: Update task status immediately using todo.md style (- [ ] todo, - [x] done)
8. **Research First**: When uncertain about implementation details, frameworks, APIs, or best practices, search the internet for current documentation and examples before proceeding
9. **Constants for Repeated Values**: Values used >1 MUST be named constants
10. **Scope Adherence**: Stay within task scope. Propose improvements as new tasks
11. **Change Confirmation**: Confirm epic/task association before making changes
12. **Preserve Existing Features**: NEVER remove or break existing functionality unless explicitly requested
13. **Variable Safety**: Before modifying existing variables, analyze all usage locations to prevent breaking changes
14. **Additive Development**: Prefer adding new code over modifying existing code when possible

## 3. Epic and Task Management

### 3.1 File Structure
```
epics/
├── epic-001-user-authentication.md
├── epic-002-data-pipeline.md
└── epic-003-api-integration.md
```

### 3.2 Epic File Format

Each epic file follows this structure:

```markdown
# Epic 001: User Authentication

## Overview
Brief description of the epic and its goals.

## Requirements
- High-level requirements for this epic
- Business objectives
- Success criteria

## Tasks

### Task 001-01: Setup Authentication Database Schema
- [ ] Create user table with email, password_hash, created_at
- [ ] Create sessions table for session management
- [ ] Add database migration scripts
- [ ] Test database schema creation

**Status**: Todo | InProgress | Done | Blocked
**Assigned**: [Date when work started]
**Completed**: [Date when marked done]

### Task 001-02: Implement User Registration
- [ ] Create registration endpoint
- [ ] Add password hashing with bcrypt
- [ ] Implement email validation
- [ ] Add registration tests

**Status**: Todo
**Assigned**:
**Completed**:

## Notes
- Implementation decisions
- Architecture notes
- Dependencies between tasks
```

### 3.3 Task Workflow

**Statuses**: Todo, InProgress, Done, Blocked

**Working Process**:
1. User specifies: "Work on Epic 001, Task 001-01"
2. AI_Agent updates task status to "InProgress" and adds assigned date (use CURRENT date)
3. **Impact Analysis**: Before modifying existing code, AI_Agent must:
   - Search codebase for all usages of variables/functions being modified
   - Identify potential breaking changes
   - If changes affect existing functionality, request User approval first
   - Document what existing code will be modified and why
4. AI_Agent implements the task following the checklist
5. AI_Agent commits code with message: `001-01: Setup Authentication Database Schema`
6. **IMPORTANT**: AI_Agent does NOT mark task as "Done" or check off items until:
   - User explicitly confirms the implementation works as specified
   - All functionality has been tested and approved by User
   - User gives explicit approval to mark task complete
7. Only after User approval, AI_Agent:
   - Marks all checklist items as `- [x] done`
   - Updates status to "Done" and adds completion date (use CURRENT date)
   - Moves completed task to "Completed Tasks" section

### 3.4 Task ID Format
- Epic ID: 3 digits (001, 002, 003...)
- Task ID: Epic-ID + dash + 2 digits (001-01, 001-02, 002-01...)

## 4. Version Control

### 4.1 Commit Messages
Format: `<task-id>: <task-description>`
Example: `001-01: Setup Authentication Database Schema`

### 4.2 Branch Strategy (if applicable)
- Create feature branch for each task: `task/001-01-auth-db-schema`
- Merge to main when task is Done

## 5. Testing Requirements

### 5.1 Test Plan per Task
Each task with code changes must include:
- Unit tests for new functions/classes
- Integration tests for component interactions
- Basic compilation/syntax verification

### 5.2 Test Locations
- Unit tests: `test/unit/`
- Integration tests: `test/integration/`

### 5.3 Completion Criteria
No task marked "Done" without:
- All checklist items implemented (but not checked off until User approval)
- Code committed with proper task ID
- **User explicit approval** that functionality works as specified
- Only then: check off items and update status to "Done"

## 6. AI Agent Instructions

1. **Always confirm epic and task** before starting work
2. **Update task status to "InProgress"** when starting work (use CURRENT date)
3. **Research when needed**: If you don't know how to implement something, search the internet for official documentation, tutorials, or best practices BEFORE starting implementation
4. **Conduct impact analysis**: Before modifying existing code, search codebase for dependencies and potential breaking changes
5. **Graduated approval for existing code changes**:
   - **No approval needed**: Adding imports, new functions/classes, minor integration code, new routes/endpoints
   - **Requires approval**: Modifying function signatures, changing variable behavior/types, refactoring existing logic, database schema changes
   - **Always requires approval**: Removing existing features, breaking changes to APIs, major refactoring
6. **Follow the checklist** - implement each item but do NOT check them off
7. **Commit code** with proper task ID in message when implementation is complete
8. **Wait for User approval** - do NOT mark task as "Done" or check off items until User explicitly confirms the implementation works
9. **Use current date** - never use historical dates, always use today's actual date
10. **Ask for clarification** if task requirements are unclear
11. **Propose new tasks** for scope outside current task
12. **Focus on one task** - no parallel work unless explicitly approved
13. **Preserve existing functionality** - Never delete or modify existing features unless explicitly required by the task
14. **No feature removal suggestions** - Never suggest removing existing features, even if they seem unused
15. **Implementation vs Completion**: Implementation = code written and committed; Completion = User approved and confirmed working

## 7. User Instructions for AI

To assign work, use format:
```
Work on Epic [XXX], Task [XXX-XX]: [Task Name]
```

Example:
```
Work on Epic 001, Task 001-01: Setup Authentication Database Schema
```

**To approve completion**, use format:
```
Approve Task [XXX-XX] - mark as completed
```

**Important**: AI will implement and commit code, but will NOT mark tasks as "Done" until you explicitly approve.
