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

## Java

### Style Guide
Follow Google Java Style Guide.

### Naming Conventions
```java
// Classes and interfaces: UpperCamelCase
public class UserAccount { }
public interface DataProcessor { }

// Methods and variables: lowerCamelCase
public void calculateTotal(int itemCount) {
    int totalAmount = itemCount * PRICE_PER_ITEM;
}

// Constants: UPPER_SNAKE_CASE
public static final int MAX_CONNECTIONS = 100;
public static final String DEFAULT_NAME = "Unknown";

// Package names: lowercase
package com.example.project.util;
```

### Formatting
- **Indentation**: 2 spaces (Google style)
- **Line length**: 100 characters
- **Braces**: K&R style (opening brace on same line)
- **Column limit**: Wrap at 100 characters

### Best Practices
```java
// Use Java 8+ features
List<String> filtered = list.stream()
    .filter(s -> s.length() > 5)
    .collect(Collectors.toList());

// Try-with-resources for AutoCloseable
try (BufferedReader reader = new BufferedReader(new FileReader(file))) {
    return reader.readLine();
}

// Use Optional to avoid null
public Optional<User> findUser(int id) {
    return Optional.ofNullable(userMap.get(id));
}

// Immutable collections when possible
List<String> immutable = List.of("a", "b", "c");

// Builder pattern for complex objects
User user = User.builder()
    .name("John")
    .email("john@example.com")
    .build();
```

### Javadoc
```java
/**
 * Calculates the total price for a given quantity.
 *
 * @param quantity the number of items to calculate for
 * @param pricePerItem the price of a single item
 * @return the total price
 * @throws IllegalArgumentException if quantity is negative
 */
public double calculateTotal(int quantity, double pricePerItem) {
    if (quantity < 0) {
        throw new IllegalArgumentException("Quantity cannot be negative");
    }
    return quantity * pricePerItem;
}
```

---

## C# (C-Sharp)

### Style Guide
Follow Microsoft C# Coding Conventions.

### Naming Conventions
```csharp
// Classes, methods, properties: PascalCase
public class UserAccount
{
    public string UserName { get; set; }
    
    public void CalculateTotal()
    {
        // Method implementation
    }
}

// Local variables and parameters: camelCase
public void ProcessData(int itemCount)
{
    string userName = "John";
    var totalAmount = itemCount * 10;
}

// Private fields: _camelCase (with underscore prefix)
private readonly string _connectionString;
private int _itemCount;

// Constants: PascalCase
public const int MaxRetries = 3;
private const string DefaultName = "Unknown";

// Interfaces: I prefix + PascalCase
public interface IUserRepository { }
```

### Formatting
- **Indentation**: 4 spaces
- **Braces**: Allman style (opening brace on new line)
- **Line length**: No strict limit, but keep reasonable (120-140 chars)

### Best Practices
```csharp
// Use modern C# features (C# 12)
// File-scoped namespaces
namespace MyApp.Services;

// Record types for immutable data
public record User(string Name, string Email);

// Collection expressions (C# 12)
int[] numbers = [1, 2, 3, 4, 5];

// Pattern matching
string result = value switch
{
    0 => "zero",
    > 0 and < 10 => "small",
    _ => "large"
};

// Nullable reference types
string? nullableString = null;
string nonNullable = nullableString ?? "default";

// LINQ queries
var filtered = users
    .Where(u => u.Age > 18)
    .OrderBy(u => u.Name)
    .Select(u => u.Email);

// Async/await
public async Task<string> FetchDataAsync()
{
    using var client = new HttpClient();
    return await client.GetStringAsync(url);
}

// String interpolation
var message = $"Hello, {user.Name}! You have {count} items.";

// Using declarations (automatic disposal)
using var stream = File.OpenRead("file.txt");
```

### XML Documentation
```csharp
/// <summary>
/// Calculates the total price for the given items.
/// </summary>
/// <param name="items">The list of items to calculate.</param>
/// <returns>The total price as a decimal.</returns>
/// <exception cref="ArgumentNullException">
/// Thrown when items is null.
/// </exception>
public decimal CalculateTotal(List<Item> items)
{
    if (items == null)
        throw new ArgumentNullException(nameof(items));
    
    return items.Sum(item => item.Price);
}
```

---

## Go

### Style Guide
Follow Effective Go (official Go documentation) and use `gofmt` for automatic formatting.

### Naming Conventions
```go
// Exported (public): Start with uppercase
type UserAccount struct {
    Name string
    Age  int
}

func CalculateTotal(items []Item) int {
    // Function implementation
}

// Unexported (private): Start with lowercase
type internalState struct {
    value int
}

func processData(data string) {
    // Function implementation
}

// Constants: MixedCaps (no underscores)
const MaxConnections = 100
const defaultTimeout = 30

// Interfaces: -er suffix when possible
type Reader interface {
    Read(p []byte) (n int, err error)
}

type Writer interface {
    Write(p []byte) (n int, err error)
}

// Package names: lowercase, single word
package httputil
package stringutil
```

### Formatting
- **Indentation**: Tabs (gofmt default)
- **Line length**: No strict limit, but wrap long lines sensibly
- **Braces**: K&R style (opening brace on same line)
- **Automatic**: Use `gofmt` to format all code

### Best Practices
```go
// Error handling - explicit error returns
func ReadFile(filename string) ([]byte, error) {
    data, err := os.ReadFile(filename)
    if err != nil {
        return nil, fmt.Errorf("reading %s: %w", filename, err)
    }
    return data, nil
}

// Defer for cleanup
func ProcessFile(filename string) error {
    f, err := os.Open(filename)
    if err != nil {
        return err
    }
    defer f.Close()  // Always closes, even on error
    
    // Process file
    return nil
}

// Multiple return values
func Divide(a, b float64) (float64, error) {
    if b == 0 {
        return 0, errors.New("division by zero")
    }
    return a / b, nil
}

// Goroutines for concurrency
go func() {
    // Run in separate goroutine
    processData(data)
}()

// Channels for communication
ch := make(chan int, 10)  // Buffered channel
go func() {
    ch <- 42
}()
value := <-ch

// Context for cancellation and timeouts
ctx, cancel := context.WithTimeout(context.Background(), 5*time.Second)
defer cancel()

// Short variable names in limited scope
for i := 0; i < len(items); i++ {
    // 'i' is clear in this context
}

// Use package name for context
import "encoding/json"
data, err := json.Marshal(obj)  // Not jsonlib.Marshal
```

### Comments
```go
// Package documentation appears before package clause
// Package httputil provides HTTP utility functions for common tasks.
package httputil

// Exported function/type comments start with the name
// CalculateTotal computes the sum of all item prices.
func CalculateTotal(items []Item) int {
    total := 0
    for _, item := range items {
        total += item.Price
    }
    return total
}
```

---

## Rust

### Style Guide
Follow the Rust Style Guide and use `rustfmt` for automatic formatting.

### Naming Conventions
```rust
// Types, traits: UpperCamelCase
struct UserAccount {
    name: String,
    age: u32,
}

trait DataProcessor {
    fn process(&self, data: &str) -> Result<String, Error>;
}

// Functions, variables, modules: snake_case
fn calculate_total(item_count: i32) -> i32 {
    let price_per_item = 10;
    item_count * price_per_item
}

// Constants: SCREAMING_SNAKE_CASE
const MAX_CONNECTIONS: usize = 100;
static DEFAULT_NAME: &str = "Unknown";

// Lifetimes: short, lowercase
fn longest<'a>(x: &'a str, y: &'a str) -> &'a str {
    if x.len() > y.len() { x } else { y }
}
```

### Formatting
- **Indentation**: 4 spaces (no tabs)
- **Line length**: 100 characters
- **Trailing commas**: Use in multi-line contexts
- **Automatic**: Use `rustfmt` to format all code

### Best Practices
```rust
// Ownership and borrowing
fn process_data(data: String) {  // Takes ownership
    println!("{}", data);
}  // data dropped here

fn read_data(data: &String) {  // Borrows immutably
    println!("{}", data);
}  // data still valid after

fn modify_data(data: &mut String) {  // Borrows mutably
    data.push_str(" modified");
}

// Error handling with Result
fn read_file(path: &str) -> Result<String, std::io::Error> {
    std::fs::read_to_string(path)
}

// Match for exhaustive handling
match result {
    Ok(value) => println!("Success: {}", value),
    Err(e) => eprintln!("Error: {}", e),
}

// ? operator for error propagation
fn process() -> Result<(), Error> {
    let data = read_file("config.txt")?;
    let parsed = parse_data(&data)?;
    save_result(parsed)?;
    Ok(())
}

// Option for nullable values
fn find_user(id: i32) -> Option<User> {
    if id > 0 {
        Some(User::new(id))
    } else {
        None
    }
}

// Iterators over loops
let doubled: Vec<i32> = numbers.iter()
    .map(|x| x * 2)
    .collect();

// Pattern matching and destructuring
let (x, y) = point;
if let Some(value) = optional {
    println!("{}", value);
}

// Trait bounds for generic functions
fn print_all<T: Display>(items: &[T]) {
    for item in items {
        println!("{}", item);
    }
}
```

### Documentation
```rust
/// Calculates the total price for the given items.
///
/// # Arguments
///
/// * `items` - A slice of items to calculate the total for
///
/// # Examples
///
/// ```
/// let items = vec![Item::new(10), Item::new(20)];
/// let total = calculate_total(&items);
/// assert_eq!(total, 30);
/// ```
///
/// # Panics
///
/// Panics if the total overflows i32.
pub fn calculate_total(items: &[Item]) -> i32 {
    items.iter().map(|item| item.price).sum()
}
```

---

## Ruby

### Style Guide
Follow the Ruby Style Guide (community standard).

### Naming Conventions
```ruby
# Methods and variables: snake_case
def calculate_total(item_count)
  price_per_item = 10
  item_count * price_per_item
end

user_name = "John"

# Classes and modules: UpperCamelCase
class UserAccount
end

module DataProcessor
end

# Constants: SCREAMING_SNAKE_CASE
MAX_CONNECTIONS = 100
DEFAULT_TIMEOUT = 30

# Predicate methods: end with ?
def empty?
  @items.empty?
end

# Dangerous methods: end with !
def save!
  # Raises exception on failure
end

# Instance variables: @snake_case
class MyClass
  def initialize
    @internal_state = nil
  end
end
```

### Formatting
- **Indentation**: 2 spaces (no tabs)
- **Line length**: 80 characters (max 120 for teams)
- **String quotes**: Single quotes for literals, double for interpolation
- **Blocks**: `{...}` for single-line, `do...end` for multi-line

### Best Practices
```ruby
# Use symbols for hash keys
user = { name: 'John', age: 30 }

# Blocks over loops
items.each do |item|
  process(item)
end

# Prefer map, select, reject over loops
doubled = numbers.map { |n| n * 2 }
evens = numbers.select { |n| n.even? }

# Use &: for simple transformations
names = users.map(&:name)

# String interpolation
message = "Hello, #{user.name}!"

# Trailing if/unless for simple conditions
return unless valid?
process_data if ready?

# Use attr_reader, attr_accessor, attr_writer
class User
  attr_reader :name
  attr_accessor :age
  attr_writer :email
end

# Prefer unless over negated if
unless error?
  proceed
end

# Duck typing over type checking
# Good: Just call the method
def process(processor)
  processor.process_data
end

# Safe navigation operator
user&.profile&.name

# Heredoc for multi-line strings
sql = <<~SQL
  SELECT * FROM users
  WHERE active = true
  ORDER BY created_at DESC
SQL
```

### Documentation
```ruby
# Method documentation with YARD
##
# Calculates the total price for given items.
#
# @param items [Array<Item>] the items to calculate total for
# @param discount [Float] optional discount percentage (0.0-1.0)
# @return [Float] the total price after discount
# @raise [ArgumentError] if discount is outside valid range
#
# @example
#   items = [Item.new(10), Item.new(20)]
#   total = calculate_total(items, 0.1)
#   #=> 27.0
def calculate_total(items, discount = 0.0)
  raise ArgumentError, 'Invalid discount' unless (0.0..1.0).cover?(discount)
  
  subtotal = items.sum(&:price)
  subtotal * (1.0 - discount)
end
```

---

## PHP

### Style Guide
Follow PSR-12 (Extended Coding Style Guide).

### Naming Conventions
```php
<?php

// Classes: PascalCase (StudlyCaps)
class UserAccount
{
    // Properties: camelCase
    private string $userName;
    protected int $itemCount;
    
    // Methods: camelCase
    public function calculateTotal(int $quantity): float
    {
        return $quantity * 10.0;
    }
}

// Functions: camelCase
function processData(string $input): array
{
    return explode(',', $input);
}

// Constants: UPPER_SNAKE_CASE
const MAX_CONNECTIONS = 100;
define('DEFAULT_TIMEOUT', 30);

// Interfaces: PascalCase with Interface suffix (optional)
interface DataProcessorInterface
{
    public function process(string $data): string;
}
```

### Formatting
- **Indentation**: 4 spaces (no tabs)
- **Line length**: 120 characters soft limit (80 preferred)
- **Braces**: Opening brace on own line for classes, same line for methods
- **Line ending**: Unix LF only

### Best Practices
```php
<?php

// Declare strict types
declare(strict_types=1);

namespace App\Services;

use App\Models\User;
use Exception;

// Type declarations for parameters and returns
function calculateTotal(int $count, float $price): float
{
    return $count * $price;
}

// Visibility keywords required on all properties/methods
class UserService
{
    private UserRepository $repository;
    
    public function __construct(UserRepository $repository)
    {
        $this->repository = $repository;
    }
    
    public function findUser(int $id): ?User
    {
        return $this->repository->find($id);
    }
}

// Nullable types with ?Type syntax
function processUser(?User $user): string
{
    return $user?->getName() ?? 'Guest';
}

// Union types (PHP 8.0+)
function process(int|float $number): string
{
    return (string) $number;
}

// Named arguments (PHP 8.0+)
createUser(
    name: 'John',
    email: 'john@example.com',
    age: 30
);

// Match expression (PHP 8.0+)
$result = match ($status) {
    'pending' => 'Processing',
    'success' => 'Complete',
    'error' => 'Failed',
    default => 'Unknown',
};

// Array destructuring
[$first, $second] = $array;
['name' => $name, 'age' => $age] = $user;
```

### Documentation
```php
<?php

/**
 * Calculates the total price for the given items.
 *
 * @param array<Item> $items The items to calculate total for
 * @param float $discount The discount percentage (0.0-1.0)
 * @return float The total price after discount
 * @throws InvalidArgumentException If discount is invalid
 *
 * @example
 * $items = [new Item(10), new Item(20)];
 * $total = calculateTotal($items, 0.1);
 * // Returns 27.0
 */
function calculateTotal(array $items, float $discount = 0.0): float
{
    if ($discount < 0.0 || $discount > 1.0) {
        throw new InvalidArgumentException('Discount must be between 0 and 1');
    }
    
    $subtotal = array_sum(array_map(fn($item) => $item->getPrice(), $items));
    return $subtotal * (1.0 - $discount);
}
```

---

## Swift

### Style Guide
Follow Swift API Design Guidelines (official Apple/Swift.org documentation).

### Naming Conventions
```swift
// Types: UpperCamelCase
struct UserAccount {
    var name: String
    var age: Int
}

class DataProcessor {
    func process(_ data: String) -> Bool {
        return true
    }
}

// Functions, variables, properties: lowerCamelCase
func calculateTotal(itemCount: Int) -> Int {
    let pricePerItem = 10
    return itemCount * pricePerItem
}

var userName = "John"
let maxConnections = 100

// Protocols: UpperCamelCase, often with -able, -ible suffix
protocol Drawable {
    func draw()
}

protocol ProgressReporting {
    var progress: Double { get }
}

// Enums and cases: UpperCamelCase for enum, lowerCamelCase for cases
enum CompassDirection {
    case north
    case south
    case east
    case west
}

// Boolean properties/methods: Read as assertions
var isEmpty: Bool
func isValid() -> Bool
```

### Formatting
- **Indentation**: 4 spaces (no tabs)
- **Line length**: No strict limit, keep readable
- **Braces**: Opening brace on same line

### Best Practices
```swift
// Clarity at point of use
extension List {
    public mutating func remove(at position: Index) -> Element
}
employees.remove(at: x)  // Clear what 'x' represents

// Mutating/non-mutating pairs
x.sort()              // Mutates in place
let y = x.sorted()    // Returns new sorted array

x.reverse()
let y = x.reversed()

// Use verb phrases for side-effects
x.addSubview(y)
x.dismiss(animated: false)

// Use noun phrases for non-mutating
let distance = x.distance(to: y)
let successor = i.successor()

// Omit needless words
// Bad: allViews.removeElement(cancelButton)
// Good:
allViews.remove(cancelButton)

// Factory methods start with 'make'
x.makeIterator()

// First argument forms grammatical phrase
view.addSubview(button)
let color = Color(red: 0.5, green: 0.2, blue: 0.8)

// Use default parameter values
func compare(
    _ other: String,
    options: CompareOptions = [],
    range: Range? = nil
) -> Ordering

// Guard for early exit
guard let user = getUser() else {
    return
}
// Use user here

// Prefer value types (structs) over reference types (classes)
struct Point {
    var x: Double
    var y: Double
}

// Protocol-oriented programming
protocol Flyable {
    func fly()
}

extension Bird: Flyable {
    func fly() {
        print("Flying")
    }
}

// Optionals for absence of value
var optionalName: String?
if let name = optionalName {
    print("Hello, \(name)")
}

// Trailing closures
items.map { $0 * 2 }
UIView.animate(withDuration: 0.3) {
    view.alpha = 0
}
```

### Documentation
```swift
/// Returns a "view" of `self` containing the same elements in reverse order.
///
/// - Complexity: O(1)
func reversed() -> ReversedCollection

/// Inserts `newElement` at position `i`.
///
/// - Parameter newElement: The element to insert
/// - Parameter i: The position at which to insert the element
/// - Precondition: `i <= count`
/// - Complexity: O(*n*) where *n* is the length of the collection
mutating func insert(_ newElement: Element, at i: Index)

/// Writes the textual representation of each element to output.
///
/// The representation for each item `x` is generated by `String(x)`.
///
/// - Parameters:
///   - items: The items to print
///   - separator: Text printed between items. Default is a space.
///   - terminator: Text printed at the end. Default is newline.
///
/// - Note: To print without a trailing newline, pass `terminator: ""`
func print(_ items: Any..., separator: String = " ", terminator: String = "\n")
```

---

## Kotlin

### Style Guide
Follow Kotlin Coding Conventions (official JetBrains/Kotlin documentation).

### Naming Conventions
```kotlin
// Classes and objects: UpperCamelCase
class UserAccount {
    val name: String = ""
}

object DatabaseConfig {
    const val MAX_CONNECTIONS = 100
}

// Functions and properties: lowerCamelCase
fun calculateTotal(itemCount: Int): Int {
    val pricePerItem = 10
    return itemCount * pricePerItem
}

var userName = "John"

// Constants: UPPER_SNAKE_CASE (screaming snake case)
const val MAX_RETRIES = 3
const val DEFAULT_TIMEOUT = 30

// Backing properties: prefix with underscore
class MyClass {
    private val _elementList = mutableListOf<Element>()
    
    val elementList: List<Element>
        get() = _elementList
}

// Package names: lowercase (no underscores)
package com.example.project
package org.company.application
```

### Formatting
- **Indentation**: 4 spaces (no tabs)
- **Braces**: Opening brace at end of line
- **Line length**: No hard limit, keep readable
- **Trailing commas**: Encouraged in multi-line declarations

### Best Practices
```kotlin
// Prefer immutability
val immutableValue = 10  // Use val
var mutableValue = 20    // Use var only when necessary

// Prefer immutable collections
val list = listOf("a", "b", "c")  // Immutable
val mutableList = mutableListOf("a", "b")  // Mutable

// Use data classes for data holders
data class User(val name: String, val age: Int)

// Expression body functions
fun double(x: Int): Int = x * 2

// When expression instead of if-else chains
when (x) {
    0 -> "zero"
    in 1..10 -> "small"
    else -> "large"
}

// Smart casts after type checking
if (obj is String) {
    print(obj.length)  // obj automatically cast to String
}

// Null safety with safe calls and Elvis operator
val length = str?.length ?: 0

// Extension functions
fun String.removeWhitespace(): String {
    return this.replace(" ", "")
}

// Scope functions
val result = user?.let {
    processUser(it)
    it.name
}

// Apply for configuration
val user = User("John", 30).apply {
    email = "john@example.com"
    verified = true
}

// Lambda with receivers
buildString {
    append("Hello")
    append(" World")
}

// Destructuring declarations
val (name, age) = user
val (_, second, third) = list  // Use _ for unused values

// Trailing lambda syntax
items.map { it * 2 }
    .filter { it > 10 }

// Named arguments for clarity
createUser(
    name = "John",
    age = 30,
    email = "john@example.com"
)

// Default parameter values
fun connect(
    host: String = "localhost",
    port: Int = 8080,
    timeout: Int = 3000
) { }

// Use ranges
for (i in 0..<10) {  // 0 to 9
    println(i)
}

if (age in 18..65) {
    println("Adult")
}
```

### Documentation
```kotlin
/**
 * Calculates the total price for the given items.
 *
 * @param items the list of items to calculate
 * @param discount optional discount factor between 0.0 and 1.0
 * @return the total price after applying discount
 * @throws IllegalArgumentException if discount is invalid
 *
 * @sample samples.calculateTotalExample
 */
fun calculateTotal(items: List<Item>, discount: Double = 0.0): Double {
    require(discount in 0.0..1.0) { "Discount must be between 0 and 1" }
    
    val subtotal = items.sumOf { it.price }
    return subtotal * (1.0 - discount)
}
```

---

## C++

### Style Guide
Follow Google C++ Style Guide (targeting C++20).

### Naming Conventions
```cpp
// Classes, structs, type aliases: UpperCamelCase
class UserAccount {
public:
    UserAccount();
    ~UserAccount();
};

struct DataPoint {
    int x;
    int y;
};

using IntMap = std::unordered_map<int, int>;

// Functions: UpperCamelCase (Google style)
void CalculateTotal(int itemCount) {
    int totalAmount = itemCount * kPricePerItem;
}

// Variables: snake_case
int item_count = 10;
std::string user_name = "John";

// Constants: kConstantName (k prefix + UpperCamelCase)
const int kMaxConnections = 100;
constexpr double kPi = 3.14159;

// Class data members: trailing underscore
class MyClass {
private:
    int member_variable_;
    std::string name_;
};

// Namespaces: snake_case
namespace my_project {
namespace internal {
}  // namespace internal
}  // namespace my_project

// Macros: UPPER_SNAKE_CASE with project prefix
#define MYPROJECT_ASSERT(condition) ...
```

### Formatting
- **Indentation**: 2 spaces (no tabs)
- **Line length**: 80 characters maximum
- **Braces**: Opening brace on same line (K&R style)
- **Pointer/reference**: No space after * or &

### Best Practices
```cpp
// Use auto for type deduction when it improves clarity
auto widget = std::make_unique<Widget>(args);
auto it = my_map.find(key);

// Use const liberally
const int kValue = 42;
void ProcessData(const std::string& data);  // const reference

// Smart pointers for ownership
std::unique_ptr<Foo> CreateFoo();  // Exclusive ownership
std::shared_ptr<const Bar> GetBar();  // Shared ownership

// Prefer nullptr over NULL or 0
int* ptr = nullptr;

// Use override for virtual functions
class Derived : public Base {
public:
    void Process() override;  // Not virtual
};

// Range-based for loops
for (const auto& item : items) {
    ProcessItem(item);
}

// Use std::optional for optional values
std::optional<User> FindUser(int id);
if (auto user = FindUser(42)) {
    ProcessUser(*user);
}

// Use structured bindings (C++17)
auto [iter, success] = my_map.insert({key, value});

// RAII for resource management
{
    std::lock_guard<std::mutex> lock(mutex_);
    // Critical section
}  // lock automatically released

// Avoid exceptions (Google style)
// Use error codes or std::optional instead

// Use constexpr for compile-time constants
constexpr int kBufferSize = 1024;
constexpr double Square(double x) { return x * x; }

// Avoid using namespace directives in headers
// Bad: using namespace std;
// Good: use explicit names or type aliases

// Prefer references to pointers for parameters
void ProcessData(const Data& data);  // Reference
void ModifyData(Data* data);  // Pointer (can be null)

// Use static_cast for most type conversions
double value = static_cast<double>(int_value);

// Initialize variables at declaration
int count = 0;  // Good
std::vector<int> data = {1, 2, 3};

// Use enum class over plain enum
enum class Color {
    kRed,
    kGreen,
    kBlue
};

// Use std::string_view for non-owning string references
void PrintMessage(std::string_view message);
```

### Comments
```cpp
// File-level comment (copyright, description)
// Copyright 2025 Company Name
// This file implements the user authentication system.

// Class comment
// Represents a user account with authentication credentials.
// Thread-safe for concurrent access.
class UserAccount {
 public:
  // Creates a new user account with the given username.
  // Returns nullptr if username is invalid.
  static std::unique_ptr<UserAccount> Create(const std::string& username);
  
  // Authenticates the user with the given password.
  // Returns true if authentication succeeds.
  bool Authenticate(const std::string& password);
  
 private:
  std::string username_;
  std::string password_hash_;
};

// Function comment
// Calculates the total price for the given items.
//
// Args:
//   items: The items to calculate the total for
//   discount: Optional discount factor (0.0 to 1.0)
//
// Returns:
//   The total price after applying the discount.
//
// Note: This function is O(n) where n is the number of items.
double CalculateTotal(const std::vector<Item>& items, double discount = 0.0);
```

---

## Conclusion

These coding standards provide GitHub Copilot with comprehensive context for generating high-quality, idiomatic code across major programming languages. Key takeaways:

### Universal Best Practices
- **Readability first**: Write code that others can understand
- **Consistency**: Follow project conventions and language idioms
- **Type safety**: Use strong typing features available in each language
- **Error handling**: Handle errors explicitly and safely
- **Documentation**: Document public APIs and complex logic

### Tool Integration
Enhance Copilot's effectiveness by combining it with:
- **Linters**: ESLint, Pylint, RuboCop, Clippy, etc.
- **Formatters**: Prettier, Black, gofmt, rustfmt
- **Type checkers**: TypeScript, mypy, Flow
- **Static analysis**: SonarQube, CodeQL, language-specific analyzers

### Continuous Learning
- Stay updated with language evolution and new features
- Review generated code for correctness and idiomaticity
- Provide feedback to improve Copilot suggestions
- Share knowledge with your team

### Remember
While these guidelines help Copilot generate better code, always review and test the generated code. Copilot is a tool to assist development, not replace developer judgment and expertise.




