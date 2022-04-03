---
layout: post
title: How Rusts Expressiveness enables better Performance
date: 2020-12-06 17:00:00 +0100
categories: Programmieren
tags: [Rust, C, Optimization]
description: "A comparison between Rust and C."
---

More expressive languages allow for better transfer of information. This concept is not only true for spoken languages, but also for programming languages.

Programmers in most cases don't write their programs directly in machine language, but they use a higher level language which is better understandable for humans, and then compile this language into a lower level language which is then executed by a computer.

Programs in their core are nothing more than descriptions of how data is manipulated. Thus, to achieve optimal performance for our program, we want to provide the compiler with as much information about how data is manipulated in our program as possible. This is only possible if our programming language is able to express data manipulation in great detail.

Consider the following C program:

```c
void add_two_times(int *a, int *b) {
    *a += *b;
    *a += *b;
}
```

We have two pointers to an integer `a` and `b`. In the function body, we add the value pointed to by `b` to the value pointed to by `a`, twice.

If we compile the code snippet above using `gcc 10.2 -O3`, we get the following assembly output:

```nasm
movl    (%rsi), %eax
addl    (%rdi), %eax
movl    %eax, (%rdi)
addl    (%rsi), %eax
movl    %eax, (%rdi)
ret
```

In the first line, we load `b` into the register `%eax`. Next, we load and add `a` to `%eax`. Nothing suprising until now, but the next step is interesting. Instead of simply loading and adding `b` again as we might expect, We proceed to store `%eax` back into `a`. Then we load `b` again and add it to `%eax`. Finally we store `%eax` back into `a` and we are done.

Our final assemply program which is compiled from C requires 5 load and stores, even with the `-O3` optimization flag enabled. Now let's look at the following Rust program:

```rust
pub fn add_two_times(a: &mut i64, b: &i64) {
    *a += *b;
    *a += *b;
}
```

If we compile the program using `rustc 1.47.0 -C opt-level=3`, we get:

```nasm
movl    (%rsi), %eax
addl    %eax, %eax
addl    %eax, (%rdi)
retq
```

This assembly program simply loads `b`, adds it to itself, and then adds `b` to the value pointed to by `a`. We only require two load and stores. But why is the rust compiler able to generate this much more performant assembly code?

If we look at the C code again, we might assume that because `a` and `b` have different names, they point to different locations, but this does not have to be the case at all. The compiler also has to consider the case where `a` points to the same location as `b`. If we rewrite our program assuming `a == b`, we get:

```c
void add_two_times(int *a) {
    *a += *a;
    *a += *a;
}
```

After the execution of this code, the value pointed to by `a` is essentially multiplied by four. But this is not the result of our assembly code from Rust.

Rust on the other hand can safely assume that `a` and `b` do not alias because `a` is a mutable reference and `b` is an immutable reference. From the Rust borrowing rules, we know that there can never exist both a mutable and an immutable reference to the same location. Thus, the Rust compiler can infer that the first line in our function may only change the value pointed to by `a`, but never the value pointed to by `b`. That's why it's not necessary for the assembly code produced by the Rust compiler to store `a` and load `b` again after executing the first line of the function body.

We learn from this example that because of the additional information known to the Rust compiler, it was able to safely perform more radical optimizations than the C compiler. For programming languages that aim to be as performant as possible, it is crucial to express data manipulation in a precice way.
