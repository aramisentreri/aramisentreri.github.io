---
layout: post
title: Feynman's proof of the Maxwell equations
tags: [Physics]
comments_id: 1
---
# Feynman's proof of the Maxwell equations

A few weeks ago, [Freeman Dyson](https://en.wikipedia.org/wiki/Freeman_Dyson), a renowned professor from the Institute for Advanced Study in Princeton, passed away. He was a very curious physicist, with many interests and wild thought experiments (see Dyson sphere). He was also a student of Feynman, and in October 1948, Feynman showed him a proof of Maxwell equations, assuming only Newton's law of motion and the commutation relation between position and velocity for a single nonrelativistic particle.

I know, weird huh?

This curious paper was published in ([Am. J. Phys. 58 (3), March 1990](https://aapt.scitation.org/doi/10.1119/1.16188)), and then brought to my attention by this awesome paper subscription service, [Fermat's Library](https://fermatslibrary.com/), that was celebrating Dyson's life.

For a math-physics enthusiast, this is a hardcore click-bait title. So I dived in. If you are curious, please see the paper [here](https://fermatslibrary.com/s/feynmans-proof-of-the-maxwell-equations).   

The algebra is simple enough, and one might think to understand it right away. Classic Feynman argumentation. The reality is that, after a little bit of probing ones own understanding, one realizes that nothing is really clear!

Take for example the first argument line:
Assume a particle exists with position $x_j\ (j=1,2,3)$ and velocity $\dot{x}_j$ satisfying Newton's equation

$$m\ddot{x}_j = F_j(x,\dot{x},t)$$

with commutation relations

$$[x_j, x_k] = 0,$$

$$[x_j, \dot{x}_k] = i\hbar \delta_{jk}.$$

"Sure" you might say, "seems reasonable"... Really though?
What is the commutator of $x_j$ and $x_k$? **What is** $x_jx_k - x_kx_j$? Is that multiplication?

What is $x_j$ itself? Is it really just a scalar function of time that gives you the position of the particle? What about $\dot{x}_k$?

I hope you see where I'm going here. If they are truly scalars, then both of the above commutation relations would be zero, because multiplication is commutative. But no, something is not being stated...

Let's try to figure it out.

## The roles of $x$ and $p$

We recognized above that $x(t)$ and $p(t)$ cannot be scalars (otherwise the commutator would be 0), therefore we need to consider them for what they truly are: Operators.  
1. $\bf x(t)$ is an operator that acts on a wave function $\psi$, by multiplying by $x$, i.e. ${\bf x(t)}(\psi) = x(t)\psi(x(t))$.

In the Statistical Interpretation of the wave function,

$$<x(t)> = \int \psi^* (x) x \psi(x) dx$$

is the average of measuring the position $x(t)$ on a very large number of equivalent systems, independent of each other and represented by the same wave function $\psi$. In a way, this Statistical framework gives us $<x(t)>$ to be the average trajectory, which is perhaps the best representation of the macroscopically observed trajectory. One for which equation \eqref{newton} is a good representation of its dynamics, i.e. _the mean values follow the classical laws of motion to a good approximation_.       
Let's assume then that this is the meaning by which Feynman and Dyson write equation (1).

But also lets remember the quantum mechanical interpretation of the operator $x(t)$: To be a measurement of the position of a particle in the quantum system whose evolution is described by the wave function $\psi(t,x)$ that satisfies Schroedinger equation,

$$ i\hbar \frac{d}{dt}\psi = H \psi. $$

2. What is $p$ then? 
This is when things become a little tricky, and we need to expand our thinking to consider this rigorously. $p$ is the operator that represents a measurement of the momentum of a particle. Given the wave like nature of the Schroedinger equation, it is an illustrative example to think of a plane wave to understand $p$.

For a plane wave (representing perhaps a photon of a given frequency $\omega$),
$$ \psi = e^{i({\bf k \cdot r} - \omega t)}$$
with the photon's momentum given by $p = k/\hbar$. 

Notice that for this example, it is easy to see that in order to recover the momentum of the plane wave, it's enough to take the derivative: 
$$ \frac{1}{i\hbar}\frac{\partial}{\partial x}\psi = \frac{1}{i\hbar}ik e^{i({\bf k\cdot r} - \omega t)} = \frac{k}{\hbar}= p$$

So as a first intuition, one might consider the momentum operator acting on a wave function $\psi$ as $ p \psi = \frac{1}{i\hbar}\frac{\partial}{\partial x} \psi$. 

More generally, any wave function can be written as a sum of plane waves (since these are a basis of the space of wave functions):

$$
\psi(t,x) = \frac{1}{(2\pi\hbar)^{\frac{3}{2}}} \int\limits_{\mathbb{R}^3} \Phi(p) e^{ip\cdot x} dp
$$

where $\Phi(p)$ is the Fourier transform of $\psi$, 

Add more detail...

Then in the general case, the momentum operator acts like a derivative: 
$$p = \frac{1}{i\hbar}\frac{\partial}{\partial x}.$$

## The evolution of a time dependent operator

Think of the evolution of an un-observed quantum system described by a wave function $\psi(t)$, that at some initial time started at a state $\psi(t_0)$.

We can therefore define an _Evolution Operator_ $U(t,t_0)$ such that 

$|\psi(t)> = U(t,t_0)|\psi(t_0)>$

as basically the operator that advances the state of a quantum system in time. 

We are interested in knowing how does this operator evolve in time, namely $\frac{d}{dt}U(t,t_0)$. 

I'm not sure if it's better to explain why now to motivate it, or if if should just find the derivative, and then use it. Let's motivate it. 

### Time derivative of a quantum operator

To calculate the derivative of an operator, we need to compute it as a limit, 
$\frac{d}{dt} x(t) = \lim\limits_{\epsilon\rightarrow 0} \frac{1}{\epsilon}(x(t+\epsilon) - x(t)),$
meaning that we should apply the operator $x(t+\epsilon)$ to a wave function $\psi$ and also apply the operator $x(t)$ to the same wave function $\psi$, then subtract and divide by $\epsilon$. 

But you see what I'm doing there? I'm hiding things because $\psi$ is a function that depends on time as well, and the operators $x(t)$ and $x(t+\epsilon)$ can't act on the function $\psi$ at the same time $t$, since we need to remember that $x$ is the operator that when you apply it to a quantum state, it should give you the collapsed _position_ of the particle whose evolution is being described by the probability density $\psi$. Therefore $x(t+\epsilon)$ is asking for a measurement of the position of a particle at time $t+\epsilon$, and $x(t)$ a measurement at time $t$. 

Does that makes sense? You can't just mix the two operators. We need to include something else. This is where the Evolution Operator comes into play. 

Consider the inverse of $U$, $U^\dagger(t,t_0)$ so that 
$$
U^\dagger(t,t_0) U(t,t_0) = I
$$

Intuitively this is like taking a quantum state at time $t$, and looking back in time to $t_0$. The benefit of this is that we can now define properly the application of the position operator at two different times $t+\epsilon$ and $t$. 

First, take the state of the quantum system at time $t+\epsilon$, $|\psi(t+\epsilon)>$ and apply $U^\dagger (t+\epsilon,t_0)$. 
$U^\dagger (t+\epsilon, t_0) |\psi(t+\epsilon)> = |\psi(t_0)>$

Notice that this state is independent of time. Now we can apply the position operator $x$, obtaining ???. Let's now evolve this value back to the time $t+\epsilon$, by applying $U(t+\epsilon, t_0)$. 

Therefore the position at $t+\epsilon$ is

$U(t+\epsilon, t_0)\ x\ U^\dagger(t+\epsilon, t_0) |\psi(t+\epsilon)>$ 

equivalently, the position at time $t$ is
$U(t,t_0)\ x\ U^\dagger(t, t_0).$

Putting things together we obtain that the derivative of $x$ is

$\lim\limits_{\epsilon\rightarrow 0} \frac{1}{\epsilon} (x(t+\epsilon) - x(t))|\psi> = \frac{1}{\epsilon} (U(t+\epsilon, t_0)\ x\ U^\dagger(t+\epsilon, t_0) - U(t, t_0)\ x\ U^\dagger(t, t_0))|\psi>$ 

Let's use the classic trick of adding and subtracting an intermediary term: $U(t,t_0)\ x\ U^\dagger(t+\epsilon, t_0)$,

$$
\lim\limits_{\epsilon\rightarrow 0} \frac{1}{\epsilon} (x(t+\epsilon) - x(t)) = \frac{1}{\epsilon} [U(t+\epsilon, t_0)\ x\ U^\dagger(t+\epsilon, t_0) - U(t,t_0)\ x\ U^\dagger(t+\epsilon, t_0)\\
+ U(t,t_0)\ x\ U^\dagger(t+\epsilon, t_0) - U(t, t_0)\ x\ U^\dagger(t, t_0)]\\
= (\frac{U(t+\epsilon,t_0) - U(t,t_0)}{\epsilon})\ x\ U^\dagger(t+\epsilon,t_0)\\
+ U(t,t_0)\ x\ (\frac{U^\dagger(t+\epsilon,t_0) - U^\dagger(t,t_0)}{\epsilon})
$$

So we recognize the following identity for the evolution of the operator 

$$
\frac{d}{dt}x(t) = \frac{dU}{dt}(t,t_0)\ x\ U^\dagger(t,t_0) + U(t,t_0)\ x\ \frac{dU^\dagger}{dt}(t,t_0)
$$

### Evolution of the Evolution operator $U(t,t_0)$

The evolution of an unobserved quantum system is described by the Hamiltonian, so we must find a relationship between $U(t,t_0)$ and $H(t)$. Lets provide the intuition.

Since the eigenvectors of $H$ form a basis for the function space of possible wave functions $\psi(t)$, we can determine $U(t,t_0)$ by computing its effects on each eigenvector. If for example $|u_E(t_0)>$ is the eigenvector associated with the eigenvalue $E$, then,

$$
\begin{equation}
H\ |u_E(t_0)>\ =  E\ |u_E(t_0)> 
\end{equation}
$$

Therefore, since the evolution of a system is given by Schroedinger equation, i.e.  $\frac{d}{dt} u_E(t) = H u_E(t) = E u_E(t)$, which is a simple 1D differential equation. 

Then $|u_E(t)> = e^{-i\omega(t-t_0)}|u_E(t_0)> = e^{-\frac{iE}{\hbar}(t-t_0)}|u_E(t_0)>$, where the last equality follows from $E= \hbar\omega$. 

Looking at that equation, a good a priory guess for $U(t,t_0)$ is,
$$
U(t,t_0) = e^{-i\frac{E}{\hbar}(t,t_0)}
$$
since then, $|u_E(t)> = U(t,t_0) |u_E(t_0)>$ .

Equivalently, one might define more generally $U(t,t_0)$ as the solution to the equation:
$$
i\hbar \frac{d}{dt}U(t,t_0) = H\ U(t,t_0)
$$


