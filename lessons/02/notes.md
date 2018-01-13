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



在老师的教程里面放的是~符号，但是我的没有出来
@import "~src/common/stylus/variable"
下面使用绝对路径的方式调试出来
@import "../src/common/stylus/variable"


```vue


<template>
  <div id="app">
    hello ,world
  </div>
</template>

<script type="text/ecmascript-6">
export default {
  name: 'app'
}
</script>

<style scoped lang="stylus" rel="stylesheet/stylus">
  @import "../src/common/stylus/variable"

  #app
    background-color:$color-theme
</style>

```



修改`.eslintrc.js`配置文件信息

增加两个配置项


```javascript


// https://eslint.org/docs/user-guide/configuring

module.exports = {
  root: true,
  parser: 'babel-eslint',
  parserOptions: {
    sourceType: 'module'
  },
  env: {
    browser: true,
  },
  // https://github.com/standard/standard/blob/master/docs/RULES-en.md
  extends: 'standard',
  // required to lint *.vue files
  plugins: [
    'html'
  ],
  // add your custom rules here
  rules: {
    // allow async-await
    'generator-star-spacing': 'off',
    // allow debugger during development
    'no-debugger': process.env.NODE_ENV === 'production' ? 'error' : 'off',
    'eol-last':0,//在文件的末尾不用新加一行
    'space-before-function-parents':0
  }
}





```


```json
resolve: {
    extensions: ['.js', '.vue', '.json'],
    alias: {
      '@': resolve('src'),
      'src': resolve('src'),
      'common': resolve('src/common'),
    }
  },

```

配置完alias以后，就能使用~common，导入variable文件了。


```vue


<style scoped lang="stylus" rel="stylesheet/stylus">
  /*@import "../src/common/stylus/variable"*/
  @import "~common/stylus/variable"

  #app
    color:$color-theme
</style>

```
