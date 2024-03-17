## Closures

Closures are a powerful feature in Rust that allow you to create anonymous functions that can capture the environment where they are defined. Let's explore them with examples at various skill levels:

- **Basic Concept:**
    - A closure is a block of code that can be treated like a function but doesn't have a name.
    It uses `||` instead of `()` around input variables.
    - It can capture variables from its surrounding scope and use them even after the surrounding function has finished executing.

- **Simple Closure:**

```rust
fn main() {
  let mut count = 0;
  let mut increment = || {
    count += 1;
  }; // A closure taking no arguments which returns an `i32`. The return type is inferred.

  increment(); // Call the closure
  increment();

  println!("Count: {}", count); // Output: 2
}

```
Here, the `increment` variable holds a closure that captures the `count` variable from the surrounding `main` function.


- **Closures with Arguments:**

```rust
fn main() {
  let mut add = |x: i32, y: i32| -> i32 {
    x + y
  };

  let result = add(5, 3);
  println!("Sum: {}", result); // Output: 8
}
```

This closure takes two arguments (`x` and `y`) and returns their sum.
It can be used like a regular function to perform calculations.

- **Closures and Borrowing:**

```rust
fn main() {
  let numbers = vec![1, 2, 3, 4, 5];

  let find_even = numbers.iter().filter(|&num| num % 2 == 0); // Closure for filtering even numbers

  for num in find_even {
    println!("Even number: {}", num);
  }
}
```

Here, we use a closure with the `filter` method on a vector to find even numbers.
The closure borrows (`&`) the elements from the `numbers` vector.

- **Closures and Iterators:**
    - Closures are frequently used with iterators to define custom logic for processing collections.
    - Explore advanced iterator methods like `map`, `fold`, and `any` to leverage closures for complex data manipulation.

**Key Points:**

- Closures offer flexibility by allowing functions to be defined "on the fly."
- They can access variables from their enclosing scope, enabling data persistence.
- Practice writing closures for different use cases to master their power.
- Be mindful of variable borrowing within closures to avoid ownership issues.
