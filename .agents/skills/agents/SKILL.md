```markdown
# agents Development Patterns

> Auto-generated skill from repository analysis

## Overview
This skill introduces the core development patterns and workflows used in the `agents` TypeScript codebase. It covers coding conventions, file organization, commit practices, and the main product specification workflow. By following these guidelines, contributors can write consistent, maintainable code and effectively participate in the product planning process.

## Coding Conventions

### File Naming
- Use **camelCase** for file names.
  - Example: `agentManager.ts`, `userProfile.test.ts`

### Import Style
- Use **relative imports** for referencing modules.
  - Example:
    ```typescript
    import { Agent } from './agentManager';
    ```

### Export Style
- Use **named exports** rather than default exports.
  - Example:
    ```typescript
    // agentManager.ts
    export function createAgent() { ... }
    export const AGENT_VERSION = '1.0.0';
    ```

### Commit Messages
- Follow **conventional commit** format.
  - Prefixes: `feat` (feature), `fix` (bugfix)
  - Example:  
    ```
    feat: add agent scheduling logic
    fix: correct agent initialization bug
    ```

## Workflows

### Conductor Spec and Plan Update
**Trigger:** When introducing or updating a Conductor product/track specification and its implementation plan  
**Command:** `/update-conductor-spec`

1. **Edit or add the specification file:**
   - Path: `.conductor/tracks/<track-name>/spec.md`
   - Define or update:
     - Functional requirements
     - Acceptance criteria
     - Risk register
   - Example:
     ```markdown
     ## Functional Requirements
     - Agents must support dynamic task allocation.

     ## Acceptance Criteria
     - [ ] Tasks are assigned within 100ms.

     ## Risk Register
     - Integration with legacy systems may cause delays.
     ```
2. **Edit or add the implementation plan:**
   - Path: `.conductor/tracks/<track-name>/plan.md`
   - Outline or revise:
     - Implementation phases
     - Tasks
     - Checkpoints
   - Example:
     ```markdown
     ## Phase 1: Core Logic
     - [ ] Implement agent scheduler
     - [ ] Write integration tests

     ## Phase 2: UI Integration
     - [ ] Connect to dashboard
     ```
3. **(Optional) Update overall product vision:**
   - Path: `.conductor/product.md`
   - Revise product vision or scope as needed.

## Testing Patterns

- **Test files** use the pattern: `*.test.*` (e.g., `agentManager.test.ts`)
- **Testing framework** is not specified; check existing test files for conventions.
- Example test file structure:
  ```typescript
  // agentManager.test.ts
  import { createAgent } from './agentManager';

  describe('createAgent', () => {
    it('should initialize agent with default values', () => {
      const agent = createAgent();
      expect(agent.status).toBe('idle');
    });
  });
  ```

## Commands

| Command                | Purpose                                                        |
|------------------------|----------------------------------------------------------------|
| /update-conductor-spec | Create or update a Conductor product/track spec and plan files |
```
