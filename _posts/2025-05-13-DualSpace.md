---
title: Dual Space
date: 2025-05-13 23:00:00 +0900
categories: [Algebra, Linear Algebra]
tags: [Linear Algebra, Functional Analysis, Dual Space, Hilbert Space, Banach Space]
author: ksa23027
math: true
---

## 0. Introduction
수학에서 어떤 구조를 다루고자 할 때 그 대상(object) 뿐만 아니라 그들 사이의 함수(morphism)를 보는 것, 나아가 함수들을 모아놓은 새로운 공간을 정의하는 것이 유용하다는 것은 경험적으로 잘 알려진 사실이다. 예를 들어 푸리에 해석학에서는 함수들의 벡터공간과 그것의 정규직교기저를 잡아 주어진 함수를 기저 함수들의 선형결합으로 표현하고 이를 통해 여러 유용한 결과를 이끌어낸다. 

이 글에서는 주어진 벡터공간 $V$에 대해 $V$ 위에서 정의된 선형범함수(linear functional)들의 공간인 $V^* $가 갖는 성질을 정리하고 이를 직관적으로 이해하는 설명들을 제공할 것이다. $V$가 무한차원일 때, 내적 공간일 때, Banach space일 때 등 다양한 경우에 대해 성질이 어떻게 달라지고 추가되는지를 최대한 체계적으로 정리하고자 한다.
## 1. Definition
- 체 $F$위의 벡터공간 $V,W$에 대해 $L(V,W)$는 $V$에서 $W$로 가는 선형함수들의 벡터공간으로, 덧셈은 $(f+g)(v)=f(v)+g(v)$으로, 스칼라곱은 $(cf)(v)=cf(v)$으로 정의된다.
- $V^*  =L(V,F)$로 정의하고, $V$의 쌍대공간(dual space)이라 한다. 쌍대공간의 원소는 dual vector, covector, 1-form 등으로 부른다.

예를 들어 $V=\mathbb{R}^2$ 일 때 $V^* $는 $f:\mathbb{R}^2\rightarrow\mathbb{R}$ 들의 공간이 된다. 이때 $f$가 선형이므로 $f(x,y)=ax+by$ 꼴로 표현될 것이다. 따라서 $V^{* } $의 원소는 $a,b$에 의해 결정되므로 $V^* $ 역시 $V$와 마찬가지로 2차원 공간이 된다.

항상 $V$와 $V^* $가 이와 같이 isomorphic할까? 그 해답을 다음 장부터 알아보자.
## 2. Dual Basis
$V^* $의 구조를 분석하려면 당연히 그것의 기저를 찾아야 할 것이다. 앞 장의 예시에서 $V^* $의 원소 $f$는 $ax+by$ 꼴로 표현되었고, 따라서 여기선 $x':(x,y)\mapsto x,y':(x,y)\mapsto y$ 라는 함수들이 기저가 된다($(a,b)=(1,0),(0,1)$을 대입해보면 쉽게 이해된다). 이 두 함수는 벡터를 받아 좌표의 특정 성분을 내놓는 함수들이다. 일반적인 $V$에 대해서도 $V^* $의 기저를 마찬가지 방법으로 구성하고자 한다.

$V$의 기저 $B=\\{ e_i\\}$가 주어졌을 때 $V^* $의 subset $B^* =\\{e^i\\}$ where $e^i(e_j)=\delta_{ij}$ 를 $B$의 쌍대기저(dual basis)라고 한다. $B^* $가 linearly independent인 것은 정의를 통해 쉽게 확인 가능하지만, 실제로 $V^* $의 기저가 되는지는 아직 불분명하다. 

$\dim V=n<\infty$일 때는 $V^* $의 원소를 $1\times n$ 행렬로 표현할 수 있으므로 $V^* $도 $n$차원이 되고, 따라서 $B^* $는 linearly independent set of size $n$이므로 $V^* $의 기저가 된다. 그러나 $V$가 무한차원일 때는 이것이 성립하지 않는다.

다만 무한차원 케이스에 대해서도 우리는 dual basis를 통해 $V\rightarrow V^* $로의 injective map $e_i\mapsto e^i$을 구성할 수 있다. 따라서 $\dim V^*  \ge \dim V$가 성립함을 알 수 있다. 사실 $V$가 무한차원이면 항상 $\dim V^*  > \dim V$가 성립하지만 이 글에선 증명하지 않을 것이다.
## 3. Identifications of $V$ and $V^* $
$V$가 유한차원일 때 $V$와 $V^* $이 isomorphic하다는 것을 직관적으로 이해하는 방법들로는 다음과 같은 것들이 있다:
1. 좌표와 좌표함수들의 identification: "벡터의 $i$번째 성분"과 "벡터를 받아 i번째 성분을 내놓는 함수"는 거의 같은 것으로 취급할 수 있다. 이것이 dual basis의 구성에 직접적으로 활용되었다.
2. $1\times n$ 행렬과 $n\times 1$ 행렬의 identification: Dual vector는 $1\times n$ 행렬로 나타낼 수 있고 이는 $90^\circ$ 돌려서 $V$의 원소인 $n\times 1$ 행렬과 같게 볼 수 있다. Dual basis 개념도 이것과 호환된다: Dual basis는 행렬로 나타내면 $[0,\cdots,0,1,0,\cdots,0]$이 된다. 앞에서 $\dim V^*  =n$를 증명할 때 이를 사용하였다.

$V$에 내적까지 주어졌을 때는 다음과 같은 이해도 가능하다:

3\. 고정된 벡터와의 내적과 선형범함수의 identification: 내적공간에서는 고정된 벡터 $v$에 대해 $w\mapsto (v,w)$가 선형범함수가 된다. 반대로 Riesz Representation Theorem에 의하면 모든 선형범함수를 이와 같이 내적으로 표현할 수 있다. 따라서 $V^* $의 원소인 선형범함수 하나가 $V$의 원소인 $v$와 일대일로 대응되게 된다. 

마지막 설명은 앞서 본 dual basis 개념과도 호환시킬 수 있는데, 주어진 $V$의 기저가 정규직교기저가 되도록 내적을 잡으면 된다("정규직교기저에선 좌표를 내적으로 구한다" 아이디어가 쓰인 것이다). 또 2번째 identification과도 호환되는데 이는 $(v,w)=v^T w$ 가 성립하기 때문이다.

즉 지금 이야기한 모든 identification이 사실 같은 것을 여러 방식으로 표현하고 있는 것이다.
## 4. In Hilbert Space
$V$가 무한차원일 때는 앞에서 설명했듯이 $V^* $가 $V$와 isomorphic하지 않다는 문제점이 있었다. 게다가 Hilbert space들끼리의 linear map은 continuous인 것과 bounded인 것이 동치이다. 따라서 우리는 $V$가 Hilbert space일 때에는 모든 linear functional을 생각하는 대신 bounded linear functional들만을 생각할 것이다. 이제 이 함수공간을 (analytical) dual space $V^* $라고 부르고, 원래 우리가 알던 $V^* $는 algebraic dual space라고 하자.

이렇게 새롭게 정의한 $V^* $가 $V$와 isomorphic한지 묻는 것이 자연스러운 질문일 것이다. 답은 Yes이며, 증명은 Riesz Representation Theorem이 Hilbert space 위에서 정의된 bounded linear functional에 대해서도 성립함을 보인 후 3번째 identification을 사용하면 된다.
## 5. In Banach Space
$V$가 Banach space일 때에도 $V^* $의 정의는 Hilbert space 케이스와 마찬가지로 bounded linear functional만을 고려한다. 그러나 $V$가 Hilbert가 아니면 3번째 identification을 쓸 수 없기에 $V\cong V^* $ 라고 말할 수 없다. 다만 앞서 정의한 dual basis를 통한 injective map $V\rightarrow V^* $이 norm을 보존한다는 것을 쉽게 확인할 수 있으므로 $V$는 Banach space로서 $V^* $에 imbedding된다는 것은 알 수 있다. 

Dual space of a Banach space의 대표적인 예시로는

$$(l^p)^* \cong l^q, (L^p)^*  \cong L^q$$

for $1/p+1/q=1, 1\le p<\infty$가 있다. $p=q=2$를 대입하면 $l^p,L^p$는 Hilbert space가 되고 따라서 위 식은 Hilbert space $V$에 대해 $V\cong V^* $라는 사실의 예시도 된다. 증명은 횔더 부등식과 Radon-Nikodym Theorem을 이용하면 되는데 자세한 증명은 여기서 하지 않는다.
## 6. Double Dual
지금까지 $V$와 $V^* $를 비교할 때는 basis가 꼭 필요했지만 $V$와 $V^{**  }=(V^*  )^* $를 비교할 때는 그렇지 않다. $V$에서 $V^{**  }$로의 injective map을 다음과 같이 잡을 수 있기 때문이다: 

$$v\mapsto (\phi_v:f\mapsto f(v))$$

여기서 $\phi_v$를 evaluation map이라 한다. 풀어서 설명하면 $\phi_v$는 $V^* $의 원소 $f$를 입력받아 $f(v)\in F$를 내뱉는, 즉 $v$를 대입하는 선형범함수이기 때문에 $V^{**  }$의 원소가되고, 각 $v$마다 이러한 $\phi_v$가 하나씩 존재하므로 이 대응은 $V\rightarrow V^{**  }$로의 mappping이 된다. 

Evaluation map을 직관적으로 이해하려면 $f(v)$ 대신 $(f, v)$라는 이변수함수 노테이션을 써보면 된다. 이변수함수에서 변수 하나를 고정하면 나머지 변수에 대한 함수가 만들어진다(함수형 프로그래밍에서의 currying 개념). 여기서 $f$를 고정하면 이는 $v$를 입력받는 함수, 즉 $V^* $의 원소가 된다. 반대로 $v$를 고정하면 이는 $f$를 입력받는 함수, 즉 $V^{**  }$의 원소가 된다. 그래서 $v$ 하나당 $V^{**  }$의 원소 하나가 대응되는 것이다. 이러한 사고방식을 Natural Pairing이라 한다.

$V$가 유한차원인 경우 $V$와 $V^{**  }$가 위 mapping에 의해 isomorphic하다는 것은 쉽게 보일 수 있다. 

$V$가 Banach space일 때 $\phi_v$는 항상 bounded linear functional이 되고 위 mapping은 norm을 보존한다. 따라서 $V$는 Banach space로서 자기자신의 analytical dual space로 imbedding된다. 하지만 $V\cong V^{**  }$가 항상 성립하는건 아니고, 그게 성립하는 공간을 reflexive하다고 한다.
## 7. References
1. 2025-1 KSA 수학특강(심화선형대수학) 수업
2. Steven Roman - Advanced Linear Algebra
3. E. M. Stein & R. Shakarchi - Real Analysis
4. <https://en.wikipedia.org/wiki/Dual_basis>
