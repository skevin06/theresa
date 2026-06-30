# Drude 型旋光色散与级数展开

## Drude 型公式
用 Drude 型旋光色散描述糖溶液中比旋光度随波长变化：

$$
\boxed{
[\alpha]_{\lambda}
=
\frac{A}{\lambda^2-\lambda_0^2}
}
$$

因此旋光角为：

$$
\boxed{
\theta(\lambda)
=
[\alpha]_{\lambda}lc
=
\frac{Alc}{\lambda^2-\lambda_0^2}
}
$$

- $A$：与旋光物质有关的常数。
- $c$：溶液浓度。
- $l$：光程长度。
- $\lambda_0$：特征吸收波长。

## 蔗糖文献参数
Mahurin, Compton 与 Zare 对蔗糖溶液旋光色散曲线给出的 Drude 拟合值：

$$
\boxed{\lambda_0 \approx 131\ \mathrm{nm}}
$$

$$
\boxed{
A \approx 2.17\times 10^7\,
\mathrm{deg\cdot nm^2\cdot dm^{-1}\cdot g^{-1}\cdot mL}
}
$$

参考：*Demonstration of Optical Rotatory Dispersion of Sucrose*, J. Chem. Educ. 1999, DOI: [10.1021/ed076p1234](https://doi.org/10.1021/ed076p1234)。

## 斜率
对波长求导：

$$
\boxed{
\frac{d\theta}{d\lambda}
=
-\frac{2Alc\lambda}{(\lambda^2-\lambda_0^2)^2}
}
$$

该斜率决定不同波长被角度区分的快慢，也是估算带宽的关键量。

## 远离吸收峰展开
当 $\lambda \gg \lambda_0$：

$$
\frac{1}{\lambda^2-\lambda_0^2}
=
\frac{1}{\lambda^2}
+\frac{\lambda_0^2}{\lambda^4}
+\frac{\lambda_0^4}{\lambda^6}
+\cdots
$$

因此：

$$
\boxed{
\theta(\lambda)
=
Alc
\left(
\frac{1}{\lambda^2}
+\frac{\lambda_0^2}{\lambda^4}
+\frac{\lambda_0^4}{\lambda^6}
+\cdots
\right)
}
$$

## 参考波长定积分
若已知参考波长旋光角：

$$
\boxed{
\theta(\lambda)
=
\theta(\lambda_{\mathrm{ref}})
+
\int_{\lambda_{\mathrm{ref}}}^{\lambda}
\frac{d\theta}{d\lambda'}
\,d\lambda'
}
$$
