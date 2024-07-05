# Traits
**Traits are similar to interfaces in other languages, but with some differences.**
**Rust takes composition over inheritance approach.**

```rust
struct RedFox {
    enemy: bool,
    life: u32,
}

impl RedFox {
    fn new() -> Self {
        Self {
            enemy: true,
            life: 100,
        }
    }
}

impl RedFox {
    fn attack(&self) {
        println!("RedFox attacks!");
    }
    fn defend(&mut self) {
        println!("RedFox defends!");
        self.life -= 10;
        println("Life left: {}", self.life);
    }
}

trait Noisy {
    fn get_noise(&self) -> &str;
}

impl Noisy for RedFox {
    fn get_noise(&self) -> &str {
        "Yip Yip"
    }
}
```
## **Traits define a required behavior**
### In another words function and methods a struct must implement if it wants to have that trait.

## Why use traits?
- We could have just implemented the trait `get_noise()` in above case directly as a method in the struct `RedFox`. Why go for the trait?
- **Traits allow us to define a common behavior that can be implemented by different structs.**
- **This allows us to write generic code that can work with any struct that implements the trait.**
```rust
fn print_noise<T: Noisy>(item: T) {
    println!("{}", item.get_noise());
}
```
### - As long as one of either a trait or struct is defined in your project, you can implement any trait for any struct.
### - This is a powerful feature of Rust, as it allows you to write code that is more flexible and reusable.

```rust
impl Noisy for u8 {
    fn get_noise(&self) -> &str {
        "BYTE!"
    }
}
```

## Copy trait
- **Copy trait is a special trait that allows you to copy the value of a variable instead of moving it.**
- **This is useful when you want to keep the original value and use the copy of it.**
- **All primitive types implement the Copy trait.**
- **You can implement the Copy trait for your custom types if they are simple enough to be copied.**
- **If the type has any heap allocation, copy trait cannot be implemented.**

## Traits Inheritance
- **Traits can inherit from other traits.**
- **Any one implementing the derived trait must also implement the base trait.**

## Notes
- **Traits can also have default behaviors.**
- **Traits can be used to define a common behavior for different structs.**
```rust
train Run {
    fn run(&self) {
        println!("Running!");
    }
}

struct Robot {}
impl Run for Robot {}
```
- **In this case we defined a default behavior for trait `Run`.**
- **And we didn't override it in the struct `Robot`.**
- **So, the default behavior will be used when we call `run()` on a Robot instance.**
- **You can't define fields in traits.**
- **Workaround is to define setter and getter methods in your trait.**