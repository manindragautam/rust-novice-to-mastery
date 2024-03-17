## Advanced Function Concepts: Generics, and Iterators

Now that you've grasped the fundamentals of functions, let's delve into more advanced concepts in Rust:

**1. Generic Functions:**

- **Concept:**
  Define functions that can work with different data types by using placeholders.
- **Syntax:**
  Use angle brackets `<>` to define type parameters (`T`).
- **Use Cases:**
  Write reusable functions that operate on various data types without code duplication.

```rust
fn max<T: PartialOrd>(a: T, b: T) -> T {
    if a > b {
        a
    } else {
        b
    }
}

fn main() {
    let max_int = max(5, 10); // max_int = 10
    let max_float = max(3.14, 2.71); // max_float = 3.14
    println!("{}, {}", max_int, max_float);
}
```

**2. Iterators:**

- **Concept:**
  Provide a way to efficiently step through elements in a collection (like arrays, vectors).
- **Traits:**
  `Iterator` trait defines the protocol for iteration.
- **Use Cases:**
  Process elements in collections one by one using methods like `next()`, `for` loops.

```rust
fn main() {
    let numbers = [1, 2, 3, 4, 5];

    // Manual iteration
    let mut i = 0;
    while i < numbers.len() {
        println!("{}", numbers[i]);
        i += 1;
    }

    // Using 'for' loop with iterator (more concise)
    for num in numbers.iter() {
        println!("{}", num);
    }
}
```
