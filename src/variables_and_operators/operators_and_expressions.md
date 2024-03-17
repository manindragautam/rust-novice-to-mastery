## Operators and Expressions

- **Operators:** Symbols used to perform operations on variables and values.
- **Expressions:** Combinations of variables, operators, and function calls that evaluate to a single value.

**Basic Arithmetic Operators:**

- `+` (addition), `-` (subtraction), `*` (multiplication), `/` (division)
- Example (using variables):

```rust
fn main() {
    let x = 10;
    let y = 5;

    let sum = x + y;
    let difference = x - y;
    let product = x * y;
    let quotient = x / y; // Integer division, truncates decimals (consider f64 for decimal results)

    println!("Sum: {}, Difference: {}, Product: {}, Quotient: {}", sum, difference, product, quotient);
}
```

**Advanced Arithmetic Operators:**

- `%` (modulo - remainder after division)
- `+=`, `-=`, `*=`, `/=` (assignment operators - perform operation and assign result back to variable)
- Example:

```rust
fn main() {
    let mut count = 3;
    count += 2; // Equivalent to count = count + 2

    println!("Count after increment: {}", count);
}
```

**Comparison Operators:**

- `==` (equal to), `!=` (not equal to), `<` (less than), `>` (greater than), `<=` (less than or equal to), `>=` (greater than or equal to)
- Example:

```rust
fn main() {
    let age = 25;

    if age >= 18 {
        println!("You are eligible to vote.");
    } else {
        println!("You are not eligible to vote.");
    }
}
```

**Logical Operators:**

- `&&` (and), `||` (or), `!` (not)
- Example:

```rust
fn main() {
    let is_admin = true;
    let has_permission = false;

    if is_admin || has_permission {
        println!("You have access.");
    } else {
        println!("You don't have access.");
    }
}
```

**Operator Precedence:**

```rust
fn main() {
    let result = 2 + 3 * 4; // Evaluates to 14 (multiplication happens first)
    let result_with_parens = (2 + 3) * 4; // Evaluates to 20 (parentheses force addition first)

    println!("Without parentheses: {}, With parentheses: {}", result, result_with_parens);
}
```

**Bitwise Operators:**

Perform operations on individual bits within integers (`&` (bitwise AND), `|` (bitwise OR), `^` (bitwise XOR), etc.).

```rust
fn main() {
    let num1 = 10; // (00001010 in binary)
    let num2 = 5; // (00000101 in binary)

    let and_result = num1 & num2; // Bitwise AND: 00000000 (0)
    let or_result = num1 | num2; // Bitwise OR:  00001111 (15)
    let xor_result = num1 ^ num2; // Bitwise XOR: 00001111 (15) - sets bits that are different

    println!("AND: {}, OR: {}, XOR: {}", and_result, or_result, xor_result);
}
```

**Advanced Expressions:**

1. **Range Syntax:**
range syntax (.. or ..= for inclusive ranges) for iterating over sequences

```rust
fn main() {
    for num in 1..=5 { // Inclusive range: 1, 2, 3, 4, 5
        println!("{}", num);
    }
}
```

2. **Conditional Expressions (`if` expressions):**

```rust
fn main() {
    let grade = 85;
    let letter_grade = if grade >= 90 { 'A' } else if grade >= 80 { 'B' } else { 'C' };

    println!("Letter grade: {}", letter_grade);
}
```

3. **Operator Overloading:**

    This requires defining custom behavior for operators with specific data types using traits. It's an advanced topic best explored after mastering the basics. Refer to the Rust documentation for details: [https://doc.rust-lang.org/std/ops/](https://doc.rust-lang.org/std/ops/)
