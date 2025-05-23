---
title: Fourier Restriction Problem
date: 2025-05-14 12:00:00 +0900
categories: [Analysis, Fourier Analysis]
tags: [Hilbert Space, Restriction Problem, Analysis, Fourier Analysis, Functional Analysis]
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


## Tomas–Stein Theorem

이 문제에 대한 고전적인 결과로는 **Tomas–Stein theorem**이 있습니다.

$$
S = S^{n-1} \subset \mathbb{R}^n \text{일 때,} \quad p \leq \frac{2(n+1)}{n+3}
$$

이면 restriction inequality가 성립합니다.

이 정리는 restriction theory의 출발점이 되었고, 이후 다양한 확장들이 이루어졌습니다.

---

## Stein's Conjecture

Stein은 다음과 같은 **sharp한 restriction inequality**를 제안했습니다:

$S = S^{n-1}$이고, $q \leq p' = \frac{p}{p-1}$일 때,  
$p < \frac{2n}{n+1}$이면 restriction inequality가 성립하고,  
그 외에는 성립하지 않는다는 것이며, 이는 아직 $n \geq 3$**에서는 미해결**입니다.

---

## Bilinear & Multilinear Restriction Theorems

이 외에도 함수 하나가 아닌 여러 함수의 곱에 대해 restriction inequality를 적용한 결과들이 있습니다.

**Bilinear Restriction Theorem**은 $\hat{f}$, $\hat{g}$가 주파수 영역에서 분리되어 있을 때,

$$
\Vert \hat{f}\vert_S\cdot \hat{g}\vert_S\Vert_{L^r(S)} \leq C \Vert f \Vert_{L^p} \Vert g \Vert_{L^p}
$$

같은 형태의 부등식이 성립함을 보여줍니다.

**Multilinear Restriction Theorem**은 세 개 이상의 함수에 대해 더 정교한 결과를 제공하며,  
restriction problem을 해석하는 데 강력한 도구로 사용됩니다.

---

## Connection with Kakeya problem

신기하게도 restriction inequality의 **sharpness**는 **Kakeya problem**과도 깊게 연결되어 있습니다.

Kakeya problem이란, $\mathbb{R}^n$에서 **모든 방향의 단위 선분을 포함하는 가장 작은 집합의 부피(또는 차원)**를 묻는 문제입니다.  
이 문제는 특히 $n \geq 4$에서 아직까지 해결되지 않았습니다.

Restriction problem의 최적의 $L^p \to L^q$ 부등식을 얻으려면,  
주파수 공간에서 특정 방향에 집중된 함수들을 분석해야 하고,  
그 함수들이 공간적으로 얼마나 concentrate될 수 있는지 평가하는 과정에서  
**Kakeya-type 집합의 기하적 구조**가 자연스럽게 등장하게 됩니다.

---

## Ending

Restriction problem은 Kakeya problem과 연관이 깊은만큼 아직까지도 많은 미해결 문제가 존재합니다. Stien's conjecture 상에는 $p' = \frac{p}{p-1}$이라고 하는 수가 등장합니다.

$$
\frac{1}{p} + \frac{1}{p'} = 1
$$

을 만족하는 $p'$은 푸리에 변환에 있어 매우 중요한 역할을 합니다. 다음 포스트에서는 그 이유를 소개해보도록 하겠습니다.
