---
layout: archive
permalink: /misc/qc/qc_UCC/
title: Quantum computing -- UCC ansatz
description: Unitary Coupled Clusters ansatz
---


## Unitary Coupled Clusters (UCC) ansatz

- Yangchao Shen, Xiang Zhang, Shuaining Zhang, Jing-Ning Zhang, Man-Hong Yung, and Kihwan Kim  
  _Quantum implementation of the unitary coupled cluster for simulating molecular electronic structure_  
  Phys. Rev. A **95**, 020501(R) (2017) [article](https://doi.org/10.1103/PhysRevA.95.020501)

- P. J. J. O’Malley, R. Babbush, I. D. Kivlichan, J. Romero, J. R. McClean, R. Barends, J. Kelly, P. Roushan, A. Tranter, N. Ding, B. Campbell, Y. Chen, Z. Chen, B. Chiaro, A. Dunsworth, A. G. Fowler, E. Jeffrey, E. Lucero, A. Megrant, J. Y. Mutus, M. Neeley, C. Neill, C. Quintana, D. Sank, A. Vainsencher, J. Wenner, T. C. White, P. V. Coveney, P. J. Love, H. Neven, A. Aspuru-Guzik and J. M. Martinis5  
  _Scalable Quantum Simulation of Molecular Energies_  
  Phys. Rev. X **6**, 031007 (2016) [article](https://doi.org/10.1103/PhysRevX.6.031007) [arXiv](https://arxiv.org/abs/1512.06860) 

- J. R. McClean, J. Romero, R. Babbush and A. Aspuru-Guzik  
  _The theory of variational hybrid quantum-classical algorithms_  
  New J. Phys. **18**, 023023 (2016) [article](https://doi.org/10.1088/1367-2630/18/2/023023) [arXiv](https://arxiv.org/abs/1509.04279)

- A. Peruzzo, J. McClean, P. Shadbolt, Man-Hong Yung, Xiao-Qi Zhou, P. J. Love, A. Aspuru-Guzik and J. L. O’Brien  
  _A variational eigenvalue solver on a photonic quantum processor_  
  Nature Communications **5**, 4213 (2014) [article](https://www.nature.com/articles/ncomms5213) [arXiv](https://arxiv.org/abs/1304.3061)

- M.-H. Yung, J. Casanova, A. Mezzacapo, J. McClean, L. Lamata, A. Aspuru-Guzik and E. Solano  
  _From transistor to trapped-ion computers for quantum chemistry_  
  Scientific Reports **4**, 3589 (2014) [article](https://doi.org/10.1038/srep03589)


## Article 

- E. F. Dumitrescu, A. J. McCaskey, G. Hagen, G. R. Jansen, T. D. Morris, T. Papenbrock, R. C. Pooser, D. J. Dean, and P. Lougovski  
  _Cloud Quantum Computing of an Atomic Nucleus_  
  Phys. Rev. Lett. **120**, 210501 (2018) [article](https://doi.org/10.1103/PhysRevLett.120.210501) -- [arXiv](https://arxiv.org/abs/1801.03897)


The UCC ansatz writes:  

$$
\begin{equation}
  \ket{\Psi}_{\text{UCC}} = {e}^{\hat{T} - \hat{T}^{\dagger}} \ket{\Psi}_{\text{HF}}
\end{equation}
$$  

where ${ \hat{T} = \hat{T}_{1} + \hat{T}_{2} + ... }$ with ${ \hat{T}_{i} }$ is an operator exciting ${ i }$ particles out of the Hartree-Fock (HF) reference state. In the "single" case (${ i = 1 }$) and for only two shells labeled by ${ n = 0,1 }$, one has:  

$$
\begin{equation}
  {e}^{\hat{T} - \hat{T}^{\dagger}} = {e}^{ {a}_{0}^{\dagger} {a}_{1} - {a}_{1}^{\dagger} {a}_{0} }
\end{equation}
$$  

As such, this ansatz cannot be used together with the VQE method (see [link](./qc/)) and must be parametrized. To this end, one simply adds a parameter ${ \theta }$ in the exponential. 

$$
\begin{equation}
  U(\theta) = {e}^{ \theta ( a_0^{\dagger} a_1 - a_1^{\dagger} a_0 ) }
\end{equation}
$$  

Moreover, the creation and annihilation operators can transformed into the ${ X }$, ${ Y }$, and ${ Z }$ gates acting on qubits using the Jordan-Wigner transformation:

\begin{equation}
\begin{aligned}
  & \hat{a}\_n^{\dagger} \to \frac{1}{2} \left[ \prod\_{j=0}^{n-1} (-Z_j) \right] ( X_n - i Y_n ) \\\\\\\\
  & \hat{a}\_n \to \frac{1}{2} \left[ \prod\_{j=0}^{n-1} (-Z_j) \right] ( X_n + i Y_n )
\end{aligned}
\end{equation}

It follows that:  

\begin{equation}
\begin{aligned}
  & \hat{a}_0^{\dagger} \to \frac{1}{2} ( X_0 - i Y_0 ) \\\\\\\\
  & \hat{a}_0 \to \frac{1}{2} ( X_0 + i Y_0 ) \\\\\\\\
  & \hat{a}_1^{\dagger} \to \frac{1}{2} (-Z_0) ( X_1 - i Y_1 ) \\\\\\\\
  & \hat{a}_1 \to \frac{1}{2} (-Z_0) ( X_1 + i Y_1 )
\end{aligned}
\end{equation}

and hence:  

\begin{equation}
\begin{aligned}
  {a}_0^{\dagger} a_1 - a_1^{\dagger} a_0 &\to \frac{1}{2} ( X_0 - i Y_0 ) \frac{1}{2} (-Z_0) ( X_1 + i Y_1 ) - \frac{1}{2} (-Z_0) ( X_1 - i Y_1 ) \frac{1}{2} ( X_0 + i Y_0 ) \\\\\\\\
  &= \frac{1}{4} \left[ ( X_0 X_1 + i X_0 Y_1 - i Y_0 X_1 + Y_0 Y_1 ) (-Z_0) + Z_0 ( X_1 X_0 + i X_1 Y_0 - i Y_1 X_0 + Y_1 Y_0 ) \right] \\\\\\\\
  &= \frac{1}{4} \left[ X_1 ( Z_0 X_0 - X_0 Z_0 ) + Y_1 ( Z_0 Y_0 - Y_0 Z_0 ) + i Y_1 ( Z_0 Y_0 + Y_0 Z_0 ) - i Y_1 ( Z_0 Y_0 + Y_0 Z_0 ) \right] \\\\\\\\
  &= \frac{i}{2} ( X_1 Y_0 - Y_1 X_0 )
\end{aligned}
\end{equation}

It appears that the operator in the exponential writes:

\begin{equation}
\begin{aligned}
  X_1 Y_0 - Y_1 X_0 = -2
  \begin{pmatrix}
		0 & 0 & 0 & 0 \\\\\\\\
		0 & 0 & -i & 0 \\\\\\\\
		0 & i & 0 & 0 \\\\\\\\
		0 & 0 & 0 & 0 
	\end{pmatrix}
\end{aligned}
\end{equation}

This is equivalent to a ${ Y }$ gate in the subspace defined by ${ \ket{01} }$ and ${ \ket{10} }$, and so the exponential operator is equivalent to a rotation operator around the ${ y }$ axis in this subspace. One can then emulate the effect of this operator by starting from the HF reference  state ${ \ket{00} }$, flip one qubit to ${ \ket{1} }$ using a ${ X }$ gate, apply a rotation ${ {R}_{Y}(\theta) = {e}^{-i \frac{\theta}{2} Y } }$ on the second qubit (also noted ${ Y(\theta) }$), and finally flip the first qubit to ${ \ket{0} }$ only if the second qubit is ${ \ket{1} }$ using a CNOT gate from 2 to 1 (also noted ${ \text{CNOT}_{01} }$ instead of ${ \text{CNOT}_{10} }$ for usual one). This is how the UCC ansatz was simplified in Phys. Rev. Lett. **120**, 210501 (2018) (for details see [link](./page_pn.html)).  

![](assets/fig_qc_circuit_UCC.png)

This results in the following wave function after the first operations:  

\begin{equation}
\begin{aligned}
	\ket{\Psi(t_1)} &= X \ket{0} \otimes {R}_{y}(\theta) \ket{0} \\\\\\\\
	&= 
	\begin{pmatrix}
		0 & 1 \\\\\\\\
		1 & 0
	\end{pmatrix}
	\begin{pmatrix}
		1 \\\\\\\\
		0
	\end{pmatrix}
	\otimes
  \begin{pmatrix}
		\cos(\frac{\theta}{2}) & -\sin(\frac{\theta}{2}) \\\\\\\\
		\sin(\frac{\theta}{2}) & \sin(\frac{\theta}{2})
	\end{pmatrix}
	\begin{pmatrix}
		1 \\\\\\\\
		0
	\end{pmatrix}\\\\\\\\
  &= \ket{1} \otimes \left( \cos(\frac{\theta}{2}) \ket{0} + \sin(\frac{\theta}{2}) \ket{1} \right) \\\\\\\\
  &= \cos(\frac{\theta}{2}) \ket{10} + \sin(\frac{\theta}{2}) \ket{11}
\end{aligned}
\end{equation}

and then after the two-quibit gate one has:  

\begin{equation}
\begin{aligned}
	\ket{\Psi(t_2)} &= \text{CNOT}_{01} \ket{\Psi(t_1)} \\\\\\\\
	&= 
  \begin{pmatrix}
		1 & 0 & 0 & 0 \\\\\\\\
		0 & 0 & 0 & 1 \\\\\\\\
    0 & 0 & 1 & 0 \\\\\\\\
    0 & 1 & 0 & 0 
	\end{pmatrix}
	\left[
	\cos(\frac{\theta}{2})
	\begin{pmatrix}
		0 \\\\\\\\
		0 \\\\\\\\
		1 \\\\\\\\
		0 
	\end{pmatrix}
	+ \sin(\frac{\theta}{2})
	\begin{pmatrix}
		0 \\\\\\\\
		0 \\\\\\\\
		0 \\\\\\\\
		1 
	\end{pmatrix}
	\right] \\\\\\\\
	&= \cos(\frac{\theta}{2})
	\begin{pmatrix}
		0 \\\\\\\\
		0 \\\\\\\\
		1 \\\\\\\\
		0 
	\end{pmatrix}
	+ \sin(\frac{\theta}{2})
	\begin{pmatrix}
		0 \\\\\\\\
		1 \\\\\\\\
		0 \\\\\\\\
		0 
	\end{pmatrix}\\\\\\\\
  &= \cos(\frac{\theta}{2}) \ket{10} + \sin(\frac{\theta}{2}) \ket{01}
\end{aligned}
\end{equation}

The UCC ansatz wave function looks like a parametrized Bell state:

\begin{equation}
	\ket{\Psi}_{\text{UCC}} = \cos(\frac{\theta}{2}) \ket{10} + \sin(\frac{\theta}{2}) \ket{01}
\end{equation}





