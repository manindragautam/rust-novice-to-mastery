## Loops

Loops are essential for repeating code blocks based on a condition. Let's explore different looping constructs in Rust with working examples at various skill levels:

- **`loop` statement:**
Executes a block of code repeatedly until you explicitly break out of it.

```rust
fn main() {
  let mut count = 0;

  loop {
    println!("Count: {}", count);
    count += 1;

    if count == 5 {
      break; // Exit the loop when count reaches 5
    }
  }
}
```

- **`while` loop:**
Executes a block of code as long as a condition remains true.

```rust
fn main() {
  let mut counter = 1;

  while counter <= 3 {
    println!("Iteration: {}", counter);
    counter += 1;
  }
}
```

- **`for` loop:**
Iterates over elements in a collection (e.g., arrays, vectors).

```rust
fn main() {
  let numbers = [1, 2, 3, 4, 5];

  for number in numbers.iter() {
    println!("Number: {}", number);
  }
}
```

- **`for` loop with range syntax:**
Iterates over a range of values.

```rust
fn main() {
  for num in 1..=5 { // Inclusive range: 1, 2, 3, 4, 5
    println!("{}", num);
  }
}
```

- **Loop control flow:**
    - `break` statement: Exits the loop prematurely from within the loop body.
    - `continue` statement: Skips the current iteration and moves to the next one.

```rust
fn main() {
  for num in 1..=10 {
    if num % 2 == 0 { // Skip even numbers
      continue;
    }
    println!("Odd number: {}", num);

    if num == 7 {
      break; // Exit after printing 7
    }
  }
}
```

- **`while let` loop:**
Combines pattern matching with loop conditions.

```rust
enum Message {
  Quit,
  Move { x: i32, y: i32 },
  Input(String),
}

fn main() {
  let mut message = Message::Input(String::from("Hello"));

  while let Message::Input(text) = message {
    println!("Input: {}", text);
    message = Message::Quit; // Change message to exit the loop
  }
}
```

- **Infinite loops:**
Be cautious with `loop` statements to avoid infinite loops. Use conditions or break statements to ensure termination.

- **Advanced Loops:**
Explore iterator adapters like `map`, `filter`, `fold` for concise and expressive data processing within loops. Refer to the Rust documentation on iterators: [https://doc.rust-lang.org/std/iter/trait.Iterator.html](https://doc.rust-lang.org/std/iter/trait.Iterator.html).
