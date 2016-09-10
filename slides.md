class: center, middle

# Definite Assignment and Local Functions

---

# Agenda

1. Review of definite assignment

1. Theoretical foundations

1. How are local functions different?

1. Algorithm for local functions

1. Proof of correctness

1. Roslyn Implementation

---

# What is definite assignment?

- Tracks when a variable is assigned
        
- Form of _dataflow analysis_:

    - Tracking of state across the control flow of the program

    - In this case, state = assignment

### _Meet on all paths:_

A variable is _definitely assigned_ at a particular
point when the variable is assigned in all branches leading to that point

---

# Definite Assignment

- Given a control flow graph, data "flows" along the edges of that graph, e.g.

<img src="dataflow1.png" style="width: 500px; height: 300px; display:block; margin: auto;" />

- All assignment paths "meet" at `x++`
    - The set of definitely assigned variables is the _intersection_ of the paths

---

# Definite Assignment Equations

<img src="dataflow2.svg" style="display:block; margin: auto;" />

- In other words, statement assignments are the intersection of all predecessors
  until a fixed point is reached
    - _forward-must_ analysis: Data flows _forward_ on every branch and _must_ be
      available on every branch to be available at _in(s)_

---

# 