> [!summary] 关键总结
> 拉格朗日乘数法与 KKT 的核心不是背方程组，而是“梯度平衡”。在等式约束 $g(x)=0$ 的极值点 $x^*$ 处，$\nabla f(x^*)$ 必须落在约束法空间内，所以存在 $\lambda^*$ 使
> $$
> \nabla f(x^*)+\lambda^*\nabla g(x^*)=0.
> $$
> 对不等式约束 $g_i(x)\le0$，只有边界活跃的约束才可能产生影响；内部点相当于无约束。KKT 比 Lagrange 多两条：
> - 对偶可行：$\mu_i\ge0$；
> - 互补松弛：$\mu_i g_i(x^*)=0$。
>
> 最简单用法：写 Lagrangian → 令 $\nabla_x L=0$ → 分类讨论活跃集 → 检查 $\mu_i\ge0$ → 比较候选点。
>
> 联系与推广：凸问题中 KKT 是全局最优的充要条件；乘子 $\mu_i$ 是影子价格；KKT 等价于强对偶与鞍点。

> [!definition] 定义：Lagrange 乘数法
> 对等式约束问题
> $$
> \min_{x\in\mathbb R^n} f(x)\quad \mathrm{s.t.}\quad g_i(x)=0,\ i=1,\dots,m,
> $$
> 构造 Lagrangian
> $$
> L(x,\lambda)=f(x)+\sum_{i=1}^m\lambda_i g_i(x).
> $$
> 若 $x^*$ 是极值点且 $\{\nabla g_i(x^*)\}$ 线性无关，则存在唯一 $\lambda^*\in\mathbb R^m$ 使
> $$
> \nabla_x L(x^*,\lambda^*)=0.
> $$

> [!note] 核心图像：梯度为什么必须平衡
> 若 $x^*$ 在约束边界 $g(x)=0$ 上达到极值，沿边界任意可行方向的移动都不应改变目标值，因此 $\nabla f(x^*)$ 不能有切向分量，只能与 $\nabla g(x^*)$ 共线。对多个约束，$\nabla f(x^*)$ 必须在所有活跃约束梯度张成的法空间中。
>
> 对不等式 $g_i(x)\le0$，可行方向 $d$ 必须满足 $\nabla g_i(x^*)^T d\le0$。若要避免目标下降，需不存在 $d$ 同时满足 $\nabla f(x^*)^T d<0$。几何上，$-\nabla f$ 必须落在活跃约束梯度的正锥中，即
> $$
> -\nabla f(x^*)=\sum_{i\in I(x^*)}\mu_i\nabla g_i(x^*),\quad \mu_i\ge0.
> $$
> 这就是 KKT 梯度条件与对偶可行的来源。不活跃约束不影响局部极值，故对应乘子取 $0$。

> [!definition] 定义：KKT 条件（标准形式）
> 考虑问题
> $$
> \min_{x\in\mathbb R^n} f(x)\quad \mathrm{s.t.}\quad g_i(x)\le0,\ i=1,\dots,m;\quad h_j(x)=0,\ j=1,\dots,p.
> $$
> Lagrangian 为
> $$
> L(x,\mu,\lambda)=f(x)+\sum_{i=1}^m\mu_i g_i(x)+\sum_{j=1}^p\lambda_j h_j(x).
> $$
> $x^*$ 满足 KKT 条件是指存在 $\mu^*\in\mathbb R^m$，$\lambda^*\in\mathbb R^p$ 使得：
> 1. 梯度为零：$\nabla_x L(x^*,\mu^*,\lambda^*)=0$；
> 2. 原始可行：$g_i(x^*)\le0$，$h_j(x^*)=0$；
> 3. 对偶可行：$\mu_i^*\ge0$；
> 4. 互补松弛：$\mu_i^*g_i(x^*)=0$。

> [!tip] 方法论：KKT 最简单用法
> 实际解题不必执着于证明，只需按以下步骤：
> 1. 写 Lagrangian：不等式项前乘 $\mu_i$，等式项前乘 $\lambda_j$；
> 2. 令 $\nabla_x L=0$，得到梯度方程；
> 3. 对每个不等式约束 $g_i\le0$ 分类讨论：是活跃（取等号）还是不活跃（乘子为 $0$）？
> 4. 解出候选点，检查 $\mu_i\ge0$ 与所有约束；
> 5. 比较候选点的目标值。若问题是凸的，则 KKT 点即为全局最优。

> [!example] 例题：KKT 分类讨论
> 求解
> $$
> \min_{(x,y)\in\mathbb R^2}\ (x-1)^2+(y-2)^2\quad \mathrm{s.t.}\quad x+y\le1,\ x\ge0,\ y\ge0.
> $$
> Lagrangian 为
> $$
> L=(x-1)^2+(y-2)^2+\mu_1(x+y-1)-\mu_2 x-\mu_3 y,
> $$
> 其中 $\mu_1,\mu_2,\mu_3\ge0$。
>
> 梯度条件：
> $$
> 2(x-1)+\mu_1-\mu_2=0,\quad 2(y-2)+\mu_1-\mu_3=0.
> $$
> 原始可行：$x+y\le1$，$x\ge0$，$y\ge0$。
> 互补松弛：$\mu_1(x+y-1)=0$，$\mu_2 x=0$，$\mu_3 y=0$。
>
> 分类讨论：
> - 若 $x+y<1$，则 $\mu_1=0$。若 $x>0,y>0$，则 $\mu_2=\mu_3=0$，得 $x=1,y=2$，违反 $x+y\le1$，舍去。
> - 因此 $x+y=1$ 活跃，$\mu_1\ge0$。还需检查 $x$ 或 $y$ 是否为 $0$。
> - 取 $x=0$，则 $y=1$，由方程得 $-2+\mu_1-\mu_2=0$，$-2+\mu_1=0$，故 $\mu_1=2,\mu_2=0$，全部非负。候选点 $(0,1)$，目标值 $2$。
> - 取 $y=0$，则 $x=1$，得 $0+\mu_1-\mu_2=0$，$-4+\mu_1=0$，故 $\mu_1=4,\mu_2=4$，非负。候选点 $(1,0)$，目标值 $4$。
>
> 由于目标函数凸，约束凸，KKT 点全局最优。比较得最优解 $(0,1)$，最优值 $2$。

> [!warning] 注意事项：约束规范不能丢
> KKT 条件不是无条件必要的。经典反例：
> $$
> \min x\quad \mathrm{s.t.}\quad x^2\le0.
> $$
> 可行域只有 $\{0\}$，最优解 $x^*=0$。但 $\nabla g(0)=0$，梯度方程 $1+\mu\cdot0=0$ 不可能成立。原因是约束梯度退化，约束规范失效。实际使用中，若约束梯度线性无关（LICQ）或凸问题满足 Slater 条件，则 KKT 可靠。

> [!note] 联系与推广
> - **凸优化充分性**：若 $f,g_i$ 凸，$h_j$ 仿射，则任一 KKT 点都是全局最优。证明思想：此时 $L(\cdot,\mu^*,\lambda^*)$ 是凸函数，梯度为零的点是全局最小点，再利用互补松弛与可行性比较 $f(x^*)$ 与 $f(x)$。
> - **对偶与鞍点**：对偶函数 $\theta(\mu,\lambda)=\inf_x L(x,\mu,\lambda)$。强对偶下原问题与对偶问题同值，KKT 条件等价于鞍点条件
> $$
> L(x^*,\mu,\lambda)\le L(x^*,\mu^*,\lambda^*)\le L(x,\mu^*,\lambda^*).
> $$
> - **影子价格**：$\mu_i^*$ 近似表示第 $i$ 个约束右端增加一单位时最优值的变化，即 $-\partial p^*/\partial b_i\approx\mu_i^*$。因此乘子衡量约束的“稀缺性”或“价格”。
> - **罚函数联系**：KKT 可看作精确罚函数
> $$
> P_\rho(x)=f(x)+\rho\sum_i\max(0,g_i(x))^2+\rho\sum_j h_j(x)^2
> $$
> 在 $\rho\to\infty$ 时的极限一阶条件。
> - **机器学习应用**：支持向量机、Lasso、带约束的神经网络训练等大量使用 KKT 作为最优性刻画。

> [!exercise] 习题
> 1. 用 KKT 求解
> $$
> \min_{(x,y)\in\mathbb R^2}\ x^2+y^2\quad \mathrm{s.t.}\quad x+y\ge1.
> $$
> 2. 验证反例 $\min x$ s.t. $x^2\le0$ 没有 KKT 点但仍有最优解，并指出违背了哪个约束规范。
> 3. 设 $f$ 凸，$g$ 凸，$h$ 仿射。简述为什么 KKT 点是全局最优解。
> 4. 若将不等式约束写成 $g_i(x)\ge0$，乘子符号会如何变化？给出新的对偶可行条件。
