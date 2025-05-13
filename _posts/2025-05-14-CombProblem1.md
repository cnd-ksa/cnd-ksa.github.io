---
title: 조합 문제 풀이 (1)
date: 2025-05-14 01:00:00 +0900
categories: [Discrete Mathematics, Combinatorics]
tags: [Problem Solving, Combinatorics, Discrete Mathematics, Construction, Olympiad]
author: ksa23063
math: true
---


## 문제


Let $\\{ M_i \mid 1 \le i \le 11, i \in \N \\}$ be a collection of sets, where $\lvert M_i\rvert = 5$ and $M_i \cap M_j \ne \varnothing$ for all $1 \le i < j \le 11$. Let $m$ be the largest number for which there exist $M_{i_1}, ..., M_{i_m}$ among the chosen sets with $\bigcap_{k=1}^m M_{i_k} \ne \varnothing$. Find the minimal value of $m$ over all initial choices of $M_i$.

## 풀이

먼저 풀이를 보자. 답은 $m = 4$이다. $m$이 4임을 보이기 위해서
- $m \le 4$이며 (upper bound),
- $m \ge 4$ (lower bound)

임을 증명해야 한다.

### $m \ge 4$

이 말은 곧 $M_1, ..., M_{11}$의 선택에 아무런 관계없이 공통 원소를 공유하는 4개의 집합을 고를 수 있음을 의미한다. 

먼저 $M_i$들이 어디에 속해있는지를 먼저 잡아주어야 뭔가 구체화시킬 수 있을 것 같다. $X = \bigcup_{i=1}^{11} M_i$로 두자. 그리고 각각의 $x \in X$에 대하여 $A_x = \\{ i \mid x \in M_i \\}$로 정의해 보자. 그러면 문제를 $A_x$의 언어로 다시 쓸 수 있게 된다.

$$(1) \; M_i \cap M_j \ne \varnothing \implies \exists x \in X \text{ such that } \\{ i, j \\} \subseteq A_x$$

$$(2) \; \cap_{k=1}^m M_{i_k} \ne \varnothing \implies \exists x \in X \text{ such that } \lvert A_x\rvert \ge m \implies \max_{x \in X} |A_x| \ge m$$

$$
(3) \; \text{Eleven sets} \implies 1 \le |A_x| \le 11
$$

$$
\begin{aligned}
(4) \; M_i : \text{set of five elements} \implies
\sum_{x \in X} |A_x| &= \sum_{x \in X} \sum_{i \in A_x} 1 \\
&= \sum_{i=1}^{11} \sum_{x \in M_i} 1 \\
&= \sum_{i=1}^{11} |M_i| = 55.
\end{aligned}
$$

이렇게 formulation을 하면 여러 개를 선택하는 상황을 고려해야 했던 이전의 상황과는 달리 $\lvert A_x\rvert$의 최댓값만 살피면 상황으로 단순화되었다.

이 상황에서 이제 $\max_{x\in X} \lvert A_x\rvert$의 lower bound를 최대한 끌어올려 보자. 우리가 $\lvert A_x\rvert$의 크기에 대해 알고 있는 것은 합밖에 없다. 이로부터 알 수 있는 건
$$ \exists x \in X \text{ such that } \lvert A_x\rvert \ge \frac{55}{\lvert X\rvert} $$
이다. 즉 $\lvert X\rvert$의 크기의 upper bound를 줄이다 보면 $m$의 lower bound를 찾을 수 있을지도 모른다. 실제로 $\lvert X\rvert \le 55$이긴 하지만 $M_i$끼리 많이 겹치므로 bound를 꽤 줄일 수 있을 것 같다.

하지만 이런 접근은 통하지 않는다. 극단적인 예시로 $M_i$들이 전부 공통된 원소 하나만을 공유하고 나머지 부분은 서로소라고 가정하자. 그러면 $\lvert X\rvert = 55-1 = 54$로 매우 크다. 다른 접근이 필요해 보인다.

만약 $\lvert A_x\rvert \le 2, \forall x \in X$라 가정하자. (1)에 의하여 임의의 $i \ne j$에 대하여 $A_x = \\{ i, j \\}$인 $x$가 존재하므로 $\binom{11}{2} = 55$개의 pair에 대하여 정확히 하나의 $A_x$가 대응되고, 이 관계는 injective하다. 따라서 $\lvert X\rvert \ge 55$이다. 이는 $M_i$끼리 pairwise disjoint해야 겨우 얻어질 수 있으므로 조건에 모순. 즉 $m \ge 3$을 얻는다.

$\lvert A_x\rvert \le 3, \forall x \in X$라 가정하고 조금 더 정교하게 들여다본다. $\\{1, 2\\}, ..., \\{1, 11\\}$의 10개의 pair들이 $A_x$들에 포함되어야 하는데, 3개 이상의 pair가 한 $A_x$의 부분집합이 될 수 없다. 또한 이중 정확히 하나의 pair만 부분집합으로 가지는 $A_x$ 또한 존재할 수 없다. (그러면 이들을 부분집합으로 가지는 $A_x$가 6개 이상이어야 하고, 이는 $\lvert M_i\rvert = 5$에 위배됨) 따라서 이들을 2개씩 총 5개의 $A_x$에 나누어서 집어넣어야 하고, 이때 각 $A_x$들은 정확히 3개의 원소를 가진다.

$\\{2, 3\\}, ..., \\{2, 11\\}$을 보면 이중 하나는 이전 step에서 이미 어떤 $A_x$의 부분집합에 들어가 있다. 남은 8개의 pair에 대해 이전과 동일한 논리를 적용하면 정확히 3개의 원소를 가지는 4개의 $A_x$들로 쪼개짐을 확인할 수 있다.

이런 step을 모든 남은 pair들에 대해 순차적으로 반복하자. 그러면 $\lvert A_x\rvert = 3$인 $5+4+3+...+1=15$개의 set을 얻고, 이외에 다른 $A_x$가 추가적으로 있으면 안 된다. $(\lvert M_i\rvert = 5$ 조건을 위배) 그런데 $\sum_{x \in X} \lvert A_x\rvert = 3 \times 15 = 45 < 55$이므로 모순.

이로부터 $m \ge 4$를 얻는다.



### $m \le 4$

Tightness를 보이기 위해서는 4개가 최대로 고를 수 있는 $M_i$들을 직접 구성해 주면 된다. 여기서 $A_x$를 조건을 만족시키도록 구성하는 것이 $M_i$를 구성하는 것과 동치임을 확인하고, $A_x$를 구성해 보았다. 굳은 의지를 가지고 열심히 해보면 아마 잘 구성할 수 있을 것이다. 다음은 내가 찾은 예시이다.

$$A_{x_1} = \{ 1, 2, 3, 4 \}, A_{x_2} = \{ 1, 5, 6, 7 \},\\
A_{x_3} = \{ 1, 8, 9, 10 \}, A_{x_4} = \{ 2, 5, 3, 6 \},\\
A_{x_5} = \{ 2, 7, 3, 8 \}, A_{x_6} = \{ 2, 9, 3, 10 \},\\
A_{x_7} = \{ 4, 5, 8, 11 \}, A_{x_8} = \{ 4, 6, 9, 11 \},\\
A_{x_9} = \{ 4, 7, 10, 11 \}, A_{x_{10}} = \{ 1, 2, 3, 11 \},\\
A_{x_{11}} = \{ 5, 6, 9, 10 \}, A_{x_{12}} = \{ 6, 7, 8, 9 \},\\
A_{x_{13}} = \{ 1, 4, 5, 7 \}, A_{x_2} = \{ 8 \}.$$

여기서 $\max_{x \in X} \lvert A_x\rvert = 4$이므로 $m \le 4$가 명백하다.

## 코멘트

전형적인 최대/최소값을 구하는 조합 문제이다. 집합에서 원소의 포함 관계를 다루는 문제에서는 이처럼 double counting 느낌으로 $A_x$를 정의하면 문제가 단순화될 수 있다는 점을 기억하자.

이렇게 어떤 collection이 얼마나 커질 수/작아질 수 있는지의 문제를 해결하는 분야를 Extremal combinatorics(극단조합론)이라 한다. 이런 종류의 문제에 관심 있으면 공부해 보자.

## 출처

위 문제는 Titu의 102 Combinatorial Problems From the Training of the USA IMO Team에서 발췌한 문제이다.
