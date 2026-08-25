# Cauchy收敛准则全总结

> [!abstract] 核心思想
> 柯西准则的本质：不依赖极限值本身，仅通过“充分靠后的项之间是否任意接近”来判断收敛性。它是实数完备性的等价表述，也是处理抽象空间收敛问题的通用工具。
> 
> 充分性的关键在于：柯西列必有界，有界必有收敛子列，进而原序列收敛。这一链条依赖于实数系的完备性（确界原理或单调有界定理等）。

## 1. 数列的Cauchy收敛准则

> [!definition] 定义：柯西列
> 数列 $\{x_n\}$ 称为**柯西列**（基本列），若对任意 $\varepsilon>0$，存在 $N\in\mathbb{N}$，当 $m,n>N$ 时，有 
> $$|x_m-x_n|<\varepsilon.$$

> [!theorem] 定理（数列柯西收敛准则）
> 数列 $\{x_n\}$ 收敛的充要条件是 $\{x_n\}$ 为柯西列。

**证明**  
（必要性）设 $\lim_{n\to\infty}x_n=a$。对任意 $\varepsilon>0$，存在 $N$，当 $n>N$ 时 $|x_n-a|<\frac{\varepsilon}{2}$。于是当 $m,n>N$ 时，
$$
|x_m-x_n|\le |x_m-a|+|x_n-a|<\frac{\varepsilon}{2}+\frac{\varepsilon}{2}=\varepsilon.
$$

（充分性）设 $\{x_n\}$ 为柯西列。  
先证有界：取 $\varepsilon=1$，存在 $N$，当 $n>N$ 时 $|x_n-x_{N+1}|<1$，故 $|x_n|\le |x_n-x_{N+1}|+|x_{N+1}|<1+|x_{N+1}|$，前 $N$ 项有限，所以数列有界。  
由致密性定理（有界数列必有收敛子列），存在子列 $\{x_{n_k}\}$ 收敛于 $a$。  
再证原序列收敛于 $a$：对任意 $\varepsilon>0$，由柯西条件存在 $N_1$，当 $m,n>N_1$ 时 $|x_m-x_n|<\frac{\varepsilon}{2}$；由子列收敛存在 $K$，当 $k>K$ 时 $|x_{n_k}-a|<\frac{\varepsilon}{2}$。取 $k$ 充分大使 $n_k>N_1$ 且 $k>K$，则对任意 $n>N_1$，
$$
|x_n-a|\le |x_n-x_{n_k}|+|x_{n_k}-a|<\frac{\varepsilon}{2}+\frac{\varepsilon}{2}=\varepsilon.
$$
故 $\lim_{n\to\infty}x_n=a$。 $\square$

> [!tip] 直观理解
> 柯西列意味着“尾巴上的项挤在一起”。如果存在极限，它们当然挤在一起；反过来，实数系的完备性保证“挤在一起的项”必有极限。有理数系中，柯西列不一定收敛（例如十进制展开逼近 $\sqrt{2}$ 的有理数列），这正是实数系完备性的体现。

## 2. 级数的Cauchy收敛准则

> [!theorem] 定理（级数柯西收敛准则）
> 级数 $\sum_{n=1}^{\infty}a_n$ 收敛的充要条件是：对任意 $\varepsilon>0$，存在 $N$，当 $m>n>N$ 时，
> $$
> \left|\sum_{k=n+1}^{m}a_k\right|<\varepsilon.
> $$

**证明**  
设部分和 $S_n=\sum_{k=1}^{n}a_k$。级数收敛等价于 $\{S_n\}$ 收敛。应用数列柯西准则，$\{S_n\}$ 为柯西列等价于：对任意 $\varepsilon>0$，存在 $N$，当 $m>n>N$ 时，
$$
|S_m-S_n|=\left|\sum_{k=n+1}^{m}a_k\right|<\varepsilon.
$$
因此命题成立。 $\square$

> [!warning] 逆否命题（常用判别发散）
> 若存在 $\varepsilon_0>0$，对任意 $N$，都能找到 $m>n>N$ 使得
> $$
> \left|\sum_{k=n+1}^{m}a_k\right|\ge \varepsilon_0,
> $$
> 则级数发散。

> [!example] 应用：证明调和级数发散
> 取 $\varepsilon_0=\frac{1}{2}$。对任意 $N$，令 $n=N+1$，$m=2N$（假设 $N$ 足够大），则
> $$
> \sum_{k=N+1}^{2N}\frac{1}{k} \ge N\cdot \frac{1}{2N}=\frac{1}{2}.
> $$
> 因此不满足柯西条件，故 $\sum_{n=1}^{\infty}\frac{1}{n}$ 发散。

## 3. 函数极限的Cauchy收敛准则

> [!theorem] 定理（函数极限的柯西准则，$x\to x_0$ 型）
> 极限 $\lim_{x\to x_0}f(x)$ 存在的充要条件是：对任意 $\varepsilon>0$，存在 $\delta>0$，当 $0<|x'-x_0|<\delta$ 且 $0<|x''-x_0|<\delta$ 时，
> $$
> |f(x')-f(x'')|<\varepsilon.
> $$

**证明**  
（必要性）设极限为 $A$。对任意 $\varepsilon>0$，存在 $\delta>0$，当 $0<|x-x_0|<\delta$ 时 $|f(x)-A|<\frac{\varepsilon}{2}$。若 $x',x''$ 满足条件，则
$$
|f(x')-f(x'')|\le |f(x')-A|+|A-f(x'')|<\varepsilon.
$$

（充分性）利用归结原则（海涅定理）。任取数列 $\{x_n\}$ 满足 $x_n\to x_0$ 且 $x_n\neq x_0$。由柯西条件，对任意 $\varepsilon>0$，存在 $\delta>0$；因 $x_n\to x_0$，存在 $N$，当 $m,n>N$ 时 $0<|x_m-x_0|<\delta$、$0<|x_n-x_0|<\delta$，于是 $|f(x_m)-f(x_n)|<\varepsilon$。故 $\{f(x_n)\}$ 为柯西列，从而收敛。再证明极限唯一：若两个趋于 $x_0$ 的数列对应函数值极限分别为 $A,B$，构造交错数列可知 $A=B$。故函数极限存在。 $\square$

> [!note] $x\to\infty$ 型的柯西准则
> 极限 $\lim_{x\to\infty}f(x)$ 存在的充要条件是：对任意 $\varepsilon>0$，存在 $X>0$，当 $x',x''>X$ 时，
> $$
> |f(x')-f(x'')|<\varepsilon.
> $$

## 4. 反常积分的Cauchy收敛准则

> [!theorem] 定理（无穷限反常积分的柯西准则）
> 积分 $\displaystyle \int_a^{+\infty}f(x)\,dx$ 收敛的充要条件是：对任意 $\varepsilon>0$，存在 $A\ge a$，当 $A_1,A_2>A$ 时，
> $$
> \left|\int_{A_1}^{A_2}f(x)\,dx\right|<\varepsilon.
> $$

**证明**  
令 $F(A)=\int_a^{A}f(x)\,dx$。无穷积分收敛等价于 $\lim_{A\to+\infty}F(A)$ 存在。由函数极限 $x\to\infty$ 的柯西准则，后者等价于：对任意 $\varepsilon>0$，存在 $X>0$，当 $A_1,A_2>X$ 时，$|F(A_2)-F(A_1)|<\varepsilon$，即
$$
\left|\int_{A_1}^{A_2}f(x)\,dx\right|<\varepsilon.
$$
结论成立。 $\square$

> [!tip] 类比
> 反常积分的柯西准则与级数柯西准则结构相同：级数考虑“一段和”，积分考虑“一段积分”，本质都是尾部量趋于零。

## 5. 函数项级数一致收敛的Cauchy准则

> [!definition] 一致收敛
> 函数项级数 $\sum u_n(x)$ 在区间 $I$ 上一致收敛到 $S(x)$，若对任意 $\varepsilon>0$，存在 $N$（仅与 $\varepsilon$ 有关，与 $x$ 无关），当 $n>N$ 时，对所有 $x\in I$ 都有
> $$
> |S_n(x)-S(x)|<\varepsilon.
> $$

> [!theorem] 定理（一致收敛的柯西准则）
> 函数项级数 $\sum u_n(x)$ 在区间 $I$ 上一致收敛的充要条件是：对任意 $\varepsilon>0$，存在 $N$，当 $m>n>N$ 时，对所有 $x\in I$，
> $$
> \left|\sum_{k=n+1}^{m}u_k(x)\right|<\varepsilon.
> $$

**证明**  
（必要性）设 $S_n(x)\rightrightarrows S(x)$。对任意 $\varepsilon>0$，存在 $N$，当 $n>N$ 时，对所有 $x\in I$ 有 $|S_n(x)-S(x)|<\frac{\varepsilon}{2}$。当 $m>n>N$ 时，
$$
\left|\sum_{k=n+1}^{m}u_k(x)\right|=|S_m(x)-S_n(x)|\le |S_m(x)-S(x)|+|S(x)-S_n(x)|<\varepsilon.
$$

（充分性）已知对任意 $\varepsilon>0$，存在 $N$，当 $m>n>N$ 时，对所有 $x\in I$ 有 $|S_m(x)-S_n(x)|<\varepsilon$。  
固定 $x$，数列 $\{S_n(x)\}$ 为柯西列，故逐点收敛，设极限函数为 $S(x)$。  
在上式中固定 $n>N$，令 $m\to\infty$，得到对所有 $x\in I$，有 $|S(x)-S_n(x)|\le \varepsilon$。因此 $S_n(x)\rightrightarrows S(x)$。 $\square$

> [!important] 一致收敛与逐点收敛的区别
> 逐点收敛：$N$ 可能依赖于 $x$；一致收敛：$N$ 只依赖于 $\varepsilon$。柯西准则形式正是将这种“一致性”量化为对 $x$ 的一致控制。

## 方法论总结

1. **证明收敛**：若要证明某序列/级数收敛，可尝试直接验证柯西条件，尤其当极限值未知时。
2. **证明发散**：取一个特定的 $\varepsilon_0$（常取 $\frac{1}{2}$ 或 $1$），构造一列 $m,n$ 使得“一段和/差”始终不小于 $\varepsilon_0$，从而违背柯西条件。
3. **完备性的角色**：柯西准则的充分性不是逻辑上的平凡结论，它依赖于实数系的完备性。在更一般的空间中，柯西列不一定收敛（例如有理数空间），因此柯西准则成为定义“完备空间”的标准。
4. **一致性的体现**：函数项级数的一致收敛柯西准则中，$N$ 不依赖 $x$ 是关键，这也是它与逐点收敛柯西条件的唯一区别。

## 习题

1. 用柯西准则证明：若 $\sum a_n$ 收敛，则 $\lim_{n\to\infty}a_n=0$。
2. 用柯西准则证明：$\sum_{n=1}^{\infty}\frac{1}{n^2}$ 收敛（提示：利用 $\frac{1}{k^2}<\frac{1}{k(k-1)}$ 放缩，证明部分和是柯西列）。
3. 判断下列命题真假并说明理由：若对任意 $\varepsilon>0$，存在 $N$，当 $n>N$ 时 $|a_{n+1}-a_n|<\varepsilon$，则数列 $\{a_n\}$ 收敛。（假，例如 $a_n=\ln n$）
4. 设 $f(x)=\sin\frac{1}{x}$，用柯西准则说明 $\lim_{x\to 0}f(x)$ 不存在。