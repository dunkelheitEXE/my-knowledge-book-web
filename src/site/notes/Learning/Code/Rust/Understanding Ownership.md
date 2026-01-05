---
{"dg-publish":true,"permalink":"/learning/code/rust/understanding-ownership/"}
---

## 📚The stack and the heap

Both are available parts of memory, however both work different, they are structured different

- **The stack**: It follow a way to push in and get out data called *"lats in, first out"*:

>[!QUOTE]
>Think of a stack of plates: when you add more plates, you put them on top of the pile, and when you need a plate, you take one off the top.

## 🖋️Practial use

This  string is different to the common that we have been seeing until this moment. To difference with `let s = "Hi"` (String literals), `String` type is very compatible with the way that the heap stores data, **because its value can be modified (mutable) at running time**, instead of **harcode in compiling time**:

```rust
fn main () {
	let s = String::from("");
	
	s.push_str("Hi");
}
```

### Importance of Scope:

Based on Rust documentation

>[!QUOTE]
>it’s our responsibility to identify when memory is no longer being used and to call code to explicitly free it, just as we did to request it. Doing this correctly has historically been a difficult programming problem. If we forget, we’ll waste memory. If we do it too early, we’ll have an invalid variable. If we do it twice, that’s a bug too. We need to pair exactly one `allocate` with exactly one `free`.
>
>Rust takes a different path: **the memory is automatically returned once the variable that owns it goes out of scope**. Here’s a version of our scope example from Listing 4-1 using a `String` instead of a string literal

**Here is an example**

```rust
{
	let s = String::from("hello"); // s is valid from this point forward
	// do stuff with s
}                                  // this scope is now over, and s is no
								   // longer valid
```

There is a natural point at wich we can return the memory our `string` needs to the allocator.

>[!QUOTE]
>... when `s` goes out of scope. When a variable goes out of scope, Rust calls a special function for us. This function is called [`drop`](file:///home/alangrajeda/.rustup/toolchains/stable-x86_64-unknown-linux-gnu/share/doc/rust/html/std/ops/trait.Drop.html#tymethod.drop), and it’s where the author of `String` can put the code to return the memory. Rust calls `drop` automatically at the closing curly bracket.

To continue, we are going to see some situations where we can find this way to code helpful.

### Variables and Data Interacting with Move

Multiple variables can interact with the same data in different ways in Rust. Let's take a look at this example

```rust
let x = 5;
let y = x
```

Here we are setting value of 5 to `x` and then, we copy that in `y`. This works perfectly because the `integers` values have a known fixed size and these two 5 values are pushed onto the stack.

Now, let's see with `string` type

```rust
let s1 = String::from("hello");
let s2 = s1;
```

We can assume that this example works in the same way that `integers` do, but this is not like that

Here we have what exactly happens with a String. It is composed of three parts:

- A pointer to the memory that holds the content of the string, a *length* and a *Capacity*. This group of data will be stored in the stack, in the right side we can see data stored on the heap

![Pasted image 20251222161307.png](/img/user/Learning/Code/Rust/Pasted%20image%2020251222161307.png)

*Figure 1. Representation in memory of  `String` type holding `"hello"`*

>[!QUOTE] From rust docs
>The length is how much memory, in bytes, the contents of the `String` are currently using. The capacity is the total amount of memory, in bytes, that the `String` has received from the allocator. The difference between length and capacity matters, but not in this context, so for now, it’s fine to ignore the capacity.
>
>When we assign `s1` to `s2`, the `String` data is copied, meaning we copy the pointer, the length, and the capacity that are on the stack. We do not copy the data on the heap that the pointer refers to. In other words, the data representation in memory looks like Figure 4-2. (In this guide, we are using *Figure 2*).

![Pasted image 20251222161745.png](/img/user/Learning/Code/Rust/Pasted%20image%2020251222161745.png)

*Figure 2. Representation in memory of the variable `s2` that has a copy of the pointer, length, and capacity of `s1`*

