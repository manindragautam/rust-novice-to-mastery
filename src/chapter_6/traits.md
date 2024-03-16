# Traits

**Novice Level:**

At the novice level, you should understand that traits in Rust are similar to interfaces in other programming languages. They define a set of methods that a type must implement. Here's a simple example:

```rust
trait Greeter {
    fn greet(&self) -> String;
}

struct Person {
    name: String,
}

impl Greeter for Person {
    fn greet(&self) -> String {
        format!("Hello, my name is {}", self.name)
    }
}

fn main() {
    let person = Person { name: String::from("Alice") };
    println!("{}", person.greet());
}
```

In this example, we define a `Greeter` trait with a single method `greet`. We then implement this trait for the `Person` struct, providing an implementation for the `greet` method.

**Competence Level:**

At the competence level, you should understand that traits can have default method implementations, and you can override or extend these default implementations in your own types.

```rust
trait Greeter {
    fn greet(&self) -> String {
        String::from("Hello, world!")
    }

    fn greet_loudly(&self) -> String {
        self.greet().to_uppercase()
    }
}

struct Person {
    name: String,
}

impl Greeter for Person {
    fn greet(&self) -> String {
        format!("Hi, my name is {}", self.name)
    }
}

fn main() {
    let person = Person { name: String::from("Alice") };
    println!("{}", person.greet());
    println!("{}", person.greet_loudly());
}
```

In this example, the `Greeter` trait has a default implementation for the `greet` method, and a second method `greet_loudly` that uses the `greet` method. When we implement the `Greeter` trait for `Person`, we override the `greet` method with our own implementation, but we can still use the `greet_loudly` method as defined in the trait.

**Proficiency Level:**

At the proficiency level, you should understand that traits can have associated types and associated constants, which allow for more flexibility and abstraction.

```rust
trait Iterator {
    type Item;
    fn next(&mut self) -> Option<Self::Item>;
}

struct Counter {
    count: u32,
}

impl Iterator for Counter {
    type Item = u32;

    fn next(&mut self) -> Option<Self::Item> {
        if self.count < 5 {
            let value = self.count;
            self.count += 1;
            Some(value)
        } else {
            None
        }
    }
}

fn main() {
    let mut counter = Counter { count: 0 };
    for value in counter {
        println!("{}", value);
    }
}
```

In this example, the `Iterator` trait has an associated type `Item`, which represents the type of values that the iterator produces. When we implement the `Iterator` trait for the `Counter` struct, we specify that the associated type `Item` is `u32`. This allows the `Counter` to be used with other code that expects an iterator over `u32` values.

**Expertise Level:**

At the expertise level, you should understand advanced trait features like trait bounds, conditional trait implementation, and orphan rules.

```rust
trait Print {
    fn print(&self);
}

impl<T> Print for T
where
    T: Debug,
{
    fn print(&self) {
        println!("{:?}", self);
    }
}

struct Person {
    name: String,
    age: u32,
}

impl Person {
    fn new(name: &str, age: u32) -> Person {
        Person {
            name: name.to_string(),
            age,
        }
    }
}

fn main() {
    let person = Person::new("Alice", 30);
    person.print();
}
```

In this example, we define a `Print` trait with a single method `print`. We then implement this trait for any type `T` that implements the `Debug` trait, using a trait bound `where T: Debug`. This means that any type that implements `Debug` will automatically get a default implementation of the `print` method that prints the debug representation of the value.

**Mastery Level:**

At the mastery level, you should be able to leverage advanced features like trait objects, dynamic dispatch, and the orphan rules to write idiomatic and efficient Rust code.

```rust
trait Shape {
    fn area(&self) -> f64;
}

struct Rectangle {
    width: f64,
    height: f64,
}

impl Shape for Rectangle {
    fn area(&self) -> f64 {
        self.width * self.height
    }
}

struct Circle {
    radius: f64,
}

impl Shape for Circle {
    fn area(&self) -> f64 {
        std::f64::consts::PI * self.radius * self.radius
    }
}

fn main() {
    let shapes: Vec<Box<dyn Shape>> = vec![
        Box::new(Rectangle {
            width: 3.0,
            height: 4.0,
        }),
        Box::new(Circle {
            radius: 2.5,
        }),
    ];

    for shape in shapes {
        println!("Area: {}", shape.area());
    }
}
```

In this example, we define a `Shape` trait with a single method `area`. We then implement this trait for the `Rectangle` and `Circle` structs. In the `main` function, we create a vector of trait objects (`Box<dyn Shape>`), which allows us to store different types that implement the `Shape` trait in the same vector. We can then call the `area` method on each shape through dynamic dispatch, which determines the correct implementation to call at runtime based on the concrete type.

This example demonstrates the power of traits in Rust for achieving dynamic polymorphism, code reuse, and abstraction. By mastering traits, you can write highly modular and extensible code that adheres to the principles of object-oriented programming while leveraging Rust's unique features and guarantees around memory safety and concurrency.
