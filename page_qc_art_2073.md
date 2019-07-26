---
layout: default
title: Quantum computing
description: Details on E. F. Dumitrescu et al., Phys. Rev. Lett. 120, 210501 (2018)
future: true
---

[back](./)

## Article 

- E. F. Dumitrescu, A. J. McCaskey, G. Hagen, G. R. Jansen, T. D. Morris, T. Papenbrock, R. C. Pooser, D. J. Dean, and P. Lougovski  
  _Cloud Quantum Computing of an Atomic Nucleus_  
  Phys. Rev. Lett. **120**, 210501 (2018) [article](https://doi.org/10.1103/PhysRevLett.120.210501) -- [arXiv](https://arxiv.org/abs/1801.03897)

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


The UCC ansatz was simplified in article to a $${ X }$$ gate the first qubit, a rotation around the $${ y }$$ axis $${ {R}_{y}(\theta) = {e}^{-i \frac{\theta}{2} Y } }$$ on the second qubit, and the CNOT gate from 2 to 1 (also noted $${ \text{CNOT}_{01} }$$ instead of $${ \text{CNOT}_{10} }$$ for usual one). This results in the following wave function after the first operations:

$$
\newcommand{\bra}[1]{\left<#1\right|}
\newcommand{\ket}[1]{\left|#1\right>}
\newcommand{\bk}[2]{\left<#1|#2\right>}
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

The UCC ansatz wave function looks like a parametrized Bell state. Once the ansatz is set, one can apply the Hamiltonian derived in the article:  

$$
\begin{equation}
	{H}_{2} = a I + b {Z}_{0} + c {Z}_{1} + d ({X}_{0} {X}_{1} + {Y}_{0} {Y}_{1})
\end{equation}
$$  
where $${ a }$$, $${ b }$$, $${ c }$$, and $${ d }$$ are constants given by the problem (see article). The identity $${ I }$$ and the $${ Z }$$ gates are trivial while the two-qubit gates $${ XX }$$ and $${ YY }$$ need to be computed before. The final ansatz wave function is:  

$$
\begin{align}
  {H}_{2} \ket{\Psi({t}_{2})} &= a \left( \cos(\frac{\theta}{2}) \ket{10} + \sin(\frac{\theta}{2}) \ket{01} \right) \\
  &+ b \left( 
  \cos(\frac{\theta}{2}) 
  \begin{pmatrix}
  1 & 0 \\
  0 & -1
  \end{pmatrix}
  \begin{pmatrix}
  0 \\
  1
  \end{pmatrix}
  \otimes
  \begin{pmatrix}
  1 \\
  0
  \end{pmatrix}
	+ \sin(\frac{\theta}{2}) 
  \begin{pmatrix}
  1 & 0 \\
  0 & -1
  \end{pmatrix}
  \begin{pmatrix}
  1 \\
  0
  \end{pmatrix}
  \otimes
  \begin{pmatrix}
  0 \\
  1
  \end{pmatrix}
  \right) \\
  & + c \left( 
  \cos(\frac{\theta}{2}) 
  \begin{pmatrix}
  0 \\
  1
  \end{pmatrix}
  \otimes
  \begin{pmatrix}
  1 & 0 \\
  0 & -1
  \end{pmatrix}
  \begin{pmatrix}
  1 \\
  0
  \end{pmatrix}
	+ \sin(\frac{\theta}{2}) 
  \right)
  %\begin{pmatrix}
  %1 \\
  %0
  %\end{pmatrix}
  %\otimes
  %\begin{pmatrix}
  %1 & 0 \\
  %0 & -1
  %\end{pmatrix}
  %\begin{pmatrix}
  %0 \\
  %1
  %\end{pmatrix}
\end{align}
$$  
One can then compute the average energy of the system as:  

test14





[back](./)
