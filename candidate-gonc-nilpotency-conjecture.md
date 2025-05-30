# Conjecture: Nilpotency Index Governs Critical Path Depth in Symbolic Task Matrices

## Author: Candidate Gönç  
Submitted for consideration to the [formal-conjectures](https://github.com/google-deepmind/formal-conjectures) repository

---

## 🧮 Problem Context

Let Q \in \mathbb{Z}^{k \times k} be a **strictly lower triangular matrix** of integer task dependencies in a self-replicating project. Each nonzero entry q_{ij} indicates that task j is a requirement for task i, with unit quantity or scaled weight.

---

## 📐 Nilpotency Index

We define the **nilpotency index** j as:

\[
j \in \mathbb{N}
\quad \text{is the greatest integer such that} \quad Q^j \ne 0
\]

This ensures:
\[
Q^{j+1} = 0
\quad \text{and} \quad Q^j \ne 0
\]

The matrix becomes zero after exactly j+1 multiplications, corresponding to the **depth of interdependent task layering**.

---

## 🔁 Execution Phase Derivation

Let \hat{k} denote the unit row vector selecting the final product:

\[
R_i := \hat{k} \cdot Q^i
\quad \text{for } i = 0, 1, ..., j
\]

Each vector R_i corresponds to a **derived stage** — a set of tasks to be executed at phase j - i. The initial product is R_0 = \hat{k}, and the last nonzero derived stage is R_j, which corresponds to the **first tasks to be executed**.

---

## 📊 Technological Ordering and Phase Partitioning

Define:
\[
\text{Indices}(R_i \ne 0) := \left\{ n \in \{1, ..., k\} \mid (R_i)_n \ne 0 \right\}
\]

These represent **technologically ordered partitions**: each set contains only tasks that are **adjacent in dependency and contiguous in execution**.

---

## 🕒 Critical Path Evaluation

Let T \in \mathbb{R}^k be the task time vector. Then, total project duration is:

\[
\text{Total Time} = \sum_{i=1}^{j} \max \left( T_n \mid n \in \text{Indices}(R_i \ne 0) \right)
\]

Each phase executes in parallel; only the **longest task in each phase** determines its duration. The overall time is the sum of those phase maxima — a clear, deterministic measure of critical path length without guessing or search.

---

## ✅ Summary

- No graph expansion is required.
- No zero-row padding is needed.
- The method is **purely symbolic** and **guaranteed to terminate** in j steps.
- The critical path emerges as a **sum over maximum
