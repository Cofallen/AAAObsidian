主人，今天由我为您深入剖析如何利用 **Taylor 展开** 优雅地求取斜渐近线。这一方法将极限计算转化为微分运算，揭示了渐近线的本质——函数在无穷远处的“仿射切线”。

> [!summary] 核心速览
> 斜渐近线 $y=ax+b$ 的系数可以通过将 $f(x)$ 在无穷远点作变量代换 $t=1/x$ 后 Taylor 展开到一阶直接读出：若 $f(x)=x\phi(1/x)$ 且 $\phi(t)$ 在 $t=0$ 可导，则 $a=\phi(0)$，$b=\phi'(0)$。即便不能直接提取 $x$，将 $f(1/t)$ 展开为 $\frac{a}{t}+b+o(1)$ 即可。相较极限公式 $\displaystyle a=\lim_{x\to\infty}\frac{f(x)}{x},\; b=\lim_{x\to\infty}(f(x)-ax)$，Taylor 法将问题转化为求导或多项式展开，对根式、指数混合型函数尤其高效。

> [!definition] 斜渐近线
> 设 $f(x)$ 在 $[M,+\infty)$ 上有定义。若存在实数 $a,b$ 使得
> $$\lim_{x\to +\infty}\bigl[f(x)-(ax+b)\bigr]=0,$$
> 则称直线 $y=ax+b$ 为曲线 $y=f(x)$ 当 $x\to +\infty$ 时的 **斜渐近线**。若 $a=0$ 则为水平渐近线。对于 $x\to -\infty$ 可类似定义。垂直渐近线是 $\lim_{x\to x_0}f(x)=\infty$，此处不表。

> [!abstract] 思想精髓：无穷远点处的 Taylor 展开
> 作变换 $t=1/x$，则 $x\to\infty$ 对应 $t\to0^\pm$。令 $g(t)=f(1/t)$，于是 $f(x)-(ax+b)=g(t)-\frac{a}{t}-b$。斜渐近线存在等价于 $g(t)-\frac{a}{t}$ 在 $t=0$ 处有可去奇点，且
> $$g(t)=\frac{a}{t}+b+o(1),\quad t\to0.$$
> 这正是 $g(t)$ 在 $t=0$ 处的 Laurent 展开截断到常数项。如果能通过 Taylor 展开求得 $g(t)$ 在原点的邻域内的表达式，斜渐近线系数便唾手可得。
> 
> 更常见的实用形式：若 $f(x)$ 可写为 $f(x)=x\,\phi\!\left(\frac{1}{x}\right)$，且 $\phi(t)$ 在 $t=0$ 可导，则
> $$\phi(t)=\phi(0)+\phi'(0)t+o(t),$$
> 代入得
> $$f(x)=x\left[\phi(0)+\frac{\phi'(0)}{x}+o\!\left(\frac{1}{x}\right)\right]=\phi(0)\,x+\phi'(0)+o(1).$$
> 于是 $a=\phi(0)$，$b=\phi'(0)$。此式表明斜渐近线系数正是 $\phi$ 在 $0$ 处的值和导数值——多么简洁！

> [!tip] Taylor 展开操作步骤
> 1. **提取主导项**：将 $f(x)$ 整理为一个一次幂函数乘以一个仅依赖 $1/x$ 的表达式。典型手法是提出最高次幂 $x$，使剩余部分当 $x\to\infty$ 时趋于常数。
> 2. **变量代换**：令 $t=1/x$，则 $f(x)=x^k\psi(t)$（斜渐近线情形多为 $k=1$）。若 $k\neq1$ 则曲线有幂函数渐近行为，考研通常考察 $k=1$。
> 3. **展开至一阶**：将 $\psi(t)$ 在 $t=0$ 展开至 $O(t)$：$\psi(t)=\psi(0)+\psi'(0)t+o(t)$。
> 4. **回代得渐近线**：$f(x)=x\bigl(\psi(0)+\psi'(0)/x+o(1/x)\bigr)=\psi(0)x+\psi'(0)+o(1)$，故 $y=\psi(0)x+\psi'(0)$ 即为斜渐近线。
> 5. **对 $x\to -\infty$ 需格外小心**，代换 $t=1/x$ 时 $t\to 0^-$，且提取 $\sqrt{x^2}=|x|=-x$（因 $x<0$）等符号问题。

> [!example] 例1：基础根式
> 求 $f(x)=\sqrt{x^2+2x+5}$ 当 $x\to +\infty$ 的斜渐近线。
> 
> **解**：当 $x>0$，提取 $x$：
> $$f(x)=x\sqrt{1+\frac{2}{x}+\frac{5}{x^2}}=x\,\phi\!\left(\frac{1}{x}\right),$$
> 其中 $\phi(t)=\sqrt{1+2t+5t^2}$。显然 $\phi(0)=1$。求导：
> $$\phi'(t)=\frac{2+10t}{2\sqrt{1+2t+5t^2}},$$
> 故 $\phi'(0)=1$。因此斜渐近线为 $y=1\cdot x+1=x+1$。
> 
> 若 $x\to -\infty$，令 $x<0$，则 $\sqrt{x^2}=|x|=-x$，
> $$f(x)=|x|\sqrt{1+\frac{2}{x}+\frac{5}{x^2}}=-x\,\phi\!\left(\frac{1}{x}\right).$$
> 此时 $\phi(0)=1$，$f(x)=-x(1+1/x+o(1/x))=-x-1+o(1)$，斜渐近线为 $y=-x-1$。
> 
> 常规极限法需计算两个极限，Taylor 法仅需一次求导。

> [!example] 例2：涉及反三角
> 求 $f(x)=x\arctan x$ 当 $x\to +\infty$ 的斜渐近线。
> 
> **解**：利用恒等式 $\arctan x = \frac{\pi}{2} - \arctan\frac{1}{x}$（$x>0$）。则
> $$f(x)=\frac{\pi}{2}x - x\arctan\frac{1}{x}.$$
> 令 $t=1/x$，第二项为 $\frac{1}{t}\arctan t$。在 $t=0$ 处将 $\arctan t$ Taylor展开：
> $$\arctan t = t - \frac{t^3}{3} + O(t^5).$$
> 于是 $\frac{1}{t}\arctan t = 1 - \frac{t^2}{3} + O(t^4)=1+o(1)$。代入：
> $$f(x)=\frac{\pi}{2}x - \left(1+o(1)\right) = \frac{\pi}{2}x - 1 + o(1).$$
> 因此斜渐近线为 $y=\frac{\pi}{2}x-1$。
> 
> 也可直接用 $t=1/x$ 写出 $g(t)=f(1/t)=\frac{1}{t}\arctan(1/t)=\frac{1}{t}\left(\frac{\pi}{2}-\arctan t\right)=\frac{\pi}{2}\cdot\frac{1}{t} - \frac{1}{t}\left(t - \frac{t^3}{3}+\cdots\right)=\frac{\pi}{2}\frac{1}{t}-1+O(t^2)$，立刻得到 $a=\frac{\pi}{2},\; b=-1$。

> [!example] 例3：混合函数
> 求 $f(x)=x\ln\!\left(e+\frac{1}{x}\right)$ 当 $x\to +\infty$ 的斜渐近线。
> 
> **解**：写为 $f(x)=x\ln\!\left[e\left(1+\frac{1}{ex}\right)\right]=x\left[1+\ln\!\left(1+\frac{1}{ex}\right)\right]=x + x\ln\!\left(1+\frac{1}{ex}\right)$。
> 令 $t=1/x$，则第二项为 $\frac{1}{t}\ln(1+\frac{t}{e})$。展开对数：
> $$\ln\!\left(1+\frac{t}{e}\right)=\frac{t}{e} - \frac{t^2}{2e^2} + O(t^3),$$
> 因此 $\frac{1}{t}\ln(1+\frac{t}{e}) = \frac{1}{e} - \frac{t}{2e^2}+O(t^2)=\frac{1}{e}+o(1)$。于是
> $$f(x)=x + \frac{1}{e} + o(1).$$
> 斜渐近线为 $y=x+\frac{1}{e}$。

> [!warning] 注意事项
> - 展开的阶数必须足以提取常数项。形如 $x\cdot\psi(1/x)$ 时，$\psi(t)$ 展开至 $O(t)$ 即可，更高阶项贡献 $o(1)$，不影响斜渐近线。
> - 若函数在无穷远处有振荡（如 $x\sin x$），斜渐近线不存在，不能用此法。
> - 对于 $x\to-\infty$，处理偶次根式务必使用 $|x|$，防止符号颠倒。同样，$1/x$ 的奇次幂符号反转，但 $t\to0^-$ 处的展开形式相同，只是代入时注意。
> - 并不是所有斜渐近线都能轻易通过初等函数的 Taylor 展开得到；若 $\phi(t)$ 在 $t=0$ 不可导，则方法失效，需回归极限定义。

> [!thought] 更高视角：渐近级数与射影几何
> 上述操作实际上是求函数在无穷远点的 **Poincaré 渐近展开** 的前两项。若 $f(x)$ 在无穷远处有渐近级数 $f(x) \sim a x + b + \frac{c_1}{x} + \frac{c_2}{x^2} + \cdots$，则可通过重复提取主项得到。斜渐近线对应一次部分 $ax+b$。
> 
> 在射影几何中，曲线 $y=f(x)$ 的渐近线正是它与其在无穷远点的切线。无穷远点 $(\pm\infty)$ 对应齐次坐标，斜渐近线恰是与曲线交于无穷远点且重数≥2的直线，Taylor 展开给出该“切触”的局部坐标描述。这样的统一视角将微分展开与代数几何联系了起来。

> [!question] 习题
> 1. 求曲线 $y=\frac{x^3+2x^2+1}{x^2-1}$ 的所有渐近线。（提示：作多项式除法，得 $y=x+2+\frac{x+3}{x^2-1}$，斜渐近线 $y=x+2$；垂直渐近线 $x=\pm1$。）
> 2. 求 $f(x)=(x-1)\,e^{\frac{x}{x-1}}$ 当 $x\to\infty$ 的斜渐近线。（答案：$y=ex$）
> 3. 设 $f(x)=\sqrt[3]{x^3+ax^2+bx}$，讨论参数 $a,b$ 使得 $x\to+\infty$ 时存在斜渐近线，并求出渐近线方程。（答案：斜渐近线 $y=x+\frac{a}{3}$。）
> 4. （稍难）求 $f(x)=x\arctan x - \frac{\pi}{2}x\cos\frac{1}{x}$ 当 $x\to+\infty$ 的渐近线。要求用 Taylor 展开。（答案：水平渐近线 $y=-1$，因为一次项抵消。）

主人，以上就是用 Taylor 展开攻克斜渐近线的全部心法。能从极限定义中抽出“无穷远点的导数”，正是分析学的精妙所在。若您需要我补充任何细节，或探究更深入的渐近分析方法，请尽情吩咐。（欠身）