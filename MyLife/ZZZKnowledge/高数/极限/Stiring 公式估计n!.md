> [!abstract] 定义：斯特林公式（Stirling's formula）
> 当 $n\to\infty$ 时，阶乘 $n!$ 的核心渐近展开为：
> $$n!\sim\sqrt{2\pi n}\left(\frac{n}{e}\right)^n$$
> 另外，为了方便应对带有对数运算的题目，您特别关心的**含 $\ln$ 的等价式**为：
> $$\ln(n!)\sim n\ln n - n$$
> 在实际考研运算中，当我们遇到 $\ln(n!)$ 时，可以直接将其替换为 $n\ln n - n$，从而使复杂的连乘结构立刻变成简单的加减结构。

> [!tip] 关键思想与理论延伸
> **1. 维度对齐思想**：阶乘 $n!$ 是离散的连乘结构，极难直接求极限。斯特林公式的作用是将这种“离散连乘”等价转化为“连续幂函数”，从而让 $n!$ 和 $n^n$、$2^n$ 等结构在指数层面上能够直接进行对齐比较。
> **2. 无穷大量级比较**：当面对 $2^n$、$n^n$ 和 $\ln^{10}n$ 混合的极限时，本质是比较“指数爆炸”、“幂函数增长”和“对数增长”的速度差距。在计算中，一眼就能看出底数小于 $1$ 的指数衰减项是决定极限收敛的绝对主力。
> **3. 方法论迁移**：斯特林公式虽然强大，但在处理形如 $\sqrt[n]{n!}$ 这类根式时容易变得繁琐。此时若引入**正项级数的比值和根值的等价关系**，可以避开公式记忆，直接通过构造数列算出答案，这是考研中隐藏极深但屡试不爽的妙招。

> [!question] 习题 1（对应您图片 1 的题目）
> 求极限：
> $$\lim_{n\to\infty}\frac{2^n\cdot(n!)\cdot\ln^{10}n}{n^n}$$
> 
> **解析（斯特林公式直接秒杀）**：
> 利用 $n!\sim\sqrt{2\pi n}\left(\frac{n}{e}\right)^n$，原式化为：
> $$\lim_{n\to\infty}\frac{2^n\cdot\sqrt{2\pi n}\cdot\left(\frac{n}{e}\right)^n\cdot\ln^{10}n}{n^n}$$
> 合并化简得：
> $$=\lim_{n\to\infty}\sqrt{2\pi n}\cdot\ln^{10}n\cdot\left(\frac{2}{e}\right)^n$$
> 由于底数 $\frac{2}{e}\approx0.736<1$，可见 $\left(\frac{2}{e}\right)^n$ 是**指数级衰减**，其衰减速度碾压了 $\sqrt{n}$ 和 $\ln^{10}n$ 的增长速度。因此最终极限为：
> $$\lim_{n\to\infty}\sqrt{2\pi n}\cdot\ln^{10}n\cdot\left(\frac{2}{e}\right)^n = 0$$

> [!question] 习题 2（对应您图片 2 的题目）
> 求极限：
> $$\lim_{n\to\infty}\frac{\sqrt[n]{n!}}{n}$$
> 
> **解法一（直接套用斯特林公式）**：
> 代入公式 $n!\sim\sqrt{2\pi n}\left(\frac{n}{e}\right)^n$，并计算其开 $n$ 次方：
> $$\lim_{n\to\infty}\frac{\left[\sqrt{2\pi n}\left(\frac{n}{e}\right)^n\right]^{\frac{1}{n}}}{n} = \lim_{n\to\infty}\frac{(2\pi n)^{\frac{1}{2n}}\cdot\frac{n}{e}}{n}$$
> 利用常用极限 $\lim_{n\to\infty} n^{\frac{1}{n}} = 1$，可得 $(2\pi n)^{\frac{1}{2n}}\to 1$。从而最终计算结果为：
> $$\lim_{n\to\infty}\frac{\sqrt[n]{n!}}{n} = \frac{1}{e}$$

> [!method] 替代解法总结（级数判别法转求极限，完全避开斯特林公式）
> 主人，这就是您特意嘱咐要加的**方法二**！面对这种带有 $\sqrt[n]{n!}$ 的结构，我们完全可以不用斯特林公式，而是利用**级数的比值与根值判别法的内在联系**。
> 
> **理论依据**：
> 对于正项数列 $a_n$，若 $\lim_{n\to\infty}\frac{a_{n+1}}{a_n}$ 存在，则必有如下等价关系：
> $$\lim_{n\to\infty}\sqrt[n]{a_n} = \lim_{n\to\infty}\frac{a_{n+1}}{a_n}$$
> 
> **应用题解步骤**：
> 令 $a_n = \frac{n!}{n^n}$，我们要求解的目标正是：
> $$\lim_{n\to\infty}\frac{\sqrt[n]{n!}}{n} = \lim_{n\to\infty}\sqrt[n]{a_n}$$
> 现在只需计算相邻两项的比值极限即可：
> $$\lim_{n\to\infty}\frac{a_{n+1}}{a_n} = \lim_{n\to\infty}\frac{\frac{(n+1)!}{(n+1)^{n+1}}}{\frac{n!}{n^n}}$$
> 展开并约去公因子 $n!$：
> $$= \lim_{n\to\infty}\frac{(n+1)\cdot n^n}{(n+1)\cdot(n+1)^n} = \lim_{n\to\infty}\left(\frac{n}{n+1}\right)^n$$
> 代入第二个重要极限结论：
> $$\lim_{n\to\infty}\left(\frac{n}{n+1}\right)^n = \lim_{n\to\infty}\frac{1}{\left(1+\frac{1}{n}\right)^n} = \frac{1}{e}$$
> 由于比值极限恰好是 $\frac{1}{e}$，因此原根值极限也等于 $\frac{1}{e}$，即：
> $$\lim_{n\to\infty}\frac{\sqrt[n]{n!}}{n} = \frac{1}{e}$$
> 
> **女仆提醒**：这种方法的核心精妙之处在于，**构造出 $a_n$ 后，利用 $a_{n+1}$ 比 $a_n$ 的展开，可以直接把难缠的 $n!$ 给完全抵消掉**。在忘记斯特林公式的情况下，此法是极其可靠的保底操作。

> [!tip] 延伸挑战与练习
> 主人，刚才用两种方法剖析了这道题，想必您现在已完全掌握了这两种思路的精髓。为了巩固成果，不妨试试下面这道稍微拔高的考研真题：
> $$\lim_{n\to\infty}\frac{(2n)!}{(n!)^2\cdot4^n}$$
> 
> **思路点拨**：
> 您可以直接拿出斯特林公式，分别展开分子的 $(2n)!$ 和分母的 $n!$，看看底数和幂次是如何约掉的；
> 同时，您也可以试试刚学的**构造 $a_n$ 计算比值**的方法，两种算法得出的最终常数应该是完全一致的。如果有不懂的，女仆随时为您继续解答。

