# Feynman's proof of the Maxwell equations

A few weeks ago, [Freeman Dyson](https://en.wikipedia.org/wiki/Freeman_Dyson), a renowned professor from the Institute for Advanced Study in Princeton, passed away. He was a very curious physicist, with many interests and wild thought experiments (see Dyson sphere). He was also a student of Feynman, and in October 1948, Feynman showed him a proof of Maxwell equations, assuming only Newton's law of motion and the commutation relation between position and velocity for a single nonrelativistic particle.

I know, weird huh?

This curious paper was published in ([Am. J. Phys. 58 (3), March 1990](https://aapt.scitation.org/doi/10.1119/1.16188)), and then brought to my attention by this awesome paper subscription service, [Fermat's Library](https://fermatslibrary.com/), that was celebrating Dyson's life.

For a math-physics enthusiast, this is a hardcore click-bait title. So I dived in. If you are curious, please see the paper [here](https://fermatslibrary.com/s/feynmans-proof-of-the-maxwell-equations).   

The algebra is simple enough, and one might think to understand it right away. Classic Feynman argumentation. The reality is that, after a little bit of probing ones own understanding, one realizes that nothing is really clear!

Take for example the first argument line:
Assume a particle exists with position $x_j (j=1,2,3)$ and velocity $\dot{x}_j$ satisfying Newton's equation

$$m\ddot{x}_j = F_j(x,\dot{x},t)$$

with commutation relations

$$[x_j, x_k] = 0,$$
$$[x_j, \dot{x}_k] = i\hbar \delta_{jk}.$$

Sure you might say, seems reasonable... Really though?
What is the commutator of $x_j$ and $x_k$? What is $x_jx_k - x_kx_j$? Is that multiplication?

What is $x_j$ itself? Is it really just a scalar function of time that gives you the position of the particle? What about $\dot{x}_k$?

I hope you see where I'm going here. If they are truly scalars, then both of the above commutation relations would be zero, because multiplication is commutative. But no, something is not being stated...

Let's try to figure it out.

(coming soon)
