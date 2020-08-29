---
layout: post
title: Rust Memory Management
date: 2020-03-13 17:00:00 +0200
categories: Programmieren
tags: [Rust, Memory]
---

||||
|---|---|---|
||Immutable|Mutable|
|Single-Threaded|||
|Multi-Threaded|`Send`|`Send + Sync`|

||||
|---|---|---|
||Immutable|Mutable|
|Single-Threaded|`T`|`RefCell<T>`|
|Multi-Threaded|`Arc<T>`|`Arc<Mutex<T>>`|