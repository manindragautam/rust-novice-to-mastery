## Declaring and Assigning Variables

In Rust, declaring and assigning variables go hand-in-hand. Let's explore the specifics:

**Declaring Variables:**

- Use the `let` keyword followed by the variable name and a colon (`:`).
- After the colon, specify the desired data type for the variable.
- If you don't explicitly specify the data type, Rust can infer it from the assigned value

```rust
let age: u32; // Declares a variable 'age' of type u32 (unsigned 32-bit integer)
let message: &str; // Declares a variable 'message' of type &str (immutable string slice)
```

**Assigning Values:**

- You can assign a value to a variable during declaration using an equal sign (`=`).
- This initializes the variable with the provided value.

```rust
let age: u32 = 25; // Declares and initializes 'age' with value 25
let greeting = "Hello"; // Declares and initializes 'greeting' with string "Hello" (type inferred from value)
```

**Mutable Bindings (let mut):**

By default, bindings in Rust are immutable. This means their value cannot be changed after assignment. However, you can use `let mut` to create a mutable binding that allows you to modify its value later.

```rust
let mut x = 5;
x = 12; // This is allowed because x is mutable
```

**Shadowing:**

Rust allows you to create a new binding with the same name as an existing one. This is called shadowing. The new binding shadows the older one.

```rust
let x = 10;
let x = x + 20; // Shadows the first x

println!("x: {}", x); // P, effectively hiding it within that scoperints 30
```

**Scope:**

Block `{}` creates a new anonymous namespace scope. This means variables and other items declared within a block are only accessible within that block. When the block finishes execution, these local variables go out of scope and are no longer accessible.

```rust
let x = 10; // This x is in the outer scope

{
  let y = 20;  // This y is only accessible within this block
  println!("Inside block: x = {} y = {}", x, y);
}

println!("Outside block: x = {}", x); // This line will print 10 (y is not accessible here)
```

**Constants:**

- Use the `const` keyword to declare constants with fixed values that cannot be changed after initialization.

```rust
const PI: f64 = 3.14159; // Constant 'PI' with value 3.14159 (fixed)
```


**In summary:**

- Use `let` to declare variables.
- Specify data types explicitly or let Rust infer them.
- Use `mut` for mutable variables that can be changed later.
- Use `const` for fixed values (constants).
- Remember variable scope within code blocks.
