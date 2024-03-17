## Scalar and Compound Data Types

**Scalar Types:**

1. **Integers:**

   ```rust
   fn main() {
       let signed_number: i8 = -128; // Signed 8-bit integer (range: -128 to 127)
       let unsigned_number: u16 = 65_535; // Unsigned 16-bit integer (range: 0 to 65535)

       println!("Signed number: {}, Unsigned number: {}", signed_number, unsigned_number);
   }
   ```

2. **Floating-point:**

   ```rust
   fn main() {
       let pi: f32 = 3.14159; // Single-precision floating-point
       let large_number: f64 = 1.23456789e+10; // Double-precision floating-point (scientific notation)

       println!("Pi (f32): {}, Large number (f64): {}", pi, large_number);
   }
   ```

3. **Boolean:**

   ```rust
   fn main() {
       let is_true: bool = true;
       let is_false = false;

       println!("is_true: {}, is_false: {}", is_true, is_false);
   }
   ```

4. **Character:**

   ```rust
   fn main() {
       let letter: char = 'A';
       let emoji: char = '🤞'; // Unicode character

       println!("Letter: {}, Emoji: {}", letter, emoji);
   }
   ```

**Compound Types:**

1. **Tuples:**

   ```rust
   fn main() {
       let point: (i32, f32) = (1, 2.5); // Tuple with different data types

       println!("Point coordinates: ({}, {})", point.0, point.1);
   }
   ```

2. **Arrays:**

   ```rust
   fn main() {
       let numbers: [i32; 5] = [1, 2, 3, 4, 5]; // Array of 5 integers

       println!("Third element: {}", numbers[2]);
   }
   ```

3. **Strings:**

   ```rust
   fn main() {
       let mut greeting = String::from("Hello"); // Mutable string (use String::from for initialization)
       greeting.push_str(", world!"); // Modify the string

       let name: &str = "Alice"; // Immutable string slice

       println!("{} {}", greeting, name);
   }
   ```

**Note:**

- Arrays are less common in Rust due to ownership rules. Consider using vectors for dynamic collections.
