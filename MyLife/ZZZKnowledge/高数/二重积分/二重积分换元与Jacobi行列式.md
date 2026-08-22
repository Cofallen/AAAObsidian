主人，以下内容已按 Obsidian 格式整理，可直接复制到笔记中。

# 二重积分换元与 Jacobi 行列式

> [!note] 核心总结
> 设 $\Phi(u,v)=(x(u,v),y(u,v))$ 是 $uv$ 平面区域 $D'$ 到 $xy$ 平面区域 $D$ 的 $C^1$ 单射，且除面积为零的集合外满足 $\det J_\Phi(u,v)\neq 0$。则
> $$\iint_D f(x,y)\,dx\,dy=\iint_{D'} f(x(u,v),y(u,v))\left|\frac{\partial(x,y)}{\partial(u,v)}\right|\,du\,dv.$$
> 核心：$J_\Phi$ 的绝对值是局部面积伸缩因子，公式本质是“局部线性化 + 平行四边形面积 + Riemann 和极限”。

> [!note] 定义：Jacobi 矩阵与 Jacobi 行列式
> 设 $D'\subset\mathbb{R}^2$ 为有界区域，$\Phi:D'\to\mathbb{R}^2$ 由 $\Phi(u,v)=(x(u,v),y(u,v))$ 给出。若 $x,y$ 在 $D'$ 上有连续偏导数，则称 $\Phi$ 为 $C^1$ 映射。其 Jacobi 矩阵为
> $$J_\Phi(u,v)=\begin{pmatrix}\partial x/\partial u & \partial x/\partial v\\ \partial y/\partial u & \partial y/\partial v\end{pmatrix}.$$
> Jacobi 行列式记作
> $$\frac{\partial(x,y)}{\partial(u,v)}=\det J_\Phi(u,v)=\frac{\partial x}{\partial u}\frac{\partial y}{\partial v}-\frac{\partial x}{\partial v}\frac{\partial y}{\partial u}.$$
> 若 $\Phi$ 在 $D'$ 上单射、$C^1$，并且逆映射也连续，则称 $\Phi$ 为 $D'$ 上的同胚；若逆映射还是 $C^1$ 且 $J_\Phi\neq 0$，则称 $\Phi$ 为 $C^1$ 微分同胚。

> [!warning] 定理使用条件
> 考研范围内的常见充分条件是：$\Phi$ 在闭区域 $D'$ 上 $C^1$，把 $D'$ 的内部一一映到 $D$ 的内部，且在内部成立 $J_\Phi(u,v)\neq 0$。边界上允许退化，例如极坐标在 $r=0$ 处 $J=0$。若 $J_\Phi$ 改变符号，应把 $D'$ 拆成若干子区域，使每个子区域上 $J_\Phi$ 保持同号。

> [!note] 证明思路：从线性近似到面积微元
> 对 $D'$ 作矩形分割，取小矩形 $[u_0,u_0+\Delta u]\times[v_0,v_0+\Delta v]$。由可微性，
> $$\Phi(u_0+\Delta u,v_0+\Delta v)=\Phi(u_0,v_0)+J_\Phi(u_0,v_0)\begin{pmatrix}\Delta u\\ \Delta v\end{pmatrix}+o\left(\sqrt{\Delta u^2+\Delta v^2}\right).$$
> 略去高阶无穷小后，小矩形在 $xy$ 平面中的像近似为平行四边形，其两边为
> $$a=\frac{\partial \Phi}{\partial u}(u_0,v_0)\Delta u,\quad b=\frac{\partial \Phi}{\partial v}(u_0,v_0)\Delta v.$$
> 该平行四边形的面积为
> $$|\det(a,b)|=\left|\det J_\Phi(u_0,v_0)\right|\Delta u\Delta v.$$
> 于是 Riemann 和
> $$\sum_{i,j} f(\Phi(u_i,v_j))\left|\det J_\Phi(u_i,v_j)\right|\Delta u\Delta v$$
> 同时逼近原积分与新积分；线性化造成的误差可由可微性和可积性控制。这就是换元公式的来源。

> [!tip] 直觉：为什么是行列式？
> 一元换元中 $dx=x'(u)\,du$，线性近似把长度微元拉长 $|x'(u)|$ 倍。二元换元中线性映射 $J_\Phi$ 把单位正方形变为平行四边形，面积伸缩恰好为 $|\det J_\Phi|$。所以行列式不是额外记忆，而是线性代数中“线性映射的体积伸缩率”在局部线性化下的自然继承。

> [!warning] 注意与反例
> - 必须取绝对值：例如交换变量 $\Phi(u,v)=(v,u)$，$J=-1$，但面积不缩小，$|J|=1$。
> - 局部可逆不等于全局单射：极坐标 $\Phi(r,\theta)=(r\cos\theta,r\sin\theta)$ 在 $r>0$ 局部 $J=r\neq 0$，但若 $\theta$ 区间长度超过 $2\pi$ 会重叠覆盖，公式必须限制在单射区域。
> - $J=0$ 不一定不可积，但若在正面积集合上恒为 $0$，像的面积为 $0$，如 $\Phi(u,v)=(u,0)$，$J=0$，不能作为二重积分换元到二维区域。
> - 边界参数化要单独检查，例如极坐标原点的退化不影响积分值，因为边界面积为零。

> [!example] 示例：圆盘面积与高斯积分
> 令 $x=r\cos\theta,\ y=r\sin\theta$，其中 $0\le r\le R,\ 0\le\theta\le2\pi$。于是
> $$J=\frac{\partial(x,y)}{\partial(r,\theta)}=\begin{vmatrix}\cos\theta & -r\sin\theta\\ \sin\theta & r\cos\theta\end{vmatrix}=r.$$
> 因 $r\ge 0$，$|J|=r$。面积
> $$\iint_D 1\,dxdy=\int_0^{2\pi}\int_0^R r\,dr\,d\theta=\pi R^2.$$
> 高斯积分
> $$\iint_D e^{-(x^2+y^2)}\,dxdy=\int_0^{2\pi}\int_0^R e^{-r^2}r\,dr\,d\theta=\pi(1-e^{-R^2}).$$
> 若 $R\to\infty$，可得 $\int_{-\infty}^{\infty}e^{-t^2}\,dt=\sqrt{\pi}$。

> [!note] 延伸：$n$ 重积分与微分形式
> $n$ 重积分换元为
> $$\int_{\Phi(D')} f(x)\,dx=\int_{D'} f(\Phi(u))|\det D\Phi(u)|\,du.$$
> 若用微分形式，体积形式 $\omega=dx_1\wedge\cdots\wedge dx_n$ 的拉回为
> $$\Phi^*\omega=(\det D\Phi)\,du_1\wedge\cdots\wedge du_n.$$
> 这里无绝对值，因为微分形式携带定向；重积分处理的是非定向密度，故取绝对值。

> [!example] 习题
> 1. 设区域由 $xy=1,xy=2,y=x,y=2x$ 围成，求 $\iint_D (x^2+y^2)\,dxdy$。
> 2. 用换元 $u=x+y,\ v=x-y$ 计算正方形 $0\le x+y\le 1,\ 0\le x-y\le 1$ 上的积分 $\iint_D e^{x^2-y^2}\,dxdy$。
> 3. 讨论 $\Phi(r,\theta)=(r\cos\theta,r\sin\theta)$ 在 $\theta\in[0,2\pi]$ 时为什么只差一个零面积集合是一一映射；若 $\theta\in[0,4\pi]$ 会如何破坏公式。

> [!tip] 方法论：换元四步法
> 4. 选映射：区域边界可参数化或函数组合简化，如 $x^2+y^2$ 对应极坐标，边界 $xy$ 常数对应 $u=xy$。
> 5. 求 Jacobi 行列式：$J=\partial(x,y)/\partial(u,v)$，并判断符号。
> 6. 确定新区域：由原区域边界解出 $u,v$ 范围，检验映射单射性。
> 7. 代公式：被积函数复合，面积微元乘 $|J|$，计算累次积分。

> [!note] 总结
> 二重积分换元公式可压缩为
> $$dx\,dy=\left|\frac{\partial(x,y)}{\partial(u,v)}\right|du\,dv.$$
> 它的严格基础是 $C^1$ 映射的局部线性化和行列式作为面积伸缩率；实际使用时，关键是选对映射、正确求 $|J|$、确定新区域并保持单射性。
