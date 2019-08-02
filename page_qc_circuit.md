---
layout: default
title: Quantum computing circuits
description: Basic circuits
future: true
---

[back](./)

$$
\begin{equation}
\Qcircuit @C=1em @R=.7em {
  \lstick{\ket{\psi}_C}   & \ctrl{1} & \gate{H} & \meter                  & \control \cw \\
  \lstick{\ket{\Phi}^+_A} & \targ    & \meter   & \control \cw \cwx[1] \\
  \lstick{\ket{\Phi}^+_B} & \qw	     & \qw      & \targ                   & \control \cwx[-2] \qw & \rstick{\ket{\psi}_B} \qw
 }
\end{equation}
$$


[back](./)
