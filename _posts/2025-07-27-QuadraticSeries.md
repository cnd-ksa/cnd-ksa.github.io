---
title: Infinite Series Of The Reciprocals of Quadratic function
date: 2025-07-27 12:00:00 +0900
categories: [Series]
tags: [Gamma function, Infinite Series, Fourier Analysis]
author: ksa25114
math: true
---


## Introduction

급수 $\sum_{n=1}^{\infty}\frac{1}{n}$는 발산함이 쉽게 증명됩니다.

이를 이용해 급수 $\sum_{n=1}^{\infty}\frac{1}{an+b}, a\neq 0,\forall n\in \mathbb{N}, an+b\neq 0$도 발산함이 증명됩니다.

그렇다면 급수 $\sum_{n=1}^{\infty}\frac{1}{an^2+bn+c}, a\neq 0,\forall n\in \mathbb{N}, an^2+bn+c\neq 0$는 수렴할까요 발산할까요?

또 수렴한다면 수렴값은 어떻게 구할 수 있을까요?

---

## Convergence & Divergence

LCT(limit comparison test)는 다름과 같습니다:

자연수 $n=1,2,3,\cdots $에 대하여 $a_n>0, b_n>0$이고 두 수열

$$
\displaystyle \lim_{ n\to \infty}\frac{a_n}{b_n}
$$

이 양수로서 존재하면, 두 급수 $\sum_{n=1}^{\infty}a_n$, $\sum_{n=1}^{\infty}b_n$는 둘 다 수렴하거나 발산한다.

$a_n=\left\vert \frac{1}{an^2+bn+c} \right\vert$, $b_n=\frac{1}{n^2}$으로 둡니다. 그러면

$$
L=\displaystyle \lim_{n \to \infty}\frac{\left\vert a_n \right\vert}{\left\vert b_n \right\vert}=\displaystyle \lim_{n \to \infty}\frac{\left\vert \frac{1}{an^2+bn+c} \right\vert}{\left\vert \frac{1}{n^2} \right\vert}
$$

$$
=\displaystyle \lim_{n \to \infty}\left\vert \frac{n^2}{an^2+bn+c} \right\vert=\left\vert \frac{1}{a} \right\vert
$$

로 양수로 존재합니다. 그런데 $\sum_{n=1}^{\infty}\frac{1}{n^2}$는 수렴하므로 $\sum_{n=1}^{\infty}\frac{1}{an^2+bn+c}$도 수렴합니다.

이제 $\frac{1}{an^2+bn+c}=\frac{1}{a(n^2+\alpha n+\beta )}$로 두고 $D=\alpha ^2-4\beta $에 따라 다뤄보겠습니다.

---

## $D>0$일 때

$n^2+\alpha n+\beta =0$의 두 실근을 $p, q$라 두면 

$$
\sum_{n=1}^{\infty}\frac{1}{n^2+\alpha n+\beta }=\sum_{n=1}^{\infty}\frac{1}{(n-p)(n-q)}=\frac{1}{p-q}\sum_{n=1}^{\infty}\frac{1}{n-p}-\frac{1}{n-q}
$$

이 됩니다. 여기서 $p-q\in \mathbb{Z}$라면 망원급수로 쉽게 풀리지만 $p-q\in \mathbb{R}-\mathbb{Z}$라면 망원급수로 풀리지 않습니다.


---

## Polygamma function

폴리감마 함수는 $\ln \Gamma (z)$를 $z$에 대해 여러번 미분한 함수입니다. 

$$
\psi _n(z)=\frac{d^{n+1}}{dz^{n+1}}\ln \Gamma (z)
$$

으로 정의되며 $\psi _0(z)$은 $\psi (z)$으로도 표기합니다.

이제 디감마 함수, $\psi (z)$를 

$$
\Gamma (z)=\frac{1}{z}e^{-\gamma z}\prod_{k=1}^{\infty}\frac{e^{\frac{z}{k}}}{1+\frac{z}{k}}
$$

을 이용하여 나타내보겠습니다. 여기서 $\gamma $는 다음과 같이 정의되는 오일러-마스케로니 상수입니다.

$$
\gamma =\displaystyle \lim_{n \to \infty}\left ( \sum_{k=1}^{n}\frac{1}{k}-\ln n\right )
$$

---

## Using Digamma function

$$
\ln \Gamma (z)=-\ln z-\gamma z+\sum_{k=1}^{\infty}\left ( \frac{z}{k}-\ln \left ( 1+\frac{z}{k} \right )\right )
$$

$$
\psi (z)=\frac{d}{dz}\ln \Gamma (z)=-\frac{1}{z}-\gamma +\sum_{k=1}^{\infty}\left ( \frac{1}{k}-\frac{1}{k+z} \right )=-\gamma +\sum_{k=1}^{\infty}\left ( \frac{1}{k}-\frac{1}{k+z-1} \right )
$$

을 얻을 수 있습니다. 이제 우리가 원하는 꼴인 $\psi (-p+1)-\psi (-q+1) $을 구해보면

$$
\psi (-p+1)-\psi (-q+1)=\sum_{k=1}^{\infty}\left ( \frac{1}{k}-\frac{1}{k-p} \right )-\sum_{k=1}^{\infty}\left ( \frac{1}{k}-\frac{1}{k-q} \right )=-\sum_{k=1}^{\infty}\left ( \frac{1}{k-p}-\frac{1}{k-q} \right )
$$

이 되므로 다음과 같은 결과를 얻을 수 있습니다.

$$
\sum_{n=1}^{\infty}\frac{1}{(n-p)(n-q)}=\frac{\psi (-q+1)-\psi (-p+1)}{p-q}
$$

---

## $D=0$일 때

$n^2+\alpha n+\beta =(n+p)^2$로 두면

$$
\sum_{n=1}^{\infty}\frac{1}{(n+p)^2}
$$

이 됩니다. $p\in \mathbb{Z}^{0+}$일 땐 $\zeta (2)$를 사용하여 풀 수 있지만 $p\in \mathbb{R}-\mathbb{Z}$인 경우는 다른 방법으로 풀어야 합니다.

---

## Using Trigamma function

위에서 구한 디감마 함수, $\psi (z)$를 $z$에 대해 미분하여 트리감마 함수, $\psi _1(z)$를 나타내보면

$$
\frac{d}{dz}\psi (z)=\frac{d}{dz}\left ( -\gamma +\sum_{k=1}^{\infty}\left ( \frac{1}{k}-\frac{1}{k+z-1} \right )\right )=\sum_{k=1}^{\infty}\frac{1}{(k+z-1)^2}
$$

을 얻을 수 있습니다. 결과적으로

$$
\sum_{n=1}^{\infty}\frac{1}{(n+p)^2}=\psi _1(p+1)
$$

이 성립합니다.

---

## $D<0$일 때

$n^2+\alpha n+\beta =(n+p)^2+q^2$꼴일 땐, 일반적으론 초등 함수으로 값을 나타낼 수 없으며 

$\alpha =1$일 땐, 복소해석학을 통해, $\alpha =0$엔 푸리에 급수를 통해서도 유도할 수 있습니다.

이 글에선 푸리에 급수를 통해, 즉 $\alpha =0$일 때만 유도해보겠습니다.

---

## Using Fourier Series

$$
f(x)=\left\{
\begin{array}{l}
\cosh (ax) ,(x\in [-\pi, \pi]) \\
f(x+2\pi) ,(x\in\mathbb{R-[-\pi, \pi]})
\end{array}
\right.
$$

인 함수를 생각해보겠습니다. $f(x)$를 $[-\pi, pi]$에서 푸리에 급수로 표현하면

$$
f(x)=a_0+\sum_{n=1}^{\infty}a_n\cos (nx)+\sum_{n=1}^{\infty}b_n\sin (nx)
$$

이 되고 $\cosh(ax) $는 even function이므로 $b_n=0$이 됩니다. 푸리에 계수는

$$
a_0=\frac{1}{2\pi}\int _{-\pi}^{\pi}\cosh (ax)dx, a_n=\frac{2}{\pi}\int _{-\pi}^{\pi}\cosh (ax)\cos (nx)dx
$$

다음과 같이 되고 정적분을 계산해보면

$$
a_0=\frac{2}{2\pi}\left [ \frac{\sinh (ax)}{a} \right ]^\pi_0=\frac{\sinh (a\pi)}{a\pi},
a_n=\frac{1}{\pi}\int_{-\pi}^{\pi}\cosh(ax)\cos(nx)=\frac{2a\sinh (a\pi)}{\pi}\frac{(-1)^n}{n^2+a^2}
$$

이 됩니다. 결과적으로

$$
f(x)=\frac{\sinh(a\pi)}{a\pi}+\sum_{n=1}^{\infty}\frac{2a\sinh(a\pi)}{\pi}\frac{(-1)^n}{n^2+a^2}\cos(n\pi)
$$

을 얻을 수 있습니다. 그런데 $\cos(n\pi)=(-1)^n$이므로 $x=\pi$을 대입하면

$$
\frac{2a\sinh(a\pi)}{\pi}\sum_{n=1}^{\infty}\frac{1}{n^2+a^2}=\cosh(a\pi)-\frac{\sinh(a\pi)}{a\pi}
$$

$$
\sum_{n=1}^{\infty}\frac{1}{n^2+a^2}=\frac{\pi}{2a}\coth(a\pi)-\frac{1}{2a^2}
$$

을 얻을 수 있습니다.

---

## Example

$$
\begin{aligned}
1. &\sum_{n=1}^{\infty}\frac{1}{6n^2-5n+1}=\frac{\pi}{2\sqrt{3}}-\frac{3}{2}\ln 3+2\ln 2\\
2. &\sum_{n=1}^{\infty}\frac{1}{4n^2+4n+1}=\frac{\pi^2}{8}-1\\
3. &\sum_{n=1}^{\infty}\frac{1}{n^2+1}=\frac{\pi\coth\pi-1}{2}
\end{aligned}
$$
