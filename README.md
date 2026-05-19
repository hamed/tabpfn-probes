# tabpfn-probes

Small experiments that hand TabPFN systems with known ground truth and watch where it bends.

Both notebooks use analytically tractable problems — the kind where you can derive the right answer and compare against it exactly, no benchmarks needed. The point isn't to beat anything. The point is to see what the model actually does at the edges, and whether what it does is honest.

---

## Thermodynamics with TabPFN

A two-state spin system in a magnetic field. The Fermi-Dirac distribution gives the exact probability of each state at every temperature. We show TabPFN only the moderate temperatures and ask it about the extremes.

Logistic regression nails the extrapolation, because the sigmoid *is* the Fermi-Dirac equation — its inductive bias and the physics happen to be the same. TabPFN refuses to extrapolate. More data doesn't fix it. The refusal turns out to be the right answer for a model that doesn't know it's looking at physics.

[→ open notebook](./Thermodynamics_with_TabPFN.ipynb)

---

## Two Gaussians with TabPFN

Two Gaussian clouds in one dimension, with shared center and different widths. The Bayes-optimal posterior is U-shaped — there's no line that separates the classes, only a typicality test.

TabPFN recovers the U. Logistic regression collapses to a flat 50%. The interesting part is on the log-scale entropy: TabPFN's confidence has a *floor* that scales cleanly with sample size. It's reluctant, ever so slightly, to be more certain than the training set has earned.

[→ open notebook](./Two_Gaussians_with_TabPFN.ipynb)

---

## Running them

Both notebooks use `tabpfn_client`. You need a TabPFN API token — drop it into Colab Secrets as `TABPFN_TOKEN` or set it as an environment variable. Everything else is standard scientific Python.

---

*Hamed Seyed-allaei · Berlin · 2026*
