# Laplace 方法：核心思想与简单推导

> [!abstract] 核心思想
> 大参数 $n$ 让指数项 $e^{nf(x)}$ 变得极其“势利”：它只认 $f$ 的最大值点 $x_0$。
> 只要 $f(x)<f(x_0)$，哪怕只小一点，$e^{n(f(x)-f(x_0))}$ 也会指数级变小。
> 所以积分贡献集中在 $x_0$ 附近，其他区域全部忽略。
> 这就是“局部化”思想。

> [!note] 简单推导
> 设 $x_0\in(a,b)$ 是 $f$ 的内点最大值，且
> $$
> f'(x_0)=0,\qquad f''(x_0)<0.
> $$
> 在 $x_0$ 附近用 Taylor 展开：
> $$
> f(x)\approx f(x_0)-\frac{A}{2}(x-x_0)^2,
> $$
> 其中 $A=-f''(x_0)>0$。
>
> 于是
> $$
> \int_a^b g(x)e^{nf(x)}dx
> \approx
> g(x_0)e^{nf(x_0)}
> \int_{x_0-\delta}^{x_0+\delta}
> e^{-\frac{nA}{2}(x-x_0)^2}
> dx.
> $$
> 令 $u=\sqrt n(x-x_0)$，则
> $$
> \int_{-\sqrt n\delta}^{\sqrt n\delta}
> e^{-\frac{A}{2}u^2}
> du
> \to
> \int_{-\infty}^{\infty}
> e^{-\frac{A}{2}u^2}
> du
> =
> \sqrt{\frac{2\pi}{A}}.
> $$
> 代回得到
> $$
> \int_a^b g(x)e^{nf(x)}dx
> \sim
> g(x_0)e^{nf(x_0)}
> \sqrt{\frac{2\pi}{-nf''(x_0)}}.
> $$

> [!tip] 公式怎么记
> 记三个要素：
> 1. 最大值点 $x_0$。
> 2. 主指数因子 $e^{nf(x_0)}$。
> 3. 高斯宽度因子 $\sqrt{\dfrac{2\pi}{n|f''(x_0)|}}$。
>
> 直观理解：指数把积分压成一个“高斯波包”，宽度约为 $1/\sqrt n$，高度由 $g(x_0)e^{nf(x_0)}$ 决定。

> [!warning] 边界最大值要小心
> 如果最大值在区间端点 $x=a$，内部公式不能直接用。
> 例如
> $$
> \int_0^{\pi/2}\sin^n x dx
> =
> \int_0^{\pi/2} e^{n\ln\sin x} dx.
> $$
> 这里 $f(x)=\ln\sin x$ 的最大值在端点 $x=\frac{\pi}{2}$，并且
> $$
> f'\left(\frac{\pi}{2}\right)=0,\qquad
> f''\left(\frac{\pi}{2}\right)=-1.
> $$
> 端点附近
> $$
> \sin\left(\frac{\pi}{2}-t\right)=\cos t\approx 1-\frac{t^2}{2},
> $$
> 所以
> $$
> \ln\sin x\approx -\frac{t^2}{2},
> $$
> 积分只在 $t>0$ 一侧贡献，相当于高斯积分的一半：
> $$
> \int_0^{\pi/2}\sin^n x dx
> \sim
> \frac12\sqrt{\frac{2\pi}{n}}
> =
> \sqrt{\frac{\pi}{2n}}.
> $$
> 这就是著名的 Wallis 型渐近。

> [!tip] 常见边界情形的快捷记忆
> 若最大值在边界 $x=1$，且 $f'(1)\neq 0$，则局部
> $$
> f(x)\approx f(1)-c(1-x),\quad c>0.
> $$
> 积分
> $$
> \int_0^1 e^{nf(x)}dx
> \approx
> e^{nf(1)}
> \int_0^\infty e^{-nc u}du
> =
> e^{nf(1)}\frac{1}{nc}.
> $$
> 所以
> $$
> \int_0^1 x^n g(x)dx
> \sim
> \frac{g(1)}{n},
> $$
> 因为 $x^n=e^{n\ln x}$，$f(x)=\ln x$，$f'(1)=1$。

> [!example] 验证内部公式
> 求
> $$
> \int_{-\infty}^{\infty} e^{-nx^2}dx.
> $$
> 取 $f(x)=-x^2$，$g(x)=1$。最大值点 $x_0=0$，且
> $$
> f'(0)=0,\qquad f''(0)=-2.
> $$
> 代入公式：
> $$
> \int_{-\infty}^{\infty} e^{-nx^2}dx
> \sim
> \sqrt{\frac{2\pi}{-n(-2)}}
> =
> \sqrt{\frac{\pi}{n}}.
> $$
> 这正是标准高斯积分结果。

> [!success] 方法论总结
> 做积分极限题时，先把幂写成指数：
> $$
> [a(x)]^n=e^{n\ln a(x)}.
> $$
> 然后看 $f(x)=\ln a(x)$ 的最大值点在哪里。
> - 内点二阶非退化：主项 $n^{-1/2}$。
> - 边界线性衰减：主项 $n^{-1}$。
> - 边界二次衰减：主项 $n^{-1/2}$ 的一半。
> 最后用局部展开和高斯积分或指数积分写出等价量。
