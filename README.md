# Finite Element Method for the 1D Heat Equation

This repository implements a **continuous Galerkin finite element method (CG-FEM)** for solving the **one-dimensional heat equation**, with both **explicit (Forward Euler)** and **implicit (Backward Euler)** time integration schemes.

The project was developed as a final project for a Computational Engineering course and emphasizes:
- weak (variational) formulations,
- element-level matrix assembly,
- Gaussian quadrature,
- and stability/accuracy behavior of time-integration methods.

---

## Problem Description

We consider the 1D heat equation on the unit domain:

$$
\frac{\partial u}{\partial t} - \frac{\partial^2 u}{\partial x^2} = f(x,t),
\quad x \in [0,1], \; t \in [0,1]
$$

with Dirichlet boundary conditions

$$
u(0,t) = 0, \quad u(1,t) = 0
$$

and initial condition

$$
u(x,0) = \sin(\pi x).
$$

The forcing term is chosen so that the **analytic solution** is

$$
u(x,t) = e^{-t}\sin(\pi x),
$$

which enables direct validation of the numerical method.

---

## Numerical Method

### Spatial Discretization
- Continuous Galerkin (CG) finite element method
- Linear Lagrange basis functions
- Uniform 1D mesh
- Element-level mass and stiffness matrices assembled via reference-element mapping
- Two-point Gaussian quadrature for all integrals

### Time Integration
Two time-stepping schemes are implemented and compared:

- **Forward Euler (explicit)**
  - Conditionally stable
  - Exhibits strong time-step restrictions tied to mesh size
- **Backward Euler (implicit)**
  - Unconditionally stable
  - Introduces numerical diffusion for large time steps

---

## Key Results

- Forward Euler becomes unstable when the time step exceeds a mesh-dependent stability limit.
- Refining the spatial mesh tightens the explicit stability constraint.
- Backward Euler remains stable for all time steps but becomes overly diffusive when $\Delta t$ is large relative to $h$.
- Numerical solutions are compared directly with the analytic solution to illustrate accuracy and stability effects.

Representative plots include:
- stability thresholds for Forward Euler,
- resolution effects from spatial refinement,
- overdamping behavior in Backward Euler.

---

## Repository Structure

├── src/ # FEM assembly and time-integration code
├── figures/ # Generated plots (numerical vs analytic solutions)
├── report/ # Final project report (PDF)
└── README.md


---

## Skills Demonstrated

- Variational formulation of PDEs
- Finite element matrix assembly
- Reference-element mappings
- Gaussian quadrature
- Explicit vs implicit time integration
- Numerical stability and accuracy analysis

---

## Author

**Jiwoong (Alex) Choi**  
Computational Engineering  
University of Texas at Austin  

---

## Notes

This code is intended for educational and research purposes.  
Extensions such as higher-order elements, Crank–Nicolson time integration, or multi-dimensional problems are natural next steps.