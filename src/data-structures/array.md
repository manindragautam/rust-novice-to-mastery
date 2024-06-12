# Array

**1. Declaring and Initializing Arrays:**

- Arrays have a fixed size and store elements of the same type.

```rust
let numbers: [i32; 5] = [1, 2, 3, 4, 5]; // Array with 5 elements

let chars = ['a', 'b', 'c']; // Array of characters (char type)
```

**2. Accessing Elements:**

- Use indexing (`[]`) to access elements by their position (zero-based).

```rust
let first_number = numbers[0]; // Access the first element
println!("First number: {}", first_number);
```

**3. Array Length:**

- Use the `len()` method to get the number of elements in the array.

```rust
let array_length = numbers.len();
println!("Array length: {}", array_length);
```

**4. Array Slices:**

- Create a slice from an array to access a sub-section without copying data.

```rust
let slice = &numbers[1..3]; // Slice from index 1 (inclusive) to 3 (exclusive)
println!("Slice: {:?}", slice);
```

**Remember:**

- Arrays are useful for fixed-size data when mutability isn't a requirement.
- Consider vectors for dynamic resizing and built-in functionalities like sorting and searching.
