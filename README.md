# Algotrip

The equilibrium calculation algorithm in Mean Field Games (MFG) is solved iteratively using a pair of Hamilton–Jacobi–Bellman (HJB) and Fokker–Planck (FP) equations. In essence, we start with an initial density distribution $\rho^0(x)$ and repeatedly perform the following steps:

1.  Solve the Hamilton–Jacobi–Bellman (HJB) equation (backward in time) for the value function $V(x,t)$ given the current distribution $\rho$.
2.  Based on the obtained $V$, compute the optimal policy (control) $\alpha(x,t)$ that maximizes the payoff given the current $\rho$.
3.  Solve the Fokker–Planck (FP) equation (forward in time) for $\rho^{\text{new}}$ using the control $\alpha$.
4.  If the norm of the difference $\|\rho^{\text{new}} - \rho\|$ drops below the threshold, terminate iterations; otherwise, set $\rho \gets \rho^{\text{new}}$ and repeat.

The implementation for NMFG (Multi-Class Mean Field Games) is similar, but with a separate distribution $\rho_i$ for each class $i$. That is, at each step, multiple pairs of equations (Hamilton–Jacobi–Bellman and Fokker–Planck) are solved simultaneously—one pair for each class—taking into account the interactions between the distributions of different classes.


