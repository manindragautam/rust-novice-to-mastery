## Defining and calling functions

Functions are fundamental building blocks in Rust that encapsulate reusable code blocks. Here's a comprehensive guide with examples at various skill levels:

- **Function declaration:**
    - Uses the `fn` keyword followed by the function name, parentheses for arguments, and an arrow (`->`) specifying the return type (if any).
    - The code block within curly braces `{}` defines the function's body.

```rust
fn say_hello() -> String {
  String::from("Hello, world!")
}

fn main() {
  let x = say_hello(); // Call the function
  println!("{}", x);
}
```

- **Function arguments:**
    - Pass values to functions as arguments within parentheses.
    - Arguments are typed, like variables.

```rust
fn greet(name: &str) {
  println!("Hello, {}!", name);
}

fn main() {
  greet("Alice");
}
```

- **Return values:**
    - Use the `return` keyword to send a value back from the function.

```rust
fn add(x: i32, y: i32) -> i32 {
  return x + y; // Explicit return
}

fn main() {
  let sum = add(5, 3);
  println!("Sum: {}", sum);
}
```

- **Multiple arguments:**
    - Functions can have multiple arguments of different types.

```rust
fn calculate_area(width: f64, height: f64) -> f64 {
  return width * height; // Implicit return (no semicolon needed after the last expression)
}

fn main() {
  let area = calculate_area(2.5, 4.0);
  println!("Area: {}", area);
}
```

- **Function borrowing:**
    - Use references (`&`) to borrow data from other parts of your program without ownership transfer.

```rust
fn print_slice(data: &[i32]) { // Takes a slice of integers (& indicates reference)
  for num in data {
    println!("{}", num);
  }
}

fn main() {
  let numbers = [1, 2, 3, 4, 5];
  print_slice(&numbers); // Pass a reference to the slice
}
```

- **Closures:**
    - Anonymous functions that can capture the environment where they are defined.

```rust
fn main() {
  let mut count = 0;
  let mut increment = || {
    count += 1;
  };

  increment(); // Call the closure
  increment();

  println!("Count: {}", count);
}
```

- **Higher-order functions:**
    - Functions that take other functions as arguments or return functions.

```rust
fn add(x: i32, y: i32) -> i32 {
  x + y
}

fn multiply(x: i32, y: i32) -> i32 {
  x - y
}

// Function pointer declaration
type MathOperation = fn(i32, i32) -> i32;

fn perform_operation(op: MathOperation, a: i32, b: i32) -> i32 {
  op(a, b) // Call the function pointed to by 'op'
}

fn main() {
  let result1 = perform_operation(add, 5, 3);
  let result2 = perform_operation(multiply, 5, 3);

  println!("Addition result: {}", result1);
  println!("Multiplication result: {}", result2);
}
```
