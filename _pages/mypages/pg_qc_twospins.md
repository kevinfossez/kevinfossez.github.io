---
layout: archive
permalink: /misc/qc/qc_twospins/
title: Quantum computing
description: Two spins
markdown: kramdown
---


The coupling of two spins is the easiest quantum problem to map on a quantum computer. 

## Hamiltonian

$$
\begin{equation}
  \hat{H} = \vec{S}^2 = {( \vec{s}_1 + \vec{s}_2 )}^2 = \frac{ {\hbar}^2 }{4} {( \vec{\sigma}_1 + \vec{\sigma}_2 )}^2 = \frac{ {\hbar}^2 }{4} ( \vec{\sigma}_1^2 + \vec{\sigma}_2^2 + 2 \vec{\sigma}_1.\vec{\sigma}_2 )
\end{equation}
$$

Each Pauli vector writes ${ \vec{\sigma} = {\sigma}_{x} \vec{u}_{x} + {\sigma}_{y} \vec{u}_{y} + {\sigma}_{z} \vec{u}_{z} }$ where the vectors ${ \vec{u}_{i} }$ are normalized to one and the operators ${ {\sigma}_{i} }$ are represented by the Pauli matrices. It follows that the representation of the Hamiltonian using quantum gates is given by:  

$$
\begin{equation}
  H = \frac{ {\hbar}^{2} }{4} ( 3 {I}_{1} + 3 {I}_{2} + 2 ( {X}_{1} {X}_{2} + {Y}_{1} {Y}_{2} + {Z}_{1} {Z}_{2} ) )
\end{equation}
$$

In matrix representation one has:  

\begin{equation}
\begin{aligned}
  H = \frac{ 3 {\hbar}^2 }{4}
  \begin{pmatrix}
    1 & 0 & 0 & 0 \\\\\\\\
    0 & 1 & 0 & 0 \\\\\\\\
    0 & 0 & 1 & 0 \\\\\\\\
    0 & 0 & 0 & 1
  \end{pmatrix}
  +\frac{ {\hbar}^2 }{2} \left[
  \begin{pmatrix}
    0 & 0 & 0 & 1 \\\\\\\\
    0 & 0 & 1 & 0 \\\\\\\\
    0 & 1 & 0 & 0 \\\\\\\\
    1 & 0 & 0 & 0
  \end{pmatrix}
  +\begin{pmatrix}
    0 & 0 & 0 & -1 \\\\\\\\
    0 & 0 & 1 & 0 \\\\\\\\
    0 & 1 & 0 & 0 \\\\\\\\
    -1 & 0 & 0 & 0
  \end{pmatrix}
  +\begin{pmatrix}
    1 & 0 & 0 & 0 \\\\\\\\
    0 & -1 & 0 & 0 \\\\\\\\
    0 & 0 & -1 & 0 \\\\\\\\
    0 & 0 & 0 & 1
  \end{pmatrix} \right]
\end{aligned}
\end{equation}


## Unitary Coupled Clusters (UCC) ansatz

See [link](./page_qc_pn) for details. The UCC wave function writes:  

$$
\begin{equation}
  \ket{ {\Psi}_{\text{UCC}} } = \cos\left(\frac{\theta}{2}\right) \ket{10} + \sin\left(\frac{\theta}{2}\right) \ket{01}
\end{equation}
$$

Applying the UCC wave function on the Hamiltonian gives:  



\begin{equation}
\begin{aligned}
  H \ket{ {\Psi}_{\text{UCC}} }
	&= \frac{ 3 {\hbar}^2 }{4} \ket{ {\Psi}\_{\text{UCC}} } \\\\\\\\
  &+ \frac{ {\hbar}^2 }{2}
  \begin{pmatrix}
    0 & 0 & 0 & 1 \\\\\\\\
    0 & 0 & 1 & 0 \\\\\\\\
    0 & 1 & 0 & 0 \\\\\\\\
    1 & 0 & 0 & 0
  \end{pmatrix}
	\left[\cos\left(\frac{\theta}{2}\right)
  \begin{pmatrix}
    0 \\\\\\\\
    0 \\\\\\\\
    1 \\\\\\\\
    0 
  \end{pmatrix}
	+\sin\left(\frac{\theta}{2}\right)
  \begin{pmatrix}
    0 \\\\\\\\
    1 \\\\\\\\
    0 \\\\\\\\
    0 
  \end{pmatrix}
  \right] \\\\\\\\
  &+\frac{ {\hbar}^2 }{2}
  \begin{pmatrix}
    0 & 0 & 0 & -1 \\\\\\\\
    0 & 0 & 1 & 0 \\\\\\\\
    0 & 1 & 0 & 0 \\\\\\\\
    -1 & 0 & 0 & 0
  \end{pmatrix}
	\left[\cos\left(\frac{\theta}{2}\right)
  \begin{pmatrix}
    0 \\\\\\\\
    0 \\\\\\\\
    1 \\\\\\\\
    0 
  \end{pmatrix}
	+\sin\left(\frac{\theta}{2}\right)
  \begin{pmatrix}
    0 \\\\\\\\
    1 \\\\\\\\
    0 \\\\\\\\
    0 
  \end{pmatrix}
  \right] \\\\\\\\
  &+\frac{ {\hbar}^2 }{2}
  \begin{pmatrix}
    1 & 0 & 0 & 0 \\\\\\\\
    0 & -1 & 0 & 0 \\\\\\\\
    0 & 0 & -1 & 0 \\\\\\\\
    0 & 0 & 0 & 1
  \end{pmatrix}
	\left[\cos\left(\frac{\theta}{2}\right)
  \begin{pmatrix}
    0 \\\\\\\\
    0 \\\\\\\\
    1 \\\\\\\\
    0 
  \end{pmatrix}
	+\sin\left(\frac{\theta}{2}\right)
  \begin{pmatrix}
    0 \\\\\\\\
    1 \\\\\\\\
    0 \\\\\\\\
    0 
  \end{pmatrix}
  \right] \\\\\\\\
  &= \frac{ 3 {\hbar}^2 }{4} \left[ \cos\left(\frac{\theta}{2}\right) \ket{10} + \sin\left(\frac{\theta}{2}\right) \ket{01} \right] \\\\\\\\
  &+ \frac{ {\hbar}^2 }{2} \left[ 2 \cos\left(\frac{\theta}{2}\right) \ket{01} + 2\sin\left(\frac{\theta}{2}\right) \ket{10} - \cos\left(\frac{\theta}{2}\right) \ket{10} - \sin\left(\frac{\theta}{2}\right) \ket{01} \right] \\\\\\\\
  &= \frac{ {\hbar}^2 }{4} \left[ \left( \cos\left(\frac{\theta}{2}\right) + 4 \sin\left(\frac{\theta}{2}\right) \right) \ket{10} + \left( \sin\left(\frac{\theta}{2}\right) + 4 \cos\left(\frac{\theta}{2}\right) \right) \ket{01} \right]
\end{aligned}
\end{equation}


# Energy of the system

The ground state energy of the two-spins system can be found by minimizing its energy given by:  

\begin{equation}
\begin{aligned}
  \bk{ {\Psi}\_{\text{UCC}} }{ H }{ {\Psi}\_{\text{UCC}} }
	&= \frac{ {\hbar}^2 }{4} \left[ \cos\left(\frac{\theta}{2}\right) \bra{10} + \sin\left(\frac{\theta}{2}\right) \bra{01} \right] \left[ \left( \cos\left(\frac{\theta}{2}\right) + 4 \sin\left(\frac{\theta}{2}\right) \right) \ket{10} + \left( \sin\left(\frac{\theta}{2}\right) + 4 \cos\left(\frac{\theta}{2}\right) \right) \ket{01} \right] \\\\\\\\
  &= \frac{ {\hbar}^2 }{4} \left( {\cos}^2\left(\frac{\theta}{2}\right) + 4 \cos\left(\frac{\theta}{2}\right) \sin\left(\frac{\theta}{2}\right) + {\sin}^{2}\left(\frac{\theta}{2}\right) + 4 \sin\left(\frac{\theta}{2}\right) \cos\left(\frac{\theta}{2}\right) \right) \\\\\\\\
  &= \frac{ {\hbar}^2 }{4} + {\hbar}^2 \cos\left(\frac{\theta}{2}\right) \sin\left(\frac{\theta}{2}\right)
\end{aligned}
\end{equation}

The minimum is obtained for ${ \theta = -\pi/2 }$ and gives ${ E = - {\hbar}^{2}/4 }$ as expected. One notes that the excited state energy can be obtained for ${ \theta = +\pi/2 }$ and one has ${ E = + 3 {\hbar}^{2}/4 }$.




