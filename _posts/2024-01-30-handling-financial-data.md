---
layout: post
title: Handling Financial Data
date: 2024-01-30 18:00:00 +0100
category: Computer Science
description: "How to store and manipulate financial data."
---

When dealing with financial data such as prices, it is common to see `float` or `double` data types being used. This seems fine and works as expected in most cases, however, there are some issues with floating point data types that might lead to bugs in the future.

## The Issue with Floating Point Numbers

Floating point data tries to solve the issue of storing the infinite space of numbers in a finite space of bits. Naturally, this means that there is some approximation going on. Consider the following example that takes a user input and parses it to a `float` to get the price per unit.

```java
String userInput = "4.20";
float pricePerUnit = Float.parseFloat(userInput);
System.out.printf("The price per unit is %.2f%n", pricePerUnit);
// The price per unit is 4.20
```

Seems correct for now. Now we multiply the price per unit times a quantity and compute the total price.

```java
int quantity = 100000;
float totalPrice = pricePerUnit * quantity;
System.out.printf("The total price is %.2f%n", totalPrice);
// The total price is 419999.97
```

We are missing three cents! But why is this?

## How Floating Point Numbers are Stored

Floating point numbers are computed with the formula significand × base<sup>exponent</sup>, where the base is a fixed number, usually two, and the significand and exponent are stored in memory with a fixed amount of bits available. In our case, this means that the number 4.2 has no exact representation in this system. If we print more than two digits after the decimal point, we can see this in the price per unit.

```java
String userInput = "4.20";
float pricePerUnit = Float.parseFloat(userInput);
System.out.printf("The price per unit is %.8f%n", pricePerUnit);
// The price per unit is 4.19999981
```

## How to Store Financial Data Instead

There are multiple ways to deal with this issue, the easiest one in Java is to use `BigDecimal` instead of floating point numbers. A `BigDecimal` consists of an arbitrary precision integer unscaled value and a scale. The scale is the number of digits to the right of the decimal point. However, arbitrary precision also means they are not the best performance and have more memory usage as they require some sort of heap allocation.

If the memory usage or performance of `BigDecimal` is a problem, consider using a primitive integral data type such as `int` or `long` instead, where the number stores the number of cents, rappen or whatever the smallest unit is. This is usually accurate enough if the data is mainly stored but not necessarily manipulated.
