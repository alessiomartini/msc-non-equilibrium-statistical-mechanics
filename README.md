# Non-Equilibrium Statistical Mechanics — MSc Coursework (2025)

Jupyter notebooks written for the *Non-Equilibrium Statistical Mechanics* course
of the MSc in Physics, University of Amsterdam, academic year 2024/2025
(Alessio Martini, student no. 15621707).

Everything here is **numerical**: Langevin dynamics, random walks and sums of
random variables are simulated from scratch with `numpy`, and the results are
checked against the analytic predictions of the theory. The physics argument
lives in the markdown cells between the plots, so the notebooks read as short
reports rather than as bare code.

## The notebooks

| Notebook | Topic |
| --- | --- |
| `Problem Set 1 - final version.ipynb` | **Brownian motion, from free diffusion to Kramers escape.** Integrates the fully overdamped Langevin equation: first for a free particle, validating $\langle x^2 \rangle \propto t$ by fitting the simulated MSD and extracting the diffusion constant $D$ and its temperature dependence; then in a double-well potential, where the stationary distribution $p(x;T)$ is measured at three temperatures and compared with Boltzmann; then the choice of the integration step $\Delta t$, justified by building a timescale out of the parameters of the problem; and finally the statistics of the **first-passage time** $\tau_1$ to the top of the barrier as a function of barrier height $\Delta$ and temperature $T$ — the Kramers/Arrhenius law — including where that scaling breaks down. |
| `Problem Set 1 - Random Walk.ipynb` | The scratch version of Problem Set 1 — the working notebook where the pieces (single ODE, systems of ODEs, random forcing, ensembles of trajectories) were built and tested one at a time before being assembled. |
| `Problem Set 2 - Homework 1.ipynb` | **Random walks on a lattice: return probability and fractal dimension.** Walkers on a 3d cubic lattice, then the same measurement in $d = 1, 2, 3, \dots$ — the numerical counterpart of Pólya's theorem: the walk returns to the origin with probability 1 in one and two dimensions, and with probability < 1 from three dimensions upwards. Closes with the fractal dimension of the walk. The notebook is explicit about where the statistics are too thin to show the convergence cleanly. |
| `Problem Set 2 - Homework 2.ipynb` | **Sums of random variables from fat-tailed distributions.** Sampling a Pareto-type density $p(x) \sim x^{-1-\mu}$ by the inversion method; the probability density of the sum $S_N$ for several tail exponents $\mu$; scaling collapse of those densities, and a numerical estimate of the crossover $N_*$ beyond which the sum starts to look Gaussian. |
| `non-eq stat mech - Test PS2.ipynb` | A short scratch notebook: many 3d random walks, plotted in 3d. |
| `Exam - Alessio Martini.ipynb` | **Final exam.** Sums of random variables with $\mu = 3$ — a tail light enough for the Central Limit Theorem to hold. Argues that the skewness vanishes by symmetry, plots the distribution on logarithmic axes, identifies the rescaling exponents $\gamma = \phi = 1/2$ that make the variables dimensionless, and demonstrates the resulting data collapse. |

## The recurring method

Three techniques come back in nearly every notebook, and they are the point of
the course as much as the individual results:

1. **Simulate an ensemble, not a trajectory.** Every observable is an average
   over many independent realisations; the notebooks state the number of walkers
   and steps used, and note when that number is too small for the statistics to
   have converged.
2. **Look for the scaling law.** Rather than a single curve, the target is the
   exponent — $\langle x^2 \rangle \propto t$, or the pair $(\gamma, \phi)$ that
   makes a family of distributions collapse.
3. **Collapse the data.** Rescaling the axes so that curves for different $N$
   fall on top of one another is the visual proof that the scaling exponents are
   right, and it makes the crossover scale $N_*$ readable straight off the plot.

## Running the notebooks

Pure standard scientific Python — no course-specific package and no data files:

```bash
pip install numpy scipy matplotlib
jupyter lab
```

The simulations are stochastic and most cells do not fix a random seed, so
numbers and plots differ slightly from run to run. The outputs committed in the
notebooks are the ones the reports were written against.

## Related repository

- [`hydrodynamics_2025_msc_course`](https://github.com/alessiomartini/hydrodynamics_2025_msc_course)
  — homework notebooks from the Hydrodynamics course of the same MSc year.
