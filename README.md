# Primal Simplex Algorithm Implementation in Linear Programming

> Academic project developed for the **Operations Research** course  
> Faculty of Applied Sciences

---

## Table of Contents

1. [Overview](#overview)
2. [Authors](#authors)
3. [Theoretical Background](#theoretical-background)
4. [Validation System](#validation-system)
5. [Technologies & Architecture](#technologies--architecture)
6. [Usage Guide](#usage-guide)
7. [License](#license)

---

## Overview

A computational application for solving **linear optimization problems** using the Primal Simplex Algorithm. It facilitates understanding of the computation process through:

- Step-by-step generation of Simplex tableaux (T₀, T₁, …)
- Rigorous validation of the optimal solution based on mathematical convergence criteria

🔗 **[Open Application](https://algoritm-simplex-ildd.streamlit.app/)**

> **Note:** All in-code comments are written in **Romanian**.

---

## Authors

| Name | Group |
|------|-------|
| Dedu Anișoara-Nicoleta | 1333a |
| Dumitrescu Andreea Mihaela | 1333a |
| Iliescu Daria-Gabriela | 1333a |
| Lungu Ionela-Diana | 1333a |

---

## Theoretical Background

The algorithm follows the canonical steps of the Simplex method, with pre-processing and post-processing for validation.

### A. Conversion to Standard Form

**Rule R1 — Variable Sign Restrictions**  
Handles sign-restricted variables (`xⱼ ≥ 0`, `xⱼ ≤ 0`) and free variables through substitutions of the form `x = x' − x''`.

**Rule R2 — Positivity of Right-Hand Side**  
Adjusts the vector `b` so that `bᵢ ≥ 0` by multiplying the corresponding constraints by `-1` and reversing the inequality direction.

**Slack and Artificial Variables**  
Introduces auxiliary variables and the *Big-M method* to penalize artificial variables in MIN problems or in constraints of type `≥` and `=`.

### B. Optimality Criterion and Pivoting

| Step | Description |
|------|-------------|
| Pivot column selection | Variable with the largest reduced cost `Δⱼ` (MAX) or smallest (MIN) |
| Minimum ratio criterion | Determines the pivot row to maintain basic feasibility |
| Gauss-Jordan pivoting | Updates the tableau to move to an adjacent basis |

---

## Validation System

The final validation module confirms the correctness of the results through three fundamental criteria:

### ✅ V1 — Optimality Criterion
Verifies the sign of the reduced cost vector `Δⱼ` with respect to the objective function type (MAX/MIN).

### ✅ V2 — Objective Function Check
Reconstructs the value `f(x)` through direct computation:

```
Z = Σ cⱼ · xⱼ
```

The result is compared against the value in the final tableau.

### ✅ V3 — Matrix Relation Check
Validates the fundamental relationship between the initial and final solutions using the transfer matrix `S` (the matrix of final basis columns from the initial tableau):

```
X_B(I₀) = S · X_B(I_stop)
```

---

## Technologies & Architecture

| Component | Technology |
|-----------|------------|
| Core Engine | Python 3.x — NumPy (matrix computation), Pandas (data structuring) |
| Didactic Display | `fractions.Fraction` — converts decimal results to fractions for manual verification |
| Frontend | Streamlit — reactive interface with Dark/Light mode support |

---

## Usage Guide

**Step 1 — Configuration**  
Set the number of variables and constraints.

**Step 2 — Data Input**  
Enter the objective function coefficients and the constraint matrix elements.

**Step 3 — Constraints**  
Choose the logical operator (`≤`, `≥`, `=`) and the non-negativity bounds for each variable.

**Step 4 — Processing**  
Click **"Calculate Solution"** to trigger the Simplex iterations, displaying each intermediate tableau (T₀, T₁, …).

**Step 5 — Final Report**  
Consult the validation section for mathematical confirmation of the optimum.

---

## License

© 2024 — Dedu A., Dumitrescu A., Iliescu D., Lungu D.

Developed for academic purposes. Use of the code for educational purposes is permitted with **proper attribution to the authors**.
