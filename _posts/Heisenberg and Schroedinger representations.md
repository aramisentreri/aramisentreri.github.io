### Heisenberg and Schroedinger "representations"

From Messiah pg. 315:

In particular, one defines the Heisenberg "representation" by performing upon the kets and observables of the Schroedinger "representation" the unitary, time-dependent transformation $U^\dagger(t,t_0)$. Let us attach the subscript S to the old quantities, and the subscript H to the new quantities. The ket 
$$
|\psi_S(t)> = U(t,t_0) |\psi_S(t_0)>\nonumber
$$

which represents the dynamical state of the of the system at time $t$ is transformed into a stationary ket 
$$
|\psi_H> = U^\dagger(t,t_0) |\psi_S(t)> = |\psi_S(t_0)> \nonumber
$$
The same transformation can be done to an operator (or "observable") $A_S$ of the Schroedinger "representation", 
$$
A_H = U^\dagger(t,t_0) A_S U(t,t_0)\nonumber
$$
so that
$$
A_H |\psi_H>\ =\ U^\dagger(t,t_0) A_S U(t,t_0)\ U^\dagger(t,t_0) |\psi_S(t)>\\
= U^\dagger(t,t_0) A_S |\psi_S(t)>
$$
To fully understand, lets suppose that $\psi_S$ is an eigenvector of $A_S$ , so that $A_S |\psi_S> = a|\psi_S>$, then the above equation looks like
$$
A_H |\psi_H> = U^\dagger(t,t_0) A_S|\psi_S(t)> = U^\dagger(t,t_0) a|\psi_S(t)> = a\ U^\dagger(t,t_0)|\psi_S(t)> =  a\ |\psi_H>\nonumber
$$
This way of understanding the evolution of a system, both as a dynamical state $|\psi(t)>$ and the transformed stationary version $|\psi(t_0)>\ = U^\dagger(t,t_0)\ |\psi(t)>$ are typically referred to as **Schroedinger** and **Heisenberg** "representations". 

They are not precisely "representations" in the way we think about representing vectors and matrices, but more as a way of "descriptions of the system".