## Structs

Structs are user-defined data types that allow you to group related data together into a single unit. They are similar to classes in object-oriented programming, but without inheritance.

**Defining a Struct**

You can define a struct using the `struct` keyword, followed by the struct name and its fields:

```rust
struct Person {
    name: String,
    age: u32,
    is_student: bool,
}
```

**Creating Instances**

To create an instance of a struct, you can use the struct literal syntax:

```rust
let person = Person {
    name: String::from("Alice"),
    age: 25,
    is_student: true,
};
```

Alternatively, you can use struct update syntax, which allows you to create a new instance based on an existing one, with some fields updated:

```rust
let person2 = Person {
    name: String::from("Bob"),
    ..person // Copy the remaining fields from `person`
};
```

**Accessing Fields**

You can access the fields of a struct using dot notation:

```rust
println!("Name: {}", person.name);
```

**Methods**

You can define methods on structs using the `impl` (implementation) block:

```rust
impl Person {
    fn new(name: &str, age: u32, is_student: bool) -> Person {
        Person {
            name: String::from(name),
            age,
            is_student,
        }
    }

    fn greet(&self) {
        println!("Hello, my name is {}", self.name);
    }
}
```

In this example, we define a `new` method to create a new `Person` instance, and a `greet` method that prints a greeting.

**Tuple Structs**

Rust also supports tuple structs, which are structs with unnamed fields:

```rust
struct Color(u8, u8, u8);

let red = Color(255, 0, 0);
```
