# Solving the Wide-band Inverse Scattering Problem via Equivariant Neural Networks
## Presentation for the journal club

Presentation based on the original paper https://arxiv.org/abs/2212.06068 by Borong Zhang, Leonardo Zepeda-Núñez, Qin Li. I moved it here from Overleaf just in case.

## Outline

- Problem formulation
	- Helmholtz equation setting
	- Green's function, $C_{norm}$
	- Data
		- $\mathbf{s}$ - incoming plane wave direction
		- $\mathbf{r}$ - direction of measurement for refracted wave
		- $\Lambda^{\omega}(\mathbf{s}, \mathbf{r})$ - data for probing waves with frequency $\omega$
	- Forward problem: given $\eta(\mathbf{x}) = n(\mathbf{x}) - 1$ ($n$ is a refractive index), compute $\Lambda^{\omega} = \mathcal{F}^{\omega}(\eta)$ 
	- **Inverse problem**: infer $\mathcal{F}^\omega$ from measured data $\Lambda^{\omega}$
$$\eta^{*} = \mathcal{F}^{-1}(\{ \Lambda^{\omega} \}_{\omega \in \bar{\Omega}})$$
- Linearization and filtered back-projection (baseline algorithm)
	$$\eta^* = ((F^{\omega})^* \cdot F^{\omega} + \varepsilon I )^{-1}(F^\omega)^* \Lambda^{\omega}$$ 
	- Back-scattering operator $(F^\omega)^*$, rotation equivariant
	- Filtering operator $((F^{\omega})^* \cdot F^{\omega} + \varepsilon I )^{-1}$, translation equivariant, can be represented as a convolution
- CNN architecture
	- Mimic butterfly factorization when applying $(F^\omega)^*$ (optional for compressed version of the model)
	- Convolutional layers approximate the filtering operator
	- Shifting the data matrix to create intermediate representation encoding equivariance
- Results
  - The model was successfully trained on five categories of media and compared with existing algorithms
  - Neural networks are capable of efficiently approximating the map between media and data

