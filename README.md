

# 🚀 Neutron Star Solver: TOV Equations & Stochastic EoS Analysis

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Physics](https://img.shields.io/badge/Physics-General%20Relativity-purple)
![License](https://img.shields.io/badge/License-MIT-green)

A Python simulation that solves the **Tolman-Oppenheimer-Volkoff (TOV)** equations to model neutron stars. The script demonstrates a physical analog to the **Malliavin Volatility Effect**: showing how massive neutron stars are significantly more sensitive to uncertainties in nuclear physics than lighter stars.

## 🔭 The Physics

This simulation solves the General Relativistic equations for hydrostatic equilibrium (TOV):

$$ \frac{dP}{dr} = -\frac{G(\epsilon + P)(m + 4\pi r^3 P/c^2)}{r^2(1 - 2Gm/rc^2)} $$

Where:
*   $P$ is pressure.
*   $\epsilon$ is energy density ($\rho c^2$).
*   $m$ is the enclosed mass.

### The Equation of State (EoS)
We use a **Polytropic Equation of State** to model the degenerate neutron matter core:
$$ P = K \rho^\gamma $$
*   **$\gamma = 2.0$**: Represents non-relativistic neutron degeneracy.
*   **$K$**: The "stiffness" of the nuclear matter.

### The "Malliavin Volatility" Demonstration
In stochastic calculus (financial math), Malliavin calculus measures the sensitivity of a derivative's price to the volatility of the underlying asset.

In this astrophysical context, we apply this concept to **Stochastic Sensitivity**:
1.  We introduce **Gaussian noise** to the nuclear stiffness parameter $K$ (simulating uncertainty in nuclear physics).
2.  We compare the resulting variance in Mass ($M$) and Radius ($R$) for two targets:
    *   **Standard Star:** $1.4 M_\odot$
    *   **Massive Star:** $2.0 M_\odot$

**Hypothesis:** Due to the extreme curvature of spacetime near the black hole limit, the $2.0 M_\odot$ star will act as a "lever," amplifying input noise into massive output variance.

---

## 📦 Requirements

*   Python 3.7+
*   Scientific libraries:

```bash
pip install numpy scipy matplotlib
```

## 🏃‍♂️ Usage

Save the code as `neutron_star_solver.py` and run it via terminal:

```bash
python neutron_star_solver.py
```

## 📊 Output Explanation

### 1. Console Output
The script will perform a calibration phase, finding the central densities ($\rho_c$) required to create 1.4 and 2.0 solar mass stars. It then runs a Monte Carlo simulation.

```text
🚀 NEUTRON STAR SOLVER: Malliavin Volatility Demonstration
============================================================
🔎 Tuning ρ_c for 1.4 M☉...
   ✅ Found: ρ_c=7.82e+14 -> M=1.401 M☉

🔎 Tuning ρ_c for 2.0 M☉...
   ✅ Found: ρ_c=2.15e+15 -> M=2.003 M☉

🎲 Generating Ensemble: 1.4 M☉ Star...
🎲 Generating Ensemble: 2.0 M☉ Star...

🎯 SENSITIVITY RATIO (Heavy/Light): 3.42x
✅ MALLIAVIN EFFECT CONFIRMED: Heavy stars are more volatile.
```

### 2. Visualization
A matplotlib window will open displaying two plots:

1.  **Mass-Radius Relation (Left):**
    *   Scatter plot showing the distribution of generated stars.
    *   **Blue:** $1.4 M_\odot$ ensemble.
    *   **Red:** $2.0 M_\odot$ ensemble.
    *   *Note how the Red cluster is significantly more "spread out" vertically than the Blue cluster.*

2.  **Variance Comparison (Right):**
    *   A bar chart quantifying the variance ($\sigma^2$).
    *   Visually demonstrates the non-linear sensitivity of the massive star.

## ⚙️ Customization

You can modify the `NeutronStarSolver` class in the code to test different physics:

*   **Change Gamma:** Modify `self.gamma` (e.g., try 2.5 or 2.75 for stiffer EoS).
*   **Increase Noise:** Change `noise = np.random.normal(0, 0.03)` to test higher volatility environments.
*   **Resolution:** Adjust `max_step` in `solve_ivp` for finer integration.

## 📝 License

This project is open-source and available under the MIT License. Feel free to use it for educational purposes in Physics or Computational Mathematics classes.
