---
title: 2025 IMO P3 - Integer Functional Equations Using Primes
date: 2025-07-27 22:00:00 +0900
categories: [Olympiad, Number Theory]
tags: [Primes, Dirichlet’s Theorem, Primitive Roots]
author: sejinpark46
math: true
---

## Step 0. Introdution to the Problem

**2025 IMO Problem 3**

---

$f : N \to N$ is called "bonza" if

$$
f(a)|b^a-f(b)^{f(a)}   \text{   for all a,b}
$$

Determine the smallest number $c$ such that $f(n)\leqslant cn$ for all bonza functions $f$ and all positive integers $n$.

---

It is trivial that $f(n)=n$ is a bonza function, therefore $1\leqslant c$ is valid.

What if there exist n such that f(n) $\neq$ n?


## Step 1. For Sufficiently Large Prime Number p, f(p)=1

$$
P(a,b): f(a)|b^a-f(b)^{f(a)}
$$

$$
P(a,a): f(a)|a^a-f(a)^{f(a)}, \qquad f(a)|a^a
$$

If a is prime p, $f(p)|p^p$, $\quad f(p)>1 \Rightarrow p|f(p), f(p)=p^l$

Assume that prime p satisfying $f(p)>1$ is infinite.

$$
P(p,n): p|f(p)|f(n)^{f(p)}-n^p
$$

According to Fermat's little theorem, $n^p \equiv n \pmod{p}$

$$
0 \equiv f(n)^{f(p)}-n^p \equiv f(n)^{p^l}-n^p \equiv f(n)-n \pmod{p}, \qquad p|f(n)-n
$$

As $f(n)-n \neq 0$ and satisfying prime $p$ is infinite, there exists p such that $p>|f(n)-n|$, contradictory to $p|f(n)-n$.

---

Therefore, prime p s.t $f(p)>1$ is finite, $\exists$ N s.t. p>N $\Rightarrow f(p)=1$

$\blacksquare$


## Step 2: $f(p)=1$ for all prime p>2

Take prime q>2, as $q|f(q)$,

$$
P(q,p): q|f(q)|p^q-1 \text{for all p>N}
$$

---
**Primative Root**

For all prime $p$, there exists $g$ such that

$$
p|g^a-1 \Rightarrow p-1|a
$$



**Dirichlet's theorem**

For all coprime positive integer a,b, there are infinite prime p such that $p \equiv a \pmod{b}$

---


Let $g$ be a **Primitive root** modulo $q$. By **Dirichlet's theorem**, there are infinitely many primes of the form $qk+g$.

Thus, for sufficiently large primes $p$, we can choose $p$ to be of the form $qk+g$.

$$
0 \equiv p^q-1 \equiv g^q-1 \pmod{q}
$$

Due to the definition, $q-1|q$, $q-1|1$, contradiction.

$\blacksquare$


## Step 3. Finalle

**1. f(m) is power of 2**

For all positive integer m and prime $p>2$,

$$
P(m,p): f(m)|p^m-1
$$

If f(m) has prime factors p>2, $p|f(m)|p^m-1$, $p|1$, contradiction.

Therefore, for all m, f(m) is power of 2.

**2. If m is odd, f(m)=1**

$P(m,m): f(m)|m^m$, f(m) is odd, therefore f(m)=1

**3. If m is even, $f(m) \leq 2^{V_2(m)+2}$**

$P(m,3): f(m)|3^m-1$,

$$
V_2(f(m)) \leq V_2(3^m-1) = V_2(m)+2
$$

(Omit the proof of $V_2(3^m-1) = V_2(m)+2$)

Therefore, $f(m) \leq 2^{V_2(m)+2}$

**4. Minimum of c is 4**

$f(m) \leq 4m$ for all m, $m=2^k \Rightarrow f(2^k)=4x2^k$.

$\blacksquare$
