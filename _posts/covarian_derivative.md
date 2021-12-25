## Covariant derivative of a Tensor

This last weekend I had a super good time with a friend, just spending a few hours figuring out some math from the physics behemoth "Gravity" by Misner, Wheeler and Thorne. I have some experience with general relativity and differential geometry, but I've never made it very far into the field, so we just opened the textbook, somewhere in Chapter 2, and looked in for entertainment:   

Consider a 1-1 tensor $T$ (sometimes written as $T^i_j$ as well), and let's attempt to compute the covariant derivative of it.

But first, what is the covariant derivative anyways?

$\nabla_{\bf u} T$ := ??

In some textbooks that lean towards the more abstract description of differential geometry (like in Wald's General Relativity for example), they define it as an operator that satisfy a few properties: 

1. Linearity
2. Leibnitz/Product rule
3. Effect on scalar functions
4. ??
5. Torsion free (this one being optional some times)

The geometric way of understanding and defining the covariant derivative, and the one I thought I remembered is as follows: 

Given a point $p$ in M, and a (tangent) vector $\bf u$  in $T_p$, consider a curve that passes through $p$ in the direction of $\bf u$ described by the parameter $\lambda$: 

$x^\mu (\lambda)$ so that $\frac{d x^\mu}{d\lambda}\vert_{\lambda=0} = {\bf u}$  

With this parametrization of the curve, we can describe the covariant derivate as simply the rate of change of the tensor $T(x^\mu(\lambda))$: 

$$ \nabla_{\bf u} T = \frac{d T (x^\mu(\lambda))}{d\lambda}$$

My intuition worked pretty well for vector fields, which correspond to what is called as _0-1 tensors_, because you can write a tensor/vector as a sum over the basis of the tangent plane at the point $T_p$:
$$
T = \sum\limits_{i=1}^nT_i {\bf e_i} = T_i {\bf e_i} \text{ (using Einstein sumation convention)}
$$
Where the $\bf e_i$ are basis vectors of the vector space $T_p$. Therefore the parametric definition of the covariant derivative looks like: 

$$
\nabla_{\bf u} T =  \frac{d T (x^\mu(\lambda))}{d\lambda} = \frac{d}{d\lambda}(T_i {\bf e_i}) = \frac{d T_i(x(\lambda))}{d\lambda} {\bf e_i}  + T_i \frac{d {\bf e_i}(x(\lambda))}{d\lambda}
$$

$$
= \frac{\partial T_i}{\partial x^\mu}\frac{d x^\mu}{d \lambda} {\bf e_i} + T_i  \frac{d {\bf e_i}}{d x^\gamma} \frac{d x^\gamma}{d \lambda}
$$



Then we notice on the second term of the sum, that $\frac{d{\bf e_i}}{d x^\gamma}$ is a vector as well (the variation of $e_i$ along the curved trajectory), so it can be written as a sum of the basis vectors $\bf e_i$

$$
\frac{d{\bf e_i}}{d x^\gamma}  = \sum\limits_{j}\Gamma^j_{i\gamma} {\bf e_j}
$$

where we are calling the coefficients as $\Gamma^j_{i\gamma}$, sometimes referred to as the _Christoffel symbols_.

Ok so, if we put some things together, for example noticing that $\frac{d x^\mu}{d \lambda} = u^\mu$, exchanging the indices $i$ and $j$ on the second term, and renaming the $\gamma$ and $\mu$ indices as well, we get that 

$$
\label{eq:cov_der_scalar}
\nabla_{\bf u} T = T_{i,\mu} u^\mu {\bf e_i} + T_i \Gamma^j_{i\gamma} u^\gamma {\bf e_j} = T_{i,\mu} u^\mu {\bf e_i} + T_j \Gamma^i_{j\gamma} u^\gamma {\bf e_i} = (T_{i,\gamma} + T_j \Gamma^i_{j\gamma})u^\gamma{\bf e_i}
$$

So that in terms of components, some people chose to write the covariant derivative as 

$$
\label{eq:misleading}
\nabla_{\gamma} T = T_{i;\gamma} = T_{i,\gamma} + \Gamma^i_{j\gamma} T_j
$$
but this is of course incomplete if not a little misleading too. The cruelty of geometers... (and mathematicians in general). This is what I would call an abuse of notation. It's only allowed if you are an expert in the field. For the rest of the mortals, please write everything out! 



## Second section

So just from this brief and intuitive analysis based on the geometric idea, we can see that we want the Covariant derivative (as described in equation $\eqref{eq:misleading}$) to be at least an operator that takes tangent vectors $T$ (aka 0-1 tensors), and transforms them into a 1-1 tensor. 

> Note: What is a 1-1 tensor anyway?  In equation $\eqref{eq:misleading}$, in order to complete the actual formula without abuse of notation, or better said to complete the expression so that the outcome is a scalar, one needs to "multiply" (and add with Einstein notation) the 2 terms: $u^\gamma$ and $e_i$, like in equation $\eqref{eq:cov_der_scalar}$. 
> We refer to $e_i$ as a tangent vector, because as we defined it above, it is a basis vector that lives in the tangent plane $T_p$ (at the point p). This is also a 0-1 tensor.
> In contrast, we consider $u^\gamma$ to be a contravariant vector (is this the right name???), or a 1-0 tensor, because in order to get a scalar one needs to "multiply" it with a 0-1 vector (like the $e_i$ for example). One can think of contravariant or 1-0 tensors as linear functions on the tangent space $T_p$, as in the act/operate on vectors, like a linear function: 

$$
\mathbb{L}(v) = u^\gamma v_\gamma
$$
Note: Why is it then that this "linear functional" is also a set of numbers $u^\gamma$ that just multiply in order to act? 
Well, this comes from the fact that the only linear functionals in a vector space are constants. (refine this point)  

But don't worry if you don't grasp this right away. Thinking like this takes some time. I don't want to encourage you skip it though, cause Physicists normally would underplay the importance of understanding that fact (that 1-0 tensors or contravariant vectors are linear functions over the tangent space of vectors), but later on when one tries to look at harder material, this gap will cost you greatly.  

## Third section: What happens if we take the covariant derivative of a contravariant vector (1-0 tensor)?

First it is important to understand what are we trying to do, or what does it mean to compute the covariant derivate of a 1-0 tensor? What are we after? 

We need to concretize the problem: Say $w^i$ is a contravariant vector 1-0 tensor. What does it mean to derive it covariantly?
Well, the geometric idea in my mind is that now we have a field/function that is meant to operate on tangent vectors of different points in a manifold, but it acts (as a function) differently depending in which point of the manifold you are. 
So the covariant derivative is trying to compute the rate of change of this linear function across the manifold in some tangent vector's direction. 



Since we want to compute a derivative of $w^i$ , we have to do this at a point of the manifold $p$, and in some direction $\bf u$ that lives in the tangent plane at p, so just like before, we consider a parametrization $x^\mu (\lambda)$ so that $\frac{d x^\mu}{d\lambda}\vert_{\lambda=0} = {\bf u}$. But notice that now we want to evaluate $w$ along the curve (not just at one point $p$)! The point $p$ is somewhat changing, and therefore so is the tangent plane $T_p$. This means that we actually need to choose a sequence of vectors $v(p)\in T_p$ for $p$ along the curve.  Then, we can take the derivative of this scalar over the manifold along the curve $x(\lambda)$,
$$
\frac{d}{d\lambda} (w_{x(\lambda)} [v(x(\lambda))]) = ??
$$
  $w = w^i de_i$ where $de_i$ is the $i$ base element of the Co-tangent space (or space of linear functionals over $T_p$), i.e. $de_i(e_j) = \delta_{ij}$

This last statement is the magic key: Since $\delta_{ij}$ is a constant, the derivative with respect to $\lambda$ is zero, therefore:
$$
\frac{d}{d\lambda} de^i(e_j) = 0
$$

$$
\frac{d de^i}{d\lambda} e_j + de^i \frac{d e_j}{d\lambda} = 0
$$

this last one is not right :( 

