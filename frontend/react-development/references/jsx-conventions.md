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