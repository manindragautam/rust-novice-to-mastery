## Enums

Enums (short for enumerations) are a way to define a type that can have one of several possible variants. They are particularly useful for representing a set of related values.

**Defining an Enum**

You can define an enum using the `enum` keyword, followed by the enum name and its variants:

```rust
enum Direction {
    North,
    South,
    East,
    West,
}
```

**Using Enums**

You can create instances of an enum variant like this:

```rust
let direction = Direction::North;
```

**Enum Variants with Data**

Enum variants can also have associated data:

```rust
enum Shape {
    Circle(f64), // Radius
    Rectangle(f64, f64), // Width, height
    Triangle(f64, f64, f64), // Side lengths
}

let shape = Shape::Rectangle(3.0, 4.0);
```

**Pattern Matching**

One of the most powerful features of enums is pattern matching, which allows you to handle different variants of an enum using the `match` expression:

```rust
match shape {
    Shape::Circle(radius) => {
        println!("Circle with radius: {}", radius);
    }
    Shape::Rectangle(width, height) => {
        println!("Rectangle with width: {}, height: {}", width, height);
    }
    Shape::Triangle(a, b, c) => {
        println!("Triangle with sides: {}, {}, {}", a, b, c);
    }
}
```

**Advanced Enum Features**

Rust provides several advanced features for working with enums, including:

1. **Associated Functions and Methods**: You can define associated functions and methods on enums using the `impl` block, similar to structs.
2. **Enums as Data Structures**: Enums can be used to represent more complex data structures like linked lists, binary trees, and state machines.
3. **C-like Enums**: Rust also supports C-like enums, where each variant can have an associated integer value.

Structs and enums are powerful tools for organizing and representing data in Rust. They promote code reuse, encapsulation, and type safety, making your code more maintainable and less prone to errors.
