<center><h1>Quantum_Option_Pricing</h1></center>

<img width="302" height="456" alt="image" src="https://github.com/user-attachments/assets/218ffeff-3476-4155-bc8a-6b4a8ee964c8" />

<p>
Quantum_Circuit☝️
<p>
<h2>Quantum Option Pricing Using Qiskit (5-Qubit Implementation)</h2>

This project demonstrates a minimal and transparent quantum approach to pricing a European call option using Qiskit 1.x. The goal is to show how a quantum circuit can approximate the expected payoff of an option by encoding a probability distribution into quantum amplitudes and applying controlled rotations that represent the payoff function.

## Overview

The final stock price under the risk-neutral model follows a lognormal distribution. Since quantum circuits operate on discrete states, the distribution is approximated using 5 qubits, giving 32 possible price bins. Each bin corresponds to one possible future stock price outcome.

The notebook performs the following steps:

1. **Discretization of Stock Price Distribution**  
   The continuous lognormal distribution is divided into 32 bins. For each bin, the midpoint price and its probability mass are computed. These probabilities form the basis of the amplitude-encoded quantum state.

2. **Amplitude Encoding**  
   The square roots of the bin probabilities are loaded into a 5-qubit register using the `Initialize` instruction. This produces a quantum state where all price outcomes are represented in superposition according to their true probabilities.

3. **Payoff Function Encoding**  
   For each basis state (representing a price bin), a multi-controlled RY rotation is applied to an ancilla qubit.  
   - The rotation angle is proportional to the option payoff for that bin.  
   - Bins with no payoff generate no rotation.  
   Measuring the ancilla qubit allows estimation of the expected payoff.

4. **Estimating the Quantum Expected Payoff**  
   After the controlled rotations, the circuit is executed on the Aer simulator.  
   The probability of the ancilla measuring as `|1⟩` is proportional to the normalized expected payoff. This value is rescaled and discounted to obtain the quantum price estimate.

5. **Classical Benchmark**  
   Using the same discretized distribution, a classical expected payoff is calculated. This serves as the ground truth for evaluating the quantum estimate.

## Purpose

This project is designed as an example illustrating:

- amplitude encoding of probability distributions,
- controlled rotations for expectation estimation,
- mapping financial payoff functions onto quantum operations,
- comparison between classical and quantum pricing approaches,
- compatibility with the Qiskit 1.x architecture.

The implementation focuses on clarity and correctness rather than performance or quantum advantage.

## Limitations

- Only a simple European call option is modeled.
- Uses a small 5-qubit discretization, which limits accuracy.
- Does not implement full Quantum Amplitude Estimation or error mitigation.

## Requirements

- Python 3.10+
- Qiskit 1.x
- Qiskit Aer
- NumPy, SciPy, Matplotlib


