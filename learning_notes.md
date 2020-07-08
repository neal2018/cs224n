## Matrix

函数$F:\mathbb{R}\rightarrow \mathbb{R^{m\times n}}$，则 $\partial{F}/\partial{x}$ 是一个 $m\times n$ 维矩阵，且 $(\partial{F}/\partial{x})_{ij} = \partial{f_{ij}}/\partial{x}$。

若函数$f:\mathbb{R^{m\times n}}\rightarrow \mathbb{R}$，则 $\partial{f}/\partial{X}$ 也是一个 $m\times n$ 维矩阵，且 $(\partial{f}/\partial{X})_{ij} = \partial{f}/\partial{x_{ij}}$。

若函数 $\boldsymbol{f}:\mathbb{R^{n}}\rightarrow\mathbb{R^{m}}$，则 $\partial{\boldsymbol{f}}/\partial{\boldsymbol{x}}$ 是一个 $m\times n$ 维矩阵，且 $(\partial{\boldsymbol{f}}/\partial{\boldsymbol{x}})_{ij} = \partial{f_i}/\partial{x_j}$。

$\nabla tr(A^TX) = \nabla tr(AX^T) = A$

$\nabla tr(AX) = \nabla tr(XA) = A^T$

$\nabla_{X} \;f(AX+B) = A^T \nabla_Y f$

$\nabla_{\boldsymbol{x}} \;f(A\boldsymbol{x}+\boldsymbol{b}) = A^T \nabla_\boldsymbol{y} f$

$\sum_j a_{ij}b_{jk} => AB$

$\sum_i u_iv_i = \boldsymbol{u}^T\boldsymbol{v}$

$\sum_{ij}a_{ij}b_{ij} = tr(A^TB)$



---

### softmax

A function turning a vector into a distribution.

Given $v = (v_1, v_2, ..., v_n)$

the output distribution is

$$
P_i = \frac{e^{v_i}}{\sum_{0<j\le n} e^{v_j}}
$$

---

### cross-entropy

A function accepting two distributions as input, and return a value to measure their difference.

Given two distributions $P$ and $Q$

the output value is 
$$
H(P,Q) = -\sum_{x \in X} P(x)\log Q(x)
$$

---

### draft

Task: given words $o$ and $c$, find out the probability that $o$ falls in the window of $c$



$$
P(O=o|C=c) = \frac{e^{u^T_ov_c}}{\sum_{\omega \in Vocab}e^{u^T_\omega v_c}}
$$

$$
loss = J_{naive-softmax}(v_c, o,U) = -\log P(O=o|C=c)
$$

