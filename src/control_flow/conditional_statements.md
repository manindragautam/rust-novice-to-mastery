# Conditional statements

Here's a breakdown of conditional statements in Rust for control flow:


- **`if` statement:**
Executes code based on a condition.

```rust
fn main() {
  let age = 25;

  if age >= 18 {
    println!("You are an adult.");
  }
}
```


- **`if` with `else`:**
Executes one block of code if the condition is true, another if it's false.

```rust
fn main() {
  let is_raining = true;

  if is_raining {
    println!("Bring an umbrella!");
  } else {
    println!("Enjoy the sunshine.");
  }
}
```


- **`if` with `else if` chain:**
Checks multiple conditions sequentially.

```rust
fn main() {
  let grade = 88;

  if grade >= 90 {
    println!("Excellent!");
  } else if grade >= 80 {
    println!("Very good!");
  } else {
    println!("Keep practicing!");
  }
}
```


- **Nested `if` statements:**
Create more complex decision-making logic.

```rust
fn main() {
  let age = 20;
  let is_citizen = true;

  if age >= 18 {
    if is_citizen {
      println!("You are eligible to vote.");
    } else {
      println!("You must be a citizen to vote.");
    }
  } else {
    println!("You must be 18 or older to vote.");
  }
}
```

- **Match expressions:**
Powerful alternative to `if` statements for pattern matching (often used for enums).

```rust
enum Day {
  Monday,
  Tuesday,
  Wednesday,
  Thursday,
  Friday,
  Saturday,
  Sunday,
}

fn main() {
  let today = Day::Wednesday;

  match today {
    Day::Saturday | Day::Sunday => println!("Enjoy the weekend!"),
    _ => println!("Back to work!"),
  }
}
```


- **Short circuiting:**
Use `&&` (logical AND) and `||` (logical OR) for short-circuiting logic. The evaluation stops once the result is known.

```rust
fn main() {
  let is_admin = true;
  let has_permission = false;

  if is_admin || has_permission { // Only evaluates has_permission if is_admin is false
    println!("You have access.");
  }
}
```
