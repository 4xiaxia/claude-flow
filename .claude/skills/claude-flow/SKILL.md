```markdown
# claude-flow Development Patterns

> Auto-generated skill from repository analysis

## Overview
This skill teaches you the core development patterns and workflows used in the `claude-flow` repository, a TypeScript codebase built on the Hono framework. You'll learn about the project's coding conventions, how to manage dependencies across a monorepo, and how to write and organize tests.

## Coding Conventions

### File Naming
- Use **kebab-case** for all file names.
  - Example: `api-handler.ts`, `user-service.ts`

### Import Style
- Use **relative imports** for internal modules.
  - Example:
    ```typescript
    import { getUser } from './user-service';
    ```

### Export Style
- Use **named exports**.
  - Example:
    ```typescript
    // user-service.ts
    export function getUser(id: string) { ... }
    ```

### Commit Messages
- Commit messages are **freeform** (no strict prefix), typically concise (~65 characters).
  - Example: `fix bug in user authentication flow`

## Workflows

### Dependency Update Across Monorepo
**Trigger:** When you need to update one or more npm dependencies across multiple packages/plugins in the repository (e.g., via Dependabot or manually).
**Command:** `/update-dependencies`

1. Identify outdated dependencies in all relevant `package.json` files (including subdirectories like `v*/`).
2. Update the version(s) of the dependency in each relevant `package.json`.
3. Update corresponding lockfiles (`package-lock.json`, `pnpm-lock.yaml`) in each directory.
4. Commit all changed `package.json` and lockfile(s) together.
5. Write a detailed changelog in the commit message describing the updates.

**Example:**
```shell
# Manually update a dependency in multiple packages
cd packages/api
npm install some-dependency@latest
cd ../core
npm install some-dependency@latest

# Update lockfiles
npm install

# Commit changes
git add packages/*/package.json packages/*/package-lock.json
git commit -m "Update some-dependency to vX.Y.Z across monorepo"
```

## Testing Patterns

- Test files use the `*.test.*` naming pattern.
  - Example: `user-service.test.ts`
- The specific testing framework is **unknown** from the analysis, but tests are colocated with source files or in relevant directories.

**Example:**
```typescript
// user-service.test.ts
import { getUser } from './user-service';

test('getUser returns correct user', () => {
  expect(getUser('123')).toEqual({ id: '123', name: 'Alice' });
});
```

## Commands

| Command              | Purpose                                                      |
|----------------------|--------------------------------------------------------------|
| /update-dependencies | Update one or more dependencies across the monorepo packages |
```
