# meta
放在 <head> 标签中

1. 禁止识别电话与邮箱（邮箱有时候没效果）
<meta name="format-detection" content="telephone=no, email=no" />

2. 设置添加到主屏幕后的标题（ios）
<meta name="app-mobile-web-app-title" content="index"/>

3. 添加到主屏幕后，全屏显示，删除苹果默认的工具栏和菜单栏
<meta name="apple-mobile-web-app-capable" content="yes" />

4. 放在桌面上的 logo
<link rel="apple-touch-icon-precomposed" href="xxx.png" />

5. 启动时候的画面
<link rel="apple-touch-startup-image" href="xxxx.png" />

设置 x5 内核浏览器只能竖屏浏览
<meta name="x5-orientation" content="portrait" />

设置 x5 内核浏览器全屏浏览
<meta name="x5-fullscreen" content="true" />
