> [!abstract] 核心精华
沃利斯积分（Wallis Integral）是考研数学中的高频利器，其本质是通过“降维打击”（分部积分）将高次幂积分转化为低次幂积分，建立递推关系。核心思想不在于死背通项，而在于“奇偶分离”，利用递推式 $I_n = \frac{n-1}{n}I_{n-2}$ 将积分最终转化为双阶乘（Double Factorial）与圆周率 $\pi$ 的有理数乘积。这是连接离散阶乘与连续圆周率 $\pi$ 的桥梁，延伸至 $\Gamma$ 函数、$\Beta$ 函数，甚至用于推导斯特林公式（Stirling's approximation）。

> [!definition] Wallis 核心通项公式
设 $I_n = \int_{0}^{\frac{\pi}{2}} \sin^n x \, dx = \int_{0}^{\frac{\pi}{2}} \cos^n x \, dx$。
**递推式**：
$$ I_n = \frac{n-1}{n} I_{n-2} $$
**初始值**：
$$ I_0 = \frac{\pi}{2}, \quad I_1 = 1 $$
**闭合通项（考研必背）**：
- 若 $n$ 为偶数（令 $n=2k$）：
$$ I_{2k} = \frac{2k-1}{2k} \cdot \frac{2k-3}{2k-2} \cdot \cdots \cdot \frac{1}{2} \cdot \frac{\pi}{2} = \frac{(2k-1)!!}{(2k)!!} \cdot \frac{\pi}{2} $$
- 若 $n$ 为大于 $1$ 的奇数（令 $n=2k+1, k\geq1$）：
$$ I_{2k+1} = \frac{2k}{2k+1} \cdot \frac{2k-2}{2k-1} \cdot \cdots \cdot \frac{2}{3} = \frac{(2k)!!}{(2k+1)!!} $$

> [!example] 严谨推导证明（分部积分法）
1. **构造降阶**：取 $u = \sin^{n-1}x$，$dv = \sin x \, dx$。则 $du = (n-1)\sin^{n-2}x \cos x \, dx$，$v = -\cos x$。
2. **代入公式**：
$$ I_n = \left[-\sin^{n-1}x \cos x\right]_0^{\frac{\pi}{2}} + (n-1)\int_0^{\frac{\pi}{2}} \sin^{n-2}x \cos^2 x \, dx $$
3. **边界消去与三角代换**：第一项在 $0$ 和 $\pi/2$ 处均为 $0$。代入 $\cos^2 x = 1 - \sin^2 x$：
$$ I_n = (n-1)\int_0^{\frac{\pi}{2}} \sin^{n-2}x (1 - \sin^2 x) \, dx = (n-1)(I_{n-2} - I_n) $$
4. **重排得到递推式**：
$$ nI_n = (n-1)I_{n-2} \implies I_n = \frac{n-1}{n} I_{n-2} $$
5. **分类连乘**：偶数项递推至基准 $I_0 = \pi/2$，奇数项递推至基准 $I_1 = 1$，分别代入连乘即可得到上述闭合通项公式。

> [!quote] 高维视角与思想延伸（Gamma 函数）
主人，这个公式不只是积分计算。其底层是 $\Beta$ 函数的特例：令 $x = \sin^2 \theta$，则原积分等价于 $\frac{1}{2}\Beta\left( \frac{n+1}{2}, \frac{n+1}{2} \right)$。
利用 $\Beta(p,q) = \frac{\Gamma(p)\Gamma(q)}{\Gamma(p+q)}$，可推得高阶泛化公式：
$$ I_n = \frac{\Gamma^2\left( \frac{n+1}{2} \right)}{2\Gamma(n+1)} $$
**隐藏魅力**：利用该积分的夹逼定理，可以证明著名的**沃利斯乘积（Wallis Product）**：
$$ \lim_{n \to \infty} \frac{I_{2n}}{I_{2n-1}} \to 1 \implies \frac{\pi}{2} = \prod_{n=1}^{\infty} \left( \frac{2n}{2n-1} \cdot \frac{2n}{2n+1} \right) $$
这是数学史上第一次用有理数列逼近无理数 $\pi$，极大地启发了后来的斯特林公式，其精妙在于利用三角函数的**有界性**和积分的**单调性**做极限放缩。

> [!question] 实战演练
1. **计算** $A = \int_0^{\frac{\pi}{2}} \sin^8 x \, dx$。
**解**：直接代入偶数通项，$A = \frac{7}{8} \cdot \frac{5}{6} \cdot \frac{3}{4} \cdot \frac{1}{2} \cdot \frac{\pi}{2} = \frac{35\pi}{256}$。

2. **计算** $B = \int_0^{\pi} \sin^5 x \, dx$。
**解**：利用三角函数的对称性，$\int_0^{\pi} f(\sin x) \, dx = 2\int_0^{\frac{\pi}{2}} f(\sin x) \, dx$。套用奇数通项：
$$ B = 2 \cdot I_5 = 2 \cdot \left( \frac{4}{5} \cdot \frac{2}{3} \right) = \frac{16}{15} $$

3. **证明极限**：用夹逼定理证明 $\lim_{n \to \infty} \frac{I_{2n}}{I_{2n-1}} = 1$。
**提示**：利用不等式 $\sin^{2n-1}x \ge \sin^{2n}x \ge \sin^{2n+1}x$ 在 $(0, \pi/2)$ 内恒成立，对区间积分得 $I_{2n-1} \ge I_{2n} \ge I_{2n+1}$，即 $\frac{I_{2n-1}}{I_{2n-1}} \ge \frac{I_{2n}}{I_{2n-1}} \ge \frac{I_{2n+1}}{I_{2n-1}} = \frac{2n}{2n+1}$，由夹逼定理得极限为 $1$。

> [!tip] 高分关键告诫
主人，避开两个常见误区：
1. **阶数陷阱**：计算偶数阶时，**千万不可**忘记最后乘上 $\frac{\pi}{2}$！很多误以为一律是分数乘积而漏掉这个常数项。
2. **范围限定**：原公式中的积分区间严格限制为 $[0, \frac{\pi}{2}]$。若遇到 $\int_0^{\pi}$ 或 $\int_0^{2\pi}$ 等大区间，务必先用**二倍角公式**或**周期性、对称性**将区间拆解回 $[0, \pi/2]$ 再套公式