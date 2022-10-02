---
marp: true
theme: uncover
style: |
    h1 {
        font-size: 50px;
        text-align: left;
    }
    h2 {
        font-size: 45px;
        text-align: left;
    }
    h3 {
        font-size: 40px;
        text-align: left;
    }
    section {
        font-size: 35px;
        text-align: left;
    }
    ul, ol {
        margin-left: 0;
        margin-right: auto;
    }
class: invert
paginate: true
#backgroundColor: #fff
---

# Functional Analysis Reading Group
## Orthogonality (section 4.2)
02/10/2022

---
# Today's menu
Now that we're living in inner-product spaces, we can define what it means for two vectors to be *orthogonal*, which entails

* Orthogonal/Orthonormal bases
* *Orthogonalizing* a basis

Orthonormal bases are very useful, both mathematically and numerically, so having them on function spaces is good©.

NB. Most of the results in this section hold for *inner product spaces*.

---
# Orthogonal vectors / Orthonormal set
Let $(X, \langle \cdot,\cdot \rangle)$$ be an inner product space

1. Vectors $x,y \in X$ are *orthogonal* if $\langle x, y\rangle = 0$
2. A set $S \subset X$ is *orthonormal* if
    - $\forall x, y \in S$, s.t. $x\neq y$, $\langle x,y\rangle = 0$
    - $\forall x \in S$, $\|x\|^2 = \langle x,x \rangle = 1$

---
# Examples of orthnormal sets (1)

- $\mathbb{R}^d$: $\left\{ e_1 = \begin{bmatrix} 1\\ 0 \\ \vdots \\ 0 \end{bmatrix}, \dots, e_d = \begin{bmatrix} 0\\ 0 \\ \vdots \\ 1 \end{bmatrix} \right\}$ (one-hot vectors)
- $\ell^2$: $\{e_i \ | \ i\in\mathbb{N} \}$ where $e_i$ is the $i$-th "one-hot sequence"

---
# Examples of orthonormal sets (2)

In $C[0,1]$, the Fourier basis $\{F_n | n\in \mathbb{Z}\}$, defined as
$$ F_n(t) = e^{2\pi int} $$
is an orthonormal set.

Indeed, it is an *orthonormal basis* of $C[0,1]$, and taking the Fourier series decomposition of a function $f$ is equivalent to expressing $f$ in that basis!

---
# Orthonormal sets and basis expansions
Given an orthonormal set $\{u_k | k \in K \}$, and a vector $x$ in its span, we can write
$$ x = \sum_{k\in K} \alpha_k u_k $$
where
$$ \alpha_k = \langle x, u_k \rangle $$

Moreover, any orthonormal set is always linearly independent.

---
# Gram-Schmidt orthonormalisation
Given a linearly independent subset $\{x_1, x_2 \dots\}$, we can construct an orthonormal set $\{u_1, u_2, \dots\}$ by the following procedure:

1. $u_1 = \frac{x_1}{\|x_1\|}$
2. $u_n = \frac{x_n - \sum_{k=1}^{n-1}\langle x_n,u_k\rangle u_k}{\| x_n - \sum_{k=1}^{n-1}\langle x_n,u_k\rangle u_k\|}$ for $n\ge 2$

The constructed set $\{u_1, u_2, \dots\}$ has the same span as the original set, i.e. for all $n \in \mathbb{N}$

$$ \text{span} \{u_1, \dots, u_n\} = \text{span} \{x_1, \dots, x_n\} $$

---
# Orthonormal sets of polynomials

The set of monomials $\{1, t, t^2, t^3, \dots \}$ is a linearly independent set in $C[-1,1]$, but it is not orthonormal!

Applying Gram-Schmidt orthogonalization to it yields the *Legendre polynomials*, which satisfy
$$ P_n(t) = \frac{1}{n! 2^n} \left( \frac{d}{dt}\right)^n (t^2-1)^n $$
and are orthogonal, with norm $\| P_n\|^2 = \frac{2}{2n+1}$

---
# Other orthonormal bases of polynomials
- Hermite polynomials (Ex 4.13) (orthogonal set of polynomials over $L^2(\mathbb{R})$)
$$H_n(x) = (-1)^n e^{x^2} \left( \frac{d}{dx}\right)^n e^{-x^2}$$

- Chebyshev polynomials ($x\in [-1,1]$)
$$ T_n(x) = \cos(n \arccos(x)) $$

Note: These families of functions (Fourier, Legendre, Hermite, ...) tend to show up as fundamental solutions of classical ODEs from physics

---
# Orthogonal complement

Given a subspace $Y$ of an inner product space $X$, the *orthogonal complement* $Y^\bot$ of $Y$ is defined as
$$ Y^{\bot} = \left\{ x\in X \ | \ \langle x,y\rangle = 0, \forall y \in Y \right\} $$

This generalizes the notion of "hyperplane"

---
# Properties of the orthogonal complement

- $Y^\bot$ is a *closed subspace* of $X$
- $Y \cap Y^\bot = \{0\}$ (Ex. 4.16)
- $Y \subset Y^{\bot\bot} = (Y^\bot)^\bot$ (4.17)
- $Y \subset Z \ \Rightarrow \ Z^\bot \subset Y^\bot$
- $Y^\bot = (\bar{Y})^\bot$
- $Y$ dense in $X$ $\Rightarrow \ Y^\bot = \{0\}$

---
# Concluding remarks

Stepping into inner product spaces is already yielding us benefits:
- Basis decomposition into an orthogonal basis is *tractable* (mathematically **and** numerically)
- We get "hyperplanes" of vectors in the *same space* as our vectors
- Connection to famous ODEs from physics

---
# PSA

- From now on, the meetings will be scheduled by default on Sundays at the "usual time" (20:00 GMT)
- Next meeting on the 23/10/2022 (unless someone is willing to do the recap in my stead)
- Feedback wanted! How are you finding these meetings?