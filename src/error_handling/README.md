# Error Handling

Unlike some languages with exceptions, Rust prioritizes safety and control over errors. It uses two primary types for error handling: `Result` and `Option`.

- **Basic Idea:**
  - `Result<T, E>` represents an outcome, either successful (`Ok(value)`) with a value of type `T`, or an error (`Err(error_value)`) of type `E`.
  - `Option<T>` represents an optional value. It can be `Some(value)` or `None`.

```rust
// Simple example
fn divide(x: i32, y: i32) -> Result<i32, String> {
  if y == 0 {
    return Err(String::from("DivisionByZero")); // Return error on division by zero
  }
  Ok(x / y) // Return Ok with the result
}

fn main() {
  let result = divide(10, 2);
  match result {
    Ok(value) => println!("Result: {}", value),
    Err(error) => println!("Error: {}", error), // Handle the error
  }
}
```

- **Propagating Errors:**
  - Functions can return `Result` to propagate errors to the calling code.

```rust
fn read_file(filename: &str) -> Result<&str, std::io::Error> {
  Ok("Hello World!")
}

fn main() {
  let result = read_file("data.txt");
  match result {
    Ok(content) => println!("File content: {}", content),
    Err(error) => println!("Error reading file: {}", error),
  }
}
```

- **Chaining Operations with `?` Operator:**
  - The `?` operator allows early exit from a function if an error occurs.

```rust
fn read_file(filename: &str) -> Result<&str, std::io::Error> {
  Err(std::io::Error::new(std::io::ErrorKind::Other, "oh no!"))
}

fn process_data(filename: &str) -> Result<(), std::io::Error> {
  let content = read_file(filename)?; // Use ? to propagate errors
  // Process the content
  Ok(())
}

fn main() {
  process_data("data.txt").unwrap_or_else(|err| println!("Error: {}", err)); // Handle error with unwrap_or_else
}
```

- **Custom Error Types:**
  - Create your own error types to provide more specific error information.

```rust
#[derive(Debug)]
enum MyError {
  DivisionByZero,
  InvalidData,
}

fn divide(x: i32, y: i32) -> Result<i32, MyError> {
  if y == 0 {
    return Err(MyError::DivisionByZero);
  }
  Ok(x / y)
}

fn main() {
  let result = divide(10, 0);
  match result {
    Ok(value) => println!("Result: {:?}", value),
    Err(error) => println!("Error: {:?}", error), // Handle the error
  }
}
```

**Additional Resources:**

- Module std::result: [https://doc.rust-lang.org/std/result/](https://doc.rust-lang.org/std/result/)
- Module std::option: [https://doc.rust-lang.org/std/option/](https://doc.rust-lang.org/std/option/)
