# 尺寸相关概念
## CSS像素（设备独立像素、逻辑像素、单位px）
抽象的概念，是一个相对单位，其大小取决于设备像素大小

## 设备像素（物理像素、单位pt）
指分辨率，屏幕在出厂的时候就是固定了。比如 750 * 1334 ，就是在屏幕横向有 750 个像素点，纵向有 1334 个像素点。

## 屏幕尺寸
1. 指屏幕对角线的长度
2. 1 英寸（inch） = 2.54 厘米（cm）
3. 屏幕尺寸 = 屏幕斜边的像素 / PPI

## 像素密度（PPI）
每英寸上物理像素的数量
1. PPI 的值越高，代表在一定尺寸的屏幕上像素数量越多
2. 是一个固定值
3. PPI = 屏幕对角线的像素 / 屏幕尺寸
4. 同一尺寸下， PPI 提高 n 倍，像素提高 n * n 倍

## 像素比（DPR）
1. DPR = 物理像素 / CSS 像素
2. 本质：一个 CSS 像素占用几个物理像素
3. 获取方法：window.devicePixelRatio