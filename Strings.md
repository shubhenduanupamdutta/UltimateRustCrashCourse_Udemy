# Strings

## Some warnings
- There are at least 6 types of strings in Rust Standard Library.
- We mostly care about 2 of them that overlap each other `&str` and `String`.


## String Slice `str`
- We will almost always see and use it as `&str`, borrowed string slice.
- A literal string is a `&str`.
- Borrowed string slice is a referred to as a string.
- Data in a `&str` is immutable, i.e. can't be modified.
- It is internally made up of a pointer to some bytes and a length.


## String `String`
- A `String` data can be modified.
- We can create a `String` from a `&str` using `to_string()` method. Example: `let s = "hello".to_string();`
- We can also create a `String` from a `&str` using `String::from()`. Example: `let s = String::from("hello");`
- String is made up of three parts: a pointer to some bytes, a length, and a capacity.
- Capacity can be higher than what is currently being used.


## Notes
- `&str` is a subset of `String` in more ways than one.
- They share a bunch of other characteristics.
- Both `&str` and `String` are valid UTF-8, by definitions, by compiler enforcement and by runtime checks.
- Strings can't be index by character position, because of UTF=8 encodings and variable length characters.
- Our options are
    - Use `chars()` method to iterate over characters.
    - Use `bytes()` method to iterate over bytes. This works fine for ASCII characters.
    - Use `graphemes()` method from `unicode-segmentation` crate to iterate over graphemes.
- Iterators have a handy method `.nth(3)` to get the nth element, instead of indexing.