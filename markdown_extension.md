# markdown_extension

## 目录

<!-- TOC -->

- [markdown_extension](#markdown_extension)
    - [目录](#目录)
    - [1. matrix](#1-matrix)
        - [1.1 不带括号的矩阵](#11-不带括号的矩阵)
        - [1.2 带括号{}的矩阵](#12-带括号的矩阵)
        - [1.3 带括号[]的矩阵](#13-带括号的矩阵)
        - [1.4 不使用left和right关键词](#14-不使用left和right关键词)
        - [1.5 带省略号的矩阵](#15-带省略号的矩阵)
        - [1.6 带参数的矩阵](#16-带参数的矩阵)
        - [1.7 行间矩阵](#17-行间矩阵)
    - [2. LaTeX 公式](#2-latex-公式)
        - [2.1 上下标](#21-上下标)
        - [2.2 括号和分隔符](#22-括号和分隔符)
        - [2.3 分数](#23-分数)
        - [2.4 开方](#24-开方)
        - [2.5 省略号](#25-省略号)
        - [2.6 矢量](#26-矢量)
        - [2.7 积分](#27-积分)
        - [2.8 极限](#28-极限)
        - [2.9 累加和累乘](#29-累加和累乘)
        - [2.10 矩阵](#210-矩阵)
        - [2.11 希腊字母](#211-希腊字母)
        - [2.12 其他符号](#212-其他符号)
    - [参考：](#参考)
    - [更多资源](#更多资源)

<!-- /TOC -->

## 1. matrix

Markdown的语法与LaTeX的语法有诸多相似之处，这里使用 `$$\begin{matrix}…\end{matrix}$$` 来写矩阵。

### 1.1 不带括号的矩阵

```markdown
$$
  \begin{matrix}
   1 & 2 & 3 \\
   4 & 5 & 6 \\
   7 & 8 & 9
  \end{matrix}
$$
```

$$
  \begin{matrix}
   1 & 2 & 3 \\
   4 & 5 & 6 \\
   7 & 8 & 9
  \end{matrix}
$$

### 1.2 带括号{}的矩阵

```markdown
$$
  \left\{
  \begin{matrix}
   1 & 2 & 3 \\
   4 & 5 & 6 \\
   7 & 8 & 9
  \end{matrix}
  \right\}
$$
```

$$
  \left\{
  \begin{matrix}
   1 & 2 & 3 \\
   4 & 5 & 6 \\
   7 & 8 & 9
  \end{matrix}
  \right\}
$$

### 1.3 带括号[]的矩阵

```markdown
$$
  \left[
  \begin{matrix}
   1 & 2 & 3 \\
   4 & 5 & 6 \\
   7 & 8 & 9
  \end{matrix}
  \right]
$$
```

$$
  \left[
  \begin{matrix}
   1 & 2 & 3 \\
   4 & 5 & 6 \\
   7 & 8 & 9
  \end{matrix}
  \right]
$$

### 1.4 不使用left和right关键词

```markdown
$$
  \begin{bmatrix}
   1 & 2 & 3 \\
   4 & 5 & 6 \\
   7 & 8 & 9
  \end{bmatrix}
$$
```

$$
  \begin{bmatrix}
   1 & 2 & 3 \\
   4 & 5 & 6 \\
   7 & 8 & 9
  \end{bmatrix}
$$

```markdown
$$
  \begin{Bmatrix}
   1 & 2 & 3 \\
   4 & 5 & 6 \\
   7 & 8 & 9
  \end{Bmatrix}
$$
```

$$
  \begin{Bmatrix}
   1 & 2 & 3 \\
   4 & 5 & 6 \\
   7 & 8 & 9
  \end{Bmatrix}
$$

### 1.5 带省略号的矩阵

```markdown
$$
  \left[
  \begin{matrix}
  1      & 2      & \cdots & 4      \\
  7      & 6      & \cdots & 5      \\
  \vdots & \vdots & \ddots & \vdots \\
  8      & 9      & \cdots & 0      \\
  \end{matrix}
  \right]
$$
```

$$
  \left[
  \begin{matrix}
  1      & 2      & \cdots & 4      \\
  7      & 6      & \cdots & 5      \\
  \vdots & \vdots & \ddots & \vdots \\
  8      & 9      & \cdots & 0      \\
  \end{matrix}
  \right]
$$

### 1.6 带参数的矩阵

```markdown
$$
  \left[
  \begin{array}{cc|c}
    1 & 2 & 3 \\
    4 & 5 & 6
  \end{array}
  \right]
$$
```

$$
  \left[
  \begin{array}{cc|c}
    1 & 2 & 3 \\
    4 & 5 & 6
  \end{array}
  \right]
$$

### 1.7 行间矩阵

```markdown
啦啦啦$\bigl(
    \begin{matrix}
      a & b \\ c & d
    \end{matrix}
  \bigr)
$，$\begin{bmatrix}
    a & b \\ c & d
  \end{bmatrix}
$，$\begin{Bmatrix}
    a & b \\ c & d
  \end{Bmatrix}
$，$\begin{vmatrix}
    a & b \\ c & d
  \end{vmatrix}
$，$\begin{aligned}
  a & b \\ c & d \\ e & f
\end{aligned}
$，$\begin{array}{c|c}
  a & b \\ c & d
\end{array}
$叽叽喳喳
```

啦啦啦$\bigl(
    \begin{matrix}
      a & b \\ c & d
    \end{matrix}
  \bigr)
$，$\begin{bmatrix}
    a & b \\ c & d
  \end{bmatrix}
$，$\begin{Bmatrix}
    a & b \\ c & d
  \end{Bmatrix}
$，$\begin{vmatrix}
    a & b \\ c & d
  \end{vmatrix}
$，$\begin{aligned}
  a & b \\ c & d \\ e & f
\end{aligned}
$，$\begin{array}{c|c}
  a & b \\ c & d
\end{array}
$叽叽喳喳

## 2. LaTeX 公式

LaTeX的数学公式有两种： **行中公式** 和 **独立公式** 。行中公式放在文中与其它文字混编，独立公式单独成行。

行中公式：
$y = \alpha x + \beta$

独立公式：
$$
F_\beta(x) =\sum_i^{1000} \sum_{m=0}^\infty \frac{(-1)^m+m!+\frac{1}{m}}{m! \Gamma (m^m + \beta + 1 + i^2)} {\left({ \frac{x}{2} }\right)}^{2^m + \beta}
$$

### 2.1 上下标

`\^` 表示上标，`_` 表示下标。

`$$x^{y^z}=(1+{\rm e}^x)^{-2xy^w}$$`

$$x^{y^z}=(1+{\rm e}^x)^{-2xy^w}$$

如果要在左右两边都有上下标，可以用 `\sideset` 命令。

### 2.2 括号和分隔符

`$$f(x,y,z) = 3y^2z \left( 3+\frac{7x+5}{1+y^2} \right)$$`

$$f(x,y,z) = 3y^2z \left( 3+\frac{7x+5}{1+y^2} \right)$$

有时候要用 `\left.` 或 `\right.` 进行匹配而不显示本身。

`$$\left. \frac{{\rm d}u}{{\rm d}x} \right| _{x=0}$$`

$$\left. \frac{{\rm d}u}{{\rm d}x} \right| _{x=0}$$

### 2.3 分数

`$\frac{1}{3}$` 或者 `$1 \over 3$`

$\frac{1}{3}$ 或者 $1 \over 3$

### 2.4 开方

`$\sqrt{3}$`，`$\sqrt[n]{3}$`

$\sqrt{3}$，$\sqrt[n]{3}$

### 2.5 省略号

`$$f(x_1,x_2,\ldots,x_n) = x_1^2 + x_2^2 + \cdots + x_n^2$$`

$$f(x_1,x_2,\ldots,x_n) = x_1^2 + x_2^2 + \cdots + x_n^2$$

### 2.6 矢量

`$\vec{a}\cdot\vec{b}$`

$\vec{a}\cdot\vec{b}$

### 2.7 积分

`$$\int_0^1 x^2 {\rm d}x$$`

$$\int_0^1 x^2 {\rm d}x$$

### 2.8 极限

`$$\lim_{n \rightarrow +\infty} \frac{1}{n(n+1)}$$`

$$\lim_{n \rightarrow +\infty} \frac{1}{n(n+1)}$$

### 2.9 累加和累乘

`$$\sum_{i=0}^n \frac{1}{i^2}$$`

$$\sum_{i=0}^n \frac{1}{i^2}$$

`$$\prod_{i=0}^n \frac{1}{i^2}$$`

$$\prod_{i=0}^n \frac{1}{i^2}$$

### 2.10 矩阵

```markdown
$$
\begin{bmatrix}
  1 & x & x^2 \\
  1 & y & y^2 \\
  1 & z & z^2 \\
\end{bmatrix}
$$
```

$$
\begin{bmatrix}
  1 & x & x^2 \\
  1 & y & y^2 \\
  1 & z & z^2 \\
\end{bmatrix}
$$

### 2.11 希腊字母

|输入|显示|输入|显示|
|----|----|----|----|
|\alpha|$\alpha$|A|$A$
|\beta|$\beta$|B|$B$
|\gamma|$\gamma$|\Gamma|$\Gamma$
|\delta|$\delta$|\Delta|$\Delta$
|\eta|$\eta$|H|$H$
|\theta|$\theta$|\Theta|$\Theta$
|\lambda|$\lambda$|\Lambda|$\Lambda$
|\mu|$\mu$|M|$M$
|\nu|$\nu$|N|$N$
|\xi|$\xi$|\Xi|$\Xi$
|\pi|$\pi$|\Pi|$\Pi$
|\rho|$\rho$|P|$P$
|\sigma|$\sigma$|\Sigma|$\Sigma$
|\phi|$\phi$|\Phi|$\Phi$
|\omega|$\omega$|\Omega|$\Omega$

(部分希腊字母)

### 2.12 其他符号

|输入|显示|输入|显示|输入|显示|输入|显示|
|----|----|----|----|----|----|----|----|
|\pm|$\pm$|\times|$\times$|\div|$\div$|\mid|$\mid$
|\nmid|$\nmid$|\cdot|$\cdot$|\circ|$\circ$|\ast|$\ast$
|\lt|$\lt$|\gt|$\gt$|\leq|$\leq$|\geq|$\geq$
|\neq|$\neq$|\approx|$\approx$|\equiv|$\equiv$|\sum|$\sum$
|\prod|$\prod$|\coprod|$\coprod$|\bigodot|$\bigodot$|\bigotimes|$\bigotimes$|

|输入|显示|输入|显示|输入|显示|输入|显示|
|----|----|----|----|----|----|----|----|
|\emptyset|$\emptyset$|\in|$\in$|\notin|$\notin$|\subset|$\subset$
|\supset|$\supset$|\bigcap|$\bigcap$|\bigcup|$\bigcup$|\bigvee|$\bigvee$
|\bigwedge|$\bigwedge$|

|输入|显示|输入|显示|输入|显示|
|----|----|----|----|----|----|
|\log|$\log$|\ln|$\ln$|\lg|$\lg$|

|输入|显示|输入|显示|输入|显示|输入|显示|
|----|----|----|----|----|----|----|----|
|\prime|$\prime$|\int|$\int$|\iint|$\iint$|\iiint|$\iiint$
|\oint|$\oint$|\lim|$\lim$|\infty|$\infty$|\nabla|$\nabla$

|输入|显示|输入|显示|
|----|----|----|----|
|\because|$\because$|\therefore|$\therefore$|
|\forall|$\forall$|\exists|$\exists$
|\not=|$\not=$|\not>|$\not>$|
|\not\subset|$\not\subset$

|输入|显示|输入|显示|
|----|----|----|----|
|\uparrow|$\uparrow$|\downarrow|$\downarrow$|
|\Uparrow|$\Uparrow$|\Downarrow|$\Downarrow$
|\rightarrow|$\rightarrow$|\leftarrow|$\leftarrow$|
|\Rightarrow|$\Rightarrow$|\Leftarrow|$\Leftarrow$
|\longrightarrow|$\longrightarrow$|\longleftarrow|$\longleftarrow$|
|\Longrightarrow|$\Longrightarrow$|\Longleftarrow|$\Longleftarrow$

|输入|对用字体|
|----|--------|
|\rm|罗马体
|\it|意大利体
|\bf|黑体
|\cal|花体
|\st|倾斜体
|\sf|等线体
|\mit|数学斜体
|\tt|打字机字体
|\sc|小体大写字母

## 参考：

[使用LaTeX写矩阵](https://blog.csdn.net/bendanban/article/details/44221279)

[MarkDown Latex公式，矩阵，表格等使用](https://blog.csdn.net/u014228934/article/details/78223442)

## 更多资源

[Markdown 公式指导手册](https://www.zybuluo.com/codeep/note/163962)

[markdown完美支持latex](https://whaozl.github.io/2016/08/07/tool-markdown-latex.html)

[Cmd Markdown 编辑阅读器](https://www.zybuluo.com/mdeditor)
