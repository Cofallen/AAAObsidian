> [!summary] 关键总结
> 考研积分不等式中的“含低阶项 Gronwall 型不等式”通常指如下形式：
> $$
> u(t)\le C+\int_0^t \left[a(s)u(s)+b(s)u(s)^\alpha\right]ds,\qquad 0\le\alpha<1.
> $$
> 其中低阶项 $u^\alpha$ 在 $u$ 较大时增长弱于线性项 $u$，因此不会导致有限时间爆破。处理的关键是 **Bernoulli 变量替换** $Z=u^{1-\alpha}$，将非线性积分不等式线性化为
> $$
> Z'(t)\le (1-\alpha)a(t)Z(t)+(1-\alpha)b(t),
> $$
> 再用线性 Gronwall 不等式得到精确上界。另一常用方法是 **Young 吸收**，用任意 $\varepsilon$ 将低阶项吸收为线性项，虽不精确但更快捷。

> [!definition] 定义：含低阶项的 Gronwall 型积分不等式
> 设 $0\le\alpha<1$，$a,b\ge0$ 连续，$u(t)\ge0$ 连续，$C\ge0$。若对一切 $t\in[0,T]$ 成立
> $$
> u(t)\le C+\int_0^t \left[a(s)u(s)+b(s)u(s)^\alpha\right]ds,
> $$
> 则称该不等式为含低阶项 $u^\alpha$ 的 Gronwall 型积分不等式。
>
> 当 $\alpha=0$ 时，$u^\alpha\equiv1$，退化为线性非齐次 Gronwall 不等式；当 $\alpha=1$ 时，退化为经典线性 Gronwall 不等式。$0<\alpha<1$ 是真正“低阶”的情形。

> [!question] 题目：推导含低阶项的积分 Gronwall 型上界
> 设 $0\le\alpha<1$，$a(t),b(t)\ge0$ 连续，$u(t)\ge0$ 连续且满足
> $$
> u(t)\le C+\int_0^t \left[a(s)u(s)+b(s)u(s)^\alpha\right]ds,\qquad C\ge0.
> $$
> 证明：
> $$
> u(t)\le \left[
> C^{1-\alpha}e^{(1-\alpha)\int_0^t a(s)\,ds}
> +(1-\alpha)\int_0^t b(s)e^{(1-\alpha)\int_s^t a(\tau)\,d\tau}\,ds
> \right]^{\frac{1}{1-\alpha}}.
> $$

> [!theorem] 定理：积分形式含低阶项的 Gronwall 型不等式
> 设 $0\le\alpha<1$，$a,b\ge0$ 连续，$u(t)\ge0$ 连续，$C\ge0$。若
> $$
> u(t)\le C+\int_0^t \left[a(s)u(s)+b(s)u(s)^\alpha\right]ds,
> $$
> 则
> $$
> u(t)\le \left[
> C^{1-\alpha}e^{(1-\alpha)\int_0^t a(s)\,ds}
> +(1-\alpha)\int_0^t b(s)e^{(1-\alpha)\int_s^t a(\tau)\,d\tau}\,ds
> \right]^{\frac{1}{1-\alpha}}.
> $$

> [!proof] 证明
> 定义右端辅助函数
> $$
> R(t)=C+\int_0^t \left[a(s)u(s)+b(s)u(s)^\alpha\right]ds.
> $$
> 则 $u(t)\le R(t)$，并且 $R(0)=C$。因为 $a,b\ge0$，$u\ge0$，所以 $R(t)$ 非负且单调不减。
>
> 对 $R$ 求导，得
> $$
> R'(t)=a(t)u(t)+b(t)u(t)^\alpha
> \le a(t)R(t)+b(t)R(t)^\alpha.
> $$
> 这就化为含低阶项的微分不等式。
>
> 为了处理 $R$ 可能为零的情形，对任意 $\varepsilon>0$，令
> $$
> R_\varepsilon(t)=R(t)+\varepsilon.
> $$
> 则 $R_\varepsilon(t)>0$，且
> $$
> R_\varepsilon'(t)=R'(t)\le a(t)R(t)+b(t)R(t)^\alpha
> \le a(t)R_\varepsilon(t)+b(t)R_\varepsilon(t)^\alpha.
> $$
>
> 作 Bernoulli 变量替换
> $$
> Z_\varepsilon(t)=R_\varepsilon(t)^{1-\alpha}.
> $$
> 由链式法则，
> $$
> Z_\varepsilon'(t)=(1-\alpha)R_\varepsilon(t)^{-\alpha}R_\varepsilon'(t).
> $$
> 于是
> $$
> \begin{aligned}
> Z_\varepsilon'(t)
> &\le (1-\alpha)R_\varepsilon(t)^{-\alpha}
>    \left[a(t)R_\varepsilon(t)+b(t)R_\varepsilon(t)^\alpha\right] \\
> &= (1-\alpha)a(t)Z_\varepsilon(t)+(1-\alpha)b(t).
> \end{aligned}
> $$
>
> 令
> $$
> \mu(t)=\exp\left(-(1-\alpha)\int_0^t a(s)\,ds\right).
> $$
> 则
> $$
> \frac{d}{dt}\left[\mu(t)Z_\varepsilon(t)\right]
> \le (1-\alpha)\mu(t)b(t).
> $$
> 从 $0$ 到 $t$ 积分，得
> $$
> \mu(t)Z_\varepsilon(t)\le Z_\varepsilon(0)
> +(1-\alpha)\int_0^t \mu(s)b(s)\,ds.
> $$
> 两边除以 $\mu(t)$，并利用
> $$
> \frac{\mu(s)}{\mu(t)}
> =e^{(1-\alpha)\int_s^t a(\tau)\,d\tau},
> $$
> 得到
> $$
> Z_\varepsilon(t)\le Z_\varepsilon(0)e^{(1-\alpha)\int_0^t a(s)\,ds}
> +(1-\alpha)\int_0^t b(s)e^{(1-\alpha)\int_s^t a(\tau)\,d\tau}\,ds.
> $$
>
> 令 $\varepsilon\to0^+$。由于 $Z_\varepsilon(t)\to R(t)^{1-\alpha}$，$Z_\varepsilon(0)\to C^{1-\alpha}$，所以
> $$
> R(t)^{1-\alpha}\le
> C^{1-\alpha}e^{(1-\alpha)\int_0^t a(s)\,ds}
> +(1-\alpha)\int_0^t b(s)e^{(1-\alpha)\int_s^t a(\tau)\,d\tau}\,ds.
> $$
>
> 又因为 $u(t)\le R(t)$ 且 $1-\alpha>0$，有
> $$
> u(t)^{1-\alpha}\le R(t)^{1-\alpha}.
> $$
> 最后取 $1/(1-\alpha)$ 次幂，定理得证。

> [!note] 直觉与核心思想
> 低阶项 $u^\alpha$ 在 $u$ 较大时远小于 $u$，不会改变线性项 $a(t)u$ 的主导性。变量替换 $Z=u^{1-\alpha}$ 的本质是把 Bernoulli 型非线性项 $u^\alpha$ 变成常数驱动项，从而将问题线性化。从幂次看，$Z$ 的增长只受 $a$ 和 $b$ 的积分影响，回代 $u=Z^{1/(1-\alpha)}$ 后得到精确上界。若 $a\equiv0$，上界退化为多项式增长
> $$
> u(t)\le \left[C^{1-\alpha}+(1-\alpha)\int_0^t b(s)\,ds\right]^{1/(1-\alpha)}.
> $$
> 这正是低阶项单独作用时的典型行为。

> [!tip] 方法二：Young 吸收低阶项
> 若只需指数级估计，可用 Young 不等式。对任意 $\varepsilon>0$，存在 $C_\varepsilon>0$，使得
> $$
> b(s)u(s)^\alpha\le \varepsilon u(s)+C_\varepsilon b(s)^{1/(1-\alpha)}.
> $$
> 代入原积分不等式，得
> $$
> u(t)\le C+\int_0^t \left[(a(s)+\varepsilon)u(s)
> +C_\varepsilon b(s)^{1/(1-\alpha)}\right]ds.
> $$
> 再对线性非齐次 Gronwall 不等式积分，得到
> $$
> u(t)\le
> \left(C+\int_0^t C_\varepsilon b(s)^{1/(1-\alpha)}\,ds\right)
> e^{\int_0^t (a(s)+\varepsilon)\,ds}.
> $$
> 该方法核心是“低阶项可被线性项吸收”，代价是常数含任意参数 $\varepsilon$，不如变量替换法精确。

> [!warning] 注意事项
> 1. 条件 $0\le\alpha<1$ 是本质的。若 $\alpha>1$，低阶项变为高阶项，可能有限时间爆破。例如 $u'=u^2$ 的解 $u(t)=1/(1-t)$ 在 $t\to1^-$ 时爆破。
> 2. 积分形式中通常要求 $a,b\ge0$，否则从 $u\le R$ 不能推出 $au\le aR$ 或 $u^\alpha\le R^\alpha$。若 $a$ 可变号，应改用微分形式并借助 $\varepsilon$ 正则化。
> 3. 若 $u$ 可能取零值，变量替换 $Z=u^{1-\alpha}$ 在零点不可导，但通过 $u+\varepsilon$ 正则化可严格处理。
> 4. 当 $C=0$ 时上界仍成立；当 $C>0$ 时更易直接使用 $R(t)\ge C>0$ 而无需正则化。

> [!example] 例题：考研常见情形
> 设 $u(t)\ge0$ 满足
> $$
> u(t)\le 1+\int_0^t \left[u(s)+u(s)^{1/2}\right]ds,\quad t\ge0.
> $$
> 这里 $C=1$，$a(t)\equiv1$，$b(t)\equiv1$，$\alpha=1/2$。由定理，
> $$
> \begin{aligned}
> u(t)
> &\le \left[
> 1^{1/2}e^{t/2}
> +\frac12\int_0^t e^{(t-s)/2}\,ds
> \right]^{2}\\
> &= \left[
> e^{t/2}+(e^{t/2}-1)
> \right]^{2}
> = (2e^{t/2}-1)^2.
> \end{aligned}
> $$

> [!exercise] 习题
> 1. 设 $u(t)\ge0$ 连续，$0<\alpha<1$，$b\ge0$ 连续。若
> $$
> u(t)\le C+\int_0^t b(s)u(s)^\alpha\,ds,
> $$
> 证明：
> $$
> u(t)\le \left[C^{1-\alpha}
> +(1-\alpha)\int_0^t b(s)\,ds\right]^{1/(1-\alpha)}.
> $$
> 2. 设 $u(t)\ge0$ 连续，满足
> $$
> u(t)\le 1+\int_0^t \left[2u(s)+3u(s)^{1/3}\right]ds.
> $$
> 求 $u(t)$ 的一个显式上界。
> 3. 设 $u(t)\ge0$ 连续，$0<\alpha<1$，$a>0$ 为常数。若
> $$
> u(t)\le C+\int_0^t \left[au(s)+u(s)^\alpha\right]ds,
> $$
> 证明当 $C=0$ 时，
> $$
> u(t)\le \left(\frac{1-e^{-a(1-\alpha)t}}{a}\right)^{1/(1-\alpha)}.
> $$

> [!tip] 方法论总结
> 处理考研积分不等式中含低阶项 $u^\alpha$ 的标准流程：
> 4. 确认 $0\le\alpha<1$，且 $u\ge0$，$a,b\ge0$。
> 5. 构造右端函数 $R(t)$，将积分不等式化为微分不等式
>    $$
>    R'(t)\le a(t)R(t)+b(t)R(t)^\alpha.
>    $$
> 6. 作 Bernoulli 变量替换 $Z=R^{1-\alpha}$，得到线性微分不等式
>    $$
>    Z'\le (1-\alpha)a(t)Z+(1-\alpha)b(t).
>    $$
> 7. 用积分因子和线性 Gronwall 公式解出 $Z$ 的上界。
> 8. 回代 $R=Z^{1/(1-\alpha)}$，并由 $u\le R$ 得到 $u$ 的上界。
>
> 核心思想：用非线性替换将低阶项线性化，再用线性工具完成估计。

