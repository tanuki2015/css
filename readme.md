# css设计指南笔记
## 5.2固定三栏布局
1. 首先需要<wrapper>,固定宽度960px，居中。
2. <header>无需浮动，自动摆在第一行。
3. <nav>，<article>,<aside>依次float:left.
4. <footer>引用clear:both后自动摆在最下。

### 三栏布局的问题
内容的增加或每栏margin,padding的增加，导致空间不够，把后面的<aside>挤到下面。

解决方法是：
1. 仔细调整每一栏的宽度（太麻烦，弃用）。
2. 为每一栏增加一个<inner>的容器，不设置宽度，在它上面设置padding和margin，不要动外面有宽度的div。
3. 最为简单的方法，给浮动的<nav>，<article>,<aside>应用box-sizing:border-box.

#### ie6,7不支持box-sizing时，应用borderBoxModel.js这个腻子脚本。

#### 预防过大的元素，img或文本。
可以给img使用{max-width:100%;},以限制图片不超过父元素的宽度。

## 5.3 三栏-中栏流动布局
1. 用负的外边距实现（麻烦，略过）。
2. 用css3单元格实现（ie7以下不支持，也没有腻子脚本）。

实现比较简单，给<nav>，<article>,<aside>加上`display:table-cell`就行了。
