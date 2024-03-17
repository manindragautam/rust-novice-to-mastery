## References and borrowing

References and borrowing are cornerstones of Rust's ownership system, allowing you to access data without taking ownership. Let's explore them with examples at various skill levels:

- **Basic Concept:**
    - A reference (`&`) provides a temporary way to access data owned by another variable.
    - You can think of it as a pointer to the actual value.

```rust
fn main() {
  let name = "Alice"; // 'name' owns the string "Alice"
  let greeting = &name; // 'greeting' borrows the string from 'name'

  println!("Hello, {}", greeting);
}
```

- **Moving:**
    - When assigning a value to another variable using `=` (move semantics), ownership is transferred.
    - The original variable can no longer be used.

```rust
fn main() {
  let name = String::from("Alice"); // 'name' owns the string "Alice"
  let another_name = name; // Ownership is transferred to 'another_name'

  println!("{}", name); // This line will cause an error because 'name' no longer owns the string
}
```

- **Copying:**
    - In some cases (e.g., primitive types like integers), Rust copies the value when assigning. Both variables own independent copies.

```rust
fn main() {
  let age = 30; // 'age' owns the value 30
  let my_age = age; // A copy of 30 is assigned to 'my_age'

  println!("Age: {}", age); // Still valid
  println!("My age: {}", my_age);
}
```

- **Immutable Borrowing:**
    - References are immutable by default. You can't modify the borrowed data through the reference.

```rust
fn main() {
  let name = String::from("Bob"); // 'name' owns the string "Bob"
  let greeting = &name; // Borrow the string

  greeting.push_str("!"); // Error: 'greeting' is immutable

  println!("Hello, {}", greeting);
}
```

- **Mutable Borrowing:**
    - Use `&mut` for mutable borrowing, allowing changes to the borrowed data. However, only one mutable borrow can exist at a time.

```rust
fn main() {
  let mut name = String::from("Charlie"); // 'name' owns the mutable string "Charlie"
  {
    let greeting = &mut name; // Borrow mutably
    greeting.push_str(" Brown"); // Modify the borrowed data through 'greeting'
  }

  println!("Hello, {}", name); // Output: "Hello, Charlie Brown"
}
```

- **Dangling References:**
    - Be cautious of "dangling references" that point to deallocated memory. This occurs if the original owner goes out of scope before the reference is finished using it.

```rust
fn main() {
  // This is bad practice!
  let mut message;
  {
    let greeting = String::from("Hello"); // 'greeting' owns the string "Hello"
    message = &greeting; // Borrow the string (potential dangling reference)
  }

  // 'greeting' is out of scope here, so the reference might be dangling
  println!("Message: {}", message); // This might cause an error
}
```

**Remember:**

- Ownership and borrowing are crucial for memory safety and preventing memory leaks.
- Choose the appropriate ownership mechanism (moving, copying, borrowing) based on your needs.
