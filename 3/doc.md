---
marp: true
theme: default
header: 'ゼミ 石川健太郎 2024/07/22'
footer: 'The Triads Geometric Consistency Index in AHP-Pairwise Comparison Matrices'
paginate: true
size: 16:9
style: |
    /* @theme beam */
    /* Author: rnd195 https://github.com/rnd195/ */
    /* beam license - GNU GPLv3 https://github.com/rnd195/my-marp-themes/blob/live/LICENSE_beam */
    /* License of beamer which inspired this theme - GNU GPLv2 https://github.com/rnd195/my-marp-themes/blob/live/LICENSE_GPLv2 */

    @import "default";

    :root {
        font-family: "CMU Sans Serif", "Segoe UI", Helvetica, sans-serif;
        --main: #1f38c5;
        --secondary: #141414;
    }

    section {
        background-color: #ffffff;
        /* bottom two-coloured bar in base64 svg */
        background-image:
            url(data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVVRGLTgiPz4KPHN2ZyB3aWR0aD0iMjUwbW0iIGhlaWdodD0iNS4zNTQ2bW0iIHZlcnNpb249IjEuMSIgdmlld0JveD0iMCAwIDI1MCA1LjM1NDYiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyI+CjxnIHRyYW5zZm9ybT0idHJhbnNsYXRlKC0yMC4zNDcgLTkxLjAyOCkiPgo8cmVjdCB4PSIyMC4zNDciIHk9IjkxLjAyOCIgd2lkdGg9IjEyNSIgaGVpZ2h0PSI1LjM1NDYiIGZpbGw9IiMxNDE0MTQiIGZpbGwtcnVsZT0iZXZlbm9kZCIgc3Ryb2tlLXdpZHRoPSIwIi8+CjxwYXRoIGQ9Im0xNDUuMzUgOTMuNzA1di0yLjY3NzNoMTI1djUuMzU0NmgtMTI1eiIgZmlsbD0iIzFmMzhjNSIgc3Ryb2tlLXdpZHRoPSIwIi8+CjwvZz4KPC9zdmc+);
        background-repeat: no-repeat;
        background-position: center bottom;
        background-size: 150% 1em;
        padding: 2em;
    }

    header {
        font-size: 0.6em;
        /* this text-align is important */
        text-align: right;
        /* I don't like this absolute positioning, but it works */
        position: absolute;
        top: 96.2%;
        width: 100%;
        right: 0;
        left: -51%;
        color: white;
    }

    footer {
        font-size: 0.5em;
        position: absolute;
        /* this text-align is important */
        text-align: left;
        top: 96.2%;
        width: 100%;
        right: 0;
        left: 50.8%;
        color: white;
    }

    h1 {
        color: #141414;
        font-size: 1.4em;
    }

    h2,
    h3,
    h4,
    h5,
    h6 {
        color: #141414;
        font-size: 1.1em;
    }

    /* only apply to the first occurrence of h1 */
    h1:nth-of-type(1) {
        font-family: "CMU Bright", "Segoe UI Semibold";
        color: #ffffff;
        background-color: var(--main);
        border-top: 0.3em solid var(--main);
        padding: 0;
        position: absolute;
        top: 0;
        right: 0;
        width: 100%;
        height: 1.5em;
        text-indent: 0.5em;
    }

    code {
        background-color: rgba(100, 100, 100, 0.2);
        font-size: 0.85em;
    }

    mark {
        background-color: #f5db7e;
    }

    /* formatting page numbers  */
    section::after {
        font-size: 0.5em;
        /* https://github.com/yhatt/marp/issues/263 */
        content: attr(data-marpit-pagination) " / " attr(data-marpit-pagination-total);
        position: absolute;
        text-align: right;
        top: 96.2%;
        width: 100%;
        right: 0;
        left: -0.5em;
        color: white;
    }

    /* inline math was too large wrt text */
    .katex {
        font: normal 1em KaTeX_Main, "Times New Roman", serif
    }

    /* the "center" keyword centers the image - may break, careful */
    /* https://github.com/marp-team/marpit/issues/141#issuecomment-473204518 */
    img[alt~="center"] {
        display: block;
        margin: 0 auto;
    }

    /* || SECTION CLASS: title */
    /* title page - only to be used as for a single slide */
    /* <!-- _class: title --> */
    section.title>h1 {
        font-family: "CMU Bright", "Segoe UI Semibold";
        color: #ffffff;
        background-color: var(--main);
        border-radius: 25px;
        text-align: center;
        top: 25%;
        left: 0;
        right: 0;
        margin-left: auto;
        margin-right: auto;
        width: 80%;
        padding-bottom: 0.2em;
        height: auto;
    }

    /* remake this to be positioned with respect to h1 */
    section.title>p {
        position: relative;
        text-align: center;
        top: 35px;
    }

    /* || SECTION CLASS: tinytext */
    /* new class that makes p, ul, and blockquote text smaller */
    /* might be useful for the References slide, use <!-- _class: tinytext --> */
    section.tinytext>p,
    section.tinytext>ul,
    section.tinytext>blockquote {
        font-size: 0.7em;
    }

    table {
        font-size: 0.8em;
    }

    p {
        font-size: 0.9em;
    }

math: katex

---

<!-- _class: title -->

# The Triads Geometric Consistency Index <br> in AHP-Pairwise Comparison Matrices
<br><br>

Aguarón J, Escobar MT, Moreno-Jiménez JM, Turón A (2020)

---

# Introduction

PCM $A = (a_{ij})$ は次を満たすときに整合している. [4, 9]

$$
a_{ij} a_{jk} a_{ki} = 1, ~~ \forall i,j,k = 1, \dots, n
$$

PCM の整合性の多くは順位付けの手続き (重みの求め方) に依存している.
一方で, 整合性の定義に基づいて定義し, 特定の順位付け方法と結びついていない整合性指標も提案されている.

本論文では, 特定の順位付け方法と結びついておらず Geometric Consistency Index ($\mathrm{GCI}$) と値が一致する Triads Geometric Consistency Index ($\mathrm{T\text{-}GCI}$) を提案する.

---

# Introduction

## 論文の構成

2. 従来の整合性の概念
3. $\mathrm{T\text{-}GCI}$ の定義
4. $\mathrm{GCI}$ と $\mathrm{T\text{-}GCI}$ の関係とその証明
5. より長いサイクルで同様の整合性指標を定義しても
$\mathrm{T\text{-}GCI}$ と値が一致することの証明
    ($\mathrm{T\text{-}GCI}$ は $a_{ij}, a_{jk}, a_{ki}$ の長さ 3 のサイクルを考えている)

---

# Consistency in the Analytic Hierarchy Process

## 整合性指標の分類

PCM の整合性指標は以下の二つのグループに分類することができる.

1. 特定の順位付け方法と結びついているもの
2. triads に基づくもの (Saaty の与えた (完全) 整合の定義に基づくもの)

---

# Consistency in the Analytic Hierarchy Process

## $\mathrm{CI}, \mathrm{CR}$

固有値法では PCM $A = (a_{ij})$ から次のように重要度ベクトル $w = (w_i)$ を求める.

$$
\begin{align*}
A w & = \lambda_\mathrm{max} w \\
& \text{ with } ~~ w_i \geq 0, ~~ i = 1, \dots, n \\
& \text{ and } ~~ \sum_{i=1}^n w_i = 1
\end{align*}
$$

($\lambda_\mathrm{max}$ は PCM $A$ の最大固有値)

---

# Consistency in the Analytic Hierarchy Process

この順位付け方法に基づいて, 整合性指標 $\mathrm{CI}$ が定義される.

$$
\begin{align*}
\mathrm{CI}(A)
& = \frac{\lambda_\mathrm{max} - n}{n - 1} \\
& = \frac{1}{n(n-1)} \sum_{i \neq j}^n \left( a_{ij} \frac{w_j}{w_i} - 1 \right)
\qquad \left( \because \lambda_\mathrm{max} = \sum_{j = 1}^n a_{ij} \frac{w_j}{w_i} \right)
\end{align*} 
$$

$\lambda_\mathrm{max} = \sum_{j = 1}^n a_{ij} w_j / w_i$ は, $w$ が固有値法の重要度ベクトル ($A$ の最大固有値 $\lambda_\mathrm{max}$ に対応する固有ベクトル) であるときに成り立つ. 
$\mathrm{CI}$ は固有値法と結びついている.

同様に, $\mathrm{CR}(A) = \mathrm{CI}(A) / \mathrm{RI}(n)$ もまた固有値法と結びついている.

---

# Consistency in the Analytic Hierarchy Process

$$
\begin{align*}
\frac{1}{n(n-1)} \sum_{i \neq j} \left( a_{ij} \frac{w_j}{w_i} - 1 \right)
& = \frac{1}{n(n-1)} \left( -n^2 + \underset{= \sum_{i = j} a_{ij} w_j / w_i}{\underline{n}} + \sum_{i \neq j} a_{ij} \frac{w_j}{w_i} \right) \\
& = \frac{1}{n(n-1)} \left( -n^2 + \sum_{i = 1}^n \underset{= \lambda_\mathrm{max}}{\underline{\sum_{j = 1}^n a_{ij} \frac{w_j}{w_i}}} \right) \\
& = \frac{1}{n(n-1)} \left( -n^2 + \sum_{i=1}^n \lambda_\mathrm{max} \right) \\
& = \frac{\lambda_\mathrm{max} - n}{n - 1}
\end{align*}
$$

---

# Consistency in the Analytic Hierarchy Process

## $\mathrm{GCI}$

次のように行幾何平均法の重要度ベクトル $w = (w_i)$ を求める.

$$
w_i = \prod_{j=1}^n a_{ij}^\frac{1}{n}
$$

Geometric Consistency Index ($\mathrm{GCI}$) は次のように定義される.

$$
\mathrm{GCI}(A) = \frac{1}{(n-1)(n-2)} \sum_{i, j} \left( \log \left( a_{ij} \frac{w_j}{w_i} \right) \right)^2
$$

$\mathrm{GCI}$ は明らかに行幾何平均法と結びついている.

---

# Consistency in the Analytic Hierarchy Process

## Koczkodaj の整合性指標 [30]

次の triads に基づく整合性指標は特定の順位付け方法と結びついていない. [30]

$$
\mathrm{KI}(A) = \max_{i < j < k} \left\{ \min \left\{ \left| 1 - \frac{a_{ik}}{a_{ij} a_{jk}} \right|, \left| 1 - \frac{a_{ij} a_{jk}}{a_{ik}} \right| \right\} \right\}
$$

推移率の破れが最大の triads $a_{ij}, a_{jk}, a_{ki}$ に注目している.

次のように, $a_{ij}$ と $a_{ik} a_{kj}$ とのずれを $a_{ij}$ (比率尺度なので) で正規化したものを考えている.

$$
\begin{align*}
& \min \left\{ \frac{| a_{ij} - a_{ik} a_{kj} |}{a_{ij}}, \frac{| a_{ik} - a_{ij} a_{jk} |}{a_{ik}}, \frac{| a_{jk} - a_{ji} a_{ik} |}{a_{jk}} \right\} \\
= ~~ & \min \left\{ \frac{| a_{ij} a_{jk} - a_{ik}|}{a_{ij} a_{jk}}, \frac{| a_{ik} - a_{ij} a_{jk} |}{a_{ik}}, \frac{|a_{ij} a_{jk} - a_{ik}|}{a_{ij} a_{jk}} \right\} \\ 
= ~~ & \min \left\{ \left| 1 - \frac{a_{ik}}{a_{ij} a_{jk}} \right|, \left| 1 - \frac{a_{ij} a_{jk}}{a_{ik}} \right| \right\} \\
\end{align*}
$$


---

# Consistency in the Analytic Hierarchy Process

## Palaez と Lamata の整合性指標 [31]

次の triads に基づく整合性指標は特定の順位付け方法と結びついていない. [31]

$$
\mathrm{PLI}(A) = \sum_{i < j < k} \left( \frac{a_{ik}}{a_{ij} a_{jk}} + \frac{a_{ij} a_{jk}}{a_{ik}} - 2 \right) / 
\begin{pmatrix} n \\ 3 \end{pmatrix}
$$
