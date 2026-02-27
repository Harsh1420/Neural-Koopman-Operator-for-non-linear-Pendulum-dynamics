# Learning the Koopman Operator for a Nonlinear Pendulum using an Autoencoder

## Project Overview

This project implements a neural-network-based approach to learn the **Koopman operator** representation of a nonlinear dynamical system.

The nonlinear system considered is a simple pendulum governed by:

θ'' + g sin(θ) = 0

Instead of directly modeling the nonlinear dynamics, the code:

1. Generate trajectory data from the nonlinear ODE.
2. Use an autoencoder to lift the state into a latent space.
3. Learn a linear Koopman operator in that latent space.
4. Compare the predicted trajectory against the true ODE solution.

This project was developed as a learning exercise to better understand:
- Koopman operator theory
- Nonlinear system linearization in lifted spaces
- Neural network autoencoders
- Data-driven dynamical systems modeling

---

## System Assumptions

For learning purposes, the following assumptions were made:

- Pendulum length = 1
- Pendulum mass = 1
- Gravity = 9.8 m/s²
- Initial angle constrained to [-π/4, π/4]
- Initial angular velocity constrained to [-1.5, 1.5]

The initial condition constraints are intentionally restricted.  
This project is meant as a controlled learning experiment rather than a fully generalized system.

---

## Model Architecture

The architecture consists of:

Encoder:
x → ψ(x)

Decoder:
ψ(x) → x

Linear Koopman Operator:
ψ(xₜ₊₁) = K ψ(xₜ)

Loss Function:

Total Loss =  
• Reconstruction Loss  
• One-step Prediction Loss  
• Latent Linearity Loss  

The Koopman matrix K is extracted directly from the trained linear layer.

---

## Results

After training:

- The model successfully learns a latent linear representation.
- The learned Koopman operator produces a predicted trajectory that closely follows the true ODE trajectory.
- The velocity comparison between the true system and learned system demonstrates good agreement.

Example result:

The learned Koopman operator (The K matrix)

<img width="433" height="224" alt="learned K matrix" src="https://github.com/user-attachments/assets/c981f220-9a71-42f5-ade4-544fdf78dc60" />

The Velocity comparison plot

<img width="628" height="350" alt="predicted trajectory vs actual trajector" src="https://github.com/user-attachments/assets/6b153d4b-232b-4952-863e-3d8151480c2d" />

---

## Technologies Used

- Python
- PyTorch
- NumPy
- SciPy
- Matplotlib

---
