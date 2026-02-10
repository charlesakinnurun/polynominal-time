# Polynomial‑Time

**Explanation of Polynomial Time Complexity (O(nᵏ))**

This repository provides examples and explanations related to **polynomial time complexity** — a broad class of algorithmic time complexities where the running time grows as a polynomial function of the input size.

---

## 📊 What Is Polynomial Time (O(nᵏ))?

In algorithm and complexity analysis, an algorithm runs in **polynomial time** if its time complexity can be expressed as:


for some positive constant `k`, where:

- **T(n)** is the algorithm’s running time as a function of the input size `n`
- **O(...)** is Big‑O notation, showing the growth rate
- **k** is a fixed constant exponent that does *not* depend on `n`

This means the running time grows at most as some power of `n`. Many common algorithm complexities like O(n), O(n²), and even O(nᵌ) are all **polynomial time**. 

---

## 🧠 Why Polynomial Time Matters

Algorithms that run in polynomial time are generally considered **efficient and feasible** for practical input sizes. In theoretical computer science, the class of problems solvable in polynomial time on a deterministic machine is called **P**, and problems in P are often called *tractable*.

Polynomial time is a baseline for algorithm efficiency — while algorithms with higher growth rates like exponential or factorial time become impractical for large inputs, polynomial‑time algorithms remain much more scalable. 

---

## 📌 Typical Polynomial Time Examples

Common algorithm time complexities that are polynomial include:

- **Linear Time — O(n)** — scales in direct proportion with input size  
- **Quadratic Time — O(n²)** — often comes from nested loops  
- **Cubic Time — O(n³)** — deeper nested operations  
- **Other Polynomial Degrees — O(nᵏ)** — where `k` is any fixed number  

These are examples of how *polynomial* time can cover many different growth rates. 

---

## 📁 Source Code

```python
import time
import math

"""
================================================================================
UNDERSTANDING POLYNOMIAL TIME (P)
================================================================================

In computational complexity theory, Polynomial Time refers to an algorithm 
whose running time T(n) is upper-bounded by a polynomial expression in the 
size of the input (n).

Mathematically, T(n) = O(n^k) for some constant k.

Why is this important?
- Algorithms in P are generally considered "efficient" or "tractable."
- If an algorithm is NOT in P (e.g., Exponential Time O(2^n)), it quickly 
  becomes impossible to run even on the world's fastest supercomputers as 
  n grows.
================================================================================
"""

def constant_time_demo(data):
    """
    O(1) - Constant Time
    Technically a polynomial of degree 0 (n^0).
    The execution time remains the same regardless of input size.
    """
    # Accessing an index is always the same speed
    return data[0] if data else None


def linear_time_demo(data):
    """
    O(n) - Linear Time
    A polynomial of degree 1 (n^1).
    If the input size doubles, the time taken roughly doubles.
    """
    count = 0
    for item in data:
        count += 1
    return count

def quadratic_time_demo(data):
    """
    O(n^2) - Quadratic Time
    A polynomial of degree 2.
    Common in nested loops (e.g., Bubble Sort, checking all pairs).
    If input size doubles, time increases by 4x.
    """
    iterations = 0
    for i in data:
        for j in data:
            iterations += 1
    return iterations


def cubic_time_demo(data):
    """
    O(n^3) - Cubic Time
    A polynomial of degree 3.
    Common in basic matrix multiplication.
    """
    iterations = 0
    for i in data:
        for j in data:
            for k in data:
                iterations += 1
    return iterations

def exponential_time_warning(n):
    """
    O(2^n) - Exponential Time (NOT POLYNOMIAL)
    This is NOT in P. The time doubles with every single increment of n.
    Polynomials have the variable in the base (n^k), 
    Exponentials have the variable in the exponent (k^n).
    """
    # This is just a theoretical representation
    total_operations = 2 ** n
    return total_operations


def run_comparison():
    # We will test with a small n because O(n^3) grows quickly
    sizes = [10,100,500]

    print(f"{"Input Size (n)":<15} | {"O(n):<12"} | {"O(n^2)":<12} | {"O(n^3)":<12}")
    print("-" * 60)

    for n in sizes:
        linear = n
        quadratic = n**2
        cubic = n**3
        print(f"{n:<15} | {linear:<12} | {quadratic:12} | {cubic:<12}")


    print("----- Efficiency Wall -----")
    n_large = 100
    print(f"When n = {n_large}:")
    print(f"Polynomial O(n^2): {n_large**2:,} operations (Easy for computers)")

    # Calculate exponential for comparison
    try:
        expo = 2 ** n_large
        print(f"Exponential O(2^n): {expo:,} operations")
        print("Note: 2^100 is more than the estimated number of atoms in the universe!")
        print("This is why being in 'Polynomial Time' is the benchmark for practical software.")
    except OverflowError:
        print("O(2^n): Too large to even calculate!")


if __name__ == "__main__":
    run_comparison()
```

