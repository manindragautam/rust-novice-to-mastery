# Functions

Functions are the workhorses of any programming language. In Rust, they encapsulate reusable blocks of code that perform specific tasks. This guide dives deep into functions in Rust with illustrative examples:

**1. Function Basics:**

- **Structure:** Functions are defined using the `fn` keyword, followed by the function name, parentheses for arguments (inputs), an optional return type, and the code block within curly braces (`{}`).

```rust
fn greet(name: &str) { // Function name: greet, argument: name (string reference)
  println!("Hello, {}!", name);
}
```

- **Arguments and Return Values:**
  - Arguments (inputs) are passed to the function when it's called, providing data for the function to work with.
  - The return type specifies the data type the function returns after its execution (optional, `->` separates arguments and return type).

**2. Calling Functions:**

- Use the function name followed by parentheses containing the actual values (arguments) to be passed to the function.

```rust
greet("Alice"); // Calling greet function with argument "Alice"
```

**3. Advantages of Functions:**

- **Reusability:** Functions can be called from anywhere in your program, promoting code maintainability and avoiding redundancy.
- **Modularity:** Functions break down complex tasks into smaller, manageable units.
- **Encapsulation:** Functions can encapsulate internal logic and data, improving code organization and hiding implementation details.

**4. Working Examples:**

**Example 1: Simple Function with No Arguments**

```rust
fn say_hi() {
  println!("Hi there!");
}

fn main() {
  say_hi(); // Calling the function from main
}
```

**Example 2: Function with Multiple Arguments and a Return Value**

```rust
fn calculate_area(width: f32, height: f32) -> f32 {
  let area = width * height;
  return area; // You can omit `return` for simple expressions
}

fn main() {
  let area = calculate_area(5.0, 3.0);
  println!("Area: {}", area);
}
```

**Example 3: Function with Default Arguments**

```rust
fn print_info(name: &str, age: u32, city: Option<&str>) { // Optional argument with Option type
  println!("Name: {}, Age: {}, City: {:?}", name, age, city);
}

fn main() {
  print_info("Bob", 35, Some("New York")); // Passing all arguments
  print_info("Alice", 28, None); // Omitting optional argument
}
```

**5. Function Scope:**

- Variables declared within a function are local to that function and cannot be accessed from outside.
- Arguments passed to a function are treated as local variables within that function.

**6. Ownership and Borrowing:**

- Rust's ownership system and borrowing concepts play a crucial role in function arguments and return values. Understanding these concepts is essential for writing efficient and memory-safe Rust code.
