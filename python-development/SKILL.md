---
name: python-development
description: Develop, debug, review and maintain Python applications and scripts. Use when writing Python code, creating functions and classes, working with modules, processing files, automating tasks, handling errors, managing dependencies, designing Python projects or troubleshooting Python applications.
---

# Python development

## 1. Purpose

This skill provides development guidelines fro writing, maintaining, debugging and improving Python applications.

The goal is to produce Python code that is:
- Readable and maintainable.
- Efficient and reliable.
- Modular and reusable.
- Easy to test and debug.
- Consistent with modern Python practices.
- Appropriate for the project's requirements.

Adapt the implementation to the project's complexity and intended use.

## 2. General development principles

Follow these principles when developing Python applications:
- Follow Python's established coding conventions.
- Write clean, readable and maintainable code.
- Use meaningful variable, function and class names.
- Prefer simple solutions over unnecessary complexity.
- Avoid unnecesary dependencies.
- Use modular programming where appropriate.
- Avoid duplicated code.
- Keep functions focused on specific responsibilities.
- Handle errors appropriately.
- Preserve existing functionality when modifying projects.
- Add comments when they clarify complex logic.
- Do not introduce unnecessary abstractions.

Follow the principle of readability over cleverness.

## 3. Before starting development

Before implementing changes, inspect the existing project.

Identify:

1. Python version
2. Project structure
3. Existing dependencies
4. Entry-point files
5. Configuration files
6. Existing modules and packages
7. Database connections (if applicable)
8. Existing testing frameworks
9. Environment and execution requirements

Inspect relevant files such as:

- pyproject.toml
- requirements.txt
- setup.py
- setup.cfg
- .gitignore
- README.md

Not every project uses all these files.

For existing projects, follow the established architecture and conventions unless there is a clear reason to change them.

## 4. Python coding standards

### 4.1 Naming conventions

Follow standard Python naming conventions:
- Variables: snake_case
- Functions: snake_case
- Classes: PascalCase
- Constants: UPPER_SNAKE_CASE
- Modules: lowercase, preferably short names

Example:

```python
MAX_RETRY_COUNT = 3

def calculate_total(price, quantity):
    return price * quantity

class ShoppingCart:
    pass
```

Avoid unclear variable names such as x, temp or data when more descriptive names are appropriate.

### 4.2 Indentation and formatting

- Use four spaces for indentation.
- Avoid mixing tabs and spaces.
- Keep lines reasonably readable.
- Separate logical sections with blank lines.
- Use consistent formatting.
- Follow PEP 8 where applicable.

Use automated formatters when appropriate, such as Black or Ruff.

### 4.3 Comments and documentation

Write comments to explain why something is done when the reason is not obvious.

Use docstrings for public functions, classes and modules where appropriate.

Example:

```python
def calculate_discount(price, percentage):
    """Calculate the discounted price."""
    discount = price * (percentage / 100)
    return price - discount
```

Avoid comments that simply repeat what the code already expresses.

## 5. Variable and Data Types

Use appropriate Python data types:
- int for integers.
- float for floating point numbers.
- str for text.
- bool for Boolean values: true/false.
- list for ordered collections.
- tuple for fixed collections.
- dict for key-value data.
- set for unique elements.

Guidelines:
- Use descriptive variable names.
- Avoid unnecessary type conversions.
- Choose suitable data structures.
- Avoid mutable default arguments.
- Use constants for values that should remain unchanged.
- Consider type hints for improved readability and maintainability.

Example:

```python
def calculate_average(numbers: list[float]) -> float:
    if not numbers:
        return 0.0

    return sum(numbers) / len(numbers)
```

## 6. Functions

Use functions to organize reusable logic.

Guidelines:
- Keep functions focused on one responsibility.
- Use descriptive names.
- Pass required information through parameters.
- Return values instead of relying on unnecessary global variables.
- Avoid functions with too many parameters.
- Validate inputs when necessary.
- Document non-obvious behavior.

Example:

```python
def calculate_area(length: float, width: float) -> float:
    return length * width
```

Avoid repeating the same logic across multiple parts of an application.

## 7. Object-Oriented Programming

Use classes when they provide a meaningful organizational or modeling benefits.

Follow these principles:
- Encapsulate related data and behavior.
- Use inheritance only when there is a suitable relationship.
- Prefer composition when it provides simpler designs.
- Keep classes focused on clear responsibilities.
- Avoid unnecessarily deep inheritance structures.
- Use appropriate acces conventions.
- Implement special methods only when they provide useful behavior.

Example:

```python
class Student:
    def __init__(self, name: str, student_id: str):
        self.name = name
        self.student_id = student_id

    def display_details(self) -> str:
        return f"{self.name} ({self.student_id})"
```

Do not force object-oriented programming into projects where simple functions are sufficient.

## 8. Modules and project structure

Organize code into modules when a project grows beyond a simple script.

Suggested structure:

```text
my_project/
│
├── src/
│   └── my_project/
│       ├── __init__.py
│       ├── main.py
│       ├── config.py
│       ├── services/
│       │   └── user_service.py
│       └── utils/
│           └── helpers.py
│
├── tests/
│   └── test_main.py
│
├── .env.example
├── .gitignore
├── pyproject.toml
└── README.md
```

This is a suggested structure, not a mandatory convention.

Guidelines:
- Separate unrelated functionality into appropriate modules.
- Avoid putting all application logic into one file.
- Keep imports organized.
- Avoid circular imports.
- Use packages to group related modules.
- Keep configuration separate from business logic.
- Adapt the structure to the project's size.

For small scripts, a single Python file may be sufficient.

## 9. Error handling and exceptions

Handle errors explicitly and appropriately.

Guidelines:
- Use try and except when an error can reasonably be handled.
- Catch specific exceptions instead of using bare except.
- Use finally when cleanup must always occur.
- Raise meaningful exceptions when necessary.
- Avoid silently ignoring errors.
- Do not expose sensitive information in error messages.

Example:

```python
try:
    number = int(input("Enter a number: "))
except ValueError:
    print("Please enter a valid integer.")
```

Do not use exception handling as a replacement for proper input validation.

## 10. File Operations

When working with files:
- Prefer pathlib for filesystem path operations.
- Use context manager when opening files.
- Specify encoding when handling text files.
- Handle missing files and permission errors.
- Avoid hardcoding machine-specific absolute paths.
- Avoid overwriting important files unintentionally.

Example:

```python
from pathlib import Path

file_path = Path("data") / "records.txt"

with file_path.open("r", encoding="utf-8") as file:
    content = file.read()
```

For structured data, use appropriate libraries or standard modules.

Examples:
- json for JSON files.
- csv for CSV files.
- sqlite3 for SQLite databases.
- xml.etree.ElementTree for XML files.

## 11. Dependencies and environment management

Manage project dependencies appropriately

Guidelines:
- Use virtual environments for project isolation.
- Avoid installing unnecessary packages globally.
- Document project dependencies.
- Pin dependency versions when reproducibility requires it.
- Avoid unnecessary dependency upgrades.
- Use environment variables for configuration and secrets.

Example:

```bash
python -m venv .venv
```

Activate it on Windows:

```bash
.venv\Scripts\activate
```

Activate it on Linux or macOS:

```bash
source .venv/bin/activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

When appropriate, use modern project configuration through pyproject.toml.

Never hardcode password, API keys, or other sensitive credentials in source code.

## 12. External libraries and frameworks

Choose libraries based on the actual requirements.

Examples include:
- Requests or HTTPX for HTTP requests.
- Flask, Django or FastAPI for web development.
- Pandas and NumPy for data analysis.
- OpenPyXL fro Excel processing.
- python-docx for Word document processing.
- ReportLab for PDF generation.
- Selenium or Playwright for browser automation.

Guidelines:

- Check whether the standard library already provides the required functionality.
- Prefer established and maintained libraries.
- Avoid introducing large dependencies for simple tasks.
- Follow the library's official documentation.
- Explain installation requirements when introducing new dependencies.

Do not assume that every project requires an external library.

## 13. Database operations

When working with databases:
- Use appropriate database libraries.
- Use parameterized queries.
- Avoid constructing SQL statements directly from untrusted user input.
- Handle database errors appropriately.
- Close database connections and cursors when necessary.
- Use trasnsactions for related operations.
- Avoid unnecessarily duplicating database logic.
- Protect credentials and connection information.

Example using SQLite:

```python
import sqlite3

connection = sqlite3.connect("database.db")

try:
    cursor = connection.cursor()

    cursor.execute(
        "SELECT * FROM users WHERE user_id = ?",
        (user_id,)
    )

    users = cursor.fetchall()

finally:
    connection.close()
```

Adapt database practices to the database system and library being used.

## 14. Security Guidelines

Consider security when developing Python applications.

- Validate external input.
- Avoid executing untrusted code.
- Do not use eval or exec on untrusted input.
- Protect sensitive information.
- Avoid unsafe deserialization.
- Use secure authentication practices.
- Keep dependencies updated.
- Avoid exposing internal errors or credentials.
- Apply appropriate file permissions.
- Use secure communication when transmitting sensitive data.

Do not assume that input from files, APIs, or users is trustworthy.

## 15. Testing and Debugging

When testing Python applications:

- Test individual functions.
- Test important application workflows.
- Check normal and exceptional cases.
- Test boundary conditions.
- Verify expected outputs.
- Use automated tests when appropriate.
- Follow the existing project's testing framework.

Common testing tools include:

- pytest
- unittest
- unittest.mock

When debugging:

1. Understand the reported problem.
2. Inspect the relevant code.
3. Identify the underlying cause.
4. Implement the smallest appropriate fix.
5. Run relevant tests.
6. Check for regressions.
7. Explain the changes.

Do not randomly modify code without understanding the cause of the problem.

## 16. Performance and Optimization

Follow these principles:

- Choose appropriate data structures.
- Avoid unnecessary repeated operations.
- Avoid premature optimization.
- Use efficient algorithms where necessary.
- Consider memory usage when processing large datasets.
- Use generators when they are beneficial.
- Profile performance before optimizing complex bottlenecks.
- Prioritize correctness and maintainability.

Do not sacrifice code readability for insignificant performance improvements.

## 17. Development Workflow

Follow this workflow when implementing a Python project or feature:

1. Understand the requirements.
2. Inspect the existing project.
3. Identify the relevant modules and files.
4. Determine the required functionality.
5. Plan the implementation.
6. Write or modify the code.
7. Handle errors and edge cases.
8. Run the application or relevant tests.
9. Verify the expected behavior.
10. Explain the implementation and changes.

For substantial changes, explain the proposed approach before implementation.

## 18. Code Modification Rules

When working with existing Python projects:

- Preserve existing architecture where practical.
- Modify only necessary files.
- Do not remove unrelated functionality.
- Do not overwrite configuration files unnecessarily.
- Follow existing naming and formatting conventions.
- Explain new dependencies.
- Identify required environment changes.
- Maintain compatibility with the project's Python version.

When the user requests complete code, provide the complete relevant file rather than disconnected snippets.

## 19. Response Guidelines

When providing Python development assistance:

- Identify the filename.
- Explain the purpose of important functions and classes.
- Provide complete code when requested.
- Include required installation commands.
- Explain how to run the application.
- Include testing instructions.
- Mention relevant assumptions and limitations.

For beginner-level questions, explain concepts progressively and include practical examples.

Avoid unnecessary explanations for straightforward changes.

## 20. Final Quality Checklist

Before completing a development task, verify:

- [ ] Code follows Python conventions.
- [ ] Variable and function names are meaningful.
- [ ] Functions have clear responsibilities.
- [ ] Data structures are appropriate.
- [ ] Error handling is implemented where necessary.
- [ ] File operations are handled safely.
- [ ] Dependencies are documented.
- [ ] Sensitive information is protected.
- [ ] Database queries are parameterized where applicable.
- [ ] Existing functionality is preserved.
- [ ] Tests have been executed where possible.
- [ ] No unnecessary complexity has been introduced.
- [ ] Instructions for running the code are provided.