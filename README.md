# 适配的元素：
1. 字体

2. 宽高

3. 间距

4. 图像

# 适配的方法：
1. 百分比适配

2. viewport 缩放(不常用)
把所有机型的 css 像素设置成一致的

3. DPR 缩放
把 css 像素缩放成与设备像素一样大的尺寸

4. rem 适配(常用)

5. vw、vh 适配

## viewport 缩放
需要动态的改变 meta 标签中 initial-scale 的值
```js
(function () {
    // 获取 css 像素（前提是 viewport 没有缩放）
    var curWidth = document.documentElement.clientWidth;
    // 或
    // var curWidth = window.innerWidth;
    // 或
    // var curWidth = window.screen.width;
    var targetWidth = 375;
    var scale = curWidth / targetWidth;
    // 给 meta 标签加上一个 id="view"
    var view = document.getElementById('view');
    view.content = "initial-scale=" + scale + ",minimum-scale=" + scale + ",maximum-scale=" + scale + ",user-scalable=no";
})()
```

## DPR 缩放
```js
(function () {
     var meta = document.querySelector('meta[name="viewport"]');
     var scale = 1 / window.devicePixelRatio;

     if (!meta) {
         meta = document.createElement('meta');
         meta.name = 'viewport';
         meta.content = "initial-scale=" + scale + ",minimum-scale=" + scale + ",maximum-scale=" + scale + ",user-scalable=no";
         doucment.head.appendChild(meta);
     }else {
         meta.content = "initial-scale=" + scale + ",minimum-scale=" + scale + ",maximum-scale=" + scale + ",user-scalable=no";
     }
})()
```

## rem 适配
### rem
CSS3新增的相对单位，相对于根元素字体大小。
```
html {
    font-size: 20px;
}
1rem = 20px
```

### em
作为 font-size 的单位时，其值为其父元素字体的大小，作为其他属性单位时，其值为自身字体的大小。
```
父级字体大小
font-size: 16px;
1em = 32px;
自身字体大小
font-size: 16px;
1em = 16px;
```
#### 注意：在真正切图的时候的方法是
1. 算 rem，根据设备实际的 css 像素来算
2. 量出一个元素在设计稿里的尺寸（比如一张图片100px）
3. 拿到这个尺寸除以像素比（DPR）之后，再去换算rem
```js
(function (doc, win, designWidth) {
    var html = doc.documentElement;
    const refreshRem = () => {
        const clientWidth = html.clientWidth;
        if (clientWidth >= designWidth) {
            html.style.fontSize = '100px';
        }else {
            html.style.fontSize = 100 * (clientWidth / designWidth) + 'px';
        }
    }
    doc.addEventListener('DOMContentLoaded', refreshem);
})(document, window, 750)
// 参数750 表示以 iphone6 为基准
```
### 媒体查询
```
@media screen and (min-width: 320px) {
    html {
        font-size: 21px
    }
    body {
        font-size: 15px
    }
}
@media screen and (min-width: 480px) {
    html {
        font-size: 32px
    }
    body {
        font-size: 15.36px
    }
}
```

## vw, vh
### vw: Viewport's Width 的简写， 1vw 等于视口宽度的 1%
### vh: Viewport's Height 的简写，1vh 等于视口高度的 1%
### vmin: 取 vw 和 vh 中最小的值
### vmax: 取vw 和 vh 中最大的值
支持情况： ios8  android 4.4
### 使用方案
1. 方案一： 通篇使用 vw
2. 方案二：通过 vw 设置根节点字体大小，页面里的尺寸还是使用 rem（常用）
#### 方案二的用法
```js
// 通过公式 100 * (clientWidth / designWidth) 算出需要给 html 根节点设置的字体大小为多少。假如 clientWidth 为414，设计稿量出来的 designWidth 为 1080。
var html_px = 100 * (414 / 1080);
// 再算出 1vw 的具体像数值
var _vw =  414 / 100;
// 最后算出根节点字体大小具体为多少 vw，将这个值给根节点
var html_vw = html_px / _vw;
// ==> html_vw = 9.259259259259261
```
```css
html {
    font-size: 9.259259259259261vw
}
/* 如果现在要给 div 设置一个 400 * 200 宽高就可以使用 rem，值为实际的像素值除以 100*/
div {
    width: 4rem;
    height: 2rem;
}
```