---
# You don't need to edit this file, it's empty on purpose.
# Edit theme's home layout instead if you wanna make some changes
# See: https://jekyllrb.com/docs/themes/#overriding-theme-defaults
layout: single
author_profile: true
---

Complex numbers are numbers with a *real component* and an *imaginary component*, in the form of $\a+bi$, where a and b are both **real numbers**, and i is the **imaginary unit**

An extended explanation of complex numbers can be found [here](https://en.wikipedia.org/wiki/Complex_number)

It can be helpful to visualize complex numbers on the complex plane:
![complex plane](https://upload.wikimedia.org/wikipedia/commons/5/5d/Imaginarynumber2.PNG)

Complex numbers can also be represeted in polar form as below:
[![polar form](https://upload.wikimedia.org/wikipedia/commons/thumb/7/71/Euler%27s_formula.svg/250px-Euler%27s_formula.svg.png)](https://en.wikipedia.org/wiki/Polar_coordinate_system)

To understand how the polar form is derived, check out this video:
<iframe width="560" height="315" src="https://www.youtube.com/embed/lFT2hwsCMls?si=IJZ6nsglLM12VV7-" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

title: Mini-Project Proposal

subtitle: Project Idea

My project idea is a breakdown and analysis of the derivation and justification for Grover’s algorithm (essentially literature review consisting primarily of the original paper in which this algorithm was proposed: ![A fast quantum mechanical algorithm for database search](https://arxiv.org/pdf/quant-ph/9605043)), as well as how the algorithm evolved and developed over time. This is one of the most important foundational algorithms of quantum computing, first discovered in 1996 by Lov Grover. 

subtitle: Background

Grover's algorithm is applied to problems that involve trying to find a specific entry in a database of N elements that, given an unknown function, will return a specified value when plugged into said function. It allows for a quadratic speedup O(sqrt(N)) with the number of entries- meaning that as N gets larger, the algorithm will take an amount of time proportional to sqrt(N), meaning that it gets quadratically faster for larger data sets, as opposed to most classical methods which give a linear speedup O(n)- because a classical computer can only guess and check each element one by one, which would lead to an average of N/2 tries before it finds the right answer, allowing for much more efficient large-scale search algorithms. This presents great applications in optimization, graph, and pattern recognition problems, as the generic algorithm is applied to a problem whose solution is easily verifiable, but hard to find, which describes all of what are called NP problems.

The way the algorithm works is by starting in a state that is an equal superposition of all N elements in the list (reached by applying a sequence of Hadamard gates), only one of which, when plugged into the given function, will give us the result we are looking for. We can call this initial state vector b, and the key value we are searching for k. Thus, the plane in the N-dimensional space containing the b and k vectors will look like this: 

![Grover's Algorithm Initial State Visualization](https://github.com/user-attachments/assets/fa75b305-8113-4ef3-b97a-75403aeb85a6)

Then, we can apply what is called an “oracle function” to the entire state, which is defined by leaving an amplitude unchanged if it does not give the value we are looking for when plugged into the function, and returns the additive inverse of the amplitude of a value that, when plugged into the given function, gives the value we want. This looks like flipping about the x-axis in the above diagram. Thus, when it is applied to the starting state, all it does is flip the amplitude of the value we want, and leave all others unchanged. Then, we can iteratively apply the “Grover operator” to this new state, consisting of both a reflection about the mean state (b), and an inversion about the marked state (flipping the sign of the key value’s amplitude), which, over time, amplifies the state we want and diminishes all other states, which would be represented above by the state vector “wobbling” back and forth as these two operations are applied repeatedly, until it nearly coincides with k. Applied O(sqrt(N)) times, it makes measuring the final state to be the state we want almost guaranteed, because applying the Grover operator is paramount to a rotation of 2 times the angle of the initial state, and dividing a right angle by this one yields sqrt(N) repititions.
