# Guidelines: TypeScript Best Practices

## Type System & Type Safety

- Use TypeScript for all code and enable strict mode.
- Ensure complete type safety throughout stores, hooks, and component interfaces.
- Prefer interfaces over types for object definitions; use types for unions, intersections, and mapped types.
- Entity interfaces should extend common patterns while maintaining their specific properties.
- Use TypeScript type guards in filtering operations for relationship safety.
- Avoid the 'any' type; prefer 'unknown' when necessary.
- Use generics to create reusable components and functions.
- Utilize TypeScript's features to enforce type safety.
- Use type-only imports (import type { MyType } from './types') when importing types, because verbatimModuleSyntax is enabled.
- Avoid enums; use maps instead.

## Naming Conventions

- Names should reveal intent and purpose.
- Use PascalCase for component names and types/interfaces.
- Prefix interfaces for React props with 'Props' (e.g., ButtonProps).
- Use camelCase for variables and functions.
- Use UPPER_CASE for constants.
- Use lowercase with dashes for directories, and PascalCase for files with components (e.g., components/auth-wizard/AuthForm.tsx).
- Use descriptive variable names with auxiliary verbs (e.g., isLoading, hasError).
- Favor named exports for components.

## Code Structure & Patterns

- Write concise, technical TypeScript code with accurate examples.
- Use functional and declarative programming patterns; avoid classes.
- Prefer iteration and modularization over code duplication.
- Use the "function" keyword for pure functions.
- Use curly braces for all conditionals for consistency and clarity.
- Structure files appropriately based on their purpose.
- Keep related code together and encapsulate implementation details.

## Performance & Error Handling

- Use immutable and efficient data structures and algorithms.
- Create custom error types for domain-specific errors.
- Use try-catch blocks with typed catch clauses.
- Handle Promise rejections and async errors properly.
- Log errors appropriately and handle edge cases gracefully.

## Project Organization

- Place shared types in a types directory.
- Use barrel exports (index.ts) for organizing exports.
- Structure files and directories based on their purpose.

## Other Rules

- Use comments to explain complex logic or non-obvious decisions.
- Follow the single responsibility principle: each function should do exactly one thing.
- Follow the DRY (Don't Repeat Yourself) principle.
- Do not implement placeholder functions, empty methods, or "just in case" logic. Code should serve the current specification's requirements only.
- Use 2 spaces for indentation (no tabs).