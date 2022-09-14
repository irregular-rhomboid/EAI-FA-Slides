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

# FA Reading Group Section 3.1 and 3.2
## Functional Derivatives
### 07/08/2022

---
# Section contents
- Definition of the "derivative" of a map $f:X \rightarrow Y$ between generic normed spaces
- First order conditions for optimization problems (in possibly infinite dimensions)

Applications: Euler-Lagrange equations/Quantum mechanics/Optimal control, ...

---
# Functional derivative

Let $f:X \rightarrow Y$ be a map between two normed spaces $X$ and $Y$. $f$ is said to be *differentiable* at $x_0 \in X$ if there exists  $L \in CL(X,Y)$, such that for all $\varepsilon > 0$, there exists $\delta > 0$ s.t. if $\|x-x_0\|_X < \delta$, then
$$ \frac{\|f(x)-f(x_0)-L(x-x_0)\|_Y}{\|x-x_0\|_X} < \varepsilon $$

Note: This is known as the *Fréchet derivative*. There are weaker notions of functional derivatives, such as the *Gateaux derivative*.

---
# Type signature
The derivative of a function at a point is a linear operator from $X$ to $Y$, i.e. the derivative has the "type signature"

$$ f' : X \rightarrow CL(X,Y) $$

which contrasts with the good old derivative of a scalar function
$$ f' : \mathbb{R} \rightarrow \mathbb{R} $$

---
# Type signature
| Primal | Derivative |
--- | ---
$f:\mathbb{R} \rightarrow \mathbb{R}$|$f': \mathbb{R} \rightarrow \mathbb{R}$
$f:\mathbb{R}^n \rightarrow \mathbb{R}$|$\nabla f: \mathbb{R}^n \rightarrow \mathbb{R}^n$
$f:\mathbb{R}^n \rightarrow \mathbb{R}^m$|$\mathcal{J}f: \mathbb{R}^n \rightarrow \mathbb{R}^{m\times n}$
$f:X \rightarrow Y$|$Df:X\rightarrow CL(X,Y)$
$f:X\rightarrow \mathbb{R}$|$Df:X\rightarrow X'$

Turns out we were just confused about the type signature of the classical derivative! 

---
# Key results
- For scalar functions the (Fréchet) derivative is the same as the classical one
- Uniqueness of the derivative
- $f$ differentiable $\Rightarrow$ $f$ continuous (Ex. 3.2)
- Chain rule still works! (Ex. 3.4)

---
# Optimality conditions
From Undergrad Real analysis, remember that, for $f:\mathbb{R}\rightarrow \mathbb{R}$ (differentiable)
1. $x_* \in \mathbb{R}$ is a minimizer of $f$ $\Rightarrow$ $f'(x_*) = 0$
2. $f'(x_*) = 0$ and $f''(x) \ge 0, \forall x$ $\Rightarrow$ $x_*$ is a minimum of $f$

---
# When you don't have $f''$
For a real valued function $f:X\rightarrow \mathbb{R}$
1. $x_*$ is a minimizer of $f$ $\Rightarrow$ $f'(x_*) = 0$
2. $f$ convex and $f'(x_*) = 0$ $\Rightarrow$ $x_*$ is a minimizer of $f$

---
# Extra: Gateaux derivative

$f: X \rightarrow Y$ is *Gateaux differentiable* at $x_0 \in X$ if there exists a map $g:X \rightarrow Y$ s.t. $\forall h \in X$
$$ \lim_{\tau \rightarrow 0}\frac{f(x_0 + \tau h) - f(x_0)}{\tau} = g(h) $$
Generalization of the directional derivative!
Gateaux derivative: $df: X \times X \rightarrow Y$ (not necessarily linear, or continuous)

---
# Example: Optimal Control
Minimize
$$ \mathcal{J}[x, u, t_0, t_f] = \mathcal{E}(x(t_0), t_0, x(t_f), t_f) + \int_{t_0}^{t_f} \mathcal{F}(x(t), u(t), t)dt $$
with constraints
- $\dot{x}(t) = f(x(t), u(t), t)$
- $h(x(t), u(t), t) \le 0$
- $e(x(t_0), t_0, x(t_f), t_f) = 0$

---
# Example: Shortest (differentiable) Path
Let $x, y \in \mathbb{R}^n$. Consider the curve length functional $\ell:C^1_0([0,1],\mathbb{R}^n) \rightarrow \mathbb{R}$
$$ \ell(\gamma) = \int_0^1 \| \lambda'(t) + \gamma'(t) \| dt $$
where $\lambda(t) = (1-t)x+ty$

Problem: find the minimizer(s) of $\ell$ (i.e. the shortest curve from $x$ to $y$)
