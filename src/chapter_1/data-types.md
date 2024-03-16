## Data Types

Rust has several scalar data types for storing single values:

1. **Integers**
   - Signed integers: `i8`, `i16`, `i32`, `i64`, `i128` (ranging from 8 bits to 128 bits)
   - Unsigned integers: `u8`, `u16`, `u32`, `u64`, `u128` (ranging from 8 bits to 128 bits)
   - The default integer type is `i32`.
   - You can use type suffixes like `92u8` to explicitly specify the type.

2. **Floating-Point Numbers**
   - `f32` (32-bit single-precision)
   - `f64` (64-bit double-precision)
   - The default floating-point type is `f64`.

3. **Booleans**
   - `bool` represents a value of either `true` or `false`.

4. **Characters**
   - `char` represents a Unicode Scalar Value (code point), which can be a letter, numeric digit, special character, or emoji.
   - Characters are enclosed in single quotes: `let c = 'z';`

Rust also has several compound data types:

1. **Tuples**
   - A tuple is a fixed-size collection of values of different types.
   - Tuples are created using parentheses `()` with values separated by commas.
   - Example: `let person = ("John", 32, 1.75);`

2. **Arrays**
   - An array is a collection of values of the same type with a fixed length.
   - Arrays are created using square brackets `[]` with values separated by commas.
   - Example: `let numbers = [1, 2, 3, 4, 5];`
   - Arrays have a fixed size, which is known at compile-time.

In addition to these built-in data types, Rust also allows you to create your own custom data types using `struct`s and `enum`s, which we'll cover later.

When working with variables and data types, it's important to understand Rust's ownership rules and borrowing mechanisms, which ensure memory safety and prevent common issues like null pointer dereferences and data races.

Here are a few more examples to illustrate variable declarations and different data types:

```rust
let x: i32 = 42; // signed 32-bit integer
let y: f64 = 3.14; // 64-bit floating-point number
let is_positive = true; // boolean
let character = 'A'; // character

let tup: (i32, f64, char) = (500, 6.4, 'x'); // tuple
let (city, population) = ("Kanpur", 3286000); // destructuring with tuple
let arr = [1, 2, 3, 4, 5]; // array
```

Remember, Rust's static type system helps catch many potential issues at compile-time, making your code more robust and easier to reason about.
