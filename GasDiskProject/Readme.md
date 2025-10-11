# Gas Disk Simulation

This project models a system of interacting **gas disks** in two dimensions using **Monte Carlo Markov Chain (MCMC)** methods.  
It is part of the *Statistical Mechanics* course and aims to study the thermodynamic behavior of a gas composed of finite-size particles subject to excluded volume interactions.

---

## Physical Idea

The system consists of a collection of **hard disks** of radius σ confined within a finite box.  
Each disk interacts with others through a *hard-core repulsion*:  
they cannot overlap, and configurations violating this constraint have infinite potential energy.

### Core Concept

The model represents a **classical system** where the potential energy is defined as:

\[
U = 
\begin{cases}
0, & \text{if no disks overlap,} \\
\infty, & \text{if any pair of disks overlap.}
\end{cases}
\]

As a result, the only accessible configurations are those with **no overlap**.  
The probability of a configuration in equilibrium at temperature \( T \) follows the **Boltzmann distribution**:

\[
P(\text{configuration}) \propto e^{-U / k_B T}.
\]

Since \( U = 0 \) for valid configurations, all allowed states are *equally probable*.  
Thus, the statistical weight of a state depends purely on its **geometric accessibility** — a key idea behind **entropy-driven phase transitions** (e.g., liquid–solid transitions in hard-sphere systems).

---

## Monte Carlo Algorithm

The simulation proceeds by:
1. **Initializing** disks randomly in the box without overlaps.  
2. **Proposing random moves** (small displacements of one disk at a time).  
3. **Accepting or rejecting** the move depending on the overlap condition:
   - If the move causes overlap → reject.  
   - If not → accept (since \( U = 0 \)).  
4. **Repeating** many iterations to sample equilibrium configurations.

The system can then be used to compute:
- Radial distribution functions \( g(r) \)  
- Packing fractions  
- Mean-square displacements  
- Equation of state behavior


