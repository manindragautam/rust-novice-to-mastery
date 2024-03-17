## Defining and implementing traits

Traits are a fundamental concept in Rust that define behavior (methods) that different types can implement. They promote code reusability, abstraction, and polymorphism. Let's explore them with examples at various skill levels:

- **Basic Idea:**
    - A trait is like a blueprint that outlines functionalities (functions) that types can adhere to.
    - It doesn't contain any implementation details, just the expected behavior.

```rust
trait Printable {
  fn print(&self);
}

fn main() {
  // This code won't work yet because there's no implementation for Printable
  // let message = "Hello";
  // println!("{}", message.print()); // Error: The type `std::borrow::Cow<'_, str>` doesn't implement `Printable`
}
```

- **Implementing Traits:**
    - Types can implement a trait by using the `impl` keyword.
    - The implementation provides the actual code for the methods defined in the trait.

```rust
trait Printable {
  fn print(&self);
}

struct Person {
  name: String,
}

impl Printable for Person {
  fn print(&self) {
    println!("Name: {}", self.name);
  }
}

fn main() {
  let alice = Person { name: String::from("Alice") };
  alice.print();
}

```

- **Trait Bounds:**
    - When defining functions or methods, you can specify trait bounds using `where` clauses.
    - This ensures that only types that implement the required trait can be used.

```rust
use std::fmt::Display;

trait Printable {
  fn print(&self);
}

impl<T> Printable for T
where T: Display {
  // Default implementation using the Display trait
  fn print(&self) {
    println!("{}", self);
  }
}

struct Person {
  name: String,
}

impl Display for Person {
  fn fmt(&self, f: &mut std::fmt::Formatter<'_>) -> std::fmt::Result {
    write!(f, "Name: {}", self.name)
  }
}

fn main() {
  let alice = Person { name: String::from("Alice") };
  alice.print(); // Now Person can print automatically
}
```

- **Default Traits:**
    - Define default implementations for trait methods if desired.

```rust
trait Printable {
  fn print(&self) {
    println!("Default implementation");
  }
}

struct Person {
  name: String,
}

impl Printable for Person {
  // Override the default implementation
  fn print(&self) {
    println!("Name: {}", self.name);
  }
}

fn main() {
  let alice = Person { name: String::from("Alice") };
  alice.print(); // Prints "Name: Alice"
}

```

- **Associated Types:**
    - Associated types provide flexibility in trait implementations by allowing them to define the specific type for calculations or data structures based on the implementing type.
    - The concrete type for the associated type is specified in the impl block for the trait.

```rust
trait Shape {
  // Associated type to represent the area type (could be f32, u32, etc.)
  type AreaType;

  // Method to calculate area, returning the associated type
  fn area(&self) -> Self::AreaType;
}

struct Square {
  side: f32,
}

impl Shape for Square {
  type AreaType = f32; // Define the concrete type for Square's area

  fn area(&self) -> Self::AreaType {
    self.side * self.side
  }
}

fn main() {
  let square = Square { side: 5.0 };
  let area = square.area();
  println!("Area of square: {}", area);
}
```

In next example, we define a `Summable` trait that has an associated type `Sum` representing the result of summing two values of the same type. The trait also has a default type parameter `T = Self`, which means that if no type parameter is provided, `T` defaults to the type implementing the trait.

We then implement the `Summable` trait for `i32`, specifying that the associated type `Sum` is `i32`, and implementing the `sum` method to perform integer addition.

```rust
use std::ops::Add;

trait Summable<T = Self> {
    type Sum: Add<T, Output = Self>;

    fn sum(self, other: T) -> Self::Sum;
}

impl Summable for i32 {
    type Sum = i32;

    fn sum(self, other: i32) -> i32 {
        self + other
    }
}

impl Summable for f32 {
    type Sum = f32;

    fn sum(self, other: f32) -> f32 {
        self + other
    }
}

fn main() {
    let x = 5.sum(10); // x = 15
    let y = (5.5).sum(2.3); // y = 7.8
    println!("{}, {}", x, y);
}
```

- **Trait Objects (Dynamic Dispatch):**
    - Use trait objects (`dyn Trait`) for polymorphism with types that don't know the specific trait at compile time.
