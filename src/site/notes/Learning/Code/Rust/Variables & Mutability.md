---
{"dg-publish":true,"permalink":"/learning/code/rust/variables-and-mutability/"}
---

## Importante Terms
---
### Mutability

In rust, variables are inmutables by default. To make a variable mutable, you have to write before the variable the word `mut`, Here is an example:

```rust
use std::io;

fn main () {
	let mut name = "Value 1";
	
	print("old value of 'name': {name}")
	
	io::stdin().read_line(&mut name)
		.expect("Something has gone wrong");
		
	print("new value of 'name': {name}")
}
```

First, we define a varaible with a value of *Value 1*, later `name` value is printed. After that we use `stdin` to enter a new value for `name` then we use `&mut name` to shadow the value of name and rename that. At the end we printed it.

### Constants

```rust
const TWO_HOURS_INS_SEC = 2 * 60 * 60;
```

### Shadowing

It means that you can overwrite a value in a variable, without the necessity to create another instance. Example:

```rust
fn main () {
	let x = 10;
	println!("First Value of x: {x}");
	let x = x + 5;
	println!("Overwritting x value: {x}");
}
```

```output
First value of x: 10
Overwritting x value: 15
```

#### Within inner Scope

To create an inner scope, you have to use `{}` indicating a inner scope was created. Inside this, the value of `x` will change until scope ends, then x return to the original value

```rust
fn main () {
	let x = 10;
	println!("First Value of x: {x}");
	
	{
		let x = x - 5;
		println!("x Value within inner scope {x}");
	}
	let x = x + 5;
	println!("Overwritting x value: {x}");
}
```

>[!INFO] Important
>Shadowing concept is not the same that change or making a variable `mut`. When you are using `let` it means that you effectively are creating another variable
