---
layout: post
title: Rust Memory Safety Mechanisms and a Bit of C
date: 2020-03-13 17:00:00 +0200
categories: Programmieren
tags: [C, Rust, Memory Safety]
---

## Why Memory Safety is Important

Both Google and Microsoft agree that around 70% of all security bugs are memory safety issues.[^1][^2]

But what to do about it? We could avoid potentially memory-unsafe languages like C or C++ in favour of garbage collected languages like Java, which are memory safe. But this comes some disadvantages like a decrease in performance, stalls in program execution, and consuming additional resources.

Rust on the other hand is memory safe, it does not permit null pointers, dangling pointers, or data races, while having none of these disadvantages thanks to its liftime, ownership and borrowing systems. Despite these guarantees, the performance of Rust is comparable to C/C++.[^3]

## Examples

In the following segment, we look at examples of memory-related bugs in C and how safe Rust avoids them.

### Null Pointers

Consider the following code:

```c
#include <stdlib.h>
#include <assert.h>

int main() {
    int *x = NULL;
    assert(*x == 42);
    return 0;
}
```

Obviously, the result is a segmentation fault as we attempt to dereference a null pointer:

```text
Segmentation fault (core dumped)
```

Let's try to rewrite this in Rust:

```rust
use std::ptr;

fn main() {
    let x: *const u8 = ptr::null();
    assert_eq!(*x, 42);
}
```

We get the following compiler error:

```text
   Compiling playground v0.0.1 (/playground)
error[E0133]: dereference of raw pointer is unsafe and requires unsafe function or block
 --> src/main.rs:5:5
  |
5 |     assert_eq!(*x, 42);
  |     ^^^^^^^^^^^^^^^^^^^ dereference of raw pointer
  |
  = note: raw pointers may be NULL, dangling or unaligned; they can violate aliasing rules and cause data races: all of these are undefined behavior
  = note: this error originates in a macro (in Nightly builds, run with -Z macro-backtrace for more info)
```

Pointer dereferencing is always unsafe in Rust, the pointer location might be invalid. Instead of pointers, Rust uses references, which are always valid and thus are never allowed to be null `NULL`. This is how null pointers are avoided in Rust. Next, let's look at how Rust prevents dangling pointers.

### Dangling Pointers

Let's look at the following code in C, which creates a dangling pointer:

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

Rust highly discourages the use of `unsafe` code by both requiring the explicit `unafe` block as well as hiding `unsafe` operations behind the `alloc` module, which we explicity have to `use`. Let's look at the equivalent safe Rust code.

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
  = note: this error originates in a macro (in Nightly builds, run with -Z macro-backtrace for more info)
```

Rust makes use of its ownership system, to catch the bug before actually running the code. At line `2`, `x` is owned by the function main. However, `drop` takes ownership of `x`, which is why we can't borrow `x` later at line `4`.

Let's look at another similar example in C, but with two pointers instead of only one:

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

Again, we see that both `x` and `y` point to the same memory location, which is later invalidated by using `free` on `y`. But after freeing the memory, we try to access the now invalid memory location using the pointer `x`.

```text
a.out: main.c:12: main: Assertion `*x == 1' failed.
Aborted (core dumped)
```

This is a common bug as both `x` and `y` point to the same memory location despite having a different name. Unsafe Rust allows us to introduce the same bug:

```rust
use std::{
    alloc::{alloc, dealloc, Layout},
};

fn main() {
    let layout = Layout::new::<i32>();

    unsafe {
        let x: *mut i32;
        let y = alloc(layout) as *mut i32;
        *y = 1;
        x = y;
        dealloc(y as *mut u8, layout);
        assert_eq!(*x, 1);
    }
}
```

We a the runtime error:

```text
   Compiling playground v0.0.1 (/playground)
    Finished dev [unoptimized + debuginfo] target(s) in 0.46s
     Running `target/debug/playground`
thread 'main' panicked at 'assertion failed: `(left == right)`
  left: `0`,
 right: `1`', src/main.rs:14:9
 ```

Again, the code above looks horrendous by design in order to discourage the use of `unsafe` code. Let's look at the safe version of Rust:

```rust
fn main() {
    let x: &i32;
    {
        let y = Box::new(1);
        x = &y;
    }
    assert_eq!(*x, 1);
}
```

Much better to look at! Instead of explicitly deallocating the memory location, we create `y` in a nested block, where at its end, `y` is automatically deallocated. Because we never use `unsafe`, we have the guarantee that the compiler catches our memory safety bug at compile time:

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

To understand this error, we first have to understand lifetimes and borrowing. First, `x` has to live until the end of the function `main`. But `y` is only valid until the end of the block in which it is declared in, and as soon as the block ends, it is deallocated. We can't borrow something for longer than its lifetime, which is why we get the error above. This way, Rust avoids having references to memory locations that were dropped, also known as dangling pointers.

### Data Races

The following C code counts to 1000000 in two separate threads, but it contains a data race:

```c
#include <assert.h>
#include <pthread.h>

void *increment(void *counter) {
    // Increment counter in secondary thread.
    for (unsigned int i = 0; i < 500000; i++) {
        (*((unsigned int *) counter))++;
    }
    return NULL;
}

int main() {
    unsigned int counter = 0;

    // Create a new thread.
    pthread_t thread_id;
    pthread_create(&thread_id, NULL, increment, (void *) &counter);

    // Increment counter in main thread.
    for (unsigned int i = 0; i < 500000; i++) {
        counter++;
    }

    // Join threads.
    pthread_join(thread_id, NULL);

    // Check if we counted correctly.
    assert(counter == 1000000);

    return 0;
}
```

Because both the main thread and the secondary thread increment `counter`, there may be bad interleavings that lead to a data race. This is why we encounter an assertion failure:

```text
a.out: main.c:27: main: Assertion `counter == 1000000' failed.
Aborted (core dumped)
```

We could again rewrite the same in unsafe Rust as we did in the previous examples, but instead we directly try to implement it in safe Rust.

```rust
use std::thread;

fn main() {
    let mut counter: u32 = 0;

    // Create a new thread.
    let handle = thread::spawn(move || {
        // Increment counter in secondary thread.
        for _ in 0..500000 {
            counter += 1;
        }
    });

    // Increment counter in main thread.
    for _ in 0..500000 {
        counter += 1;
    }

    // Join threads.
    handle.join().unwrap();

    // Check if we counted correctly.
    assert_eq!(counter, 1000000);
}
```

This Program compiles with a warning, and then panicks with an assertion error:

```test
   Compiling playground v0.0.1 (/playground)
warning: unused variable: `counter`
 --> src/main.rs:9:13
  |
9 |             counter += 1;
  |             ^^^^^^^
  |
  = note: `#[warn(unused_variables)]` on by default
  = help: did you mean to capture by reference instead?

warning: 1 warning emitted

    Finished dev [unoptimized + debuginfo] target(s) in 0.97s
     Running `target/debug/playground`
thread 'main' panicked at 'assertion failed: `(left == right)`
  left: `500000`,
 right: `1000000`', src/main.rs:19:5
```

The compiler already noticed the error we made. Instead of passing by reference to the secondary thread, the `move` keyword implicitly copied the `counter` because it has type `u32` which implements `Copy`. Let's try to `move` a reference to the secondary thread instead:

```rust
use std::thread;

fn main() {
    let mut counter: u32 = 0;
    // Create a reference to counter
    // that can be moved into the secondary thread.
    let counter_ref = &mut counter;

    // Create a new thread.
    let handle = thread::spawn(move || {
        // Increment counter in secondary thread.
        for _ in 0..500000 {
            *counter_ref += 1;
        }
    });

    // Increment counter in main thread.
    for _ in 0..500000 {
        counter += 1;
    }

    // Join threads.
    handle.join().unwrap();

    // Check if we counted correctly.
    assert_eq!(counter, 1000000);
}
```

The compiler complains, and rightly so, as our program still contains a data race:

```text
   Compiling playground v0.0.1 (/playground)
error[E0597]: `counter` does not live long enough
  --> src/main.rs:6:23
   |
6  |       let counter_ref = &mut counter;
   |                         ^^^^^^^^^^^^ borrowed value does not live long enough
7  |
8  |       let handle = thread::spawn(move || {
   |  __________________-
9  | |         for _ in 0..500000 {
10 | |             *counter_ref += 1;
11 | |         }
12 | |     });
   | |______- argument requires that `counter` is borrowed for `'static`
...
21 |   }
   |   - `counter` dropped here while still borrowed

error[E0503]: cannot use `counter` because it was mutably borrowed
  --> src/main.rs:15:9
   |
6  |       let counter_ref = &mut counter;
   |                         ------------ borrow of `counter` occurs here
7  |
8  |       let handle = thread::spawn(move || {
   |  __________________-
9  | |         for _ in 0..500000 {
10 | |             *counter_ref += 1;
11 | |         }
12 | |     });
   | |______- argument requires that `counter` is borrowed for `'static`
...
15 |           counter += 1;
   |           ^^^^^^^^^^^^ use of borrowed `counter`

error[E0502]: cannot borrow `counter` as immutable because it is also borrowed as mutable
  --> src/main.rs:20:5
   |
6  |       let counter_ref = &mut counter;
   |                         ------------ mutable borrow occurs here
7  |
8  |       let handle = thread::spawn(move || {
   |  __________________-
9  | |         for _ in 0..500000 {
10 | |             *counter_ref += 1;
11 | |         }
12 | |     });
   | |______- argument requires that `counter` is borrowed for `'static`
...
20 |       assert_eq!(counter, 1000000);
   |       ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^ immutable borrow occurs here
   |
   = note: this error originates in a macro (in Nightly builds, run with -Z macro-backtrace for more info)
```

Many errors are thrown, but let's try to fix the first error, which complains that the borrowed `counter_ref` does not live long enough. We as programmers know that it actually does, because we join the secondary thread before the memory location of `counter` is invalidated. But the Rust compiler can't be sure, and it is conservative, so it throws an error.

We have three options to fix this:

1. Use unsafe.
2. Use a `static` counter with a `'static` lifetime, wich ensures that the borrow checker knows that `counter_ref` is valid for at least as long as the secondary thread is active.
3. Use a reference counter.

Option 1 is not acceptable, because we want to take advantage of the Rust safety guarantees.

Option 2 would be a solution, but because we are good programmers, we know that we should avoid global variables whenever possible, especially if they are mutable in multithreaded contexts.

This is why we choose option 3 and use reference counters, which are provided by Rust with `Rc<T>`:

```rust
use std::{
    thread,
    rc::Rc,
};

fn main() {
    let mut counter: Rc<u32> = Rc::new(0);
    // Clone the reference counter, note that
    // the counter itself is not cloned.
    let counter_clone = counter.clone();

    let handle = thread::spawn(move || {
        // Increment counter in secondary thread.
        for _ in 0..500000 {
            *counter_clone += 1;
        }
    });

    // Increment counter in main thread.
    for _ in 0..500000 {
        *counter += 1;
    }

    // Join threads.
    handle.join().unwrap();

    // Check if we counted correctly.
    assert_eq!(*counter, 1000000);
}
```

We still get an error:

```text
   Compiling playground v0.0.1 (/playground)
error[E0277]: `std::rc::Rc<u32>` cannot be sent between threads safely
   --> src/main.rs:10:18
    |
10  |       let handle = thread::spawn(move || {
    |  __________________^^^^^^^^^^^^^_-
    | |                  |
    | |                  `std::rc::Rc<u32>` cannot be sent between threads safely
11  | |         for _ in 0..500000 {
12  | |             *counter_clone += 1;
13  | |         }
14  | |     });
    | |_____- within this `[closure@src/main.rs:10:32: 14:6 counter_clone:std::rc::Rc<u32>]`
    |
    = help: within `[closure@src/main.rs:10:32: 14:6 counter_clone:std::rc::Rc<u32>]`, the trait `std::marker::Send` is not implemented for `std::rc::Rc<u32>`
    = note: required because it appears within the type `[closure@src/main.rs:10:32: 14:6 counter_clone:std::rc::Rc<u32>]`
```

The compiler complains that `Rc<u32>`  cannot be sent between threads safely, which is reasonable because the counter which keeps track of the references is itself not thread safe. This is why rust also provides us with `Arc<T>`, which an atomic reference counter an thus thread safe:

```rust
use std::{
    thread,
    sync::Arc,
};

fn main() {
    let counter: Arc<u32> = Arc::new(0);
    // Clone the reference counter, note that
    // the counter itself is not cloned.
    let counter_clone = counter.clone();

    let handle = thread::spawn(move || {
        // Increment counter in secondary thread.
        for _ in 0..500000 {
            *counter_clone += 1;
        }
    });

    // Increment counter in main thread.
    for _ in 0..500000 {
        *counter += 1;
    }

    // Join threads.
    handle.join().unwrap();

    // Check if we counted correctly.
    assert_eq!(*counter, 1000000);
}
```

More errors:

```text
   Compiling playground v0.0.1 (/playground)
error[E0594]: cannot assign to data in an `Arc`
  --> src/main.rs:15:13
   |
15 |             *counter_clone += 1;
   |             ^^^^^^^^^^^^^^^^^^^ cannot assign
   |
   = help: trait `DerefMut` is required to modify through a dereference, but it is not implemented for `std::sync::Arc<u32>`

error[E0594]: cannot assign to data in an `Arc`
  --> src/main.rs:21:9
   |
21 |         *counter += 1;
   |         ^^^^^^^^^^^^^ cannot assign
   |
   = help: trait `DerefMut` is required to modify through a dereference, but it is not implemented for `std::sync::Arc<u32>`
```

The problem here is that we can't mutate the contents of `Arc<u32>`, meaning we cannot increment the inner `u32`. To solve this problem, we use a concept called *interior mutability*, that is we mutate a value without actually requiring a mutable reference to it.

This functionality is provided by `Mutex<T>`, which defines the following method:

```rust
pub fn lock(&self) -> LockResult<MutexGuard<T>>
```

Note that `lock` method only requires `&self`, and not `&mut self`. Because multiple references to the same location are allowed as long as they are not mutable, we can use `lock` at multiple points in the code, for example both in the main thread and the secondary thread, without the compiler complaining:

```rust
use std::{
    thread,
    sync::{Arc, Mutex},
};

fn main() {
    let counter: Arc<Mutex<u32>> = Arc::new(Mutex::new(0));
    // Clone the reference counter, note that
    // the counter itself is not cloned.
    let counter_clone = counter.clone();

    let handle = thread::spawn(move || {
        // Increment counter in secondary thread.
        for _ in 0..500000 {
            *counter_clone.lock().unwrap() += 1;
        }
    });

    // Increment counter in main thread.
    for _ in 0..500000 {
        *counter.lock().unwrap() += 1;
    }

    // Join threads.
    handle.join().unwrap();

    // Check if we counted correctly.
    assert_eq!(
        *counter.lock().unwrap(),
        1000000
    );
}
```

Our code finally compiles, which gives us the guarantee that there are no data races, but now we have introduced locking. In this specific example, instead uf using `Mutex<T>`, we could also have used an atomic type `AtomicU32`, such that our code is lock free:

```rust
use std::{
    thread,
    sync::{Arc, atomic::{AtomicU32, Ordering}},
};

fn main() {
    let counter: Arc<AtomicU32> = Arc::new(AtomicU32::new(0));
    // Clone the reference counter, note that
    // the counter itself is not cloned.
    let counter_clone = counter.clone();

    let handle = thread::spawn(move || {
        // Increment counter in secondary thread.
        for _ in 0..500000 {
            counter_clone.fetch_add(1, Ordering::Relaxed);
        }
    });

    // Increment counter in main thread.
    for _ in 0..500000 {
        counter.fetch_add(1, Ordering::Relaxed);
    }

    // Join threads.
    handle.join().unwrap();

    // Check if we counted correctly.
    assert_eq!(
        Arc::try_unwrap(counter).unwrap().into_inner(),
        1000000
    );
}
```

This compliles without errors, which gives us the guarantee that our code contains no more data races.

## References

[^1]: [ZDNet. (2020). Chrome: 70% of all security bugs are memory safety issues](https://www.zdnet.com/article/chrome-70-of-all-security-bugs-are-memory-safety-issues/)

[^2]: [ZDNet. (2019). Microsoft: 70 percent of all security bugs are memory safety issues](https://www.zdnet.com/article/microsoft-70-percent-of-all-security-bugs-are-memory-safety-issues/)

[^3]: [The Computer Language Benchmarks Game. (2020). Rust versus C++.](https://benchmarksgame-team.pages.debian.net/benchmarksgame/fastest/rust-gpp.html)
