# Scalar Types
# ============

## Integer Types
### Unsigned Integers
- `u8`: 8-bit unsigned integer
- `u16`: 16-bit unsigned integer
- `u32`: 32-bit unsigned integer
- `u64`: 64-bit unsigned integer
- `u128`: 128-bit unsigned integer
- `usize`: Pointer-sized unsigned integer

### Signed Integers
- `i8`: 8-bit signed integer
- `i16`: 16-bit signed integer
- `i32`: 32-bit signed integer
- `i64`: 64-bit signed integer
- `i128`: 128-bit signed integer
- `isize`: Pointer-sized signed integer. Maximum bound for isize is upper bound of object and array size.

### Some notes
- `isize` and `usize` depend on the architecture of the computer your program is running on: 64 bits if you're on a 64-bit architecture and 32 bits if you're on a 32-bit architecture.
- `isize` and `usize` are primarily used to index collections.
- `isize` and `usize` are the default integer types for indexing collections.
- The default integer type is `i32`. Because it's generally the fastest, even on 64-bit systems.
- Not all integer types are supported in all the systems. For example, `i128` is only supported in systems that have a 128-bit architecture.

### Specification of integers
- `Decimal`: `98_222`
- `Hex`: `0xff`
- `Octal`: `0o77`
- `Binary`: `0b1111_0000`
- `Byte (u8 only)`: `b'A'`

### More notes on integers
- The terms `u8` and `bytes` are used interchangeably in rust.
- Representation of integers which take more than one digit can be separated by underscores for better readability.

## Floating-Point Types
- `f32`: 32-bit floating-point number, 32-bit precision
- `f64`: 64-bit floating-point number, 64-bit precision

### Notes on floating-point types
- `f64` is the default type for floating-point numbers because on modern CPUs it's roughly the same speed as `f32` but is capable of more precision. But it is really slow in < 64-bit systems.
- Floating-point literals follow the `IEEE-754` standard. No special suffix is required. It requires at least one digit before the decimal point, which can be 0.

## Notes on numerical literals
- It is also completely fine to use the type suffixes with numerical literals. For example, `42u8` is a valid expression. And we can use underscores in numerical literals for better readability. For example, `42_u8` is the same as `42u8`.

## Boolean Type
- `bool`: Represents a boolean value. It can have two values: `true` and `false`.
- The size of the `bool` type is `1 byte`.
- Arithmetic operations are not allowed on boolean types.
- `bool` types can be casted to integers. `true` is `1` and `false` is `0`, for arithmetic operations. Example: `let x: i32 = true as i32;`


## Character Type
- `char`: Represents a single Unicode character. It is 4 bytes in size.
- It is specified with single quotes. Example: `let x: char = 'x';`
- Characters are fairly useless.