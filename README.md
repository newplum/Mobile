# viewport
可视窗口区，通过 meta 标签设置
## 未设置：
1. 默认为980，但不同型号也会不同
2. 用 document.documentElement.clientWidth 获取

## 设置了
### content 包含以下内容
- width  视口宽度，值为正整数，或字符串 device-width（设备的宽度指 css 像素）
- height 视口高度（与 width 一致）
- user-scalable 是否允许用户缩放页面，值为 no 或 yes
- initial-scale 页面初始缩放值，值为数字（可以为小数）
- minimum-scale 页面最小能够缩放的比例，值为数字（可以为小数）
- maximum-scale 页面最大能够缩放的比例，值为数字（可以为小数）
```html
<meta name="viewport" content="width=device-width,initial-scale=1,user-scalable=no,minimum-scale=1,maximum-scale=1">
```
initial-scale 有值的情况下算页面的公式：
- 缩放比=css像素/viewport宽度  
- viewport宽度=css像素/缩放比