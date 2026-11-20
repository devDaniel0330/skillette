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