There is an experiment that allows us to show without a doubt that Quantum phenomena is differentiable from any possible classical phenomena. This is the Bell experiment or CHSH game. 

## The CHSH game
Given two people, Alice and Bob, they each get an input bit: $x\in\{0,1\}$ for Alice and $y\in\{0,1\}$ for Bob. 
Then they each decide what output to select given their respective inputs $x, y$. We call these outputs $a, b \in \{0, 1\}$.

The game is won if either of the following situations happen: 
1. $x = y = 1$ and $a \neq b$, or
2. $x \neq y$ or $x = y = 0$, and $a = b$.  

### Classical winning strategy 
Alice and Bob can agree in advance that no matter what inputs $x, y$ they get, they will choose outputs $a=b=0$. With this agreement, their chance of winning is 3/4. 
Indeed, the possible cases that can happen are:
- $x=0, y=0$ then $a=0, b=0$, which is winning option 2 above. 
- $x=0, y=1$ then $a=0, b=0$, which again is winning option 2.
- $x=1, y=0$ then $a=0, b=0$, which again is winning option 2
- $x=1, y=1$ then $a=0, b=0$ which fails winning condition 1. 
Since those are all possible cases, 3 times out of 4 Alice and Bob win the game. One could then expect that if we sample x, y randomly over a long period of time, we shld see an occurrence of winning with probability 3/4. 

#### This strategy is the best classical strategy
Is there any other tactics that Alice and Bob can use to improve their chances of success? Any information that they can exchange before the game starts in order to win more often? 

The answer is no, and it's easy to see if one fills out the following table with the best logical strategy case by case. 
Suppose first that the inputs are x = 0, y = 0: Then, in order to win, Alice and Bob can chose both either a=b=1, or a=b=0. Lets chose the later (but it's actually a symmetric choice). Then:
| x | y | a | b |
| - | - | - | - |
| 0 | 0 | 0 | 0 |
Now, suppose x = 0, and y = 1. Since Alice got the same input as before (x=0), her response is the same, a = 0. Again if they ought to win as much as possible, Bob's best choice is to again set b = 0.   
| x | y | a | b |
| - | - | - | - |
| 0 | 0 | 0 | 0 |
| 0 | 1 | 0 | 0 |
Similarly if x = 1 and y = 0, Bob is now forced by his previous decision for y = 0 to return b = 0, which leaves Alice to win if she choses a = 0 and fit into case 2, so
| x | y | a | b |
| - | - | - | - |
| 0 | 0 | 0 | 0 |
| 0 | 1 | 0 | 0 |
| 1 | 0 | 0 | 0 |
But now what happens for the last combination x = 1 and y = 1? In this case, both Alice and Bob have already determined in their previous cases what they will choose for an input = 1: 
| x | y | a | b |
| - | - | - | - |
| 0 | 0 | 0 | 0 |
| 0 | 1 | 0 | 0 |
| 1 | 0 | 0 | 0 |
| 1 | 1 | 0 | 0 |
So again we get that probability of wining to be 3/4. 

## The quantum version of the game
How to leverage two entangled qbits to obtain a much superior probability of winning. 

### Quantum strategy
See here [here](https://learning.edx.org/course/course-v1:BerkeleyX+CS-191x+2T2020/block-v1:BerkeleyX+CS-191x+2T2020+type@sequential+block@16d3a31cd38e4634aaf1fb71054cd11f/block-v1:BerkeleyX+CS-191x+2T2020+type@vertical+block@8b437a49b5fb40bd8c50b12353d45e69)
Let us now describe the quantum measurements that achieve greater correlation. They are remarkably simple to describe:

-   if rA\=0, then Alice measures in the standard |0⟩/|1⟩ basis.
    
-   if rA\=1, then Alice measures in the π/4 basis (i.e. standard basis rotated by π/4).
    
-   if rB\=0, then Bob measures in the π/8 basis.
    
-   if rB\=1, then Bob measures in the −π/8 basis.
    

The analysis of the success probability of this experiment is also beautifully simple. We will show that in each of the four cases rA\=rB\=0, etc, the success probability P\[rA×rB\=a+b( mod 2)\]\=cos2π/8.

## If only Einstein would have known! 
## Random number generation with Bells experiment
https://arxiv.org/pdf/0911.3427v3.pdf 
https://arxiv.org/pdf/1111.6054v1.pdf Certifiable quantum dice