This article is part of a series on [topological quantum computing](http://www.orbifold.net/default/tag/quantum-computing/).

This time we'll describe some crucial elements we need later on:

- how electric and magnetic fields are unified in one vector field
- how electrons 'feel' hole in spacetime
- how the Wilson loop is a natural thing when looking at loops (and later on, knots).

Electromagnetism as described by Maxwell's equations is actually a decoupling of a more fundamental field called the vector potential, denoted by $A$. It's a four-vector

$$A = (A^0, A^1, A^2, A^3) = (\phi,\, \bar{A})$$

with $\phi$ the scalar part and $\bar{A}$ the vector part.
The magnetic field is a derivative of the potential

$$B:= \nabla\times \bar{A}$$

and in the example below we show how you can go from Maxwell's equation to all of this. **The essential idea you need to understand is that the whole of electromagnetism sits in this potential and (quantum) field theory deals with $A$ and not the electic $E$ or magnetic $B$ fields.** From a classical perspective the vector potential can a curiosity, but on a quantum level it's the other way around.

This is even more striking when looking at the famous Aharonov-Bohm effect where one can have a vanishing magnetic field and still a noticeable influence on quantum behavior.

If you take a quantum particle travelling around a point-like magnetic field the path integral becomes

$$I = \int Dx(t)\,e^{i\frac{S_0}{\hbar}}\,e^{i\frac{q}{\hbar}\int A.dr}$$

where $S_0$ is the free-particle Lagrangian. This is usually called the minimal coupling and is part of the replacement $p\mapsto p-qA$. Since we look at the particle making a loop around the magnetic line the extra factor can be written as

$$\exp{i\frac{q}{\hbar}\oint A.dr} \\= \exp{i\frac{q}{\hbar}\oint (\nabla\times A).dr} \\= \exp{i\frac{q}{\hbar}\int B.dS} = \exp{i\frac{q\Phi}{\hbar}}$$

using Stoke's trick. The surface integral is basically the flux from the magnetic field and because it's concentrated in the center you can see that the factor is independent of the path taken. Hence,

$$I = I_0\,\exp{i\frac{q\Phi}{\hbar}}$$

with $I_0$ the free-particle integral. Since the integral give us the propagator for the particle's wave function 

$$\psi(\Delta t) \sim I_{\Delta t}\,\psi(0)$$

you can see that the vector potential induces a phase-shift

$$\psi  \sim \psi.\,\exp{i\frac{q\Phi}{\hbar}}$$.

Note the surprise here: you move something around in a place where there is no magentic field and still you can have a noticeable effect from something you circled around. The situation is a bit similar to the complex line integrals where poles lead to non-zero residues. Though in that case the function is singular and not the underlying space. 

The phase-shift is crucial to understanding anyons and topological computing in general and there are a few key-concept to take away from here. First, contrary to the situation you have in complex analysis the function we integrate is not singular rather the underlying space has a singularity. The magnetic line punches a hole in the topology leading to, what is called, **a non-zero winding number** (or **fundamental homology group $\pi_1$**). The fundamental group looks at loops in the punctured space and you have indeed the situation that a loop can (1) not encircle the hole, (2) loop around it, (3) loop twice around...and so on. This means that each and every path gets a number corresponding to how many times it circles around the hole. Furthermore, there is a difference between moving in clockwise or anti-clockwise fashion. All of this results in partitioning the space of loops in boxes you can label with an integer. So, one writes

$$\pi_1 = \mathbb{Z}.$$

One alsay say that the fundamental group reflects the knottiness (naughtyness?) of the space. Similarly, if you look at the taurus a bit you will discover that the tarus has $\pi_1 = \mathbb{Z}\times \mathbb{Z}$ because the space is basically $S_1\times S_1.$ So, the Aharonov-Bohm effect is a crucial example of how topology of space affects behavior at a quantum level. **This single fact sits at the heart of topological quantum computing.**

> From Maxwell to the vector potential

Let's take the Maxwell equations in vacuum:

$$\begin{align}
  \nabla \times  \mathbf{B} -\,  \frac{\partial\mathbf{E}}{\partial t} & = 0 \\
  \nabla \cdot \mathbf{E} & = 0 \\
  \nabla \times \mathbf{E}\, +\,  \frac{\partial\mathbf{B}}{\partial t} & = 0 \\
  \nabla \cdot \mathbf{B} & = 0
\end{align}$$

The fact that $ \nabla \cdot \mathbf{B}=0$ implies that there is a vectorial function with $\mathbf{B} = \nabla\times \mathbf{A}$ based on the [Helmholtz decomposition theorem](https://en.wikipedia.org/wiki/Helmholtz_decomposition) (and standard theory of manifolds and de Rham). With this in place you automatically satisfy the last equation. The equation

$$\nabla \times \mathbf{E}\, +\,  \frac{\partial\mathbf{B}}{\partial t} \\ = \nabla\times (\mathbf{E} + \frac{\partial A}{\partial t}) = 0$$

means that there is a scalar $\phi$ such that 

$$\mathbf{E} + \frac{\partial A}{\partial t} = \nabla\phi$$

which automatically satisfies the third equation. The first equation can be transformed using

$$\nabla\times B = \nabla\times\nabla\times A\\=\nabla(\nabla \cdot A) - \Delta A$$

giving

$$\nabla(\nabla \cdot A) - \Delta A + \frac{\partial^2 A}{\partial t^2} - \nabla(\frac{\partial\phi}{\partial t})  = 0$$
or 

$$\nabla(\nabla \cdot A - \frac{\partial\phi}{\partial t})  = \Box A.$$

Finally, the second equation gives

$$\Delta \phi -  \frac{\partial(\nabla\cdot A)}{\partial t} = 0.$$

Now, lean back a bit and look at the last two equations. You can see that if you set (that is, require)

$$\nabla \cdot A - \frac{\partial\phi}{\partial t} = 0$$

all of Maxwell's equation reduce to 

$$\Box A = 0,\, \Box\phi = 0.$$

Even more, if you define the four-vector as

$$(A^\mu) = (\phi,\, \bar{A})$$

everything simplifies to 

$$\Box\,A = 0,\, \partial_\mu A^\mu = 0.$$

So, as stated earlier, one can reduce all of electromagnetism to dealing with the vector potential instead of using the electric and magnetic fields.

The simplification has far reaching consequences and deep roots in differential geometry. The concept of **gauge invariance** can be seen in the equation above. Replacing 

$$A^\mu\mapsto A^\mu+\partial^\mu\chi$$

does indeed not alter the equations and it means that the vector potential can always be shifted with the derivative of an arbitrary function. This idea, when extended to a local invariance, leads to gauge field theory and ultimately to the standard model of elementary particles.

> Vector potential of a solenoid

How can one have a non-vanishing A-field with a zero magnetic field? Take a magnetic field centered in a cylindrical tube of Radius R along the z-axis. By defining


$$A^\theta = \left \{
  \begin{array}{ll}
  	\frac{1}{2}B_0\,r  & \mbox{if } r < R \\
		 \frac{1}{2r}B_0\,R^2 & \mbox{if } r \geq R
  \end{array}
  \right.$$
  
and $A^r = A^z = 0$ in cylindrical coordinates. The [curl in cylindrical coordinates](https://en.wikipedia.org/wiki/Del_in_cylindrical_and_spherical_coordinates) has only a non-zero value in z-direction and within the diameter $R$:

$$B^z = (\nabla\times A)^z = \frac{1}{r}\frac{\partial}{\partial r}(r\,A^\theta)=  \left \{
  \begin{array}{ll}
  	B_0  & \mbox{if } r < R \\
		0 & \mbox{if } r \geq R
  \end{array}
  \right.$$

So, you have indeed a non-zero vector potential outside the magnetic tube. Note that the vector potential is continuous at $R$ and the $1/r$ potential is similar to Newton's law or the electric potential outside a point-charge.

>Minimal coupling

Minimal coupling is a prescription to couple the dynamics of one field to another. Usually it refers to how a matter-field (say, electrons) is coupled to electromagnetism.

The minimal coupling of the vector field with a free particle is essentially the substitution

$$ \frac{dx^\mu}{dt} \mapsto \frac{dx^\mu}{dt} - iq\,A^\mu$$

leading to a factor

$$\int dt \,\frac{dx}{dt}.A = \int dx.A$$ and a purely vectorial $\int A^2$ not affecting the phase (a constant). The minimal coupling of the Klein-Gordon dynamics with the vector potential is

$$\partial\phi \mapsto \partial\phi- iq\,A\phi.$$

This simple rule has deep roots in differential geometry ([covariant derivatives](https://en.wikipedia.org/wiki/Covariant_derivative) and [vector bundles](https://en.wikipedia.org/wiki/Vector_bundle)). It might appear a bit ad-hoc but there is a large body of refined maths underneath it. It's also where you can venture into [non-commutative geometry](https://en.wikipedia.org/wiki/Noncommutative_geometry) and [exotic](https://en.wikipedia.org/wiki/Orbifold) variations of [Riemannian geometry](https://en.wikipedia.org/wiki/Riemannian_geometry).


> Wilson loops and curvature

From the discussion above it should be clear that the integral $$\int A.dx$$

is rather important. It plays in fact a crucial role in the bridge between knots and QFT as we'll see later. For now, let's look at the parallel transport of the fibers (of a vector bundle). If $A$ is the connection of a vector bundle the parallel transport of a vector $V$ is

$$(1 + A.dx)\,V$$

and if you continue transporting it you get 

$$(1 + A_1.dx)(1 + A_2.dx)\ldots$$

where the product has to be performed in such a way that the ordering of the $A's$ corresponds to the ordering of the points of the path taken. Often this is called the **path ordering** of the product and it corresponds to 


$$\mathcal{P}\exp \int A.dx$$

with $\mathcal{P}$ the path ordering. So, if one transports a vector around a loop you get
$$\mathcal{P}\exp \oint A.dx$$

which is known as a **Wilson loop**. Note the similarity with the Aharonov-Bohm factor.

One of the very cool things you can do with this is looking at infinitesimal loops and one can show that the result is directly related to the curvature of $A$. We will demonstrate this in our discussion related to polynomials from quantum loops. With some conceptual courage you can generalize the whole mechanics and this leads to the loop representation and generalize loop groups which are the basis of [loop quantum gravity](https://www.amazon.com/Theories-Quantum-Cambridge-Monographs-Mathematical/dp/0521654750).




