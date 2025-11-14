# Quantum_Option_Pricing
<img width="302" height="456" alt="image" src="https://github.com/user-attachments/assets/0284b5da-2213-47fa-b4d0-1348ad3bbfcb" />

## 📘 Problem Summary (Compact & Clear)

This project focuses on **pricing a call option using quantum computing** instead of classical models like Black–Scholes or Monte Carlo.

A option call has payoff:
\[
\max(S_T - K, 0)
\]
where \(S_T\) is the future stock price.

### 🎯 Goal
Build a quantum circuit that:
1. **Encodes the future stock price distribution** (lognormal) into qubit amplitudes  
2. **Encodes the option payoff** using multi-controlled RY rotations  
3. **Extracts the expected payoff** via ancilla measurement  
4. **Produces a quantum-estimated option price** that matches the classical price  

---

## 🧠 Core Quantum Idea (Very Simple)

Quantum computers can:
- Represent probability distributions using **amplitudes**  
- Encode payoff into **rotation angles**  
- Use **measurement probabilities** to estimate expected values  

Thus, the entire pricing process becomes a **quantum Monte Carlo estimator**.

---

## 🛠 Techniques You Demonstrate
- **Amplitude Encoding** → converts probability distribution into |ψ⟩  
- **Payoff Encoding** → controlled RY(θ) rotations map payoff → ancilla qubit  
- **Measurement-Based Expectation** → ancilla probability ≈ expected payoff  
- **Discounting** → converts payoff to final option price  

Your implementation successfully reproduces the classical price with very small error.
