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