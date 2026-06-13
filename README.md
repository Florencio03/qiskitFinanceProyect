# Quantum Portfolio Optimization using QAOA

This project implements the Markowitz portfolio optimization model using the Quantum Approximate Optimization Algorithm (QAOA) and Qiskit.

The optimization problem is formulated as a Quadratic Unconstrained Binary Optimization (QUBO) problem, transformed into an Ising Hamiltonian, and solved using both classical and quantum optimization techniques.

---

## Features

- Markowitz portfolio optimization.
- Real financial market data from Yahoo Finance.
- Expected return vector and covariance matrix estimation.
- QUBO formulation.
- Ising Hamiltonian transformation.
- Exact classical optimization.
- Quantum optimization using QAOA.
- IBM Quantum backend support.
- Portfolio risk-return analysis.

---

## Technologies

- Python 3.12
- Qiskit
- Qiskit Aer
- Qiskit Algorithms
- Qiskit Optimization
- Qiskit Finance
- IBM Quantum Runtime
- NumPy
- Pandas
- Matplotlib
- yfinance
- Jupyter Notebook

---

## Repository Structure

```text
.
├── portfolio_optimization_qaoa.ipynb
├── requirements.txt
└── README.md
```

---

## Clone the Repository

```bash
git clone git@github.com:Florencio03/qiskitFinanceProyect.git
cd qiskitFinanceProyect
```

---

## Create a Virtual Environment

### Linux / macOS

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### Windows

```powershell
python -m venv .venv
.venv\Scripts\activate
```

---

## Install Dependencies

Upgrade pip:

```bash
pip install --upgrade pip
```

Install all required packages:

```bash
pip install -r requirements.txt
```

---

## IBM Quantum Configuration

This project assumes that you already have an IBM Quantum account.

Save your IBM Quantum API token:

```python
from qiskit_ibm_runtime import QiskitRuntimeService

QiskitRuntimeService.save_account(
    channel="ibm_quantum",
    token="YOUR_API_TOKEN",
    overwrite=True
)
```

Verify the connection:

```python
from qiskit_ibm_runtime import QiskitRuntimeService

service = QiskitRuntimeService()

print(service.backends())
```

---

## Running the Notebook

Launch Jupyter:

```bash
jupyter lab
```

or

```bash
jupyter notebook
```

Open:

```text
portfolio_optimization.ipynb
```

and execute the notebook sequentially.

---

## Methodology

The workflow implemented in this project is:

```text
Historical Price Data
         ↓
Daily Returns
         ↓
Expected Return Vector (μ)
         ↓
Covariance Matrix (Σ)
         ↓
Markowitz Portfolio Model
         ↓
QUBO Formulation
         ↓
Ising Hamiltonian
         ↓
Classical Optimization / QAOA
         ↓
Optimal Portfolio
```

---

## Portfolio Optimization Model

The Markowitz objective function is

\[
\max
\left(
\mu^{T}x
-
q\,x^{T}\Sigma x
\right),
\]

where:

- \( \mu \) is the expected return vector.
- \( \Sigma \) is the covariance matrix.
- \( q \) is the risk-aversion parameter.
- \( x_i \in \{0,1\} \) indicates whether asset \(i\) is selected.

A budget constraint

\[
\sum_i x_i = B
\]

is incorporated through a penalty term to obtain a QUBO formulation.

---

## Example Results

For the 9-asset portfolio considered in this project:

```text
Exact value: -0.009905078666018589
QAOA value:  -0.009905078666018589
Difference:  0.0
```

The QAOA implementation successfully reproduced the exact optimal solution obtained by the classical solver.

---

## Future Improvements

- Test deeper QAOA circuits (higher reps).
- Benchmark against VQE.
- Execute on IBM Quantum hardware.
- Explore larger portfolios.
- Compare different risk-aversion parameters.

---

## References

1. Harry Markowitz, *Portfolio Selection*, Journal of Finance, 1952.
2. Farhi et al., *A Quantum Approximate Optimization Algorithm*, 2014.
3. Qiskit Documentation.
4. IBM Quantum Documentation.
