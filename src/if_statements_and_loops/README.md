# If statements & Loops

Control flow statements dictate the execution path of your Rust program, allowing you to make decisions and repeat code blocks based on conditions. Here's a deep dive into `if` statements and loops in Rust:

**1. Decision Making with `if` Statements**

- **Basic Structure:** The `if` statement allows you to execute a code block if a certain condition is true. Optionally, you can include an `else` block for alternative execution if the condition is false.

```rust
let grade = 85;
if grade >= 90 {
  println!("Excellent!");
} else {
  println!("Good effort!");
}
```

- **`else if` for Multiple Conditions:** You can chain multiple `else if` statements to check for additional conditions.

```rust
let temperature = 20;
if temperature > 30 {
  println!("Hot!");
} else if temperature < 10 {
  println!("Cold!");
} else {
  println!("Pleasant!");
}
```

- **Expressions in Conditions:** The condition within the `if` statement can be any boolean expression that evaluates to `true` or `false`.

```rust
let is_registered = true;
let is_adult = age >= 18;

if is_registered && is_adult {
  println!("You are eligible to vote.");
}
```

**2. Looping with `loop`, `while`, and `for`**

- **`loop` Statement (Infinite Loop):** The `loop` statement creates an infinite loop that continuously executes the code block within its curly braces. You can use a `break` statement to exit the loop prematurely.

```rust
let mut count = 0;
loop {
  println!("Count: {}", count);
  count += 1;
  if count > 5 {
    break;
  }
}
```

- **`while` Loop (Conditional Loop):** The `while` loop executes a code block as long as a specified condition remains true. The condition is checked before each iteration.

```rust
let mut index = 0;
while index < 3 {
  println!("Index: {}", index);
  index += 1;
}
```

- **`for` Loop (Iterating over Collections):** The `for` loop provides a concise way to iterate over elements in a collection (like a vector, array, or range).

```rust
let colors = ["red", "green", "blue"];
for color in colors.iter() {
  println!("Color: {}", color);
}
```

**3. Loop Control Flow:**

- **`break` Statement:** Used to exit a loop prematurely, regardless of the current condition.

```rust
for number in 1..10 { // Range from 1 (exclusive) to 10 (exclusive)
  println!("Number: {}", number);
  if number == 5 {
    break;
  }
}
```

- **`continue` Statement:** Skips the current iteration of the loop and moves on to the next one.

```rust
for number in 1..10 {
  if number % 2 == 0 { // Skip even numbers
    continue;
  }
  println!("Odd number: {}", number);
}
```

**4. Choosing the Right Loop:**

- Use `loop` for situations where you need an infinite loop (rare in practice) or when the exit condition is complex and requires manual control with `break`.
- Employ `while` loops when you have a clear condition that determines how many times the loop should iterate.
- Utilize `for` loops whenever you need to iterate through elements in a collection in a sequential manner.

**5. Advanced Control Flow:**

- **Nested Loops:** Loops can be nested within each other to create more complex control flow patterns.
- **Loop Labels:** Labels can be attached to loops for breaking or continuing from specific parts within nested loops.
