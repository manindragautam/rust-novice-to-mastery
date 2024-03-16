## Control Flows

**1. `if` Expressions**

`if` expressions are used for conditional branching. They evaluate a boolean condition and execute the associated code block if the condition is true.

```rust
let x = 5;

if x > 0 {
    println!("Positive number");
} else if x < 0 {
    println!("Negative number");
} else {
    println!("Zero");
}
```

You can also use `if` in a let statement to assign a value based on a condition:

```rust
let is_even = if x % 2 == 0 { true } else { false };
```

**2. `loop` Loops**

The `loop` keyword creates an infinite loop, which can be exited using the `break` keyword or by returning from the loop.

```rust
let mut counter = 0;

loop {
    counter += 1;
    println!("Counter: {}", counter);

    if counter == 5 {
        break;
    }
}
```

**3. `while` Loops**

A `while` loop executes a block of code as long as a specific condition is true.

```rust
let mut x = 0;

while x < 10 {
    println!("x = {}", x);
    x += 1;
}
```

**4. `for` Loops**

The `for` loop is used to iterate over an iterator, such as a range, an array, or a vector.

```rust
// Iterate over a range
for x in 0..5 {
    println!("{}", x); // Prints 0 1 2 3 4
}

// Iterate over an array
let arr = [10, 20, 30, 40, 50];

for element in arr.iter() {
    println!("Value: {}", element);
}
```

**5. `match` Expressions**

The `match` expression is a powerful control flow construct that performs pattern matching against a value. It's often used with enums to handle different cases.

```rust
enum Color {
    Red,
    Green,
    Blue,
}

let color = Color::Red;

match color {
    Color::Red => println!("The color is red"),
    Color::Green => println!("The color is green"),
    Color::Blue => println!("The color is blue"),
}
```

You can also use the `_` catch-all pattern to handle any unmatched cases.

These control flow constructs allow you to write complex logic and control the execution flow of your Rust programs. Rust's safety guarantees ensure that these constructs are used correctly and prevent common issues like off-by-one errors or infinite loops.
