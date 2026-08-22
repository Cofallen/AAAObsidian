主人，这份 Glasser 主定理讲义已按 Obsidian 格式整理，直接复制即可。

# Glasser 主定理

> [!note] 核心总结
> 设 $f\in L^1(\mathbb R)$，$a_k>0$，$c_k\in\mathbb R$ 互异。令
> $$\phi(x)=x-\sum_{k=1}^n\frac{a_k}{x-c_k}.$$
> 则
> $$\int_{-\infty}^{\infty}f(\phi(x))\,\mathrm{d}x=\int_{-\infty}^{\infty}f(x)\,\mathrm{d}x.$$
> 最常用的单参数情形是
> $$\int_{-\infty}^{\infty}f\left(x-\frac{a}{x}\right)\mathrm{d}x=\int_{-\infty}^{\infty}f(x)\,\mathrm{d}x,\quad a>0.$$
> 核心思想：$\phi$ 在每个极点分隔出的区间上单调地把该区间映满 $\mathbb R$，所有分支的 Jacobian 倒数之和恒为 $1$，因此整体保持积分值。

> [!note] 定义（Glasser 变换）
> 称
> $$\phi(x)=x-\sum_{k=1}^n\frac{a_k}{x-c_k},\quad a_k>0,\ c_k\in\mathbb R$$
> 为 Glasser 变换。$c_k$ 是它的极点。若 $n=1,c_1=0,a_1=a$，就得到常见的 $x-\frac ax$。

> [!note] 定理（Glasser 主定理）
> 设 $f\in L^1(\mathbb R)$，$a_k>0$，$c_k\in\mathbb R$ 互异。定义
> $$\phi(x)=x-\sum_{k=1}^n\frac{a_k}{x-c_k}.$$
> 则
> $$\int_{-\infty}^{\infty}f(\phi(x))\,\mathrm{d}x=\int_{-\infty}^{\infty}f(x)\,\mathrm{d}x.$$
> 若两侧积分只在 Cauchy 主值或广义 Riemann 积分意义下存在，则通常也要在相同意义下理解结论。

> [!note] 严格证明
> **第一步：分支与单调性。**
> 令 $I_0=(-\infty,c_1)$，$I_j=(c_j,c_{j+1})$，$j=1,\dots,n-1$，$I_n=(c_n,\infty)$。在每个 $I_j$ 上，
> $$\phi'(x)=1+\sum_{k=1}^n\frac{a_k}{(x-c_k)^2}>0.$$
> 因为 $a_k>0$，所以 $\phi$ 在每个区间上严格递增。
>
> 考察端点：当 $x\to c_k^+$ 时，$\frac{a_k}{x-c_k}\to+\infty$，故 $\phi(x)\to-\infty$；当 $x\to c_{k+1}^-$ 时，$-\frac{a_{k+1}}{x-c_{k+1}}\to+\infty$，故 $\phi(x)\to+\infty$。外区间也有
> $$\phi(-\infty)=-\infty,\quad \phi(c_1^-)=+\infty,\quad \phi(c_n^+)=-\infty,\quad \phi(+\infty)=+\infty.$$
> 因此对每个 $u\in\mathbb R$，方程 $\phi(x)=u$ 在每个 $I_j$ 中恰有一个根，记为 $x_j(u)$。
>
> **第二步：证明 Jacobian 倒数之和为 $1$。**
> 固定 $u\in\mathbb R$。因为 $\phi'(x_j(u))>0$，这些根都是单根。考虑有理函数
> $$R(z)=\frac{1}{\phi(z)-u}.$$
> 它的有限极点正是 $x_0(u),\dots,x_n(u)$，且
> $$\operatorname{Res}_{z=x_j(u)}R(z)=\frac{1}{\phi'(x_j(u))}.$$
> 注意 $c_k$ 处 $\phi(z)\to\infty$，所以 $R(z)\to0$，$c_k$ 不是极点。
>
> 当 $z\to\infty$ 时，$\phi(z)=z+O(1/z)$，所以
> $$R(z)\sim\frac1z.$$
> 因此
> $$\operatorname{Res}_{z=\infty}R(z)=-\lim_{z\to\infty}zR(z)=-1.$$
> 有理函数在 Riemann 球上的留数总和为零，所以
> $$\sum_{j=0}^n\frac{1}{\phi'(x_j(u))}-1=0.$$
> 即
> $$\sum_{j=0}^n\frac{1}{\phi'(x_j(u))}=1.$$
>
> **第三步：换元积分。**
> 把积分按区间拆开：
> $$\int_{-\infty}^{\infty}f(\phi(x))\,\mathrm{d}x=\sum_{j=0}^n\int_{I_j}f(\phi(x))\,\mathrm{d}x.$$
> 在每个 $I_j$ 上令 $u=\phi(x)$。由于 $\phi$ 单调递增，
> $$\mathrm{d}x=\frac{\mathrm{d}u}{\phi'(x_j(u))}.$$
> 于是
> $$\int_{-\infty}^{\infty}f(\phi(x))\,\mathrm{d}x=\sum_{j=0}^n\int_{-\infty}^{\infty}f(u)\frac{\mathrm{d}u}{\phi'(x_j(u))}.$$
> 由 $f\in L^1(\mathbb R)$ 和有限和，可交换求和与积分：
> $$\int_{-\infty}^{\infty}f(\phi(x))\,\mathrm{d}x=\int_{-\infty}^{\infty}f(u)\left[\sum_{j=0}^n\frac{1}{\phi'(x_j(u))}\right]\mathrm{d}u=\int_{-\infty}^{\infty}f(u)\,\mathrm{d}u.$$
> 证毕。

> [!tip] 直观理解
> 变换 $\phi(x)=x-\sum_k\frac{a_k}{x-c_k}$ 并不是一对一，而是把每个区间 $I_j$ 都单调地映射到整条实轴。换元后，同一个 $u$ 会出现多次，但每次的 Jacobian 权重之和正好是 $1$。所以积分总质量没有被放大或缩小。
>
> 这也是为什么参数必须 $a_k>0$：只有正参数才能保证 $\phi'>0$，从而每个分支严格单调且覆盖整个 $\mathbb R$。

> [!example] 例 1：有理函数
> 计算
> $$\int_{-\infty}^{\infty}\frac{\mathrm{d}x}{\left(x-\frac{2}{x}\right)^2+1}.$$
> 取 $f(y)=\frac{1}{y^2+1}$，$a=2$。由 Glasser 主定理，
> $$\int_{-\infty}^{\infty}\frac{\mathrm{d}x}{\left(x-\frac{2}{x}\right)^2+1}=\int_{-\infty}^{\infty}\frac{\mathrm{d}y}{y^2+1}=\pi.$$

> [!example] 例 2：Gauss 型积分
> 计算
> $$\int_{-\infty}^{\infty}\exp\left[-\left(x-\frac{1}{x}\right)^2\right]\mathrm{d}x.$$
> 取 $f(y)=e^{-y^2}$，得
> $$\int_{-\infty}^{\infty}\exp\left[-\left(x-\frac{1}{x}\right)^2\right]\mathrm{d}x=\int_{-\infty}^{\infty}e^{-y^2}\,\mathrm{d}y=\sqrt{\pi}.$$

> [!example] 例 3：多极点情形
> 计算
> $$\int_{-\infty}^{\infty}\frac{\mathrm{d}x}{\left(x-\frac{1}{x}-\frac{2}{x-1}\right)^2+1}.$$
> 令 $f(y)=\frac{1}{y^2+1}$，由一般定理直接得到
> $$\int_{-\infty}^{\infty}\frac{\mathrm{d}x}{\left(x-\frac{1}{x}-\frac{2}{x-1}\right)^2+1}=\int_{-\infty}^{\infty}\frac{\mathrm{d}y}{y^2+1}=\pi.$$

> [!warning] 注意事项与反例
> - 必须保证 $a_k>0$。若 $a<0$，例如 $\phi(x)=x+\frac1x$，其值域是 $(-\infty,-2]\cup[2,\infty)$，不覆盖 $(-2,2)$，定理一般失效。
> - 反例：取 $f(y)=\mathbf 1_{(0,1)}(y)$，$a=-1$。则
> $$\int_{-\infty}^{\infty}f(x)\,\mathrm{d}x=\int_0^1\mathrm{d}y=1,$$
> 但 $\phi(x)=x+\frac1x$ 永远不落在 $(0,1)$ 中，所以
> $$\int_{-\infty}^{\infty}f(\phi(x))\,\mathrm{d}x=0.$$
> - 定理要求 $f$ 可积，或至少积分在 Cauchy 主值意义下存在。两边都发散时不能声称相等。
> - 若 $f$ 只有条件收敛，需要先对截断积分证明，再取极限。

> [!note] 方法论总结
> 遇到形如
> $$\int_{-\infty}^{\infty}f\left(x-\sum_{k=1}^n\frac{a_k}{x-c_k}\right)\mathrm{d}x$$
> 的积分时：
> 1. 先识别被积函数是否为某个已知积分核 $f$ 的复合；
> 2. 检查参数 $a_k$ 是否全部为正；
> 3. 写出 $\phi$ 的极点，把实轴切成单调区间；
> 4. 对每个区间换元，得到各支 Jacobian 倒数之和；
> 5. 用留数恒等式或代数恒等式证明该和为 $1$；
> 6. 把结果化简为 $\int_{-\infty}^{\infty}f(u)\,\mathrm{d}u$。

> [!question] 习题
> 1. 计算
> $$\int_{-\infty}^{\infty}\frac{\mathrm{d}x}{\left(x-\frac{3}{x+1}\right)^2+4}.$$
> 2. 设 $a>0$，说明
> $$\int_{-\infty}^{\infty}\frac{x^2}{x^4+1}\,\mathrm{d}x=\int_{-\infty}^{\infty}\frac{(x-a/x)^2}{(x-a/x)^4+1}\,\mathrm{d}x.$$
> 3. 找一个 $a<0$ 的具体函数 $f$，验证 Glasser 定理失败。
>
> 答案提示：1. 取 $f(y)=\frac{1}{y^2+4}$，结果为 $\frac\pi2$。2. 这是 Glasser 主定理的直接结果。3. 可用 $f=\mathbf 1_{(0,1)}$，$a=-1$。
