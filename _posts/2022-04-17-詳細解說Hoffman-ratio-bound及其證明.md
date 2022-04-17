---
title: 詳細解說 Hoffman ratio bound 及其證明
categories: essay
date: 2022-04-17 17:00:00 +0800
authors: 李翊誠
spicy: 3
---

<style>
    div.theorem{
        background-color:rgb(230, 230, 230);
        border:  2px solid rgb(100, 100, 100);
        border-radius: 6px;
    }
    p.innerText{
        margin-left: 40px;
        background-color: rgb(230, 230, 0);
    }
</style>

## 前言與定理敘述

在譜圖論（spectral graph theory）中，有一個描述連結圖獨立數和相鄰矩陣最小特徵值之間的不等式 &mdash; Hoffman ratio bound，或稱 Hoffman&ndash;Delsarte inequality：

<div class="theorem">
<p>
&emsp;&emsp;Suppose that $G$ is a $k$-regular graph, then
</p>
    
<div>\[
    \alpha(G) \leq \frac{n}{1-\frac{k}{\lambda_n}}.
\]</div>  
</div>

其中有許多符號及定義，我們先一一解釋：

* $$\alpha(G)$$，在圖 $$G$$ 之中最大的獨立集（[independent set](https://zh.wikipedia.org/wiki/%E7%8B%AC%E7%AB%8B%E9%9B%86)）的大小。何謂獨立集？是指在 $$G$$ 的點集合中的一子集合，且任兩個在該子集合的元素在圖中不相連。
* 我們定義 $$\lambda_1 \geq \lambda_2 \geq \dots \geq \lambda_n$$ 為 $$G$$ 所表示的鄰接矩陣（[adjacency matrix](https://en.wikipedia.org/wiki/Adjacency_matrix)）的特徵值，其中 $$\lambda_n$$ 為其最小的特徵值。
* regular graph，指的是該圖之中的每個點都有相同的度數，$$k$$--regular graph 尤指每個點的度數都為 $$k$$。

尋找獨立集的大小在圖論之中是其中一個重要的課題，但要求出它的精確值是一個 NP-問題。然而、我們可以使用一些不等式將其壓在特定數值之下，而 Hoffman ratio bound 就是其中一個方式。

---

## 證明

首先我們先定義：

- $$J_n$$ 為 $$n\times n$$ 的全 $$1$$ 矩陣，
- $$\lambda_n$$ 為 $$A$$ 最小的特徵值。

我們寫兩個矩陣：

<div>\[
    A,\quad \frac{k-\lambda_n}{n}J_n.
\]</div>

注意這邊 $$A$$ 和 $$J_n$$ 各自都可以對角化，且 $$AJ_n = J_nA$$ 則存在一可逆矩陣 $$S$$ 使得 $$S^{-1}AS$$ 和 $$S^{-1}J_nS$$ 均為對角矩陣，也就是說 $$A$$ 和 $$J_n$$ 有相同的特徵向量集，我們稱 $$A$$ 和 $$J_n$$ 可同時對角化（[simultaneously diagonalizable](https://en.wikipedia.org/wiki/Diagonalizable_matrix#Simultaneous_diagonalization)）。接著我們令相同的特徵向量集為 $$V$$，任何 $$V$$ 中的特徵向量 $$\bv$$ 也是 矩陣 $$A-J_n$$ 的特徵向量，因為：

<div>\[
    (A-J_n)\bv = A\bv - J_n\bv = \lambda_A\bv - \lambda_{J_n}\bv = (\lambda_A - \lambda_{J_n})\bv.
\]</div>

其中，$$\lambda_A$$ 代表 $$A$$ 的某一個特徵值、$$\lambda_{J_n}$$ 代表 $$J_n$$ 的某一個特徵值，也就是說我們可以透過相減一些 $$A$$ 的特徵值與 $$J_n$$ 來得到新的矩陣 $$(A-J_n)$$ 的特徵值。  

但我們怎麼知道哪一個特徵值對應到哪個特徵值呢？

我們知道全為 $$1$$ 的矩陣 $$J_n$$ 的特徵值只有兩個 $$n$$、$$0$$，重數分別為 $$1$$ 和 $$n-1$$，而矩陣 $$\frac{k-\lambda_n}{n}J_n$$ 的特徵值則為 $$k-\lambda_n$$ 和 $$0$$。這部份可以由全一向量 $$\bone$$ 看出來，因為 

<div>\[
    A\bone = k\bone,\quad \frac{k-\lambda_n}{n}J_n\bone=(k-\lambda_n)\bone.
\]</div>

所以 $$A$$ 之中特徵值 $$k$$ 對應到的是 $$\frac{k-\lambda_n}{n}J_n$$ 之中的 $$(k-\lambda_n)$$，其餘的特徵值對應到的都是 $$0$$，因此我們可以重組出新矩陣的全部特徵值，令 $$A$$ 的特徵值為 $$\lambda_1 = k,\lambda_2,\dots,\lambda_n$$ 且 $$\lambda_n$$ 為最小的特徵值，則

<div>\[
    \begin{aligned}
    \spec(A - \frac{k-\lambda_n}{n}J_n) &= \{\lambda_1-(k-\lambda_n),\lambda_2-0,\lambda_3-0,\dots,\lambda_n-0\}\\
    &=\{k-k+\lambda_n, \lambda_2,\dots, \lambda_n\}\\
    &=\{\lambda_n, \lambda_2,\dots, \lambda_n\}
    \end{aligned}
\]</div>

之中最小的特徵值確定為 $$\lambda_n$$。
接著我們定義矩陣  

<div>\[
    E = A - \frac{k-\lambda_n}{n}J_n - \lambda_nI_n.
\]</div>

這麼做可以將所以特徵值統一減去 $$\lambda_n$$，保證了 $$E$$ 必為半正定（positive semi-definite）。
給定原圖 $$G$$ 之中最大的獨立集 $$S$$，$$S$$ 的大小為 $$\alpha$$。並在 $$E$$ 之中單獨取出第對應到 $$S$$ 中元素的那些行列所形成的子矩陣 $$E_S$$，其為矩陣 $$E$$ 的一個主子矩陣（principal submatrix）。由於 $$S$$ 為一個獨立集，$$A$$ 在這部份均為零，所以

<div>\[
    E_S = -\frac{k-\lambda_n}{n}J_\alpha - \lambda_n I_\alpha.
\]</div> 

如下舉例：  

<div>\[
    \text{If } E =\begin{bmatrix}
    2 & 4 & 1 & 3 & 0\\
    4 & 6 & 2 & 1 & 2\\
    1 & 2 & 7 & 3 & 0\\
    3 & 1 & 3 & 9 & 3\\
    0 & 2 & 0 & 3 & 2\\
    \end{bmatrix}
    ,\text{then  }
    E_{\{2,4,5\}}=\begin{bmatrix}
    6 & 1 & 2\\
    1 & 9 & 3\\
    2 & 3 & 2\\
    \end{bmatrix}.
\]</div>

而一個半正定矩陣的主子矩陣也會是半正定，不過現在的 $$E_S$$ 僅由 $$J_\alpha$$ 和 $$I_\alpha$$ 組成，我們能夠直接推導出他的特徵值為


<div>\[
    \begin{aligned}
    \spec(E_S) &= \spec(-\frac{k-\lambda_n}{n}J_\alpha - \lambda_n I_\alpha) \\
    &= \{-\alpha\frac{k-\lambda_n}{n}-\lambda_n,-\lambda_n^{(\alpha-1)}\}.
    \end{aligned}
\]</div>

且半正定矩陣的所有特徵值均大於等於零，因此

<div>\[
    -\alpha\frac{k-\lambda_n}{n}-\lambda_n\ge0.
\]</div>

而經過計算後可得  

<div>\[
    \alpha \le \frac{n}{1-\frac{k}{\lambda_n}}.
\]</div>

到此我們就證明完了 Hoffman ratio bound。

---

## 補充

我們在這邊補充一個小知識：

<div class="theorem" style="text-align: center;">
<p>
    &emsp;&emsp;While $G$ is a $k$-regular graph, then $\lambda_1 = k$.
</p>
</div>

其中提醒一下 $$\lambda_1$$ ，是指 $$G$$ 所表示的鄰接矩陣（adjacency matrix）的最大特徵值。


我麼先說明這個背景小知識，令：

* $$A$$ 為圖 $$G$$ 的鄰接矩陣。
* $$\bx$$ 為 $$A$$ 的一特徵向量，且 $$\bx$$ 所對應的特徵值為 $$\lambda_1$$。
* $$x_j$$ 為 $$\bx$$ 之中絕對值最大的元素，即 <span markdown=0>$x_j = \max_{i=0}^{n}|x_i|$</span>。


我們可以透過以下不等式來說明：

<div>\[
    |\lambda_1||x_j| = |(A\bx)_j| = \left|\sum_{i, v_i\in N(v_j)} x_i\right| \leq \deg(v_j)|x_j| = k |x_j|
\]</div>
其中 $$N(v_j)$$ 代表點 $$v_j$$ 的鄰居，$$\deg(v_j)$$ 代表點 $$v_j$$ 的度數。

1. 第一個等於只是簡單地單看 $$A\bx$$ 的第 $$j$$ 項，也就是單獨將 $$A$$ 的第 $$j$$ 列與 $$\bx$$ 內積相乘。
2. 而 $$A$$ 作為一圖的鄰接矩陣，其中不是 $$0$$ 就是 $$1$$、第 $$j$$ 列中為 $$1$$ 的位址代表的即是圖 $$G$$ 中與 $$v_j$$ 相連的點，因而得到第二個等號。
3. 因此將會有 $$\deg(v_j)$$ 個元素相加，但我們已令 $$x_j$$ 為 $$\bx$$ 之中絕對值最大的元素，所以得到中間的不等式。
4. 同時 $$\deg(v_j)$$ 就是 $$k$$，因此我們就有了以上的不等式。

以上幾點說明了 <span markdown=0>$|\lambda_1| \le k$</span>，但實際上，我們可以說 $$\lambda_1 = k$$，因為確實存在一特徵向量，也就是全一向量 $$\bone$$，使得 $$A\bone = k\bone$$，而其對應的特徵值剛好就是 $$k$$。

因此我們可以將 Hoffman ratio bound 的定理敘述改為：

<div class="theorem">
<p>
&emsp;&emsp;Suppose that $G$ is a $k$-regular graph, then
</p>
    
<div>\[
    \alpha(G) \leq \frac{n}{1-\frac{\lambda_1}{\lambda_n}}.
\]</div>  
</div>

