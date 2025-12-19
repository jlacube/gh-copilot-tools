# GitHub Copilot Coding Standards

This document provides comprehensive coding standards and best practices for major programming languages. These guidelines help GitHub Copilot generate code that follows industry-standard conventions and idiomatic patterns.

## Purpose

This guide serves as context for GitHub Copilot to:
- Generate code following language-specific conventions
- Apply consistent naming and formatting patterns
- Use idiomatic constructs and best practices
- Produce maintainable, readable, and secure code

## General Principles

### Code Readability
- **Optimize for readers, not writers** - Code is read far more often than it's written
- **Clarity over cleverness** - Prefer obvious solutions over obscure optimizations
- **Meaningful names** - Use descriptive identifiers that convey intent
- **Consistent style** - Follow project conventions consistently

### Naming Guidelines
- **Descriptive names** - Name things based on their purpose, not implementation
- **Scope-appropriate length** - Shorter names for narrow scopes, descriptive names for broader scopes
- **Avoid abbreviations** - Use full words unless abbreviation is universally known
- **Context matters** - Names should be clear without requiring extensive context

### Code Organization
- **Single Responsibility** - Each function/class should have one clear purpose
- **Keep it simple** - Avoid unnecessary complexity
- **DRY principle** - Don't Repeat Yourself, but don't over-abstract
- **Small functions** - Break large functions into focused, testable units

### Security
- **Input validation** - Always validate and sanitize external input
- **Secure defaults** - Choose secure options by default
- **Least privilege** - Grant minimum necessary permissions
- **Error handling** - Don't expose sensitive information in error messages

### Performance
- **Profile before optimizing** - Measure before making performance-related changes
- **Readable first** - Write clear code first, optimize only when needed
- **Algorithm choice** - Choose appropriate data structures and algorithms

## Language-Specific Guidelines

---

## Python

### Style Guide
Follow PEP 8 (Python Enhancement Proposal 8) and The Hitchhiker's Guide to Python recommendations.

### Naming Conventions
```python
# Functions and variables: snake_case
def calculate_total(item_count, price_per_item):
    total_amount = item_count * price_per_item
    return total_amount

# Classes: PascalCase
class UserAccount:
    pass

# Constants: UPPER_SNAKE_CASE
MAX_CONNECTIONS = 100
DEFAULT_TIMEOUT = 30

# Private members: leading underscore
class MyClass:
    def __init__(self):
        self._internal_state = None
```

### Formatting
- **Indentation**: 4 spaces (no tabs)
- **Line length**: 79 characters for code, 72 for docstrings/comments
- **Blank lines**: 2 before top-level functions/classes, 1 between methods
- **Imports**: Standard library, third-party, local (in that order, separated by blank lines)

### Best Practices
```python
# Use type hints (PEP 484/526)
def greet(name: str) -> str:
    return f"Hello, {name}!"

# Prefer list comprehensions for simple transformations
squares = [x**2 for x in range(10)]

# Use context managers for resource management
with open('file.txt', 'r') as f:
    content = f.read()

# Explicit is better than implicit (Zen of Python)
if len(items) > 0:  # Prefer over: if items:  (when checking actual length)
    process(items)

# Use enumerate for index + value
for index, value in enumerate(my_list):
    print(f"{index}: {value}")

# Use f-strings for formatting (Python 3.6+)
message = f"User {username} logged in at {timestamp}"
```

### Docstrings
```python
def calculate_distance(x1: float, y1: float, x2: float, y2: float) -> float:
    """
    Calculate the Euclidean distance between two points.
    
    Args:
        x1: X-coordinate of first point
        y1: Y-coordinate of first point
        x2: X-coordinate of second point
        y2: Y-coordinate of second point
    
    Returns:
        The distance between the two points as a float.
    
    Example:
        >>> calculate_distance(0, 0, 3, 4)
        5.0
    """
    return ((x2 - x1)**2 + (y2 - y1)**2)**0.5
```

---

## JavaScript / TypeScript

### Style Guide
Follow Airbnb JavaScript Style Guide and TypeScript best practices.

### Naming Conventions
```javascript
// Variables and functions: camelCase
const userName = 'John';
function calculateTotal(items) { }

// Classes and interfaces: PascalCase
class UserAccount { }
interface IUser { }

// Constants: UPPER_SNAKE_CASE or camelCase
const MAX_RETRIES = 3;
const apiEndpoint = 'https://api.example.com';  // Also acceptable

// Private fields: # prefix (ES2022+) or _ prefix (convention)
class MyClass {
    #privateField;
    _conventionalPrivate;
}
```

### TypeScript Specific
```typescript
// Use strict types, avoid 'any'
function processData(data: string[]): number {
    return data.length;
}

// Interface for object shapes
interface User {
    id: number;
    name: string;
    email?: string;  // Optional property
}

// Type unions for flexibility
type Status = 'pending' | 'success' | 'error';

// Generics for reusable code
function first<T>(arr: T[]): T | undefined {
    return arr[0];
}
```

### Formatting
- **Indentation**: 2 spaces (configurable, but 2 is most common)
- **Semicolons**: Required (Airbnb style)
- **Quotes**: Single quotes for strings, backticks for template literals
- **Trailing commas**: Yes (in multi-line)

### Best Practices
```javascript
// Use const/let, never var
const permanent = 'value';
let changeable = 0;

// Arrow functions for callbacks
items.map(item => item.value);

// Destructuring for cleaner code
const { name, age } = user;
const [first, second] = array;

// Template literals for string interpolation
const message = `Hello, ${name}!`;

// Spread operator for copying/merging
const newArray = [...oldArray, newItem];
const merged = { ...defaults, ...options };

// Optional chaining and nullish coalescing
const value = obj?.deeply?.nested?.property ?? 'default';

// Async/await over raw promises
async function fetchData() {
    try {
        const response = await fetch(url);
        const data = await response.json();
        return data;
    } catch (error) {
        console.error('Fetch failed:', error);
    }
}

// Use Array methods (map, filter, reduce)
const doubled = numbers.map(n => n * 2);
const evens = numbers.filter(n => n % 2 === 0);
```

---

## Conclusion

These coding standards provide GitHub Copilot with comprehensive context for generating high-quality, idiomatic code. Key takeaways:

### Universal Best Practices
- **Readability first**: Write code that others can understand
- **Consistency**: Follow project conventions and language idioms
- **Type safety**: Use strong typing features available in each language
- **Error handling**: Handle errors explicitly and safely
- **Documentation**: Document public APIs and complex logic

### Tool Integration
Enhance Copilot's effectiveness by combining it with:
- **Linters**: ESLint, Pylint
- **Formatters**: Prettier, Black
- **Type checkers**: TypeScript, mypy
- **Static analysis**: SonarQube, CodeQL, language-specific analyzers

### Continuous Learning
- Stay updated with language evolution and new features
- Review generated code for correctness and idiomaticity
- Provide feedback to improve Copilot suggestions
- Share knowledge with your team

### Remember
While these guidelines help Copilot generate better code, always review and test the generated code. Copilot is a tool to assist development, not replace developer judgment and expertise.
