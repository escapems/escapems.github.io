我准备在这系列文章中记录一下我美化自己blog的过程，研究一下不同的配置文件标签是什么效果。

首先，利用这个tag里的教程。
[gmeek提供的教程](https://blog.meekdai.com/tag.html#Gmeek)

### 1. yearColorList
用于自定义显示不同年份标签的颜色

模样是这样的：
`"yearColorList":["#bc4c00","#0969da","#1f883d", "#A333D0"],`

> [!NOTE]
> 结论：
list里的颜色顺序是按照顺序被显示，分配给年份标签的





想修改自己年份标签的颜色可以随便复制文章中的一个数据，直接用谷歌搜索，不需要额外添加关键词，就可以得到“颜色选择器”，来自己挑选喜欢的颜色

推理过程：

通过颜色选择器，我们可以发现，案例给出的颜色按照顺序分别是：黄褐色，蓝色，绿色，紫色
我观察过meekdai的blog页面，颜色和年份的对应为
蓝色：2025  2021  2017
黄褐：2024  2020  2016
紫色：2023  2019  2015
绿色：2022  2018
它似乎并不是按照顺序排列的，但每一年的颜色会按照list的顺序更改。
我选择了五种颜色
#d6b1e6 紫色，#99ccf0 蓝色，#c2f2ca 绿色，#f6f7cb 黄色，#cfabc9粉色
今年是2025年，标签显示的是#D6B1E6【我用取色器得到的】
所以可以推测，list里的颜色顺序是按照顺序被显示，分配给年份标签的

### 2. urlMode
用于定义文章链接生成模式，目前支持pinyin/issue/ru_translit

根据gpt的总结：
**Pinyin**
会将文章标题转换为拼音，作为 URL 的一部分
案例：/post/ni-hao-shi-jie.html
优点：链接可读性高、利于搜索引擎优化（SEO）

**Issue**
使用文章的 issue 编号（数字）作为链接
案例：/post/1.html
优点：不想暴露标题、喜欢简洁数字型链接

**ru_translit**
将文章标题使用俄语转写系统转换为英文字符
案例：/post/privet-mir.html（比如“Привет мир”变成拉丁字母）
优点：如果你的文章标题多为俄语（或其他非拉丁文字），用 ru_translit 更合适。

### 3.目录，图片放大功能
我首先参考了[CJW的blog](https://github.com/cao-gift/cao-gift.github.io)
这个博主的config文件，最后三行代码可以直接复制来用，就会生成目录等功能

**加载目录功能脚本**
`<script src='https://blog.freeblock.cn/plugins/ArticleTOC.js'></script>`
TOC 通常指 “Table of Contents”，也就是自动生成文章目录的功能。

**加载 Lightbox 功能**
`<script src='https://blog.freeblock.cn/plugins/lightbox.js'></script>`
用于图像弹出查看功能。
你点击文章里的图片时，它会弹窗放大、支持左右滑动浏览。

**图片链接修正逻辑**
```
<script>
  document.querySelectorAll('a').forEach(anchor => {
    const img = anchor.querySelector('img');
    if (img && img.hasAttribute('data-canonical-src')) {
      const canonicalSrc = img.getAttribute('data-canonical-src');
      anchor.setAttribute('href', canonicalSrc);
      img.setAttribute('src', canonicalSrc);
      img.removeAttribute('data-canonical-src');
    }
  });
</script>
```
恢复原始图片链接和原始图源，保证点击图片时显示高清版本

我的目录可以收起展开，是chatgpt帮我实现的，大家如果喜欢可以去我的config里面复制来用！


### 其他：
primerCSS
这个标签直接改自己想要的链接，别的不用管
