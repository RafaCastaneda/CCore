# CCore Programming Language

[![Join the chat at https://gitter.im/ccore-lang/Lobby](https://badges.gitter.im/ccore-lang/Lobby.svg)](https://gitter.im/ccore-lang/Lobby?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

CCore is a programming language for .NET Core

## Features

* Nullability and mutability tracking in the type system.

* Pervasive values, any class can be allocated in the heap or in the stack, and ownership tracking with move semantics.
Value ADTs and pattern-matching.

* try-match error handling based on values (typically ADTs).

* Explicit differentiation of values from references with lifetime tracking.

* Language built-in RAII-like resource management for external resources and automatic clearing of managed references.

* Object-Oriented with strictly only interface inheritance, and implementation reuse by mix-in composition.

* Strict separation of class interface and implementation.

* Structured concurrency.

* Built-in native interop and unsafe code.

## Objective

To experiment how all this features work together to make a middle level (lower level than C# but not native) and convenient language, so as to be applicable for high performance networking and web services, games, low latency audio synthesis, signal processing, scientific computing, etcetera.
