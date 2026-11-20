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