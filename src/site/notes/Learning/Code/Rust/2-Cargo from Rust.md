---
{"dg-publish":true,"permalink":"/learning/code/rust/2-cargo-from-rust/"}
---

## What is Cargo?

Cargo is the Rust's build system and package manager, you will be able to install any library or dependency using this tool. Also, it handle a lot if tasks for you, such as download all libraries or *dependencies* that you code needs.

Execute to know the version

```shell
cargo --version
```

If you **do not** see anything, go to [https://rust-lang.org/tools/install/](https://rust-lang.org/tools/install/)

## Create a Project with Cargo

```shell
cargo new your-project-name
cd your-project-name
```

After that, list your files into this directory using ``ls`` (Linux, MAC, Windows).

By default, cargo project comes with a ``.git`` directory. You can use another type of version controller. Also, you can delete that and manage your own repository.

Also you will be able to see ``cargo.toml`` and a directory named ``src``, where you can find your ``main.rs``

## Running your cargo project

This command compile and build a binary (or executable in windows case) that you can run

```shell
# In the root dir where you have your cargo.toml
cargo build
```

Then, you will be able to run it:

```shell
./target/debug/hello_cargo
```

Instead of this, you just can run:

```shell
cargo run
```

and your project will be compiled, built and run

The last one, you must know this command because it shows you if your program compiles without build a binary file

```shell
cargo check
```

### Build in release

Finally, when you current version of your project feels done, you can build with ``cargo build --release``. This command builds the executable/binary with optimizations.

## Cargo as tool to create big projects

Cargo makes easy for you build and maintain big apps or projects, with a bunch of simple commands, you will clone and create a whole project in your own machine

```console
git clone example.org/someproject
cd someproject
cargo build
```

