---
layout: post
title: Dangerous Things in C and how Rust Disallows them
date: 2020-03-13 17:00:00 +0200
categories: Programmieren
tags: [C, Rust, Memory Safety]
---

## Why Memory Safety is Important

Both Google and Microsoft agree that around 70% of all security bugs are memory safety issues.[^1][^2]

But what to do about it? We could avoid potentially memory-unsafe languages like C or C++ in favour of garbage collected languages like Java, which are memory safe. But this comes some disadvantages like a decrease in performance, stalls in program execution, and consuming additional resources. Rust on the other hand is memory safe while having none of these disadvantages thanks to its liftime, ownership and borrowing systems.

## Examples

In the following segment, we look at examples of memory-related bugs in C and how safe Rust avoids them.

### Freeing Memory while still in Use

Let's look at the following code in C:

```c
#include <stdlib.h>
#include <assert.h>

int main() {
    int *x = malloc(sizeof(int));
    *x = 1;
    free(x);
    assert(*x == 1);
    return 0;
}
```

Immediately we see that we free `x` but later try to dereference it. Running the code leads to the following error:

```text
a.out: main.c:8: main: Assertion `*x == 1' failed.
Aborted (core dumped)
```

Rust gives us the power to do the same, but we have to explicity mark the code as `unsafe`, because the functions `alloc` and `dealloc`, as well as dereferencing pointers, are all `unsafe` operations.

```rust
use std::alloc::{alloc, dealloc, Layout};

fn main() {
    let layout = Layout::new::<i32>();

    unsafe {
        let x = alloc(layout) as *mut i32;
        *x = 1;
        dealloc(x as *mut u8, layout);
        assert_eq!(*x, 1);
    }
}
```

Because we made use of `unsafe` code, we opt out of Rusts memory safety guarantees, which is why we encounter the following runtime error:

```text
Compiling playground v0.0.1 (/playground)
    Finished dev [unoptimized + debuginfo] target(s) in 0.45s
     Running `target/debug/playground`
thread 'main' panicked at 'assertion failed: `(left == right)`
  left: `0`,
 right: `1`', src/main.rs:10:9
```

Rust highly discourages the use of `unsafe` code, by both requiring the explicit `unafe` block as well as hiding `unsafe` operations behind the `alloc` module, which we explicity have to `use`. Let's look at the equivalent safe Rust code.

```rust
fn main() {
    let x = Box::new(1);
    drop(x);
    assert_eq!(*x, 1);
}
```

This code is much cleaner. It has no explicit `unsafe` blocks, as Rust is implicity memory safe. Furthermore, `Box` is available without requiring a `use`, contrary to `alloc` and `dealloc`. This how Rust encourages us to write memory safe code by default.

As we don't use any `unsafe`, Rust guarantees us memory safety. Concretely, this means that our bug is catched at compile time:

```text
   Compiling playground v0.0.1 (/playground)
error[E0382]: borrow of moved value: `x`
 --> src/main.rs:4:5
  |
2 |     let x = Box::new(1);
  |         - move occurs because `x` has type `std::boxed::Box<i32>`, which does not implement the `Copy` trait
3 |     drop(x);
  |          - value moved here
4 |     assert_eq!(*x, 1);
  |     ^^^^^^^^^^^^^^^^^^ value borrowed here after move
  |
  = note: this error originates in a macro (in Nightly builds, run with -Z macro-backtr`ace for more info)
```

Rust makes use of its ownership system, which allows the compiler to catch bugs at compile time. At line `2`, `x` is owned by the function main. However, `drop` takes ownership of `x`, which is why we can't borrow `x` later at line `4`.

## Ownership and References

Let's look at the following similar example in C:

```c
#include <stdlib.h>
#include <assert.h>

int main() {
    int *x;

    int *y = malloc(sizeof(int));
    *y = 1;
    x = y;
    free(y);

    assert(*x == 1);
}
```

Again, we see that both `x` and `y` point to the same memory location, which is later invalidated by using `free` on `y`. But after freeing the memory, we try to access the now invalid memory location using the pointer `x`

```text
a.out: main.c:12: main: Assertion `*x == 1' failed.
Aborted (core dumped)
```

This is a common bug as both `x` and `y` point to the same memory location despite having a diffrent name.

Unsafe Rust allows us to reproduce the same bug:

```rust
use std::{
    alloc::{alloc, dealloc, Layout},
    mem::MaybeUninit,
};

fn main() {
    let layout = Layout::new::<i32>();

    unsafe {
        #[allow(unused_assignments)]
        let mut x = MaybeUninit::<*mut i32>::uninit().assume_init();

        let y = alloc(layout) as *mut i32;
        *y = 1;
        x = y;
        dealloc(y as *mut u8, layout);

        assert_eq!(*x, 1);
    }
}
```

Again, the code above looks horrendous by design in order to discourage the use of `unsafe` code. Let's look at the safe version of Rust:

```rust
fn main() {
    #[allow(unused_assignments)]
    let mut x = &0;
    {
        let y = Box::new(1);
        x = &y;
    }
    assert_eq!(*x, 1);
}
```

Much better to look at! And we even have the guarantee that the compiler catches our memory safety bug:

```text
   Compiling playground v0.0.1 (/playground)
error[E0597]: `y` does not live long enough
 --> src/main.rs:6:13
  |
6 |         x = &y;
  |             ^^ borrowed value does not live long enough
7 |     }
  |     - `y` dropped here while still borrowed
8 |     assert_eq!(*x, 1);
  |     ------------------ borrow later used here
```

To understand this error, we first have to understand lifetimes and borrowing. First, `x` has to live until the end of the function `main`. But `y` is only valid until the end of the block it is declared in, as soon as the block ends, it is dropped (or freed, in C slang). We can't borrow something for longer than it lives, which is why we get the error above. This avoids having a reference to a memory location that is invalid.

On a quick note, safe Rust disallows uninitialized variables, which is why we use `MaybeUninit` in the unsafe version, and set `x` to `&0` in the safe version. Note that the value `0` can be arbitrary as we later set `x = y` anyway. This is also why we denote the line with `#[allow(unused_assignments)]`. A more ideomatic way to write this in Rust would be:

```rust
fn main() {
    let x: &i32 = {
        let y = Box::new(1);
        &y
    };
    assert_eq!(*x, 1);
}
```

We can directly assign `x` to the output of the block that is `&y`.

## References

[^1]: [Chrome: 70% of all security bugs are memory safety issues](https://www.zdnet.com/article/chrome-70-of-all-security-bugs-are-memory-safety-issues/)

[^2]: [Microsoft: 70 percent of all security bugs are memory safety issues](https://www.zdnet.com/article/microsoft-70-percent-of-all-security-bugs-are-memory-safety-issues/)