# FWHM 带宽与最优检偏角

## FWHM 定义
对固定检偏器角度 $\beta$，输出相对光强为：

$$
I_{\mathrm{rel}}(\lambda,\beta)
$$

半高点满足：

$$
I_{\mathrm{rel}}(\lambda_{\mathrm{left}},\beta)
=
I_{\mathrm{rel}}(\lambda_{\mathrm{right}},\beta)
=
\frac{I_{\max}(\beta)}{2}
$$

带宽：

$$
\boxed{
\Delta\lambda(\beta)
=
\mathrm{FWHM}(\beta)
=
\lambda_{\mathrm{right}}(\beta)
-
\lambda_{\mathrm{left}}(\beta)
}
$$

## 半高条件
若中心波长 $\lambda^\*$ 满足：

$$
\theta(\lambda^\*)=\beta
$$

则峰值可达 $I_{\max}=1$，半高条件为：

$$
\boxed{
\left|\beta-\theta(\lambda)\right|
=
\frac{\pi}{4}
}
$$

## 局部近似
在 $\lambda^\*$ 附近一阶展开：

$$
\theta(\lambda)-\beta
\approx
\left.
\frac{d\theta}{d\lambda}
\right|_{\lambda=\lambda^\*}
(\lambda-\lambda^\*)
$$

带宽近似：

$$
\boxed{
\Delta\lambda(\beta)
\approx
\frac{\pi/2}{
\left|
\left.
\dfrac{d\theta}{d\lambda}
\right|_{\lambda=\lambda^\*(\beta)}
\right|
}
}
$$

角度制：

$$
\boxed{
\Delta\lambda(\beta)
\approx
\frac{90^\circ}{
\left|
\left.
\dfrac{d\theta}{d\lambda}
\right|_{\lambda=\lambda^\*}
\right|
}
}
$$

## 最优角度
目标是找到带宽最窄的检偏器角度：

$$
\boxed{
\beta_{\mathrm{best}}
=
\arg\min_{\beta}\mathrm{FWHM}(\beta)
}
$$

**斜率 $\left|d\theta/d\lambda\right|$ 越大，局部可分辨波长越细，近似带宽越窄。**
