# References and Borrowing

```rust
let s1 = String::from("hello");
do_stuff(&s1);
println!("{}", s1); // hello

fn do_stuff(s: &String) {
    println!("{}", s);
}
```
- In the above code, `do_stuff` function takes a reference to a `String` as an argument using `&` symbol.
- In this case, `s1` is not moved to `do_stuff` function, but a reference to `s1` is passed to the function. `s1` is still the owner of the value.
- At the end of function, the reference goes out of scope and is dropped, not the value.

## Lifetimes
#### - **References must always be valid.**

- Rust compiler wouldn't let you create a reference that outlives the data it is ultimately referencing.
- This makes sure that you don't have a dangling reference, i.e. references never point to null.
- References defaults to _immutable_, even if value is mutable.
- If we make a **mutable reference** to a **mutable value**, then we can use the reference to modify the value.

```rust
let mut s = String::from("hello");
do_stuff(&mut s);

fn do_stuff(s: &mut String) {
    s.push_str(", world");
}
```

- We can use `.push_str()` or other `.` methods to change value using both the variable and the reference, `.` methods automatically dereference the reference until the value is reached.
- `*` is the deference operator, which can be used to dereference the reference manually.

### If you have a variable x
- `&x` is a immutable reference to x.
- `&mut x` is a mutable reference to x.
- `i32` is the type of x.
- `&i32` is a type of immutable reference.
- `&mut i32` is a type of mutable reference.
- `x: &i32` is a type of reference, then `*x` is the immutable value of x.
- `x: &mut i32` is a type of mutable reference, then `*x` is the mutable value of x.

## Rules of References
- **At any given time, you can either have one mutable reference or any number of immutable references.**
- This rule applies across all threads.

## All these rules are enforced by the compiler at compile time.