---
title: Graph Problems
date: 2025-05-11 23:00:00 +0900
categories: [Discrete Mathematics, Graph Theory]
tags: [Graph Theory, Max Flow Min Cut Theorem, Bipartite Matching, Linear Programming]
author: 23-027 Junghwan Kim
math: true
---

## 0. Introduction
많은 알고리즘 문제들은 그래프 문제로 환원해서 풀 수 있다. 왜냐하면 그래프는 $E\subseteq V^2$ 라는 아주 일반적인 조건으로 정의되기 때문이다. 하지만 $V,E$를 점과 선으로 시각화함으로써 path, cycle, spanning tree, flow, matching, cover, coloring, planarity 등 수많은 기하학적/위상적 개념들이 만들어질 수 있었고, 이것이 그래프 이론의 유용한 정리들로 이어진다.

그래프의 이러한 위상적 성질을 다루는 방법에는 matroid와 같은 상위 개념을 이용하는 것도 있지만 이 글에서는 순수하게 그래프 안에서만 내용을 전개할 것이다. 이 글에선 여러 그래프 문제들을 소개하고 이들 사이의 Duality Theorem들을 알아볼 것이다.

Notation: (무방향 or 방향) 그래프에서 vertex set은 $V$로, edge set은 $E$로, 각각의 edge는 $x\rightarrow y$ 또는 $xy$로 나타낸다($x,y\in V$). 

## 1. Vertex cover / Independent set
 - Vertex cover: $V_C\subseteq V$ is a vertex cover if for all $e\in E$ there is $v\in V_C$ s.t. $vw\in E$ for some $w\in V$. 즉 모든 edge가 적어도 한 vertex를 포함한다.
 - Independent set: $V_I\subseteq V$ is an independent set if there is no $v,w\in V_I$ s.t. $vw\in E$. 즉 vertex들끼리 서로 인접하지 않는다.

Vertex cover는 집합이 커질수록 만족하기 쉽고, independent set은 집합이 작아질수록 만족하기 쉽다. 사실 $V_I$가 independent set일 필요충분조건은 $(V_I)^C$가 vertex cover인 것이다. 따라서 min vertex cover problem과 max independent set problem은 서로 동치이며, 둘 다 NP hard이다.

## 2. Edge cover / Matching (independent edge set)
- Edge cover: $E_C\subseteq E$ is an edge cover if for all $v\in V$ there is $e\in E_c$ s.t. $e=vw$ for some $w\in V$. 즉 모든 vertex가 적어도 한 edge에 포함된다.
- Matching (independent edge set): $M\subseteq E$ is a matching if there is no $e,f\in M$ s.t. $e=vw$ and $f=vx$ for some $v,w,x\in V$. 즉 vertex들이 1개 이하의 edge에 포함된다.

Edge cover는 집합이 커질수록 만족하기 쉽고 matching은 집합이 작아질수록 만족하기 쉽다. Matching에는 다음과 같은 perfectness 개념이 존재한다:
- Matchinig $M$ is perfect if: vertex들이 정확히 1개의 edge에 포함된다. 

정의에 의해 perfect matching은 항상 maximal matching이다.

Matching과 independent set은 line graph에 의해 완전히 일대일로 대응되진 않는다는 점에 주의해야 한다: $V$의 matching은 $L(V)$의 independent set과 대응되지만, $V$의 independent set은 $L(V)$의 matching과 대응되지 않는다.

일반적인 그래프에서 edge cover와 matching은 다항시간에 구할 수 있다.

## 3. Max Flow Problem
방향 그래프 $(V,E)$와 소스, 싱크 $s\in V, t\in V, s\ne t$ 그리고 용량 $c:E\rightarrow\mathbb{Z}_0^+$가 주어졌을 때 $s-t$ flow는 다음 조건을 만족하는 함수 $f:E\rightarrow \mathbb{Z}_0^+$를 말한다:
- $f(ws)=0, f(tw)=0, \sum_w f(wv) = \sum_w f(vw)$ for $v\ne s,t$. 

즉 $s$에는 outcoming flow만 있고, $t$에는 incoming flow만 있고, 나머지 노드에 대해선 incoming flow와 outcoming flow의 합이 같아야 한다(이를 유량의 보존 속성이라 부르자).

$f$의 value $\left\vert f\right\vert$는 $s$의 outcoming flow의 합으로 정의한다. Max flow problem은 value를 최대화하는 flow $f$를 찾는 것이다.

이 문제는 다음과 같은 그리디 전략으로 다항시간에 해결할 수 있다: Flow를 흘릴 수 있는 $s-t$ path (이를 augmenting path라 부른다)를 아무거나 찾아서 flow를 흘려보낸다. 이때 기존에 보냈던 flow를 제거하는 것은 역방향으로 flow를 흘리는 것과 같게 취급한다. 더 이상 augmenting path가 존재하지 않을 때까지 이를 반복한다.

이때 augmenting path를 어떻게 찾느냐에 따라 알고리즘이 달라진다.
- Ford-Fulkerson: DFS로 찾는다. 시간복잡도는 $O(Ef)$ 
- Edmond-Karp: BFS로 찾는다. 시간복잡도는 $O(\min(VE^2,Ef))$ 
- Dinic: BFS level graph를 만들고 level이 +1씩 증가하는 경로들을 DFS로 찾는다. 시간복잡도는 $O(\min(V^2E,Ef))$

## 4. Min Cut Problem
Flow에서와 마찬가지로 소스, 싱크, 용량이 주어졌을 때 $s-t$ cut은 $s\in S, t\in T$를 만족하는 $V$의 partition $C=(S,T)$를 말한다. 

이때 $C$의 capacity $\left\vert C\right\vert$는 $\sum_{v\in S, w\in T} c(vw)$로 정의한다. $s-t$ min cut problem은 capacity를 최대화하는 $s-t$ cut $C$를 찾는 것을 말한다.

## 5. Max Flow Min Cut Theorem
$s-t$ min cut problem은 다음의 Max Flow Min Cut Theorem을 이용하여 max flow problem으로 환원하여 다항시간에 구할 수 있다:

$$\max_{f:\,s-t \text{ flow}} \left\vert f\right\vert = \min_{C:\,s-t\text{ cut}} \left\vert C\right\vert$$

증명을 위해 먼저 다음을 보인다:
- (Weak duality) $\max |f|\le \min |C|$. 

이는 유량의 보존 속성을 이용하면 쉽게 증명된다. 

이제 다음 세 조건이 동치임을 보이면 충분하다:
1. $|f|=|C|$ for some $s-t$ cut $C$
2. $f$ is a max $s-t$ flow
3. $f$ has no augmenting path

$1\rightarrow 2$는 weak duality에 의해 성립하고, $2\rightarrow 3$은 자명하다. $3\rightarrow 1$을 보이자. Augmenting path가 없는 flow $f$에 대해 $S$를 $s$에서 residual graph(flow가 흐를 수 있는 간선들만 생각한 그래프)에서 도달가능한 정점들의 집합으로 둔다. 그러면 augmenting path가 없기 때문에 $t\notin S$ 이고 따라서 $C=(S,V-S)$로 두면 이는 $s-t$ cut이 된다. $\left\vert C\right\vert=\left\vert f\right\vert$인 것은 $C$의 정의로부터 쉽게 증명된다.

## 6. Modeling Tips
주어진 문제를 max flow, min cut으로 모델링해서 풀 때 다음과 같은 팁들이 도움이 될 것이다:
- Flow는 유량의 보존 속성을 가지고 있기 때문에 뭔가를 '분배하는 문제' 혹은 '매칭 or 선택시키는 문제' 는 flow로 환원시키면 좋다. 예를 들어 밑에서 설명할 maximal bipartite matching problem 역시 flow로 환원해서 푼다.
- Min cut 모델링에서 $s$에 용량 $c$ 간선을 연결하는건 $t$에 용량 $-c$ 간선을 연결하는 것과 거의 같은 효과를 준다. 그래서 용량을 양수로 맞춰주기 위해 간선을 $s,t$중 하나에 연결하면 된다. 
- Min cut 모델링에서 간선의 용량을 $\infty$로 설정하면 그 간선을 통해 연결된 정점들이 항상 cut의 같은 쪽에 포함되도록 강제할 수 있다. 이 아이디어는 Hall's Theorem 증명에도 쓰인다.
- 정점이 간선의 역할을 하게끔 모델링하고 싶으면 정점을 들어오는 점과 나가는 점 2개로 쪼개고 그 둘을 간선으로 이으면 된다. 정점 분할이라고도 불리는 테크닉인데 아주 많이 쓰인다. 
- 주어진 목적함수 값이 Sum of profits - min cut capacity가 되도록 모델링하는 문제가 꽤 있으므로 유형을 익혀두면 좋다.

## 7. Bipartite matching
Bipartite graph $V=(L,R)$에서의 matching을 bipartite matching이라 한다. Maximal bipartite matching problem은 크기가 최대한 bipartite matching을 찾는 것이다. 이는 다음과 같이 maximum flow 문제로 환원하여 구할 수 있다:
- $V$에 가상의 소스와 싱크 $s,t$와 간선 $s\rightarrow l\in L, r\rightarrow t\in R$를 추가해서 새로운 그래프 $V'$을 만든다. 
- $V$에 원래 있던 간선에 대해서는 방향을 $L\rightarrow R$로 두고 용량을 $\infty$로 둔다. 
- 새로 추가한 간선의 용량은 1로 둔다. 
- 이제 $V$의 maximal bipartite matching의 크기는 $V'$의 maximum flow의 value와 같다. 

$V'$에서의 maximum flow를 Ford-Fulkerson Algorithm으로 구해주면 원래의 문제를 $O(VE)$ 시간복잡도에 풀 수 있다.

Bipartite matching에 대해서는 다음의 2가지 중요한 정리가 성립한다:
- (Kőnig's Theorem) Bipartite graph에서 $\max \left\vert M\right\vert = \min \left\vert V_C\right\vert$
- (Hall's Theorem) Bipartite graph (L,R)에서 perfect matching이 존재할 필요충분조건은 모든 $S\subseteq L$에 대해 $|S|\le |N(S)|$가 성립하는 것이다($N(S)$는 $S$와 인접한 vertex들의 집합).

Kőnig's Theorem을 이용하면 (일반적인 그래프에서와 달리) bipartite graph에서의 vertex cover와 independent set을 bipartite matching 문제로 환원하여 다항시간에 찾을 수 있다.

Hall's Theorem을 이용하면 maximal matching을 직접 구하지 않고도 perfect matching의 존재성을 판정할 수 있다.

## 8. Generalization
사실 지금까지 소개한 여러 그래프 문제들을 포함하는 general form이 있는데 바로 Linear Programming, 줄여서 LP 문제이다. LP 문제의 표준적인 형태는 다음과 같다:
- Maximize $\mathbf{b}^T \mathbf{x}$ where $A\mathbf{x}\le \mathbf{c}, \mathbf{x}\ge \mathbf{0}$

위 LP 문제의 dual problem을 다음과 같이 정의하자:
- Minimize $\mathbf{c}^T \mathbf{y}$ where $A^T \mathbf{y}\ge \mathbf{b}, \mathbf{y}\le \mathbf{0}$

그러면 다음의 LP duality가 성립한다:
- (Weak duality) $\max \mathbf{b}^T \mathbf{x}\le \min A^T \mathbf{y}$ 
- (Strong duality) $\max \mathbf{b}^T \mathbf{x}= \min A^T \mathbf{y}$ 

Max flow problem을 비롯한 많은 조합론적 최적화 문제를 LP 혹은 Integer Linear Programming으로 formulate할 수 있고 따라서 각 문제들에 대한 Duality Theorem들을 LP duality 하나로부터 유도할 수 있다. 앞서 설명한 Max Flow Min Cut Theorem과 Kőnig's Theorem 등이 대표적인 예시이다.

## 9. References
1. 2025-1 KSA 알고리즘 수업
2. <https://en.wikipedia.org/wiki/Independent_set_(graph_theory)>
3. <https://en.wikipedia.org/wiki/Edge_cover>
4. <https://en.wikipedia.org/wiki/Flow_network>
5. <https://en.wikipedia.org/wiki/Cut_(graph_theory)>
6. <https://en.wikipedia.org/wiki/Linear_programming>
