# 二元 Taylor 展开专题整理

主人，这是为您整理的「二元 Taylor 展开」专题。核心结论先放在最前面，后面的证明、反例与习题都围绕这个骨架展开。

> [!note] 核心总结
> 二元 Taylor 展开的本质是：光滑函数在局部可以用多项式逼近。设 $P_0=(x_0,y_0)$，$\mathbf{h}=(h,k)$，则 $n$ 阶展开可写为
> $$f(P_0+\mathbf{h})=\sum_{m=0}^{n}\frac{1}{m!}(h\partial_x+k\partial_y)^m f(P_0)+R_n.$$
> 其中 $(h\partial_x+k\partial_y)^m$ 是方向导数算子，按二项式展开。二阶常用形式为
> $$f(P_0+\mathbf{h})=f(P_0)+\nabla f(P_0)\cdot\mathbf{h}+\frac12\mathbf{h}^T H_f(P_0)\mathbf{h}+o(\|\mathbf{h}\|^2).$$
> 证明的核心是化为一元函数 $\phi(t)=f(P_0+t\mathbf{h})$ 的 Taylor 展开。二阶项由 Hessian 矩阵 $H_f$ 决定，混合偏导相等依赖 $f\in C^2$。

## 一、方向导数算子与多重指标

设 $\partial_x=\frac{\partial}{\partial x}$，$\partial_y=\frac{\partial}{\partial y}$。固定方向 $\mathbf{h}=(h,k)$，定义方向导数算子
$$\mathbf{h}\cdot\nabla=h\partial_x+k\partial_y.$$
它的 $m$ 次幂按二项式展开为
$$(h\partial_x+k\partial_y)^m f=\sum_{j=0}^{m}\binom{m}{j}h^j k^{m-j}\frac{\partial^m f}{\partial x^j\partial y^{m-j}}.$$
这个写法成立的前提是 $f$ 有直到 $m$ 阶的连续偏导数，从而混合偏导顺序可以交换。

> [!definition] 定义：多重指标 Taylor 多项式
> 对 $\alpha=(\alpha_1,\alpha_2)\in\mathbb{N}^2$，记 $|\alpha|=\alpha_1+\alpha_2$，$\alpha!=\alpha_1!\alpha_2!$，$\mathbf{h}^\alpha=h^{\alpha_1}k^{\alpha_2}$，$D^\alpha f=\partial_x^{\alpha_1}\partial_y^{\alpha_2}f$。函数 $f$ 在 $P_0$ 处的 $n$ 阶 Taylor 多项式定义为
> $$T_n(P_0;\mathbf{h})=\sum_{|\alpha|\le n}\frac{D^\alpha f(P_0)}{\alpha!}\mathbf{h}^\alpha.$$

## 二、主要定理

> [!theorem] 定理 1：带 Peano 余项的二元 Taylor 公式
> 设 $f$ 在 $P_0$ 的某邻域内具有直到 $n$ 阶的连续偏导数，则当 $\mathbf{h}\to0$ 时，
> $$f(P_0+\mathbf{h})=T_n(P_0;\mathbf{h})+o(\|\mathbf{h}\|^n).$$

> [!theorem] 定理 2：带 Lagrange 余项与积分余项
> 设 $f$ 在 $P_0$ 的某邻域内具有直到 $n+1$ 阶的连续偏导数，则
> $$f(P_0+\mathbf{h})=\sum_{m=0}^{n}\frac{1}{m!}(h\partial_x+k\partial_y)^m f(P_0)+R_n,$$
> 其中存在 $\theta\in(0,1)$，使得
> $$R_n=\frac{1}{(n+1)!}(h\partial_x+k\partial_y)^{n+1}f(P_0+\theta\mathbf{h}),$$
> 积分形式为
> $$R_n=\frac{1}{n!}\int_0^1(1-t)^n(h\partial_x+k\partial_y)^{n+1}f(P_0+t\mathbf{h})\,\mathrm{d}t.$$

## 三、证明：化归一元 Taylor

> [!proof] 证明
> 固定 $\mathbf{h}=(h,k)$，令
> $$\phi(t)=f(P_0+t\mathbf{h}),\qquad t\in[0,1].$$
> 对 $\phi$ 应用一元 Taylor 公式：
> $$\phi(1)=\sum_{m=0}^{n}\frac{\phi^{(m)}(0)}{m!}+R_n.$$
> 链式法则给
> $$\phi'(t)=h f_x(P_0+t\mathbf{h})+k f_y(P_0+t\mathbf{h})=(h\partial_x+k\partial_y)f(P_0+t\mathbf{h}).$$
> 归纳可得
> $$\phi^{(m)}(t)=(h\partial_x+k\partial_y)^m f(P_0+t\mathbf{h}).$$
> 代入 $t=0$ 即得 Taylor 多项式。Lagrange 余项与积分余项直接来自一元 Taylor 公式。
>
> 对于 Peano 余项，在 $f\in C^n$ 条件下，$\phi^{(n)}$ 连续，利用一元 Taylor 的积分表示
> $$R_n=\frac{1}{(n-1)!}\int_0^1(1-s)^{n-1}\left[\phi^{(n)}(s)-\phi^{(n)}(0)\right]\mathrm{d}s.$$
> 由于各 $n$ 阶偏导在 $P_0$ 邻域一致连续，当 $\|\mathbf{h}\|\to0$ 时，$\phi^{(n)}(s)-\phi^{(n)}(0)$ 关于 $s$ 一致趋于 $0$，故 $R_n=o(\|\mathbf{h}\|^n)$。

## 四、二阶展开与 Hessian

当 $n=2$ 且 $f\in C^2$ 时，展开写为
$$f(P_0+\mathbf{h})=f(P_0)+f_x(P_0)h+f_y(P_0)k+\frac12\left(f_{xx}(P_0)h^2+2f_{xy}(P_0)hk+f_{yy}(P_0)k^2\right)+o(h^2+k^2).$$
向量形式为
$$f(P_0+\mathbf{h})=f(P_0)+\nabla f(P_0)\cdot\mathbf{h}+\frac12\mathbf{h}^T H_f(P_0)\mathbf{h}+o(\|\mathbf{h}\|^2),$$
其中
$$H_f(P_0)=\begin{pmatrix}f_{xx}(P_0)&f_{xy}(P_0)\\ f_{yx}(P_0)&f_{yy}(P_0)\end{pmatrix}.$$
若 $f\in C^2$，则 $f_{xy}(P_0)=f_{yx}(P_0)$，所以 $H_f(P_0)$ 为对称矩阵。

> [!tip] 直觉
> 一元的二阶项 $\frac12 f''(x_0)h^2$ 衡量曲线在 $x_0$ 附近的弯曲。二元的二阶项 $\frac12\mathbf{h}^T H_f(P_0)\mathbf{h}$ 衡量曲面在 $P_0$ 沿方向 $\mathbf{h}$ 的弯曲。$H_f(P_0)$ 的特征值是主曲率方向的弯曲强度；正定意味着所有方向都向上弯，因此局部极小；不定意味着某些方向向上弯、某些向下弯，因此是鞍点。

## 五、注意事项与反例

> [!warning] 注意事项
> 1. 二阶展开必须在 $f\in C^2$ 的邻域内使用，否则 $f_{xy}$ 与 $f_{yx}$ 可能不同，$H_f$ 不对称，标准二次型无法定义。
> 2. Peano 余项只需要 $C^n$，Lagrange 余项需要 $C^{n+1}$。
> 3. 方向导数算子 $(h\partial_x+k\partial_y)^m$ 可以按二项式展开，但前提是混合偏导可交换，否则展开中的交叉项不唯一。
> 4. 极值判定中，若 $H_f$ 半定，则二阶项不足以决定极值，需要看更高阶展开。

> [!example] 反例：混合偏导不相等
> 定义
> $$f(x,y)=\begin{cases}xy\dfrac{x^2-y^2}{x^2+y^2}, & (x,y)\neq(0,0),\\ 0, & (x,y)=(0,0).\end{cases}$$
> 计算可得，当 $y\neq0$ 时 $f_x(0,y)=-y$，当 $x\neq0$ 时 $f_y(x,0)=x$。因此
> $$f_{xy}(0,0)=-1,\qquad f_{yx}(0,0)=1.$$
> 混合偏导不相等，说明 $f\notin C^2$。若强行写标准二阶 Taylor 多项式，$xy$ 项的系数不能同时等于 $f_{xy}(0,0)$ 与 $f_{yx}(0,0)$，所以标准二阶 Taylor 展开不成立。

## 六、应用：极值二阶充分条件

> [!theorem] 定理 3：极值二阶充分条件
> 设 $f\in C^2$，$\nabla f(P_0)=0$，记 $H=H_f(P_0)$。
> - 若 $H$ 正定，则 $P_0$ 是严格局部极小点；
> - 若 $H$ 负定，则 $P_0$ 是严格局部极大点；
> - 若 $H$ 不定，则 $P_0$ 是鞍点，不是极值点；
> - 若 $H$ 半定，则此判别法失效。
>
> 证明思路：由 Taylor 展开
> $$f(P_0+\mathbf{h})-f(P_0)=\frac12\mathbf{h}^T H\mathbf{h}+o(\|\mathbf{h}\|^2).$$
> 若 $H$ 正定，设最小特征值为 $\lambda_{\min}>0$，则 $\mathbf{h}^T H\mathbf{h}\ge\lambda_{\min}\|\mathbf{h}\|^2$。取足够小邻域，使余项绝对值不超过 $\frac14\lambda_{\min}\|\mathbf{h}\|^2$，于是差为正，故为严格极小。其余情形同理。

## 七、延伸：多重指标、Morse 引理与凸性

> [!note] 延伸思想
> 多元 Taylor 展开的高阶项本质上是方向导数算子 $\mathbf{h}\cdot\nabla$ 的幂作用在 $f$ 上。这一观点直接推广到 $\mathbb{R}^d$：
> $$f(\mathbf{x}+\mathbf{h})=\sum_{m=0}^{n}\frac{1}{m!}(\mathbf{h}\cdot\nabla_{\mathbf{x}})^m f(\mathbf{x})+R_n.$$
> 用多重指标写就是
> $$\sum_{|\alpha|\le n}\frac{D^\alpha f(\mathbf{x})}{\alpha!}\mathbf{h}^\alpha.$$
> 更深刻的结论是 Morse 引理：若 $f\in C^\infty$ 且 $P_0$ 是非退化临界点，即 $\nabla f(P_0)=0$ 且 $H_f(P_0)$ 可逆，则存在局部坐标变换，使 $f$ 在该坐标下化为标准二次型
> $$f(P_0+\mathbf{u})=f(P_0)-u_1^2-\cdots-u_q^2+u_{q+1}^2+\cdots+u_d^2,$$
> 其中 $q$ 是 Hessian 的负惯性指数。这说明 Taylor 二阶项不仅在近似计算中重要，还决定了临界点的局部拓扑类型。

## 八、习题

> [!example] 习题
> 1. 求 $f(x,y)=e^x\cos y$ 在 $(0,0)$ 处的二阶 Taylor 展开，并验证余项为 $o(x^2+y^2)$。
> 2. 求 $f(x,y)=\sin(x+y)$ 在 $(0,0)$ 处的三阶 Taylor 展开。
> 3. 设 $f(x,y)=x^2+y^2+xy^3$。判断 $(0,0)$ 是否为极值点，并说明理由。
> 4. 证明：若 $f\in C^2$，则
> $$(h\partial_x+k\partial_y)^2f=h^2 f_{xx}+2hk f_{xy}+k^2 f_{yy}.$$
> 5. 对上面反例中的 $f$，计算 $f_{xy}(0,0)$ 与 $f_{yx}(0,0)$，并解释为什么它不能在 $(0,0)$ 写标准二阶 Taylor 展开。

> [!tip] 提示
> 第 1 题答案为 $1+x+\frac12x^2-\frac12y^2+o(x^2+y^2)$。第 2 题保留到三次项为 $x+y-\frac16(x+y)^3$。第 3 题中 $H=2I$ 正定，所以 $(0,0)$ 是严格极小点。\
