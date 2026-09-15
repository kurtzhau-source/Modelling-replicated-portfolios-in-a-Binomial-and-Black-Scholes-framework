# Option Replication: Binomial vs Black-Scholes

## Objective
Compare the replicating portfolios of European call options under the binomial and Black-Scholes frameworks. Simulate stock paths using geometric Brownian motion and measure the tracking error of the binomial hedge relative to Black-Scholes as the number of time steps increases.

## Replicating Portfolios

### Binomial model
At each step, the hedge consists of $\Delta$ shares and a cash amount $B$:

$$
\Delta = \frac{C_u - C_d}{S(u-d)}, \qquad
B = \frac{u C_d - d C_u}{R(u-d)}
$$

where $R = e^{r \Delta t}$, $u = e^{\sigma\sqrt{\Delta t}}$, $d = 1/u$, and $C_u, C_d$ are the up/down option payoffs.

### Black-Scholes model
The continuous-time hedge is:

$$
\Delta = N(d_1), \qquad
B = -K e^{-r(T-t)} N(d_2)
$$

with

$$
d_1 = \frac{\ln(S/K) + (r + \sigma^2/2)(T-t)}{\sigma\sqrt{T-t}}, \qquad
d_2 = d_1 - \sigma\sqrt{T-t}
$$

## Simulation Setup
- $S_0 = 7$, $K = 7$, $\sigma = 0.5$, $T = 1$ year, $r = 0.06$
- Stock paths: $S_i = S_{i-1} \exp\left((r - \tfrac12\sigma^2)\Delta t + Z_i \sigma\sqrt{\Delta t}\right)$
- Binomial rebalancing at $n = 252$ steps
- Black-Scholes hedge rebalanced at the same frequency for fair comparison

## Results

<img width="642" height="453" alt="image" src="https://github.com/user-attachments/assets/1c909ac5-6ec4-49e8-9ec9-5690f42dbcb6" />
<img width="597" height="443" alt="image" src="https://github.com/user-attachments/assets/0c139e33-f5b3-41f0-98ba-78473c9e9bc4" />
<img width="703" height="459" alt="image" src="https://github.com/user-attachments/assets/985eb49e-0cf0-4ad6-8f2e-fb733e28215d" />
<img width="634" height="446" alt="image" src="https://github.com/user-attachments/assets/39c3493f-3afc-4a12-97b0-3ee66d26dd41" />



- At expiry, both portfolios match the option payoff.
- The binomial hedge exhibits small tracking error relative to Black-Scholes over the option's life.
- When S > K the binomial hedge converges to the Black-Scholes hedge.

## Conclusion
The binomial replicating portfolio provides a good discrete approximation to the Black-Scholes portfolio. The approximation error decreases with over time, confirming the theoretical convergence of the binomial model to Black-Scholes.

