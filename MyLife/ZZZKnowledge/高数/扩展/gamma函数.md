# Gamma 函数：核心定义、余元公式与定积分应用

> [!summary] 核心总结
> Gamma 函数是阶乘的解析延拓。最常用的定义是积分定义，但 Euler 乘积、Weierstrass 乘积、Bohr-Mollerup 定理给出等价刻画。核心工具是递推关系、余元公式、倍元公式以及 Gamma 与 Beta 函数的关系。计算定积分的基本思路：先通过换元把被积函数化为 $t^{a-1}e^{-t}$ 或 $x^{p-1}(1-x)^{q-1}$ 的形状，再用 Gamma 函数、Beta 函数以及余元公式化简。

## 1. Gamma 函数的多种定义

### 1.1 积分定义

> [!definition] 定义 1：积分定义
> 对 $\operatorname{Re}(z)>0$，定义
> $$
> \Gamma(z)=\int_0^\infty t^{z-1}e^{-t}\,dt.
> $$

> [!theorem] 递推关系
> 对 $\operatorname{Re}(z)>0$，
> $$
> \Gamma(z+1)=z\Gamma(z).
> $$
> 特别地，对正整数 $n$，
> $$
> \Gamma(n+1)=n!.
> $$

证明：对 $\Gamma(z+1)$ 分部积分：
$$
\Gamma(z+1)
=\int_0^\infty t^z e^{-t}\,dt
=\left[-t^z e^{-t}\right]_0^\infty
+z\int_0^\infty t^{z-1}e^{-t}\,dt
=z\Gamma(z).
$$
边界项在 $\operatorname{Re}(z)>0$ 时消失。

> [!note] 解析延拓
> 利用递推关系反向写
> $$
> \Gamma(z)=\frac{\Gamma(z+n)}{z(z+1)\cdots(z+n-1)},
> $$
> 右边当 $\operatorname{Re}(z+n)>0$ 时有定义，因此可以把 $\Gamma(z)$ 延拓到整个复平面，除了非正整数点 $z=0,-1,-2,\dots$。这些点是单极点，留数为
> $$
> \operatorname{Res}(\Gamma,-n)=\frac{(-1)^n}{n!}.
> $$

### 1.2 Euler 乘积定义

> [!definition] 定义 2：Euler 乘积
> 对 $z\neq 0,-1,-2,\dots$，
> $$
> \Gamma(z)=\lim_{n\to\infty}
> \frac{n!\,n^z}{z(z+1)\cdots(z+n)}.
> $$

> [!theorem] 积分定义与 Euler 乘积等价
> 对 $\operatorname{Re}(z)>0$，有
> $$
> \int_0^\infty t^{z-1}e^{-t}\,dt
> =\lim_{n\to\infty}
> \int_0^n t^{z-1}\left(1-\frac{t}{n}\right)^n dt
> =\lim_{n\to\infty}
> \frac{n!\,n^z}{z(z+1)\cdots(z+n)}.
> $$

证明思路：先利用
$$
e^{-t}=\lim_{n\to\infty}\left(1-\frac{t}{n}\right)^n
$$
并控制收敛，得到
$$
\Gamma(z)=\lim_{n\to\infty}\int_0^n t^{z-1}\left(1-\frac{t}{n}\right)^n dt.
$$
令 $t=nu$，则
$$
\int_0^n t^{z-1}\left(1-\frac{t}{n}\right)^n dt
=n^z\int_0^1 u^{z-1}(1-u)^n du.
$$
对积分反复分部积分：
$$
\int_0^1 u^{z-1}(1-u)^n du
=\frac{n!}{z(z+1)\cdots(z+n)}.
$$
于是得到 Euler 乘积。

### 1.3 Weierstrass 乘积定义

> [!definition] 定义 3：Weierstrass 乘积
> 对任意 $z\in\mathbb C\setminus\{0,-1,-2,\dots\}$，
> $$
> \frac{1}{\Gamma(z)}
> =z e^{\gamma z}
> \prod_{n=1}^{\infty}
> \left(1+\frac{z}{n}\right)e^{-z/n},
> $$
> 其中 $\gamma$ 为欧拉常数
> $$
> \gamma=\lim_{n\to\infty}
> \left(\sum_{k=1}^n\frac1k-\log n\right).
> $$

> [!note] 与 Euler 乘积的关系
> Weierstrass 乘积可由 Euler 乘积变形得到：
> $$
> \frac{1}{\Gamma(z)}
> =\lim_{n\to\infty}
> \frac{z(z+1)\cdots(z+n)}{n!\,n^z}
> =z\lim_{n\to\infty}
> \left(\prod_{k=1}^n\left(1+\frac{z}{k}\right)\right)
> e^{-z\log n}.
> $$
> 再利用
> $$
> \log n-\sum_{k=1}^n\frac1k\to -\gamma
> $$
> 即得 Weierstrass 乘积。

### 1.4 Bohr-Mollerup 唯一性定理

> [!theorem] Bohr-Mollerup 定理
> 设 $f:(0,\infty)\to(0,\infty)$ 满足：
> 1. $f(1)=1$；
> 2. $f(x+1)=xf(x)$；
> 3. $\log f(x)$ 是凸函数。
>
> 则 $f(x)=\Gamma(x)$。

> [!tip] 关键思想
> 仅有函数方程 $f(x+1)=xf(x)$ 不能唯一确定阶乘的插值。例如
> $$
> f(x)=\Gamma(x)(1+a\sin(2\pi x))
> $$
> 对充分小的 $a$ 仍满足递推和 $f(1)=1$，但它不是对数凸的。Bohr-Mollerup 定理说明：对数凸性是排除振荡解、唯一确定 Gamma 函数的本质条件。

证明思路：对 $x\in(0,1]$ 和正整数 $n$，对数凸性给出
$$
\frac{\log f(n+1)-\log f(n)}{1}
\le \frac{\log f(x+n)-\log f(n)}{x}
\le \frac{\log f(n+2)-\log f(n+1)}{1}.
$$
化简并利用 $f(n)=(n-1)!$，取极限后可唯一确定 $f(x)$。

## 2. 核心性质

### 2.1 递推关系

对任意 $z\in\mathbb C\setminus\{0,-1,-2,\dots\}$，
$$
\Gamma(z+1)=z\Gamma(z).
$$
由此可延拓并计算极点留数。

### 2.2 余元公式

> [!theorem] 余元公式
> 对 $z\notin\mathbb Z$，
> $$
> \Gamma(z)\Gamma(1-z)=\frac{\pi}{\sin \pi z}.
> $$

证明：由 Euler 乘积，
$$
\frac{1}{\Gamma(z)}
=\lim_{n\to\infty}
\frac{z(z+1)\cdots(z+n)}{n!\,n^z}.
$$
同理，
$$
\frac{1}{\Gamma(1-z)}
=\lim_{n\to\infty}
\frac{(1-z)(2-z)\cdots(n+1-z)}{n!\,n^{1-z}}.
$$
两式相乘，分母为 $(n!)^2 n$，分子为
$$
z(1-z)(z+1)(2-z)\cdots(z+n)(n+1-z).
$$
将因子配对：
$$
z\prod_{k=1}^n (k-z)(k+z)\cdot(n+1-z)
=z(n+1-z)\prod_{k=1}^n (k^2-z^2).
$$
因此
$$
\begin{aligned}
\frac{1}{\Gamma(z)\Gamma(1-z)}
&=\lim_{n\to\infty}
\frac{z(n+1-z)\prod_{k=1}^n(k^2-z^2)}
{(n!)^2 n}\\
&=\lim_{n\to\infty}
\frac{z(n+1-z)}{n}
\prod_{k=1}^n\left(1-\frac{z^2}{k^2}\right)\\
&=z\prod_{k=1}^{\infty}
\left(1-\frac{z^2}{k^2}\right)\\
&=\frac{\sin \pi z}{\pi}.
\end{aligned}
$$
最后一步用到正弦函数的 Euler 无穷乘积
$$
\sin \pi z
=\pi z\prod_{k=1}^{\infty}
\left(1-\frac{z^2}{k^2}\right).
$$
于是
$$
\Gamma(z)\Gamma(1-z)=\frac{\pi}{\sin \pi z}.
$$

> [!important] 特别情形
> 取 $z=\frac12$，得
> $$
> \Gamma\left(\frac12\right)^2=\pi,
> $$
> 所以
> $$
> \Gamma\left(\frac12\right)=\sqrt{\pi}.
> $$

### 2.3 倍元公式

> [!theorem] 倍元公式
> 对 $z\neq 0,-\frac12,-1,-\frac32,\dots$，
> $$
> \Gamma(z)\Gamma\left(z+\frac12\right)
> =2^{1-2z}\sqrt{\pi}\,\Gamma(2z).
> $$

证明：先建立 Beta 函数关系
$$
B(z,z)=\int_0^1 t^{z-1}(1-t)^{z-1}\,dt
=\frac{\Gamma(z)^2}{\Gamma(2z)}.
$$
作换元 $t=\frac{1+s}{2}$，则
$$
B(z,z)
=2^{2-2z}\int_0^1 (1-s^2)^{z-1}\,ds.
$$
再令 $u=s^2$，得
$$
\int_0^1 (1-s^2)^{z-1}\,ds
=\frac12 B\left(\frac12,z\right)
=\frac{\Gamma\left(\frac12\right)\Gamma(z)}{2\Gamma\left(z+\frac12\right)}.
$$
于是
$$
\frac{\Gamma(z)^2}{\Gamma(2z)}
=2^{1-2z}
\frac{\Gamma\left(\frac12\right)\Gamma(z)}
{\Gamma\left(z+\frac12\right)}.
$$
代入 $\Gamma\left(\frac12\right)=\sqrt{\pi}$，整理得
$$
\Gamma(z)\Gamma\left(z+\frac12\right)
=2^{1-2z}\sqrt{\pi}\,\Gamma(2z).
$$

### 2.4 Stirling 渐近公式

> [!theorem] Stirling 公式
> 当 $x\to+\infty$ 时，
> $$
> \Gamma(x+1)
> \sim \sqrt{2\pi x}\left(\frac{x}{e}\right)^x.
> $$

证明思路：作代换 $t=xu$，
$$
\Gamma(x+1)
=x^{x+1}\int_0^\infty e^{-x(u-\log u)}\,du.
$$
函数 $u-\log u$ 在 $u=1$ 处取最小值 $1$。用 Laplace 方法在 $u=1$ 附近展开
$$
u-\log u=1+\frac{(u-1)^2}{2}+O\left((u-1)^3\right),
$$
即得主项。

### 2.5 Gamma 函数与 Beta 函数

> [!definition] Beta 函数
> 对 $\operatorname{Re}(x)>0,\operatorname{Re}(y)>0$，定义
> $$
> B(x,y)=\int_0^1 t^{x-1}(1-t)^{y-1}\,dt.
> $$

> [!theorem] Beta 与 Gamma 的关系
> $$
> B(x,y)=\frac{\Gamma(x)\Gamma(y)}{\Gamma(x+y)}.
> $$

证明：
$$
\Gamma(x)\Gamma(y)
=\int_0^\infty\int_0^\infty
u^{x-1}v^{y-1}e^{-(u+v)}\,du\,dv.
$$
作换元
$$
u=st,\qquad v=s(1-t),
$$
雅可比为 $s$，于是
$$
\Gamma(x)\Gamma(y)
=\Gamma(x+y)\int_0^1 t^{x-1}(1-t)^{y-1}\,dt
=\Gamma(x+y)B(x,y).
$$

## 3. 用 Gamma 函数计算常见定积分

### 3.1 基本欧拉积分

由定义立即得到：
$$
\int_0^\infty x^{p-1}e^{-x}\,dx=\Gamma(p),
\qquad \operatorname{Re}(p)>0.
$$

> [!example] 例 1：高斯积分
> $$
> \int_0^\infty e^{-x^2}\,dx
> =\frac12\int_0^\infty u^{-1/2}e^{-u}\,du
> =\frac12\Gamma\left(\frac12\right)
> =\frac{\sqrt{\pi}}2.
> $$

> [!example] 例 2：带幂次的指数积分
> 对 $a>0$，
> $$
> \int_0^\infty x^{m}e^{-ax^2}\,dx
> =\frac{1}{2a^{\frac{m+1}{2}}}
> \Gamma\left(\frac{m+1}{2}\right).
> $$
> 换元 $u=ax^2$ 即可。

### 3.2 Beta 积分

由 Beta 函数定义：
$$
\int_0^1 x^{p-1}(1-x)^{q-1}\,dx
=B(p,q)
=\frac{\Gamma(p)\Gamma(q)}{\Gamma(p+q)}.
$$

> [!example] 例 3：简单幂积分
> $$
> \int_0^1 x^m(1-x)^n\,dx
> =B(m+1,n+1)
> =\frac{\Gamma(m+1)\Gamma(n+1)}{\Gamma(m+n+2)}
> =\frac{m!\,n!}{(m+n+1)!}.
> $$

### 3.3 三角函数积分

> [!theorem] 三角积分化为 Beta 函数
> 对 $\operatorname{Re}(m)>0,\operatorname{Re}(n)>0$，
> $$
> \int_0^{\pi/2}
> \sin^{m-1}x\cos^{n-1}x\,dx
> =\frac12 B\left(\frac{m}{2},\frac{n}{2}\right)
> =\frac{\Gamma\left(\frac{m}{2}\right)\Gamma\left(\frac{n}{2}\right)}
> {2\Gamma\left(\frac{m+n}{2}\right)}.
> $$

证明：令 $u=\sin^2 x$，则 $du=2\sin x\cos x\,dx$，且 $\cos^2 x=1-u$，于是
$$
\begin{aligned}
\int_0^{\pi/2}
\sin^{m-1}x\cos^{n-1}x\,dx
&=\frac12\int_0^1 u^{\frac{m-2}{2}}(1-u)^{\frac{n-2}{2}}\,du\\
&=\frac12 B\left(\frac{m}{2},\frac{n}{2}\right).
\end{aligned}
$$

> [!example] 例 4：Wallis 积分
> $$
> \int_0^{\pi/2}\sin^n x\,dx
> =\frac12 B\left(\frac{n+1}{2},\frac12\right)
> =\frac{\sqrt{\pi}\,\Gamma\left(\frac{n+1}{2}\right)}
> {2\Gamma\left(\frac{n}{2}+1\right)}.
> $$
> 特别地，
> $$
> \int_0^{\pi/2}\sin^2 x\,dx
> =\frac{\pi}{4},
> \qquad
> \int_0^{\pi/2}\sin^3 x\,dx
> =\frac23.
> $$

### 3.4 有理函数积分与余元公式

> [!theorem] 余元积分
> 对 $0<\operatorname{Re}(a)<1$，
> $$
> \int_0^\infty \frac{x^{a-1}}{1+x}\,dx
> =\frac{\pi}{\sin \pi a}.
> $$

证明：作换元
$$
t=\frac{x}{1+x},
\qquad
x=\frac{t}{1-t},
\qquad
dx=\frac{dt}{(1-t)^2},
$$
并且
$$
1+x=\frac{1}{1-t}.
$$
于是
$$
\begin{aligned}
\int_0^\infty \frac{x^{a-1}}{1+x}\,dx
&=\int_0^1
\left(\frac{t}{1-t}\right)^{a-1}
(1-t)\frac{dt}{(1-t)^2}\\
&=\int_0^1 t^{a-1}(1-t)^{-a}\,dt\\
&=B(a,1-a)\\
&=\Gamma(a)\Gamma(1-a)\\
&=\frac{\pi}{\sin \pi a}.
\end{aligned}
$$

> [!example] 例 5：有理幂积分
> 对 $0<a<b$，
> $$
> \int_0^\infty \frac{x^{a-1}}{1+x^b}\,dx
> =\frac{\pi}{b\sin\left(\frac{\pi a}{b}\right)}.
> $$
> 换元 $u=x^b$，化为余元积分即可。

> [!example] 例 6：常见积分
> 取 $a=\frac12$，得
> $$
> \int_0^\infty \frac{dx}{\sqrt{x}(1+x)}
> =\pi.
> $$
> 取 $a=\frac14,b=1$ 可计算
> $$
> \int_0^\infty \frac{x^{-3/4}}{1+x}\,dx
> =\frac{\pi}{\sin(\pi/4)}
> =\sqrt2\,\pi.
> $$

### 3.5 对数积分

对 Gamma 函数积分定义两端关于 $a$ 求导：
$$
\int_0^\infty x^{a-1}e^{-x}\ln x\,dx
=\Gamma'(a).
$$
一般地，
$$
\int_0^\infty x^{a-1}e^{-x}(\ln x)^n\,dx
=\Gamma^{(n)}(a).
$$
这给出含对数的指数积分。

> [!example] 例 7
> $$
> \int_0^\infty e^{-x}\ln x\,dx
> =\Gamma'(1)=-\gamma,
> $$
> 其中 $\gamma$ 为欧拉常数。

## 4. 计算定积分的方法论

1. 观察被积函数是否形如 $x^a e^{-kx^p}$。若在 $[0,\infty)$ 上，先换元 $u=kx^p$，化为 Gamma 函数。
2. 观察被积函数是否形如 $x^a(1-x)^b$。若在 $[0,1]$ 上，直接化为 Beta 函数。
3. 观察有理函数 $\frac{x^{a-1}}{1+x^b}$。先换元 $u=x^b$，化为 $\frac{u^{\frac ab-1}}{1+u}$，再用 Beta 函数和余元公式。
4. 观察三角函数积分 $\sin^p x\cos^q x$。令 $u=\sin^2 x$ 或 $u=\cos^2 x$，化为 Beta 函数。
5. 遇到含 $\ln x$ 与 $x^{a-1}e^{-x}$ 的积分，可对 Gamma 函数的参数求导。
6. 计算过程中要紧盯收敛条件，例如余元公式要求 $0<\operatorname{Re}(a)<1$，否则积分在 $0$ 或 $\infty$ 发散。

## 5. 习题

> [!exercise] 习题 1
> 证明：
> $$
> \int_0^\infty \frac{x^{1/3}}{(1+x)^2}\,dx
> =\frac{2\pi}{3\sqrt3}.
> $$
> 提示：化为 Beta 函数或直接使用余元公式。

> [!exercise] 习题 2
> 计算
> $$
> \int_0^\infty \frac{dx}{1+x^4}.
> $$
> 提示：先用余元公式表示 $\int_0^\infty \frac{x^{a-1}}{1+x}\,dx$，再换元。

> [!exercise] 习题 3
> 利用 Gamma 函数证明 Wallis 乘积：
> $$
> \frac{\pi}{2}
> =\prod_{n=1}^{\infty}
> \frac{4n^2}{4n^2-1}.
> $$
> 提示：考虑 $I_{2n}=\int_0^{\pi/2}\sin^{2n}x\,dx$ 和 $I_{2n+1}$ 的比值，并用 Gamma 函数表示。

> [!exercise] 习题 4
> 计算
> $$
> \int_0^1 \frac{dx}{\sqrt[4]{1-x^4}}.
> $$
> 提示：令 $u=x^4$，化为 Beta 函数。

> [!exercise] 习题 5
> 利用余元公式计算
> $$
> \int_0^\infty \frac{x^{a-1}}{(1+x)^2}\,dx
> $$
> 并用 Beta 函数验证结果。
