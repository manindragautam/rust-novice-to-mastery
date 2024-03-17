## Defining and using structs

Structs are fundamental building blocks in Rust for creating custom data types that group related values together. Let's explore them with examples at various skill levels:

- **Basic Concept:**
  - A struct is a user-defined type that bundles data fields of different types under a single name.
  - It's similar to a class in other languages but without methods (functions associated with the struct).

```rust
struct Person {
  name: String, // Field of type String
  age: u32,     // Field of type u32 (unsigned 32-bit integer)
}

fn main() {
  // Create a struct instance (like creating an object)
  let alice = Person { name: String::from("Alice"), age: 30 };

  println!("Name: {}", alice.name); // Access fields using dot notation
  println!("Age: {}", alice.age);
}
```

- **Updating Struct Fields:**
  - Struct fields can be modified after creation (except when using `const` for constant values).

```rust
struct Person {
  name: String,
  age: u32,
}

fn main() {
  let mut alice = Person { name: String::from("Alice"), age: 30 }; // Use 'mut' for mutability
  alice.age = 31; // Update the 'age' field

  println!("Name: {}", alice.name);
  println!("Age: {}", alice.age);
}
```

- **Methods**

  - You can define methods on structs using the `impl` (implementation) block:

```rust
struct Person {
  name: String,
  age: u32,
}

impl Person {
    fn new(name: &str, age: u32) -> Person {
        Person {
            name: String::from(name),
            age,
        }
    }

    fn greet(&self) {
        println!("Hello, my name is {}", self.name);
    }
}

fn main() {
    let alice = Person::new("Alice", 30);
    alice.greet();
}
```

- **Unit Structs:**
  - Structs with no fields are called unit structs and are useful for markers or placeholders.

```rust
struct Empty; // Unit struct with no fields

fn main() {
  let empty_struct = Empty; // Create an instance of the empty struct
}
```

- **Tuple Structs:**
  - Structs with named fields that behave similarly to tuples.

```rust
struct Point(i32, i32); // Tuple struct with x and y coordinates

fn main() {
  let origin = Point(0, 0);
  println!("X: {}, Y: {}", origin.0, origin.1); // Access fields by index
}
```
