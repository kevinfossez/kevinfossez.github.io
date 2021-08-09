---
layout: archive
permalink: /misc/qc/qc_gates/
title: Quantum computing gates
description: One- and two-qubit gates
---

See wikipedia page on [quantum gates](https://en.wikipedia.org/wiki/Quantum_logic_gate) for more details.

## One qubit

### Spin ${ 1/2 }$ representation and conventions

$$
\ket{ s = 1/2, {m}_{s} = \pm 1/2 } = \ket{\pm}
$$

Sometimes the kets ${ \ket{\pm} }$ are used for the Hadamard transformed basis [link](https://en.wikipedia.org/wiki/Controlled_NOT_gate), otherwise, the convention is to take ${ \ket{+} = \ket{0} }$ and ${ \ket{-} = \ket{1} }$, so in the matrix representation one has:  

\begin{equation}
\begin{aligned}
  & \ket{+} = \ket{0} = 
  \begin{pmatrix}
    1 \\\\\\\\
    0
  \end{pmatrix} \\\\\\\\
  & \ket{-} = \ket{1} = 
  \begin{pmatrix}
    0 \\\\\\\\
    1
  \end{pmatrix}
\end{aligned}
\end{equation}


### One-qubit gates

The identity matrix is trivially:

\begin{equation}
\begin{aligned}
  I =  
  \begin{pmatrix}
    1 & 0 \\\\\\\\
    0 & 1
  \end{pmatrix} 
  = \ket{0}\bra{0} + \ket{1}\bra{1}
\end{aligned}
\end{equation}



Pauli matrices are the building blocks for all operations acting on spins ${ 1/2 }$ and so on individual qubits. In matrix representation they are defined as:  

\begin{equation}
\begin{aligned}
  {\sigma}_{1} =  
  \begin{pmatrix}
    0 & 1 \\\\\\\\
    1 & 0
  \end{pmatrix} 
  = X = \ket{1}\bra{0} + \ket{0}\bra{1}
\end{aligned}
\end{equation}

\begin{equation}
\begin{aligned}
  {\sigma}_{2} =  
  \begin{pmatrix}
    0 & -i \\\\\\\\
    i & 0
  \end{pmatrix} 
  = Y = i \ket{1}\bra{0} -i \ket{0}\bra{1}
\end{aligned}
\end{equation}

\begin{equation}
\begin{aligned}
  {\sigma}_{3} =  
  \begin{pmatrix}
    1 & 0 \\\\\\\\
    0 & -1
  \end{pmatrix} 
  = Z = \ket{0}\bra{0} - \ket{1}\bra{1}
\end{aligned}
\end{equation}


The ${ X }$ matrix is also called the NOT gate.

The rotation gates along the ${ X }$, ${ Y }$, and ${ Z }$ axes are defined as:

\begin{equation}
\begin{aligned}
  {R}_{X}(\theta) = {e}^{ -i \frac{\theta}{2} X } = cos\left( \frac{\theta}{2} \right) I - i \sin\left( \frac{\theta}{2} \right) X = 
  \begin{pmatrix}
    \cos\left( \frac{\theta}{2} \right) & -i \sin\left( \frac{\theta}{2} \right) \\\\\\\\
    -i \sin\left( \frac{\theta}{2} \right) & \cos\left( \frac{\theta}{2} \right)
  \end{pmatrix} 
\end{aligned}
\end{equation}

\begin{equation}
\begin{aligned}
  {R}_{Y}(\theta) = {e}^{ -i \frac{\theta}{2} Y } = cos\left( \frac{\theta}{2} \right) I - i \sin\left( \frac{\theta}{2} \right) Y = 
  \begin{pmatrix}
    \cos\left( \frac{\theta}{2} \right) & - \sin\left( \frac{\theta}{2} \right) \\\\\\\\
     \sin\left( \frac{\theta}{2} \right) & \cos\left( \frac{\theta}{2} \right)
  \end{pmatrix} 
\end{aligned}
\end{equation}

\begin{equation}
\begin{aligned}
  {R}_{Z}(\theta) = {e}^{ -i \frac{\theta}{2} Z } = cos\left( \frac{\theta}{2} \right) I - i \sin\left( \frac{\theta}{2} \right) Z = 
  \begin{pmatrix}
    {e}^{ -i \frac{\theta}{2} } & 0 \\\\\\\\
    0 & {e}^{ i \frac{\theta}{2} }
  \end{pmatrix} 
\end{aligned}
\end{equation}


The Hadamard gate ${ H }$ satisfies ${ {H}^{2} = I }$ and ${ {H}^{\dagger} = H }$, and writes:  

\begin{equation}
\begin{aligned}
  H = \frac{1}{ \sqrt{2} } 
  \begin{pmatrix}
    1 & 1 \\\\\\\\
    1 & -1
  \end{pmatrix} 
\end{aligned}
\end{equation}

This gate puts a qubit in a pure state into a mixed state (superposition):

\begin{equation}
\begin{aligned}
  & H \ket{0} = \frac{1}{ \sqrt{2} } 
  \begin{pmatrix}
    1 & 1 \\\\\\\\
    1 & -1
  \end{pmatrix} 
	\begin{pmatrix}
    1 \\\\\\\\
    0 
  \end{pmatrix} 
  = \frac{1}{ \sqrt{2} } ( \ket{0} + \ket{1} ) \\\\\\\\
  & H \ket{1} = \frac{1}{ \sqrt{2} } 
  \begin{pmatrix}
    1 & 1 \\\\\\\\
    1 & -1
  \end{pmatrix} 
	\begin{pmatrix}
    0 \\\\\\\\
    1 
  \end{pmatrix} 
  = \frac{1}{ \sqrt{2} } ( \ket{0} - \ket{1} )
\end{aligned}
\end{equation}


## Two qubits

### two-qubit states

The two-qubit states can also be represented as matrices:
$$
\begin{equation}
  \ket{00} = 
  \begin{pmatrix}
    1 \\
    0 \\
    0 \\
    0 
  \end{pmatrix}, \quad 
  \ket{01} = 
  \begin{pmatrix}
    0 \\
    1 \\
    0 \\
    0 
  \end{pmatrix}, \quad 
  \ket{10} = 
  \begin{pmatrix}
    0 \\
    0 \\
    1 \\
    0 
  \end{pmatrix}, \quad 
  \ket{11} = 
  \begin{pmatrix}
    0 \\
    0 \\
    0 \\
    1 
  \end{pmatrix}
\end{equation}
$$

### two-qubit gates

The CNOT gate from 1 to 2 is denoted ${ \text{CNOT}_{10} }$ while the CNOT gate from 2 to 1 is denoted ${ \text{CNOT}_{01} }$:

\begin{equation}
\begin{aligned}
  \text{CNOT}_{10} =  
  \begin{pmatrix}
		1 & 0 & 0 & 0 \\\\\\\\
		0 & 1 & 0 & 0 \\\\\\\\
    0 & 0 & 0 & 1 \\\\\\\\
    0 & 0 & 1 & 0 
  \end{pmatrix}
\end{aligned}
\end{equation}


\begin{equation}
\begin{aligned}
  \text{CNOT}_{01} =  
  \begin{pmatrix}
		1 & 0 & 0 & 0 \\\\\\\\
		0 & 0 & 0 & 1 \\\\\\\\
    0 & 0 & 1 & 0 \\\\\\\\
    0 & 1 & 0 & 0 
	\end{pmatrix}
\end{aligned}
\end{equation}

The gates ${ {X}_{0} {X}_{1} }$, ${ {Y}_{0} {Y}_{1} }$, and ${ {Z}_{0} {Z}_{1} }$ can be obtained with the tensorial product ${ \otimes }$ of the one-qubit matrices:


\begin{equation}
\begin{aligned}
	X_0 \otimes X_1 =  
	\begin{pmatrix}
		0\begin{pmatrix} 
			0 & 1 \\\\\\\\
			1 & 0
		\end{pmatrix} & 1\begin{pmatrix}
											0 & 1 \\\\\\\\
											1 & 0
										\end{pmatrix} \\\\\\\\
    1\begin{pmatrix} 
			0 & 1 \\\\\\\\
			1 & 0
		\end{pmatrix} & 0\begin{pmatrix}
											0 & 1 \\\\\\\\
											1 & 0
										\end{pmatrix} 
  \end{pmatrix} = 
  \begin{pmatrix}
		0 & 0 & 0 & 1 \\\\\\\\
		0 & 0 & 1 & 0 \\\\\\\\
    0 & 1 & 0 & 0 \\\\\\\\
    1 & 0 & 0 & 0 
  \end{pmatrix}
\end{aligned}
\end{equation}




\begin{equation}
\begin{aligned}
	Y_0 \otimes Y_1 =  
	\begin{pmatrix}
		0\begin{pmatrix} 
				0 & -i \\\\\\\\
				i & 0
			\end{pmatrix} & -i\begin{pmatrix}
													0 & -i \\\\\\\\
													i & 0
												\end{pmatrix} \\\\\\\\
    i\begin{pmatrix} 
				0 & -i \\\\\\\\
				i & 0
			\end{pmatrix} & 0\begin{pmatrix}
													0 & -i \\\\\\\\
													i & 0
												\end{pmatrix} 
  \end{pmatrix} = 
  \begin{pmatrix}
		0 & 0 & 0 & -1 \\\\\\\\
		0 & 0 & 1 & 0 \\\\\\\\
    0 & 1 & 0 & 0 \\\\\\\\
    -1 & 0 & 0 & 0 
  \end{pmatrix}
\end{aligned}
\end{equation}

\begin{equation}
\begin{aligned}
	Z_0 \otimes Z_1 =  
	\begin{pmatrix}
		1\begin{pmatrix} 
				1 & 0 \\\\\\\\
				0 & -1
			\end{pmatrix} & 0\begin{pmatrix}
													1 & 0 \\\\\\\\
													0 & -1
												\end{pmatrix} \\\\\\\\
    0\begin{pmatrix} 
				1 & 0 \\\\\\\\
				0 & -1
			\end{pmatrix} & -1\begin{pmatrix}
													1 & 0 \\\\\\\\
													0 & -1
												\end{pmatrix} 
  \end{pmatrix} = 
  \begin{pmatrix}
		1 & 0 & 0 & 0 \\\\\\\\
		0 & -1 & 0 & 0 \\\\\\\\
    0 & 0 & -1 & 0 \\\\\\\\
    0 & 0 & 0 & 1 
  \end{pmatrix}
\end{aligned}
\end{equation}



