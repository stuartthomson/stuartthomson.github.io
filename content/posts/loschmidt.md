---
title: "Loschmidt's Paradox"
date: 2020-01-01T00:00:01Z
draft: false
tags: ["Maths", "Philosophy"]
---

$$
   \def\G{{\vec{\Gamma}}}
   \def\bm#1{{\vec{#1}}}
$$

<span class='drop-cap'>W</span>hy do waves never build a sandcastle? We often see the waves dissolve a carefully constructed sandcastle, but we never see the sea gather disparate grains of sand from the seabed and deposit them in the same shape on the beach. Both of these processes are in some sense allowed by the microscopic laws of physics, and yet we only ever observe one of them in real life. This is the essence of the problem of irreversibility - there is nothing in the equations of motion that disallow it because the underlying physics is symmetric under a change in the direction of time.  How do we get a universe with a definitive arrow of time from fundamental physics without one? This is the question I will try to answer in this essay.{{<marg-l>}}I don't want to talk about anything other than statistical physics here so I won't be discussing why the early universe had such low entropy, quantum mechanical time asymmetry, or any other related arrow-of-time questions. Or Boltzmann brains.{{</marg-l>}}

## Newtonian Time
To illustrate the problem a little we can look at Newton's equations of motion and see what they have to say about this. Let's just consider a single object under the influence of some force. Newtonian mechanics tells us how to calculate it's velocity at some point in the future using the equation:
{{<marg-r>}}$\bm{F}$: the force on the object<br>$m$: the mass of the object<br>$\bm{a}$: the acceleration of the object<br>An arrow above a quantity means that it's a vector.{{</marg-r>}}
$$
\begin{equation}
\bm{F} = m\bm{a},
\end{equation}
$$

The process of working out the object's position is then a process of doing something like the following:

1. For the object's current position, find out the value of the force at this location.
2. Calculate the object's acceleration by solving the equation above like $\bm{a} = \bm{F}/m$
3. Update the object's velocity by using this calculated acceleration (the larger the acceleration, the more the velocity will change). Update the object's position with the object's velocity.
4. Go to step 1.

This process will result in a trajectory of the object through space; at each point in time there is an associated vector telling the object how far it moves until the next point in time. We can then imagine 'reversing' the direction of time. This would mean starting the object at the end of its trajectory and setting its velocity to be the opposite to the velocity it had at that point in time when iterating forwards. If we then repeat the iteration of positions we will find it retracing its steps, and it will end up back where it started. This is what we mean when we say a system is 'time-reversible'.

## Boltzmannian Time
In 1872 Ludwig Boltzmann published one of the first papers to deal with non-equilibrium statistical physics in which he showed that a system out of equilibrium will tend towards equilibrium. He showed - starting with time reversible Newtonian physics - that a quantity related to the entropy of the system will always decrease. This elicited Loschmidt's famous reversibility argument in which he argued that if we take the endpoint of a time evolution of this system and reverse the velocities of all the particles we should expect to end up back at the start and should therefore expect to see this quantity _increase_ rather than decrease as Boltzmann claimed was inevitable. In order to understand the origin of this puzzle we will quickly review Boltzmann's derivation.
### Derivation
We shall consider a system of particles, each characterised by its position $\bm{q}$ and momentum $\bm{p}$ (we shall call a point in the phase space $\G = (\bm{p}, \bm{q})$. Consider the number density of particles for this system $f(\bm{q}, \bm{p}, t)$. We will try to find the time derivative of this quantity by looking at the difference in the rate of particles moving in and out of a small box due to collisions; we know from Liouville's theorem that in a system without collisions $f(\bm{q}, \bm{p}, t)$ is a constant.


$$
\begin{equation}
\frac{d}{dt}f(\G, t) = R_{in} - R_{out}
\end{equation}
$$

Where $R_{in}$ and $R_{out}$ are the rates of particles entering and leaving the box. In order to calculate these rates we will need to consider a new quantity, $f_2(\bm{q}, \bm{p}, \bm{p*}, t)$ which is the distribution function for finding particles with momenta $\bm{p}$, $\bm{p*}$ at position $\bm{q}$, i.e two particles colliding at position $\bm{q}$. Here a difficulty arises because in order to solve for the behaviour of $f$ we have had to introduce $f_2$, and in order to solve for $f_2$ we will want to involve higher order correlation and we end up in with an infinite hierarchy or higher and higher order correlations. To solve this problem we introduce the concept of _molecular chaos_ which is the assumption that the two particles involved in collision described by $f_2$ are uncorrelated and so the two-point function can be decomposed into two one-point functions:

$$
\begin{equation}
\label{stoss}
f_2(\bm{q}, \bm{p}, \bm{p*}, t) = f(\G, t)f(\G^*, t)
\end{equation}
$$

By doing this we are losing information about the past state of the system, and in essence assuming the system had higher disorder in the past than might actually be true. We now introduce the statistical quantity that gives the theorem its name:

$$
\begin{equation}
H(t) = \int f(\bm{p}, t)\ln f(\bm{p}, t)d\bm{p}
\end{equation}
$$

From this point on the derivation is mostly simple algebra, and noticing the time reversal symmetry of the collisions and the symmetry under particle swap. Eventually the following expression can be found:

$$
\begin{multline}
\frac{dH}{dt} = \frac{1}{4}\int d\bm{p}d\bm{p}^* d\bm{p}' d\bm{p}^{*\prime}\left( f(\bm{p}',t)f(\bm{p}^{*\prime}) - f(\bm{p},t)f(\bm{p}^*, t)\right) \\\\\\ \times \left(     \ln f(\bm{p},t)f(\bm{p}^{*}) - \ln f(\bm{p}',t)f(\bm{p}^{*\prime}) \right)
\end{multline}
$$

From which it can be seen that $H$ is decreasing for all time $t$. This equation even suggest that if you do as Loschmidt suggested and reverse all velocities of the final state $H$ would still be a decreasing function.

### The Stosszahlansatz

The origin of the paradox is the step shown in equation \ref{stoss}. There is a subtle introduction of a time asymmetry here - the assumption is that the particles going in to the collision are uncorrelated, but this need not be true of the particles _leaving_ the collision. In other words, the particles are not influenced by the fact that they are _going to_ collide, but they are influenced by the fact that they have _just collided_. With that in mind it is not difficult to see how reversing the velocities does not yield an increase in $H$ because we would then be looking at a system with a different idea of where the particles will be correlated and unocorrelated. This explains the origin of the time asymmetry _in this derivation_ but to what degree it is a genuine solution to Loschmidt's paradox is not clear; it certainly seems as if by making the molecular chaos assumption we are merely imposing irreversibility on the system, and not quite explaining it.

The Stosszahlansatz has historically caused quite a degree of confusion and debate, perhaps due to the subtle but important way it encodes the time asymmetry of Boltzmann's derivation. It seems as if discussing the the stosszahlansatz never satisfactorily eliminates Loschmidt's objection, because by asserting it you implicitly deny any fundamental microscopic reversibility and it is difficult to tell exactly to what degree Boltzmann's derivations respect a Newtonian outlook for the microscopic dynamics. I suspect that the fundamental disagreement between Boltzmann and Loschmidt is due to the former thinking of the question as a fundamentally statistical problem, whereas the latter was really thinking about it as a dynamical system.

With that in mind, we will now turn our attention to a method of obtaining irreversibility that begins with a fundamentally deterministic and reversible dynamical system.

## Evans-Searles Fluctuation Theorem
Fluctuation theorems can be used as a way to derive and quantify macroscopic irreversibility from fundamentally reversible microscopic behaviour by explicitly using Loschmidt's idea of reversing velocities in a deterministic system, rather from trying to sweep the reverse trajectories under the rug. In my view they give a clearer idea of what Loschmidt's objection actually entails and therefore clarify the origin of the irreversibility. I will consider deterministic fluctuation theorems as to derive stochastic ones would confuse the message contained about the origin of irreversibility which is that we do not need stochastic dynamics to create irreversibility. We will look first at the Evans-Searles Fluctuation theorem.{{<marg-r>}}Most of ideas and derivation here are explained more fully in a <a href="https://arxiv.org/abs/0709.3888">2008 paper by Sevick et al.</a>{{</marg-r>}}


### Derivation
Consider a deterministic set of points in phase space denoted $\G_t = (\bm{p}, \bm{q}, t)$ corresponding to the position and momenta of all of the particles in the system. The system is driven away from equilibrium either by a time-varying control parameter $\lambda (t)$ to the potential energy function $\phi(\lambda)$ or buy work done on the system by a purely dissipative field $\bm{F}$. The purely dissipative field prevents the system from every reaching equilibrium when it is present (an example could be the presence of walls of the container shearing the flow, preventing a fluid from settling). Each trajectory $\G_0\rightarrow\G_{\tau}$ has a corresponding anti-trajectory $\G_0^*\rightarrow\G^*_{\tau}$  where $\G_0 = \G^*_{\tau}$ and $\G_t = \G^*_0$. We will now use $f(\G, t)$ as a probability density (as opposed to a number density in the previous section). We will define macroscopic <em>irreversibility</em> by reference to the following definition of macroscopic <em>reversibility</em>:

- For every possible trajectory in the phase space at a time $t$ the corresponding initial point of the anti-trajectory is also present in the phase space.
- The probability of observing an infinitesimal bundle of trajectories is equal to the probability of observing the corresponding bundle of anti-trajectories, i.e. $f(\G_0, 0)\delta V(\G_0) = f(\G^*_{\tau}, 0)\delta V(\G^*_{\tau})$ where $\delta V(\G_t)$ is an infinitesimal phase-space volume around the point $\G_t$.%$dP(d\G_0, 0) = dP(d\G_{\tau}^*, 0)$

which allows us to rewrite the expression in the second point to obtain the following mathematical condition for reversibility:

$$
\begin{equation}
\frac{f(\G_0, 0)}{f(\G^*_{\tau}, 0)}\frac{\delta V(\G_0)}{\delta V(\G^*_{\tau})} = 1
\end{equation}
$$

The behaviour of the infinitesimal volume elements is therefore critical to our notion of reversibility. We can obtain the change in this volume over a trajectory by calculating the determinant of the Jacobian matrix. Using Liouville's formula we obtain the following result:

$$
\begin{equation}
\frac{\delta V(\G_{\tau})}{\delta V(\G_{0})} = \exp\left( \int_{0}^{\tau}\Lambda(\G_t, t)dt\right)
\end{equation}
$$

Where $\Lambda$ is $\left(\frac{\partial}{\partial\bm{q}} . \dot{\bm{q}} + \frac{\partial}{\partial\bm{p}} . \dot{\bm{p}}\right)$ evaluated at time $t$ and is referred to as the phase space compression factor.
In order for the system to exhibit microscopic time reversibility, we require that any external forces in the equations of motion have time symmetry. This implies that if we start with equal sized infinitesimal volumes $\delta V(\G_0)$ and $\delta V(\G^*_0)$ that there will be an equal change in the volume along the trajectories and so $\delta V(\G^*_{\tau}) = \delta V(\G_{\tau})$. Combining these results we introduce the following quantity as a measure of irreversibility:

$$
\begin{align}
\Omega_{\tau}(\G_0)&= \ln \left(\frac{f(\G_0, 0)}{f(\G_{\tau}, 0)}\right) - \int_{0}^{\tau}\Lambda(\G_t, t)dt \\\\\\
\label{dP} &= \ln\left(\frac{dP(d\G_0, 0)}{dP(d\G^*_{\tau}, 0)}\right)
\end{align}
$$

The second equation being merely a description of how we started the derivation, not a result which follows from the first. Any trajectory for which $\Omega_{\tau}(\G_0) \neq 0$ does not satisfy the second condition for reversibility and so this quantity can be used as a measure of irreversibility and $\langle \Omega_{\tau}\rangle \neq 0$ is a condition for macroscopic irreversibility. We can use this definition to find the probability density of trajectories having a certain degree of irreversibility:

$$
\begin{equation}
dP(\Omega_{\tau} = \mathcal{A}) = \int f(\G_0, 0)\delta[\Omega_{\tau}(\G_0) - \mathcal{A}]d\G_0
\end{equation}
$$

Where $\delta$ here is the Dirac delta. We can write a very similar expression which selects the corresponding anti-trajectories (noting that microscopic time reversibility requires that anti-trajectories have the same magnitude of irreversibility as their corresponding trajectories, only with the opposite sign):

$$
\begin{equation}
dP(\Omega_{\tau} = -\mathcal{A}) = \int f(\G^*_{\tau}, 0)\delta[\Omega_{\tau}(\G^*_{\tau}) - \mathcal{A}]d\G^*_{\tau}
\end{equation}
$$

Combining these results with equation \ref{dP} we obtain the Evans-Searles fluctuation theorem:

$$
\begin{equation}
\frac{dP(\Omega_{\tau} = \mathcal{A})}{dP(\Omega_{\tau} = \mathcal{-A})} = \exp(\mathcal{A})
\end{equation}
$$

Averaging over all trajectories (via averaging over $\mathcal{A}$) we obtain an expression of macroscopic irreversibility:

$$
\begin{equation}
\langle\Omega_\tau\rangle \geq 0
\end{equation}
$$

### Discussion
The irreversibility of the time evolution is a consequence of time-symmetry necessary for microscopic reversibility. If an infinitesimal volume in phase space shrinks as a result of the external forcing, then the external forcing will also cause the anti-trajectory to shrink. If we take Loschmidt's idea seriously and reverse the velocities, we still find that the infinitesimal volume is shrinking.

The Evans-Searles FT is just one of a whole class of related fluctuation theorems, which all have roughly analogous shape. Very vaguely this is:

$$
\begin{equation}
\frac{P(A \rightarrow B)}{P(A \leftarrow B)} = \exp (\mathcal{F})
\end{equation}
$$

For some $\mathcal{F}$ which quantifies the trajectory $A \rightarrow B$ and has the same magnitude but opposite sign for the anti-trajectory. As the system size increase (number of particles increases) or observation times increase it become almost impossibly unlikely to observe anti-trajectories and so second-law violations become all but statistically impossible.

All of these results would be opposite if one assumption was changed. The assumption has been made that the system _begins_ in some initial state and then evolves to a later state. If this was reversed, and the assumption is that the system evolves _into_ some known state then we would instead see that the average dissipative term is negative. This highlights that the really fundamental reason for the time asymmetry is the nature of causality itself.

There seems to be two, related reasons to reject Loschmidt's objection. Firstly, his anti-trajectories could be in some sense solutions to the equations of motion of a system, but in a chaotic system (thermodynamics) they would be so unstable as to hardly count as solutions at all and the probability of observing one for a macroscopic system is vanishingly small. In the space of all trajectories, an anti-trajectory has measure 0. Secondly, in our discussion of the Evans-Searle FT it became apparent that causality is the reason why time flows one way and not the other. It turns out that causality is a proper way to understand Boltzmann's assertion of molecular chaos. By saying that the particles are uncorrelated going into the collision but correlated coming out he is implicitly stating the order of causation that we expect to be followed. The reason the arrow of time flows the way it does is because it is fundamentally an expression of logical causation.

