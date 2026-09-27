---
layout: default
title: "Week 3"
---

# Internship Documentation — Week 3

**Intern:** Swaraj Anil Harne
**Branch:** Computer Science and Engineering (3rd Year)
**Focus Area:** Introduction to JavaScript (ApexaiQ Training Module)

---

## 1. Overview of the Week

After spending Week 1 understanding the ApexaiQ product itself, Week 3 shifted focus to **technical upskilling** — starting with a structured training module on **JavaScript**, one of the core languages used in web development. This session covered everything from the very basics of the language to more advanced concepts like closures, promises, and async/await.

The goal wasn't just to learn syntax, but to understand *why* each concept exists and *when* to use it — which will directly help with any front-end or DOM-related tasks later in the internship.

---

## 2. What is JavaScript & Where Does It Run?

JavaScript was created by **Brendan Eich**, originally just to add simple interactivity to the Netscape browser. Today, it's one of the three core technologies of web development, alongside HTML and CSS.

**The classic web dev analogy:**
- **HTML** — the structure (headings, paragraphs, buttons)
- **CSS** — the styling (colors, layout, animations)
- **JavaScript** — the behavior (click actions, form validation, dynamic content)

JavaScript isn't limited to browsers anymore. It runs in three main environments:
- **Browser** — client-side scripting for interactivity and DOM updates
- **Node.js** — server-side scripting for backend apps and APIs
- **Cross-platform** — desktop, mobile, and IoT apps using frameworks built on JS

---

## 3. JavaScript Basics

### Variables
JavaScript gives us three ways to declare a variable, each with different rules:
- **var** — the old way, used until 2015
- **let** — introduced in 2015; must be declared before use and can't be redeclared in the same scope
- **const** — introduced in 2015; can't be redeclared or reassigned, and has block scope

**Rule of thumb:** always declare variables → prefer `const` by default → use `let` only if the value needs to change → use `var` only if you must support very old browsers.

### Data Types
- **String** — text, e.g. `"Apexaiq"`
- **Number** — e.g. `25`, `3.14`
- **Boolean** — `true` / `false`
- **Null** — an intentional empty value
- **Undefined** — declared but not yet assigned
- **Object** — a collection of key-value pairs
- **Array** — an ordered collection of values

### Operators
- **Arithmetic:** `+ - * / %`
- **Comparison:** `== === != < >`
- **Logical:** `&& (AND)  || (OR)  ! (NOT)`
- **Assignment:** `= += -= *= /=`

---

## 4. Control Flow

**Conditional statements** decide *which* block of code runs:
- **if** — runs code if a condition is true
- **else** — runs code if that condition is false
- **else if** — checks a new condition if the first one fails
- **switch** — handles many possible alternative cases at once

**Loops** decide *how many times* code runs:
- **for** — runs a set number of times
- **for/in** — loops through an object's properties
- **for/of** — loops through the values of any iterable (like an array)
- **while** — runs while a condition stays true
- **do/while** — same as `while`, but always runs at least once

---

## 5. Functions

A **function** is a reusable block of code built to perform a specific task, and it only runs when it's called. Key building blocks of a function include:
- **Parameters** — the input values it accepts
- **Return** — the output value it sends back
- **Scope** — where a variable is accessible: **Global** (everywhere), **Local** (inside the function), or **Block** (inside `{}` when using `let`/`const`)

**Types of functions covered:**
1. **Function Declaration** — defined using the `function` keyword; *hoisted*, meaning it can be called before it's defined
2. **Function Expression** — a function stored in a variable; *not hoisted*, so it must be defined before use
3. **Arrow Function (ES6)** — shorter syntax using `=>`; doesn't have its own `this`
4. **Anonymous Function** — a function with no name, often used as a callback
5. **IIFE (Immediately Invoked Function Expression)** — runs automatically right after it's defined
6. **Higher-Order Function** — a function that takes another function as an argument, or returns one
7. **Recursive Function** — a function that calls itself, important in object/class-based logic

---

## 6. Arrays & Objects

**Arrays** are ordered lists of values — they can hold numbers, strings, objects, or even functions. Common array tools:
- `.length` → total number of items
- `.push()` / `.pop()` → add/remove from the end
- `.unshift()` / `.shift()` → add/remove from the start
- `.map()`, `.filter()`, `.reduce()` → process and transform data

**Objects** are collections of key-value pairs, where keys act like labels (always strings/symbols) and values can be anything. Objects support:
- Accessing, adding, updating, and deleting properties
- Methods — functions stored inside an object
- Built-in object methods for common tasks

---

## 7. DOM (Document Object Model)

The **DOM** is what lets JavaScript actually "see" and change a webpage. It represents an HTML page as a **tree of nodes** — elements, attributes, and text — that JavaScript can read and modify.

Why it matters:
- Lets us dynamically update content (text, images, etc.)
- Enables real user interaction (clicks, form input)
- Turns a static webpage into a dynamic, interactive one

**Common DOM manipulation tasks:** selecting elements, changing content, changing style, and creating new elements on the fly.

---

## 8. Event Handling

An **event** is any action that happens in the browser — a click, a keypress, a mouse movement — and JavaScript can "listen" for these events and react to them.

**Commonly used events:**
- `onclick` — element is clicked
- `onmouseover` — mouse hovers over an element
- `onkeydown` / `onkeyup` — a key is pressed or released
- `onsubmit` — a form is submitted
- `onchange` — an input's value changes

---

## 9. Callbacks

A **callback** is simply a function passed into another function, to be run later. This is especially useful for tasks that take time — like reading a file or calling an API — since the code doesn't have to freeze and wait.

**Why callbacks matter:**
- **Reusability** — swap the callback without touching the main function
- **Async handling** — wait for a task to finish before continuing
- **Control flow** — clearly defines what happens once a task completes

---

## 10. Promises

A **Promise** is a special object used to handle asynchronous operations — representing a value that may exist *now, later, or never*. Every promise has one of three states:
- **Pending** — still waiting for the result
- **Fulfilled** — the operation succeeded
- **Rejected** — the operation failed

**Why use Promises?** They avoid the messy nesting of "callback hell," offer cleaner handling through `.then()` and `.catch()`, and can be chained to run multiple async steps in sequence.

---

## 11. Async & Await

**Async/Await** is modern syntax built on top of Promises that makes asynchronous code *look and behave* like normal, step-by-step synchronous code.
- `async` → marks a function that will return a Promise
- `await` → pauses execution until that Promise resolves or fails

**Why it's preferred:** cleaner, more readable code, no more chaining `.then()` calls, and simple error handling using `try...catch` — making it the modern best practice for handling asynchronous tasks.

---

## 12. Closures

A **closure** happens when a function "remembers" variables from its outer scope, even after that outer function has already finished running. This happens automatically whenever a function is defined inside another function.

**Why closures are useful:**
- **Data privacy** — variables stay hidden and can't be accessed directly from outside
- **Encapsulation** — only specific functions get access to the hidden variables
- **Stateful functions** — perfect for counters, caching, and event handlers
- **Functional programming** — forms the foundation of many advanced JS patterns

---

## 13. Key Takeaway from Week 3

This week built the core JavaScript foundation needed for real development work — from variables and control flow, all the way to asynchronous programming and closures. The biggest shift in understanding was around **asynchronous behavior**: callbacks, promises, and async/await all solve the same underlying problem — handling tasks that take time — just with progressively cleaner syntax. This concept will be essential going forward, especially once real API calls and DOM-driven features come into play.
