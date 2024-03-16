## Blocks

In Rust, a block refers to a group of statements enclosed within curly braces `{}`. It serves two main purposes:

1. **Control Flow:** Blocks act as a unit of execution. The statements within a block are executed sequentially, one after the other. This allows you to group related statements and control the flow of your program.

2. **Scope:** Blocks create a new anonymous namespace scope. This means variables and other items declared within a block are only accessible within that block. When the block finishes execution, these local variables go out of scope and are no longer accessible.

Here's a breakdown of the two functionalities:

**Control Flow:**

```rust
let mut x = 5;

if x > 0 {
  println!("x is positive");
  x = x + 1; // This statement is only executed if the condition is true
}

println!("x is now: {}", x); // This line will print 6
```

In this example, the `if` statement has a block containing the `println!` and assignment statement. These statements only execute if the condition `x > 0` is true.

**Scope:**

```rust
let x = 10; // This x is in the outer scope

{
  let y = 20;  // This y is only accessible within this block
  println!("Inside block: x = {} y = {}", x, y);
}

println!("Outside block: x = {}", x); // This line will print 10 (y is not accessible here)
```

Here, the inner block creates a new variable `y`. This `y` is separate from the outer `x`. You can access the outer `x` from within the block, but the inner `y` is not accessible outside the block.
