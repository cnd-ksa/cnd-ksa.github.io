---
title: Integration Of Metamorphosis of Infinite Power Tower Function
date: 2025-08-16 12:00:00 +0900
categories: [Integration]
tags: [Integration, Lambert W Function, Infinite Power Tower Function]
author: ksa25114
math: true
---


## Introduction

다음과 같은 이상적분

$$
\int_{0}^{1}{(x^x)}^{{{(x^x)}^{{(x^x)}^{...}}}}dx
$$

의 값은 어떻게 구할 수 있을까요? 이를 구하기 전에 사용될 함수 람베르트 $W$ 함수에 대한 간단한 소개를 하겠습니다.

---

## Lambert W Function

람베르트 $W$ 함수는 다음 함수의 역함수로 정의됩니다.

$$
f(x)=xe^x
$$

그런데 $xe^x$는 단사 함수가 아니므로 다음 그래프와 같이 $W_0(x)$와 $W_{-1}(x)$로 나눠서 정의합니다.

![construction](./images/Lambert W Function.png){:width="400"}

이제 람베르트 $W$ 함수를 사용하여 원래 풀려 했던 적분을 구해보겠습니다.

## Infinite Power Tower To Lambert W Function

$$
{(x^x)}^{{{(x^x)}^{{(x^x)}^{...}}}}=y
$$

라고 두겠습니다. 그러면

$$
{(x^x)}^y=y=e^{xy\ln x}
$$

$t=-xy\ln x$로 치환하면

$$
\frac{t}{-x\ln x}=e^{-t},\;te^t=-x\ln x
$$

$x\in (0,1)$에서 $-x\ln x\in (0,\frac{1}{e}]$이므로

$$
t=W_0(-x\ln x),\;y=\frac{W_0(-x\ln x)}{-x\ln x}
$$

를 얻을 수 있습니다.

---


## Maclaurin Series Of Lambert W Function

$W_0(x)$의 맥클로린 급수는 다음과 같으며

$$
W_0(x)=\sum_{n=1}^{\infty }\frac{(-n)^{n-1}}{n!}x^n
$$

$\left | x\right |<\frac{1}{e}$에서 수렴하고 추가로 $x=\frac{1}{e}$에서도 수렴합니다.

정적분 범위에서 $W_0(x)$의 맥클로린 급수가 수렴하므로 처음 적분을 다음과 같이 적을 수 있습니다.

$$
I=\int_{0}^{1}\frac{W_0(-x\ln x)}{-x\ln x}dx=\sum_{n=1}^{\infty}\frac{(-n)^{n-1}}{n!}\int_{0}^{1}(-x\ln x)^{n-1}dx
$$

$$
I=\sum_{n=1}^{\infty}\frac{n^{n-1}}{n!}\int_{0}^{1}(x\ln x)^{n-1}dx
$$

---

## Solving Infinity Series

$x=e^{-t}$로 치환하면 $dx=-e^{-t}dt$이고

$$
\int_{0}^{1}(x\ln x)^{n-1}dx=\int_{\infty}^{0}-(-t)^{n-1}e^{-nt}dt=(-1)^{n-1}\int_{0}^{\infty}t^{n-1}e^{-nt}dt
$$

$nt=u$로 치환하여 정리하면

$$
\frac{(-1)^{n-1}}{n^n}\int_{0}^{\infty}u^{n-1}e^{-u}du=(-1)^{n-1}\frac{\Gamma (n)}{n^n}=(-1)^{n-1}\frac{(n-1)!}{n^n}
$$

---

## Final Calculation

처음 적분에 대입해보면

$$
I=\sum_{n=1}^{\infty}(-1)^{n-1}\frac{n^{n-1}}{n!}\frac{(n-1)!}{n^n}=\sum_{n=1}^{\infty}\frac{(-1)^{n-1}}{n^2}
$$

$$
\sum_{n=1}^{\infty}\frac{(-1)^{n-1}}{n^2}=(1-2^{-1})\zeta (2)
$$

이므로 처음 적분은

$$
\int_{0}^{1}{(x^x)}^{{{(x^x)}^{{(x^x)}^{...}}}}dx=\frac{\pi^2}{12}
$$

---
