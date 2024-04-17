# Variables & Operators

Variables and operators are the building blocks of any programming language. In Rust, they play a crucial role in storing data, manipulating values, and controlling program flow. Here's a detailed breakdown of both concepts:

**1. Variables:**

- **What are they?** Variables act as named containers that store data during program execution. You can think of them as labeled boxes where you can keep specific values.
- **Declaration:** To create a variable, you use the `let` keyword followed by the variable name, a colon (`:`), and the data type it will hold.

```rust
let age: i32 = 30; // Declares an integer variable 'age' with value 30
let name: String = "Alice".to_string(); // Declares a String variable 'name'
```

- **Data Types:** Data types specify the kind of data a variable can hold. Rust offers various data types for different purposes:
  - **Scalar Types:** Represent single values like integers (`i32`, `u32`), floating-point numbers (`f32`, `f64`), booleans (`bool`), and characters (`char`).
  - **Compound Types:** Group multiple values under one name. Examples include tuples (fixed-length ordered sequences), arrays (fixed-size collections of the same type), and vectors (dynamically sized arrays that can grow or shrink).
  - **References:** Borrowed pointers to existing data, useful for avoiding unnecessary copying.

**2. Variable Scope:**

- **Scope:** The part of your code where a variable is accessible.
- **Local Scope:** Variables declared within a function or block are only accessible within that specific block.

```rust
fn print_age() {
  let age = 25; // Local variable 'age' only accessible within this function
  println!("Age: {}", age);
}
```

- **Global Scope:** Variables declared outside of functions are globally accessible, but use them cautiously to avoid naming conflicts and promote code organization.

**3. The Power of Mutability:**

- **Mutable vs. Immutable:**
  - **Mutable variables:** Their values can be changed after assignment using the assignment operator (`=`).
  - **Immutable variables:** Once assigned a value, they cannot be changed. This improves memory safety and prevents accidental modifications.

```rust
let mut count = 0; // Mutable variable 'count'
count += 1; // Incrementing the value

let pi: f64 = 3.14159; // Immutable variable 'pi' (cannot be reassigned)
```

**4. Operators:**

- **Operators** are symbols that perform various operations on data. Rust provides a rich set of operators for different purposes:
  - **Arithmetic Operators:** Perform basic mathematical calculations (+, -, \*, /, %).
  - **Comparison Operators:** Compare values and return boolean results (==, !=, <, >, <=, >=).
  - **Logical Operators:** Combine boolean expressions (&&, ||, !).
  - **Bitwise Operators:** Perform bit-level operations on data (&, |, ^, <<, >>).
  - **Assignment Operators:** Assign values to variables and perform operations simultaneously (+=, -=, \*=, /=, etc.).

```rust
let x = 10;
let y = 5;

let sum = x + y; // Arithmetic operator: addition
let is_equal = x == y; // Comparison operator: equality

let is_true = true;
let result = is_true && (x > y); // Logical operators: AND and comparison

let mut value = 1;
value <<= 2; // Bitwise operator: left shift by 2 bits (value becomes 4)
```

**5. Choosing the Right Operator:**

- Understanding operator precedence is crucial for writing correct expressions. Parentheses can be used to override default precedence (higher precedence operations are evaluated first).

```rust
let result = (x + y) * 2; // Evaluates x + y first, then multiplies by 2
```

**6. Beyond the Basics:**

- **Operator Overloading:** Rust allows defining custom behavior for operators with specific data types.
- **Error Handling:** Variables and operators can be integrated with error handling mechanisms to ensure program robustness.
