# Bearish-Notes
In this notebook, I describe how to value this type of note. Below I provide the mathematical equation of the payoff that the holder will receive.

A bearish note is a type of structured product whereby the holder of the note looks to benefit from the decline in the price of the underlying stock. In this type of note, the holder is guaranteed to receive the full capital of what they initially invested. So this is a type of capital protected product.

Let $N$ be the capital amount that the holder initially invests and $S$ be the underlying stock. The payoff $V_T$ at maturity at $T$ is:
$$V_T=N\left(1+\beta\times\max\left(1-\frac{S_T}{S_0}, 0\right)\right)=N+\frac{N\cdot \beta}{S_0}\times\max\left(S_0-S_T,0\right),$$
where $\beta$ is the participation rate, which can be lower or higher than $1$ and $S_0$ is the initial stock price.

As you can see, this can be replicated by buying a ZCB with capital $N$ and buying $\frac{N\cdot \beta}{S_0}$ amounts of put options with strike $S_0$.

To value this note, a risk-neutral pricing formula is used:
$$V_0=N e^{-rT}+\frac{N\cdot\beta}{S_0}\times\mathbb{E}[e^{-rT}\max\left(S_0-S_T,0\right)].$$

I assume that the underlying stock follows the Black-Scholes dynamics. The value of the bearish note is
$$V_0 = N e^{-rT} + \frac{N \cdot \beta}{S_0} \cdot \left( S_0 \Phi(-d_1) - S_0 e^{-rT} \Phi(-d_2) \right)= N e^{-rT} + N \cdot \beta \cdot \left(\Phi(-d_1) - e^{-rT} \Phi(-d_2) \right).$$

The delta is
$$\Delta = -\frac{N \cdot \beta}{S_0} \cdot \Phi(-d_1),$$

The Gamma
$$\Gamma = \frac{N \cdot \beta}{S_0} \cdot \frac{\phi(d_1)}{S_0 \cdot \sigma \sqrt{T}},$$

The Vega
$$\nu = \frac{N \cdot \beta}{S_0} \cdot S_0 \sqrt{T} \cdot \phi(d_1),$$
where
$d_1 = \frac{(r + \frac{\sigma^2}{2}) T}{\sigma \sqrt{T}}$ and
$d_2 = d_1 - \sigma \sqrt{T}$, $\Phi$ and $\phi$ are standard normal cumulative distribution and probability density functions, respectively.
