## 从第四章开始做练习
1. 使用背景图像
2. 圆角和透明度rgba

## 第五章
### 链接样式的修饰

给外部链接添加辨识图标
```
// 1 用属性选择器 找到所有链接，添加背景图标

a[http ^= "http:"] {
  background: url(./img/external.gif) no-repeat right top;
  padding-right: 10px;
}
// 2. 再恢复自己内部站点的样式
a[http ^= "http://mysite.com"],
a[http ^= "http://www.mysite.com"] {
  background-image: none;
  padding-right: 0;
}

```
## 第六章 列表和导航条
### 列表的自定义图标
* 去掉默认列表样式
* 在li上添加背景图标，并padding出空间放图标

须注意的问题：
* 背景用left定位水平位置，垂直位置会自动设定为center。
* 使用关键字left或50%这种，会同时作用于背景图和元素上。让背景和元素的50%这个位置对齐。
* 使用px则应用于背景图上，让图片左上角放到距离元素左上角的地方，spirt图的做法。

### 一个垂直导航条
1. 在ul和a上应用样式，而不是li上，容易管理。
2. 用em设定按钮的宽度和padding.
3. 突出显示当前页，需要在body上增加一个类，这个以后用jquery做跟灵活方便，这里略过。

> 注意，background 和 padding 的简写一定要注意，容易写成 padding-left: 0.3em 1em; 直接被浏览器划掉说失效。

### 水平导航条
1. a的内容由字体大小和padding撑开，padding一定要放在a上，否则即便用了display：block也不能充满li。
2. 注入的箭头符号padding的方向。
```
a[rel="prev"]:before {
  /*箭头字符的编码*/
  content: "\00AB";
  padding-right: .5em;
  /*注意：这个padding-right指箭头字符的right，而不是a的padding-left*/
}
```
