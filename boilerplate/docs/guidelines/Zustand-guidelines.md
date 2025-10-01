# Guidelines: Zustand Best Practices

## Core Principles

- **Implement a data layer** for this React application following this specification carefully and to the letter.
- **Complete separation of concerns**: All data operations should be accessible in UI components through simple and clean entity-specific hooks, ensuring state management logic is fully separated from UI logic.
- **Shared state architecture**: Different UI components should work with the same shared state, despite using entity-specific hooks separately.

## Technology Stack

- **State management**: Use Zustand for state management with automatic localStorage persistence via the `persist` middleware.

## Store Architecture

- **Base entity:** Implement a BaseEntity interface with common properties that all entities extend:
```typescript 
export interface BaseEntity { 
  id: string; 
  createdAt: string; // ISO 8601 format 
  updatedAt: string; // ISO 8601 format 
}
```
- **Entity-specific stores**: Create separate Zustand stores for each entity type.
- **Dictionary-based storage**: Use dictionary/map structures (`Record<string, Entity>`) rather than arrays for O(1) access by ID.
- **Handle relationships**: Implement cross-entity relationships (like cascade deletes) within the stores where appropriate.

## Hook Layer

The hook layer is the exclusive interface between UI components and the Zustand stores. It is designed to be simple, predictable, and follow a consistent pattern across all entities.

### Core Principles

1.  **One Hook Per Entity**: There will be a single, comprehensive custom hook for each entity (e.g., `useBlogPosts`, `useCategories`). This hook is the sole entry point for all data and operations related to that entity. Separate hooks for single-item access will not be created.
2.  **Return reactive data, not getter functions**: To prevent stale data, hooks must return the state itself, not a function that retrieves state. Parameterize hooks to accept filters and return the derived data directly. A component calling a getter function will not update when the underlying data changes.
3.  **Expose Dictionaries for O(1) Access**: To provide simple and direct access to data, every hook will return a dictionary (`Record<string, Entity>`) of the relevant items.

### The Standard Hook Pattern

Every entity hook will follow this implementation pattern:

1.  **Subscribe** to the entire dictionary of entities from the corresponding Zustand store. This ensures the hook is reactive to any change in the data.
2.  **Filter** the data based on the parameters passed into the hook. This logic will be memoized with `useMemo` for efficiency. If no parameters are provided, the hook will operate on the entire dataset.
3.  **Return a Consistent Shape**: The hook will always return an object containing:
    *   A **filtered and sorted array** (e.g., `blogPosts`) for rendering lists.
    *   A **filtered dictionary** (e.g., `blogPostsDict`) for convenient `O(1)` lookup within the component.
    *   All necessary **action functions** (`add`, `update`, `remove`) and **relationship operations**.
    *   All necessary **helper functions** and **derived data objects**. Helper functions are suitable for pure, stateless logic (e.g., calculators). Derived data objects are memoized values that provide aggregated or summarized information from the state (e.g., an object containing status counts). They must be derived directly from the reactive state to ensure they update automatically when the underlying data changes.

## API Design Standards

- **Object Parameters**: Use object parameters instead of multiple direct parameters for better extensibility:
```typescript

// ✅ Preferred

add({ title, categoryIds })

// ❌ Avoid

add(title, categoryIds)

```
- **Internal Methods**: Use underscore-prefixed methods for cross-store operations to maintain clean separation.

## State Validation Standards

- **Existence checks**: All `update` and `remove` operations should validate entity existence before proceeding.
- **Relationship validation**: Verify both entities exist before establishing relationships between them.

## Error Handling Patterns

- **Operation failures**: Define behavior when operations fail (e.g., updating non-existent entities).
- **Graceful degradation**: How to handle missing related entities in helper functions.

## Other Standards

- **Secure ID generation**: Use `crypto.randomUUID()` for entity ID generation instead of custom implementations for better uniqueness guarantees and security.
- **Return type consistency**: `add` operations return generated IDs for component workflows requiring immediate entity access, while `update` and `remove` operations return `void` to maintain clean modification APIs.


