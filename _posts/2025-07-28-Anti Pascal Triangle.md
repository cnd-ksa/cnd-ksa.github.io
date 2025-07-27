---
title: Existence of Anti-Pascal Triangel (2018 IMO)
date: 2025-07-27 11:59:00
categories: Combinatorics
tags: [Olympiad, Problem Solving, Combinatorics, Logics]
author: ksa25078
math: true
---
## Problem
An *anti-Pascal* triangle is an equilateral triangular array of numbers such that, except for the numbers in the bottom row, each number is the absolute value of the difference of the two numbers immediately below it. For example, the following is an *anti-Pascal* triangle with four rows which contains every integer from $\displaystyle 1$ to $\displaystyle 10$.
$$ 4 $$
$$ 2 \hspace{5mm} 6$$
$$ 5 \hspace{5mm} 7 \hspace{5mm} 1 $$
$$ 8 \hspace{4.5mm} 3 \hspace{4.5mm} 10 \hspace{4.5mm} 9$$
Does there exist an *anti-Pascal* triangle with $\displaystyle 2018$ row which contains every integer from $\displaystyle 1$ to $\displaystyle 1+2+3+ \cdots +2018$?

아래에 있는 두 수의 차가 위에 있는 수가 되는 구조를 역 파스칼 삼각형이라고 할 때 한 변의 길이가 2018인 역 파스칼 삼각형이 존재하는지를 묻고 있다.

## Step 1
첫 번째 줄의 숫자를 $\displaystyle a_1$이라고 하자. $\displaystyle a_1$바로 아래의 두 숫자 중 작은 숫자를 $\displaystyle a_2$, 큰 숫자를 $\displaystyle A_2$라고 하면 $\displaystyle A_2=a_1+a_2$ $\displaystyle a_2$바로 아래의 두 숫자 중 작은 숫자를 $\displaystyle a_3$, 큰 숫자를 $\displaystyle A_3$라고 하면 $\displaystyle A_3=a_3+A_2=a_1+a_2+a_3$.

일반적으로 $\displaystyle a_i$바로 아래의 두 숫자 중 작은 숫자를 $\displaystyle a_{i+1}$, 큰 숫자를 $\displaystyle A_{i+1}$라고 하면 $\displaystyle A_{i+1}=a_{i+1}+A_i=a_1+a_2+\cdots+a_{i+1}$. 이에 대한 증명은 생략한다.

이 과정을 통해 얻어지는 $\displaystyle a_1, a_2, \cdots a_{2018}$과 $\displaystyle A_2, A_3, \cdots, A_{2018}$을 생각하자. 편의상 $\displaystyle A_1=a_1$이다. $\displaystyle A_{2018}=a_1+a_2+\cdots+a_{2018}$라는 사실에 주목하자. $\displaystyle A_{2018}$은 $\displaystyle 2018$개의 서로 다른 자연수의 합이므로 $\displaystyle 1+2+\cdots+2018$이상이다. 그런데, $\displaystyle A_{2018}$은 한변의 길이가 $\displaystyle 2018$인 역 파스칼 삼각형에 있는 숫자이므로 $\displaystyle 1+2+\cdots+2018$이하이기도 한다.

$$1+2+\cdots+2018 \geq A_{2018} \geq 1+2+\cdots+2018$$
$$\therefore A_{2018}=1+2+\cdots+{2018}$$

또 두 등호가 모두 성립해야 하므로

$$a_1+a_2+\cdots+a_{2018}=1+2+\cdots+2018$$
$$\{ a_1, a_2, \cdots, a_{2018}\} =\{ 1, 2, \cdots, 2018\} \hspace{1mm} \cdots *$$ 
또한, $\displaystyle i \geq 2$인 $\displaystyle i$에 대해 $\displaystyle a_i$왕 $\displaystyle A_i$는 이웃해 있다는 점을 기억해두자.

## Step 2
$\displaystyle \frac{2018}{2}+2=1011$ 번째 줄을 생각한다. 가장 왼쪽의 숫자를 $\displaystyle x_{1011}$ 이라고 하자. $\displaystyle x_{1011}$바로 아래의 두 숫자 중 작은 숫자를 $\displaystyle x_{1012}$, 큰 숫자를 $\displaystyle X_{1012}$라고 하면 $\displaystyle X_{1012}=x_{1011}+x_{1012}$. $\displaystyle X_{1012}$ 바로 아래의 두 숫자 중 작은 숫자를 $\displaystyle x_{1013}$, 큰 숫자를 $\displaystyle X_{1013}$라고 하면 $\displaystyle X_{1013}=x_{1013}+X_{1012}=x_{1011}+x_{1012}+x_{1013}$.

일반적으로 $\displaystyle x_i$바로 아래의 두 숫자 중 작은 숫자를 $\displaystyle x_{i+1}$, 큰 숫자를 $\displaystyle X_{i+1}$라고 하면 $\displaystyle X_{i+1}=x_{i+1}+X_i=x_1+x_2+\cdots+x_{i+1}$. 이에 대한 증명도 생략한다.

이 과정을 통해 얻어지는 $\displaystyle x_{1011}, x_{1012}, \cdots x_{2018}$과 $\displaystyle X_{1012}, X_{1013}, \cdots, X_{2018}$을 생각하자. 편의상 $\displaystyle X_{1011}=x_{1011}$이다. 

$\displaystyle x_i \hspace{1mm} (1011 \leq i \leq 2018)$들 중 $\displaystyle \{ 1, 2, \cdots, 2018 \}$
의 원소가 없다고 가정하자. 즉, $\displaystyle x_i$ 들은 모두 $\displaystyle 2018$ 초과인 것이다. $\displaystyle X_{2018}=x_{1011}+x_{1012}+\cdots+x_{2018} \geq 2019+2020+\cdots +3026 > 1+2+\cdots +2018$. 한변의 길이가 $\displaystyle 2018$인 역 파스칼 삼각형에 있는 숫자이므로 $\displaystyle X_n \leq 1+2+\cdots+2018$이므로 모순.
$$\therefore \exist \hspace{1mm} i \in \{ 1011, 1012, \cdots, 2018 \} \hspace{3mm} s.t. \hspace{3mm} x_i \in \{ 1, 2, \cdots, 2018 \} \hspace{1mm} \cdots **$$

## Step 3
$$T(x) := x 
\text{를 위쪽 꼭짓점으로 갖는 가장 큰 삼각형}$$
$\displaystyle **$에 따르면 $\displaystyle a_i \in T(x_{1011})$인 $\displaystyle i \hspace{1mm} (i \geq 1011)$가 존재한다. 그럼 $\displaystyle x_{1011}$ 바로 위의 값 $\displaystyle \alpha$에 대해 $\displaystyle a_i$가 $\displaystyle A_i$는 이웃이므로 ($\displaystyle \hspace{0.5mm} \because *$)    $\displaystyle \hspace{0.5mm}A_i \in T(\alpha)$이 성립한다. 

$\displaystyle A_i$ 바로 아래 두 칸 중 하나에 $\displaystyle A_{i+1}$이 있으므로 $\displaystyle A_{i+1} \in T(\alpha)$이다. 이를 반복하면 $\displaystyle A_{2018} \in T(\alpha)$를 얻을 수 있다.

$\displaystyle 1011$번째 줄의 가장 오른쪽의 숫자 $\displaystyle y_{1011}$에 대해서 같은 시행을 반복하자. 그럼 $\displaystyle y_{1011}$ 바로 위의 값 $\displaystyle \beta$에 대해 $\displaystyle A_{2018} \in T(\beta)$가 성립한다. 

$\displaystyle A_{2018}$은 $\displaystyle T{\alpha}$에도 존재하고 $\displaystyle T(\beta)$에도 존재하는 값이다. 그런데, $\displaystyle T(\alpha)$와 $\displaystyle T(\beta)$는 공통부분이 없기 때문에 모순이다. 즉, 한변의 길이가 $\displaystyle 2018$인 역 파스칼 삼각형은 존재하지 않는다.

<div align="center">
<img src="my_image.jpg" alt="사진1">
</div>
