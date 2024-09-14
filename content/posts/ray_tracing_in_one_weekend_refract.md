+++
title = "Ray tracing in one weekend折射公式"
date = "2024-09-15"
description = "折射公式喵"

[taxonomies]
tags = ["Graphics"]
+++

本文是对Ray Tracing in One Weekend中[折射](https://raytracing.github.io/books/RayTracingInOneWeekend.html#dielectrics/snell'slaw)一节公式的推到

图中已知的变量已经用蓝色标出，分别是$\eta、\eta'$，还有一个向量$R$已知，标为了绿色

图中一些向量为了方便观看用不同颜色标记了，其中$R_{\bot}'$和$R_{\parallel}'$是$R^{'}$的分量，分别和法线$n$单位向量垂直和平行，$R$是入射光线与$R'$出射光线两个向量都是单位向量，长度是1

首先要算出来的是$cos\theta$的值，因为$R$和$n$是单位向量，所以很容易得出

$$ \cos\theta = R \cdot n$$

之后能看出$R$在y轴上的投影的长度为$R$的长度乘上$\cos\theta$，而$R$的长度和$n$的长度其实是一样的，所以也等于$n$的长度乘上$cos\theta$，可以得出$R$在x轴上的分量为$R + n \cdot \cos\theta$，而这个分量的长度也容易通过图像得知是$\sin\theta$，所以x轴正方向的单位向量可以算出来是

$$\frac{R + n \cdot \cos\theta}{\sin\theta}$$

观察图像其实可以因为$R^{'}$长度是1知道$R_{\bot}^{'}$的长度是$\sin\theta^{'}$

由于斯涅尔折射定律

$$ \sin\theta' = \frac{\eta}{\eta'} \cdot \sin\theta $$

可以得出

$$ R_{\bot}^{'} = \sin\theta' \cdot \frac{R + n \cdot \cos\theta}{\sin\theta} = \frac{\eta}{\eta'} \cdot \frac{R + n \cdot \cos\theta}{\sin\theta}$$

因为$R_{\parallel}'$和$R_{\bot}'$是垂直的，并且是同一个单位向量的分量，可以得出$R_{\parallel}'$的长度为$\sqrt{1 - |\mathbf{R'}_{\bot}|^2}$，而$R_{\parallel}'$的方向和$n$相反，所以

$$R_{\parallel}' = -\sqrt{1 - |\mathbf{R'}_{\bot}|^2} \cdot n$$

$R_{\parallel}'$和$R_{\bot}'$加起来就得到$R'$了