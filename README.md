# Orthogonal Lattice Attack on Practical Homomorphic Encryption HE1 and HE1N for Secure Computation in the Cloud
---
This repository provides the **Maple implementation** and **experimental results** for the **Orthogonal Lattice Attack (OLA-MC)**. The attack targets **HE1** and **HE1N**, two novel homomorphic encryption schemes for integer arithmetic introduced by Dyer, Dyer, and Xu in [[1]](https://link.springer.com/article/10.1007/s10207-019-00427-0), designed for secure single-party computation in the cloud.
## 📁 Repository Contents

| File | Description |
|------|-------------|
| `OLA_MC_HE1.mw` | Maple code for OLA-MC on the HE1 scheme |
| `OLA_MC_HE1N.mw` | Maple code for OLA-MC on the HE1N scheme |
| `OLA_MC_HE1_Results.xlsx` | Experimental results for HE1 – each sheet named after input parameters |
| `OLA_MC_HE1N_Results.xlsx` | Experimental results for HE1N – each sheet named after input parameters |

---


## 🧪 Attack Overview
**(OLA-MC)** targets the **HE1** and **HE1N** homomorphic encryption schemes introduced by Dyer, Dyer, and Xu in [[1]](https://link.springer.com/article/10.1007/s10207-019-00427-0) as follows:
**For HE1:**
1. Construct a lattice from $z$ ciphertexts.
2. Apply LLL reduction.
3. Compute the coefficient matrix $\alpha$ and its kernel.
4. Recover the random values $r_i$ via kernel multiplication and a small enumeration $|f_z| \leq 10$.
5. Extract the secret key  $p = \lfloor c_1 / r_1 \rfloor$ and decrypt $m = c - p\cdot r$.

**For HE1N (two-stage attack):**
- **Stage 1:** Apply OLA-MC to recover $r$, the primary key $p$, and the intermediate value $m + s\cdot k$.
- **Stage 2:** Apply OLA-MC again to the intermediate value to recover $s$, the secondary key $k$, and the original message $m$.
---
## 📊 Experimental Results

The **OLA-MC** attack was implemented in **Maple 2024** and tested on a system with an Intel Core i5-8250U CPU (1.60 GHz), 12 GB RAM, running Windows 11 64-bit.


The accompanying Excel files (`OLA_MC_HE1_Results.xlsx` and `OLA_MC_HE1N_Results.xlsx`) contain the **complete raw results for every run**. Each sheet is titled according to the input parameters:
- For HE1: `(d, ρ)` — e.g., `(2,32)`, `(3,64)`, `(4,128)`
- For HE1N: `(d, ρ, ρ')` — e.g., `(3,16,128)`, `(2,8,64)`, `(3,1,32)`

Each sheet reports the distribution of the number of trials (over 100 runs) in which a given $|f_z|$ value (1 through 20) was required for successful recovery, along with the execution time per iteration.
