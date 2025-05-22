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

