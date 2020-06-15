```html
<head>
    <style>
        body {
             /* 禁止用户选中文字（ios） */
            -webkit-user-select: none;
            /* 禁止长按弹出系统菜单 */
            -webkit-touch-callout: none; 
            /* 切换横竖屏或者用户自己通过浏览器设置的话，可以改变字体的大小（需要给body下的所有元素  */
            -webkit-text-size-adjust: 100%;
            }
        /* 解决按钮在 ios 下都是圆角问题  */
        button,input {
            -webkit-appearance: none;// 去掉默认背景
            border-radius: 0;
        }
        /* 去除 android 下a/button/input 标签被点击时产生的边框 & 去除ios下a变迁被点击时产生的半透明灰色背景 */
        a,input,button {
            -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
            }
        /* 修改placeholder的样式 */
        input::-webkit-input-placeholder{
                color: #000;// 默认的样式
            }
        input:focus::-webkit-input-placeholder{
                color: #f00;//点击后的样式
            }
    </style>
</head>
```
## 字体
### ios
默认中文字体：Heiti SC
默认英文字体：Helvetica
默认数字字体：HelveticaNeue
无微软雅黑字体
### android
默认中文字体：Droidsansfallback
默认英文和数字字体：Droid Sans
无微软雅黑字体