# Design and Implementation of Order 2 and 3 Volterra Series for Time Series Prediction

In the field of dynamic system identification, where the information about the underlying dynamic system model is absent, modelling nonlinear dynamics in a nonparametric way with Volterra series is a common approach. Volterra series is similar to Taylor series in structure, but also adds the benefit of capturing memory effects. 

In discrete time, single input: $x(n)$ - single output: $y(n)$ relation of a stable nonlinear time invariant dynamic system is given by the discrete time Volterra series, where $k(n)$ represents the Volterra kernel, as:

<img src="https://latex.codecogs.com/gif.latex?y(n)=k_{0}&plus;\sum_{m_{1}=0}^{M_{0}-1}{k_{1}(m_{1})x(n-m_{1})}&plus;\sum_{m_{1}=0}^{M_{1}-1}\sum_{m_{2}=0}^{M_{2}-1}{k_{2}(m_{1},m_{2})x(n-m_{1})x(n-m_{2})&plus;\dots}" title="y(n)=k_{0}+\sum_{m_{1}=0}^{M_{0}-1}{k_{1}(m_{1})x(n-m_{1})}+\sum_{m_{1}=0}^{M_{1}-1}\sum_{m_{2}=0}^{M_{2}-1}{k_{2}(m_{1},m_{2})x(n-m_{1})x(n-m_{2})+\dots}" />

In our system identification, where we use order (P) 2 Volterra series with $M_{0}=M_{1}=M_{2}$ and the constant term $k_{0}$ is taken to 0, we can rewrite this as,
<img src="https://latex.codecogs.com/gif.latex?y(n)=\sum_{d=1}^{P=2}\sum_{m_{1},\dots,m_{d}=0}^{M-1}k(m_{1},\dots,m_{d})\prod_{i=1}^{d}{x(n-m_{i})}" title="y(n)=\sum_{d=1}^{P=2}\sum_{m_{1},\dots,m_{d}=0}^{M-1}k(m_{1},\dots,m_{d})\prod_{i=1}^{d}{x(n-m_{i})}" />

At each order of nonlinearity, Volterra kernels describe the dynamics of the system and constitute a canonical representation of the nonlinear dynamic system. 

The main challenge of Volterra models is the exponentially growing number of kernel coefficients as the model order increases. An order $P$ Volterra model with $M$ memory terms, has $\sum_{d=0}^{P}{M^{d}}$ parameters to estimate. For multiple input multiple output dynamic system, the numbers of parameters to estimate increases to $\sum_{d=0}^{P}{(vM)^{d}}$, where $v$ denotes the number of inputs.

One way to simplify kernel estimation is through expanding them on a orthogonal Laguerre basis. Once the kernels are estimated, Principal Dynamic Mode (PDM) can be used to characterize and explain the dynamics of the underlying nonlinear dynamic system. 
