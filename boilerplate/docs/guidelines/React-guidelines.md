# Guidelines: React Best Practices

## Component Structure

- Use functional components over class components
- Keep components small and focused
- Extract reusable logic into custom hooks
- Use composition over inheritance
- Implement proper prop types with TypeScript
- Structure React files: exported component, subcomponents, helpers, static content, types
- Use declarative TSX for React components
- Ensure that UI components use custom hooks for data fetching and operations rather than receive data via props, except for simplest components

## React Patterns

- Utilize useState and useEffect hooks for state and side effects
- Use React.memo for performance optimization when needed
- Utilize React.lazy and Suspense for code-splitting
- Implement error boundaries for robust error handling
- Keep styles close to components

## React Performance

- Avoid unnecessary re-renders
- Lazy load components and images when possible
- Implement efficient state management
- Optimize rendering strategies
- Optimize network requests
- Employ memoization techniques (e.g., React.memo, useMemo, useCallback)

## React Project Structure

```

/src
- /components - UI components (every component in a separate file)
- /hooks - public-facing custom hooks (every hook in a separate file)
- /providers - React context providers (every provider in a separate file)
- /pages - page components (every page in a separate file)
- /stores - entity-specific Zustand stores (every store in a separate file)
- /styles - global styles (if needed)
- /types - shared TypeScript types and interfaces

```

## Framework Compatibility

### Ant Design v5 with React 19+

When using Ant Design v5 in a project with React 19 or newer, a patch is required to ensure compatibility, as React 19 removed some legacy APIs that `antd` relies on.

**1. Install the patch package:**
```bash
npm install @ant-design/v5-patch-for-react-19 --save
```

**2. Apply the patch:**
In your main entry file (e.g., `src/main.tsx`), import the patch module directly after importing the Ant Design styles. This will automatically apply the necessary patch.

```tsx
import React from 'react';
import ReactDOM from 'react-dom/client';
import App from './App';
import 'antd/dist/reset.css';
import '@ant-design/v5-patch-for-react-19'; // Applies the patch

ReactDOM.createRoot(document.getElementById('root')!).render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);
```
This will polyfill the missing APIs and prevent compatibility warnings and errors.