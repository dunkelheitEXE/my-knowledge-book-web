---
{"dg-publish":true,"permalink":"/learning/code/rust/introduction/"}
---

## First Steps

To create a new project in rust, you have to run ``cargo new <project-name>``. This command will create a rust project:

```bash
project
|--cargo.toml
|--src
   |--main.rs
...
```

#### ``cargo.toml``

This file will contain metadata that will used in the project, like libraries, versions, packages, etc.

#### ``src/``

This will contains al resources that will be used in the project, those can be codes or other files.

#### ``main.rs``

Main code of the program

### Run your first program

In root path, you have to run ``cargo run``. When you create a first project, code has a ``hello world`` program. This must be the exit:

```bash
cargo run
    Finished `dev` profile [unoptimized + debuginfo] target(s) in 0.01s
     Running `target/debug/SolanaToken`
Hello, world!
```

### Add Dependencies

In this section, we will see how to add dependencies to our rust projects. To find dependencies, you have to visit [https://crates.io/](https://crates.io/), this web site brings us a lot of libraries that we can use in our rust projects.

To this example, we will be using ``ferris-says``. We will write this line in ``cargo.toml``, in ``dependencies`` section:

```toml
[dependencies]
...
ferris-says = "0.3.2"
```

Also you can run this in terminal:

```bash
cargo add ferris-says
```

#### To use

```rust
use ferris_says::say;
use std::io::{stdout, BufWriter};

fn main() {
    let out = stdout();
    let message = String::from("Hello, World!");

    let width = message.chars().count();
    let mut writer = BufWriter::new(out.lock());
    say(&message, width, &mut writer).unwrap();
}
```

**Exit**:

```shell
_______________
< Hello, World! >
 ---------------
        \
         \
            _~^~^~_
        \) /  o o  \ (/
          '_   -   _'
          / '-----' \
```
