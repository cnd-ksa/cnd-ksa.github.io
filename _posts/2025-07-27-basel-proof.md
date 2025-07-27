---
title: Proof of the Basel Problem
date: 2025-07-27 16:00:00 +0900
categories: [Analysis, Series]
tags: [Basel Problem, Power Series, Wallis Integral, Trigonometric Substitution, Integration, Inverse Sine, Infinite Series]
author: ksa23027
math: true
---

## 1. Power Series for $\sin^{-1}(x)$

**Step 1: Differentiate**

$$
\frac{d}{dx}(\sin^{-1}(x)) = \frac{1}{\sqrt{1 - x^2}}.
$$

**Step 2: Expand using the binomial theorem**

$$
\frac{1}{\sqrt{1 - x^2}} = \sum_{n=0}^{\infty} \frac{(2n)!}{4^n (n!)^2} x^{2n}.
$$

**Step 3: Integrate term-by-term**

$$
\sin^{-1}(x) = \sum_{n=0}^{\infty} \frac{(2n)!}{4^n (n!)^2 (2n+1)} x^{2n+1}.
$$

---

## 2. Expressing the Integral as a Series

Let

$$
I = \int_0^1 \frac{\sin^{-1}(x)}{\sqrt{1 - x^2}} \, dx.
$$

Substitute the series for $\sin^{-1}(x)$:

$$
I = \int_0^1 \frac{1}{\sqrt{1 - x^2}} \left( \sum_{n=0}^{\infty} \frac{(2n)!}{4^n (n!)^2 (2n+1)} x^{2n+1} \right) dx.
$$

Interchanging the sum and the integral:

$$
I = \sum_{n=0}^{\infty} \frac{(2n)!}{4^n (n!)^2 (2n+1)} \int_0^1 \frac{x^{2n+1}}{\sqrt{1 - x^2}} \, dx.
$$

### Trigonometric substitution:

Let $x = \sin \theta$, then $dx = \cos \theta \, d\theta$, and the integral becomes:

$$
\int_0^1 \frac{x^{2n+1}}{\sqrt{1 - x^2}} dx = \int_0^{\pi/2} \sin^{2n+1} \theta \, d\theta.
$$

Using Wallis’ integral formula:

$$
\int_0^{\pi/2} \sin^{2n+1} \theta \, d\theta = \frac{(2n)!!}{(2n+1)!!} = \frac{4^n (n!)^2}{(2n+1)!}.
$$

Substitute back:

$$
I = \sum_{n=0}^{\infty} \frac{(2n)!}{(2n+1)(2n+1)!} = \sum_{n=0}^{\infty} \frac{1}{(2n+1)^2}.
$$

---

## 3. Proof of the Basel Problem

We want to prove:

$$
\sum_{n=1}^{\infty} \frac{1}{n^2} = \frac{\pi^2}{6}.
$$

From the previous result:

$$
\sum_{n=0}^{\infty} \frac{1}{(2n+1)^2} = I = \frac{\pi^2}{8}.
$$

Split full sum:

$$
\sum_{n=1}^{\infty} \frac{1}{n^2} = \left( \sum_{k=0}^{\infty} \frac{1}{(2k+1)^2} \right) + \left( \sum_{k=1}^{\infty} \frac{1}{(2k)^2} \right).
$$

Note:

$$
\sum_{k=1}^{\infty} \frac{1}{(2k)^2} = \sum_{k=1}^{\infty} \frac{1}{4k^2} = \frac{1}{4} \sum_{k=1}^{\infty} \frac{1}{k^2}.
$$

Let $S = \sum_{n=1}^{\infty} \frac{1}{n^2}$, then:

$$
S = \frac{\pi^2}{8} + \frac{1}{4} S \Rightarrow \frac{3}{4} S = \frac{\pi^2}{8} \Rightarrow S = \frac{4}{3} \cdot \frac{\pi^2}{8} = \frac{\pi^2}{6}.
$$

$\blacksquare$
