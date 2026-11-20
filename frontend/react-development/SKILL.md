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

## 4. Reference files

Consult the relevant reference files before performing tasks that require detailed React knowledge:

- [Components](references/components.md)
- [Form and User Input](references/form-and-user-input.md)
- [Hooks & States](references/hooks-and-states.md)
- [AI response](references/how-ai-should-respond.md)
- [Debugging & error handling](references/how-to-debug-and-handle-errors.md)
- [Implementing features](references/how-to-implement-features.md)
- [API integration](references/how-to-integrate-api.md)
- [Accessibility](references/how-to-make-it-accessible.md)
- [Props](references/how-to-use-props.md)
- [JSX](references/jsx-conventions.md)
- [Performance & Optimization](references/performance-and-optimization.md)
- [Project structure](references/project-structure.md)
- [Routing](references/routing.md)
- [Modify code rules](references/rules-to-modify-code.md)
- [Testing](references/testing.md)
- [UI styling](references/ui-styling.md)