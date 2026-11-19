---
name: react-development
description: Build, modify, debug, review and maintain React applications. Use when creating React components, implementing UI functionality, managing states, working with hooks, integrating APIs, handling forms, configuring routing, organizing React projects or troubleshooting React errors.
---

# React development

## 1. Purpose

This skill provides development guidelines for building and maintaining React applications.

The goal is to produce applications that are:
- Maintainable and scalable.
- Component-based and reusable.
- Responsive and accessible.
- Efficient and performant.
- Consistent with modern React practices.

Follow the existing project's architecture and conventions whenever modifying an existing application.

## 2. General development practices

Follow these principles when developing React applications:
- Use functional components by default.
- Write reusable components when appropriate.
- Keep components focused on a single responsibility.
- Use meaningful component, variable and function names.
- Avoid unnecessary complexity and abstraction.
- Separate UI presentation from complex business logic where practical.
- Avoid unnecessary dependencies.
- Follow moder JavaScript or TypeScript conventions.
- Preserve existing functionality when modifying an application.
- Do not introduce libraries or architectural changes without a valid reason.

## 3. Before starting development

Before implementing changes, inspect the existing project.

Identify:
1. Project structure.
2. React and React DOM versions.
3. Build tool or framework being used.
4. Whether the project uses JavaScript or TypeScript.
5. Existing dependencies and libraries.
6. Existing component organization.
7. Current styling approach.
8. Existing routing and state management solutions.

Inspect relevant configuration files including:
- package.json
- vite.config.js or equivalent
- tsconfig.json if applicable
- Existing application entry points.

Do not assume every React project uses Vite.

For existing projects, follow their current architecture unless there is a clear reason to change it.

## 4. React fundamentals

### 4.1 Components

- Use functional components.
- Use PascalCase for component names.
- Keep components small and focused.
- Extract repeated UI elements into reusable components.
- Avoid unnecessarily large components containing related functionality.

Example:

```jsx
function WelcomeMessage({ name }) {
  return <h1>Welcome, {name}!</h1>;
}
export default WelcomeMessage;
```

### 4.2 JSX

Follow JSX conventions:

- Use className instead of class.
- use camelCase for JSX event attributes.
- Wrap JavaScript expressions in curly braces.
- Use parenthesis for multiline JSX when appropriate.
- Ensure elements are properly closed.
- Use meaningful keys when rendering lists.

Example:

```jsx
function UserList({ users }) {
  return (
    <ul>
      {users.map((user) => (
        <li key={user.id}>
          {user.name}
        </li>
      ))}
    </ul>
  );
}
```

Avoid using array indexes as keys when list items have stable identifiers.

### 4.3 Props

Use props to pass data and functions between components.

Guidelines:
- Pass only the information a component needs.
- Use descriptive prop names.
- Destructure props when it improves readability.
- Avoid modifying props.
- Use callback props to communicate events to parent components.

Example:

```jsx
function UserCard({ name, email }) {
  return (
    <div>
      <h3>{name}</h3>
      <p>{email}<p>
    </div>
  );
}
```

### 4.4 State

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

## 5. React hooks

Follow React's rules of hooks.

### 5.1 useState

Use for managing local component state.

### 5.2 useEffect

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

### 5.3 useRef

Use useRef when a value needs to persist between renders without triggering a re-render.

Common applications:
- Accessing DOM elements.
- Managing timers.
- Storing mutable values.

### 5.4 useMemo and useCallback

Use these hooks only when there is a meaningful performance or reference-stability benefit.

Do not use memoization everywhere by default.

### 5.5 Custom hooks

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

## 6. Component organization

Organize components according to their responsibilities.

Example structure:
```text
src/
│
├── components/
│   ├── Navbar.jsx
│   ├── Sidebar.jsx
│   └── Button.jsx
│
├── pages/
│   ├── Dashboard.jsx
│   ├── Login.jsx
│   └── Users.jsx
│
├── hooks/
│   └── useAuth.js
│
├── services/
│   └── api.js
│
├── assets/
│
├── styles/
│   └── global.css
│
├── App.jsx
└── main.jsx
```

This is a suggested structure, not a mandatory convention.

Guidelines:
- Group related components logically.
- Keep page-level components separate from reusable components.
- Store reusable hooks in an appropriate location.
- Separate API communication into service modules when useful.
- Avoid creating folders for components that do not need them.
- Adapt the structure as the project grows.

## 7. Styling and responsive design

Follow the styling approach alreayd established by the project.

Possible styling approaches include:
- Regular CSS.
- CSS modules.
- Tailwind CSS.
- Styled components.
- Other established styling libraries.

Guidelines:
- Maintain consistent spacing and typography.
- Use reusable styles where appropriate.
- Avoid excessive inline styling.
- Avoid unnecessary !important declarations.
- Support mobile, tablet and desktop layouts.
- Use Flexbox and CSS Grid appropriately.
- Maintain sufficient color contrast.
- Ensure interactive elements have clear hover, focus and disabled states.

Do not introduce a new styling framework without a valid reason.

## 8. Form and user input

When implementing forms:
- Use controlled components when appropriate.
- Maintain form state clearly.
- Validate user input.
- Display useful validation messages.
- Prevent duplicate submissions when necessary.
- Prevent loading and success states.
- Handle submission errors.
- Use appropriate HTML input types.

Example:

```jsx
import { useState } from 'react';

function LoginForm() {
  const [email, setEmail] = useState("");
  function handleSubmit(event) {
    event.preventDefault();
    console.log("Submitted:", email);
  }
  return (
    <form onSubmit={handleSubmit}>
      <label htmlFor="email">Email</label>
      <input id="email" type="email" value={email} onChange={(event) => setEmail(event.target.value)} required/>
      <button type="submit">Login</button>
    </form>
  );
}
```

## 9. API integration

When connecting React applications to backend services:
- Keep API communication organized.
- Use fetch or an established HTTP client.
- Handle loading, success and error states.
- Handle unsuccessful HTTP responses.
- Avoid duplicating API request logic.
- Keep sensitive credentials out of frontend source code.
- Do not assume frontend validation replaces backend validations.

Example:

```jsx
async function fetchUsers() {
  const response = await fetch("/api/users");

  if (!response.ok) {
    throw new Error("Failed to fetch users");
  }

  return response.json();
}
```

For more complex applications, organize API requests into service modules.

## 10. Routing

When an application requires multiple pages:
- Follow the existing routing solution.
- Use React Router or the routing system provided by the selected framework.
- Organize routes logically.
- Separate page components from reusable layout components.
- Handle invalid routes.
- Implement protected routes when authentication is required.

Do not introduce a routing library if the project already has an established routing solution.

## 11. State management

Choose state management according to application complexity.

Use:
- useState for local component state.
- useReducer for more complex local state transitions.
- Context API for sharing suitable application-wide data.
- An established state management library when application requirements justify it.

Avoid introducing global state for data that only one component needs.

Do not duplicate server data unnecessarily between multiple state stores.

## 12. Performance and optimization

Follow these practices:

- Avoid unnecessary component re-renders.
- Avoid unnecessary state updates.
- Use appropriate list keys.
- Split large components when beneficial.
- Lazy-load appropriate routes or components.
- Avoid unnecessary dependencies.
- Optimize images and other static assets.
- Use memoization only when beneficial.

Do not optimize prematurely. Prioritize readability and correctness.

## 13. Accessibility

Ensure the application is accessible.

- Use semantic HTML elements.
- Associate form labels with inputs.
- Provide meaningful alternative text for images.
- Ensure keyboard navigation works.
- Provide visible focus indicators.
- Use appropriate ARIA attributes when necessary.
- Do not rely solely on color to communicate information.

Prefer native HTML elements over custom interactive elements when possible.

## 14. Debugging and Error Handling

When debugging:

1. Understand the reported problem.
2. Inspect thre relevant components and files.
3. Reproduce or identify the cause of the error.
4. Check browser console errors.
5. Check network requests when API integration is involved.
6. Implement the smallest appropriate fix.
7. Verify that the fix does not break existing functionality.

Do not randomly change code without understanding the underlying problem.

## 15. Development workflow

Follow this workflow when implementing a React feature:

1. Understand the requirements.
2. Inspect the existing project.
3. Identify the affected components.
4. Determine the required state and data flow.
5. Plan the component structure.
6. Implement the functionality.
7. Apply styling and responsive behavior.
8. Handle loading, error and empty states where appropriate.
9. Test the implementation.
10. Explain the changes made.

For substantial changes, explain the proposed implementation before modifying the project.

## 16. Code modification rules

When working on existing React applications:

- Preserve the existing project structure.
- Modify only the necessary files.
- Do not remove unrelated functionality.
- Do not replace existing libraries without justification.
- Do not overwrite configuration files unnecessarily.
- Follow existing naming and formatting conventions.
- Explain any new dependencies.
- Identify any required environment or configuration changes.

When the user requests complete code, provide the complete relevant file rather than disconnected snippets.

## 17. Testing

When testing React applications:
- Test component rendering.
- Test user interactions.
- Test form validations.
- Test loading and error states.
- Test API integration where applicable.
- Test responsive layouts.
- Check for console errors.
- Verify important existing functionality after modifications.

Use the project's existing testing tools where available.

Do not claim the code has been tested unless it has actually been executed or verified.

## 18. Response guidelines

When providing React development assisstance:
- Identify teh relevant filename.
- Explain the purpose of important components.
- Explain how data flows between components when relevant.
- Provide complete code when requested.
- Explain required dependencies and installation commands.
- Include instructions for running and testing the application.
- Mention important assumptions and limitations.

Avoid unnecessary explanations for straightforward changes.

## 19. Final Quality Checklist

Before completing a development task, verify:

- [ ] Components have clear responsibilities.
- [ ] Props and state are used appropriately.
- [ ] Hooks follow the Rules of Hooks.
- [ ] State is not modified directly.
- [ ] Lists use appropriate keys.
- [ ] Event handlers are implemented correctly.
- [ ] API errors are handled appropriately.
- [ ] Forms validate user input.
- [ ] Styling is consistent and responsive.
- [ ] Accessibility has been considered.
- [ ] No unnecessary dependencies were introduced.
- [ ] Existing functionality has been preserved.
- [ ] The implementation has been tested where possible.