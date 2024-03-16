## Functions

**Syntax**

Functions in Rust are defined using the `fn` keyword, followed by the function name, parameters (if any), and the return type. Here's the basic syntax:

```rust
fn function_name(param1: Type, param2: Type, ...) -> ReturnType {
    // function body
    // ...
    // return expression;
}
```

- Function names are typically written in `snake_case` style.
- Parameters are specified with their name and type, separated by a colon (`:`).
- The return type is specified after the parameter list with the `->` symbol.
- If a function doesn't return a value, you can use the `()` syntax or omit the return type entirely.

**Example**

```rust
fn add(x: i32, y: i32) -> i32 {
    x + y
}

fn greet(name: &str) {
    println!("Hello, {}!", name);
}

fn main() {
    let sum = add(3, 5); // sum = 8
    greet("Alice"); // prints "Hello, Alice!"
}
```

**Function Parameters**

Rust supports several types of parameters:

1. **Immutable Parameters**: By default, parameters are immutable, meaning you can't modify their values within the function.
2. **Mutable Parameters**: To make a parameter mutable, use the `mut` keyword before the parameter name.
3. **Reference Parameters**: You can pass values by reference using the `&` symbol. This allows you to access and modify the original value without taking ownership.

```rust
fn increment(x: &mut i32) {
    *x += 1; // Dereference x to modify its value
}

fn main() {
    let mut value = 5;
    increment(&mut value); // value is now 6
}
```

**Return Values**

Functions can return values using the `return` keyword followed by the expression to be returned. However, in simple cases, you can omit the `return` keyword and let the last expression be the return value.

```rust
fn pow(base: i32, exponent: i32) -> i32 {
    let mut result = 1;
    for _ in 0..exponent {
        result *= base;
    }
    result
}
```

**Statements vs. Expressions**

In Rust, there's a distinction between statements and expressions:

- **Statements** are instructions that perform some action but don't return a value (e.g., `let` statements, variable assignments).
- **Expressions** are evaluated to produce a value (e.g., function calls, operations).

Rust is an expression-based language, meaning that you can use expressions in places where statements are expected, such as the right-hand side of a `let` binding.

**Diverging Functions**

Functions that don't return any value are called "diverging functions." They might terminate the program (e.g., `panic!()` or `exit()`) or run indefinitely (e.g., an infinite loop). These functions have the return type `!`, which is pronounced as the "never type."

By understanding functions, their parameters, return values, and the difference between statements and expressions, you'll be well-equipped to write modular and reusable code in Rust.
