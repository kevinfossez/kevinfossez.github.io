---
layout: default
title: Quantum computing -- UCC ansatz
description: Unitary Coupled Clusters ansatz
future: true
---

[back](./)

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
\newcommand{\bra}[1]{\left<#1\right|}
\newcommand{\ket}[1]{\left|#1\right>}
\begin{equation}
  \ket{\Psi}_{\text{UCC}} = {e}^{\hat{T} - \hat{T}^{\dagger}} \ket{\Psi}_{\text{HF}}
\end{equation}
$$  

where $${ \hat{T} = \hat{T}_{1} + \hat{T}_{2} + ... }$$ with $${ \hat{T}_{i} }$$ is an operator exciting $${ i }$$ particles out of the Hartree-Fock (HF) reference state. In the "single" case ($${ i = 1 }$$) and for only two shells labeled by $${ n = 0,1 }$$, one has:  

$$
\begin{equation}
  {e}^{\hat{T} - \hat{T}^{\dagger}} = {e}^{ {a}_{0}^{\dagger} {a}_{1} - {a}_{1}^{\dagger} {a}_{0} }
\end{equation}
$$  

As such, this ansatz cannot be used together with the VQE method (see [link](./page_qc.html)) and must be parametrized. To this end, one simply adds a parameter $${ \theta }$$ in the exponential. 

$$
\begin{equation}
  U(\theta) = {e}^{ \theta ( {a}_{0}^{\dagger} {a}_{1} - {a}_{1}^{\dagger} {a}_{0} ) }
\end{equation}
$$  

Moreover, the creation and annihilation operators can transformed into the $${ X }$$, $${ Y }$$, and $${ Z }$$ gates acting on qubits using the Jordan-Wigner transformation:

$$
\begin{align}
  & \hat{a}_{n}^{\dagger} \to \frac{1}{2} \left[ \prod_{j=0}^{n-1} (-{Z}_{j}) \right] ( {X}_{n} - i {Y}_{n} ) \\
  & \hat{a}_{n} \to \frac{1}{2} \left[ \prod_{j=0}^{n-1} (-{Z}_{j}) \right] ( {X}_{n} + i {Y}_{n} ) \\
\end{align}
$$  

It follows that:  

$$
\begin{align}
  & \hat{a}_{0}^{\dagger} \to \frac{1}{2} ( {X}_{0} - i {Y}_{0} ) \\
  & \hat{a}_{0} \to \frac{1}{2} ( {X}_{0} + i {Y}_{0} ) \\
  & \hat{a}_{1}^{\dagger} \to \frac{1}{2} (-{Z}_{0}) ( {X}_{1} - i {Y}_{1} ) \\
  & \hat{a}_{1} \to \frac{1}{2} (-{Z}_{0}) ( {X}_{1} + i {Y}_{1} )
\end{align}
$$  
and hence:  

$$
\begin{align}
  {a}_{0}^{\dagger} {a}_{1} - {a}_{1}^{\dagger} {a}_{0} &\to \frac{1}{2} ( {X}_{0} - i {Y}_{0} ) \frac{1}{2} (-{Z}_{0}) ( {X}_{1} + i {Y}_{1} ) - \frac{1}{2} (-{Z}_{0}) ( {X}_{1} - i {Y}_{1} ) \frac{1}{2} ( {X}_{0} + i {Y}_{0} ) \\
  &= \frac{1}{4} \left[ ( {X}_{0} {X}_{1} + i {X}_{0} {Y}_{1} - i {Y}_{0} {X}_{1} + {Y}_{0} {Y}_{1} ) (-{Z}_{0}) + {Z}_{0} ( {X}_{1} {X}_{0} + i {X}_{1} {Y}_{0} - i {Y}_{1} {X}_{0} + {Y}_{1} {Y}_{0} ) \right] \\
  &= \frac{1}{4} \left[ {X}_{1} ( {Z}_{0} {X}_{0} - {X}_{0} {Z}_{0} ) + {Y}_{1} ( {Z}_{0} {Y}_{0} - {Y}_{0} {Z}_{0} ) + i {Y}_{1} ( {Z}_{0} {Y}_{0} + {Y}_{0} {Z}_{0} ) - i {Y}_{1} ( {Z}_{0} {Y}_{0} + {Y}_{0} {Z}_{0} ) \right] \\
  &= \frac{i}{2} ( {X}_{1} {Y}_{0} - {Y}_{1} {X}_{0} )
\end{align}
$$  

It appears that the operator in the exponential writes:

$$
\begin{equation}
  {X}_{1} {Y}_{0} - {Y}_{1} {X}_{0} = -2
  \begin{pmatrix}
		0 & 0 & 0 & 0 \\
		0 & 0 & -i & 0 \\
		0 & i & 0 & 0 \\
		0 & 0 & 0 & 0 
	\end{pmatrix}
\end{equation}
$$  

This is equivalent to a $${ Y }$$ gate in the subspace defined by $${ \left|01\right> }$$ and $${ $${ \left|10\right> }$$, and so the exponential operator is equivalent to a rotation operator around the $${ y }$$ axis in this subspace. One can then emulate the effect of this operator by starting from the HF reference state $${ \left|00\right> }$$, flip one qubit to $${ \left|1\right> }$$ using a $${ X }$$ gate, apply a rotation $${ {R}_{Y}(\theta) = {e}^{-i \frac{\theta}{2} Y } }$$ on the second qubit (also noted $${ Y(\theta) }$$), and finally flip the first qubit to $${ \left|0\right> }$$ only if the second qubit is $${ \left|1\right> }$$ using a CNOT gate from 2 to 1 (also noted $${ \text{CNOT}_{01} }$$ instead of $${ \text{CNOT}_{10} }$$ for usual one). This is how the UCC ansatz was simplified in Phys. Rev. Lett. **120**, 210501 (2018) (for details see [link](./page_pn.html)).  

![](assets/fig_qc_circuit_UCC.png)

This results in the following wave function after the first operations:  

$$
\newcommand{\bra}[1]{\left<#1\right|}
\newcommand{\ket}[1]{\left|#1\right>}
\begin{align}
	\ket{\Psi({t}_{1})} &= X \ket{0} \otimes {R}_{y}(\theta) \ket{0} \\
	&= 
	\begin{pmatrix}
		0 & 1 \\
		1 & 0
	\end{pmatrix}
	\begin{pmatrix}
		1 \\
		0
	\end{pmatrix}
	\otimes
  \begin{pmatrix}
		\cos(\frac{\theta}{2}) & -\sin(\frac{\theta}{2}) \\
		\sin(\frac{\theta}{2}) & \sin(\frac{\theta}{2})
	\end{pmatrix}
	\begin{pmatrix}
		1 \\
		0
	\end{pmatrix}\\
  &= \ket{1} \otimes \left( \cos(\frac{\theta}{2}) \ket{0} + \sin(\frac{\theta}{2}) \ket{1} \right) \\
  &= \cos(\frac{\theta}{2}) \ket{10} + \sin(\frac{\theta}{2}) \ket{11}
\end{align}
$$  
and then after the two-quibit gate one has:  

$$
\newcommand{\bra}[1]{\left<#1\right|}
\newcommand{\ket}[1]{\left|#1\right>}
\begin{align}
	\ket{\Psi({t}_{2})} &= \text{CNOT}_{01} \ket{\Psi({t}_{1})} \\
	&= 
  \begin{pmatrix}
		1 & 0 & 0 & 0 \\
		0 & 0 & 0 & 1 \\
    0 & 0 & 1 & 0 \\
    0 & 1 & 0 & 0 
	\end{pmatrix}
	\left[
	\cos(\frac{\theta}{2})
	\begin{pmatrix}
		0 \\
		0 \\
		1 \\
		0 
	\end{pmatrix}
	+ \sin(\frac{\theta}{2})
	\begin{pmatrix}
		0 \\
		0 \\
		0 \\
		1 
	\end{pmatrix}
	\right] \\
	&= \cos(\frac{\theta}{2})
	\begin{pmatrix}
		0 \\
		0 \\
		1 \\
		0 
	\end{pmatrix}
	+ \sin(\frac{\theta}{2})
	\begin{pmatrix}
		0 \\
		1 \\
		0 \\
		0 
	\end{pmatrix}\\
  &= \cos(\frac{\theta}{2}) \ket{10} + \sin(\frac{\theta}{2}) \ket{01}
\end{align}
$$  

The UCC ansatz wave function looks like a parametrized Bell state:

$$
\newcommand{\bra}[1]{\left<#1\right|}
\newcommand{\ket}[1]{\left|#1\right>}
\begin{equation}
	\ket{\Psi}_{\text{UCC}} = \cos(\frac{\theta}{2}) \ket{10} + \sin(\frac{\theta}{2}) \ket{01}
\end{equation}
$$  





[back](./)
