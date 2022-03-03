# Barrier functions
And their use in theoretical analysis of PDEs to determine maximum principles

## Optimization
From Wikipedia:
> In constrained optimization a barrier function is a continuous function whose value on a point increases to infinity as the point approaches de boudary of the feasible region of an optimization problem. Such functions are used to replace inequality constraints by a penalizing term in the objective functions that is easier to handle. 

Example:
![[Pasted image 20201116223940.png]]

### Logarithmic barrier function
>For logarithmic barrier functions, $g(x,b)$  is defined as $−log⁡(b−x)$ when $x<b$ and $\infty$ otherwise.
This introduces a gradient to the function being optimized which favors less extreme values of $x$ (in this case values lower than $b$, while having relatively low impact on the function away from these extremes. 

Basically a logaritmic barrier function achieves the goal of pushing the optimal points away from the boundary, while keeping a smooth and differentiable objective function that is more ameanable to iterative solutions, like for example the [interior point method](https://en.wikipedia.org/wiki/Interior-point_method).  

## Maximum principle 
## What is the maximum principle
In it's most basic form, the maximum principle is just a more complete (and higher dimensional) version of 
![[plus_minus_convex.png]]
which says that if the second derivative of a function is negative, then the function is concave (or concave down as it is sometimes referrred), and if the second derivative is positive, the function is convex (or "concave up").

This means that if a function is for example convex in an interval $[a,b]$, then necessarily due to the function's shape (smiley up), the maximum of the function is on the boundary, meaning the endpoints of the interval (either a or b since it's 1D).
But there is more, we know also that the function's slope at the edges has to be "pointing up", which matematically can be expressed as: $df/dx(a) < 0$ and $df/dx(b) > 0$. More succintly $\frac{\partial f}{\partial \nu} (x) > 0$ for $x\in \partial\Omega$, where $\nu$ is the outward pointing normal vector to the boundary at x.  
The generalized version of this last statement it's referred to as Hopf's lemma. 

Of course, a self respecting Maximum principle theorem is more generalized, describing operators in many dimensions and more "complex" than just the second derivate in 1D, called "Elliptic operators", that satisfy the uniform ellipticity condition among other hypothesis, but the idea is pretty much the same.   

## How does a barrier function and a maximum principle connected? 
Given an elliptic operator that doesn't perhaps fall entirely within the hypothesis of the maximum principle, so that we can't apply its conclusions on a function that satisfy said elliptic equation, then we are left without a clue regarding the behaviour of this solution.   Using a smart choice of a barrier function, one can change this situation, and establish a version of the maximum principle that indeed gives us the behaviour of any function satisfying the elliptic equation.

For example, let's study this example from Evan's book in PDEs, pg. 367 problem 9:

---
Assume $u$ is a smooth solution of $Lu = -\sum\limits_{i,j=1}^{n} a^{ij} u_{,ij} = f$ in $U$, $u=0$ in $\partial U$, where $f$ is bounded. Fix $x_0\in\partial U$. A _barrier_ at $x_0$ is a $C^2$ function $w$ such that
$$
Lw \geq 1\ \text{in } U,\ w(x_0) = 0,\ w\geq 0\ \text{ on } \partial U.
$$
Show that if $w$ is a barrier at $x_0$, there exists a constant $C$ such that
$$
|Du(x_0)| \leq C|\frac{\partial w}{\partial \nu}(x_0)|
$$
---
>Notice the key thing here. There mere **existence** of $w$ has implications on $u$, in particular the bound on the gradient of $u$ at that boundary point. 

The proof of this problem is not difficult if you know the trick ;) If you don't know it yet, don't worry, and get ready to put this bad boy in your arsenal os magic tricks.

### Proof
We will consider the sum: $u +\beta w$, with $\beta$ a constant to be determined. Let's apply the elliptic operator
$$
L(u + \beta w) = Lu + \beta Lw = f + \beta\ \text{ in } U
$$
Rember that $f$ is bounded, so we can take $\beta >0$ large enough so that $f+\beta \geq 0$ everywhere in $U$ ($\beta$ larger than $|\min f|$ would work). On the boundary we have that
$$
u + \beta w = \beta w \geq 0 \text{ on } \partial U
$$
and particularly $u(x_0) + \beta w(x_0) = 0$. 
With this all together we have that $u + \beta w$ satisfies the hypothesis of the maximum principle, and therefore the minimum of the function $u + \beta w$ is achieved on the boundary
$$
\min\limits_{\bar{U}} u+\beta w = \min\limits_{\partial U} u+\beta w
$$
but $u + \beta w \geq 0$ in $\partial U$, and at $x_0$, $u(x_0) + \beta w(x_0) = 0$, therefore
$$
\min\limits_{\bar{U}} u+\beta w = 0
$$
and more importantly the function in the interior cannot hit the minimum point, so $u+\beta w > 0$ in $U$. Using now Hopf's lemma, we obtain 
$$
\frac{\partial}{\partial \nu}(u+\beta w)(x_0) < 0
\Leftrightarrow \frac{\partial u}{\partial \nu}(x_0) + \beta \frac{\partial w}{\partial \nu}(x_0) < 0
$$
$$
\Leftrightarrow  \frac{\partial u}{\partial \nu}(x_0) < - \beta \frac{\partial w}{\partial \nu}(x_0) = \beta |\frac{\partial w}{\partial \nu}(x_0)| 
$$
Where the last equality follows from the fact that $\frac{\partial w}{\partial \nu}(x_0) < 0$ (as a consequence of Hopf's lemma applied to $w$ itself).

>Note: It is useful for the imagination and intution to think about the smiley faces from before. Given the equations that $w$ satisfies, we can imagine that $w$ is concave (sad face because the 2nd derivative is negative), so at the boundary, the slopes are negative!

Ok, so we have one side of the desired inequality, and we are missing that 
$$
-\beta |\frac{\partial w}{\partial \nu}(x_0)| < \frac{\partial u}{\partial \nu}(x_0)
$$
but this is easy to accomplish, just a little tedious. Instead of starting with the sum $u+\beta w$, consider instead the substraction $u - \beta w$. An analogous approach as the above (but with maximums instead of minimums, and chosing $\beta$ to be larger than $|\max f|$) gives us the inquality
$$
-\beta |\frac{\partial w}{\partial \nu} (x_0)| < \frac{\partial u}{\partial \nu} (x_0)
$$
which is what we needed to conclude that 
$$ 
|\frac{\partial u}{\partial \nu} (x_0)| < \beta |\frac{\partial w}{\partial \nu} (x_0)|
$$

Now, is this the end? 
Not really right, since we have only found bounds for function $u$ along the normal direction on the boundary $\frac{\partial u}{\partial \nu} (x_0)$. To finish bounding the full gradient, we need to consider the tangential directions. We will leave this unproven since this article is long enough already, but to help the intution consider this question: what is the value of $u$ in the boundary $\partial U$? 
It's zero! so what is the "variation" of $u$ along the tangential direction to the boundary? It should be zero as well, so the contribution of this derivative into the full gradient is zero. 

---

### Summary

Ok, so we started with a solution $u$ to some elliptic equation $Lu = f$ of which we knew nothing about the sign of $f$ in $U$. This would prevent us from using the maximum principle directly on $u$ to obtain some behaviour information about it. But using the barrier function $w$, we managed to extract lots of information about it! 

That is the key. 

Questions to ponder: Is there only one possible barrier function?  
Whether the answer to the above question is yes or no, how do you find it/them? Who is going to give me the equation system for $w$? Is that system even guarranteed to have a solution? 
Not necessarily, right?

The thing to understand is that this is a trick, a magical magical trick. So we can build the barrier function $w$ to be whatever we want in order to achieve whatever goal we are pursuing. In that problem we were looking to bound the gradient of $u$ in the boundary. Some other problem might require something else, and then the choice of barrier function would be different. The only thing that one needs to consider is whether this barrier exists, and satisfies the right hypothesis, but the general approach is just trial and error! 
It's the exploratory magic of differential equations, so put on your hat and whip, and start exploring!

## Example from my research





 