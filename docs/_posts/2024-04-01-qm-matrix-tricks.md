---
title: Matrix Tricks in QM
layout: post
tag: quantum mechanics
categories: ["general"]
---

In a previous article on this site ("A Gentle Introduction to Computational Quantum Mechanics") we derived a matrix form for the
Hamiltonian in the time-independent Schrödinger equation. Let's solve
that Hamiltonian analytically. No Numpy needed for the special case of a
particle in a box!

The standard textbook answer for the eigenenergies of a particle in a
box is 

$$\begin{align}
    E_n = \frac{n^2\pi ^2}{2L^2}.\end{align}$$ 
    
Let's try to see if we can figure this out from the matrix form 

$$\begin{align}
    D = -\frac{1}{2(\Delta x)^2} \begin{bmatrix}
        -2 & 1 & 0 &  \cdots \\
        1 & -2 & 1 &  \ddots  \\
        0 & 1 & -2 &  \ddots \\
        \vdots & \ddots & \ddots & \ddots 
    \end{bmatrix}.\end{align}$$

It turns out that this sort of matrix is called a \"tridiagonal Toeplitz
matrix\". We can simply take the eigenvalues from the literature; they
are 

$$\begin{align}
    E_n=a-2\sqrt{bc} \cos \bigg(\frac{n \pi }{N+1}\bigg)\end{align}$$

where $a$ are the diagonal entries, $b$ and $c$ are the offdiagonal
entries. In our case, $a=1/(\Delta x)^2$ and $b=c=-0.5/(\Delta x)^2$ and
$N\cdot N$ is the size of the matrix.

Presuming $N\gg 1$, we can approximate $N+1\approx N$ and take the
Taylor series of $\cos$, to wit 

$$\begin{align}
    \cos \bigg( \frac{n\pi }{N+1} \bigg) \approx \cos \bigg( \frac{n\pi }{N} \bigg) \approx 1 - \frac{n^2 \pi ^2 }{2N^2}.\end{align}$$

Now, since our matrix comes from discretizing the space in to N+1
intervals with N gridpoints, evidently $N = L/\Delta x$. Hence

$$\begin{align}
    1 - \frac{n^2 \pi ^2 }{2N^2} = 1 - \frac{n^2 \pi ^2 (\Delta x)^2 }{2L^2}.\label{eq:finalcos}\end{align}$$


Plugging in $\eqref{eq:finalcos}$ and the values for $a,b$ and $c$, we
get

$$\begin{align}
    E_n =\frac{1}{(\Delta x)^2} - \frac{1}{(\Delta x)^2}\bigg( 1-\frac{n^2 \pi ^2 (\Delta x)^2 }{2L^2}\bigg) = \frac{n^2\pi ^2 }{2L ^2}\end{align}$$


which is precisely what we would get by standard methods.

Well, you say, it's not a very impressive trick -- this is a very
special form of matrix. If we added a potential, then all the entries on
the diagonal wouldn't be the same and we wouldn't get such a pretty
result.

True! There is one more exception: if we add 1 to the top right and
bottom left corners -- indicating periodic boundary conditions -- the
matrix is still solvable (it is now a circulant matrix). It is also
possible to apply the perturbation theory of matrices[^1] to get more
analytical results, even for more unusual matrix types.

This technique is not very useful in practice, but it was a funny find
anyway. If you find more quantum systems solvable in this way, I would
be interested -- contact me.

[^1]: Kato's book \"Perturbation theory of linear operators\" is the
    definitive resource for this.
