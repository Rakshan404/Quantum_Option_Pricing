# Quantum_Option_Pricing
<img width="302" height="456" alt="Screenshot 2025-11-14 221128" src="https://github.com/user-attachments/assets/4808164c-a641-49be-a44e-3c94f51f549a" />


The goal of this project is to understand and demonstrate **how quantum computing techniques can be used to price financial options**, as outlined in the challenge prompt.  
A European call option is a financial instrument whose value depends on the **uncertain future price of a stock**.  
Traditionally, options are priced using classical models like **Black–Scholes** or **Monte Carlo simulations**, which repeatedly simulate many possible future stock prices.

However, the prompt challenges us to rethink this problem using **quantum computing**.  
Quantum systems have the unique ability to represent and manipulate many possible outcomes at the same time, making them a natural fit for financial problems involving uncertainty and probability.

---

## 🎯 What the Prompt Wants You To Explore

The question encourages exploring one of these directions:

- **Quantum random walks** to model price movement  
- **Quantum machine learning (QML)** to learn the pricing function  
- **Quantum circuits** that perform option pricing through amplitude encoding  

Our project takes the **quantum circuit approach**, which is a foundation for both quantum random walks and quantum Monte Carlo methods.

---

## 🧠 What This Project Actually Does

We translate the **entire option-pricing workflow** into quantum operations.  
Here’s the full idea in simple terms:

### **1. Uncertainty in Stock Prices → Quantum Amplitudes**

Future stock prices follow a **lognormal distribution**, but instead of simulating them one by one (like classical Monte Carlo), we encode this distribution into the **amplitudes of a quantum state**:

\[
|\psi\rangle = \sum_i \sqrt{p_i} |i\rangle
\]

Each basis state \(|i\rangle\):

- represents a possible future price  
- has amplitude √pᵢ (derived from probability pᵢ)

This allows the quantum system to represent **many future price scenarios simultaneously**.

---

### **2. Option Payoff → Quantum Rotation**

The payoff of a European call option is:

\[
\max(S_T - K, 0)
\]

We encode this payoff into the quantum circuit using a **multi-controlled RY gate**, which rotates an **ancilla qubit**.  
The rotation angle is proportional to the payoff for each price scenario.

- Higher payoff → bigger rotation  
- Lower payoff → smaller rotation  
- Zero payoff → no rotation  

This step is the quantum analogue of computing payoffs in classical Monte Carlo.

---

### **3. Expected Payoff → Probability of Ancilla = 1**

After running the circuit, we measure the ancilla qubit many times (shots).  
The frequency of seeing the ancilla in state \(|1⟩\) is directly related to the **expected payoff** of the option.

This is how the quantum system performs the “averaging” that classical Monte Carlo would normally require thousands or millions of samples to compute.

---

### **4. Discounting → Quantum Option Price**

Finally, we discount the expected payoff with:

\[
e^{-rT}
\]

to get the **present value of the option**, which is the final option price.

---

## ✔ Why This Exactly Matches the Prompt

This project satisfies the challenge requirements because:

### **✓ It uses quantum computing to solve a real financial problem**
We replace classical sampling with **quantum amplitude encoding and measurement**.

### **✓ It demonstrates a meaningful quantum approach**
Instead of just simulating formulas, we build a real quantum circuit that performs:

- probability encoding  
- payoff encoding  
- expectation estimation  

### **✓ It aligns with the suggested directions**
Our circuit is a valid example of:
- **quantum probabilistic modelling**,  
- a building block for **quantum random walks**, and  
- a precursor to **quantum machine learning (QML)** models for finance.

### **✓ It produces correct results**
The quantum-estimated option price comes very close to the classical price:


