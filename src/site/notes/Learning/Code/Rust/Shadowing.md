---
{"dg-publish":true,"permalink":"/learning/code/rust/shadowing/"}
---

## What is Shadowing ?

To illustrate this, we will se the next case:

```rust
let mut numberEntered = String::new();
let numberEntered = numberEntered.trim().parse().expect("Please, input a number");
```

helpfully, Rust allows us to shadow the previous value of `numberEntered` with a new one. _Shadowing_ lets us reuse the `numberEntered` variable name rather than forcing us to create two unique variables, such as `numberEntered_str` and `numberEntered`, for example.