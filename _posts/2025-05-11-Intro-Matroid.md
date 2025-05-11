---
title: Introduction to Matroid
date: 2025-05-11 17:20:00 +0900
categories: [Discrete Mathematics, Matroid Theory]
tags: [Matroid, Algorithm, Graph Theory, Linear Algebra, Matroid Intersection, Minimal Spanning Tree, Bipartite Matching]
author: ksa23027
math: true
---

## 0. Motivation
매트로이드(Matroid)는 선형대수, 그래프이론, 체론 등 여러 분야에서 나타나는 **독립**의 개념을 추상화한 것이다. 그래서 basis, circuit 등 선형대수와 그래프이론의 용어들이 쓰이기도 한다.
 
## 1. Definition
유한집합 $S$와 $I\subseteq \mathcal{P} (S)$가 다음 성질을 만족한다고 하자.
1. $\phi\in I$
2. (Heridity) If $X\in I$ and $Y\subseteq X$ then $Y\in I$
3. (Exchange) If $X\in I$ and $\left\vert Y\right\vert < \left\vert X\right\vert$ then $Y+a\in I$ for some $a\in S$ 

이때 $M=(S,I)$ 를 $S$ 위의 matroid라 하고, $I$의 원소를 independent set이라 한다.

## 2. Examples
1. Free Matroid: 주어진 $S$에 대해 $I=\mathcal{P}(S)$로 둔다.
2. Uniform Matroid: $S$와 음이 아닌 정수 $k$가 주어졌을 때 $I=\\{X\subseteq S:\left\vert X\right\vert\le k\\}$로 둔다.
3. Partition Matroid: $S$와 color function $f: S\rightarrow C$, 음이 아닌 정수들 $k_i$가 주어졌을 때 $I = \\{X\subseteq S: \left\vert X\cap f^{-1}(c_i)\right\vert\le k_i\\}$ 로 둔다.
4. Linear Matroid: $S$를 vector space, $I$를 linearly independent set들의 집합으로 둔다.
5. Graphic Matroid: Undirected graph $G=(V,E)$에 대해 $S=E$, $I=\\{E'\subseteq E:E'\text{ contains no cycle}\\}$ 으로 둔다.
6. Co-graphic Matroid: $S$는 위와 동일, $I=\\{E'\subseteq E:E\setminus E' \text{ is connected}\\}$ 으로 둔다.
7. Transversal Matroid: Bipartite graph $G=(L,R,E)$에 대해 $S=L$, $I=\\{L'\subseteq L:L'\text{ can be matched to some }R'\subseteq R\\}$ 으로 둔다.
8. Algebraic Matroid: Field extension $L/K$가 주어졌을 때 $S$를 $L$의 finite subset, $I$를 algebraically independent set들의 집합으로 둔다.

Independent set을 정의할 때 쓰는 성질들을 matroid-like property라 하자. 예시에서 알 수 있듯이 matroid-like property는 '원소들끼리 서로 독립적인' 성질 혹은 '원소가 적을수록 만족하기 쉬운' 성질 정도로 이해하면 된다.

## 3. Basis, Circuits
Matroid $M$의 maximal independent set을 basis라 하고, minimal dependent set을 circuit이라 한다. Graphic matroid의 경우 basis는 spanning forest들이 되고, circuit은 simple cycle이 된다.

모든 basis는 원소의 개수가 같으며, 이 값을 matroid의 rank라고 한다.

## 4. Making A New Matroid From Originals
두 matroid $M_1=(S_1,I_1), M_2=(S_2,I_2)$에 대해 
- $M_1,M_2$의 direct sum $M_1+M_2$ 을 $(S_1\sqcup S_2, I_1\sqcup I_2)$ 으로 정의한다.
- $M_1, M_2$의 union $M_1\lor M_2$ 을 $(S_1\cup S_2, I_1\cup I_2)$ 으로 정의한다.

Matroid $M=(S,I)$에 대해 
- $R\subseteq S$일 때 $M$의 $R$로의 restriction $M_R$을 $(R, \\{X\cap R\\}_{X\in I})$로 정의한다.
- $M$의 dual $M^{* }=(S,I^{* })$을 다음과 같이 정의한다: $X\in I^{* }$ iff $S-X$ contains some basis of $M$. 이때 $(M^{* })^{* }=M$이 성립한다. 

Co-graphic matroid는 graphic matroid의 dual이다. 

## 5. Maximal Weight Independent Set Problem
Matroid $M=(S,I)$와 weight $w: S\rightarrow\mathbb{R}^{+}$가 주어졌을 때 maximal weight independent set을 찾는 문제는 다음과 같은 그리디 알고리즘으로 해결할 수 있다: 

1. 초기에 $X=\phi$로 둔다. 
2. $S$의 원소를 $w$값이 큰 순서대로 정렬한다.
3. $S$의 원소를 $X$에 하나씩 넣는데, 넣고 나서도 $X$의 independentness가 유지될 때에만 그렇게 하고 아니면 넘어간다. 
4. 위 과정을 마치면 $X$는 maximal weight independent set이 된다. 

Minimal weight independent set도 비슷한 방법으로 구할 수 있다. 이를 graphic matroid에 적용한 것이 minimal spanning tree를 찾는 Kruskal's algorithm이다.

위 알고리즘에서 가장 핵심적인 부분은 주어진 $X$가 independent set인지 판단하는 것으로, 이를 수행하는 알고리즘을 oracle이라 부른다. Kruskal's algorithm에선 disjoint-set 자료구조를 이용하여 oracle을 빠르게 처리한다.

## 6. Matroid Intersection Problem
앞선 문제는 matroid-like property 하나가 주어졌을 때 이를 만족하면서 maxtimal weight를 갖는 subset을 찾는 것이었다. 이제 2개의 matroid-like property가 주어진 상황, 즉 두 matroid $M_1=(S,I_1), M_2=(S,I_2)$와 weight $w:S\rightarrow\mathbb{R}^{+}$가 주어졌을 때 $X\in I_1\cap I_2$이면서 $\sum_{s\in X} w(s)$를 최대화하는 $X$를 찾는 문제를 풀 것이다. 이를 matroid intersection problem이라 한다. 역시 그리디 알고리즘으로 해결할 수 있으며 방법은 다음 장부터 설명한다.

두 matroid의 intersection은 일반적으로 matroid가 되지 않는다. 따라서 3개 이상의 matroid intersection을 구하는 것은 2개 matroid의 intersection을 구하는 문제로 환원될 수 없고, NP-hard임이 알려져 있다.

### 6-1. Computing Matroid Intersection
Maximal weight independent set problem에서와 마찬가지로 초기에 $X=\phi$로 잡고 $X$의 independentness를 유지하면서 크기를 키워나가는 방법을 사용한다:

먼저 다음을 정의한다.
1.  $S$ 위의 방향 그래프 $D_{M_i}(X): x\rightarrow y$ iff $y\in S-X$ and $X-x+y\in I_i$ 
2. $D_{M_1,M_2}(X) = D_{M_1}(X)\cup reversed(D_{M_2}(X))$
3. $X_i=\\{y \in S-X: X+y\in I_i\\}$

즉 $D_{M_1,M_2}(X)$는 $X$의 원소를 exchange하는 과정을 그래프로 표현한 것이라 보면 된다. 이제 $D_{M_1,M_2}(X)$의 $X_1$에서 $X_2$로의 shortest path $P$를 찾는다. $X:= (X-P)\cup(P-X)$로 두면 $X$의 independentness가 유지되면서 크기가 1만큼 커진다. 이러한 $P$가 존재하지 않을 때까지 이를 반복한다. 그러면 $X$가 문제의 답이 되고 알고리즘을 중단한다.

### 6-2. Examples
1. Arborescence(Directed MST): graphic matroid와 partition matroid (edge의 color를 끝점으로 둔다) 와의 intersection으로 해결할 수 있다.
2. Bipartite Matching: 두 partition matroid (edge의 color를 각각 왼쪽 끝점, 오른쪽 끝점으로 둔다)의 intersection으로 해결할 수 있다.

## 7. References
1. <https://en.wikipedia.org/wiki/Matroid> 
2. <https://infossm.github.io/blog/2019/05/15/introduction-to-matroid/>
3. <https://infossm.github.io/blog/2019/06/17/Matroid-Intersection/>
