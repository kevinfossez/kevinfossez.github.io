---
layout: default
title: Quantum computing
description: Two spins
future: true
---

[back](./)

The coupling of two spins is the easiest quantum problem to map on a quantum computer. 

## Hamiltonian

$$
\newcommand{\bra}[1]{\left<#1\right|}
\newcommand{\ket}[1]{\left|#1\right>}
\begin{equation}
  \hat{H} = \vec{S}^{2} = {( \vec{s}_{1} + \vec{s}_{2} )}^{2} = \frac{ {\hbar}^{2} }{4} {( \vec{\sigma}_{1} + \vec{\sigma}_{2} )}^{2} = \frac{ {\hbar}^{2} }{4} ( \vec{\sigma}_{1}^{2} + \vec{\sigma}_{2}^{2} + 2 \vec{\sigma}_{1}.\vec{\sigma}_{2} )
\end{equation}
$$

Each Pauli vector writes $${ \vec{\sigma} = {\sigma}_{x} \vec{u}_{x} + {\sigma}_{y} \vec{u}_{y} + {\sigma}_{z} \vec{u}_{z} }$$ where the vectors $${ \vec{u}_{i} }$$ are normalized to one and the operators $${ {\sigma}_{i} }$$ are represented by the Pauli matrices. It follows that the representation of the Hamiltonian using quantum gates is given by:  

$$
\newcommand{\bra}[1]{\left<#1\right|}
\newcommand{\ket}[1]{\left|#1\right>}
\begin{equation}
  H = \frac{ {\hbar}^{2} }{4} ( 3 {I}_{1} + 3 {I}_{2} + 2 ( {X}_{1} {X}_{2} + {Y}_{1} {Y}_{2} + {Z}_{1} {Z}_{2} ) )
\end{equation}
$$

In matrix representation one has:  

$$
\newcommand{\bra}[1]{\left<#1\right|}
\newcommand{\ket}[1]{\left|#1\right>}
\begin{equation}
  H = \frac{ 3 {\hbar}^{2} }{4}
  \begin{pmatrix}
    1 & 0 & 0 & 0 \\
    0 & 1 & 0 & 0 \\
    0 & 0 & 1 & 0 \\
    0 & 0 & 0 & 1
  \end{pmatrix} 
  + \frac{ {\hbar}^{2} }{2} \left[ 
  \begin{pmatrix}
    0 & 0 & 0 & 1 \\
    0 & 0 & 1 & 0 \\
    0 & 1 & 0 & 0 \\
    1 & 0 & 0 & 0
  \end{pmatrix} + 
  \begin{pmatrix}
    0 & 0 & 0 & -1 \\
    0 & 0 & 1 & 0 \\
    0 & 1 & 0 & 0 \\
    -1 & 0 & 0 & 0
  \end{pmatrix} + 
  \begin{pmatrix}
    1 & 0 & 0 & 0 \\
    0 & -1 & 0 & 0 \\
    0 & 0 & -1 & 0 \\
    0 & 0 & 0 & 1
  \end{pmatrix} 
  \right]
\end{equation}
$$

## Unitary Coupled Clusters (UCC) ansatz

See [link](./page_qc_pn) for details. The UCC wave function writes:  

$$
\newcommand{\bra}[1]{\left<#1\right|}
\newcommand{\ket}[1]{\left|#1\right>}
\begin{equation}
  \ket{\Psi}_{\text{UCC}} = \cos\left(\frac{\theta}{2}\right) \ket{10} + \sin\left(\đrac{\theta}{2}\right) \ket{01}
\end{equation}
$$

Applying the UCC wave function on the Hamiltonian gives:  

$$
\newcommand{\bra}[1]{\left<#1\right|}
\newcommand{\ket}[1]{\left|#1\right>}
\begin{align}
  H \ket{\Psi}_{\text{UCC}} &= 
  \frac{ 3 {\hbar}^{2} }{4} \ket{\Psi}_{\text{UCC}} +  \frac{ {\hbar}^{2} }{2} \left[  
  \begin{pmatrix}
    0 & 0 & 0 & 1 \\
    0 & 0 & 1 & 0 \\
    0 & 1 & 0 & 0 \\
    1 & 0 & 0 & 0
  \end{pmatrix} \left[ 
		\cos\left(\frac{\theta}{2}\right) 
  \begin{pmatrix}
    0 \\
    0 \\
    1 \\
    0 
  \end{pmatrix} + \sin\left(\đrac{\theta}{2}\right) 
  \begin{pmatrix}
    0 \\
    1 \\
    0 \\
    0 
  \end{pmatrix}
  \right] + 
  \begin{pmatrix}
    0 & 0 & 0 & -1 \\
    0 & 0 & 1 & 0 \\
    0 & 1 & 0 & 0 \\
    -1 & 0 & 0 & 0
  \end{pmatrix} \left[ 
		\cos\left(\frac{\theta}{2}\right) 
  \begin{pmatrix}
    0 \\
    0 \\
    1 \\
    0 
  \end{pmatrix} + \sin\left(\đrac{\theta}{2}\right) 
  \begin{pmatrix}
    0 \\
    1 \\
    0 \\
    0 
  \end{pmatrix}
  \right] + 
  \begin{pmatrix}
    1 & 0 & 0 & 0 \\
    0 & -1 & 0 & 0 \\
    0 & 0 & -1 & 0 \\
    0 & 0 & 0 & 1
  \end{pmatrix} \left[ 
		\cos\left(\frac{\theta}{2}\right) 
  \begin{pmatrix}
    0 \\
    0 \\
    1 \\
    0 
  \end{pmatrix} + \sin\left(\đrac{\theta}{2}\right) 
  \begin{pmatrix}
    0 \\
    1 \\
    0 \\
    0 
  \end{pmatrix}
  \right] \right]
\end{align}
$$





[back](./)
