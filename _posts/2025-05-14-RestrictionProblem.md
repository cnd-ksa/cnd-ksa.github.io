---
title: Fourier Restriction Problem
date: 2025-05-14 12:00:00 +0900
categories: [Analysis, Fourier Analysis]
tags: [Hilbert space, Restriction Problem, Analysis, Fourier analysis, Functional Analysis]
author: ksa22118
math: true
---


## Definition of Fourier Transform

함수 $f \in L^1(\mathbb{R}^n)$에 대한 푸리에 변환은 다음과 같이 정의됩니다:

$$
\hat{f}(\xi) = \int_{\mathbb{R}^n} f(x) \; e^{-2\pi i x \cdot \xi} \; dx
$$

푸리에 변환은 $L^1(\mathbb{R}^n)$에서 $C_0(\mathbb{R}^n)$으로의 변환이기에, $\hat{f}$는 $\mathbb{R}^n$ 전체에서 정의되어 있습니다.

또한 $L^1 \cap L^2$는 $L^2$에서 dense하므로, 푸리에 변환은 $L^2$ 전체로 유일하게 확장될 수 있으며,

$$
\Vert\hat{f}\Vert_{L^2} = \Vert f \Vert_{L^2}
$$

임이 잘 알려져 있습니다 (Plancherel Theorem). 즉, 푸리에 변환은 $L^2$ 위에서 unitary operator로 작용합니다.

---

## Uncertainty Principle

푸리에 변환은 위치 정보와 주파수 정보를 동시에 정확히 파악할 수 없는 구조적 한계를 지닙니다.  
가장 잘 알려진 Heisenberg Uncertainty Principle은 다음과 같습니다.

$f \in L^2(\mathbb{R})$이고, mean이 0일 때:

$$
\left( \int_{\mathbb{R}} x^2 |f(x)|^2 \; dx \right)
\left( \int_{\mathbb{R}} \xi^2 |\hat{f}(\xi)|^2 \; d\xi \right)
\geq \frac{1}{16\pi^2} \left( \int_{\mathbb{R}} |f(x)|^2 \; dx \right)^2
$$

즉, 함수 $f$가 특정한 위치에 집중될수록, $\hat{f}$는 넓은 주파수 대역에 퍼지게 되며, 두 함수를 동시에 localized 할 수 없습니다.

---

## Restriction Problem

Restriction Problem이란, 위의 uncertainty를 정량적으로 분석하기 위해,  
$\hat{f}$가 $\mathbb{R}^n$의 어떤 곡면 $S$ 위에 concentrated 되어 있을 때  
($S$ 바깥에서는 무시할 수 있을 정도일 때), 원래 함수 $f$는 얼마나 **regular**하거나 **integrable**해야 하는지를 묻는 문제입니다.

즉, $f \in L^p(\mathbb{R}^n)$일 때,  
$S$가 smooth한 $(n-1)$차원 곡면이고, $d\sigma$가 $S$ 위의 surface measure라면,  
다음과 같은 부등식이 성립하도록 만드는 $p, q$의 조건을 찾는 것입니다:

$$
\Vert\hat{f}\vert_S\Vert_{L^q(S, d\sigma)} \leq C \Vert f\Vert_{L^p(\mathbb{R}^n)} \quad \text{(단, $1 \leq p \leq 2$, $q \geq 1$)}
$$

---
