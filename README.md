# 📘 EquFinder Recursive OOP

### *A Recursive, Extensible Expression Solver Demonstrating Strong OOP & Algorithmic Problem-Solving*

EquFinder Recursive OOP is a fully object-oriented expression solver that evaluates **all permutations and operation combinations** of a given set of values to reach a desired target. If an exact match cannot be produced, the solver returns the **closest possible expression**.

This project is designed not only as a functional solver, but also as a demonstration of:

* Clean, extensible **OOP architecture**
* Effective use of **polymorphism**
* Robust **recursive search & backtracking**
* Designing domain-specific operations for multiple value types
* Algorithmic thinking and performance-aware recursive traversal

It is ideal for showcasing **software engineering fundamentals**, **design principles**, and **problem-solving depth**.

---

## 🚀 Key Highlights

* Supports multiple custom value types:

  * **IntegerValue**
  * **StringValue**
  * **MonthValue** (with modular month arithmetic)
* Each type fully defines its own:

  * `addition`
  * `subtraction`
  * `multiplication`
  * `distance` (used for closest-match logic)
* Full permutation generation (`n!`)
* Full operator sequence generation (`3^(n-1)`)
* Recursive evaluation with backtracking
* Returns **exact expression** or **closest expression**
* Clean architecture designed for easy future extension

---

## 🧱 Architecture Overview

```
valueSolverPack/
 ├── Value.java                     → Abstract base class for all value types
 ├── IntegerValue.java              → Integer operations (+, -, *)
 ├── StringValue.java               → Custom string operations
 ├── MonthValue.java                → Month-based arithmetic using an enum
 ├── Months.java                    → Enumeration for months (1–12)
 └── RecursiveSolver.java           → Core recursive expression solver
Test.java                           → Example usage
```

This structure demonstrates:

* Strong abstraction
* Clear type boundaries
* Reusable and maintainable design
* Easy addition of new value types without modifying existing logic (Open/Closed Principle)

---

## 🧠 How the Recursive Solver Works

### 1. Generate All Permutations

Every ordering of the input values is explored.

### 2. Try All Operator Combinations

For each step, three operations are possible:

```
+   -   *
```

### 3. Build Expressions Recursively

The solver:

* Takes the next value
* Applies each operation
* Builds an expression string dynamically
* Uses backtracking to explore all possibilities
* Tracks exact matches
* Tracks the closest expression when no exact match exists

### 4. Returns the Best Expression

* Exact match → returned immediately
* No exact match → returns expression with minimal distance

---

## 🧮 Example Usage

```java
Value v1 = new IntegerValue(11);
Value v2 = new IntegerValue(7);
Value v3 = new IntegerValue(12);
Value v4 = new IntegerValue(6);
Value[] arr = { v1, v2, v3, v4 };

Value target = new IntegerValue(41);

RecursiveSolver solver = new RecursiveSolver(arr, target);
System.out.println(solver.findExpression());
```

Example Output:

```
Result: (((11+7)+12)+6) -> 41
Execution time: 5.3 ms
```

---

## 🔤 Custom String Operations

| Operator | Behavior                                                   |
| -------- | ---------------------------------------------------------- |
| `+`      | Concatenation                                              |
| `-`      | Removes occurrences of the right-hand string from the left |
| `*`      | Expands the left string using characters from the right    |

These operator overloads demonstrate how custom semantics can be encoded per type using polymorphism.

---

## 📅 MonthValue Type

`MonthValue` applies cyclic (modular) arithmetic to months.

Example:

```
APRIL (4) + OCTOBER (10) = FEBRUARY (2)
```

---

## 🎯 Closest Expression Logic

If no exact result is found, the solver uses each value type’s `distance()` method to determine which expression is mathematically or contextually closest to the target.

This mimics real-world solver behavior where imperfect solutions must be ranked.

---

## 🧩 Extensibility (OOP Focus)

To add a new value type:

1. Extend `Value`
2. Implement:

   * `addition`
   * `subtraction`
   * `multiplication`
   * `distance`
3. Done — the solver automatically supports it
   (demonstrates adherence to the **Strategy Pattern** and **Open/Closed Principle**)

---

## 👨‍💻 Engineering Focus

This repository highlights:

* Recursive problem-solving
* Backtracking algorithms
* Polymorphism and abstraction
* Writing extensible class hierarchies
* Performance-conscious recursion
* Clean design and maintainability

Perfect for demonstrating engineering fundamentals to recruiters or interviewers.

---

## 🛣 Future Improvements

* [ ] Add division operator
* [ ] Parallelize recursive search
* [ ] Add expression tree representation
* [ ] Build a graphical interface
* [ ] Add unit test suite

---

## 📄 License

MIT License
