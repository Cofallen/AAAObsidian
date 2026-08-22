> [!summary] 核心总结
> Beta 函数 $B(x,y)$ 是区间 $[0,1]$ 上两个幂函数乘积的积分，也是 Gamma 函数乘积的比值 $B(x,y)=\frac{\Gamma(x)\Gamma(y)}{\Gamma(x+y)}$。它作为 Beta 分布和 Dirichlet 分布的归一化常数，在概率统计和特殊函数中非常常用。核心方法是变量替换和递推降维。

---

## 1. 经典 Beta 函数

> [!definition] 定义
> 设 $\operatorname{Re}x>0,\ \operatorname{Re}y>0$，定义
> $$
> B(x,y)=\int_0^1 t^{x-1}(1-t)^{y-1}\,dt.
> $$
> 等价形式：
> $$
> B(x,y)=2\int_0^{\pi/2}\sin^{2x-1}\theta\cos^{2y-1}\theta\,d\theta
> =\int_0^\infty \frac{u^{x-1}}{(1+u)^{x+y}}\,du.
> $$

> [!theorem] 基本性质
> 1. 对称性：$B(x,y)=B(y,x)$。
> 2. 递推关系：$B(x+1,y)=\frac{x}{x+y}B(x,y)$。
> 3. 与 Gamma 函数关系：$B(x,y)=\frac{\Gamma(x)\Gamma(y)}{\Gamma(x+y)}$。
> 4. 特殊值：$B(1,1)=1$，$B(\frac12,\frac12)=\pi$，且对正整数 $n,m$ 有 $B(n,m)=\frac{(n-1)!(m-1)!}{(n+m-1)!}$。

> [!proof] 与 Gamma 函数关系的证明
> 由 Gamma 函数定义，
> $$
> \Gamma(x)\Gamma(y)=\int_0^\infty\int_0^\infty u^{x-1}v^{y-1}e^{-(u+v)}\,du\,dv.
> $$
> 作变量替换 $u=r\cos^2\theta$，$v=r\sin^2\theta$，其中 $r>0$，$0<\theta<\pi/2$。雅可比行列式为
> $$
> \frac{\partial(u,v)}{\partial(r,\theta)}
> =
> \begin{vmatrix}
> \cos^2\theta & -2r\cos\theta\sin\theta\\
> \sin^2\theta & 2r\sin\theta\cos\theta
> \end{vmatrix}
> =2r\sin\theta\cos\theta.
> $$
> 于是
> $$
> \Gamma(x)\Gamma(y)
> =2\int_0^\infty e^{-r}r^{x+y-1}\,dr
> \int_0^{\pi/2}\cos^{2x-1}\theta\sin^{2y-1}\theta\,d\theta.
> $$
> 第一个积分等于 $\Gamma(x+y)$。对第二个积分令 $t=\sin^2\theta$，则 $dt=2\sin\theta\cos\theta\,d\theta$，因此
> $$
> \int_0^{\pi/2}\cos^{2x-1}\theta\sin^{2y-1}\theta\,d\theta
> =\frac12 B(y,x)=\frac12 B(x,y).
> $$
> 所以
> $$
> \Gamma(x)\Gamma(y)=\Gamma(x+y)B(x,y),
> $$
> 即得
> $$
> B(x,y)=\frac{\Gamma(x)\Gamma(y)}{\Gamma(x+y)}.
> $$

> [!proof] 递推关系证明
> 直接利用 Gamma 关系：
> $$
> B(x+1,y)=\frac{\Gamma(x+1)\Gamma(y)}{\Gamma(x+y+1)}
> =\frac{x\Gamma(x)\Gamma(y)}{(x+y)\Gamma(x+y)}
> =\frac{x}{x+y}B(x,y).
> $$

---

## 2. 不完全 Beta 函数

> [!definition] 定义
> 对 $0\le z\le1$ 及 $\operatorname{Re}a>0,\operatorname{Re}b>0$，定义
> $$
> B(z;a,b)=\int_0^z t^{a-1}(1-t)^{b-1}\,dt.
> $$
> 正则化不完全 Beta 函数为
> $$
> I_z(a,b)=\frac{B(z;a,b)}{B(a,b)}.
> $$

> [!note] 概率意义
> 若随机变量 $X\sim \operatorname{Beta}(a,b)$，则其累积分布函数为
> $$
> P(X\le z)=I_z(a,b).
> $$
> 不完全 Beta 函数在二项分布尾部概率、置信区间计算中经常出现。

---

## 3. 多元 Beta 函数（Dirichlet 积分）

> [!definition] 定义
> 设 $\alpha_i>0$，$i=1,\dots,k$，在单纯形
> $$
> \Delta_k=\left\{(x_1,\dots,x_k): x_i\ge0,\ \sum_{i=1}^k x_i=1\right\}
> $$
> 上定义
> $$
> \mathcal B(\alpha_1,\dots,\alpha_k)
> =
> \int_{\Delta_k}
> \prod_{i=1}^k x_i^{\alpha_i-1}\,dx_1\cdots dx_{k-1}.
> $$
> 其值为
> $$
> \mathcal B(\alpha_1,\dots,\alpha_k)
> =
> \frac{\prod_{i=1}^k \Gamma(\alpha_i)}
> {\Gamma\left(\sum_{i=1}^k \alpha_i\right)}.
> $$

> [!proof] Dirichlet 积分公式证明思路
> 记 $I_k=\mathcal B(\alpha_1,\dots,\alpha_k)$。固定前 $k-2$ 个变量，令 $s=1-\sum_{i=1}^{k-2}x_i$。对 $x_{k-1}$ 积分：
> $$
> \int_0^s x_{k-1}^{\alpha_{k-1}-1}(s-x_{k-1})^{\alpha_k-1}\,dx_{k-1}
> =s^{\alpha_{k-1}+\alpha_k-1}B(\alpha_{k-1},\alpha_k).
> $$
> 因此
> $$
> I_k = B(\alpha_{k-1},\alpha_k)\,I_{k-1}(\alpha_1,\dots,\alpha_{k-2},\alpha_{k-1}+\alpha_k).
> $$
> 反复递推，利用经典 Beta 与 Gamma 关系即可得到闭式。

> [!tip] 方法论
> 多维单纯形积分通过“先积最后一个变量”化为经典 Beta 函数，再逐步降维。这是处理 Dirichlet 分布矩和归一化常数的标准方法。

---

## 4. 与超几何函数的关系

> [!theorem] 超几何表示
> 对 $\operatorname{Re}c>\operatorname{Re}b>0$ 且 $|z|<1$，
> $$
> \int_0^1 t^{b-1}(1-t)^{c-b-1}(1-zt)^{-a}\,dt
> =
> B(b,c-b)\,{}_2F_1(a,b;c;z).
> $$
> 当 $a=0$ 时回到经典 Beta 函数。

> [!proof] 证明
> 展开 $(1-zt)^{-a}=\sum_{n=0}^\infty \frac{(a)_n}{n!}(zt)^n$，逐项积分得
> $$
> \sum_{n=0}^\infty \frac{(a)_n z^n}{n!}B(b+n,c-b).
> $$
> 利用
> $$
> B(b+n,c-b)=B(b,c-b)\frac{(b)_n}{(c)_n},
> $$
> 即得超几何函数表示。

---

## 5. 常用结论与技巧

> [!tip] 核心方法
> 1. **Gamma 函数连接**：几乎所有 Beta 函数积分都可以通过 Gamma 函数表达。
> 2. **变量替换**：$t=\sin^2\theta$ 或 $t=\frac{u}{1+u}$ 可将 Beta 积分转化为三角或半轴积分。
> 3. **递推降维**：多元单纯形积分逐个变量积分，化为低维积分。
> 4. **概率归一化**：Beta 函数是 Beta 分布和 Dirichlet 分布的归一化常数，矩的计算可转化为 Beta 函数比值。

> [!warning] 注意事项
> - 经典 Beta 函数要求参数实部为正，否则积分发散。例如 $B(0,1)$ 发散。
> - 不完全 Beta 函数中 $z$ 必须在 $[0,1]$ 内。
> - Dirichlet 积分要求所有 $\alpha_i>0$；若某个参数 $\le0$，积分在边界发散。

> [!example] 简单练习
> 1. 证明 $B(x,y)=B(x+1,y)+B(x,y+1)$。
> 2. 计算 $\int_0^1 x^{a-1}(1-x)^{b-1}\ln x\,dx=B(a,b)(\psi(a)-\psi(a+b))$，其中 $\psi$ 为 digamma 函数。
> 3. 若 $(X_1,\dots,X_k)\sim \operatorname{Dirichlet}(\alpha_1,\dots,\alpha_k)$，求 $E[X_i]$ 和 $\operatorname{Var}(X_i)$。
