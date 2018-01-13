在src文件夹下面创建以下文件夹

api
common
- fonts
- stylus
- js
-image
components
static

```shell

cd src
mkdir common api store
cd common 
mkdir js image stylus fonts


```



02--06：30
mixin的作用

```stylus

// 背景图片
bg-image($url)
  background-image: url($url + "@2x.png")
  @media (-webkit-min-device-pixel-ratio: 3),(min-device-pixel-ratio: 3)
    background-image: url($url + "@3x.png")

// 不换行
no-wrap()
  text-overflow: ellipsis
  overflow: hidden
  white-space: nowrap

// 扩展小图标的点击区域
extend-click()
  position: relative
  &:before
    content: ''
    position: absolute
    top: -10px
    left: -10px
    right: -10px
    bottom: -10px
    
```

```shell
npm i stylus stylus-loader -D

```
