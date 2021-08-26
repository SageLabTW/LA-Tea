---
title: 風格指引
---

## 基本原則

### B01: 句子必須完整。

每一個文字或數學式都必須落在某一個完整的句子裡，同時句子必須有適當的標點符號。  
:x: $x^2 + 2x + 3$, $2^2 - 4 \cdot 1 \cdot 3 < 0$, 無解  
:ok: 考慮方程式 $x^2 + 2x + 3 = 0$，因其判別式 $2^2 - 4 \cdot 1 \cdot 3 < 0$，所以無解。  

### B02: 數學應該在數學模式裡。

只要是數學式，就算是一個字母的變數、單一一個數字，都應該放在數學模式裡。  
:x:  考慮 x 為 1 的時候  
:ok: 考慮 $x$ 為 $1$ 的時候  

### B03: 避免使用數學符號來取代邏輯敘述。

正式寫作裡幾乎不會出現以下符號：$\forall, \exist, \therefore, \because, \implies, \iff, \ni$。  
這些符號通常是為了上課及討論時的方便，不會用在正式寫作裡，甚至有些不是世界通用的符號。  
:x:  $\forall  \epsilon > 0, \exist \delta > 0 \ni \forall |x - x_0| < \delta \implies |f(x) - f(x_0)| < \epsilon$  
:ok: 對於任何的 $\epsilon > 0$ 都存在一個 $\delta > 0$，使得任意符合 $|x - x_0| < \delta$ 的 $x$ 都滿足 $|f(x) - f(x_0)| < \epsilon$。  

## LA Tea 風格建議

### S01: 中英轉換空格

中文和英數字相鄰的時候加入一個半形空格，英數字和全形標點相鄰時則不用。

:x: 令$f$為一函數，$f'$為其導函數。  
:ok: 令 $f$ 為一函數，$f'$ 為其導函數。

> 漢學家稱這個空白字元為「盤古之白」，因為它劈開了全形字和半形字之間的混沌。另有研究顯示，打字的時候不喜歡在中文和英文之間加空格的人，感情路都走得很辛苦，有七成的比例會在 34 歲的時候跟自己不愛的人結婚，而其餘三成的人最後只能把遺產留給自己的貓。畢竟愛情跟書寫都需要適時地留白。 ---[vinta/pangu.js](https://github.com/vinta/pangu.js)

### S02: 中文使用全形標點，必要時數學模式裡可以使用半形。

:x: 考慮兩個向量 $\bx,\by$, 則其內積為 $\by\trans\bx$.  
:ok: 考慮兩個向量 $\bx,\by$，則其內積為 $\by\trans\bx$。  
:ok: 考慮兩個向量 $\bx$ 及 $\by$，則其內積為 $\by\trans\bx$。  


## Markdown

```md
在文章中可以適時加入不同的文字格式，像是**粗體**、_斜體_、或是以

- 條列形式呈現。
- 可以參考 [CommonMark: Markdown Reference](https://commonmark.org/help/)。
```

在文章中可以適時加入不同的文字格式，像是**粗體**、_斜體_、或是以

- 條列形式呈現。
- 可以參考 [CommonMark: Markdown Reference](https://commonmark.org/help/)。

另外注意在 Markdown 語法中，必須要在每行結尾留下**兩個半形空格**才能強制換行。
或者留**一個空白行**來開啟新的段落。


## LaTeX

利用 `$...$` 來進入隨文數式，利用 空白行 + `$$...$$` + 空白行 來進入展示數式。

```latex
當 $x$ 為一實變數時，方程式

$$x^2 + 2x + 3 = 0$$

無解。
```

當 $x$ 為一實變數時，方程式

$$x^2 + 2x + 3 = 0$$

無解。

---

LA Tea 網站目前使用 KaTeX 來做數學排版，可以到 [KaTeX: Supported Functions](https://katex.org/docs/supported.html) 查看所有支援的數學符號。

為了線性代數寫作方便，LA Tea 網站額外定義了一些常用的符號（macro）。
在任一個頁面點右鍵查看網頁原始碼，搜尋 `newcommand` 會看到一整區塊的新指令定義。  

| 名稱 | 原始碼 | 排版結果 | 附註 |
|---:|---|---|---|
| 轉置 | `A\trans` | $A\trans$ | |
| 內積 | `\inp{\bx}{\by}` | $\inp{\bx}{\by}$ | |
| 互斥聯集 | `\dunion` | $\dunion$ | |
| 向量 | `\bzero, \bone, \bx` | $\bzero, \bone, \bx$ | 還有 $\ba\bb\bp\bq\by\bu\bv\bw$ |

函數系列

| 名稱 | 原始碼 | 排版結果 | 附註 |
|---:|---|---|---|
| 生成 | `\span(S)` | $\span(S)$ | |
| 核數 | `\nul(A)` | $\nul(A)$ | |
| 秩 | `\rank(A)` | $\rank(A)$ | |
| 核 | `\ker(A)` | $\ker(A)$ | $\LaTeX$ 內建|
| 值域 | `\range(A)` | $\range(A)$ | |
| 行空間 | `\Col(A)` | $\Col(A)$ | |
| 列空間 | `\Row(A)` | $\Row(A)$ | |
| 特徵值 | `\spec(A)` | $\spec(A)$ | |

以下是一些例子：

**上下標、分數、根號**

```latex
當 $x_0 = \frac{1}{\sqrt{2}}$ 時，$x_0^2 = \frac{1}{2}$。
```

當 $x_0 = \frac{1}{\sqrt{2}}$ 時，$x_0^2 = \frac{1}{2}$。

---

**乘號、集合**

```latex
若 $A$ 是一個 $m\times n$ 矩陣，則

$$\{\bx \in \mathbb{R}^n \mid A\bx = \bzero\}$$

是一個 $\mathbb{R}^n$ 中的線性子空間。
```

若 $A$ 是一個 $m\times n$ 矩陣，則

$$\{\bx \in \mathbb{R}^n \mid A\bx = \bzero\}$$

是一個 $\mathbb{R}^n$ 中的線性子空間。

---

**依條件定義函數**

```latex
$$f(x) = \begin{cases}
 1 & \text{if }x\in\mathbb{Q}, \\
 0 & \text{otherwise}.
\end{cases}$$
```

$$f(x) = \begin{cases}
 1 & \text{if }x\in\mathbb{Q}, \\
 0 & \text{otherwise}.
\end{cases}$$

---

**方程式、矩陣**

```latex
方程式

$$\begin{aligned}
 x + 2y &= 3 \\
 4x + 5y &= 6
\end{aligned}$$

可以改寫成 $A\bx = \bb$，其中

$$A = \begin{bmatrix}
 1 & 2 \\
 4 & 5
\end{bmatrix},
b = \begin{bmatrix} 3 \\ 6 \end{bmatrix}.$$
```

方程式

$$\begin{aligned}
 x + 2y &= 3 \\
 4x + 5y &= 6
\end{aligned}$$

可以改寫成 $A\bx = \bb$，其中

$$A = \begin{bmatrix}
 1 & 2 \\
 4 & 5
\end{bmatrix},
b = \begin{bmatrix} 3 \\ 6 \end{bmatrix}.$$

---

**增廣矩陣**

```latex
上述方程的增廣矩陣可以寫成

$$\left[\begin{array}{cc|c}
 1 & 2 & 3 \\
 4 & 5 & 6
\end{array}\right].$$
```

上述方程的增廣矩陣可以寫成

$$\left[\begin{array}{cc|c}
 1 & 2 & 3 \\
 4 & 5 & 6
\end{array}\right].$$








