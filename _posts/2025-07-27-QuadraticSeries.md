---
title: Fourier Restriction Problem
date: 2025-05-14 12:00:00 +0900
categories: [Analysis, Fourier Analysis]
tags: [Hilbert Space, Restriction Problem, Analysis, Fourier Analysis, Functional Analysis]
author: ksa22118
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

이제 $\frac{1}{an^2+bn+c}=\frac{1}{a(n^2+\alpha n+\beta )}$로 두고 $
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
