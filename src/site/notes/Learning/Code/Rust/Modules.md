---
{"dg-publish":true,"permalink":"/learning/code/rust/modules/"}
---

## What is a Module?

>Modules in Rust help in splitting a program into logical units for better readability and organization.
>
>Once a program gets larger, it is important to split it into multiple files or namespaces. Modules help in structuring our program.
>
>A module is a collection of items: functions, structs and even other modules.

*[Programiz](https://www.programiz.com/rust/module)*

## Code

```rust
// To define module
mod module_name {
	// code here
}
```

### Inside Functions

```rust
mod dashboard {
	fn print() {
		println!("Hi!");
	}
}
```

### Public and private functions

```rust
mod config {
	
	// by default this is private
	fn environment() {
		println!("Configuration");
	}
	
	// Changing its visibility to public
	pub fn options() {
		println!("Set your options !");
	}
}
```

## Calling Module functions

```rust
mod config {
	
	// by default this is private
	fn environment() {
		println!("Configuration");
	}
	
	// Changing its visibility to public
	pub fn options() {
		println!("Set your options !");
	}
}

fn main() {
	config::options();
}
```

## Using private functions

>[!INFO] Using Private Functions
>If you want to use ``environment`` in this case, you may call it inside of another function that works as public, for example, call ``environment`` inside of ``options``

```rust
mod config {
	
	// by default this is private
	fn environment() {
		println!("Configuration");
	}
	
	// Changing its visibility to public
	pub fn options() {
		println!("Set your options !");
		environment();
	}
}

fn main() {
	config::options();
}
```

## Nested Modules

```rust
pub mod player {
    pub mod sprite {
        pub fn create() {
            println!("called player::sprite::create");
        }
    }
}

fn main() {
	player::sprite::create();
}
```

### Reserved word ``use``

To use a function without writing the whole word, you just can use ``use`` and setting the path to the specific function you want use

```rust
pub mod player {
    pub mod sprite {
        pub fn create() {
            println!("called player::sprite::create");
        }
    }
}

use player::sprite::create;

fn main() {
	create();
}
```