---
layout: default
title: "Week 2"
---

# Internship Documentation — Week 2

**Intern:** Swaraj Anil Harne
**Branch:** Computer Science and Engineering (3rd Year)
**Focus Area:** Python Fundamentals (ApexaiQ Training Module)

---

## 1. Overview of the Week

Week 2 moved to the backend side of things with a deep dive into **Python**. This module covered the language from the ground up — starting with basic syntax and data types, moving through control flow and functions, and ending with real-world software practices like coding standards, virtual environments, and APIs.

The training wasn't just about Python syntax — it also touched on the **habits and standards** professional developers follow, which felt just as important as the language itself.

---

## 2. Getting the Basics Right

Every language has rules it won't let you break — that's **syntax**. In Python, a **variable** is just a name we give to a piece of data so we can reuse it later (`name = "value"`), and every variable holds a specific **datatype**:

- **int** — whole numbers like `10` or `-50`
- **float** — decimal numbers like `3.14`
- **string** — text wrapped in quotes
- **list** — an ordered collection that *can* be changed
- **tuple** — an ordered collection that *cannot* be changed once created
- **dict** — pairs of keys and values, like a mini lookup table
- **set** — a collection that only keeps unique values, with no fixed order

### A Quicker Way to Build Lists — Comprehensions
Instead of writing a full loop just to build a list or dictionary, Python allows a one-line shortcut:
```python
squares = [x*x for x in range(10)]          # builds a list
square_dict = {x: x*x for x in range(10)}   # builds a dictionary
```
It does the same job as a loop, just in a much cleaner, more compact way.

---

## 3. Making Decisions & Repeating Tasks

**Conditional statements** let the program choose which path to take:
```python
if condition:
    # runs when true
elif another_condition:
    # runs if the first one failed but this one is true
else:
    # runs when nothing above matched
```

**Loops** handle repetition. A `for` loop steps through a sequence item by item (like a list or a string), while a `while` loop keeps running as long as a condition stays true. Two small but useful keywords control loop behavior:
- `break` — stop the loop immediately
- `continue` — skip the current round and move to the next one

### Iterators & Generators
An **iterator** is anything that lets you move through a collection one item at a time. A **generator** is a lightweight way to build one, using a function with the `yield` keyword instead of `return` — it hands out values one at a time instead of building the whole list in memory upfront, which saves a lot of memory for large datasets.

---

## 4. Functions & Decorators

A **function** is simply a named, reusable chunk of code built to do one job:
```python
def function_name(parameter1, default_param="default"):
    # logic goes here
    return "some value"
```

Two special tools help handle flexible inputs:
- `*args` — gathers any extra positional inputs into a tuple
- `**kwargs` — gathers any extra named inputs into a dictionary

**Decorators** take this a step further — they let you "wrap" one function around another to add extra behavior without editing the original function's code. The `@` symbol is just Python's shorthand for applying this wrap:
```python
@my_decorator
def say_hello():
    print("Hello!")
```

---

## 5. Object-Oriented Programming (OOP)

Instead of writing code as one long list of instructions, OOP organizes it around **objects** — bundles of data and behavior that model real things. A **class** acts as the blueprint, and an **object** is an actual item built from that blueprint.

OOP rests on a few core ideas, often called its pillars:
- **Abstraction** — hiding complex details behind a simple interface
- **Encapsulation** — keeping data and the logic that uses it bundled together
- **Inheritance** — letting one class reuse and extend another
- **Polymorphism** — letting different objects respond to the same action in their own way

---

## 6. Handling Errors Gracefully

No program is bug-free, but **exception handling** stops a single error from crashing the whole application:
```python
try:
    risky_operation()
except ValueError as e:
    print(f"Error caught: {e}")
finally:
    cleanup()
```
The `try` block holds the risky code, `except` catches specific problems, and `finally` runs no matter what — success or failure — which makes it perfect for cleanup tasks.

---

## 7. Packages & Virtual Environments

A **package** is just a folder of related Python files (modules) organized together, usually marked with an `__init__.py` file, which keeps large projects clean and reusable. Python packages generally come in three flavors:
- **Built-in** — ship with Python itself (`os`, `sys`, `math`, `datetime`)
- **Third-party** — built by the community and installed via `pip` (`requests`, `numpy`, `pandas`, `flask`)
- **User-defined** — custom packages written for a specific project

To keep a project's dependencies isolated from the rest of the system, developers use a **virtual environment**:
```bash
python -m venv <NameYourVenv>          # create it
source <NameYourVenv>/bin/activate     # activate it
pip install -r requirements.txt        # install what the project needs
```
This keeps every project's dependencies self-contained, so installing one project's libraries never breaks another.

---

## 8. Writing Professional-Quality Code

Good code isn't just code that runs — it's code other people (and future-you) can actually understand. A few standards that came up:
- **Naming conventions** — `snake_case` for variables/functions, `PascalCase` for classes
- **Docstrings** — describe *what* a function/class/module is for, written right under its definition
- **Comments** — explain the *why* behind tricky lines, using `#`
- **PEP8** — Python's official style guide for consistent formatting

Testing was also covered at three levels:
- **Unit tests** — check one small piece of code in isolation
- **Integration tests** — check that multiple pieces work correctly together
- **End-to-end tests** — check the entire application flow, start to finish

Two design principles tie it all together:
- **DRY (Don't Repeat Yourself)** — never duplicate the same logic in multiple places
- **SOLID** — a set of five principles for writing flexible, maintainable software

---

## 9. Understanding APIs

An **API** is essentially an agreed-upon contract that lets two different software systems talk to each other. A few key building blocks:

- **API styles** — REST, SOAP, and GraphQL are the most common approaches
- **HTTP status codes** — tell you how a request went:
  - `2xx` → success (e.g. `200 OK`)
  - `4xx` → something's wrong on the client's end (e.g. `404 Not Found`)
  - `5xx` → something's wrong on the server's end
- **Response format** — JSON is the modern standard for exchanging data
- **Authentication** — proving who's making the request, commonly via API Keys, OAuth 2.0, or JWTs
- **Versioning** — keeping older API versions (like `/api/v1/`) working even as new ones are released
- **CRUD operations** — the four basic actions any API supports, each mapped to an HTTP method:
  - **Create** → `POST`
  - **Read** → `GET`
  - **Update** → `PUT` / `PATCH`
  - **Delete** → `DELETE`
- **Performance tricks** — caching, rate limiting, and compressing payloads to keep APIs fast
- In Python, the **`requests`** library is the go-to tool for calling APIs directly from code

---

## 10. A Few Extra Concepts Worth Knowing

- **SDLC (Software Development Life Cycle)** — the overall roadmap for building software: plan, design, build, test, deploy, and maintain
- **Agile** — an iterative way of managing projects that focuses on delivering value in small, frequent steps rather than one big release
- **Version Control (Git)** — tracks every change made to code over time, making teamwork and rollback possible
- **Software Architecture** — the big-picture blueprint of a system, with common styles including Monolithic, Microservices, Layered (N-tier), Event-Driven, and Service-Oriented

---

## 11. Key Takeaway from Week 2

Python turned out to be less about memorizing syntax and more about **building good habits** — clean naming, proper testing, isolated environments, and understanding how systems talk to each other through APIs. Combined with the OOP concepts, this week laid the groundwork for writing code that isn't just functional, but maintainable and production-ready — which will matter a lot once real project work begins.
