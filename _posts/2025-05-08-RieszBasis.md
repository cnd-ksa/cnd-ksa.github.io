---
title: Riesz Basis
date: 2025-05-08 08:50:00 +0900
categories: [Analysis, Functional Analysis]
tags: [Analysis, Functional Analysis, Fourier Analysis, Riesz basis, Hilbert Space]
author: 22-118 Moongyun Chae
math: true
---
## Riesz Basis

Riesz basis란, 신호처리나 물리학 등에서 실제 구현 가능한 일반적인 basis를 구성하기 위해 고안된 개념입니다. 때문에 orthogonal한 성질은 사라지지만, completeness와 stability를 여전히 만족하고 있습니다.

### Definition of a Riesz Sequence

힐베르트 공간 상에서 Riesz sequence란, 다음을 만족하는 vector sequence $\{ x_n \}$을 말합니다.
어떠한 양의 실수들 $c \leq C$가 존재하여, 임의의 $\ell^2$ space 상의 복소수 수열 $\{ a_n \}$에 대해

$$
c \left(\sum |a_n|^2\right) \leq \left\| \sum a_n x_n \right\|^2 \leq C \left(\sum |a_n|^2\right)
$$

을 만족합니다.

이때, $\mathrm{span}\{ x_n \}$의 closure가 $\mathcal H$ 전체가 될 때 이를 Riesz basis라고 합니다.

### Relationship with Orthonormal Bases

이는 Fundamental theorem of Hilbert spaces에 의해, $\{ x_n \}$은 $\ell^2$에서 $\mathcal H$로 가는 어떤 bounded, invertible linear operator의 image가 됩니다. 즉, 어떤 orthonormal basis $e_n$에 대해 $x_n = T(e_n)$ 꼴로 작성할 수 있습니다.

반대로 Hilbert space에서 orthonormal한 basis는 Parseval's identity,

$$
\left\| \sum a_n e_n \right\|^2 = \sum |a_n|^2
$$

가 언제나 성립함을 의미합니다.
즉, 임의의 bounded, invertible linear operator $T$에 대해 $x_n := T(e_n)$이라 하면

$$
\left\|\sum a_n x_n\right\| = \left\|T\left( \sum a_n e_n\right)\right\| \leq \|T\|\cdot\left\|\sum a_n e_n\right\|
$$

$$
\left\|\sum a_n x_n\right\| \geq \|T^{-1}\|^{-1} \cdot \left\|\sum a_n e_n\right\|
$$

을 만족하므로 Riesz basis가 됨을 알 수 있습니다.

따라서 Riesz basis는 *어떤 orthonormal basis를 linear operator를 이용해 **약간 비튼** basis*임을 알 수 있습니다.

### Example: Kadec's 1/4 Theorem

이에 대한 대표적인 예시로는 $\exp(2\pi ix \lambda_n)$ 꼴의 집합을 생각할 수 있습니다.
Fourier series에서 $\{\exp(2\pi inx)\}$은 $\mathcal L^2(0,1)$의 orthonormal한 basis가 됨이 잘 알려져있지만, $\lambda_n = n+\delta_n$ 꼴로 약간만 비틀었을 때도 $\mathcal L^2(0,1)$의 basis가 될 수 있는가?와 같은 의문점이 남게 됩니다.
이에 대해서는 Kadec's 1/4 Theorem에 의해 $|\lambda_n - n| < \frac14$이면, $\mathcal L^2(0,1)$의 Riesz basis가 된다고 잘 알려져있습니다.

### Applications and Current Research

또한, 앞서 언급한 바와 같이 Riesz basis는 completeness와 stability를 만족하기에 수치해석적으로도 많이 활용되며, 특히 PDE의 해 공간의 basis로 eigenfunction이 Riesz basis가 되면 해를 stable하고 unique하게 표현 가능하다는 등의 장점이 있습니다. 그럼에도 불구하고 아직 Reisz basis에 관해서는 밝혀지지 않은 부분이 여럿 있어 현재까지도 연구가 진행되고 있습니다.
