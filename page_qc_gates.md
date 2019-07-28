---
layout: default
title: Quantum computing gates
description: One- and two-qubit gates
future: true
---

[back](./)

## One qubit

### Spin $${ 1/2 }$$ representation and conventions

$$
\newcommand{\bra}[1]{\left<#1\right|}
\newcommand{\ket}[1]{\left|#1\right>}
\begin{equation}
  \ket{ s = 1/2, {m}_{s} = \pm 1/2 } = \ket{\pm}
\end{equation}
$$
Sometimes the kets $${ \ket{\pm} }$$ are used for Bell states [check that]. The convention is to take $${ \ket{+} = \ket{0} }$$ and $${ \ket{-} = \ket{1} }$$, so in the matrix representation one has:  

$$
\newcommand{\bra}[1]{\left<#1\right|}
\newcommand{\ket}[1]{\left|#1\right>}
\begin{align}
  & \ket{+} = \ket{0} = 
  \begin{pmatrix}
    1 \\
    0
  \end{pmatrix} \\
  & \ket{-} = \ket{1} = 
  \begin{pmatrix}
    0 \\
    1
  \end{pmatrix}
\end{align}
$$  

### Pauli matrices

Pauli matrices are the building blocks for all operations acting on spins $${ 1/2 }$$ and, in the same representation, are defined as:  

$$
\begin{align}
  & {\sigma}_{1} =  
  \begin{pmatrix}
    0 & 1 \\
    -1 & 0
  \end{pmatrix} 
  = X \\
  & {\sigma}_{2} =  
  \begin{pmatrix}
    0 & i \\
    -i & 0
  \end{pmatrix} 
  = Y \\
  & {\sigma}_{3} =  
  \begin{pmatrix}
    1 & 0 \\
    0 & -1
  \end{pmatrix} 
  = Z
\end{align}
$$  


  

[back](./)
