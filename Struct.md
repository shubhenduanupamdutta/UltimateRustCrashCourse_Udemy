# Structs

**In other languages you have classes, in Rust you have structs.**

```rust
struct RedFox {
    enemy: bool,
    life: u8,
}
```
**Structs can have data fields, methods and associated functions**

## Syntax
- Keyword `struct`
- Name of the struct in capital camel case `RedFox`
- Curly braces `{}` with fields inside
- Then fields with their types `enemy: bool, life: u8`, in a list separated by commas.

## Instantiating a struct
```rust
let red_fox = RedFox {
    enemy: true,
    life: 100,
};
```
- Instantiating is straightforward, just use the name of the struct and assign values to the fields.
- Typically you will use an associated function to create a new instance of a struct with default values.
```rust
impl RedFox {
    fn new() -> Self {
        Self {
            enemy: true,
            life: 100,
        }
    }
}
```
- Methods and associated functions are defined using the `impl` keyword, that is separate from the struct definition.
- `Self` can be used to refer to the struct name inside the implementation block.
- Without the argument self in `new()`, it is an associated function, not a method.
- The `new()` function is a common pattern to create a new instance of a struct with default values.
```rust
let red_fox = RedFox::new();
let life_left = red_fox.life;
red_fox.enemy = false;
red_fox.some_method();
```
- The scope operator `::` is used to access parts of namespace like things. Here we are using it to access the associated function `new()` of the struct `RedFox`.
- We can use `.` syntax to get and set the fields of the struct, and call the methods of the struct.
- **Methods are also defined in the implementation block.**
```rust
impl RedFox {
    // Associated function
    fn function() {
        // code
    }
    // Method
    fn move(self) {
        // code
    }
    fn attack(&self) {
        // code
    }
    fn mut_borrow(&mut self) {
        // code
    }
}
```
- Methods are functions that take `self` as the first argument, which represents the instance of the struct.