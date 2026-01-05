---
{"dg-publish":true,"permalink":"/learning/code/rust/kick-start/"}
---

## First Program in Rust

We have to create a file named ``main.rs``. Once you did this, write in:

```rust
fn main() {
	println!("Hello World");
}
```

Now, you can run that executing the next line commands in root of the directory:

```shell
rustc main.rs
./main
```

- Firts, the command ``rustc`` creates a binary file that you can run later.

### Function definition

The first part of a Rust program is ``main`` function. The structure and way to write that is below:

```rust
fn funName() {
	// Content here ...
}
```

#### Structure

- ``fn`` word starts defining the function, then you can put the name, followed by ``()`` where, if function requires, will be the params of this function, to finish with ``{}`` where will be the content of the function

#### Content

- In this example, we are going to print a ``Hello World``.

```rust
println!("Hello world");
```

- We will notice something there. We have put ``!`` to the end of ``println`` instruction, and it's beacuse it is not a common function, it is a **macro**. Forward, we will see what is a **macro**.
- This will print ``Hello world``

>[!NOTE] What are the Macros?
>They are a way to write code that generates code to extend Rust syntax

