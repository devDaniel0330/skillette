## Custom hooks

Extract reusable stateful logic into custom hooks when appropriate.

Custom hook names should begin with "use".

Example:

```jsx
function useToggle(initialValue = false) {
  const [value, setValue] = useState(initialValue);
  function toggle() {
    setValue((previous) => !previous);
  }
  return [value, toggle];
}
```
## React hooks

Follow React's rules of hooks.

### useState

Use for managing local component state.

### useEffect

Use for synchronizing components with external systems.

Examples include:
- Event subscriptions.
- Timers.
- Browser APIs.
- External connections.
- Data fetching when appropriate.

Guidelines:
- Include all reactive dependencies used by the effect.
- Clean up subscriptions and other external resources.
- Avoid using effects for values that can be calculated during rendering.
- Avoid unnecessary effects that cause repeated rendering.
- Do not use useEffect as a replacement for event handlers.

### useRef

Use useRef when a value needs to persist between renders without triggering a re-render.

Common applications:
- Accessing DOM elements.
- Managing timers.
- Storing mutable values.

### useMemo and useCallback

Use these hooks only when there is a meaningful performance or reference-stability benefit.

Do not use memoization everywhere by default.

## States

Use React state to manage data that changes over time.

Use useState for simple local state.

Example:

```jsx
import { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);
  function increment() {
    setCount((previousCount) => previousCount + 1);
  }

  return (
    <button onClick={increment}>
      Count: {count}
    </button>
  );
}
```

Guidelines:

- Never modify state directly.
- Use state setters to update state.
- Use functional updates when the new value depends on the previous value.
- Keep state as close as practical to the components that need it.
- Avoid duplicating data that can be calculated from existing state.
- Lift state up when multiple components need to share it.

Choose state management according to application complexity.

Use:
- useState for local component state.
- useReducer for more complex local state transitions.
- Context API for sharing suitable application-wide data.
- An established state management library when application requirements justify it.

Avoid introducing global state for data that only one component needs.

Do not duplicate server data unnecessarily between multiple state stores.