---
layout: post
title: Feynman's proof of the Maxwell equations
tags: [Physics]
comments_id: 1
use_math: true
---
# Feynman's proof of the Maxwell equations

A few weeks ago, [Freeman Dyson](https://en.wikipedia.org/wiki/Freeman_Dyson), a renowned professor from the Institute for Advanced Study in Princeton, passed away. He was a very curious physicist, with many interests and wild thought experiments (see Dyson sphere). He was also a student of Feynman, and in October 1948, Feynman showed him a proof of Maxwell equations, assuming only Newton's law of motion and the commutation relation between position and velocity for a single nonrelativistic particle.

I know, weird huh?

This curious paper was published in ([Am. J. Phys. 58 (3), March 1990](https://aapt.scitation.org/doi/10.1119/1.16188)), and then brought to my attention by this awesome paper subscription service, [Fermat's Library](https://fermatslibrary.com/), that was celebrating Dyson's life.

For a math-physics enthusiast, this is a hardcore click-bait title. So I dived in. If you are curious, please see the paper [here](https://fermatslibrary.com/s/feynmans-proof-of-the-maxwell-equations).   

The algebra is simple enough, and one might think to understand it right away. Classic Feynman argumentation. The reality is that, after a little bit of probing my own understanding, I realized that nothing was really clear! My brain always tried to trick me like this, but I've learned this lesson many times. I do not know anything until I can explain all the details clearly. And trust me, the devil is always in the details.

Take for example the first argument line in 1D: Assume a particle exists with position $x$ and velocity $\dot{x}$ satisfying Newton's equation

$$ m\ddot{x} = F(x,\dot{x},t)\label{eq:newton} $$

with commutation relations $[x, x] = 0,$ $m[x, \dot{x}] = i\hbar$.

"Sure" you might say, "seems reasonable" since we have all seen these commutation relations before... Really though? What **is** the commutator of $x$ and $\dot{x}$? **What** is $x\dot{x}$? Is that multiplication?

What is $x(t)$ itself? Is it really just a scalar function of time that gives you the position of the particle? What about $\dot{x}(t)$?

I hope you see where I'm going here. If they are truly scalars, then both of the above commutation relations would be zero, because multiplication is commutative. But no, something is not being stated... They can't possible be scalars, and so what is the meaning of equation $\eqref{eq:newton}$?

Let's try to figure it out.

## The roles of $x$ and $p$

Lets start by recognizing that the second commutation relation looks like the commutator of $[x,p]$ from Quantum Mechanics, but it is somehow assumed that $m\dot{x} = p$. Is that true? I mean it is certainly true when we are talking about scalars, but at the same time scalars commute, so... what's the dealio my friends?

For the sake of this discussion, lets start with just considering $x$ and $p$. _Future Gustavo_ can figure out why is $m\dot{x} = p$ later.   

We recognized above that $x$ and $p$ cannot be scalars in the typical sense, otherwise the commutator would be 0. Therefore we need to consider them for what they truly are: Operators.

### Operators  

In Quantum Mechanics, the state of a system is described by a wave function $\psi(t)$, or sometimes written down as a "ket": $|\psi(t)>$. Don't be frightened, they are the same thing. Writing it like this just helps with some algebra.

When we try to observe some physical quantity $\mathcal{A}$ of the system, like its position or momentum, there exists an associated linear operator to that quantity $\hat{\mathcal{A}}$. The eigenvalues of $\hat{\mathcal{A}}$ correspond to the possible values that the physical quantity can take.  

In the case of $\bf x(t)$, the paper is ambiguous as to which are we referring to, the physical quantity, or the operator that acts on a wave function $\psi$. Mathematically, it requires a little bit of formalism to understand how it works when applied to an arbitrary state $\psi$, but intuitively it suffices to say that the operator $\bf x(t)$ measures the position of the particle at time $t$.

So, if $\psi(x)$ is the wave function when the particle is in position "$x$", then
$$
\hat{\bf x} \psi(x) = x\psi(x) \nonumber
$$
where on the right side, the "$x$" is now a scalar multiplying the function $\psi(x)$. Operator on the left, scalar on the right.

What is $\bf p$ then?
$\bf{p}$ is the operator that represents a measurement of the momentum of a particle, but unlike $\bf x$, the associated operator analogue $\hat{\bf p}$ is easier to understand without heavy formalism. Yay!

Given the wave like nature of the Schroedinger equation, it is an illustrative example to think of a plane wave to understand $p$. For a plane wave (representing perhaps a photon of a given frequency $\omega$), the wave function takes a simple form,
$$
\psi(t,x) = e^{i({k x} - \omega t)}\nonumber
$$
with the photon's momentum given by $p = k\hbar$. Notice that for this example, it is easy to see that in order to recover the momentum of the plane wave, it's enough to take the derivative and multiply by $\frac{\hbar}{i}$:
$$
\frac{\hbar}{i}\frac{\partial}{\partial x}\psi = \frac{\hbar}{i}ik e^{i({kx} - \omega t)} = k\hbar\ e^{i({k x} - \omega t)}= p\ \psi(t,x) \nonumber
$$

So as a first intuition, one might consider the momentum operator acting on a wave function $\psi$ as
$$
\hat{\bf p}\ \psi = \frac{\hbar}{i}\frac{\partial}{\partial x} \psi \label{eq:momentum}
$$

For now, we will assume the form $\eqref{eq:momentum}$ for all wave functions, but you can see the notes at the end of the article for more details on a general case (instead of just a plane wave).

### The proper proof of the commutation relation

So now we have a proper description of both operators $\hat{\bf x}$ and $\hat{\bf p}$, and we can identify the commutator applied to a wave function $\psi$:
$$
\left[\hat{x},\hat{p}\right]\psi = \hat{x}\hat{p}\psi - \hat{p}\hat{x}\psi \\
= x\frac{\hbar}{i}\frac{\partial}{\partial x}\psi - \frac{\hbar}{i}\frac{\partial}{\partial x} (x\psi)\\
= \frac{\hbar}{i}\left( x\frac{\partial \psi}{\partial x} - \psi - x\frac{\partial \psi}{\partial x}\right)\\
= -\frac{\hbar}{i}\psi \nonumber
$$
where we used in the third line the derivative of the product rule, and that the derivative of $x$ is 1. So we can write that, as operators, $\hat{\bf x}$ and $\hat{\bf p}$ do not commute, and instead,
$$
[\hat{\bf x}, \hat{\bf p}] = - \frac{\hbar}{i} = i\hbar\nonumber
$$

## The evolution of a time dependent operator

Remember above when I delegated the responsibility of explaining why $m\dot{x} = p$ to _future Gustavo_? Well, the future is here. sigh. **Time to clarify what is the relationship between $p$ and $\dot{x}$ as operators.**

We'll start with $\dot{x}$ -- Typically, the dot signifies a time derivative. A time derivative of the position operator?But time derivatives are for functions that change in time.... soooo... how?

Ok, let's start with exploring something simpler, like the evolution of a quantum system in time:  

#### The Evolution Operator

Think of the evolution of an un-observed quantum system described by a wave function $\psi(t)$, that at some initial time started at a state $\psi(t_0)$.

We can therefore define an _Evolution Operator_ $U(t,t_0)$ such that

$$
|\psi(t)>\ = U(t,t_0)\ |\psi(t_0)> \nonumber
$$

as basically the operator that advances the state of a quantum system in time. We are interested in knowing how does this operator evolve in time, namely $\frac{d}{dt}U(t,t_0)$.

I'm not sure if it's better to explain why now, to motivate it, or if if should just find the derivative, and then use it... Let's motivate it first!

#### Time derivative of a quantum operator

To calculate the derivative of an operator, we need to compute it as a limit,
$$
\frac{d}{dt} \hat{x}(t) = \lim\limits_{\epsilon\rightarrow 0} \frac{1}{\epsilon}(\hat{x}(t+\epsilon) - \hat{x}(t)), \nonumber
$$
meaning that we should apply the operator $\hat{x}(t+\epsilon)$ to a wave function $\psi$ and also apply the operator $\hat{x}(t)$ to the same wave function $\psi$, then subtract and divide by $\epsilon$.

But you see what I'm doing there? I'm hiding things because $\psi$ is a function that depends on time as well, and the operators $\hat{x}(t)$ and $\hat{x}(t+\epsilon)$ can't act on the function $\psi$ at the same time $t$, since we need to remember that $\hat{x}$ is the operator that when you apply it to a quantum state, it should give you the collapsed _position_ of the particle whose evolution is being described by the probability density $\psi$. Therefore $\hat{x}(t+\epsilon)$ is asking for a measurement of the position of a particle at time $t+\epsilon$, and $\hat{x}(t)$ a measurement at time $t$.

Does that makes sense? You can't just mix the two operators. We need to include something else. This is where the **Evolution Operator** comes into play. Consider as well the inverse of $U$, $U^\dagger(t,t_0)$ so that

$$
U^\dagger(t,t_0) U(t,t_0) = I \nonumber
$$

Intuitively, applying the operator $U^\dagger(t,t_0)$ is like taking a quantum state at time $t$, and looking back in time to $t_0$. The benefit of this is that we can now define properly the application of the position operator at two different times $t+\epsilon$ and $t$.

For example, to sample $\hat{x}(t+\epsilon)$, first evolve the state of the initial quantum system to the time $t+\epsilon$, by applying $U(t+\epsilon,t_0)$:
$$
|\psi(t+\epsilon)> = U(t+\epsilon,t_0) |\psi(t_0)>.\nonumber
$$
Now we can apply the position operator $\bf \hat{x}$ to this state to get the position at time $t+\epsilon$, and then revert back to the time independent state $|\psi(t_0)>$ by applying the inverse $U^\dagger(t+\epsilon,t_0)$:

$$
U^\dagger(t+\epsilon, t_0)\ {\bf \hat{x}}\ U(t+\epsilon, t_0) |\psi(t_0)>\nonumber
$$

The result of this operation would be a scalar for the position $x(t+\epsilon)$ for the collapsed wave function at that position. Equivalently, to get the position at time $t$, all we have to do is compute:
$$
U^\dagger(t,t_0)\ {\bf \hat{x}} \ U(t, t_0) |\psi(t_0)>.\nonumber
$$

Putting things together we obtain that the derivative of $x$ is

$$
\lim\limits_{\epsilon\rightarrow 0} \frac{1}{\epsilon} (\hat{x}(t+\epsilon) - \hat{x}(t))|\psi> = \lim\limits_{\epsilon\rightarrow 0}\frac{1}{\epsilon} \left(U^\dagger(t+\epsilon, t_0)\ \hat{x}\ U(t+\epsilon, t_0) - U^\dagger(t, t_0)\ \hat{x}\ U(t, t_0)\right)|\psi(t_0)> \nonumber
$$

Let's use the classic trick of adding and subtracting an intermediary term: $U^\dagger(t,t_0)\ \hat{x}\ U(t+\epsilon, t_0)$,

$$
\lim\limits_{\epsilon\rightarrow 0} \frac{1}{\epsilon} (\hat{x}(t+\epsilon) - \hat{x}(t)) = \lim\limits_{\epsilon\rightarrow 0}\frac{1}{\epsilon} [U^\dagger(t+\epsilon, t_0)\ \hat{x}\ U(t+\epsilon, t_0) {\color{red}- U^\dagger(t,t_0)\ \hat{x}\ U(t+\epsilon, t_0)}\\
{\color{red}+ U^\dagger(t,t_0)\ \hat{x}\ U(t+\epsilon, t_0)} - U^\dagger(t, t_0)\ \hat{x}\ U(t, t_0)]\\
= \lim\limits_{\epsilon\rightarrow 0}(\frac{U^\dagger(t+\epsilon,t_0) - U^\dagger(t,t_0)}{\epsilon})\ \hat{x}\ U(t+\epsilon,t_0)\\
+ \lim\limits_{\epsilon\rightarrow 0}U^\dagger(t,t_0)\ \hat{x}\ (\frac{U(t+\epsilon,t_0) - U(t,t_0)}{\epsilon}) \nonumber
$$

So we recognize the following identity for the evolution of the operator $\hat{x}$:

$$
\frac{d}{dt}\hat{x}(t) = \frac{dU^\dagger}{dt}(t,t_0)\ \hat{x}\ U(t,t_0) + U^\dagger(t,t_0)\ \hat{x}\ \frac{dU}{dt}(t,t_0)
\label{ref1}
$$

#### Evolution of the Evolution operator $U(t,t_0)$

The evolution of an unobserved quantum system is described by the Hamiltonian, so we must find a relationship between $U(t,t_0)$ and $H(t)$. Lets provide the intuition.

Since the eigenvectors of $H$ form a basis for the function space of possible wave functions $\psi(t)$, we can determine $U(t,t_0)$ by computing its effects on each eigenvector. If for example $|u_E(t_0)>$ is the eigenvector associated with the eigenvalue $E$, then,

$$
\begin{equation}
\hat{H}\ |u_E(t_0)>\ =  E\ |u_E(t_0)>
\end{equation}\nonumber
$$

Therefore, since the evolution of a system is given by Schroedinger equation, i.e.  
$$
i\hbar\frac{d}{dt} u_E(t) = \hat{H}\ u_E(t) = E\ u_E(t) \nonumber
$$
we obtain that $u_E$​ satisfies a simple 1D differential equation. Then

$$
|u_E(t)> = e^{-i\omega(t-t_0)}|u_E(t_0)> = e^{-\frac{iE}{\hbar}(t-t_0)}|u_E(t_0)>,\nonumber
$$
where the last equality follows from $E= \hbar\omega$. Looking at that equation, we can recognize what is the "factor" (*double entendre*, get it?) that evolves $u_E(t_0)$ to $u_E(t)$: $e^{-\frac{iE}{\hbar}(t-t_0)}$, so a good a priory guess for $U(t,t_0)$ is,

$$
U(t,t_0) = e^{-i\frac{E}{\hbar}(t,t_0)}\nonumber
$$
since then, $|u_E(t)> = U(t,t_0) |u_E(t_0)>$ . Equivalently, one might define more generally $U(t,t_0)$ by looking at the Schroedinger equation re-written in terms of $U$:

$$
i\hbar\frac{d}{dt} \psi(t) = H\ \psi(t)\\
i\hbar \frac{d}{dt} U(t,t_0)\psi(t_0) = H\ U(t,t_0) \psi(t_0)\\
\Rightarrow \left[i\hbar \frac{d}{dt}U(t,t_0) - H\ U(t,t_0)\right]\psi(t_0) = 0 \nonumber
$$
Where in the last line we recognize the functional equation:
$$
i\hbar \frac{d}{dt}U(t,t_0) = H\ U(t,t_0)\label{eq:evol_u}
$$
which is an equality of operators.

#### Putting things together

Going back to $\eqref{ref1}$, and replacing this equality $\eqref{eq:evol_u}$, we obtain that
$$
\frac{d}{dt}\hat{x}(t) = - \frac{1}{i\hbar}U^\dagger(t,t_0) H^\dagger \hat{x}\ U(t,t_0) + U^\dagger(t,t_0)\ \hat{x}\ \frac{1}{i\hbar}H\ U(t,t_0) \\
= \frac{1}{i\hbar}(-U^\dagger H {\color{red} U\ U^\dagger} \hat{x}\ U + U^\dagger\ \hat{x}\ {\color{red} U\ U^\dagger} H\ U) \\
= \frac{1}{i\hbar}[U^\dagger \hat{x} U, U^\dagger H U]\\
= \frac{1}{i\hbar}[x(t), H(t)]\\
= \frac{\partial H}{\partial p_x} \nonumber
$$

Where we used that $H$ is Hermitian ( $H^\dagger = H$ ), a "multiplying by the identity" trick (in red), and the definition of the commutator to put things in the brackets. The last two lines are key, because we are using that the operators $U^\dagger H U$ and $U^\dagger \hat{x} U$ are just the time independent versions of $H(t),\ x(t)$, so we can reduce them back, and finally use the known commutator properties to get the last line.  

Finally, to take the derivative of $H$ with respect to $p$, we will use the Hamiltonian for a particle under a potential $V(x)$,
$$
H = \frac{\hat{p}^2}{2m} + \hat{V}(x)\nonumber
$$
Then
$$
\frac{d\hat{x}}{dt} = \frac{\hat{p}_x}{m}\nonumber
$$

which is exactly what we wanted, but we proved it **as operators!**



## Conclusions

Freeman Dyson published Feynman's argument to derive Maxwell's equations from Newton's equation and the basic commutation relations:


$$
m\ddot{x} = F(t,x,\dot{x}),\ \text{ and }\ [x,x] = 0,\ m[x,\dot{x}] = i\hbar \nonumber
$$

These assumptions look simple and familiar, but hidden behind them are the profound fundamentals of Quantum Mechanics, and how it differs from Classical Mechanics.

How very tricky of Feynman to hide all the mathematical details to get on with calculating! I can imagine Dyson complaining to Feynman about rigor while Feynman, smiling, would shake his arms and head, impatiently following his [correct] intuition. This image, that may very well be false, makes me smile.    

As we learned in this article, there is actually nothing wrong with this "intuitive" approach. All their claims were correct if you understood the context in which they were being discussed, so we can forgive Dyson and Feynman for their wonderfully creative disregard for rigorous mathematics! Specially since you know... they are masters of the subject.

There is a lot of other interesting aspects of this paper that I could write about, but I'll leave you with this: The approach of the paper is actually incorrect. It's missing something important as brought up by multiple editorial comments and by Dyson himself:

"*The Maxwell equations are relativistically invariant, while the Newtonian assumptions, which Feynman used for his proof, are nonrelativistic. The proof begins with assumptions invariant under Galilean transformations and ends with equations invariant under Lorentz transformations. How could this have happened? After all, it was the incompatibility between Galilean mechanics and Maxwell electrodynamics that led Einstein to special relativity in 1905. Yet here we find Galilean mechanics and Maxwell equations coexisting peacefully. Perhaps it was lucky that Einstein had not seen Feynman's proof when he started to think about relativity*."  

So if this derivation is wrong because it started with nonrelativistic equations, what happens if we start, instead of with Newton's second law, with Dirac's equation?
$$
E^2 = m^2c^4 + p^2c^2\nonumber
$$


I'm sure it would be super cool to try it.

---

#### Notes

##### General proof of $\hat{p} = \frac{\hbar}{i}\frac{\partial}{\partial x}$

Any wave function can be written as a sum of plane waves (since these are a basis of the space of wave functions):

$$
\psi(x) = \frac{1}{(2\pi\hbar)^{\frac{3}{2}}} \int\limits_{\mathbb{R}^3} \Phi(p) e^{ik\cdot x} dp \nonumber
$$

where $\Phi(p)$ is the Fourier transform of $\psi$, so in the general case it is also true that the momentum operator acts like a derivative:
$$
\frac{\hbar}{i}\frac{\partial}{\partial x}\psi = \frac{\hbar}{i}\frac{\partial}{\partial x}\left[\frac{1}{(2\pi\hbar)^{\frac{1}{2}}} \int\limits_{\mathbb{R}} \Phi(p) e^{ik\cdot x} dp\right]\\= \frac{\hbar}{i}\frac{1}{(2\pi\hbar)^{\frac{1}{2}}} \int\limits_{\mathbb{R}} \Phi(p) \frac{\partial}{\partial x} e^{ik\cdot x} dp \\= \frac{ik\hbar}{i}\left[\frac{1}{(2\pi\hbar)^{\frac{1}{2}}} \int\limits_{\mathbb{R}} \Phi(p) e^{ik\cdot x} dp\right]\\= k\hbar\ \psi\\= p\ \psi \nonumber
$$

The derivative goes inside the integral, because the only thing dependent on $x$ is the exponential function, but that one doesn't change after the derivative, except for the coefficients $ik$, which we pull back outside the integral. We recognize then that $p=k\hbar$ to finish out the proof.
